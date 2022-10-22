# Question
Write a function to implement clustering algorithm based on the centroid distance

# Solution
```{cpp}
#include <cstdint>
#include <iostream>
#include <limits>
#include <algorithm>
#include <vector>
#include <cassert>
#include <random>

using namespace std;


/*****

General comment to the evaluator:

what does it mean to be sum of points x_i \in R^3 
You have to explicitly specify that

******/

struct Point {
    float x;
    float y;
    float z;
};

/* Enter your code here. */
class Clustering {
    vector<Point> points;
    vector<Point> centroids;
    vector<size_t> labels;
    int n_clusters;
    int n_iterations;
    int seed;
    
    public:
    Clustering(int n_clusters, int n_iterations, int seed = 0)
    {
        //Insert Cluster Points
        this->n_clusters = n_clusters;
        
        for(int i = 0; i < this->n_clusters; ++i)
        {
            this->centroids.push_back({0.0, 0.0, 0.0});
        }
        
        this->n_iterations = n_iterations;
        this->seed = seed;
        // Insert Centroid Points
    }
    
    vector<Point> Cluster(vector<Point> inputs, vector<size_t> &labels)
    {
        this->points = inputs;
        
        // random clustering
        default_random_engine myrand_engine;
        myrand_engine.seed(this->seed);
        normal_distribution<float> distribution(0.0,10.0);
        
        
        // randomly initialize vector
        for (int i=0; i<this->n_clusters; ++i) 
        {
            float x = distribution(myrand_engine);
            float y = distribution(myrand_engine);
            float z = distribution(myrand_engine);
            this->centroids.at(i)= {x, y, z};
        }
        
        for(int k = 0 ; k< this->n_iterations; k++)
        {
            this->labels = Assignment();
            Update();
        }
        labels = this->labels;
        
        return this->centroids;
    }
    
    float L2Norm(Point P1, Point P2)
    {
        float x2 = (P1.x - P2.x)*(P1.x - P2.x);
        float y2 = (P1.y - P2.y)*(P1.y - P2.y);
        float z2 = (P1.z - P2.z)*(P1.z - P2.z);
        
        return (x2 + y2 + z2);
        
    }
    vector <size_t> Assignment()
    {
        vector<float> L;
        vector<size_t> argL;
        for(Point p: this->points)    
        {
            float min_distance = 20000.0; // Really high distance
            int arg_min = 200000;
            int arg = 0;
            for (Point c: this->centroids)
            {
                float distance = L2Norm(c, p);
                
                if(distance < min_distance)
                {
                    min_distance = distance;
                    arg_min = arg;
                }
                arg++;
            }
            L.push_back(min_distance);

            //printf("%d\t",arg_min);
            argL.push_back(arg_min);
        }
        //printf("\n");
        return argL;
    }
    void Update()
    {
        vector <Point> new_centroid;
        new_centroid = this->centroids;
        for(int j = 0; j < int(this->centroids.size()); ++j)
        {
            float sum_numerator_x = 0;
            float sum_numerator_y = 0;
            float sum_numerator_z = 0;
            float sum_denom = 0;
            for(int i = 0; i < int(this->points.size()); ++i)
            {
                if(this->labels.at(i) == j)
                {
                    sum_numerator_x+= this->points.at(i).x;
                    sum_numerator_y+= this->points.at(i).y;
                    sum_numerator_z+= this->points.at(i).z;
                    sum_denom += 1;
                }
            }
            new_centroid.at(j) = {sum_numerator_x/sum_denom, sum_numerator_y/sum_denom,sum_numerator_z/sum_denom};
        }
        this->centroids = new_centroid;
    }
    
};

int main() {
    // Define which test case to run
    int test_number = 0;
    cin >> test_number;
        
    // Sample vectors
    std::vector<Point> sample_in_0 = {
        {-11.4860,    5.5058,   -9.0644},
        {-11.1426,    4.8875,   -8.1357},
        { 10.9231,    0.3666,   -3.5779},
        {-12.9427,    8.3412,   -5.9818},
        {-10.0903,    5.3482,   -8.7261},
        {-11.5049,    6.7360,   -7.7034},
        {  5.7238,  -14.0290,    4.2147},
        {  5.2085,  -15.4755,    3.4246},
        { 11.2001,    0.9678,   -1.0240},
        { 11.3687,   -0.6454,   -3.8518},
        { 11.0813,    0.1786,   -3.1050},
        {  6.5185,  -13.3054,    4.1873},
        { 11.4567,    0.0249,   -3.0829},
        {  7.1574,  -14.5416,    3.9704},
        {  8.4637,  -13.5819,    2.3469},
    };

    std::vector<Point> sample_in_1 = {
        { -3.3311,  -17.2487,    0.6263},
        { -2.5003,  -19.0799,   -1.0433},
        { -2.5524,  -20.3855,   -1.0302},
        { 12.2500,   -0.1451,   -0.7969},
        { 12.8404,   -0.2285,    1.5140},
        {-25.5839,    0.3063,    6.1142},
        {-24.7935,    0.5205,    5.9570},
        { -3.0146,  -18.5141,   -1.0926},
        { 10.1120,   -1.2544,   -0.1439},
        {-23.4916,   -0.8105,    6.6513},
        { -5.4538,  -20.6453,    0.1573},
        { 10.0714,   -1.0966,   -1.0421},
        {-24.5679,    2.1275,    5.7701},
        { 11.2001,   -1.5779,    1.0244},
        {-24.4899,   -0.2897,    7.3753},
    };    

    // Run tests
    Clustering c(3, 10);
    std::vector<std::size_t> labels;
    
    if (test_number == 0) {
        auto centroids = c.Cluster(sample_in_0, labels);
    } else if (test_number == 1) {
        auto centroids = c.Cluster(sample_in_1, labels);
    }

    // Print the labels
    for (auto l : labels) {
        std::cout << l << std::endl;
    }

    return 0;
} 

```

# Expected Output

```{txt}
0
0
1
0
0
0
2
2
1
1
1
2
1
2
2
```
