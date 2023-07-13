# 注意 僅網頁備份 非香港城市大學官網 禁止一切非法利用
# WEB ARCHIVE ONLY!
# NOT THE OFFICIAL WEBSITE OF THE CITY UNIVERSITY OF HONG KONG!
# ALL ILLEGAL USES ARE FORBIDDEN!

<details>
    <summary><h1>點擊查看天書（作者： HKSC2023-072）</h1></summary>
    <p><li><a href="xueba/A">Q1: 100%]</a></p>
    <p><li><a href="xueba/B">Q2: 100%]</a></p>
    <p><li><a href="xueba/C">Q3: 100%]</a></p>
    <p><li><a href="xueba/D">Q4: 100%]</a></p>
    <p><li><a href="xueba/E">Q5: 59%]</a></p>
    <p><li><a href="xueba/F">Q6: 50%]</a></p>
</details>

## [Q1: 100%](A)

```js
const inp = require('fs').readFileSync(0).toString();
const input = inp.trim();
const inputi = parseInt(input, 10);
let comb = (input.length) * 9;

for (let i=1; i<=9; i++) {
	let illegal = parseInt(i.toString().repeat(input.length), 10);
	if (illegal > inputi) comb--;
}

console.log(comb);
```


## [Q2: 100%](B)
```js

function getZodiacSign(date) {
    const month = date.getMonth() + 1; // getMonth() returns 0-based month (0=January), so add 1
    const day = date.getDate();

    if ((month == 3 && day >= 21) || (month == 4 && day <= 19)) {
        return 'Aries';
    } else if ((month == 4 && day >= 20) || (month == 5 && day <= 20)) {
        return 'Taurus';
    } else if ((month == 5 && day >= 21) || (month == 6 && day <= 21)) {
        return 'Gemini';
    } else if ((month == 6 && day >= 22) || (month == 7 && day <= 22)) {
        return 'Cancer';
    } else if ((month == 7 && day >= 23) || (month == 8 && day <= 22)) {
        return 'Leo';
    } else if ((month == 8 && day >= 23) || (month == 9 && day <= 22)) {
        return 'Virgo';
    } else if ((month == 9 && day >= 23) || (month == 10 && day <= 23)) {
        return 'Libra';
    } else if ((month == 10 && day >= 24) || (month == 11 && day <= 21)) {
        return 'Scorpio';
    } else if ((month == 11 && day >= 22) || (month == 12 && day <= 21)) {
        return 'Sagittarius';
    } else if ((month == 12 && day >= 22) || (month == 1 && day <= 19)) {
        return 'Capricorn';
    } else if ((month == 1 && day >= 20) || (month == 2 && day <= 18)) {
        return 'Aquarius';
    } else {
        return 'Pisces';
    }
}

const inp = require('fs').readFileSync(0).toString();
lines = inp.split(/\r?\n/);
lines.pop();
lines.shift();
let dates = lines.reduce((reduce, line, k, a) => {
	let date = new Date(line);
	let z = getZodiacSign(date);
	if (z in reduce) reduce[z]++;

	return reduce;
}, {
        'Aries': 0,
        'Taurus': 0,
        'Gemini': 0,
        'Cancer': 0,
        'Leo': 0,
        'Virgo': 0,
        'Libra': 0,
        'Scorpio': 0,
        'Sagittarius': 0,
        'Capricorn': 0,
        'Aquarius': 0,
        'Pisces': 0
    });

let output = '';
for (const zodiacSign in dates) {
    output += `${zodiacSign}: ${dates[zodiacSign]}\n`;
}
console.log(output.trim());
```
## [Q3: <50%](C)

```js
const inp = require('fs').readFileSync(0).toString();
let lines = inp.split(/\r?\n/);
lines.pop();
let last = lines.pop();
let size = lines.shift().split(/\s/).map(num => parseInt(num, 10));
let pos = last.split(/\s/).map(num => parseInt(num, 10)-1);
let mat = lines.reduce((col, line) => {
    let row = line.split(/\s/).reduce((row, num) => [...row, parseInt(num)], []);
    while (row.length <= pos[3]) row = [...row, ...row];
    return [...col, row];
}, []);
while (mat.length <= pos[1]) mat = [...mat, ...mat];
console.error(size, pos, mat);

// Extract the submatrix using slice()
let sub = mat.slice(pos[2], pos[3] + 1).map(row => row.slice(pos[0], pos[1] + 1));
console.log(sub);

// Calculate the sum of the submatrix
let sums = sub.reduce((r, a) => r.map((b, i) => a[i] + b), Array(sub[0]?.length || 0).fill(0));
let sum = sums.reduce((partialSum, a) => partialSum + a, 0);
console.log(sum % (10**9+7));
```
## [Q4: ???%](D)

```js
let cache = {};
function steps(n, stepped) {
	if (n in cache) return cache[n];
	if (n === 1) {
		return stepped;
	}

	if (n % 2 === 0) n = n / 2;
	else n = 3 * n + 1;
	cache[n] = steps(n, stepped + 1);
	return cache[n];
}

let inp = require('fs').readFileSync(0).toString().trim();

let sum = 0;
for (let i=1; i <= parseInt(inp, 10); i++) {
	// if (i in cache) sum += cache[i];
	// else {
		
		sum += steps(i, 0);
	// }
}
console.log(sum);
```
# [Q5](E)
# [Q6](F)
