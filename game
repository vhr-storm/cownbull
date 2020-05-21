#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>
#include <time.h>

void diviner(int num[],int temp){
    for (int i=0;i<4;i++){
        num[i] = temp % 10;
        temp = temp / 10;
    }
}

bool checker(int *num){
    bool flag=true;
    for (int i=0;i<4;i++){
        for (int j = i; j < 3;j++) {
            if(num[i]==num[j+1]){
                flag=false;
                break;
            }
        }
    }
    return flag;
}

int random(int ld,int rd){
    int temp;
    int mas[4];
    bool flag=false;
    srand(time(NULL));
    while (flag!=true){
        temp=rand()%(rd-ld+1)+ld;
        //printf("%d\n",temp);
        diviner(mas,temp);
        flag=checker(mas);
    }
    return temp;
}

int human_choice(int *num,int attempt){
    bool flag=false;
    int n,rd=9999,ld=1000;
    printf("Attempt:%d\n",attempt);
    printf("Enter num:");
    scanf("%d", & n);
    diviner(num,n);
    while(flag!=true){
        if (( n>rd)||( n<ld)||(checker(num)==false)){
            printf("Number entered incorrectly,retry");
            printf("\nEnter new num:");
            scanf("%d", & n);
            diviner(num,n);
        } else if(( n<rd)&&( n>ld)){ flag=true;}
    }

    return n;
}

void game(int secret,int start[],int check[]){
    int cow=0,bull=0,chosen_number,attempt=1;;
    while (bull!=4){
        chosen_number=human_choice(check,attempt);
        attempt=attempt++;
        if(secret== chosen_number){
            bull=4;
        }
        else {
            diviner(check,chosen_number);
            for(int i=0;i<4;i++){
                for (int j=0;j<4;j++){
                    if ((check[j]==start[i])&&(j==i)){
                        bull++;
                        break;
                    } else if ((check[j]==start[i])&&(j!=i)){
                        cow++;
                    }
                }
            }
        }
        printf("cow:%d\t bull:%d\t \n",cow,bull);
        if (bull!=4){
            cow=0;
            bull=0;
        }
    }
    printf("\nHURRAY U ARE WINNER");
}

int main (){
    int secretn;
    int start[4];
    int check[4];
    secretn=random(1000,9999);
    printf("%d\n",secretn);
    diviner(start,secretn);
    game(secretn,start,check);
    return 0;
}
