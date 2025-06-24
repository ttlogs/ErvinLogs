---
type: character
tags:
  - character
character:
---

```dataviewjs
let lvlUpRules = [200, 400, 700, 1000, 1300, 1800, 2300, 2800, 3500, 4200, 4900, 5600, 6500, 7400, 8300, 9200, 10300, 11400, 12500, 13600];

function calculateLvL(lvlUpRules,exp){
	let lvl=1;
	for (let requiredExp of lvlUpRules){
		if (exp<requiredExp) {return lvl;}
		else lvl+=1;
	}
}

function flatten(list){
	let result = [];
	for(let element of list){
		if (typeof(element)!=typeof(result)){
			result.push(element);
		}
		else {
			result.push(...element);
		}
	}
	return(result);
}

let adventures = dv.pages().where(
note=> note.file.frontmatter.type=="JournalEntry" & note.file.frontmatter.character==dv.current().file.frontmatter.character);
let rewards = flatten(adventures.rewards);

let exp = rewards.filter((t)=>t.split("оп").length>1);
exp = exp.map((t)=>parseInt(t.split("оп")[0]));
exp = exp.reduce((acc, val) => acc + val, 0);

let lvl = calculateLvL(lvlUpRules,exp);

let gp = rewards.filter((t)=>t.split("зм").length>1);
gp = gp.map((t)=>parseInt(t.split("зм")[0]));
gp = gp.reduce((acc, val) => acc + val, 0);

let food = rewards.filter((t)=>t.split("сухпай").length>1);
food = food.map((t)=>parseInt(t.split("сухпай")[0]));
food = food.reduce((acc, val) => acc + val, 0);

dv.span(
        "**Уровень:** "+lvl+"("+exp+"/"+lvlUpRules[lvl-1]+") "
        + "![progress](https://progress-bar.dev/"
        + parseInt((exp / lvlUpRules[lvl-1]) * 100)
        + "/)"
    )
dv.paragraph("**Золото:** "+gp+" зм")
dv.paragraph("**Еда:** "+food+" сухпай")
```

> [!info]- Репутация
> 
> | Fraction | Репутация | ✉️ |
> | ---- | ---- | ---- |
> | Археологи | `$= dv.pages().where(page => page.fraction==["[[археологи]]",]&& (page.file.folder==dv.current().file.folder)).length` |  |
> | Маги | `$= dv.pages().where(page => page.fraction=="маги"&& (page.file.folder==dv.current().file.folder)).length` |  |
> | Наемники | `$= dv.pages().where(page => page.fraction=="наемники"&& (page.file.folder==dv.current().file.folder)).length` |  |
> | Судостроители | `$= dv.pages().where(page => page.fraction=="судостроители"&& (page.file.folder==dv.current().file.folder)).length` |  |
> | Плотники | `$= dv.pages().where(page => page.fraction=="плотники"&& (page.file.folder==dv.current().file.folder)).length` |  |
> | Металлурги | `$= dv.pages().where(page => page.fraction=="металлурги"&& (page.file.folder==dv.current().file.folder)).length` |  |

> [!warning]- 📖Приключения
> ```dataview
> table without id
> file.link as source,
> sum(number(filter(rewards, (t)=>contains(t, "оп")))) as оп,
> sum(number(filter(rewards, (t)=>contains(t, "зм")))) as зм
> from "/"
> where rewards and this.file.folder=file.folder
> sort file.link desc
> ```

> [!quote]+ 🎒Предметы
> ```dataview
> table without id
> rewards as inventory,
> file.link as source
> from "/"
> where rewards and this.file.folder=file.folder
> flatten rewards
> where 
> 	!contains(rewards, "зм") and
> 	!contains(rewards, "оп") and
> 	!contains(rewards, "сухпай") and
> 	!contains(rewards, "рекомендательное письмо")
> sort inventory
> ```

> [!about] 🪞 Внешность
> описание


