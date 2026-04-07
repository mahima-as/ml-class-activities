# Activity 9: Neural Networks — Forward and Back Propagation

> **Notebook:** `ML/Neural Networks.ipynb`
> **Suggested time:** 30–45 minutes
> **Dataset:** None — all computations use the provided example network

---

## Learning Objectives

By the end of this activity, students will be able to:

1. Compute forward propagation through a multi-layer neural network by hand,
   tracking weight matrices, signals, and neuron outputs.
2. Compute back propagation gradients for error with respect to signals and weights.
3. Explain how gradient descent uses back propagation gradients to update weights.
4. Interpret the role of activation functions (tanh) in introducing nonlinearity.

---

## Prerequisites

- Matrix multiplication and the chain rule (calculus)
- Understanding of what a neuron's activation represents
- Familiarity with gradient descent conceptually
- It is helpful (but not required) to have read about the delta rule or
  back propagation before this activity

---

## Materials

- Notebook: `ML/Neural Networks.ipynb`
- Reference network diagram (see below — reproduce on the board or slide):

```
        [1]      [1]      [1]      [1]
         |  0.2   |        |        |
   0.1   |        |  1     |  2     |
[x] ----[tanh]--[tanh]--[tanh]----> h(x)
   0.3   |
   0.4   |
        [tanh]
         | -3
```

*Architecture: input x, 3 hidden layers with tanh activations, scalar output h(x).
Weights are labeled on connections. Bias nodes shown as [1].*

---

## Suggested Timeline

| Phase | Time | Description |
|-------|------|-------------|
| Introduction | 5 min | Instructor draws the network and walks through one forward step |
| Individual work | 15 min | Students compute full forward and back propagation by hand or in code |
| Group discussion | 10 min | Compare intermediate values; identify where errors propagate |
| Share out | 10 min | Groups present one step each; instructor connects to gradient descent |

---

## Instructor Notes

### Setup
- The notebook is currently a placeholder. This activity is primarily a
  **pencil-and-paper (or Markdown) exercise**, optionally verified in code.
- Distribute the network diagram at the start of class (or display on the board).
  All weights, bias values, and the activation function (tanh) are shown in the diagram.
- Choose an input value x (e.g., x = 0.5) and announce it to the class before
  they begin.

### Introducing the activity (5 min)
Walk through the first layer of forward propagation together:

1. Compute the weighted input to the first hidden neuron: `z = 0.3*x + 0.1*1`
2. Apply activation: `a = tanh(z)`
3. Ask: "What does this value represent? What would happen if we used a linear
   activation instead?"

Then hand it over to students to complete the rest.

### Forward Propagation Steps (students complete)
Students should track:
- Input to each neuron (weighted sum of incoming signals + bias)
- Output of each neuron (after applying tanh)
- Final output h(x)

### Back Propagation Steps (students complete)
Students should compute:
- Gradient of the loss with respect to the output: ∂E/∂h(x)
  *(Choose a simple target value, e.g., y = 1, and use squared error)*
- Gradient flowing back through each layer using the chain rule
- Gradient of the loss with respect to each weight: ∂E/∂w

### Weight Update Discussion
After computing the gradients, ask students:

> "Using a learning rate of η = 0.1, how would you update the weight labeled 0.2?
> Write the new weight."

This connects back propagation to gradient descent concretely.

### Common Issues
- Students often mix up the gradient of tanh: d/dx tanh(x) = 1 − tanh²(x).
  Write this on the board at the start.
- The chain rule application across layers is the hardest part. Encourage
  students to write each intermediate gradient explicitly rather than combining steps.
- Students sometimes compute forward propagation correctly but forget to use the
  *pre-activation* signal (z, not a) when computing back propagation deltas.

### Facilitation Tips
- Assign different groups to compute back propagation for different weights —
  e.g., Group A computes ∂E/∂w for the first layer, Group B for the second.
  During share-out, groups present their results and the class assembles the
  full back propagation pass together.
- Ask: "If the gradient for a weight is very small (near zero), what does that
  mean for learning? What could cause this?" — this previews the vanishing
  gradient problem.

---

## Student Instructions

*Distribute or display at the start of the activity:*

> Using the neural network shown in the diagram with input x = [value announced
> in class]:
>
> 1. **Forward propagation:** Show all steps including weight matrices,
>    intermediate signals (z), and neuron outputs (a) for each layer.
>    Report the final output h(x).
>
> 2. **Back propagation:** Show the gradient of the error with respect to each
>    signal and each weight. Use squared error loss with target y = [value
>    announced in class].
>
> 3. **Weight update:** Choose one weight and show how you would update it using
>    gradient descent. Explain what the sign and magnitude of the gradient
>    tell you.

---

## Discussion Prompts

1. What would happen to the forward pass if all weights were initialized to zero?
   Why is this a problem?
2. The tanh activation squashes outputs to (−1, +1). How does this help during
   back propagation? What problem can it cause in deep networks?
3. Your gradient for a weight near the input might be very different from one
   near the output. Why? What does this suggest about learning in deep networks?
4. You computed gradients for one input x. In practice, how would you handle
   a dataset with thousands of examples?
5. How would adding more hidden layers change the forward and back propagation
   calculations?

---

## Pass/Fail Specifications

To **pass** this activity, a submission must:

- [ ] Show all forward propagation steps: weighted inputs (z), activations (a),
      and final output h(x) for each layer, with intermediate values shown
- [ ] Show all back propagation steps: gradients of the error with respect to
      signals and with respect to at least two weights from different layers
- [ ] Show a weight update for at least one weight using gradient descent,
      with the updated value computed
- [ ] Include a comment on what the output gradients indicate about how
      each weight should be adjusted

Specifications will be confirmed and released when the activity is discussed in class.
Students may revise and resubmit up to two times.
