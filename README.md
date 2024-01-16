# coins-problem

const  coins = [50, 20, 10, 5, 2, 1, 0.5]
function getCurrentCount(amount:number){
    let rest = amount
    let i = 0
    let change = []
    while(rest !== 0){
        if(rest < coins[i]) {
            i++
            continue
        }
        const repeat = Math.floor(rest / coins[i])
        rest = amount % coins[i]
        if(repeat > 0){
            change.push({
                coin: coins[i],
                repeat
            })
        }
        i++
    }

    const numberOfCoin = change.reduce((acc,current)=>{
        return acc + current.repeat
    },0)

    return { numberOfCoin, details: change }
}
console.log(getCurrentCount(37.5))
