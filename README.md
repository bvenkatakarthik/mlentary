# An open-source effort for a book on machine learning.

A quasi-open-source introductory book on machine learning, focusing on geometry
and modern concepts!

CONTENTS:

    repo organization
        latex and python requirements
        desired directory structure
        branch etiquette
    vision for the book/notes
        story arc and learning goals
        what we want for writing
        what we want for code
        what we want for figures

## repo organization

#### latex and python requirements

Python 3.8, numpy ?.? etc
  FILLIN

Run `make ml` to compile `mlentary.tex` and display the pdf.  I use `pdflatex`
to compile latex source and `evince` to view pdfs, but you can use whatever you
like: (just edit your `Makefile` and include your Makefile in your
`.gitignore`).

#### desired directory structure

The following is NOT the current directory structure.  It is instead what I
WANT the repo to look like.  I haven't had time to organize.

    mlentary.tex

    tex-source/
        sam.sty
        ... [a bunch of `.tex`s, to be included in `mlentary.tex`]

    figures/
        ... [a bunch of `.png`s, most generated by little scripts in `code/`]

    code/
        plot_helpers.py
        extra/
            ... [a bunch of `.py`s for little examples not part of a big task]
        mnist/
            ... [a bunch of `.py`s for basic and advanced digit classification]
        words/
            ... [a bunch of `.py`s for basic and advanced text extrapolation]
        faces/
            ... [a bunch of `.py`s for basic and advanced face generation]
        polls/
            ... [a bunch of `.py`s for basic political poll prediction]
        robot/
            ... [a bunch of `.py`s for basic robotic arm control]
        atari/
            ... [a bunch of `.py`s for basic video game exploration]

    Makefile

    README.md

#### branch etiquette

We will primarily make commits to branches called `unit0`, ..., `unit6`.

    BRANCH...       ...CONTAINS A...

    main            (most recent quasi-coherent draft)
    release         (older but refined and thoroughly checked draft)
    unit0           (most recent compiling draft of: friendly invitation to ML)
    unit1           (most recent compiling draft of: linear models)
    unit2           (most recent compiling draft of: nonlinear models)
    unit3           (most recent compiling draft of: deep learning)
    unit4           (most recent compiling draft of: modeling uncertainty)
    unit5           (most recent compiling draft of: reinforcement learning)
    unit6           (most recent compiling draft of: appendices etc)

We will have a `main` branch for our communal "nearly latest draft so far" and
a more sacred, less frequently-committed-to called `release` for a less recent
containing a more thoroughly refined and checked draft.  The branches `unit1`
through `unit5` hold our 5 "actual" chunks of content, `unit0` is to be a
friendly invitation and orienting up-ramp to the subject, and `unit6` is for
miscellaneous items such as a short "what's next" section and maybe a sketch of
some mathematical prerequisites.

Easter Egg.  1729 is a magic number.  Direct message sam (`bohrium`) on
discord that you've seen this magic number.  This tells me you've looked at
this!

So the information flow goes something like

        authors (y'all and me)
              /       \       \
             |write    |check  \_check
             |and      |before   \really
             |program  |merging   \_carefully
             |          \           \before
             v           |           \_merging
                         |             |
            unit0  --+   v             v
                      \ 
             ...       ------>  main  ----------->  release
                      /
            unit6  --+

If you find it helpful, feel free to make one or more "personal" branches for
experimental stuff you want to try.  If you do this, use the form
`username-unit-branchdescription` for the branch name.  For example, if your
github username is `galapagos` and you're trying out some new thing with kernel
visualization for unit 2, then an appropriate branch name could be
`galapagos-unit2-kerviz` Of course, you could make these branches in just your
local repo, but if you also do so in the remote repo then others can take a
look.

## vision for the book/notes

#### story arc and learning goals

The basic story arc is as follows:

    unit0   --- what does it mean to learn from examples?
    unit1   --- visualize high-D space to learn-from-examples via linear models
    unit2   --- extend unit1's superpower to new tasks by hand-crafting nonlinearities
    unit3   --- extend unit2's superpower to richer tasks by automating the crafting of nonlinearities
    unit4   --- extend unit3's superpower to structured tasks
    unit5   --- learn-from-rewards by framing learning-from-rewards problems as learning-from-examples problems
    unit6   --- extras (e.g. helpful math refreshers)

In a bit more detail, something like the following makes sense to me.  Below,
"Unit 0" contains prerequisites rather than a friendly invitation.

    Unit 0: Prerequisites
      Coding Lecture 0: Python, Numpy, Pytorch
        Multi-axis arrays.  Speedups.  Index kung-fu.
        Common numpy maps and zips, filters, reduces, and contractions
        Example: large-numbers dice statistics, plotting
        Example: (batched) image filter made by hand
        Intro to Pytorch

      Homework 0a: Math
        Types, Functions and Dependencies, Notation
        Linear Algebra: High Dimensions, Hyperplanes, Linear Maps, Trace and Det; Quadratic Forms, Dot Products, SVD
        Probability: Expectations, Independence, Bayes, Concentration; Coinflips, Gaussians
        Optimization: Visualizing Derivative Rules, Sums of Terms (Constraints); Vectors vs Covectors, Overshooting, Convexity
        Examples: Least Squares; Gaussian Fitting M-Step

      Homework 0b: Programming
        Matrix Multiply Speed Test
        Numpy Safari / Treasurehunt
        Softmax Speed Test
        Debugging Randomized Code
        Debugging Many-File Codebase

      Project 0a:
      Project 0b:

    Unit 1: Learning from Examples
      Lecture 1a: What is Machine Learning?

      Lecture 1b: A Simple Image Classifier

      Lecture 1c: Accelerate Learning using Gradient Descent

      Lecture 1d: Training vs Testing Error % Generalization, Optimization, Approximation

      Coding Lecture 1: Coding the image classifier from lectures, from scratch.  Examining behavior on a concrete image.

      Homework 1a: Hyperplanes and Dataclouds

      Homework 1b: Learning.  Weights-vs-Correlations

      Project 1a: Text Classification % not 3-Way.  Just 2-way.

      Project 1b: Measuring Overfitting; Hyperparameter Search

    Unit 2: Engineering Features (and Friends) by Hand
      Lecture 2a: Feature Engineering
        Bias Trick
        Black Holes
        Specialty Features, e.g.\ Trig or Threshold
        Interpreting Weights (vs Correlations)
        Feature Selection and Generalization

      Lecture 2b: Loss Functions, Regularization, Margins % Logistic, Hinge, Perceptron, Square; acc bound; L-inf, L2, L1; prob interp
        Humble Models, Acc Bound
        Regularization: Why and How
        Probabilistic Interpretation, Likelihood, Gradient Descent
        Margin Maximization and Supports
        Feature Selection and Optimization (Convexity)

      Lecture 2c: Data-based Featurization % Kernels, PCA, Quantiles & Trees
        Quantiles (Binning), Stumps, Trees
        Linear Dimension Reduction: PCA
        Matrix Factorization Perspective, ICA
        Nonlinear Dimension Reduction: Similarity-to-Landmark Embeddings.  Kernels
        Designing Similarity Functions.  Consideration for Text, Images.

      Lecture 2d: Reducing to Linear Learning % Softmax, Regression, Sequences, etc
        Specialized Readouts
        Soft Classes, Multiple Classes
        Regression
        Factoring Big Problems.  E.g.\ Sequences
        Shared Features for Multiple Outputs.  Examples of Overall Architectures

      Coding Lecture 2: SVM with RBF Features from Scratch, for Image Classification
        Plan, Pictures, Meeting Data
        Forward Model
        Gradient Step
        Training and Model Selection
        Testing, Interpreting Weights

      Homework 2a: Feature Geometry, Geometry of Margins and Regression
        Matching Features (and Losses/Architectures) and Domain Knowledge, Practice
        Recognizing Decision Boundaries
        Probabilistic Interpretation of Losses, Regularizers
        Support Vector Bound.  Perceptron Update.  Perceptron worse generalization.
        Implicit Regularization in Least Squares Regression by Gradient Descent

      Homework 2b: Kernel Trick
        Data-Dependent Features.  Similarity, Inner Products, Generalization.
        Why We Want Positive Definite Kernel
        Kernelized Update
        Recognizing Decision Boundaries % ??
        Wide Random Features Kernel

      Project 2a: Overfitting to Features on Kaggle-Style Challenge % Selection/Hyperparam/Unsupervised Featurization
        Adapt the SVM to Kaggle Task; Weights and Overfitting
        Success Measures.  Accuracy vs Loss.  ROC Curve, Ranking.  Class-imbalance.
        Feature Selection and Overfitting
        Quantilization and Overfitting
        DataSnooping and Overfitting % difficult but important lesson to design!

      Project 2b: 10-Way Image Softmax Classification.  Calibration Prediction Challenge
        Softmax, Prob Calibration
        Basic Features.  Add your twist!
        Badly Set Hyperparams.  Add your insight!
        Assessing Confidence: Generalization Bounds, Margin-Based Cross-Validation
        Prediction Challenge

    Unit 3: Learning Features from Data
      Lecture 3a: Shallow Learning % Optimization tricks
        Architecture, Intuiting Decision Boundaries (Universality)
        Gradient Descent (Backprop)
        An Example Learning Trajectory: Vertical vs Horizontal Learning
        MLP as Butter: add to everything.  Regularization.  Examples.
        BIC, Johann-Lindenstrauss, Wide Random Features, Generalization.

      Lecture 3b: Deep Learning and Ideas in Architecture % Differentiable-Blah Flexibility in architecture.  Mention RNNs
        ``To Build It, Use It''
        Feature Hierarchy.  Learned ``subroutines''
        Ideas in Optimization: Backprop, Weight Initialization, Batch Normalization, ADAM, etc
        Getting Creative.  Skip Connections etc
        Curvature-Noise Interactions and Generalization

      Lecture 3c: Symmetry and Locality: Convolution
        CNN forward encodes basic image priors.  Pooling.
        Backprop formulas
        What can K Layers of a CNN Represent?
        How GPUs Work
        Pottery Image.  Symmetries and Representations.  Sports.  Melodies.

      Lecture 3d: Symmetry and Locality: Attention
        Attention forward encodes basic sequence/table priors (sparse).
        Bells and Whistles: Multiple Heads, Positional Encoding
        What is a Transformer?
        What can K Transformer Layers Represent?
        Differentiable Computers.  Stacks.  Graphs.

      Coding Lecture 3: A Deep Image Classifier from Scratch
        Plan of what we need to write, picture of architecture
        Forward Model (Including conv layers)
        Backward Model (Including conv layers)
        Quick Checks for Silly Mistakes
        Training and Interpretation of Weights

      Homework 3a: Decision Boundaries, Backpropagation
        Backprop for Simple, Fanciful Architecture
        Vanilla Neural Network Architecture
        VNN Backprop Formulas and Intuition
        Recognizing Decision Boundaries for Wide vs Deep
        Initialization of Weights, Match Comments to Lines in Training Code

      Homework 3b: Zoo of Architectural Ideas % Light Load.  Only few questions, all conceptual.
        Word Embeddings
        Siamese, Metric, LeCun Representation Learners
        RNNs, LSTMs
        Differentiable X (Renderer etc)
        Learned Losses / Ecosystems (Wass GAN, etc)

      Project 3a: An Image Sharpener (or maybe next-frame-in-video)? % Perhaps Image Sharpener? % on both Digits and Face data?
        U-Net Architecture (Pix2Pix but no GAN?)
        Forward Model
        Backward Model
        Training
        A word on Laplacian Pyramid and Diffusion Models.  Adapt to Image Generator and see bad.

      Project 3b: Text Generation Through Classification
        Transformer Architecture, Meet the Data
        Run Training Code
        Interpreting Learned Weights
        Playing with Model on Out-of-Distr Data
        Text Compression Challenge

    Unit 4: Modeling Structured Uncertainties
      Lecture 4a: Square Loss Muddies, Probabilistic Models.  Examples: 3State Traffic, HMM, GMM
        Structured Uncertainties in the World.  Rapid Holmesian
        Inferences.  Square Loss Muddies.  Recall prob interp of e.g. least
        squares regfression.  Unsup Learning.
        Latents, Marginal Likelihood for Latents, Weights as Latents.
        Example: 3State Traffic.  Challenge of Normalization.
        Example: HMM.  0s and SoftLogic and backflow
        Example: GMM.  Metapriors, hierarchy, Transfer

      Lecture 4b: Inference via Sampling % MH, EM,
        Challenge.  MH Algorithm.
        Visualizing MH.  Proposals Matter
        EM: 3State Traffic example
        EM: HMM example
        EM: GMM example

      Lecture 4c: Inference via Variation % MH, EM,
        EM overview, 3State Traffic example
        ELBO bound and pingpong KL geometry
        EM: HMM example (more detail in coding example)
        EM: GMM example (more detail in pset)
        Variational Parts as Neural Net

      Lecture 4d: Variational Autoencoders (or Encoders) % so connects back to Unit 3
        Architecture % comparison to matrix factorization, etc
        VAEs and ELBO
        Interpreting Update Intuitively
        Output side Noise Model (e.g. square loss)
        Conditional VAEs

      Coding Lecture 4: Expectation-Maximization for Sequences
        HMM architecture.  Remark on RNNa
        E-step: dynamic programming
        M-step with regularization
        End-to-end reading and mimicry of cookbook text
        Investigation of State Meanings

      Homework 4a: Gaussian Mixtures for Clustering % k-means as limit
        forward model
        E step and M step
        k-means as limit
        small-var regularization from prior
        convergence near minimum

      Homework 4b: Bayes Nets.  NNs as Amortized Inference
        Marginalization over Latents
        Weights as Latents in Linear Classification (bowtie vs pipe)
        BIC and structural penalty
        Causal modeling
        Very Basic Occlusion Inference Object Net

      Project 4a: Predicting Political Polls
        Meeting the Polling Data
        Forward Model
        Inference through Sampling
        Wrestling with Training Difficulties (burnin, etc)
        Interpreting Latents


      Project 4b: A Deep Image Generator (VAE)
        Meeting the Face Data.  How to assess success? % maybe met face data in previous unit?
        Forward Model including reparam trick
        Backward model and intuitive interpretation
        Training and Testing
        Interpreting Latents.  Sources of Prejudice and Capriciousness

    Unit 5: Learning while Acting (and from Rewards)
      Lecture 5a: Rewards and States.  Explore-Exploit Challenge.
        Learning from Rewards: overview and goal to reduce to supervision
        Conditional Bandits are kin to Supervised Learning
        Explore-Exploit Challenge
        Optimism in Face of Uncertainty
        Introduction of State Concept.  Total Utility, Episodes,  Online blurs Train and Test

      Lecture 5b: Qualitative Solutions to MDP.  Dynamic Programming, Idea of Bootstrap
        MDP framework again.  State Correlations (Credit-Assignment) Challenge
        Dynamic Programming
        Bootstrap: Online dynamic programming (SARSA)
        Example Policy in Gridworld
        Function Approximation (or Partial Observability)

      Lecture 5c: Reduce to Supervision using Q-Learning.
        Q-Learning vs Naive SARSA
        Q-Learning plus Exploration Policy
        Featurization of Huge State (Deep Q-Learning)
        LSTM for non-Markov State
        Deadly Triad, Q-Delusion

      Lecture 5d: Non-technical Discussion of: Curiosity, Language, Instruction, World-Models
        Curiosity Bonuses and Self-Curriculum % mention Adversarial self-play?
        Curricula in RL and Elsewhere
        Symbols, Contextual Learning in GPT, Instructions guide Symbol Search in World-Models
        Evolution of Programming.  Self-Coding Computers
        Speculations on Future of Learning

      Coding Lecture 5: Q-Learning for a Gridworld, from Scratch
        World Simulator
        Q-Table (with flexibility to be function approx)
        Q-Learning Update
        Training and Reading out Policy
        Visualizing Learning curves as add challenges

      Homework 5a: Bandits, Explore-Exploit, Conditional Bandits
        Epsilon Greedy for Known Timescale
        UCB Bound vs Epsilon Greedy at Various Timescales
        Function Approximation in Conditional Bandits
        Movie Recommendation Update (Linear Embeddings)
        A Very Basic Adversarial BoardGame Player

      Homework 5b: Q-Learning, on-vs-off policy, Horizons
        Practice Modeling Situations by MDPs.  Get Rich Enough State Space for Markov Property!
        Manually Solve Various MDPs
        Computations of Q-Learning Convergence
        As Human, Explore a Maze.  Short Essay on Exploration Strategy
        Baud Rates for Learning Signals Comparison

      Project 5a: Robotic Arm
        Robot Physics Overview.  Collisions?
        Clasping Reward Function (Helper to Smooth)
        Set up Q-learning for parameterized task (what are inputs to Q network etc?) % mention policy gradient?
        Training
        Visualize and Describe Motions

      Project 5a: Simple Atari-Style Games % (Fully Observed?  Partially Observed?)
        Game Family Overview
        Function Approximation
        Experience Replay
        Creative Part: Design Featurization and Exploration Policy!
        Action Challenge: Learn an Unknown Game in Same Family!

    Unit 6: Farewell
      Bonus Lecture 6a: What We Learned
      Bonus Lecture 6b: What to Learn Next

Easter Egg.  (-1/12) is a magic number.  Direct message sam (`bohrium`) on
discord that you've seen this magic number.  This tells me you've looked at
this!

What are 3 concrete verb phrases I want the notes to *enable* a reader to do?
    * Attack arbitrary prediction-from-example tasks by designing, training, and tuning an appropriate linear model from scratch.
    * Tailor nonlinearities, priors, and optimization to navigate the generalization-approximation tradeoff.
    * Impress friends by completing a small project that actually helps or entertains in daily life.
I avoided words like "understand" above because such words are too temptingly
vague.  But if I allow such words then I add these three verb phrases:
    * Diagnose, at a glance, glaring missteps in a friend's ML project.
    * Frame common ML algorithms *probabilistically* to reveal what domain assumptions the algorithm incorporates.
    * Parse an old deep learning paper (say, 2017) well enough to explain to a friend the paper's main problem and contribution.

#### what we want for writing

#### what we want for code

#### what we want for figures



