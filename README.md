# Artificial Neuron from Scratch

A single artificial neuron with logistic regression built with **NumPy only** — no deep learning framework. I wrote it to understand what actually happens inside a model before relying on libraries that hide it.

![Decision boundary on the life expectancy data](images/decision_boundary.png)

## What it does

The same neuron is trained on three binary classification problems :

| Experiment | Data | Task | Training accuracy |
|---|---|---|---|
| Life expectancy | 61 countries (year 2000), 2 features | Developed vs. developing | 82% |
| Synthetic blobs | 100 generated points, 2 features | Separate two clusters | 93% |
| Cats vs. dogs | 1,000 grayscale images (64×64) | Cat or dog | 91.1% |

> These scores are measured on the training data, so they show that the neuron learns, not how well it generalizes. See [What's next](#whats-next).

## How it works

The whole model fits in a few small functions in the notebook:

- `initialisation`: random weights and bias
- `model`: linear combination followed by a sigmoid, `A = 1 / (1 + e^-(X·W + b))`
- `log_loss`: how wrong the predictions are (clipped to avoid `log(0)`)
- `gradients` and `update`: one step of gradient descent
- `artificial_neuron`: the training loop, with a loss curve and accuracy at the end

## Getting started

## What I learned

- **Learning rate matters.** Around 0.1 to 1 worked well on the small datasets; above 1 the loss starts oscillating.
- **Normalizing inputs is not optional.** Scaling features to [0, 1] made training far more stable.
- **Real data is messy.** Dropping rows with missing values cut the life expectancy dataset from 2,938 to 1,649 rows.



*Some of the comments in the notebook are written in French.*

## License

MIT
