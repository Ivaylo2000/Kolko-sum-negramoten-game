# Колко съм неграмотен?

**Образователна мултиплейър игра с въпроси от матури.**  
**An educational multiplayer quiz built around Bulgarian matriculation exams.**

### [Играй / Play](https://kolko-sum-negramoten.vercel.app/)

React · TypeScript · Node.js · Express · Socket.IO · Redis

Разгънете предпочитания език. / Expand your preferred language.

<details>
<summary><strong>🇧🇬 Български</strong></summary>

## За проекта

„Колко съм неграмотен?“ е full-stack уеб приложение, което превръща преговора за матура в състезание между приятели. Играчите отговарят на едни и същи въпроси в реално време, сравняват отговорите си и събират точки.

Играта е предназначена за **2–5 участници** и се използва директно в браузъра, без регистрация. Интерфейсът и въпросите са на български език.

## Как се играе

1. **Създаване на стая.** Домакинът въвежда псевдоним, избира БЕЛ, География и икономика или двата предмета, както и 5, 10, 15, 20 или 30 въпроса.
2. **Покана към приятели.** Останалите се присъединяват чрез линк за покана или код на стаята и въвеждат свой псевдоним.
3. **Отговор на въпрос.** Всеки избира отговор и може да го променя, докато не го потвърди. Времето е 30, 60 или 120 секунди според въпроса.
4. **Преглед на рунда.** Когато всички потвърдят или времето изтече, се показват верният отговор, изборите на участниците и обновените точки.
5. **Крайно класиране.** Домакинът продължава към следващия въпрос. След последния се показва класирането и може да започне нова игра.

Всеки верен отговор носи **1 точка**. При задачи с няколко празни места всички избори трябва да са правилни, за да се получи точката. При равни точки играчите споделят място в класирането.

## Основни възможности

- Стаи за игра с линкове за покана и синхронизация в реално време.
- Случайни въпроси от избраните предмети, без повторение в рамките на една игра.
- Въпроси с избираем отговор и задачи с няколко групи от варианти за попълване на празни места.
- Таймер за всеки въпрос и автоматично приключване на рунда при изтичането му.
- Възстановяване на участието при презареждане или кратка загуба на връзка. Мястото, точките и потвърденият отговор се пазят до **5 минути**, а играта се поставя на пауза.
- Обозначение на източника, например **ДЗИ 18/05/22**, когато датата на изпита е известна.
- Интерфейс за използване на компютър и телефон.

## Технологии

| Област                  | Технологии                                        | Приложение                                                                       |
| ----------------------- | ------------------------------------------------- | -------------------------------------------------------------------------------- |
| Потребителски интерфейс | React, TypeScript, Vite, SCSS                     | Компоненти за стаите, настройките, въпросите и резултатите                       |
| Сървър и комуникация    | Node.js, Express, Socket.IO                       | Управление на играта и обмен на събития в реално време                           |
| Състояние на играта     | Redis, Upstash                                    | Съхранение на стаи и възстановяване на сесии                                     |
| Споделена логика        | TypeScript, npm workspaces                        | Общи типове, настройки и правила между клиента и сървъра                         |
| Подготовка на въпросите | Python, PyMuPDF, JSON                             | Извличане на задачи от PDF и подготовка на банките с въпроси                     |
| Проверки                | Node.js test runner, tsx, jsdom, ESLint, Prettier | Тестове на игровата логика и React компонентите, статични проверки и форматиране |
| Публикуване             | Vercel, Railway                                   | Работещи онлайн версии на приложението                                           |

## Как работи системата

Началната страница е статичен HTML, а стаите и самата игра са изградени с React. Клиентът комуникира със сървъра чрез Socket.IO, така че въпросите, отговорите и резултатите се обновяват за всички участници в стаята.

Сървърът управлява таймерите, потвърждаването на отговорите, точкуването и правата на домакина. Верните отговори се изпращат към участниците при прегледа на рунда. Redis съхранява състоянието на стаите, а атомарните актуализации предпазват от загуба на отговори и двойно начисляване на точки при едновременни заявки.

Автоматизираните проверки покриват избора на предмети, игровите рундове, таймерите, точкуването, повторните заявки, прекъсването и възстановяването на връзката, както и основните взаимодействия с интерфейса.

## Откъде са въпросите

Използвани са изпитни материали и официални ключове за отговори, публикувани от **Министерството на образованието и науката (МОН)**. Задачите са преобразувани в структуриран JSON и са подбрани за текстовия формат на играта.

| Предмет                     | Брой въпроси |
| --------------------------- | -----------: |
| Български език и литература |          364 |
| География и икономика       |        1 157 |
| **Общо**                    |    **1 521** |

Банката включва самостоятелни задачи с варианти за отговор. Задачите, изискващи липсваща карта, изображение, общ текст за четене или свободна писмена разработка, са изключени. Данните в по-старите изпитни задачи се отнасят за контекста на съответния изпит.

Официални източници:

- [ДЗИ по български език и литература — МОН](https://mon.bg/obshto-obrazovanie/darzhavni-zrelostni-izpiti-dzi/izpitni-materiali-za-dzi-po-predmeti/balgarski-ezik/)
- [ДЗИ по география и икономика — МОН](https://www.mon.bg/obshto-obrazovanie/darzhavni-zrelostni-izpiti-dzi/izpitni-materiali-za-dzi-po-predmeti/geografiya-i-ikonomika/)

## Изпробване на играта

**[Отвори играта](https://kolko-sum-negramoten.vercel.app/game/)** и покани приятел. Мултиплейърът може да се изпробва и в два отделни таба на браузъра с различни псевдоними.

Изходният код се поддържа в частно хранилище. Това описание е подготвено за публично представяне на проекта като част от портфолио.

</details>

<details>
<summary><strong>🇬🇧 English</strong></summary>

## About the project

“Колко съм неграмотен?” is a full-stack web application that turns exam revision into a multiplayer quiz between friends. Players answer the same questions in real time, compare their answers, and earn points.

The game supports **2–5 players** and runs directly in the browser without registration. The game interface and question content are in Bulgarian.

## How to play

1. **Create a room.** The host enters a nickname, selects Bulgarian Language and Literature, Geography and Economics, or both subjects, and chooses 5, 10, 15, 20, or 30 questions.
2. **Invite friends.** Other players join through an invitation link or room code and enter their own nicknames.
3. **Answer a question.** Players can change their selection until they confirm it. Each question has a time limit of 30, 60, or 120 seconds.
4. **Review the round.** Once everyone confirms or time runs out, the correct answer, each player's selection, and updated scores are revealed.
5. **See the final ranking.** The host advances through the questions. After the final round, players see the ranking and can return to the lobby for another game.

Each correct answer earns **1 point**. For tasks with multiple blanks, every selection must be correct to earn the point. Players with equal scores share the same rank.

## Features

- Game rooms with invitation links and real-time synchronisation.
- Random questions from the selected subjects, without repeats within a game.
- Multiple-choice questions and tasks with several groups of options for filling blanks.
- Individual question timers and automatic round completion when time runs out.
- Session recovery after a refresh or brief connection loss. The player's place, score, and confirmed answer are reserved for up to **5 minutes**, while the game pauses.
- Source labels such as **ДЗИ 18/05/22** when the exam date is known.
- An interface designed for desktop and mobile use.

## Technology stack

| Area                      | Technologies                                      | Purpose                                                             |
| ------------------------- | ------------------------------------------------- | ------------------------------------------------------------------- |
| Frontend                  | React, TypeScript, Vite, SCSS                     | Components for rooms, settings, questions, and results              |
| Backend and communication | Node.js, Express, Socket.IO                       | Game management and real-time event exchange                        |
| Game state                | Redis, Upstash                                    | Room storage and session recovery                                   |
| Shared logic              | TypeScript, npm workspaces                        | Shared types, settings, and rules across client and server          |
| Question preparation      | Python, PyMuPDF, JSON                             | Extracting PDF tasks and preparing structured question banks        |
| Quality checks            | Node.js test runner, tsx, jsdom, ESLint, Prettier | Game logic and React component tests, static checks, and formatting |
| Deployment                | Vercel, Railway                                   | Live deployments of the application                                 |

## How the system works

The landing page is static HTML, while rooms and gameplay use React. The client communicates with the backend through Socket.IO, keeping questions, answers, and results synchronised across participants.

The server controls timers, answer confirmation, scoring, and host permissions. Correct answers are sent to players during round review. Redis stores room state, and atomic updates protect against lost answers and duplicate scoring when requests arrive simultaneously.

Automated checks cover subject selection, game rounds, timers, scoring, duplicate requests, connection recovery, and key interface interactions.

## Question sources

The questions use exam materials and official answer keys published by the **Bulgarian Ministry of Education and Science (MON)** for the State Matriculation Exams, known as **DZI**. Tasks are converted into structured JSON and selected for the game's text-based format.

| Subject                           | Questions |
| --------------------------------- | --------: |
| Bulgarian Language and Literature |       364 |
| Geography and Economics           |     1,157 |
| **Total**                         | **1,521** |

The banks contain standalone tasks with answer options. Tasks requiring an unavailable map, image, shared reading passage, or extended written response are excluded. Information in older exam questions retains the context of the original exam.

Official sources:

- [Bulgarian Language and Literature exams — MON](https://mon.bg/obshto-obrazovanie/darzhavni-zrelostni-izpiti-dzi/izpitni-materiali-za-dzi-po-predmeti/balgarski-ezik/)
- [Geography and Economics exams — MON](https://www.mon.bg/obshto-obrazovanie/darzhavni-zrelostni-izpiti-dzi/izpitni-materiali-za-dzi-po-predmeti/geografiya-i-ikonomika/)

## Try the game

**[Open the game](https://kolko-sum-negramoten.vercel.app/game/)** and invite a friend. You can also try the multiplayer flow in two separate browser tabs with different nicknames.

The source code is maintained in a private repository. This document is intended as a public portfolio overview of the project.

</details>
