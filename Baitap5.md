
1 . Tìm số phần tử lặp lại nhiều nhất trong 1 mảng và đếm xem nó lặp lại bao nhiêu lần
const arr = [1, 2, 3, 9, 4, 5, 9 ,3 , 6, 7, 8, 9, 9]
function findMostFrequent(arr) {
    let mostFrequent = arr[0]
    let frequency = 1
    let obj = {}
    for(let i = 0; i < arr.length; i++) {
        let keyOfObj = arr[i]
        if(obj[keyOfObj] == null){
            obj[keyOfObj] = 1
        } else {
            obj[keyOfObj]++
        }
        if(obj[keyOfObj] > frequency){
            mostFrequent = keyOfObj
            frequency = obj[keyOfObj]
        }
    }
    return {element: mostFrequent, frequency: frequency}
}
let result = findMostFrequent(arr)
console.log('Giá trị lập nhiều nhất tron mảng là:', result.element, 'Tần suất:', result.frequency)

2 . Tìm ước chung lớn nhất và bội chung nhỏ nhất của hai số nguyên dương
var a = 32, b =64
function UCLNaAndB(a, b) {
    if(a == 0 || b == 0) 
        return a + b
    while(a != b) {
        if(a > b) 
            a -= b
        else 
            b -= a
    }
    return a
}
console.log('UCLN của', a,'và', b, 'là:', UCLNaAndB(a, b))

3 . Cho một chuỗi  , tìm độ dài của xâu dài nhất là chuỗi con với điều kiện là chuỗi con đó  không lặp lại ký tự    
VD : 
input : “swwkeppa"
output :  4 (chuỗi con dài nhất không có kí tự lặp lại là : wkep" )
input : “abcabcaa"
output : 3 ( chuỗi con dài nhất không có kí tự lặp lại là : “abc” )

var string1 = 'swwkeppa'
var string2 = 'abcabcaa'
function stringChild(string) {
    let arr = []
    let max = 0, j = 0
    while (j < string.length) {
        if(arr.indexOf(string[j]) === -1) {
            arr.push(string[j])
            max = Math.max(max, arr.length)
            j++
        } else {
            arr.shift()
        }
    }
    return max
}
console.log('Chuỗi con dài nhất không lập lại trong chuỗi \'',string1,'\' có độ dài là:', stringChild(string1))
console.log('Chuỗi con dài nhất không lập lại trong chuỗi \'',string2,'\' có độ dài là:', stringChild(string2))

4 . Cho một số nguyên x, trả về true nếu x là một số xuôi ngược đều giống nhau , nếu khác thì trả về false
VD :
input : 121
output : true

input : -121
output : false

var input = 12321
function mirror(number) {
    let reverse = number.toString().split('').reverse().join('')
    return (reverse === number.toString())
}
if(mirror(input)) {
    console.log('Xuôi')
} else {
    console.log('Không xuôi')
}

5 . Cho một mảng và một giá trị target . Tổng của 2 số bất kì trong mảng cộng lại sẽ bằng giá trị của biến target . Nhiệm vụ của bạn là tìm vị trí của 2 số đấy và cho vào một mảng
VD : 
input :  nums = [1,2,5,7] , target = 9
output :  [1,3]    vì nums[1] + nums[3] = 9

var input = [1,2,5,7], target = 9
function findLocalTarget(arr, target) {
    for(let i=0; i<arr.length-1; i++) {
        for(let j=i+1; j<arr.length; j++) {
            if(arr[i] + arr[j] === target) {
                return [i, j]
            }
        }
    }
}
console.log('Ket qua: ', findLocalTarget(input, target))

6 . Viết hàm tìm chuỗi tiền tố chung dài nhất trong một mảng các chuỗi. Nếu không có tiền tố chung, hãy trả về một chuỗi rỗng ""
VD : 
input : strs = ["flower","flow","flight"]
output : “fl"

input : strs = ["dog","racecar","car"]
output : “ ”

var input1 = ["flower","flow","flight"]
var input2 = ["dog","racecar","car"]
function longestCommonPrefix(arr) {
    if (arr.length === 0) return ''
    let prefix = arr[0]
    for(let i = 1; i < arr.length; i++) {
        while (arr[i].indexOf(prefix) !== 0) {
            prefix = prefix.substr(0, prefix.length-1)
            if(prefix === '') return ''
        }
    }
    return prefix
}
console.log('Tiền tố la: ', longestCommonPrefix(input1))
console.log('Tiền tố la: ', longestCommonPrefix(input2))