# Question

Suppose we have a set of weights at our disposal using which we intend to measure certain weights. Given the target weight (T) compute the number of ways to achieve that.

# Example

```{txt}
set of weights: 100g, 500g, 1000g

and target = 5000g

m*100 + n*500 + k*1000  = 5000

m*w1 + n*w2 + k*w3 = T


weights = {1, 2, 3}, T = 5
answer: 5
1+1+1+1+1 = 5
1+3+1 = 5
1+1+1+2 = 5
1+2+2 = 5
2+3 = 5


m = T/w1

# possible = [1 ... m] = mC1
# 

# min(w) = w0
T1 = T - w0// 4

//
T = 2
w1 = 1
w2 = 2

T1 = T - w1 // 1
T2 = T1 - w2
T2 = T - w1 - w2
if(T2 == 0)
    we are done


1, 2, 3
T1 = getting 1
T2 = getting 2
T3 = getting 3
T4 = getting 4
1/1
```

## My notes (not an actual solution)

```{cpp}

int numberOfWays(vector<int>& weights, int Target)//weights are sorted
{

    int w1 = weights.pop_back();
    

    vector<int> a1 = new vector<int>(Target+1);
    
    

    int Target_ = Target;
    numberOfWays(weights, Tatget_)

}

struct Node;
struct Node
{
    int value;
    Node* child;
};


Node* find_pivot(Node* head, int P)
{

    if(head== NULL)
        return NULL;

    
    Node* temp = head;
    int count == 0;
    
    Node* temp2 = head;
    int Length = 0
    while(temp2->child)
    {
        Length++;
        temp2 = temp2->chid;
    }

    P = P%Length;

    while(temp->child)
    {
        temp = temp->child;
        count = count + 1;
        if(count == (Length-P))
            break;
    }
    return temp;
}

pivot = find_pivot(head,P); // O(n)
tail = find_tail(head); // O(n)



newhead = (*pivot)->child
(*tail)->child = *head
(*pivot)->child = NULL
head = newhead
```
