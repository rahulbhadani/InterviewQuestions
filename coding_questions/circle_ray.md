# Question
Given a list of (x, y, r) circles on a 2D plane, calculate (-π, π] angle ranges where ray from origin does not hit a circle.

# My notes (may not be an actual solution)

```
struct circles
{
    // private:
        double x;
        double y;
        double r;
        double phi; //angle location of circle
        double alpha;//angular location of first tangent
        double beta;//angular location of the second tanget
};


vector<circles> sort(vector<circles>);

struct range{
    double start;
    double end;
};

vector<range> calc_range(vector<circles> C)
{
    for(int i  = 0; i < C.size() ; ++i)
    {
        C.at(i).phi = atan(C.at(i).y/C.at(i).x);
        C.at(i).alpha = C.at(i).phi  - asin(C.at(i).r/sqrt(C.at(i).x*C.at(i).x + C.at(i).y*C.at(i).y)); //phi - arc_sine(r0/sqrt(x0^2 + y0^2))
        C.at(i).beta = C.at(i).phi  + asin(C.at(i).r/sqrt(C.at(i).x*C.at(i).x + C.at(i).y*C.at(i).y)); //phi + arc_sine(r0/sqrt(x0^2 + y0^2))
    }
    
    vector<circles> sort_C = sort(C);
    
    vector<double> alphas;
    vector<double> betas;
    
    alphas.push_back(sort_C.at(0).alpha);
    betas.push_back(sort_C.at(0).beta);
    for(int i= 1; i < sort_C.size(); ++i)
    {
        if(C.at(i).alpha < C.at(i-1).alpha)
        {
            
        } 
    }
    
    
    
    return v_range;
}
```
