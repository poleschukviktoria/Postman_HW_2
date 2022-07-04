# Postman_HW_2

http://162.55.220.72:5005/first
1. Отправить запрос.   
2. Статус код 200
````html
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});   
````

3. Проверить, что в body приходит правильный string.
````html
pm.test("Body is correct", function () {
    pm.response.to.have.body("This is the first responce from server!");
});
````

http://162.55.220.72:5005/user_info_3
1. Отправить запрос.   
2. Статус код 200
````html
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
````

3. Спарсить response body в json.
````html
let jsonData = pm.response.json();
console.log("result --", jsonData);
let resp_name = jsonData.name;
let resp_age = jsonData.age;
let resp_salary = jsonData.salary;
let resp_salary_1_5 = jsonData.family.u_salary_1_5_year;
````

4. Проверить, что name в ответе равно name из request (name вбить руками.)
````html
pm.test("Resp_name = Req_name", function () {
    pm.expect(resp_name).to.eql("Vika");
});
````
5. Проверить, что age в ответе равно age из request (age вбить руками.)
````html
pm.test("Resp_age = Req_age", function () {
    pm.expect(resp_age).to.eql("39");
});
````
6. Проверить, что salary в ответе равно salary из request (salary вбить руками.)
````html
pm.test("Resp_salary = Req_salary", function () {
    pm.expect(resp_salary).to.eql(1000);
});
````
7. Спарсить request.
````html
let req = request.data;
let req_name = req.name;
let req_age = req.age;
let req_salary = req.salary;
````
8. Проверить, что name в ответе равно name из request (name забрать из request.)
````html
pm.test("Resp_name = Req_name", function () {
    pm.expect(resp_name).to.eql(req_name);
});
````
9. Проверить, что age в ответе равно age из request (age забрать из request.)
````html
pm.test("Resp_age = Req_age", function () {
    pm.expect(resp_age).to.eql(req_age);
});
````
10. Проверить, что salary в ответе равно salary из request (salary забрать из request.)
````html
pm.test("Resp_salary = Req_salary", function () {
    pm.expect(resp_salary).to.eql(+(req_salary));
});
````
11. Вывести в консоль параметр family из response.
````html
console.log(jsonData.family)
````
12. Проверить что u_salary_1_5_year в ответе равно salary*4 (salary забрать из request)
````html
pm.test("u_salary_1_5_year", function () {
    pm.expect(resp_salary_1_5).to.eql(req_salary*4);
});
````
http://162.55.220.72:5005/object_info_3
1. Отправить запрос.   
2. Статус код 200
````html
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
````
3. Спарсить response body в json.
````html
let jsonData = pm.response.json();
console.log("result --", jsonData);
let resp_name = jsonData.name;
let resp_age = jsonData.age;
let resp_salary = jsonData.salary;
let resp_family = jsonData.family;
let resp_dog = jsonData.family.pets.dog;
let resp_dog_name = jsonData.family.pets.dog.name;
let resp_dog_age = jsonData.family.pets.dog.age;
````
4. Спарсить request.
````html
let req = pm.request.url.query.toObject();
let req_name = req.name;
let req_age = req.age;
let req_salary = req.salary;
````
5. Проверить, что name в ответе равно name из request (name забрать из request.)
````html
pm.test("Resp_name = Req_name", function () {
    pm.expect(resp_name).to.eql(req_name);
});
````
6. Проверить, что age в ответе равно age из request (age забрать из request.)
````html
pm.test("Resp_age = Req_age", function () {
    pm.expect(resp_age).to.eql(req_age);
});
````
7. Проверить, что salary в ответе равно salary из request (salary забрать из request.)
````html
pm.test("Resp_salary = Req_salary", function () {
    pm.expect(resp_salary).to.eql(+req_salary);
});
````
8. Вывести в консоль параметр family из response.
````html
console.log("Resp_family", resp_family);
````
9. Проверить, что у параметра dog есть параметры name.
````html
pm.test("Dog_name", function () {
    pm.expect(JSON.stringify(resp_dog)).to.include("name");
});
````
10. Проверить, что у параметра dog есть параметры age.
````html
pm.test("Dog_age", function () {
    pm.expect(JSON.stringify(resp_dog)).to.include("age");
});
````
11. Проверить, что параметр name имеет значение Luky.
````html
pm.test("Dog_name_Luky", function () {
    pm.expect(resp_dog_name).to.eql("Luky");
});
````
12. Проверить, что параметр age имеет значение 4.
````html
pm.test("Dog_age_4", function () {
    pm.expect(resp_dog_age).to.eql(4);
});
````
http://162.55.220.72:5005/object_info_4
1. Отправить запрос.   
2. Статус код 200
````html
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
````
3. Спарсить response body в json.
````html
let jsonData = pm.response.json();
console.log("result --", jsonData);
let resp_name = jsonData.name;
let resp_age = jsonData.age;
let resp_salary = jsonData.salary;
````
4. Спарсить request.
````html
let req = pm.request.url.query.toObject();
let req_name = req.name;
let req_age = req.age;
let req_salary = req.salary;
````
5. Проверить, что name в ответе равно name из request (name забрать из request.)
````html
pm.test("Resp_name = Req_name", function () {
    pm.expect(resp_name).to.eql(req_name);
});
````
6. Проверить, что age в ответе равно age из request (age забрать из request.)
````html
pm.test("Resp_age = Req_age", function () {
    pm.expect(resp_age).to.eql(+req_age);
});
````
7. Вывести в консоль параметр salary из request.
````html
console.log("Req_salary", req_salary);
````
8. Вывести в консоль параметр salary из response.
````html
console.log("Resp_salary", resp_salary);
````
9. Вывести в консоль 0-й элемент параметра salary из response.
````html
console.log("Resp_salary_0", resp_salary[0]);
````
10. Вывести в консоль 1-й элемент параметра salary параметр salary из response.
````html
console.log("Resp_salary_1", resp_salary[1]);
````
11. Вывести в консоль 2-й элемент параметра salary параметр salary из response.
````html
console.log("Resp_salary_2", resp_salary[2]);
````
12. Проверить, что 0-й элемент параметра salary равен salary из request (salary забрать из request.)
````html
pm.test("Resp_salary_0 = Req_salary", function () {
    pm.expect(resp_salary[0]).to.eql(+req_salary);
});
````
13. Проверить, что 1-й элемент параметра salary равен salary*2 из request (salary забрать из request.)
````html
pm.test("Resp_salary_1 = Req_salary*2", function () {
    pm.expect(+resp_salary[1]).to.eql(req_salary*2);
});
````
14. Проверить, что 2-й элемент параметра salary равен salary*3 из request (salary забрать из request.)
````html
pm.test("Resp_salary_2 = Req_salary*3", function () {
    pm.expect(+resp_salary[2]).to.eql(req_salary*3);
});
````
15. Создать в окружении переменную name   
16. Создать в окружении переменную age     
17. Создать в окружении переменную salary    
18. Передать в окружение переменную name   
19. Передать в окружение переменную age   
20. Передать в окружение переменную salary  
````html
pm.environment.set("name", req.name);
pm.environment.set("age", req.age);
pm.environment.set("salary", req.salary);
````
21. Написать цикл который выведет в консоль по порядку элементы списка из параметра salary.
````html
resp_salary.forEach((item) => {console.log(item)});
````
http://162.55.220.72:5005/user_info_2
1. Вставить параметр salary из окружения в request       
2. Вставить параметр age из окружения в age      
3. Вставить параметр name из окружения в name         
4. Отправить запрос.        
5. Статус код 200
````html
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
````
6. Спарсить response body в json.
````html
let jsonData = pm.response.json();
console.log("result --", jsonData);
let start_qa_salary = jsonData.start_qa_salary;
let qa_salary_after_6_months = jsonData.qa_salary_after_6_months;
let qa_salary_after_12_months = jsonData.qa_salary_after_12_months;
let qa_salary_after_1_5_year = jsonData["qa_salary_after_1.5_year"];
let qa_salary_after_3_5_years = jsonData["qa_salary_after_3.5_years"];
let person = jsonData.person;
let person_u_name = jsonData.person.u_name;
let person_u_age = jsonData.person.u_age;
let person_u_salary_5_years = jsonData.person.u_salary_5_years;
````
7. Спарсить request.
````html
let req = request.data;
let req_name = req.name;
let req_age = req.age;
let req_salary = req.salary;
````
8. Проверить, что json response имеет параметр start_qa_salary
````html
pm.test("start_qa_salary", function () {
    pm.expect(JSON.stringify(jsonData)).to.include("start_qa_salary");
});
````
9. Проверить, что json response имеет параметр qa_salary_after_6_months
````html
pm.test("qa_salary_after_6_months", function () {
    pm.expect(JSON.stringify(jsonData)).to.include("qa_salary_after_6_months");
});
````
10. Проверить, что json response имеет параметр qa_salary_after_12_months
````html
pm.test("qa_salary_after_12_months", function () {
    pm.expect(JSON.stringify(jsonData)).to.include("qa_salary_after_12_months");
});
````
11. Проверить, что json response имеет параметр qa_salary_after_1.5_year
````html
pm.test("qa_salary_after_1.5_year", function () {
    pm.expect(JSON.stringify(jsonData)).to.include("qa_salary_after_1.5_year");
});
````
12. Проверить, что json response имеет параметр qa_salary_after_3.5_years
````html
pm.test("qa_salary_after_3.5_years", function () {
    pm.expect(JSON.stringify(jsonData)).to.include("qa_salary_after_3.5_years");
});
````
13. Проверить, что json response имеет параметр person
````html
pm.test("person", function () {
    pm.expect(JSON.stringify(jsonData)).to.include("person");
});
````
14. Проверить, что параметр start_qa_salary равен salary из request (salary забрать из request.)
````html
pm.test("Resp_start_qa_salary = Req_salary", function () {
    pm.expect(start_qa_salary).to.eql(+req_salary);
});
````
15. Проверить, что параметр qa_salary_after_6_months равен salary*2 из request (salary забрать из request.)
````html
pm.test("Resp_qa_salary_after_6_months = Req_salary*2", function () {
    pm.expect(qa_salary_after_6_months).to.eql(req_salary*2);
});
````
16. Проверить, что параметр qa_salary_after_12_months равен salary*2.7 из request (salary забрать из request.)
````html
pm.test("Resp_qa_salary_after_12_months = Req_salary*2.7", function () {
    pm.expect(qa_salary_after_12_months).to.eql(req_salary*2.7);
});
````
17. Проверить, что параметр qa_salary_after_1.5_year равен salary*3.3 из request (salary забрать из request.)
````html
pm.test("Resp_qa_salary_after_1.5_year = Req_salary*3.3", function () {
    pm.expect(qa_salary_after_1_5_year).to.eql(req_salary*3.3);
});
````
18. Проверить, что параметр qa_salary_after_3.5_years равен salary*3.8 из request (salary забрать из request.)
````html
pm.test("Resp_qa_salary_after_3.5_years = Req_salary*3.8", function () {
    pm.expect(qa_salary_after_3_5_years).to.eql(req_salary*3.8);
});
````
19. Проверить, что в параметре person, 1-й элемент из u_name равен salary из request (salary забрать из request.)
````html
pm.test("Resp_person_u_name_1 = Req_salary", function () {
    pm.expect(person_u_name[1]).to.eql(+req_salary);
});
````
20. Проверить, что что параметр u_age равен age из request (age забрать из request.)
````html
pm.test("Resp_person_u_age = Req_age", function () {
    pm.expect(person_u_age).to.eql(+req_age);
});
````
21. Проверить, что параметр u_salary_5_years равен salary*4.2 из request (salary забрать из request.)
````html
pm.test("Resp_person_u_salary_5_years = Req_salary*4.2", function () {
    pm.expect(person_u_salary_5_years).to.eql(req_salary*4.2);
});
````
22. ***Написать цикл который выведет в консоль по порядку элементы списка из параметра person.
````html
for (let i in jsonData.person)
console.log(jsonData.person[i])
````
