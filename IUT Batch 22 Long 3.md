# A - Even, Odd Phenomenon
The idea behind this problem is simple, the statement literally tells you what to do, if the number is even divide that by 2, and if the number is even, multiply it by 3 and add 1 to it. To check if a number is odd you can check the remainder upon dividing it by 2, which in simple terms is the mod operation that gives you the remainder. if ```cpp n%2==0``` this implies that the number is even as dividing by 2 yields a value of 0 and similarly if ```cpp n%2!=0``` or in other words if n mod 2 = 1 means that the number is odd as the division of 2 with an odd number yields a remainder of 1.
```cpp
#include <bits/stdc++.h>
 
#define endl "\n"
typedef long long ll;
using namespace std;
 
int main()
{
    ll n;
    cin>>n;
    while(n!=1){
        cout<<n<<" ";
        if(n%2==0){
            n/=2;
        }
        else{
            n=n*3+1;
        }
    }
    cout<<n<<endl;
    return 0;
}
```

# B - Where is the Number?
For this problem, it can be done using an array or a vector to store the inputs. Vectors were discussed in class and it was emphasized that vectors are superior to arrays so we are going to go with vectors. In a vector add the elements, and then loop over the elements of the vector from i -> 0 to n-1. If the value of v[i]!=i+1 that means that the value i+1 is missing. Now why i+1, since the loop is from 0 to n-1 and we want to check if numbers 1 to n is present, checking with i+1 satisfies that requirement. 
```cpp
#include <bits/stdc++.h>
 
#define fastio                        \
    ios_base::sync_with_stdio(false); \
    cin.tie(NULL)
 
#define endl "\n"
typedef long long ll;
using namespace std;
 
int main()
{
    fastio;
    ll n;
    cin>>n;
    vector<ll>v;
    ll x;
    while(cin>>x){
        v.push_back(x);
    }
    sort(v.begin(),v.end());
    for(int i=0;i<n;i++){
        if(v[i]!=i+1){
            cout<<i+1<<endl;
            break;
        }
    }
    return 0;
}
```

# C - What Moves?
This problem is also pretty simple, we want to know the minimum number of moves to make the array sorted in ascending order such that every element is at least as large as the previous element. To do this one can simply check if $a_i$ < $a_{i-1}$, if this condition is satisfied, you add the difference between $a_{i-1}$ and $a_i$ to the answer. And then to make the numbers balanced assign $a_i$ = $a_{i-1}$. This ensures that upon performing the moves the values of the array/vector are updated accordingly. 
```cpp
#include <bits/stdc++.h>
 
#define fastio                        \
    ios_base::sync_with_stdio(false); \
    cin.tie(NULL)
 
#define endl "\n"
typedef long long ll;
using namespace std;
 
int main()
{
    fastio;
    ll n;
    cin>>n;
    vector<ll>a(n);
    for(int i=0;i<n;i++){
        cin>>a[i];
    }
    ll ans=0;
    for(int i=1;i<n;i++){
        if(a[i]<a[i-1]){
            ans+=(a[i-1]-a[i]);
            a[i]=a[i-1];
        }
    }
    cout<<ans<<endl;
    return 0;
}
```

# D - Cell Value
This is a mathematical problem, in reality, we have multiple x, and y positions up to say t sets of x and y. Upon getting the values of x and y we can apply the following equation that we derive by observation. See that for the first column all the even positions contain a squared number which is the square of the column value and for the second column, the number is 1 subtracted from the square number. So we can obtain a relationship, let's call it case-I, that is $column^2$ - row + 1. Similarly, we observe that for the first column, the odd positions or the odd rows have the value given by $(column-1)^2$ + row. Now this is only valid while the column is greater than the row. For case II, observe the first row of the third column, it contains a squared number, right? similarly, observe the first row of the fifth column, it contains a squared number. So we can obtain a relationship $row^2$ - column + 1, for every odd row. And similarly, for every even row, we get $(row-1)^2$. Keeping these relationships in mind the 2 cases can be combined and implemented as shown in the code below.
```cpp
#include <bits/stdc++.h>
 
#define fastio   ios_base::sync_with_stdio(false);cin.tie(NULL)
 
#define endl "\n"
typedef long long ll;
using namespace std;
 
 
 
int main()
{
    fastio;
    int t;
    cin >> t;
    
    while(t--)
    {
       ll y,x;
       cin>>y>>x;
       if(x<y){
        if(y%2==0){
            cout<<y*y-x+1<<endl;
        }
        else{
            cout<<(y-1)*(y-1)+x<<endl;
        }
       }
       else{
        if(x%2==0){
            cout<<(x-1)*(x-1)+y<<endl;
        }
        else{
            cout<<x*x-y+1<<endl;
        }
       }
    }
    return 0;
}
```

# E - Don't Fight the Fellow Knight 
This is also a mathematical problem. Here for $1<=k<=n$, we are asked to determine the number of arrangements for a $k * k$ chessboard, such that two knights can be placed without attacking each other. For a k*k chessboard, the number of ways 2 knights can be placed such that they don't attack each other is given by the formula: $(k^2)*(k^2-1)/2 - 4*(k-1)*(k-2)$.
The first term is the total number of ways 2 knights can be placed on a k*k chessboard. The second term is the number of ways 2 knights can be placed such that they attack each other. The second term is calculated by considering the 2*3 and 3*2 chessboards and multiplying them by 4. Since there are 8 ways to place 2 knights on a 2*3 or 3*2 chessboard such that they attack each other. The 2*3 and 3*2 chessboards are subtracted from the k*k chessboard to get the number of ways 2 knights can be placed on a k*k chessboard such that they don't attack each other
```cpp
#include <bits/stdc++.h>
 
#define fastio                        \
    ios_base::sync_with_stdio(false); \
    cin.tie(NULL)
 
#define endl "\n"
typedef long long ll;
using namespace std;
 
int main()
{
    fastio;
    ll n;
    cin>>n;
    for(int i=1;i<=n;i++){
        ll k=i;
        ll ans=(k*k)*(k*k-1)/2 - 4*(k-1)*(k-2);
        cout<<ans<<endl;
    }
    return 0;
}
```

# F - Pile of Coins

```cpp
#include <bits/stdc++.h>
 
#define fastio                        \
    ios_base::sync_with_stdio(false); \
    cin.tie(NULL)
 
#define endl "\n"
 
using namespace std;
 
int main()
{
    fastio;
    int n;
    cin>>n;
    while(n--){
        int a,b;
        cin>>a>>b;
        if((a+b)%3==0 && 2*a>=b && 2*b>=a){
            cout<<"YES"<<endl;
        }
        else{
            cout<<"NO"<<endl;
        }
    }
    return 0;
}
```

# G - Uniqueness 

```cpp
#include <bits/stdc++.h>
using namespace std;
typedef long long ll;
 
int main() {
    int n;
    cin>>n;
    set<ll>s;
    for(int i=0;i<n;i++){
        ll x;
        cin>>x;
        s.insert(x);
    }
    cout<<s.size()<<endl;
 
    return 0;
}
```

# H - Fix them Ladders

```cpp
#include <bits/stdc++.h>
using namespace std;


int main()
{
    int t;
    double x, y, c;
    cin >> t;
    for (int i = 1; i <= t; i++)
    {
        cout << "Case " << i << ": ";
        cin >> x >> y >> c;
        double low = 0.00, high = min(x, y), streetWidth;
        while (high-low>=double(1e-6))
        {
            streetWidth = (low + high) / 2.00;
            double xHeight = sqrt((x * x) - (streetWidth * streetWidth));
            double yHeight = sqrt((y * y) - (streetWidth * streetWidth));
            double computedC=((xHeight * yHeight) / (xHeight + yHeight));
            if (computedC <= c)
            {
                high = streetWidth;
            }
            else
            {
                low = streetWidth;
            }
        }
        printf("%.10f\n",low);
    }
}
```

# I - Ko te Kader Molla

```cpp
#include <bits/stdc++.h>
using namespace std;
#define fastio  ios_base::sync_with_stdio(false);cin.tie(NULL)

int main() {
    fastio;
    string x,y;
    map<string,string>mp;
    int N,Q;
    string tmp;
    getline(cin,tmp);
    N=stoi(tmp);
    while(N--){
        getline(cin,x);getline(cin,y);//input statement
        mp[x]=y;
    }
    getline(cin,tmp);
    Q=stoi(tmp);
    while(Q--){
        getline(cin,x);
        if(mp.find(x)!=mp.end()){
            cout<<mp[x]<<"\n";
        }
    }
  return 0;
}
```

# J - Hmmm... Trees 

```cpp
#include <bits/stdc++.h>
using namespace std;
#define fastio  ios_base::sync_with_stdio(false);cin.tie(NULL)

int main() {
    fastio;
    int T;
    double cnt;
    string tmp;
    getline(cin,tmp);
    T=stoi(tmp);
    map<string,double>mp;
    bool finput=false;
    while(T--){
        if(finput==true)cout<<"\n";
        else{getline(cin,tmp);}
        cnt=0.00;

        while(getline(cin,tmp),!tmp.empty()){
            if(mp.find(tmp)!=mp.end()){
                mp[tmp]++;
            }
            else{
                mp[tmp]=1.00;
            }
            cnt=cnt+1.00;
        }
        for(auto u:mp){
            u.second=(u.second/cnt)*100.00;
            cout<<u.first<<" "<<fixed<<setprecision(4)<<u.second<<'\n';
        }
        mp.clear();
    finput=true;
    }


}
```

# K - Food? 

```cpp
#include <bits/stdc++.h>
using namespace std;
#define fastio  ios_base::sync_with_stdio(false);cin.tie(NULL)

int main() {
    fastio;
    int T;
    double cnt;
    string tmp;
    getline(cin,tmp);
    T=stoi(tmp);
    map<string,double>mp;
    bool finput=false;
    while(T--){
        if(finput==true)cout<<"\n";
        else{getline(cin,tmp);}
        cnt=0.00;

        while(getline(cin,tmp),!tmp.empty()){
            if(mp.find(tmp)!=mp.end()){
                mp[tmp]++;
            }
            else{
                mp[tmp]=1.00;
            }
            cnt=cnt+1.00;
        }
        for(auto u:mp){
            u.second=(u.second/cnt)*100.00;
            cout<<u.first<<" "<<fixed<<setprecision(4)<<u.second<<'\n';
        }
        mp.clear();
    finput=true;
    }


}
```

# L - That looks like a Dictionary 

```cpp
#include <bits/stdc++.h>
#define fastio                    \
    ios_base::sync_with_stdio(0); \
    cin.tie(NULL);
using namespace std;
set<string> s;

int main()
{
    fastio
        string x;
    while (cin >> x)
    {
        string res = "";
        for (int i = 0; i < x.length(); i++)
        {
            if (isalpha(x[i]))
            {
                res += tolower(x[i]);
            }
            else
            {
                if (!res.empty())
                    s.insert(res);
                res = "";
            }
        }
        x=res;
        if (!x.empty())
            s.insert(x);
    }
    for (auto u : s)
    {
        cout << u << endl;
    }
    return 0;
}
```

# M - Hoarder 

```cpp
#include <bits/stdc++.h>
 
#define fastio                        \
    ios_base::sync_with_stdio(false); \
    cin.tie(NULL)
 
#define endl "\n"
typedef long long ll;
using namespace std;
 
int main()
{
    fastio;
    int n;
    cin>>n;
    map<ll,ll>mp;
    for(int i=0;i<n;i++){
        ll u;
        cin>>u;
        mp[u]=i+1;
    }
    int lo=1;
    int rounds=1;
    for(int i=1;i<=n;i++){
        if(mp[i]<lo){
            rounds++;
        }
        lo=mp[i];
    }
    cout<<rounds<<endl;
 
    return 0;
}
```

# N - Can you create that sum? 

```cpp
#include <bits/stdc++.h>
 
#define fastio                        \
    ios_base::sync_with_stdio(false); \
    cin.tie(NULL)
 
#define endl "\n"
typedef long long ll;
using namespace std;
 
int main()
{
    fastio;
    int n;
    cin>>n;
    vector<ll>a(n);
    for(ll &i:a)cin>>i;
    sort(a.begin(),a.end());
    ll k=1;
    for(int i=0;i<n;i++){
        if(k>=a[i]){
            k+=a[i];
        }
        else break;
    }
    cout<<k<<endl;
    return 0;
}
```

# O - Why? 

```cpp
#include <bits/stdc++.h>
 
#define fastio                        \
    ios_base::sync_with_stdio(false); \
    cin.tie(NULL)
 
typedef long long ll;
 
#define endl "\n"
 
using namespace std;
 
int main()
{
    fastio;
    int n;
    cin>>n;
    vector<ll>a(n);
    for(ll &i:a)cin>>i;
    sort(a.begin(),a.end());
    ll median=a[n/2];
    ll cost=0;
    for(int i=0;i<n;i++){
        cost+=abs(a[i]-median);
    }
    cout<<cost<<endl;
    return 0;
}
```

# P - Find That Digit!!! 

```cpp
#include <bits/stdc++.h>
 
#define fastio                        \
    ios_base::sync_with_stdio(false); \
    cin.tie(NULL)
 
#define endl "\n"
typedef long long ll;
using namespace std;
 
char computeAns(ll k){
    ll bound=k;
    ll curr_length_window=1;
    while(true){
        ll power=9*(ll)pow(10,curr_length_window-1)*(curr_length_window);
        if(bound-power<=0){
            break;
        }
        curr_length_window++;
        bound-=power;
    }
    bound--;
    ll div=bound/curr_length_window;
    ll mod=bound%curr_length_window;
    ll num=(ll)pow(10,curr_length_window-1)+div;
    return to_string(num)[mod];
}
 
int main()
{
    fastio;
    int q;
    cin>>q;
    while(q--){
        ll k;
        cin>>k;
        cout<<computeAns(k)<<endl;
    }
    return 0;
}
```

# Q - DJ Remix 

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);
    string sentence;
    cin>>sentence;
    int n=sentence.length();
    int i=0;
    while(i<n-3){
        if(sentence.substr(i,3)=="WUB"){
            if(!i){
                i+=3;
                continue;
            }
            while(sentence.substr(i,3)=="WUB"){
                i+=3;
            }
            cout<<" ";
            continue;
        }
        else cout<<sentence[i];
        i++;
    }
    if(sentence.substr(i,3)!="WUB"){
        cout<<(sentence.substr(i,3))<<endl;
    }

    return 0;
}
```

# R - Mom, Where is My Sock?! 
```cpp
#include <bits/stdc++.h>
using namespace std;

int main()
{
   int n,m;
   cin>>n>>m;
   int socks=n+(n-1)/(m-1);
   cout<<socks<<endl;
return 0;
}
```
# S - Avoid That Trap
```cpp
#include <bits/stdc++.h>
using namespace std;
// In The Name Of Allah
// The Lord Of Mercy, The Giver Of Mercy
// Which of Allah's blessings can you deny?
typedef long long ll;
#define endl "\n"
#define all(v) v.begin(), v.end()

int main()
{
    ios::sync_with_stdio(false);
    cin.tie(nullptr);

    int t;
    cin >> t;

    while (t--)
    {
            int n;
    cin >> n;
    map<ll, vector<ll>> mp;
    for (int i = 0; i < n; i++)
    {
        ll a, b;
        cin >> a >> b;
        mp[a].push_back(b);
    }
    vector<ll> active_traps;
    int i = 1;
    bool trapped = false;
    for (i = 1; i <= 300; i++)
    {
        if (!mp[i].empty())
        {
            for (auto x : mp[i])
            {
                active_traps.push_back(x);
            }
        }
        for (auto &u : active_traps)
        {
            u-=2;
            if (u <= 0)
            {
                trapped = true;
                break;
            }
        }
        if (trapped)
        {
            break;
        }
        
    }

    cout << i  << endl;
    }

    return 0;
}
```

# T - Permutation Differences 

```cpp
#include <bits/stdc++.h>
using namespace std;

//In The Name Of Allah
//The Lord Of Mercy, The Giver Of Mercy
//Which of Allah's blessings can you deny?
typedef long long ll;
#define endl "\n"
#define all(v) v.begin(),v.end()



int main() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);

    int t;
    cin >> t;

    while (t--) {
           int n;
    cin>>n;
    vector<pair<ll,ll>>vp;
    for(int i=0;i<n;i++){
        ll x;
        cin>>x;
        vp.push_back({x,i+1});
    }
    sort(all(vp),greater<pair<ll,ll>>());
    vector<pair<ll,ll>>ans;
    for(int i=0;i<n;i++){
        ans.emplace_back(vp[i].second,i+1);
    }
    sort(all(ans));
    for(int i=0;i<n;i++){
        cout<<ans[i].second<<" ";
    }
    cout<<endl;
    }

    return 0;
}
```

# U - Split Into Two?

```cpp
#include <bits/stdc++.h>
 
#define fastio                        \
    ios_base::sync_with_stdio(false); \
    cin.tie(NULL)
 
#define endl "\n"
typedef long long ll;
using namespace std;
 
int main()
{
    fastio;
    ll n;
    cin>>n;
    ll sum=(n*(n+1))/2;
    vector<ll>s1,s2;
    ll sum1=0,sum2=0;
    if(sum%2){
        cout<<"NO"<<endl;
        return 0;
    }
    for(int i=n;i>0;i--){
        if(sum1+i<=sum/2){
            sum1+=i;
            s1.push_back(i);
        }
        else{
            sum2+=i;
            s2.push_back(i);
        }
    }   
    cout<<"YES"<<endl;
    cout<<s1.size()<<endl;
    for(int i=0;i<s1.size();i++){
        cout<<s1[i]<<" ";
    }
    cout<<endl;
    cout<<s2.size()<<endl;
    for(int i=0;i<s2.size();i++){
        cout<<s2[i]<<" ";
    }
    cout<<endl;
    return 0;
}
```

# V - Reorder Palindrome 

```cpp
#include <bits/stdc++.h>
 
#define fastio                        \
    ios_base::sync_with_stdio(false); \
    cin.tie(NULL)
 
#define endl "\n"
 
using namespace std;
 
int main()
{
    fastio;
    map<char,int>mp;
    string s;
    cin>>s;
    for(auto u:s){
        mp[u]++;
    }
    int odd_count=0;
    string odd;
    s="";
    for(auto u:mp){
        if(u.second%2){
            if(odd_count>0){
                cout<<"NO SOLUTION"<<endl;
                return 0;
            }
            odd_count++;
            while(mp[u.first]>0){
                odd.push_back(u.first);
                mp[u.first]--;
            }
        }
        else{
            mp[u.first]/=2;
            while(mp[u.first]>0){
                s.push_back(u.first);
                mp[u.first]--;
            }
        }
    }
    string tmp=s;
    reverse(s.begin(),s.end());
    cout<<tmp+odd+s<<endl;
 
    return 0;
}
```

# W - Nerds Unite 

```cpp
#include <bits/stdc++.h>
 
#define fastio                        \
    ios_base::sync_with_stdio(false); \
    cin.tie(NULL)
 
#define endl "\n"
typedef long long ll;
using namespace std;
 
int main()
{
    fastio;
    int n;
    cin>>n;
    vector<ll>a(n);
    for(ll &i:a)cin>>i;
    ll Max=max_element(a.begin(),a.end())-a.begin();
    ll sum =accumulate(a.begin(),a.end(),0LL);
    cout<<max(sum,2*a[Max])<<endl;
    return 0;
}
```

# X - Production Line

```cpp
#include <bits/stdc++.h>
 
#define fastio                        \
    ios_base::sync_with_stdio(false); \
    cin.tie(NULL)
 
#define endl "\n"
typedef long long ll;
using namespace std;
 
int main()
{
    fastio;
    int n;
    ll k;
    cin>>n>>k;
    vector<ll>v(n);
    for(ll &i:v)cin>>i;
    ll low=0,high=1e18;
    ll ans=0;
    while(low<=high){
        ll mid=(low+high)/2;
        ll sum=0;
        for(ll i:v){
            sum+=mid/i;
            if(sum>=k)break;//dealing with overflow
        }
        if(sum>=k){
            ans=mid;
            high=mid-1;
        }
        else low=mid+1;
    }
    cout<<ans<<endl;
    return 0;
}
```

# Y - More Police Officers?

```cpp
#include<bits/stdc++.h>
using namespace std;
#define fastio ios_base::sync_with_stdio(false);cin.tie(NULL);

int main()
{
    fastio
    int n;
    cin>>n;
    int crimesAndRecruits[n];//if value is positive recruit else crime occurence
    int recruits=0;
    int untreatedCrimes=0;
    for(int i=0;i<n;i++)
    {
        cin>>crimesAndRecruits[i];
        if(crimesAndRecruits[i]>0)
        {
            recruits+=crimesAndRecruits[i];
        }
        else{
            if(recruits>0){
                recruits--;
            }
            else{
                untreatedCrimes++;
            }
        }
    }
    cout<<untreatedCrimes<<endl;
}
```

# Z - Can Matrices be Beautiful?

```cpp
#include<bits/stdc++.h>
using namespace std;

#define fastio ios_base:: sync_with_stdio(false);cin.tie(NULL);

int main(void) {
    fastio
    int matrix[5][5];
    int row,column;
    for(int i=0;i<5;i++){
        for(int j=0;j<5;j++){
            cin>>matrix[i][j];
            if(matrix[i][j]){
                row=i;
                column=j;
            }
        }
    }
    cout<<abs(row-2)+abs(column-2)<<endl;

}
```
