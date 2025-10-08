# 134 quant finance questions
1. **Tags:** `probability` `expectation` `uniform-distribution`  
   Let $\{X_1,X_2,...,\}$ be an independent sample from uniform distribution on $[0,1]$. Let $N$ be the smallest integer for which $X_1+X_2+...+X_n>1$.Evaluate $\mathbb{E}(N)$.
   
   **Answer:** $\mathbb{E}(N) = e$
   
   **Solution:** Let $S_n = X_1 + X_2 + \cdots + X_n$. We want $\mathbb{E}(N)$ where $N = \min\{n : S_n > 1\}$.
   
   By renewal theory, $\mathbb{E}(N) = 1 + \mathbb{E}(N | S_1 \leq 1) \cdot P(S_1 \leq 1)$.
   
   Since $X_i \sim \text{Uniform}(0,1)$, we have $P(S_1 \leq 1) = P(X_1 \leq 1) = 1$.
   
   Using the fact that $S_n$ has a distribution related to the Irwin-Hall distribution, and through integration:
   $$\mathbb{E}(N) = \sum_{n=1}^{\infty} P(N \geq n) = \sum_{n=1}^{\infty} P(S_{n-1} \leq 1) = \sum_{n=0}^{\infty} \frac{1}{n!} = e$$

2. **Tags:** `combinatorics` `permutations` `derangements`  
   (Dearrangement problem) Same method apply on finite case with not same answer
   
 Find the number of derangements of $n$ objects (permutations with no fixed points) and show that the probability of a random permutation being a derangement approaches $1/e$ as $n \to \infty$. 
   
   **Answer:** $D_n = n! \sum_{k=0}^{n} \frac{(-1)^k}{k!}$ and $\lim_{n \to \infty} \frac{D_n}{n!} = \frac{1}{e}$
   
   **Solution:** Using inclusion-exclusion principle:
   - Let $A_i$ be the event that element $i$ is in its original position
   - $D_n = n! - |A_1 \cup A_2 \cup \cdots \cup A_n|$
   - By inclusion-exclusion: $|A_1 \cup \cdots \cup A_n| = \sum_{k=1}^{n} (-1)^{k+1} \binom{n}{k} (n-k)!$
   - This gives: $D_n = n! \sum_{k=0}^{n} \frac{(-1)^k}{k!}$
   - As $n \to \infty$: $\frac{D_n}{n!} \to \sum_{k=0}^{\infty} \frac{(-1)^k}{k!} = e^{-1} = \frac{1}{e}$

3. **Tags:** `maximum-likelihood` `uniform-distribution` `unbiased-estimator` `expectation`  
   Let $X_1, X_2, \ldots, X_n$ be an independent sample from a uniform distribution on $[0, \theta]$, where $\theta > 0$ is an unknown parameter.
   
   a) Find the maximum likelihood estimator (MLE) $\hat{\theta}_{MLE}$ for $\theta$.
   
   b) Show that $\hat{\theta}_{MLE}$ is biased and calculate its bias.
   
   c) Find an unbiased estimator for $\theta$ based on the MLE.
   
   d) Calculate $\mathbb{E}[\hat{\theta}_{MLE}]$ and $\text{Var}(\hat{\theta}_{MLE})$.
   
   **Answers:**
   
   a) $\hat{\theta}_{MLE} = X_{(n)} = \max(X_1, X_2, \ldots, X_n)$
   
   b) $\text{Bias} = \mathbb{E}[\hat{\theta}_{MLE}] - \theta = -\frac{\theta}{n+1}$
   
   c) $\hat{\theta}_{unbiased} = \frac{n+1}{n} X_{(n)}$
   
   d) $\mathbb{E}[\hat{\theta}_{MLE}] = \frac{n\theta}{n+1}$ and $\text{Var}(\hat{\theta}_{MLE}) = \frac{n\theta^2}{(n+1)^2(n+2)}$
   
   **Solution:**
   
   a) The likelihood function is $L(\theta) = \frac{1}{\theta^n}$ for $\theta \geq \max(x_i)$, and 0 otherwise.
      This is maximized when $\theta$ is as small as possible, so $\hat{\theta}_{MLE} = X_{(n)}$.
   
   b) The CDF of $X_{(n)}$ is $F_{X_{(n)}}(x) = \left(\frac{x}{\theta}\right)^n$ for $0 \leq x \leq \theta$.
      The PDF is $f_{X_{(n)}}(x) = \frac{nx^{n-1}}{\theta^n}$.
      So $\mathbb{E}[X_{(n)}] = \int_0^\theta x \cdot \frac{nx^{n-1}}{\theta^n} dx = \frac{n\theta}{n+1}$.
      Bias = $\frac{n\theta}{n+1} - \theta = -\frac{\theta}{n+1}$.
   
   c) To make it unbiased: $\mathbb{E}\left[\frac{n+1}{n} X_{(n)}\right] = \frac{n+1}{n} \cdot \frac{n\theta}{n+1} = \theta$.
   
   d) $\mathbb{E}[X_{(n)}^2] = \int_0^\theta x^2 \cdot \frac{nx^{n-1}}{\theta^n} dx = \frac{n\theta^2}{n+2}$.
      So $\text{Var}(X_{(n)}) = \frac{n\theta^2}{n+2} - \left(\frac{n\theta}{n+1}\right)^2 = \frac{n\theta^2}{(n+1)^2(n+2)}$. 

4. **Tags:** `linear-regression` `least-squares` `gauss-markov` `ols` `hypothesis-testing`  
   Consider the simple linear regression model: $Y_i = \beta_0 + \beta_1 X_i + \epsilon_i$ for $i = 1, 2, \ldots, n$, where $\epsilon_i \sim N(0, \sigma^2)$ are independent.
   
   a) Derive the ordinary least squares (OLS) estimators $\hat{\beta}_0$ and $\hat{\beta}_1$.
   
   b) Show that $\hat{\beta}_1$ is unbiased and find $\text{Var}(\hat{\beta}_1)$.
   
   c) Prove that $\hat{\beta}_1$ is the Best Linear Unbiased Estimator (BLUE) for $\beta_1$.
   
   d) Derive the distribution of $\frac{\hat{\beta}_1 - \beta_1}{SE(\hat{\beta}_1)}$ and construct a 95% confidence interval for $\beta_1$.
   
   e) Test the hypothesis $H_0: \beta_1 = 0$ vs $H_1: \beta_1 \neq 0$ at significance level $\alpha = 0.05$.
   
   **Answers:**
   
   a) $\hat{\beta}_1 = \frac{\sum_{i=1}^n (X_i - \bar{X})(Y_i - \bar{Y})}{\sum_{i=1}^n (X_i - \bar{X})^2} = \frac{S_{XY}}{S_{XX}}$ and $\hat{\beta}_0 = \bar{Y} - \hat{\beta}_1 \bar{X}$
   
   b) $\mathbb{E}[\hat{\beta}_1] = \beta_1$ and $\text{Var}(\hat{\beta}_1) = \frac{\sigma^2}{\sum_{i=1}^n (X_i - \bar{X})^2} = \frac{\sigma^2}{S_{XX}}$
   
   c) By the Gauss-Markov theorem, $\hat{\beta}_1$ is BLUE.
   
   d) $\frac{\hat{\beta}_1 - \beta_1}{SE(\hat{\beta}_1)} \sim t_{n-2}$ where $SE(\hat{\beta}_1) = \sqrt{\frac{\hat{\sigma}^2}{S_{XX}}}$
      
      95% CI: $\hat{\beta}_1 \pm t_{n-2,0.025} \cdot SE(\hat{\beta}_1)$
   
   e) Test statistic: $t = \frac{\hat{\beta}_1}{SE(\hat{\beta}_1)} \sim t_{n-2}$ under $H_0$
      
      Reject $H_0$ if $|t| > t_{n-2,0.025}$
   
   **Solution:**
   
   a) Minimize $SSE = \sum_{i=1}^n (Y_i - \beta_0 - \beta_1 X_i)^2$
      
      $\frac{\partial SSE}{\partial \beta_0} = -2\sum_{i=1}^n (Y_i - \beta_0 - \beta_1 X_i) = 0$
      
      $\frac{\partial SSE}{\partial \beta_1} = -2\sum_{i=1}^n X_i(Y_i - \beta_0 - \beta_1 X_i) = 0$
      
      Solving these normal equations gives the OLS estimators.
   
   b) $\hat{\beta}_1 = \sum_{i=1}^n c_i Y_i$ where $c_i = \frac{X_i - \bar{X}}{S_{XX}}$
      
      $\mathbb{E}[\hat{\beta}_1] = \sum_{i=1}^n c_i \mathbb{E}[Y_i] = \sum_{i=1}^n c_i (\beta_0 + \beta_1 X_i) = \beta_1$
      
      $\text{Var}(\hat{\beta}_1) = \sum_{i=1}^n c_i^2 \text{Var}(Y_i) = \sigma^2 \sum_{i=1}^n c_i^2 = \frac{\sigma^2}{S_{XX}}$
   
   c) Among all linear unbiased estimators of the form $\sum a_i Y_i$, $\hat{\beta}_1$ has minimum variance by Gauss-Markov theorem.
   
   d) Under normality, $\hat{\beta}_1 \sim N\left(\beta_1, \frac{\sigma^2}{S_{XX}}\right)$
      
      With $\hat{\sigma}^2 = \frac{SSE}{n-2}$, we have $\frac{\hat{\beta}_1 - \beta_1}{SE(\hat{\beta}_1)} \sim t_{n-2}$
   
   e) Under $H_0: \beta_1 = 0$, the test statistic follows $t_{n-2}$ distribution.
      Critical region: $|t| > t_{n-2,0.025}$ 

5. **Tags:** `algorithms` `financial-engineering` `time-series` `optimization` `data-structures`  
   **Question 4.7 :** How to implement rolling max drawdown function?
   
   Given a time series of asset prices or portfolio values, implement an efficient algorithm to compute the rolling maximum drawdown over a specified window.
   
   **Definition:** Maximum drawdown is the largest peak-to-trough decline in value over a given period, expressed as a percentage: $\text{MDD} = \frac{\text{Peak} - \text{Trough}}{\text{Peak}} \times 100\%$
   
   **Requirements:**
   - Input: Array of prices/values and window size
   - Output: Array of rolling max drawdowns
   - Time complexity should be optimized
   - Handle edge cases (window size, negative values, etc.)
   
   **Answer:**
   
   **Algorithm:** Use a deque-based approach with sliding window maximum tracking.
   
   **Time Complexity:** O(n) where n is the length of the time series
   **Space Complexity:** O(k) where k is the window size
   
   **Implementation Strategy:**
   ```python
   from collections import deque
   
   def rolling_max_drawdown(prices, window):
       n = len(prices)
       if n < window:
           return []
       
       result = []
       max_deque = deque()  # Store indices of potential maximums
       
       for i in range(n):
           # Remove elements outside current window
           while max_deque and max_deque[0] <= i - window:
               max_deque.popleft()
           
           # Remove elements smaller than current (they can't be max)
           while max_deque and prices[max_deque[-1]] <= prices[i]:
               max_deque.pop()
           
           max_deque.append(i)
           
           # Calculate drawdown for current window
           if i >= window - 1:
               window_start = i - window + 1
               window_max = prices[max_deque[0]]
               window_min = min(prices[window_start:i+1])
               
               drawdown = (window_max - window_min) / window_max * 100
               result.append(drawdown)
       
       return result
   ```
   
   **Optimized Version:**
   ```python
   def rolling_max_drawdown_optimized(prices, window):
       from collections import deque
       
       n = len(prices)
       result = []
       max_deque = deque()
       min_deque = deque()
       
       for i in range(n):
           # Maintain max deque
           while max_deque and max_deque[0] <= i - window:
               max_deque.popleft()
           while max_deque and prices[max_deque[-1]] <= prices[i]:
               max_deque.pop()
           max_deque.append(i)
           
           # Maintain min deque for current window
           while min_deque and min_deque[0] <= i - window:
               min_deque.popleft()
           while min_deque and prices[min_deque[-1]] >= prices[i]:
               min_deque.pop()
           min_deque.append(i)
           
           if i >= window - 1:
               peak = prices[max_deque[0]]
               trough = prices[min_deque[0]]
               drawdown = (peak - trough) / peak * 100 if peak > 0 else 0
               result.append(drawdown)
       
       return result
   ```
   


6. **Tags:** `probability` `stochastic-processes` `martingales` `markov-chains` `hitting-probabilities` `gambler-ruin`  
   (Gambler's Ruin) A gambler starts with capital $i$ ($1 \le i \le N-1$) and plays independent $\pm 1$ bets: wins $+1$ with probability $p$ and loses $1$ with probability $q = 1-p$. The game stops when the capital hits $0$ or $N$. Let 
   $$ T = \min\{ n \ge 0 : X_n \in \{0, N\}\}, \qquad X_{0} = i. $$
   (a) Compute $P_i = \mathbb{P}_i(\text{hit } N \text{ before } 0)$ for $0<p<1$.  
   (b) Simplify for $p = 1/2$.  
   (c) Find $E_i = \mathbb{E}_i[T]$ for $p \ne 1/2$.  
   (d) Simplify $E_i$ for $p = 1/2$.  
   (e) Let $N\to\infty$ with fixed $i$ and $p<1/2$. Find $\lim_{N\to\infty} P_i$ and interpret.  
  
   **Answers:**  
   a) $p \ne q$: $$P_i = \frac{1 - (q/p)^i}{1 - (q/p)^N}.$$  
   b) $p = 1/2$: $P_i = i/N$.  
   c) $p \ne 1/2$: $$E_i = \frac{i}{q-p} - \frac{N}{q-p} \cdot \frac{1 - (q/p)^i}{1 - (q/p)^N} = \frac{i - N P_i}{q - p}.$$ 
   d) $p = 1/2$: $E_i = i(N-i)$.  
   e) If $p<1/2$: $\lim_{N\to\infty} P_i = 0$ (ruin w.p. 1 with an infinite upper target).  
  
   **Solution:**  
   a) Hitting probability: $P_0=0$, $P_N=1$, and for $1\le i\le N-1$, $ P_i = p P_{i+1} + q P_{i-1}.$
   Solve $p u_{i+1} - u_i + q u_{i-1}=0$. For $p\ne q$, $u_i = A + B (q/p)^i$. Apply boundaries: $A+B=0$, $A + B (q/p)^N = 1$. Hence 
   $$ P_i = \frac{1 - (q/p)^i}{1 - (q/p)^N}. $$
   b) For $p=1/2$, recurrence $P_i = (P_{i+1}+P_{i-1})/2$ gives linear $P_i = ai+b$, with $P_0=0$, $P_N=1$ so $P_i=i/N$. Limit from (a) matches via expansion $(q/p)^x = e^{x\log(q/p)}$.  
   c) Expected duration: $E_0=E_N=0$ and $E_i = 1 + p E_{i+1} + q E_{i-1}$. Rearranged: $pE_{i+1} - E_i + qE_{i-1} = -1$. Try $Ci$ as particular solution: $C(p-q)=-1 \Rightarrow C=1/(q-p)$. General: $E_i = A + B(q/p)^i + i/(q-p)$. Apply boundaries: $A+B=0$ and $A + B(q/p)^N + N/(q-p)=0$ so $B = -\dfrac{N}{(q-p)[(q/p)^N-1]}$. Substitute to obtain the stated form, or simplify to $E_i = (i - N P_i)/(q-p)$.  
   d) For $p=1/2$: $E_{i+1} - 2E_i + E_{i-1} = -2$. Quadratic trial $ai^2+bi+c$ yields $a=-1$, with $c=0$ and $b=N$, so $E_i = i(N-i)$. This is the $p\to 1/2$ limit of the general formula (expand $(q/p)^i$).  
   e) If $p<1/2$, then $q>p$ and $(q/p)^N \to \infty$, so $P_i\to 0$: negative drift implies almost sure ruin with an infinitely distant upper boundary. (If $p>1/2$, $P_i\to 1$.)  
  


7. **Tags:** `optimal-betting` `kelly-criterion` `risk-management` `utility-maximization` `coin-flip`  
   You are in a one-on-one coin-flip gambling game. Your opponent has 1 million dollars on hand (the max you can bet is 1 million dollars). If the result is tail, you win 2x your bet; else, you lose your bet.
   How much would you bet?
   
   **Answer:** The optimal bet depends on your current wealth $W$ and risk preferences. Using Kelly criterion: bet $f^* W$ where $f^* = \frac{p(b+1) - 1}{b} = \frac{0.5 \times 3 - 1}{2} = 0.25$ (25% of wealth).
   
   **Solution:**
   
   **Setup:** Fair coin (heads/tails each probability 0.5), win 2:1 on tails, lose bet on heads. Maximum bet is $1M.
   
   **Kelly Criterion Analysis:**
   For a bet of fraction $f$ of wealth $W$:
   - Win probability: $p = 0.5$
   - Odds: $b = 2$ (win $2 for each $1 bet)
   - Kelly formula: $f^* = \frac{p(b+1) - 1}{b} = \frac{0.5 \times 3 - 1}{2} = 0.25$
   
   **Expected Utility Maximization:**
   With logarithmic utility $U(x) = \log(x)$, expected utility after bet $B$:
   $$E[U] = 0.5 \log(W + 2B) + 0.5 \log(W - B)$$
   
   Maximize by setting $\frac{dE[U]}{dB} = 0$:
   $$\frac{1}{W + 2B} + \frac{-1}{2(W - B)} = 0$$
   
   Solving: $\frac{2}{2(W + 2B)} = \frac{1}{2(W - B)} \Rightarrow 2(W - B) = W + 2B \Rightarrow B = \frac{W}{4}$
   
  

  
   
