# proxy-demo

```js

function observe(target){
    const handler = {
        get(target, key, receiver) {

            try {
                return new Proxy(target[key], handler)
            } catch (err) {
                return Reflect.get(target, key, receiver)
            }
        },
        set(target, key, value, receiver) {
            const preValue=target[key]

            console.log(`set ${key}`);
    
            return Reflect.set(target, key, value, receiver)
        }
    }
    return new Proxy(target, handler)

}



let obj={
    name:'libai',
    shares:[
        {age:12},{age:13},{age:14}
    ]
}

let res=observe(obj)
res.name='kk' // set name
res.shares=[{age:100}] // set shares
res.shares[2]={age:12} // set 2
```
