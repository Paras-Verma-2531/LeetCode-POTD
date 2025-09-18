# September 18,2025

## 2353.Design a Food Rating System

```java
public class FoodRatings {

    private Map<String, PriorityQueue<Pair>> cuisineMap;
    private Map<String, String> foodMap;
    private Map<String, Integer> ratingMap;

    public FoodRatings(String[] foods, String[] cuisines, int[] ratings) {
        foodMap = new HashMap<>();
        cuisineMap = new HashMap<>();
        ratingMap = new HashMap<>();

        for (int i = 0; i < foods.length; i++) {
            foodMap.put(foods[i], cuisines[i]);
            ratingMap.put(foods[i], ratings[i]);

            cuisineMap.putIfAbsent(cuisines[i],
                new PriorityQueue<>((a, b) -> {
                    if (b.rating != a.rating) return b.rating - a.rating;
                    return a.food.compareTo(b.food);
                }));

            cuisineMap.get(cuisines[i]).add(new Pair(foods[i], ratings[i]));
        }
    }

    public void changeRating(String food, int newRating) {
        String cuisine = foodMap.get(food);
        ratingMap.put(food, newRating);
        cuisineMap.get(cuisine).add(new Pair(food, newRating));
    }

    public String highestRated(String cuisine) {
        PriorityQueue<Pair> pq = cuisineMap.get(cuisine);
        while (!pq.isEmpty()) {
            Pair top = pq.peek();
            if (ratingMap.get(top.food) == top.rating) {
                return top.food;
            }
            pq.poll(); 
        }
        return "";
    }
}

class Pair {
    String food;
    int rating;

    Pair(String food, int rating) {
        this.food = food;
        this.rating = rating;
    }
}
