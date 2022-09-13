# О проектах в Яндекс практикум 
Мои учебные проекты. 1-й проект - вводный. В нем работа с КЭ и ГЗ, первые чек лист и тест-кейс по функциональности и верстке
2-й проект - Тестирование Веб приложений. Чек листы по логике и верстке, тестирование реализации на фронтенде новой фичи, с недоработанным бэкендом
3-й проект Тестирование мобильных приложений и API . Проверка функциональности определенных требований мобильного приложение и тестирование новой функциональности API
4-й проект - Работа с консолью и базой данных
5-й проект - Дипломный. Теория, mind map для Яндекс.Самокат, чек-лист на проверку экрана "Статус заказа" веб приложения Яндекс.Самокат, валидация полей формы бронирования, тест-кейсы для проверки нотификации в моб.приложении Яндекс.Самокат, Проверка новых фичей на бэкенде (API)
# Документация 
Ссылки на работы в google.docs 1-й прокет https://docs.google.com/document/d/1fGjL9TUOCZsDNE8UUFM2QiV1bZ3QwQjz_OI_SWB6edg/edit?usp=sharing
2-й проект https://docs.google.com/document/d/1hR3lt6AvPX14yUPaLMRGBEzN2pvLU4t_AEBJg-gxjDw/edit
3-й проект https://docs.google.com/document/d/1dTu0rChweACSJfpetztpGJjR9d0RgDuZvMb_lBARjZM/edit
4-й проект https://docs.google.com/document/d/1xS6GkCXtP4D1GGGTDJ_v08NudjP3AWvuS_pmUtQHUOY/edit#
Дипломный проект https://docs.google.com/document/d/19SyhMbgyTPP7G-P93qPiCTSnX-idYVFYr25Dd5Lk3x0/edit
# Автотест 
Мой первый автотест на js. Задача: Должен открыться браузер, открыть ссылку ya.ru , найти поисковую строку, ввести в ней текст, нажать кнопку "найти", получить результат поиска и сравнить ОР и ФР

const puppeteer = require('puppeteer'); async function testYaRu(){ console.log('Запуск браузера'); const browser = await puppeteer.launch();

console.log('Создание новой вкладки в браузере');
const page = await browser.newPage();

console.log('Переход на страницу ya.ru');
await page.goto('https://ya.ru/');

console.log('Ввод текста "Автоматизация тестирования" в поисковую строку');
const searchField = await page.$('#text');
await searchField.type('Автоматизация тестирования');

console.log('Клик в кнопку "Найти"');
const searchButton = await page.$('.button[type=submit]');
await searchButton.click();

console.log('Ожидание перехода в страницу поисковых результатов');
await page.waitForNavigation('.serp-item');

console.log('Получение элементов результата поиска');
const result = page.$('.serp-item');// todo: создай переменную result и положи в неё элемент поисковой выдачи

console.log('Сравнение ОР и ФР');
if(result == null) {console.log('Результаты поиска не найдены')}
else console.log('Результаты поиска отобразились');

console.log('Закрытие браузера');
await browser.close();
