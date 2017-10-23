# Typescript Survival
My clumsy-but-essential tips and tricks for using Typescript

## var or let?
Use let.

## arrays
Arrays are can be used as dynamic lists.
```typescript
let list: number[] = [1, 2, 3];
let a = list[0];
list.push(7);
let listCopy = list.slice();

## async / await

This traditional function with promises:
```typescript
getTiersPromise(): Promise<Tier[]> {
  return this.http.get<Tier[]>(
    this.tierUrl + '/tiers').toPromise()
    .then(function (tiers: Tier[]) { tiers.sort((a, b) => a.name < b.name ? -1 : (a.name > b.name ? 1 : 0)))
    .catch(function(err) {
      return null;
    });
} 
```
...is equal to this function using async / await:

```typescript
async getTiers(): Promise<Tier[]> {
  try {
    let tiers = await this.http.get<Tier[]>(this.tierUrl + '/tiers').toPromise();
    return tiers.sort((a, b) => a.name < b.name ? -1 : (a.name > b.name ? 1 : 0));
  }
  catch (err) {
    return null;
  };
}
```
