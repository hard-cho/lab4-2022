# Разработка игры и интеграция сервисов в пользовательский интерфейс
Отчет по лабораторной работе #4 выполнила:
- Россихина Ирина Александровна
- РИ-300002

Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | * | 20 |
| Задание 3 | * | 20 |

знак "*" - задание выполнено; знак "#" - задание не выполнено;

Работу проверили:
- к.т.н., доцент Денисов Д.В.
- к.э.н., доцент Панов М.А.
- ст. преп., Фадеев В.О.

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

Структура отчета

- Данные о работе: название работы, фио, группа, выполненные задания.
- Цель работы.
- Задание 1.
  - Часть 1 - Создание анимации объектов на сцене.
  - Часть 2 - Создание стартовой сцены и переключение между ними.
  - Часть 3 - Доработка меню и функционала с остановкой игры.
  - Часть 4 - Добавление звукового сопровождения в игре.
  - Часть 5 - Добавление персонажа и сборка сцены для публикации на web-ресурсе.
- Задание 2.
- Задание 3.
- Выводы.

## Цель работы
Продолжить разработку игры Dragon Picker и подготовить разрабатываемое интерактивное приложение к сборке и публикации.

## Задание 1
### Используя видео-материалы практических работ 1-5 повторить реализацию приведенного ниже функционала:
#### Часть 1 - Создание анимации объектов на сцене.
Ход работы:
1. Сменить название сцены с  _0Scene на _1Scene.
2. Продублировать текущую сцену и переименовать дубликат в _0Scene. Дальнейшая работа будет происходить в _0Scene.
3. Удалить Plane и Score.
4. В Main Camera удалить подключенный скрипт DragonPicker.
5. У объекта Enemy удалить скрипт EnemyDragon.
6. Настроить Transform у объекта DragonMountain.
7. Настроить Transform у объекта Enemy.
8. Создать контроллер для анимации дракона DragonIDLE.
9. Перетянуть анимацию idle01 в контроллер.
10. У объекта Enemy в компоненте Animator изменить контроллер на DragonIDLE.
11. Сохранить и проверить.
12. Загрузить и импортировать из Unity Asset Store пакет Painted HQ 2D Forest Medieval Background.
13. Создать дубликат объекта cloud02 и переместить его в папку _Textures. Затем перетащить дубликат в окно иерархии внутрь объекта Canvas.
14. Настроить Transform у объекта cloud02.
15. Создать облаку анимацию CloudAnimation.
16. Add Proprty -> transform position.
17. Передвинуть второй ключевой кадр. Посередине добавить ключ, сдвинув облако левее.
18. Изменить скорость анимации. CloudAnimation -> speed 0.1.
19. Добавить облаку компонент Rect Transform, то есть настроить "якорь".


#### Часть 2 - Создание стартовой сцены и переключение между ними.
Ход работы:
1. Добавить текст в Canvas. Назвать объект Title.
2. С помощью Rect Transform "заякорить" текст слева сверху. Написать название игры в поле Text Input и поменять размер и цвет шрифта.
3. Создать пустой объект MainMenu.
4. Создать скрипт MainMenu и подключить его к объекту MainMenu.
5. Создать три кнопки PlayButton, OptionButton и QuitButton. Настроить расположение, размер и внешний вид кнопок. Помесить все кнопки в объект MainMenu.
6. У кнопки PlayButton редактировать событие On Click. Закинуть объект MainMenu, а вместо No Function назначить PlayGame.
7. В Build Settings добавить сцену.
8. Проверить, что кнопка Play работает.


#### Часть 3 - Доработка меню и функционала с остановкой игры.
Ход работы:
1. У кнопки QuitButton редактировать событие On Click. Закинуть объект MainMenu, а вместо No Function назначить QuitGame.
2. Сделать копию MainMenu и переименовать в SettingMenu.
3. В SettingMenu сменить имя кнопки QuitButton на BackButton. Остальные кнопки удалить.
4. У кнопки BackButton в событии On Click создать два листа для MainMenu и SettingMenu, в обоих листах вместо No Function назначить SetActive. Убрать галочку у SettingMenu.
5. У кнопки OptionButton в событии On Click создать два листа для MainMenu и SettingMenu, в обоих листах вместо No Function назначить SetActive. Убрать галочку у MainMenu.
6. Проверить, что всё работает.
7. Создать скрипт PauseAndEscape и подключить его к Main Camera в _1Scene.
8. Проверить, что пауза и выход работают.
9. Добавить текстовое сообщение о паузе. В сцене _1Scene добавить объект Text, назвать его Pause. Настроить расположение и внешний вид текста. По умолчанию объект не должен быть на сцене, поэтому нужно убрать галочку
10. В Main Camera в скрипте PauseAndEscape в качестве Panel назначить объект Pause.


#### Часть 4 - Добавление звукового сопровождения в игре.
Ход работы:
1. Загрузить и импортировать из Unity Asset Store пакет Free Orchestral Music Pack.
2. Аудио-файлы Aspiration Woods (Area Theme) и Final Struggle (Boss Theme) переместить в папку _AudioFiles.
3. В сцене _0Scene к MainCamera добавить компонент Audio Source, в качестве AudioClip назначить аудио-файл Aspiration Woods (Area Theme). Включить свойства Play On Awake и Loop.
4. Проверить.
5. В сцене _1Scene к MainCamera добавить компонент Audio Source, в качестве AudioClip назначить аудио-файл AFinal Struggle (Boss Theme). Включить свойства Play On Awake и Loop.
6. Проверить.
7. Удалить папку Free Orchestral Music Pack.
8. Загрузить и импортировать из Unity Asset Store пакет Grenade Sound FX.
9. Переместить аудио-файл Grenade2Short в папку _AudioFiles и переименовать в DragonEggExplosion.
10. К префабу Egg добавить компонент Audio Source, в качестве AudioClip назначить аудио-файл DragonEggExplosion - та аудио-дорожка будет проигрываться при падении яйца на землю. Выключить свойство Play On Awake.
11. Модифицировать скрипт DragonEgg, а именно добавить публичную переменную audioSource и добавить строки кода в метод OnTriggerEnter.
12. Переместить аудио-файл Impact on Snow в папку _AudioFiles и переименовать в DragonEggImpact.
10. К префабу EnergyShield добавить компонент Audio Source, в качестве AudioClip назначить аудио-файл DragonEggImpact - эта аудио-дорожка будет проигрываться при пересечении яйца и энергетического щита. Выключить свойство Play On Awake.
11. Модифицировать скрипт EnergyShield, а именно добавить публичную переменную audioSource и добавить строки кода в метод OnCollisionrEnter.


#### Часть 5 - Добавление персонажа и сборка сцены для публикации на web-ресурсе.
Ход работы:
1. Удалить ненужные ассетпаки, текстуры перетащить в папку _Textures.
2. Скачать модель персонажа с сайта mixamo.com во вкладке Characters. 
3. Во вкладке Animations найти подходящюю анимацию. Загрузить.
4. Скачанный файл поместить в папку _Prefabs и переименовать.
5. Поместить персонажа в _1Scene, настроить компонент Transform.
6. Извлечь текструры.
7. Продублировать анимацию из персонажа, переименовать и переместить в папку _Animations. Включить свойство Loop Time.
8. Создать контроллер анимации, перекинуть в этот контроллер анимацию. Подключить контроллер к персонажу.
9. Добавить точечный источник освещения и настроить его.
10. Собрать проект для платформы WebGL и проверить работу приложения в браузере. Если нужно, подредактировать сцену и пересобрать проект



## Задание 2
### Привести описание того, как происходит сборка проекта проекта под другие платформы. Какие могут быть особенности?
Ход работы:






## Задание 3
### Добавить в меню Option возможность изменения громкости (от 0 до 100%) фоновой музыки в игре.
Ход работы:


 
## Выводы




## Powered by

**BigDigital Team: Denisov | Fadeev | Panov**
