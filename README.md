#include<stdio.h>
#include<string.h>
#include<stdlib.h>
#define MAX 50
char stack[MAX];
int top=-1;
int match_char(char a,char b){
	if(a=='(' && b==')')
		return 1;
	if(a=='{' && b=='}')
		return 1;
	if(a=='[' && b==']')
		return 1;
	else
		return 0;
}
int isempty(){
	if(top==-1)
		return 1;
	else
		return 0;
}
char pop(){
	char val;
	stack[top]=val;
	top--;
	return val;
}
void push(char data){
	top++;
	stack[top]=data;
}
int check_balanced(char*s){
	char temp;
	for(int i=0;i<strlen(s);i++){
		if(s[i]=='[' || s[i]=='(' || s[i]=='{')
			push(s[i]);
		if(s[i]==']' || s[i]==')' || s[i]=='}'){
			if(isempty()){

				printf("unbalanced expression");
				return 0;
			}
			else{
				temp=pop();
				if(!match_char(temp,s[i])){
					printf("unbalanced expression");
					return 0;
				}
			}
		}
	}
}
int main(){
	char exp[MAX];
	int balanced;
	printf("enter the string you wanna check");
	fgets(exp,MAX,stdin);
	balanced=check_balanced(exp);
	if(balanced==0)
		printf("and the expression is invalid");
	else
		printf("balanced expression and the expression is valid");
	return 0;
}

