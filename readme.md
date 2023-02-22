# Frontend Assessment (Alladin Melico)

## ⚙️ Installation
1. `yarn`
1. `yarn dev`

## ⚡️ Demo
*Hover the mouse on the top of the screen to navigate between exercises.*
![2023-02-22 11-38-20](https://user-images.githubusercontent.com/40887666/220515887-8a80508c-c061-4c3e-8237-ded5898ce3f7.gif)


### Exercise 1
**📱 Mobile**
![mobile recording](https://user-images.githubusercontent.com/40887666/220350484-0fc2633e-065d-4dfb-813d-7d394407c9bc.gif)


**🖥️ Desktop**
![My Movie2](https://user-images.githubusercontent.com/40887666/220350526-18b1c23d-3e7f-4ed6-8c24-5ebf1fd13fd6.gif)

### Exercise 2
![2023-02-22 11-35-50](https://user-images.githubusercontent.com/40887666/220516000-8d413825-5023-41cf-8614-222e6d83b986.gif)


## 🍌 Explain why the result of ('b' + 'a' + + 'a' + 'a').toLowerCase() is `banana`
We can slice that banana into sections to understand or digest it a lot better:
- `'b' + 'a'` contatenates two strings and returns `'ba'` 
- `+ 'a'` is an example of [unary plus](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Unary_plus). We often use unary plus to convert something into a number. The idea is similar whenever we add `''` with something and it converts it into string e.g. `1 + '' = '1'` 
- by appending`'a'` we now have `'baNaNa'` but it looks weird 
- so `.toLowerCase()` makes it a lot readable by converting the string into lowercase
- we now have `'banana'`, enjoy!