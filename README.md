#include <bits/stdc++.h>
using namespace std;

#define maxN 20
#define maxSum 50
#define minSum 50
#define base 50
int dp[maxN][maxSum + minSum];
bool v[maxN][maxSum + minSum];
int findCnt(int* arr, int i, int required_sum, int n)
{
	if (i == n) {
		if (required_sum == 0)
			return 1;
		else
			return 0;
	}
	if (v[i][required_sum + base])
		return dp[i][required_sum + base];
	v[i][required_sum + base] = 1;
	dp[i][required_sum + base]
		= findCnt(arr, i + 1, required_sum, n)
		+ findCnt(arr, i + 1, required_sum - arr[i], n);
	return dp[i][required_sum + base];
}
int main()
{
	int arr[] = { 3, 3, 3, 3 };
	int n = sizeof(arr) / sizeof(int);
	int x = 6;

	cout << findCnt(arr, 0, x, n);

	return 0;
