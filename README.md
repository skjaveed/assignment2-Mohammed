# assignment2-Mohammed
# Javeed Mohammed
###### My Favorite place in world is my Hometown and my Home
my parents live at my hometown and I have completed my undergrad and I belong to India 
My Hometown is **Guntur** and its state is **Andhrapradesh**


# Un ordered List 
*   I bring party clothers to my place 
    * Pair of shoes
    * Camera  
    * Shades
* Rent a Bike to enjoy maximum

**[AboutMe](https://github.com/skjaveed/assignment2-Mohammed/blob/main/AboutMe.md)**
# Food and Drinks
|FoodandDrinks |location            | money to pay|
|--------------|--------------------|-----------------------|
|Mutton Biryani |Guntur (home town) | 250                |
|rice           |Hotel Bilal(Guntur)| 100             |
|Faluda         |Hyderabad          | 50                   |
|coke           |any store          | 50            |

***Quatations***
# Pithy Qoutes
> 'You can't cross the sea merely by standing and staring at the water.’*-Sir Ravindranadh Tagore* <br>

> When something is important enough, you do it even if the odds are not in your favor.*-Elon Musk*

***code***
# Dynamic Programming on Broken Profile. Problem "Parquet"

>finding number of ways to fully fill an area (e.g. chessboard/grid) with some figures (e.g. dominoes)

[Link to the source](https://cp-algorithms.com/dynamic_programming/profile-dynamics.html)

int n, m;
vector < vector<long long> > dp;


void calc (int x = 0, int y = 0, int mask = 0, int next_mask = 0)
{
    if (x == n)
        return;
    if (y >= m)
        dp[x+1][next_mask] += dp[x][mask];
    else
    {
        int my_mask = 1 << y;
        if (mask & my_mask)
            calc (x, y+1, mask, next_mask);
        else
        {
            calc (x, y+1, mask, next_mask | my_mask);
            if (y+1 < m && ! (mask & my_mask) && ! (mask & (my_mask << 1)))
                calc (x, y+2, mask, next_mask);
        }
    }
}


int main()
{
    cin >> n >> m;

    dp.resize (n+1, vector<long long> (1<<m));
    dp[0][0] = 1;
    for (int x=0; x<n; ++x)
        for (int mask=0; mask<(1<<m); ++mask)
            calc (x, 0, mask, 0);

    cout << dp[n][0];

}
[link to the source](https://cp-algorithms.com/dynamic_programming/profile-dynamics.html)
