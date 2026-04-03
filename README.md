## Supplementary Material for Reviewer1

---

## Round2
---
## Round2-Table 1: D4RL-CL-10 Benchmark Overview

<table>
  <thead>
    <tr>
      <th>Domain</th>
      <th>Tasks</th>
      <th>Number</th>
      <th>Simulator</th>
      <th>State Dim</th>
      <th>Action Dim</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Locomotion</td>
      <td>hopper / halfcheetah / walker2d </td>
      <td>3</td>
      <td>MuJoCo</td>
      <td>11–17</td>
      <td>3–6</td>
    </tr>
    <tr>
      <td>Dexterous</td>
      <td>pen-cloned/human-v1, door-cloned/human-v1</td>
      <td>4</td>
      <td>Adroit</td>
      <td>45</td>
      <td>24–28</td>
    </tr>
    <tr>
      <td>Kitchen</td>
      <td>kitchen-partial-v0, kitchen-complete-v0</td>
      <td>2</td>
      <td>Franka Kitchen</td>
      <td>60</td>
      <td>9</td>
    </tr>
    <tr>
      <td>Navigation</td>
      <td>antmaze-umaze-v0</td>
      <td>1</td>
      <td>AntMaze</td>
      <td>29</td>
      <td>8</td>
    </tr>
    <tr>
      <td><strong>Note</strong></td>
      <td colspan="5">Compared to OCW, D4RL-CL-10 poses three additional challenges: <strong>heterogeneous state/action spaces</strong> (state dim spans 11→60), <strong>diverse simulators</strong> (4 physically distinct engines vs. OCW's unified MuJoCo).</td>
    </tr>
  </tbody>
</table>

---

## Round2-Table 2:Task Training Order & Natural Language Descriptions

| Step | Task | Domain | Data Size | Natural Language Description |
|---|---|---|---|---|
| T1 | hopper-medium-expert-v2 | Locomotion | 2000 eps | Hop forward with a single-legged robot while maintaining upright balance using a mixture of medium and expert hopping strategies. |
| T2 | pen-cloned-v1 | Dexterous | 2000 eps | Twirl and rotate a pen to a target orientation using a dexterous robotic hand, learned from a cloned behavioral policy with added exploration noise. |
| T3 | kitchen-partial-v0 | Kitchen | 613 eps | Complete a subset of kitchen manipulation subtasks including moving the kettle and opening the microwave in a simulated kitchen. |
| T4 | halfcheetah-medium-expert-v2 | Locomotion | 2000 eps | Run forward as fast as possible with a six-legged cheetah robot using a mixture of medium and expert locomotion policies. |
| T5 | door-cloned-v1 | Dexterous | 2000 eps | Open a door by grasping and turning the handle with a dexterous robotic hand, learned from a cloned behavioral policy with added exploration noise. |
| T6 | antmaze-umaze-v0 | Navigation | 2000 eps | Control a four-legged ant robot to navigate through a simple U-shaped maze to reach a fixed goal position. |
| T7 | walker2d-medium-expert-v2 | Locomotion | 2000 eps | Walk forward with a bipedal two-legged robot while keeping balance using a mixture of medium and expert walking gaits. |
| T8 | pen-human-v1 | Dexterous | 50 eps | Twirl and rotate a pen to a target orientation using a dexterous robotic hand, learned from human teleoperation demonstrations. |
| T9 | kitchen-complete-v0 | Kitchen | 19 eps | Complete all four kitchen manipulation subtasks: move kettle, open microwave, toggle light switch, and slide cabinet in a simulated kitchen environment. |
| T10 | door-human-v1 | Dexterous | 33 eps | Open a door by grasping and turning the handle with a dexterous robotic hand, learned from human teleoperation demonstrations. |

---





## Round1
---


## Round1-Table 1: Domain Number D Ablation (OCW-10, 3 Seeds)

| D (Domains) | P ↑           | F ↓            | FWT ↑         |
| ------------- | ------------- | -------------- | ------------- |
| 1             | 0.64±0.02     | −0.00±0.05     | 0.00±0.01     |
| 2             | 0.59±0.09     | 0.01±0.01      | 0.02±0.01     |
| 3             | 0.63±0.08     | 0.03±0.02      | 0.01±0.02     |
| **4 (paper)** | **0.72±0.08** | **−0.02±0.04** | **0.06±0.10** |
| 5             | 0.59±0.06     | 0.06±0.02      | 0.00±0.00     |
| 6             | 0.67±0.02     | −0.02±0.03     | 0.00±0.00     |


---

## Round1-Table 2: Task Order Robustness (OCW-10, 3 Seeds)

| Order | Task Sequence (T1 → T10)                                                                                                                                  |
| ----- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 0     | hammer-v2, push-wall-v2, faucet-close-v2, push-back-v2, stick-pull-v2, handle-press-side-v2, push-v2, shelf-place-v2, window-close-v2, peg-unplug-side-v2 |
| 1     | push-v2, window-close-v2, peg-unplug-side-v2, shelf-place-v2, handle-press-side-v2, push-back-v2, hammer-v2, stick-pull-v2, push-wall-v2, faucet-close-v2 |
| 2     | handle-press-side-v2, peg-unplug-side-v2, push-back-v2, stick-pull-v2, push-v2, shelf-place-v2, faucet-close-v2, window-close-v2, push-wall-v2, hammer-v2 |
| 3     | push-wall-v2, handle-press-side-v2, push-v2, hammer-v2, peg-unplug-side-v2, stick-pull-v2, shelf-place-v2, faucet-close-v2, window-close-v2, push-back-v2 |



| Category | Method     | Order 0       | Order 1       | Order 2       | Order 3       | Avg.     |
| -------- | ---------- | ------------- | ------------- | ------------- | ------------- | -------- | 
| Reg      | L2         | 0.29±0.06     | 0.20±0.03     | 0.23±0.05     | 0.29±0.05     | 0.25     | 
|          | EWC        | 0.16±0.02     | 0.12±0.02     | 0.11±0.02     | 0.15±0.03     | 0.13     |
|          | MAS        | 0.29±0.04     | 0.17±0.01     | 0.16±0.06     | 0.20±0.04     | 0.21     | 
|          | LwF        | 0.21±0.04     | 0.15±0.04     | 0.18±0.05     | 0.19±0.00     | 0.18     |
|          | RWalk      | 0.26±0.03     | 0.17±0.01     | 0.25±0.02     | 0.20±0.01     | 0.22     | 
|          | VCL        | 0.14±0.03     | 0.11±0.01     | 0.11±0.01     | 0.12±0.03     | 0.12     | 
|          | Finetuning | 0.11±0.03     | 0.12±0.02     | 0.15±0.06     | 0.12±0.03     | 0.12     | 
| Struc    | LoRA       | 0.54±0.03     | 0.47±0.02     | 0.35±0.03     | 0.43±0.05     | 0.45     | 
|          | PackNet    | 0.64±0.06     | 0.67±0.01     | 0.65±0.03     | 0.65±0.04     | 0.65     | 
|          | Grow       | 0.60±0.06     | 0.54±0.05     | 0.43±0.01     | 0.51±0.05     | 0.52     | 
| Reh      | PM         | 0.26±0.01     | 0.26±0.10     | 0.25±0.03     | 0.27±0.01     | 0.26     |
|          | A-GEM      | 0.12±0.04     | 0.12±0.02     | 0.11±0.01     | 0.15±0.04     | 0.13     | 
| **Ours** | **HTAC**   | **0.72±0.04** | **0.72±0.02** | **0.70±0.03** | **0.69±0.03** | **0.71** | 



