# Table of Contents

   * [Meaningful Names](#meaningful-names)
        * [Use Intention Revealing Names](#use-intention-revealing-names)
        * [Avoid similar naming](#avoid-similar-naming)

# Meaningful Names

## Use Intention Revealing Names

The name of a variable, function, or class, should reveal the intent. It can lead to confusion and disinformation as it's not immediatly obvious what the abbreviation stands for.

### Bad
```
const d = 7; // Days in a week

for (x = 0; x < diaw; x++) {
    console.log("Day:" + x);
}
```

#### Good
```
const daysInAWeek = 7;

for (elapsedDays = 0; elapsedDays < daysInAWeek; elapsedDays++) {
    console.log("Day:" + elapsedDays);
}
```

## Avoid similar naming

Avoid naming multiple variables, functions or classes similar names with subtle changes, as it can lead to disinformation for developers.


### Bad
```
const getUsers = () => {};
const getUser = () => {};
```

#### Good
```
const getListOfUsers = () => {};
const getSingleUser = () => {};
```