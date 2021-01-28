
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
import React from 'react';

export const Tall = () => {
  console.log('Tall');
  const [value, setValue] = useGlobalState('tall', '170');
  return (
    <div>
      Tall:
      <input
        value={value}
        onChange={(e) => {
          setValue(e.target.value);
        }}
      />
    </div>
  );
};
export const Weight = () => {
  console.log('Weight');
  const [value, setValue] = useGlobalState('weight', '60');
  return (
    <div style={{ display: 'flex' }}>
      Weight:
      <input
        value={value}
        onChange={(e) => {
          setValue(e.target.value);
        }}
      />
    </div>
  );
};

export const Bmi = () => {
  console.log('Bmi');
  const [tall] = useGlobalState<string>('tall');
  const [weight] = useGlobalState<string>('weight');
  return (
    <div>
      {isNaN(Number(tall)) || isNaN(Number(weight))
        ? 'Error'
        : `BMI:${Math.floor((Number(weight) / Math.pow(Number(tall) / 100, 2)) * 100) / 100}`}
    </div>
  );
};

const Page = () => (
  <>
    <Bmi />
    <Tall />
    <Weight />
  </>
);
export default Page;
```

