# tailwindComponents
This repo is a list of notes on creating Tailwind CSS components in React 

## Adding Gradient to text
First add the gradient to the tailwind.config.js

```
 theme: {
    extend: {
      backgroundImage: {
        'hero-gradient':
          "linear-gradient(20deg, rgba(71,129,236,1) 0%, rgba(38,62,227,1) 41%, rgba(38,62,227,1) 60%, rgba(130,241,220,1) 100%)",
        'hero-gradient-background':
          "linear-gradient(100deg, rgba(216,222,255,1) 0%, rgba(242,244,255,1) 27%, rgba(242,244,255,1) 76%, rgba(216,222,255,1) 100%)",
      },
    },
  },
```

Make the background color the gradient from the tailwind.css
Make the text transparent and clip the text. 

```html
<h2 className="bg-hero-gradient text-transparent bg-clip-text">Text</h2>
```

In a React component
```js
interface Props
{
    text: string,
    gradient: string,
    options?: string
}
// this component will display text using the gradiant
// used in the props
export default function GradiantText(props: Props) {
    return (
        <>
            <h2 className={`bg-${props.gradient} text-transparent bg-clip-text ${props.options}`}>{props.text}</h2>
        </>
    )
}
```

---

## Including a button inside of a input text field

```html
<input type="text" className="px-3 py-2 outline-none drop-shadow-xl rounded-full h-[51px] w-[40%] relative z-0" placeholder="Enter your email" />

<button type="button" className="px-3 py-2 ml-[-217px] bg-hero-gradient text-white rounded-full hover:bg-blue-700 z-40 relative items-end">
    Subscribe To Newsletter
</button>
```
---

## Adding gradients to tailwind.config.js

```
    extend: {
      backgroundImage: {
        'hero-gradient':
          "linear-gradient(20deg, rgba(71,129,236,1) 0%, rgba(38,62,227,1) 41%, rgba(38,62,227,1) 60%, rgba(130,241,220,1) 100%)",
      }
```

```js
// Then in code call it as
// bg-hero-gradient is what applies the gradient
<button type="button" className="px-3 py-2 ml-[-217px] bg-hero-gradient text-white rounded-full hover:bg-blue-700 z-40 relative items-end">Subscribe To Newsletter</button>
```

## Div Cover entire background

Div to cover entire background (good for gradient background so it doesn't repeat the pattern)

```html
<!-- the key className is: absolute inset-0 w-full h-full !-->
<div className='bg-hero-gradient-background absolute inset-0 w-full h-full'>
```
---