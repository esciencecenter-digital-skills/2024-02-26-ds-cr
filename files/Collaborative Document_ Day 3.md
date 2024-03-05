![](https://i.imgur.com/iywjz8s.png)


# Collaborative Document: Day 3

2024-02-26--29 Good Practices in Research Software Development Day 3.

Welcome to The Workshop Collaborative Document.

This Document is synchronized as you type, so that everyone viewing this page sees the same text. This allows you to collaborate seamlessly on documents.


----------------------------------------------------------------------------

##  🫱🏽‍🫲🏻 Code of Conduct

Participants are expected to follow these guidelines:
* Use welcoming and inclusive language.
* Be respectful of different viewpoints and experiences.
* Gracefully accept constructive criticism.
* Focus on what is best for the community.
* Show courtesy and respect towards other community members.
 
## 🎓 Certificate of attendance

If you attend the full workshop you can request a certificate of attendance by emailing to training@esciencecenter.nl .

## ⚖️ License

All content is publicly available under the Creative Commons Attribution License: [creativecommons.org/licenses/by/4.0/](https://creativecommons.org/licenses/by/4.0/).

## 🙋Getting help

To ask a question, raise your hand in zoom. Click on the icon labeled "Reactions" in the toolbar on the bottom center of your screen,
then click the button 'Raise Hand ✋'. For urgent questions, just unmute and speak up!

You can also ask questions or type 'I need help' in the chat window and helpers will try to help you.
Please note it is not necessary to monitor the chat - the helpers will make sure that relevant questions are addressed in a plenary way.
(By the way, off-topic questions will still be answered in the chat)


## 🖥 Workshop website

[link](https://esciencecenter-digital-skills.github.io/2024-02-26-ds-cr/)

🛠 Setup

[link](https://esciencecenter-digital-skills.github.io/2024-02-26-ds-cr/#setup)

## 👩‍🏫👩‍💻🎓 Instructors

Sander van Rijn, Sven van der Burg, Olga Lyashevska

## 🧑‍🙋 Helpers

Dani Bodor

## 🗓️ Agenda
| Time | Topic |
|--:|:---|
| 9:00 | Welcome and icebreaker |
| 9:15 | Writing modular code |
| 10:15 | Coffee break |
| 10:30 | Writing modular code |
| 11:30 | Coffee break |
| 11:45 | Documentation |
| 12:45 | Wrap-up |
| 13:00 | END |


## Welcome
- Questions about yesterday?
- Feedback from yesterday


## 🔧 Exercises


### Exercise: Modularity

Look at the following code.

Extract functions from it without changing its functionality.

What functions did you create?
What strategies did you use to identify them?

Share your answers in the collaborative document

```python=
def convert_temperature(temperature, unit):
    if unit == "F":
        # Convert Fahrenheit to Celsius
        celsius = (temperature - 32) * (5 / 9)
        if celsius < -273.15:
            # Invalid temperature, below absolute zero
            return "Invalid temperature"
        else:
            # Convert Celsius to Kelvin
            kelvin = celsius + 273.15
            if kelvin < 0:
                # Invalid temperature, below absolute zero
                return "Invalid temperature"
            else:
                fahrenheit = (celsius * (9 / 5)) + 32
                if fahrenheit < -459.67:
                    # Invalid temperature, below absolute zero
                    return "Invalid temperature"
                else:
                    return celsius, kelvin
    elif unit == "C":
        # Convert Celsius to Fahrenheit
        fahrenheit = (temperature * (9 / 5)) + 32
        if fahrenheit < -459.67:
            # Invalid temperature, below absolute zero
            return "Invalid temperature"
        else:
            # Convert Celsius to Kelvin
            kelvin = temperature + 273.15
            if kelvin < 0:
                # Invalid temperature, below absolute zero
                return "Invalid temperature"
            else:
                return fahrenheit, kelvin
    elif unit == "K":
        # Convert Kelvin to Celsius
        celsius = temperature - 273.15
        if celsius < -273.15:
            # Invalid temperature, below absolute zero
            return "Invalid temperature"
        else:
            # Convert Celsius to Fahrenheit
            fahrenheit = (celsius * (9 / 5)) + 32
            if fahrenheit < -459.67:
                # Invalid temperature, below absolute zero
                return "Invalid temperature"
            else:
                return celsius, fahrenheit
    else:
        return "Invalid unit"
```

Answers:

What functions did you create?
What strategies did you use to identify them?

#### Sample solutions

- Modular version: [link](https://github.com/lyashevska/modular-code-dev/blob/main/conversion_mod.py)
- Object oriented version: [link](https://github.com/lyashevska/modular-code-dev/blob/main/conversion_mod_class.py)


### Exercise: Think of good and bad examples of documentation
Write down your thoughts in the collaborative documents.
Respond with emojis :+1: :scream_cat: to your colleagues' answers.
#### Think of projects of which you like the documentation. What do you like about them?

#### Think of projects for which you don’t like the documentation. What don’t you like about them? Are you missing anything?

**NB: You can choose a mature library with lots of users for this exercise, but try to also think of less mature projects you had to collaborate on, or papers you had to reproduce.**



### Exercise README: Draft or improve a README for one of your recent projects (in breakout rooms)

Try to draft a brief README or review a README which you have written for one of your projects.

You can work individually, but you could also discuss whether anything can be improved on your neighbour's README file(s).

Think about the user (which can be a future you) of your project, what does this user need to know to use or contribute to the project? And how do you make your project attractive to use or contribute to?

(Optional): Try the https://hemingwayapp.com/ to analyse your README file and make your writing bold and clear.


### [Optional] Exercise: Adding in-code documentation (Try this for yourself)

Update your temperature conversion code from the modular coding exercise so it is well-documented.

Share your final solution in collaborative document.


## 📚 Resources
- [Learn more about object-oriented programming](https://carpentries-incubator.github.io/python-intermediate-development/35-object-oriented-programming/index.html)
- [Repo with modular coding solutions](https://github.com/lyashevska/modular-code-dev)
- [Fancy customization of your terminal with oh-my-zsh](https://ohmyz.sh/)
- [GitHub's Markdown Syntax/Formatting Documentation](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
- [Netherlands eScience Center Python Template](https://github.com/NLeSC/python-template)
- [The four kinds of documentation](https://documentation.divio.com/)