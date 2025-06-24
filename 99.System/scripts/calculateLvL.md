```dataviewjs
function calculateLvL(exp){
        let requiredExpRules = [200,400,700,1000,1300,1800,2300,2800,3500,4200,4900,5600,6500,7400,8300,9200,10300,11400,12500,13600];
        let lvl=1;
        for (let requiredExp of requiredExpRules){
                if (exp<requiredExp) {return lvl;}
                else lvl+=1;
        }
}
exports.calculateLvL = calculateLvL;
```