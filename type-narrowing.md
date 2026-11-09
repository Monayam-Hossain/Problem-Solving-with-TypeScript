# Type Narrowing in TypeScript

## Introduction

Type narrowing is the process of refining a variable from a broader type (like a union type) to a more specific type within a conditional block or code path. It allows TypeScript to provide safer, more precise type checking when a variable can hold more than one type.

## Detailed Explanation

The `typeof` operator is useful for primitive values. For example, a function accepting a string, number, or boolean can handle each case separately.

```ts
function processInput(input: string | number | boolean): string | number {
  if (typeof input === "string") {
    return input.trim().toLowerCase();
  }
  if (typeof input === "number") {
    return input * 10;
  }
  return input ? "Active" : "Inactive";
}
```

The `instanceof` operator checks whether an object was created by a particular class or constructor. It is useful when working with class instances.

```ts
class Manager {
  manage(): string {
    return "Managing a team";
  }
}

function describe(value: Date | Manager): string {
  if (value instanceof Date) {
    return value.toISOString();
  }
  return value.manage();
}
```

The `in` operator checks whether a property exists on an object. It can distinguish object variants in a union.

```ts
type EmailUser = { email: string };
type PhoneUser = { phone: string };

function contact(user: EmailUser | PhoneUser): string {
  if ("email" in user) {
    return user.email;
  }
  return user.phone;
}
```

Each check gives TypeScript evidence about the value, so operations can be performed without unsafe type assertions.

## Conclusion

Use `typeof` for primitive checks, `instanceof` for class instances, and `in` for object properties. These guards make union-typed code safer and easier to understand.
