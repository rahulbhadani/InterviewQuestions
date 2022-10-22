# Question
Create a simple linked list and show how you would remove the 3rd node from the end.

## My notes (not an actual solution)

```{cpp}
struct LL;
struct LL
{
    int item;
    LL* next;
    LL* previous;
}


LL list;
list.item = 20;
list->next = NULL;

//30->20
LL newitem;
newitem.item = 30;
newitem->next = list;
list = newitem;

//50->40->30->20->10

// SIZE N
// 5-3+1
LL* RemoveThirdFromTheEnd(LL *Head)
{
   
    int N = 0
    LL* LLTemp;
    LLTemp = Head;
    while(LLTemp->next != NULL)
    {
        LLTemp = LLTemp->next;
        N++;
    }
    // N = number of nodes
    i = 0;
    k = 56
    N= 23
    30 =P
    Previous = 40
    Previous->next = P->next
    while(i < N- k + 1)
    {
        Previous = Head;
        Head=Head->next;
    }
    if (k<N)
    { Previous->next = Head->next;}

   
   if(k<N)
       return NULL;
   else

           

}

vector<string> split(string input, char delimiter);

//# 2
double expression(string expr)//Inpt = 1 10 2 / +
{
    vector<string> splits = spli(expr); // ["1", "10", "2", "/", "+"]
    vector<int> numbers; // number \in \N
    vector<char> operators; // operators \in [+,-, \, *]
    for(int i = 0; i  < split.size(); ++i)
    {
        if( check_number(splits.at(i)))
        {
            numbers.push_back(to_int(splits.at(i)));
        }
        else if(check_op(splits.at(i)))
        {
            operators.push_back(splits.at(i));
        }
    }
    numbers = [1, 10, 2, 7]
    operators= ['/', '+', '@']

    1. [1, 10, 2/7]
    2. [1, 10 + 2/7]

    
    int i = numbers.size();//
    i = i -1;
    int c =0;
    double vals = 0;
    while(true)
    {
        switch(operators.at(c))
        {
            case '/':
                vals = numbers(i-1)/numbers(i); [1, 5]
                numbers.at(i-1) = vals; // [1, 10/2] = [1, 5]
                numbers.pop_back();
                break;
            case '+':
                vals = numbers(i-1)+numbers(i); [1+5, 5]
                numbers.at(i-1) = vals; [6,5]
                numbers.pop_back();[6];
                break;
            case '-':
                vals = numbers(i-1)-numbers(i); [1, 5]
                numbers.at(i-1) = vals; 
                numbers.pop_back();
                break;
            case '*':
                vals = numbers(i-1)*numbers(i); [1, 5]
                numbers.at(i-1) = vals; 
                numbers.pop_back();
               break;
            case '@':
                vals = numbers(i)*numbers(i);
                numbers.at(i) = vals
        }
        c++;
        if(c == operator.size())
            break;
    }
    return numbers(end);

}

```
