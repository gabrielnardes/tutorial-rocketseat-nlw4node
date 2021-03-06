<p align="center">
	<h1 align="center">NLW#4 - Node.js</h1>
</p>

## 💬 What is it?

It is a email sender application, which sends surveys to users and calculates the NPS (Net Promoter Score) based on the surveys answers.

## 🤔 Why did you made this project?

I wanted to improve and practice my skills in Node.js.

## 🛠️ What technologies did you use?

-   Typescript
-   Node.js
-   Express.js
-   Handlebars
-   Jest
-   SQLite
-   TypeORM

## 🕹️ How to execute?

Requirements

-   Node.js
-   Yarn

Clone this repository

```
git clone https://github.com/gabrielnardes/tutorial-rocketseat-nlw4.git
```

Install the dependencies

```
yarn install
```

Set your package.json accordingly to your OS:

Windows

```
"test": "set NODE_ENV=test&&jest -i"
```

Linux

```
"test": "NODE_ENV=test jest -i"
```

Run the application

```
yarn dev
```

You will be dealing with JSON to interact with the application. The idea is to:

1. Create users
1. Create a survey
1. Send the survey to users's email
1. The users answers the survey
1. You check your NPS score

To exemplify this:

1. Create users at `POST http://localhost:3333/users`

```
{
  "name": "Isaac Newton",
  "email": "isaac@newton.com"
}
```

2. Create a survey at `POST http://localhost:3333/surveys`

```
{
  "title": "Client satisfaction survey",
  "description": "How likely are you to buy from us again?"
}
```

And get it's id from `GET http://localhost:3333/surveys`

```
[
  {
    "id": "1a181ac7-c432-47ba-a1cb-37d0dd8ceb63",
    "title": "Client satisfaction survey",
    "description": "How likely are you to buy from us again?",
    "created_at": "2021-03-01T00:28:19.000Z"
  }
]
```

3. Send the survey to users's email at `POST http://localhost:3333/sendMail`

```
{
  "email": "isaac@newton.com",
  "survey_id": "1a181ac7-c432-47ba-a1cb-37d0dd8ceb63"
}
```

4. The user answers the survey

![](/imgs/npsSurvey.png)

5. You check your NPS score at `GET http://localhost:3333/nps/:survey_id`

```
{
  "detractors": 2,
  "promoters": 3,
  "passives": 1,
  "totalAnswers": 6,
  "nps": 16.67
}
```
