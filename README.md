# Tic Tac Toe Neural Workshop

A small Vite/React project where you can play against a heuristic AI and watch a neural net learn Tic-Tac-Toe from perfect-play examples. The live build is already hosted on GitHub Pages: https://jrudyray.github.io/tic-tac-toe.

## Training pipeline
- `TrainSetup` lets you name the network, pick a preset (32 → 64 → 32 neurons, etc.), and tweak learning rate, dropout, and weight decay before training.
- After creating a snapshot, `/train` loads the configured network, shows policy/value activations, and feeds supervised examples from `generateTeacherDataset` (Minimax-derived states with symmetry augmentation).
- From there you can run teacher training or Minimax rollouts, keep an eye on loss history, and test the model against Minimax, a random player, or the easy policy.

## Why Minimax is the gold standard
Minimax checks every legal Tic-Tac-Toe move and uses negamax-style recursion so the player-to-move always maximizes their worst-case reward. In a solved game like this it never loses and can force draws against imperfect opponents, which makes it a reliable source of policy/value labels the neural net tries to copy. Symmetry augmentation helps the net learn from each perfect choice even though the model has far fewer parameters than the full game tree.

## Local development (optional)
- `cd web` and run `npm install` to fetch Vite, React, and Tailwind.
- `npm run dev` launches the SPA, `npm run build` bundles it, and `npm run preview` serves the build for manual verification.