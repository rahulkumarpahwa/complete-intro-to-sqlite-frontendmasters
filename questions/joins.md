Imagine you have **two boxes of cards**.

### Box A: Kids

| Kid ID | Name    |
| ------ | ------- |
| 1      | Alice   |
| 2      | Bob     |
| 3      | Charlie |

### Box B: Favorite Toys

| Kid ID | Toy        |
| ------ | ---------- |
| 1      | Teddy Bear |
| 2      | Lego       |
| 4      | Robot      |

The **Kid ID** is like a sticker that helps us know which cards belong together.

A **JOIN** in SQL/SQLite means:

> "Take cards from two boxes and match the ones that belong together."

---

## 1. INNER JOIN

**Only keep matches that exist in both boxes.**

Think:

> "Show me only kids who have a toy listed."

```sql
SELECT Kids.Name, Toys.Toy
FROM Kids
INNER JOIN Toys
ON Kids.KidID = Toys.KidID;
```

Result:

| Name  | Toy        |
| ----- | ---------- |
| Alice | Teddy Bear |
| Bob   | Lego       |

Charlie is missing because he has no toy in the toy box.

Robot is missing because there is no kid with ID 4.

---

## 2. LEFT JOIN

**Keep everything from the LEFT table, even if there's no match.**

Think:

> "Show me ALL kids, and their toy if they have one."

```sql
SELECT Kids.Name, Toys.Toy
FROM Kids
LEFT JOIN Toys
ON Kids.KidID = Toys.KidID;
```

Result:

| Name    | Toy        |
| ------- | ---------- |
| Alice   | Teddy Bear |
| Bob     | Lego       |
| Charlie | NULL       |

`NULL` means:

> "I don't know" or "nothing was found."

Charlie stays because we said "keep all kids."

---

## 3. RIGHT JOIN

**Keep everything from the RIGHT table.**

Think:

> "Show me ALL toys, even if we don't know which kid owns them."

```sql
SELECT Kids.Name, Toys.Toy
FROM Kids
RIGHT JOIN Toys
ON Kids.KidID = Toys.KidID;
```

Result:

| Name  | Toy        |
| ----- | ---------- |
| Alice | Teddy Bear |
| Bob   | Lego       |
| NULL  | Robot      |

The Robot stays because we're keeping everything from the toy table.

### SQLite note

SQLite traditionally **does not support RIGHT JOIN** in older versions. Most SQLite programmers rewrite it as a LEFT JOIN with the tables swapped.

---

## 4. FULL OUTER JOIN

**Keep everything from BOTH tables.**

Think:

> "Show me all kids and all toys, whether they match or not."

Result:

| Name    | Toy        |
| ------- | ---------- |
| Alice   | Teddy Bear |
| Bob     | Lego       |
| Charlie | NULL       |
| NULL    | Robot      |

### SQLite note

SQLite does **not have a native FULL OUTER JOIN**. People usually simulate it using a combination of `LEFT JOIN`, `UNION`, and another join.

---

## 5. CROSS JOIN

**Match everything with everything.**

Think:

> "Every kid gets paired with every toy."

```sql
SELECT Kids.Name, Toys.Toy
FROM Kids
CROSS JOIN Toys;
```

Result:

| Name    | Toy        |
| ------- | ---------- |
| Alice   | Teddy Bear |
| Alice   | Lego       |
| Alice   | Robot      |
| Bob     | Teddy Bear |
| Bob     | Lego       |
| Bob     | Robot      |
| Charlie | Teddy Bear |
| Charlie | Lego       |
| Charlie | Robot      |

3 kids × 3 toys = 9 rows.

---

## Easy Memory Trick

Imagine two circles:

```
Kids        Toys
 ( )------( )
```

* **INNER JOIN** → only the overlap 🎯
* **LEFT JOIN** → all of left + overlap ⬅️
* **RIGHT JOIN** → all of right + overlap ➡️
* **FULL OUTER JOIN** → both circles 🌎
* **CROSS JOIN** → every item with every item 🔀

### The one you'll use most

In real projects:

1. **INNER JOIN** → "Give me matching records."
2. **LEFT JOIN** → "Give me everything from my main table, plus matching data if it exists."

These two make up the vast majority of joins you'll write in SQL and SQLite.
