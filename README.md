
#include <iostream>

using namespace std;

long long powmod_simple(long long a, long long b, long long n);
bool czy_pierwsza(int n);

int main() {

	long long p, g, a, A, B, K;
	cout << " Jakie jest p? \n";
	cin >> p;	
	while (!czy_pierwsza(p)) {
		cout << "Liczba nie jest pierwsza! Podaj inna ! \n";
		cin >> p;
	}
	cout << "Jakie jest g?\n";
	cin >> g;
	cout << "Jakie jest a \n";
	cin >> a;

	//licz A 
	A = powmod_simple(g, a, p);
	cout << A << "\n";
	//jakie bylo B
	cout << "Jakie bylo B?\n";
	cin >> B;
	//licz K
	K = powmod_simple(B, a, p);

	cout << "K wynosi: " << K <<"\n";
	system("PAUSE");
	return 0;
}

long long powmod_simple(long long a, long long b, long long n) {

	long long x = 1, y = a;
	while (b > 0) {
		if (b % 2 == 1) {
			x = (x*y) % n;
		}
		y = (y*y) % n;
		b /= 2;
	}
	return x%n;

}
bool czy_pierwsza(int n)
{
	if (n<2)
		return false; 
	for (int i = 2; i*i <= n; i++)
		if (n%i == 0)
			return false; 
	return true;
}
