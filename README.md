# 🐰 Cute Newton-Raphson Square Root Calculator 🧮✨

Ever wondered how to calculate a square root without `math.sqrt`?
This little Python program does it using the **Newton-Raphson method**—a smart “guess-and-correct” trick!

Let’s go **line by line** and see what’s happening.

---

## The Code Explained

```python
def sqrt(x, tolerance=1e-10, max_iterations=100):
```

* **We define a function** called `sqrt` that takes:

  * `x` → the number we want the square root of
  * `tolerance` → how close we need to get to the real answer (smaller = more precise)
  * `max_iterations` → a safety cap so we don’t guess forever

```python
    if x < 0:
        raise ValueError("√ Negative numbers are scary")
```

* Square roots of negative numbers? 😱
* We politely refuse and raise an error.

```python
    if x == 0:
        return 0
```

* The square root of 0 is 0. Easy peasy. 🍋

```python
    guess = x / 2.0  # start with half of the number
```

* Pick a **starting guess**.
* Half of the number is usually a good place to start.

```python
    for i in range(max_iterations):
        next_guess = (guess + x / guess) / 2
```

* We loop a maximum of `max_iterations` times. 🔄
* **Newton-Raphson formula:** `next_guess = (guess + x / guess) / 2`

  * It adjusts our guess closer to the true square root.

```python
        if abs(next_guess - guess) < tolerance:  # if guess is very close, stop
            return next_guess
```

* If the new guess is very close to the previous guess (difference < `tolerance`), we’re done! ✅
* We return `next_guess` as our answer.

```python
        guess = next_guess  # update guess and repeat
```

* Update our guess and try again until we reach the desired accuracy.

```python
    return guess  # fallback in case max_iterations is reached
```

* If we somehow didn’t converge within `max_iterations`, just return the last guess. 🏁

```python
print(sqrt(int(input('Enter number: '))))
```

* Ask the user for a number, calculate the square root using our function, and print it. 🎉

---

## Example Run

```
Enter number: 25
5.0
```

```
Enter number: 2
1.41421356237
```

## Tips

* **Smaller `tolerance`** → more accurate, might take slightly more iterations.
* **Larger numbers** → Newton-Raphson is super fast and handles them like a champ! 💪

If this felt gay it's cuz `Zesty ChatGPT` wrote this readme.md
---

🐣 Enjoy calculating square roots like a math wizard!
