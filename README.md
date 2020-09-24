# Table of Contents

* [Meaningful Names](#meaningful-names)
    * [Use Intention Revealing Names](#use-intention-revealing-names)
    * [Avoid similar naming](#avoid-similar-naming)
    * [Make meaningful distinctions](#make-meaningful-distinctions)
    * [Use pronounceable names](#use-pronounceable-names)
    * [Use searchable names](#use-searchable-names)
    * [Object names](#object-names)
    * [Method Names](#method-names)
    * [Don't Be Cute](#dont-be-cute)
* [Functions](#functions)
    * [Blocks and indentation](#blocks-and-indentation)
    * [Do one thing](#do-one-thing)


# Credit

Credit for these details, goes to the 'Clean Code: A handbook of Agile Software Craftsmanship' book.

# Meaningful Names

## Use Intention Revealing Names

The name of a variable, function, or class, should reveal the intent. If it doesn't it can quickly lead to confusion and disinformation if it's not immediately obvious what the name means.

### Bad
```
const d: number = 7; // Days in a week

for (const x: number = 0; x < diaw; x++) {
    console.log("Day:" + x);
}
```

### Good
```
const daysInAWeek: number = 7;

for (const elapsedDays: number = 0; elapsedDays < daysInAWeek; elapsedDays++) {
    console.log("Day:" + elapsedDays);
}
```

## Avoid similar naming

Avoid naming multiple variables, functions or classes similar names with subtle changes, as it can lead to developers mistakenly using an incorrect item.


### Bad
```
const getUsers: Array<User> = () => {};
const getUser: User = () => {};
```

### Good
```
const getGroupOfUsers: Array<User> = () => {};
const getSingleUser: User = () => {};
```

## Make meaningful distinctions

Avoid naming an item just to satisfy the interpreter or compiler as it can lead to lazy naming. For example, if you want create a new variable called `foo` but it's already taken in the block of code you are using, don't try and name the new variable in an arbitrary way. Try and distinguish the names in a way where future programmers know exactly what is stored / returned.

### Bad
```
// Old var
const productId: number = 10;

// New var
const productId2: number = 5;

// Both var names are arbitrary and mean nothing to someone who hasn't viewed the code before
```

### Good
```
// Old var
const multiListingProduct: number = 10;

// New var
const upgradeProductId: number = 5;

// Can quickly see what is stored in each variable
```

## Use pronounceable names 

Humans can better understand and read pronounceable words. Using unpronounceable words can make a block of code very confusing and even more confusing when trying to discuss that block of code. It also means any new developers will need to have these crazy names explained to them which just wastes time.

### Bad
```
class DBSrv {
    private unme: string;
    private pwrd: string;
}
```

### Good
```
class DatabaseServer {
    private username: string;
    private password: string;
}
```

## Use searchable names

Use names which can easily be grepped for in the code. Avoid using single letter names which can bring up many results. For example, `e` is the most used letter in the English alphabet so wouldn't be good name.

### Bad
```
const t: number = 3;

for (const x: number = 0; x < a; x++) {
    console.log(x);
}
```

### Good
```
const totalRooms: number = 3;

for (const roomIndex: number = 0; roomIndex < totalRooms; roomIndex++) {
    console.log(totalRooms);
}
```

## Object names

Use nouns when naming objects or classes, as the point of an object / class is to be a 'thing' or else in certain contexts the object or class won't make any sense (like below).

### Bad
```
class PostAnAdvert {
    public title: string;
}

const advert: PostAnAdvert = new PostAnAdvert('New room');
```

### Good
```
class Advert {
    public title: string;
}

const advert: Advert = new Advert('New room');
```

## Method Names

When naming a method inside an object / class, you should choose a verb which describes what the method is doing, as a method is a function which does a 'thing'. A good standard is the JavaBean standard where accessors, mutators and predicates should be prefixed with `get`, `set` and `is`.

### Bad
```
const advert = new Advert;

advert.title("Advert title")

const advertTitle = advert.retrievedTitle();

if (advert.posted()) {
    # Posted
}
```

### Good
```
const advert = new Advert;

advert.setTitle("Advert title")

const advertTitle = advert.getTitle();

if (advert.isPosted()) {
    # Posted
}
```

## Don't Be Cute

Don't try and be clever with the names, as it might make sense to you and other people who get the joke but anyone new may struggle to understand what the name means.

### Bad
```
const cya: void = process.exit;
```

### Good
```
const killProcess: void = process.exit;
```

# Functions

## Blocks and indentation

Blocks within `if`, `else` & `while` statements should be always moved into their own function, it's a nice way to keep functions small and easily understandable. This implies the function should not hold nested structures, so should only have an indentation level of 1 or 2.

### Bad
```
const getStatusString = (status: string, advertID: number): void {
    if (advertID) {
        if (status === "L") {
            return "Live";
        } else if (status === "T") {
            return "Expired";
        } else {
            return "Deleted";
        }
    } else {
        throw new Error("Advert not found");
    }
}
```

### Good
```
const getStatusString = (status: string, advertID: number): void {
    if (advertID) throw new Error("Advert not found");

    return renderStatusString(status);
}

const renderStatusString = (status: char): string {
    if (status === "L") return "Live";
    if (status === "T") return "Expired";

    return "Deleted";
}
```

## Do one thing

A function should only do a single function, hence the name function it should only have a single function.