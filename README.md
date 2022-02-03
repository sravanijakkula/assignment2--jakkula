# assignment2--jakkula
webApps assignment2
modified file
# jakkula
###### Hyderabad Biryani
**Ambience** of this restaurant is **beautiful** and the **environment** is **peaceful**. It is near to city's most attractive point where students hangout most. It is a fun loving spot.

---

# My Favourite Restaurant
The nearest airport is Gannavaram Airport

1. Take Right at the enterance of the airport and Walk for 15 minutes.
2. Take Left and walk ahead for 3 minutes, you will reach a junction.
3. At junction take left and continue walking for 10 minutes.
4. After 10 minutes walk take 2nd right to reach Hyderabad Biryani at your right side 2nd buliding.

* The best food items one must try in Hyderabad Biryani 
    * Chicken pepper sause sticks
    * Drum Sticks
    * Hyderabadi Dum Biryani
    * Mutton special Biryani
---

![Link to my AboutMe.md](https://github.com/sravanijakkula/assignment2--jakkula/blob/main/AboutMe.md)

---
# Sports/Activities
Table describes about the sports that iam interested and<br>would like to suggest to my friends in order to make them interested and physically active.<br> First column shows the Name of sports/activities.<br>Second column shows the Location and Third column represents the amount need to pay for personal equipment.

| Sports_Name | Location | Amount |
|:---         |:---      |:---    |
| Kabbadi     | Kabbadi court | $20,Knee_pads |
| Volley Ball | Volley Ball court | $50-Teeshirt,$30-handgloveses |
| Basket Ball | Basket Ball court | $50-Teeshirt,$100-Ball |
| Badminton   | Badminton court   | $150-Bat,$20-cock |
---

---
# Quotes
>It always seems impossible,until its done by Nelson Mandela.
>
>you will face many defeats in life, but never let yourself be defeated by Maya Angelou.
---

---
# Code Fencing
>In computer science, 2-satisfiability, 2-SAT or just 2SAT is a computational problem of assigning values to variables, each of which has two possible values, in order to satisfy a system of constraints on pairs of variables. It is a special case of the general Boolean satisfiability problem, which can involve constraints on more than two variables, and of constraint satisfaction problems, which can allow more than two choices for the value of each variable. But in contrast to those more general problems, which are NP-complete, 2-satisfiability can be solved in polynomial time.

<https://en.wikipedia.org/wiki/2-satisfiability>

```
int n;
vector<vector<int>> adj, adj_t;
vector<bool> used;
vector<int> order, comp;
vector<bool> assignment;

void dfs1(int v) {
    used[v] = true;
    for (int u : adj[v]) {
        if (!used[u])
            dfs1(u);
    }
    order.push_back(v);
}

void dfs2(int v, int cl) {
    comp[v] = cl;
    for (int u : adj_t[v]) {
        if (comp[u] == -1)
            dfs2(u, cl);
    }
}

bool solve_2SAT() {
    order.clear();
    used.assign(n, false);
    for (int i = 0; i < n; ++i) {
        if (!used[i])
            dfs1(i);
    }

    comp.assign(n, -1);
    for (int i = 0, j = 0; i < n; ++i) {
        int v = order[n - i - 1];
        if (comp[v] == -1)
            dfs2(v, j++);
    }

    assignment.assign(n / 2, false);
    for (int i = 0; i < n; i += 2) {
        if (comp[i] == comp[i + 1])
            return false;
        assignment[i / 2] = comp[i] > comp[i + 1];
    }
    return true;
}

void add_disjunction(int a, bool na, int b, bool nb) {
    // na and nb signify whether a and b are to be negated 
    a = 2*a ^ na;
    b = 2*b ^ nb;
    int neg_a = a ^ 1;
    int neg_b = b ^ 1;
    adj[neg_a].push_back(b);
    adj[neg_b].push_back(a);
    adj_t[b].push_back(neg_a);
    adj_t[a].push_back(neg_b);
}
```

<https://cp-algorithms.com/graph/2SAT.html>
---






