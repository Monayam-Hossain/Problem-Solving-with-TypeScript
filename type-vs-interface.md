# Type Aliases vs. Interfaces in TypeScript

## Introduction

Type aliases and interfaces are used to define the shape of data within TypeScript. They can help write readable, reusable and maintainable code. Although they have similarities they also have key differences which make them useful in different situations.

## Detailed Explanation

An `interface` is commonly used to describe the structure of objects and classes. Interfaces can be extended, and declarations with the same name can be merged.

```ts
interface Course {
  title: string;
  students: number;
  isPublished: boolean;
}

interface OnlineCourse extends Course {
  platform: string;
}
```

A `type` alias can describe object shapes too, but it can also represent unions, intersections, primitives, tuples, and other type expressions.

```ts
type Identifier = string | number;

type CourseSummary = {
  title: string;
  students: number;
};

type PublishedCourse = CourseSummary & {
  isPublished: true;
};
```

For example, the `Course` interface is a natural choice when defining a reusable object contract. A type alias is more flexible when a value may have several possible forms, as with `Identifier`.

Both can be used to type function parameters and return values. Interfaces support declaration merging, while type aliases do not. Interfaces for extendable object-oriented contracts, especially when classes implement them. Type aliases for unions, intersections, tuples, and complex combinations.

## Conclusion

Choose `interface` when modeling objects and extending contracts. Choose `type` when you need more flexibility such as unions or tuples.
