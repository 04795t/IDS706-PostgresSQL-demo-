# IDS706-PostgresSQL-demo-

## SQL Queries:
### What are the 5 cheapest restaurants based on avg_cost?
```sql
SELECT name, cuisine, avg_cost
FROM restaurants
ORDER BY avg_cost ASC
LIMIT 5;
```

**Result:**

| # | Name            | Cuisine      | Avg Cost |
| - | --------------- | ------------ | -------- |
| 1 | NuvoTaco        | Mexican      | 12.50    |
| 2 | Bullock’s BBQ   | Southern/BBQ | 15.00    |
| 3 | Pizzeria Toro   | Italian      | 18.00    |
| 4 | Guglhupf Bakery | German Café  | 20.00    |
| 5 | Sushi Love      | Japanese     | 25.00    |

---

### Which nearby restaurants (within 5 miles) are highly rated (4.0+)?
```sql
SELECT name, cuisine, distance_miles, rating
FROM restaurants
WHERE distance_miles <= 5 AND rating >= 4.0
ORDER BY rating DESC, distance_miles ASC;
```

**Result:**

| # | Name            | Cuisine      | Distance (miles) | Rating |
| - | --------------- | ------------ | ---------------- | ------ |
| 1 | NuvoTaco        | Mexican      | 1.2              | 4.8    |
| 2 | M Sushi         | Japanese     | 2.2              | 4.7    |
| 3 | Guglhupf Bakery | German Café  | 1.9              | 4.6    |
| 4 | Pizzeria Toro   | Italian      | 1.8              | 4.5    |
| 5 | Bullock’s BBQ   | Southern/BBQ | 2.1              | 4.4    |
| 6 | Sushi Love      | Japanese     | 0.6              | 4.1    |

---

### 1. Return name, distance_miles for restaurants within 2.0 miles, ordered by distance.
```sql
SELECT name, distance_miles
FROM restaurants
WHERE distance_miles <= 2.0
ORDER BY distance_miles ASC;
```

**Result:**

| # | Name            | Distance (miles) |
| - | --------------- | ---------------- |
| 1 | Sushi Love      | 0.6              |
| 2 | NuvoTaco        | 1.2              |
| 3 | Pizzeria Toro   | 1.8              |
| 4 | Guglhupf Bakery | 1.9              |

---

### 2. Show the top 3 restaurants by rating (highest first).
```sql
SELECT name, rating
FROM restaurants
ORDER BY rating DESC
LIMIT 3;
```

**Result:**

| # | Name            | Rating |
| - | --------------- | ------ |
| 1 | NuvoTaco        | 4.8    |
| 2 | M Sushi         | 4.7    |
| 3 | Guglhupf Bakery | 4.6    |

---

### 3. List name, avg_cost and cost with 7.5% tax as cost_with_tax.
```sql
SELECT name, avg_cost, ROUND(avg_cost * 1.075, 2) AS cost_with_tax
FROM restaurants;
```

**Result:**

| # | Name            | Avg Cost | Cost with Tax |
| - | --------------- | -------- | ------------- |
| 1 | NuvoTaco        | 12.50    | 13.44         |
| 2 | Pizzeria Toro   | 18.00    | 19.35         |
| 3 | Bullock’s BBQ   | 15.00    | 16.13         |
| 4 | Guglhupf Bakery | 20.00    | 21.50         |
| 5 | M Sushi         | 35.00    | 37.63         |
| 6 | Sushi Love      | 25.00    | 26.88         |

---

### 4. How many restaurants are there per cuisine, highest count first?
```sql
SELECT cuisine, COUNT(*) AS restaurant_count
FROM restaurants
GROUP BY cuisine
ORDER BY restaurant_count DESC;
```

**Result:**

| # | Cuisine      | Restaurant Count |
| - | ------------ | ---------------- |
| 1 | Japanese     | 2                |
| 2 | German Café  | 1                |
| 3 | Mexican      | 1                |
| 4 | Southern/BBQ | 1                |
| 5 | Italian      | 1                |