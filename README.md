
# @react-liblary/use-global-state

## sample

- sample sorce code  
<https://github.com/SoraKumo001/use-global-state-sample01>
- sample gh-pages  
<https://sorakumo001.github.io/use-global-state-sample01/>

## What is this

Global `setState` that does not require `provider` or `store`

## usage

- `[data,dispatch] = useGlobalState(key,initData)`

```tsx
import { useGlobalState } from '@react-liblary/use-global-state';

interface Props {
  name: string;
}

export const Counter = ({ name }: Props) => {
  const [count, setCount] = useGlobalState<number>(name, 10);
  return (
    <div>
      <button onClick={() => setCount((count) => count - 1)}>-</button>
      <button onClick={() => setCount(count + 1)}>+</button>
      {count}
    </div>
  );
};
```

- `mutate(key,data)`

```tsx
import { mutate } from '@react-liblary/use-global-state';

interface Props {
  name: string;
}

export const InputBox = ({ name }: Props) => {
  return (
    <div>
      <input
        defaultValue="100"
        onKeyPress={(e) => {
          e.key === 'Enter' && mutate(name, Number(e.currentTarget.value));
        }}
      />
    </div>
  );
};
```

- Page

```tsx
import React from 'react';
import { Counter } from '../components/Counter';
import { InputBox } from '../components/InputBox';

const Page = () => (
  <>
    <InputBox name="count1" />
    <Counter name="count1" />
    <Counter name="count1" />
    <hr />
    <InputBox name="count2" />
    <Counter name="count2" />
    <Counter name="count2" />
  </>
);
export default Page;

```
