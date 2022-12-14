# Разработка игры и интеграция сервисов в пользовательский интерфейс
Отчет по лабораторной работе #4 выполнила:
- Россихина Ирина Александровна
- РИ-300002

Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | # | 20 |
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

![transform mountain](https://user-images.githubusercontent.com/74662720/200521900-90a527ca-12b7-471c-9f03-f73126121e38.png)

7. Настроить Transform у объекта Enemy.

![transform enemy](https://user-images.githubusercontent.com/74662720/200521951-fc1f5127-e288-427c-8494-c6b2d1f6f9c7.png)

8. Создать контроллер для анимации дракона DragonIDLE и перетянуть анимацию idle01 в контроллер.

![idle01](https://user-images.githubusercontent.com/74662720/200522210-4cf7e154-5d5a-47f6-82f2-953fdf9138ff.png)

9. У объекта Enemy в компоненте Animator изменить контроллер на DragonIDLE.

![изменили контроллер](https://user-images.githubusercontent.com/74662720/200522266-12fb5afd-053e-4513-8777-f2650a3bb810.png)

10. Сохранить и проверить. Теперь дракон стоит рядом с горой в ожидании.

![bandicam 2022-11-07 15-27-57-994](https://user-images.githubusercontent.com/74662720/200522867-e48eaaf3-3be3-4326-9f20-fb0a78f1631d.gif)

11. Загрузить и импортировать из Unity Asset Store пакет Painted HQ 2D Forest Medieval Background.

![Painted HQ 2D Forest Medieval Background](https://user-images.githubusercontent.com/74662720/200523122-305c8b25-e288-40da-80c4-d153ed763a15.png)

12. Создать дубликат объекта cloud02 и переместить его в папку _Textures. Затем перетащить дубликат в окно иерархии внутрь объекта Canvas.

![облако и там и тут](https://user-images.githubusercontent.com/74662720/200523166-3091abd6-bbb2-453b-a187-b8610c8f1c46.png)

13. Настроить Transform у объекта cloud02.

![transform cloud](https://user-images.githubusercontent.com/74662720/200523204-a239f126-4cc6-4029-b609-aa3e625ac933.png)

14. Создать облаку анимацию CloudAnimation и подключить её к cloud02.
15. Add Proprty -> transform position. Передвинуть второй ключевой кадр. Посередине добавить ключ, сдвинув облако в сторону.

![bandicam 2022-11-07 15-46-59-646](https://user-images.githubusercontent.com/74662720/200524003-2849705e-0a78-48ca-84cb-56f2c6105e86.gif)

16. Изменить скорость анимации. CloudAnimation -> speed 0.02.

![сменили скорость](https://user-images.githubusercontent.com/74662720/200523746-130c262d-714e-427e-b341-623e18024fd6.png)

17. Добавить облаку компонент Rect Transform, то есть настроить "якорь".

![rect transform](https://user-images.githubusercontent.com/74662720/200523288-d8e90a93-798c-47cd-8b9a-bbfe8c927deb.png)


#### Часть 2 - Создание стартовой сцены и переключение между ними.
Ход работы:
1. Добавить текст в Canvas. Назвать объект Title.

![текст](https://user-images.githubusercontent.com/74662720/200524970-16c6f087-1d98-4631-beec-f3d4a6f67a35.png)

3. С помощью Rect Transform "заякорить" текст слева сверху. Написать название игры в поле Text Input и поменять размер и цвет шрифта.

![настроили заголовок](https://user-images.githubusercontent.com/74662720/200524992-dd2b692b-e484-4849-a91b-6589e82cad29.png)

5. Создать пустой объект MainMenu.
6. Создать скрипт MainMenu и подключить его к объекту MainMenu.

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.SceneManagement;

public class MainMenu : MonoBehaviour
{
    public void PlayGame()
    {
        SceneManager.LoadScene(SceneManager.GetActiveScene().buildIndex + 1);
    }

    public void QuitGame()
    {
        Application.Quit();
    }
}
```

8. Создать три кнопки PlayButton, OptionButton и QuitButton. Настроить расположение, размер и внешний вид кнопок. Поместить все кнопки в объект MainMenu.

![кнопки в главном меню](https://user-images.githubusercontent.com/74662720/200538550-7c53be2d-53d7-49f8-bee7-583cda0a4da9.png)

10. У кнопки PlayButton редактировать событие On Click. Закинуть объект MainMenu, а вместо No Function назначить PlayGame.

![собыитие](https://user-images.githubusercontent.com/74662720/200538685-bb1c16ca-9d1f-48c6-bba9-770e548611fe.png)

13. Проверить, что кнопка Play работает.

![bandicam 2022-11-07 16-55-29-401](https://user-images.githubusercontent.com/74662720/200539394-cb6a2e0d-16c3-43e1-9f2c-eaee8a26255f.gif)


#### Часть 3 - Доработка меню и функционала с остановкой игры.
Ход работы:
1. У кнопки QuitButton редактировать событие On Click. Закинуть объект MainMenu, а вместо No Function назначить QuitGame.

![событие quit](https://user-images.githubusercontent.com/74662720/200539506-52fa63ce-98f6-4265-824d-22512696419f.png)

2. Сделать копию MainMenu и переименовать в SettingMenu.
3. В SettingMenu сменить имя кнопки QuitButton на BackButton. Остальные кнопки удалить.

![кнопка back](https://user-images.githubusercontent.com/74662720/200539574-af7ecadd-7689-4c83-9f74-7e3612853514.png)

4. У кнопки BackButton в событии On Click создать два листа для MainMenu и SettingMenu, в обоих листах вместо No Function назначить SetActive. Убрать галочку у SettingMenu.

![backbutton set active](https://user-images.githubusercontent.com/74662720/200539614-bf31577b-0c3f-4401-ac7c-d264d27fe028.png)

5. У кнопки OptionButton в событии On Click создать два листа для MainMenu и SettingMenu, в обоих листах вместо No Function назначить SetActive. Убрать галочку у MainMenu.

![optionbutton set active](https://user-images.githubusercontent.com/74662720/200539677-abfc346b-fa9a-4b26-963b-b543a877e8f8.png)

6. Проверить, что переключение между главным меню и настройками работает.

![bandicam 2022-11-08 09-30-12-483](https://user-images.githubusercontent.com/74662720/200540246-a1ec751b-e7b8-4e43-a378-d4962e8e9f94.gif)

7. Создать скрипт PauseAndEscape и подключить его к Main Camera в _1Scene.

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.SceneManagement;

public class PauseAndEscape : MonoBehaviour
{
    private bool paused = false;
    public GameObject panel;

    void Update()
    {
        if (Input.GetKeyDown(KeyCode.Space))
        {
            if(!paused)
            {
                Time.timeScale = 0;
                paused = true;
                panel.SetActive(true);
            }

            else
            {
                Time.timeScale = 1;
                paused = false;
                panel.SetActive(false);
            }
        }

        if (Input.GetKeyDown(KeyCode.Escape))
        {
            SceneManager.LoadScene(SceneManager.GetActiveScene().buildIndex - 1);
        }
    }
}
```
8. Добавить текстовое сообщение о паузе. В сцене _1Scene добавить объект Text, назвать его Pause. Настроить расположение и внешний вид текста.
9. В Main Camera в скрипте PauseAndEscape в качестве Panel назначить объект Pause. Проверить работу паузы и выхода в главное меню.

![bandicam 2022-11-08 15-35-52-230](https://user-images.githubusercontent.com/74662720/200543184-e63a4ad3-cb3d-4878-adf2-56ab9f803cb1.gif)


#### Часть 4 - Добавление звукового сопровождения в игре.
Ход работы:
1. Загрузить и импортировать из Unity Asset Store пакет Free Orchestral Music Pack.

![Free Orchestral Music Pack](https://user-images.githubusercontent.com/74662720/200543439-7a0f2163-94ec-4e90-af4a-964a2d71a773.png)

2. Аудио-файлы Aspiration Woods (Area Theme) и Final Struggle (Boss Theme) переместить в папку _AudioFiles.
3. В сцене _0Scene к MainCamera добавить компонент Audio Source, в качестве AudioClip назначить аудио-файл Aspiration Woods (Area Theme). Включить свойства Play On Awake и Loop.

![maincamera 0scene](https://user-images.githubusercontent.com/74662720/200543541-ca305d53-3065-40ab-a5bd-de68975c9547.png)

4. В сцене _1Scene к MainCamera добавить компонент Audio Source, в качестве AudioClip назначить аудио-файл Final Struggle (Boss Theme). Включить свойства Play On Awake и Loop.

![maincamera 1scene](https://user-images.githubusercontent.com/74662720/200543579-5e81329f-9661-4fab-8c84-d9413aab79f1.png)

5. Удалить папку Free Orchestral Music Pack.
6. Загрузить и импортировать из Unity Asset Store пакет Grenade Sound FX.

![Grenade Sound FX](https://user-images.githubusercontent.com/74662720/200543627-c128b646-170e-4b2e-803a-604ce1456264.png)

7. Переместить аудио-файл Grenade7Short в папку _AudioFiles и переименовать в DragonEggExplosion.
8. К префабу Egg добавить компонент Audio Source, в качестве AudioClip назначить аудио-файл DragonEggExplosion - эта аудио-дорожка будет проигрываться при падении яйца на землю. Выключить свойство Play On Awake.

![назначили взрыв яйцу](https://user-images.githubusercontent.com/74662720/200543692-105d8c36-cfac-473d-81d2-4f08a38da662.png)

9. Модифицировать скрипт DragonEgg, а именно добавить публичную переменную audioSource 
```c#
public AudioSource audioSource;
```
и добавить строки кода в метод OnTriggerEnter.

```c#
audioSource = GetComponent<AudioSource>();
audioSource.Play();
```
10. Переместить аудио-файл Impact on Snow в папку _AudioFiles и переименовать в DragonEggImpact.
11. К префабу EnergyShield добавить компонент Audio Source, в качестве AudioClip назначить аудио-файл DragonEggImpact - эта аудио-дорожка будет проигрываться при пересечении яйца и энергетического щита. Выключить свойство Play On Awake.

![назначили звук щиту](https://user-images.githubusercontent.com/74662720/200543793-da587046-0325-4868-b80f-7a4a18e46fc2.png)

12. Модифицировать скрипт EnergyShield, а именно добавить публичную переменную audioSource и добавить строки кода в метод OnCollisionrEnter (см. код в пункте 9).


#### Часть 5 - Добавление персонажа и сборка сцены для публикации на web-ресурсе.
Ход работы:
1. Удалить ненужные ассетпаки, текстуры перетащить в папку _Textures.
2. На сайте [mixamo.com](https://www.mixamo.com/) выбрать персонажа и анимацию. Загрузить. 

![выбрала позу](https://user-images.githubusercontent.com/74662720/200545293-dbe63456-80e1-4c48-bce6-1b3f890cbb6f.png)

3. Скачанный файл поместить в папку _Prefabs и переименовать.

![перс в папке](https://user-images.githubusercontent.com/74662720/200545316-ef391f6d-05f8-4c32-9fd9-e3904e004d80.png)

4. Поместить персонажа в _1Scene, настроить компонент Transform.

![transform withc](https://user-images.githubusercontent.com/74662720/200545347-71d004cf-f3bf-4be4-967a-80cc1b76f6a5.png)

5. Извлечь текструры.
6. Продублировать анимацию из персонажа, переименовать и переместить в папку _Animations. Включить свойство Loop Time.

![извлекли переименовали зациклили](https://user-images.githubusercontent.com/74662720/200545392-36e7d577-969d-4b22-a9f9-2948673d0b9b.png)

7. Создать контроллер анимации, перекинуть в этот контроллер анимацию.

![создали контроллер и поместили анимацию туда](https://user-images.githubusercontent.com/74662720/200545439-6ebad58a-4978-4977-afbf-5bbeb8b92a00.png)

8. Подключить контроллер к персонажу.

![контроллер подключён к персу](https://user-images.githubusercontent.com/74662720/200545453-4a6063d3-7fc2-4426-a211-d4c94c0d5fa1.png)

9. Добавить точечный источник освещения и настроить его.

![добавили точку света](https://user-images.githubusercontent.com/74662720/200545466-e3a46e8e-a6c7-4986-abc4-89fdbd8ac302.png)

10. Собрать проект для платформы WebGL и проверить работу приложения в браузере.

https://user-images.githubusercontent.com/74662720/200545611-f63f7393-5ff8-4997-a668-1dcaf448fe04.mp4


## Задание 3
### Добавить в меню Option возможность изменения громкости (от 0 до 100%) фоновой музыки в игре.
Ход работы:
1. В SettingMenu добавить слайдер и текст. Настроить расположение и размер.

![добавили слайдер и подпись](https://user-images.githubusercontent.com/74662720/200547523-5c739f8f-ca30-4747-bb10-ce15fd3da249.png)

2. По умолчанию Value принимает значение 1. Добавить событие. В качестве объекта назначить Main Camera, вместо No Function назначить AudioListener.volume.

![событие](https://user-images.githubusercontent.com/74662720/200548334-3ce6ab56-d17c-4b9b-85fa-b7942bdd20ca.png)

3. Проверить работу бегунка.

https://user-images.githubusercontent.com/74662720/200549047-073837d8-3bcf-411f-8f1a-71e072256625.mp4

 
## Выводы
В ходе лабораторной работы была продолжена разработка игры Dragon Picker. Была создана стартовая сцена с главным меню. Также появилась возможность поставить игру на паузу и выйти из игры в главное меню. Добавлены фоновая музыка и звуковые эффекты, которые можно изменить в главном меню. В приложение был включён персонаж. Большинство этих модификаций было сделано для более объёмного восприятия игры.


## Powered by

**BigDigital Team: Denisov | Fadeev | Panov**
