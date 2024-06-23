# tailwindComponents
This repo is a list of notes on creating Tailwind CSS components in React 

## Buttons

### Glowing Background Gradient Effects

```html
<div class="px-8 py-32">
  <div class="grid gap-8 items-start justify-center">
    <div class="relative group">
      <div class="absolute -inset-0.5 bg-gradient-to-r from-pink-600 to-purple-600 rounded-lg blur opacity-75 group-hover:opacity-100 transition duration-1000 group-hover:duration-200 animate-tilt"></div>
      <button class="relative px-7 py-4 bg-black rounded-lg leading-none flex items-center divide-x divide-gray-600">
        <span class="flex items-center space-x-5">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-pink-600 -rotate-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19.428 15.428a2 2 0 00-1.022-.547l-2.387-.477a6 6 0 00-3.86.517l-.318.158a6 6 0 01-3.86.517L6.05 15.21a2 2 0 00-1.806.547M8 4h8l-1 1v5.172a2 2 0 00.586 1.414l5 5c1.26 1.26.367 3.414-1.415 3.414H4.828c-1.782 0-2.674-2.154-1.414-3.414l5-5A2 2 0 009 10.172V5L8 4z" />
          </svg>
          <span class="pr-6 text-gray-100">Labs Release 2021.09</span>
        </span>
        <span class="pl-6 text-indigo-400 group-hover:text-gray-100 transition duration-200">See what's new &rarr;</span>
      </button>
    </div>
  </div>
</div>

```

In the tailwind.config.css

```
module.exports = {
  mode: 'jit',
  theme: {
    extend: {
      animation: {
        tilt: 'tilt 10s infinite linear',
      },
      keyframes: {
        tilt: {
          '0%, 50%, 100%': {
            transform: 'rotate(0deg)',
          },
          '25%': {
            transform: 'rotate(0.5deg)',
          },
          '75%': {
            transform: 'rotate(-0.5deg)',
          },
        },
      },
    },
  },
  plugins: [],
}


```

___

### Including a button inside of a input text field

```html
<input type="text" className="px-3 py-2 outline-none drop-shadow-xl rounded-full h-[51px] w-[40%] relative z-0" placeholder="Enter your email" />

<button type="button" className="px-3 py-2 ml-[-217px] bg-hero-gradient text-white rounded-full hover:bg-blue-700 z-40 relative items-end">
    Subscribe To Newsletter
</button>
```
---

## Images

### Creating blur effect on bottom part of an image
- Set top div to relative. 
- Use the same image next to one another and then use `absolute bottom-0 left-0 z-20` to overlay it on top of the first image then bring it to the front
- Use `h-[25%]` to only show the bottom 25% blurred
- Use `object-bottom` to anchor the image to the bottom so its now overlayed correctly after the `h-[25%]` shifted it.  

```html
<div className="relative">
    <img className='object-cover w-full justify-center rounded-lg' src={props.imgPath} />
    <img className='absolute blur-sm object-cover h-[25%] object-bottom w-full justify-center rounded-lg bottom-0 left-0 z-20' src={props.imgPath} />
    <div className="absolute bottom-4 ml-3 w-full z-30">
        <h3 className="text-white font-bold">
            {props.author}
        </h3>
        <h4 className="text-white font-bold">
            {props.date}
        </h4>
    </div>
</div>
```

## Text

### Adding Gradient to text
First add the gradient to the tailwind.config.js

```jsx
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
<h2 className="bg-hero-gradient text-[45px] md:text-[55px] font-extrabold inline text-transparent bg-clip-text">Text</h2>
```

---

## Gradients

### Adding gradients to tailwind.config.js

```jsx
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

## Backgrounds

### Div Cover entire background

Div to cover entire background (good for gradient background so it doesn't repeat the pattern)

```html
<!-- the key className is: absolute inset-0 w-full h-full !-->
<div className='bg-hero-gradient-background absolute inset-0 w-full h-full'>
```
---