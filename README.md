Работа #3 - Механика тряпичной куклы в Unity
Отчет по лабораторной работе #3 выполнил(а):
•	Дюпин Никита Александрович
•	РИ-320936
•	АТ-09
Цель работы: освоить создание тряпичной куклы Ragdoll на движке Unity

 ![image](https://github.com/user-attachments/assets/2352a4da-d01f-481c-9302-d9c3abb16698)

Рекомендуемые источники для изучения:
1.	Collider Unity Documentation
2.	Тема Ragdoll в материалах лекции
Задания к работе
Задание 1 Создание механики тряпичной куклы
1.1 Скачайте любую Humanoid-модель с сайта Mixamo.com в формате FBX for Unity. Можете выбрать сразу модель с анимацией, либо скачать анимацию позднее:
  	
 ![image](https://github.com/user-attachments/assets/fc2f23d8-6b4b-4994-bf5b-522ceab0dbdc)

1.2 Добавьте модель в проект и на сцену Unity. Работает простое перетаскивание скачанной модели сначала в папку Project Unity, и далее – на сцену.
1.3 При добавлении на сцену модель будет белого цвета. Это происходит из-за отсутствия текстур. Текстуры в файле .fbx есть, но их нужно извлечь, для этого кликните по .fbx файлу и в окне Inspector выбираем Materials - Extract Textures. Появляется окно «Normal Map Settings» - нажимаем «Fix Now». Здесь выводится информация о том, что нужно правильно интерпретировать настройки карт нормали.
Скачал, добавил Humanoid-модель на сцену и извлёк текстуры

 ![image](https://github.com/user-attachments/assets/6121edfc-70c9-4a82-a357-49c224b19809)

1.4 В окне Hierarchy развернем персонажа: ALT (Option) + CLICK по нему. Так будут развернуты все вложенности. Чтобы сделать Ragdoll, нужно выделить каждую часть тела и назначить на нее серию компонентов: Rigidbody + Collider + Joint (шарнир). Для того чтобы сделать это в автоматическом режиме перейдите во вкладку GameObject -> 3D Object -> Ragdoll (инструмент создания тряпичной куклы).
Окно иерархии персонажа

 ![image](https://github.com/user-attachments/assets/bf695082-380d-4621-8723-575592d72a53)

1.5 Открывается окно со слотами, которое нужно наполнить частями тела персонажа (перетаскиванием из окна Hierarchy в окно Create Ragdoll). На те части, которых нет в списке - Rigidbody не назначается. В нижней части указывается Total Mass - вес тела, который будет распределен между всеми частями, пропорционально их размерам. Например, в нашем случае ставим вес тела 60 кг:

 ![image](https://github.com/user-attachments/assets/bec6d3bc-ae7b-4a20-9992-0b331c2f6455)

1.6 Завершите создание тряпичной куклы, подтвердив действие в окне Create Ragdoll. Если выделить самый верх иерархии (в окне Hiararchy) персонажа - то вы увидите автоматически созданные коллайдеры:

 ![image](https://github.com/user-attachments/assets/0e48c322-99a4-45ec-9274-a3a50bdd52f9)

Автоматически созданные коллайдеры

 ![image](https://github.com/user-attachments/assets/c6655639-f950-46c9-9695-997afef92956)

1.7 Запустите сцену. Что не так с механикой? Внесите исправления в автоматически назначенные компоненты, чтобы механика падения тряпичной куклы выглядела более натурально. Дайте развернутый ответ, что требовалось исправить:
В работе механики наблюдалась следующая проблема: ноги персонажа резко разъезжались в стороны из-за больших размеров коллайдера (они соприкасались друг с другом, из-за чего происходило резкое выталкивание одного коллайдера из пространства другого). Данная проблема решилась путём изменения радиуса (выставил значение в 0.05) коллайдера у объектов, относящихся к ногам (mixamorig:LeftUpLeg, mixamorig:LeftLeg, mixamorig:RightUpLeg, mixamorig:RightLeg).
Изменённый радиус у коллайдеров ног на примере LeftUpLeg

 ![image](https://github.com/user-attachments/assets/58367242-7cb4-4421-8fe1-ef9492f214db)

Задание 2 Переход между Ragdoll и анимацией персонажа
1.8 Скачайте с сайта Mixamo скелет с анимацией какого-либо движения (если не сделали этого ранее). И добавьте в проект Unity (перетаскиванием в окно Project). Разверните скачанный файл (нажав стрелку рядом с моделью). Файл с анимацией выглядит как треугольник. Извлеките его из пакета, нажав Ctrl+D. Выберите извлеченный файл анимации и сделай так, чтобы она была зациклена (клик Loop Time в окне Inspector)

 ![image](https://github.com/user-attachments/assets/b34312e7-ef56-46ac-80b5-0909b2c9c1e3)

пакет модели со скелетом для анимации

 ![image](https://github.com/user-attachments/assets/d39aaaa9-8bdf-4f72-8b8d-336638a0382c)

1.9 Правильный порядок создания анимации выглядит так:
•	создайте контроллер анимации (клик ПКМ в окне Project - Create - Animator Controller)
•	созданный Animator Controller назначьте на модель персонажа на сцене
•	откройте созданный контроллер анимации (дважды кликнув по нему)
•	переместите анимацию из предыдущего пункта в контроллер анимации

 ![image](https://github.com/user-attachments/assets/36edac25-8e89-48d1-b0d1-6fdfca75e7ff)

Создал контроллер анимации
 ![image](https://github.com/user-attachments/assets/9f6e3684-d807-47b0-8709-0f89b73f2eea)

Назначил созданный контроллер анимации на персонажа

 ![image](https://github.com/user-attachments/assets/338b887a-6238-4a04-bc14-be65c82615f2)

Открыл созданный контроллер анимации и переместил анимацию из предыдущего пункта в него

 ![image](https://github.com/user-attachments/assets/6578a4ae-77ca-4199-9508-7499c65fc625)

1.10 При запуске сцены анимация в вашем случае выглядит забагованной. Как вы считаете, почему это происходит? Дайте развернутый ответ:
Решил провести небольшой эксперимент: так как в материалах к работе в качестве примера используется две разных модели (одна в T-позе, вторая – в позе для начала движения); решил для сравнения поставить рядом две модели: одна в T-позе, другая – которая шла со скелетом анимации (на рисунке слева, находится в позе готовности к началу движения). Та модель, что стоит слева – двигается нормально без каких-либо перебоев и глюков. Поэтому, мне кажется, что всё дело в начальной позе модели перед запуском анимации (возможно идёт какой-то сбой/недопонимание в программе из-за разницы координат модели).
Upd1: после написания и подключения скрипта для включения режима Ragdoll по нажатию клавиши, анимация стала плавной и перестала баговать, не знаю, с чем это может быть связано… либо с тем, что аниматор начинает использоваться где-то ещё помимо модели, но при отключении скрипта от модели, анимация по прежнему продолжает плавно воспроизводиться.
Upd2: поиграв с данными массива allRigidbodys понял, что при добавлении в него элементов анимация становится плавной и перестаёт баговать, получается, что элементы, добавленные в этот массив перестают быть необработанными или что-то в этом духе, потому что даже если в массиве будет всего одни-два элемента, анимация всё равно будет багованная; иначе говоря, весь этот учёт элементов частей модели в массиве каким-то образом влияет на воспроизведение анимации.
Две различные модели (T-поза и поза готовности к движению).

 ![image](https://github.com/user-attachments/assets/0471a4cb-390b-4381-b15c-ca41b59551d7)

1.11 Создадим скрипт файл RagdollControl.cs, который будет отключать анимацию и включать механику тряпичной куклы. Описание скрипта:
•	Скрипт RagdollControl.cs навешивается на персонажа. Скрипт будет содержать две переменные:
•	Animator для управления анимацией
•	Массив Rigidbodies, который будет отключаться
•	Когда скрипт будет написан и подключен, в поле переменной Animator подключается Animator в пределах поля Inspector.
•	Массив All Rigidbodies нужно заполнить всеми rigid bodies модели: чтобы это сделать удобно нужно нажать замок на инспекторе персонажа.
•	В окне иерархии выделить все внутренности персонажа (через shift) и перетащить на массив в инспекторе.
•	Так будут добавлены все rigidbodies этого персонажа.
Содержание скрипта, отключающего анимацию показано ниже:
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class ScriptRagdollOff : MonoBehaviour
{
    public Animator animator;
    public Rigidbody [] allRigidbodies;

    private void Awake()
    {
        for (int i = 0; i < allRigidbodies.Length; i++)
        {
            allRigidbodies[i].isKinematic = true;
        }
    }

    void Update()
    {
        if (Input.GetKeyDown(KeyCode.Space))
        {
            MakePhysics();
        }
    }

    public void MakePhysics()
    {
        animator.enabled = false;
        for (int i = 0; i < allRigidbodies.Length; i++)
        {
            allRigidbodies[i].isKinematic = false;
        }
    }
}
Создал скрипт RigdollControl, применил его на персонаже и добавил в массив нужные части персонажа

 ![image](https://github.com/user-attachments/assets/0aa2e4bc-4b98-451e-a9d3-8b242f77f2ae)

1.12 Что произойдет, если не все Rigidbody тряпичной куклы будут отключены? Дайте развернутый ответ.

Мне кажется, что, если не все Rigidbody тряпичной куклы будут отключены, произойдёт следующее: те части, у которых Rigidbody не будут отключены, продолжат отыгрывать анимацию, а те, у которых Rigidbody отключён – перестанут двигаться и будут просто болтаться за теми частями, которые до сих пор находятся в движении.
1.13 Напишите развернутый вывод по проделанной работе. Как знания свойств компонентов Collider помогут в создании интерактивных приложений, игр и симуляторов?

В ходе данной лабораторной работы были изучены основные способы работы с таким компонентом как Ragdoll. Также была проведена работа по скачиванию и добавлению 3D-моделей и их анимаций в проект Unity. С помощью скрипта была настроена функция включения Ragdoll’а по нажатию указанной клавиши. В дальнейшем данные знания могут помочь в создании различных механик, например убийства персонажа, но уже не при нажатии какой-то клавиши, а при пересечении коллайдеров двух моделей (например коллайдер головы и коллайдер пули); по нажатии на клавишу можно сделать следующую механику: проанализировать, в каком направлении и как именно будет “падать” модель, если на неё применить Ragdoll, можно будет создать интересные и смешные анимации падения куклы.

