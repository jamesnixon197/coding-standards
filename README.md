# Table of Contents

   * [Meaningful Names](#meaningful-names)
        * [Use Intention Revealing Names](#use-intention-revealing-names)
        * [Avoid similar naming](#avoid-similar-naming)
        * [Make meaningful distinctions](#make-meaningful-distinctions)
        * [Use pronounceable names](#use-pronounceable-names)
        * [Use searchable names](#use-searchable-names)
        * [Avoid adding type information](#avoid-adding-type-information)
        * [Object names](#object-names)

# Meaningful Names

## Use Intention Revealing Names

The name of a variable, function, or class, should reveal the intent. If it doesn't it can quickly lead to confusion and disinformation if it's not immediately obvious what the abbreviation stands for.

### Bad
```
const d: number = 7; // Days in a week

for (const x: number = 0; x < diaw; x++) {
    console.log("Day:" + x);
}
```

#### Good
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

#### Good
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

#### Good
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

#### Good
```
class DatabaseServer {
    private username: string;
    private password: string;
}
```

## Use searchable names

Use names which can easily be grepped for in the code. Avoid using single letter names which can bring up many results. Remember `e` is the most used letter in the English alphabet.

### Bad
```
const t: number = 3;

for (const x: number = 0; x < a; x++) {
    console.log(x);
}
```

#### Good
```
const totalRooms: number = 3;

for (const roomIndex: number = 0; roomIndex < totalRooms; roomIndex++) {
    console.log(totalRooms);
}
```

## Avoid adding type information

Avoid adding encoding type or scope info into names as it can just add an extra burden to a developer trying to decipher the name, especially when even the encoding type isn't clearly obvious in a name, an example of this art form is [Hungarian Notation](https://en.wikipedia.org/wiki/Hungarian_notation). This isn't a massive issue for strongly typed languages as the type is next to the name in most cases.

### Bad
```
class Property {
    public roomArr: Array<Room>;
}
```

#### Good
```
class Property {
    public rooms: Array<Room>;
}
```

## Object names

Always use a noun when naming objects or classes, as the point of an object / class is to be a 'thing' or else in certain contexts the object or class won't make any sense (like below).

### Bad
```
class PostAnAdvert {
    public title: string;
}

const advert: PostAnAdvert = new PostAnAdvert('New room');
```

#### Good
```
class Advert {
    public title: string;
}

const advert: Advert = new Advert('New room');
```

