#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#define N 24
char yer_kontrolu(int satir,int sutun,int uzunluk,int yon,int m[][N],int n);//üretilen yon, satir, sutun da uzunluga göre gemi var mı ya gemi yerlesemez mi diye kontrol eder
void gemi_yerlestir(int uzunluk,int m[][N],int n);//gemilerimizi uygun yerlestirir yer kontrolu fonksiyonundan faydalanilir
void matris_yazdir(char [][24],int n);//oyuncunun matrisini yazdirir
void matris_yazdir2(int m[][24],int n);//bilgisayarin matrisini yazdirir
void batti_mi(int bilgisayarin[][24],char oyuncunun[][24],int satir,int sutun,int oyun_kenar);//gemi battimi kontrol eder
char bitti_mi(int bilgisayarin[][24],char oyuncunun[][24],int oyun_kenar);//butun gemiler battımı kontrol eder
int main()//ana fonksiyon
{
    char oyuncunun[24][24]= {},s,k='c';
    int oyun_kenar,gemi_uzunluk,sutun,satir;
    int atis_hakki=0,uzunluk_top=0,sayac=0,sayac1=0;
    int  bilgisayarin[24][24]= {{0}};
    printf("\t\t***AMIRAL BATTI OYUNU****\n");

    do
    {
        printf("\tOyun alaninizin bir kenarini giriniz\n(4 ile 24 arasinda cift sayi olmali):");//oyun kenari kontrolu
        scanf("%d",&oyun_kenar);
        if(oyun_kenar>25|| oyun_kenar<3|| oyun_kenar%2!=0)
            printf("Sinirlari astiniz.. tekrar deneyiniz...\n");//uyari mesaji

    }
    while(oyun_kenar>25|| oyun_kenar<3|| oyun_kenar%2!=0); //yanlis ise yenisni ister

    for(sayac=0; sayac<oyun_kenar; sayac++)
    {
        for(sayac1=0; sayac1<oyun_kenar; sayac1++)
        {
            oyuncunun[sayac][sayac1]='O';
            bilgisayarin[sayac][sayac1]=0;
        }
    }
    matris_yazdir(oyuncunun,oyun_kenar);
    for(sayac=1; sayac<=oyun_kenar/2; sayac++)
    {
        do
        {
            printf("\t%d. Geminizin uzunlugunu giriniz:",sayac);
            scanf("%d",&gemi_uzunluk);
            if(gemi_uzunluk<2|| gemi_uzunluk>oyun_kenar/2+1)//uyari mesaji
                printf("\t\nGemi uzunlugu 2 ile %d arasinda olmalidir\n\n\tSinirlar icinde deger girerek tekrar deneyiniz!!!\a\n\n",oyun_kenar/2+1);
        }
        while(gemi_uzunluk<2 || gemi_uzunluk>oyun_kenar/2+1); // gemi uzunluk kontrolu

        printf("\n\n\tGemileriniz yerlesirken lutfen bekleyiniz!!!!\n");
        gemi_yerlestir(gemi_uzunluk,bilgisayarin,oyun_kenar);
        uzunluk_top+=gemi_uzunluk;
        atis_hakki=oyun_kenar*oyun_kenar-uzunluk_top;
    }
    printf("\nToplam atis hakkiniz: %d\n",atis_hakki);
    //matris_yazdir2(bilgisayarin,oyun_kenar);
    for(sayac=0; sayac<atis_hakki; sayac++)
    {
        do
        {
            printf("\nAtis icin satiri giriniz:\n");
            scanf("%d",&satir);
            if(satir<1||satir>oyun_kenar)// matrisin satirlarindan birini girmediyse uyari mesaji
                printf("Atis icin oyunun satir sinirlarini astiniz\n");
        }
        while(satir<1||satir>oyun_kenar); // acaba doru satir girdi mi girmediyse yeni deger ister dogru girinceye kadar
        do
        {
            printf("Atis icin sutunu giriniz:\n");
            scanf(" %c",&s);
            sutun=s-65;
            if(sutun<0||sutun>oyun_kenar)//matrisin sutunlarindan birini girmediyse uyari mesaji
                printf("Atis icin oyunun sutun sinirlarini astiniz\n");
        }
        while(sutun<0||sutun>oyun_kenar); //girilen sutunun kontrolunu yapar

        if(bilgisayarin[satir-1][sutun]==1)//bilgisayara gore gemi buluundu ise I atar yani isabet yapar
        {
            oyuncunun[satir-1][sutun]='I';
            printf("\nTebrikler isabetli atis!!\n\n");
            batti_mi(bilgisayarin,oyuncunun,satir,sutun,oyun_kenar);//gemi batti mi kontrol eder
            k=bitti_mi(bilgisayarin,oyuncunun,oyun_kenar);// butun gemiler bitti mi kontrol eder
        }
        else// bilisayar matrisinde satir ve sutun degerinde gemi yoksa K atar yani karavana der
        {
            oyuncunun[satir-1][sutun]='K';
            printf("Uzgunum karavana :/\n\n");
            matris_yazdir(oyuncunun,oyun_kenar);//matris yazdirilir
        }
        if(atis_hakki-sayac-1==0)//atis hakki kalmadiysa atis hakkin bitti mesaji
            printf("Atis hakkiniz bitmistir,uzulmeyin olur boyle seyler\n\n");
        else
            printf("Kalan atis hakkiniz %d dir\n",atis_hakki-sayac-1);//kalan atis hakki meaji

        if(k=='g')// butum gemiler bulundu ise oyunu bitirdin basardin mesaji bitti_mi fonksiyonundan donen deger...
        {
            printf("Butun Gemileri Batirmayi Basardiniz!! :)))\n");
            break;
        }

    }

    //matris_yazdir2(bilgisayarin,oyun_kenar);

    return 0;
}

void matris_yazdir(char m[][24],int n)// oyuncunun atis yaptigi matrisi yazdirmak icin kullanilir
{
    int i,k;

    printf("*");// kose yıldizi:)
    for(k='A'; k<n+65; k++)
        printf("%3c",k);
    for(i=0; i<n; i++)
    {
        printf("\n%d ",i+1);

        for(k=0; k<n; k++)
        {
            printf("%2c ",m[i][k]);
        }// bosluk ayarladik goruntu icin alt alta gelsin diye
        printf("\n");
    }

    return;
}
void matris_yazdir2(int m[][24],int n)// geminin yerlestirildigi bilgisayarin matrisi icin yazdirma
{
    int k,i;

    printf("*");
    for(k=1; k<n+1; k++)
        printf("%3d",k);
    for(i=0; i<n; i++)
    {
        printf("\n%d ",i+1);

        for(k=0; k<n; k++)
        {
            printf("%2d ",m[i][k]);
        }// goruntu icin bosluk yapildi:)
        printf("\n");
    }
    return;
}
void gemi_yerlestir(int uzunluk,int m[][24],int n)// gemilerin yerlestirildigi matris
{
    int ilk_satir,ilk_sutun,yon,sayac=0;
    char a='b';
    int sutun;
    do
    {
        //srand(time(NULL));
        printf("yonunuzun baslangic satirini giriniz:\n");
        //ilk_satir=rand()%n;
        scanf("%d",&ilk_satir);
        //ilk_sutun=rand()%n;
        printf("yonunuzun baslangic sutununu giriniz:\n");
       // yon=1+rand()%4;
         scanf("%s",&sutun);
        ilk_sutun=sutun+'A'-65;
        printf("yonunuzu giriniz[1 : kuzey 2:guney 3:dogu  4:bati\n");
        scanf("%d",&yon);
        switch(yon)
        {
        case 1://kuzey
            if(ilk_satir+uzunluk>n-1) // gemi yerlesirken sınırlari asti mi
            {
                a='t';
                break;
            }
            if(ilk_satir+uzunluk<n) // eger sinirlar asilmadiysa
            {
                a=yer_kontrolu(ilk_satir,ilk_sutun,uzunluk,yon, m,n);// burada onceden gemi varmıydıve gemi yerlesebilir  mi kontrolu
                if(a=='t')
                    break;
            }
            for(sayac=ilk_satir; sayac<ilk_satir+uzunluk; sayac++) //eger hicbir engel yoksa gemi yerlesir
                m[sayac][ilk_sutun]=1;
            break;
        case 2://guney
            if(ilk_satir-uzunluk<0) // gemi yerlesirken sınırlari asti mi
            {
                a='t';
                break;
            }
            if(ilk_satir-uzunluk>=0) // eger sinirlar asilmadiysa
            {
                a=yer_kontrolu(ilk_satir,ilk_sutun,uzunluk,yon,m,n);// burada onceden gemi varmıydıve gemi yerlesebilir  mi kontrolu
                if(a=='t')
                    break;
            }
            for(sayac=ilk_satir; sayac>ilk_satir-uzunluk; sayac--) //eger hicbir engel yoksa gemi yerlesir
                m[sayac][ilk_sutun]=1;
            break;
        case 3://dogu
            if(ilk_sutun-uzunluk<0) // gemi yerlesirken sınırlari asti mi
            {
                a='t';
                break;
            }
            if(ilk_sutun-uzunluk>=0) // eger sinirlar asilmadiysa
            {
                a=yer_kontrolu(ilk_satir,ilk_sutun,uzunluk,yon,m,n);// burada onceden gemi varmıydıve gemi yerlesebilir  mi kontrolu
                if(a=='t')
                    break;
            }
            for(sayac=ilk_sutun; sayac>ilk_sutun-uzunluk; sayac--) //eger hicbir engel yoksa gemi yerlesir
                m[ilk_satir][sayac]=1;
            break;
        case 4://bati
            if(ilk_sutun+uzunluk>n-1) // gemi yerlesirken sınırlari asti mi
            {
                a='t';
                break;
            }
            if(ilk_sutun+uzunluk<n) // eger sinirlar asilmadiysa
            {
                a=yer_kontrolu(ilk_satir,ilk_sutun,uzunluk,yon,m,n);// burada onceden gemi varmıydıve gemi yerlesebilir  mi kontrolu
                if(a=='t')
                    break;
            }
            for(sayac=ilk_sutun; sayac<ilk_sutun+uzunluk; sayac++) //eger hicbir engel yoksa gemi yerlesir
                m[ilk_satir][sayac]=1;
            break;
        }
    }
    while(a=='t');

    //printf("%d,%d,%d\n",ilk_satir+1,ilk_sutun+1,yon);
}

char yer_kontrolu(int ilk_satir,int ilk_sutun,int uzunluk,int yon,int m[][24],int n)// gemi yerlesirken yer kontrolu yapar gemi
// gelebir mi diye kontrol eder ve deger dondurur bulundu yada bulunmadi diye
{
    int sayac;
    char  bulundu='b';

    switch(yon)
    {
    case 1://kuzey
        if(m[ilk_satir-1][ilk_sutun]==1) // kuzey icin yon kontrolu en ust satir
        {
            bulundu='t';
            break;
        }
        if(m[ilk_satir+uzunluk][ilk_sutun]==1) // en alt satir kontrolu
        {
            bulundu='t';
            break;
        }
        for(sayac=ilk_satir; sayac<ilk_satir+uzunluk; sayac++) // dongu boyunca uc sati tarar  sag sol ve ust ustte gelme
        {
            // gemi boyu kadar ilerler
            if(m[sayac][ilk_sutun-1]==1) // sagda gemi var mi
            {
                bulundu='t';
                break;
            }
            if(m[sayac][ilk_sutun]==1) //  solda gemi var i kontrolu
            {
                bulundu='t';
                break;
            }
            if(m[sayac][ilk_sutun+1]==1) // gemilerin ust uste gelme kontrolu
            {
                bulundu='t';
                break;
            }
        }
        break;
    case 2://guney
        if(m[ilk_satir+1][ilk_satir]==1) // guney icin en altta gemi var mi kontrolu
        {
            bulundu='t';
            break;
        }
        if(m[ilk_satir-uzunluk][ilk_sutun]==1) // en ustte gemi var  mi kontrolu
        {
            bulundu='t';
            break;
        }
        for(sayac=ilk_satir; sayac>ilk_satir-uzunluk; sayac--) // dongu boyunca uc sati tarar  sag sol ve ust ustte gelme gemi boyu kadar ilerler
        {
            if(m[sayac][ilk_sutun-1]==1) // solda gemi var mi kontrolu
            {
                bulundu='t';
                break;
            }
            if(m[sayac][ilk_sutun+1]==1) // sagda gemi var mı kontrolu
            {
                bulundu='t';
                break;
            }
            if(m[sayac][ilk_sutun]==1) // gemiler ustuste gelmis mi kontrolu
            {
                bulundu='t';
                break;
            }
        }
        break;
    case 3://dogu
        if(m[ilk_satir][ilk_sutun+1]==1) //dogu icin yon kontrolu en sagda gemi var mi kontrol eder
        {
            bulundu='t';
            break;
        }
        if(m[ilk_satir][ilk_sutun-uzunluk]==1) // en solda gemi var mi kontrol eder
        {
            bulundu='t';
            break;
        }
        for(sayac=ilk_sutun; sayac>ilk_sutun-uzunluk; sayac--) // gemi boyu kadar uc satir tarar ve kontrol eder
        {
            if(m[ilk_satir][sayac]==1) // gemilerin cakisma durumunu kontrol eder
            {
                bulundu='t';
                break;
            }
            if(m[ilk_satir-1][sayac]==1)// ustte gemi var mi kontrol eder
            {
                bulundu='t';
                break;
            }
            if(m[ilk_satir+1][sayac]==1)// altta gemi varmi kontrol eder
            {
                bulundu='t';
                break;
            }
        }
        break;
    case 4://bati
        if(m[ilk_satir][ilk_sutun+1]==1)// bati icin gemi var mi bakilir ,en sagda gemi var mi kontrol eder
        {
            bulundu='t';
            break;
        }
        if(m[ilk_satir][ilk_sutun+uzunluk]==1)// en solda gemi var mi kontrol eder
        {
            bulundu='t';
            break;
        }
        for(sayac=ilk_sutun; sayac<ilk_sutun+uzunluk; sayac++) // gemi boyun kadar uc satir tarar gemi bulunca cikar
        {
            if(m[ilk_satir][sayac]==1)// ustuste olma durumunu yada cakisma durumunu kontrol eder
            {
                bulundu='t';
                break;
            }
            if(m[ilk_satir+1][sayac]==1)// altta gemi var mi kontrol eder
            {
                bulundu='t';
                break;
            }
            if(m[ilk_satir-1][sayac]==1)// ustte gemi var  mi kontrol eder
            {
                bulundu='t';
                break;
            }
        }
        break;
    }
    return bulundu;// gemi bulursa t doner yoksa b doner ve yerlestirmeye baslanir gemi yerlestirde :)
}

void batti_mi(int bilgisayarin[][24],char oyuncunun[][24],int satir,int sutun,int oyun_kenar)// acaba gemi battimi ogrenelm bakalim
{
    int k,soldaki,sag=1,sagdaki=0,alt=1,alttaki=0,ustteki,tersyon=1,gemi_boyut=1;
    char kontrol='e',ch='g';

    if(bilgisayarin[satir-1][sutun-1]==1 || bilgisayarin[satir-1][sutun+1]==1)  ////Gemi mutlaka yatayda
    {

        if(bilgisayarin[satir-1][sutun-1]==0 && bilgisayarin[satir-1][sutun+1]==1) //isabet edilen nokta geminin sol ucu ise
        {

            while(bilgisayarin[satir-1][sutun+gemi_boyut]==1)  // var olan geminin boyutunun belirlenmesi
            {
                gemi_boyut++;
            }
            for(k=1; k<=gemi_boyut; k++) //geminin batmasi icin butun karakterlerin girilip girilmediginin kontrolu
            {
                if(bilgisayarin[satir-1][sutun+k]==1 && oyuncunun[satir-1][sutun+k]!='I')
                    kontrol='h';

            }

            if(kontrol=='e')  //butun karakterler girildiyse gemiyi batiriyoruz.
            {
                for(k=0; k<gemi_boyut; k++)
                    oyuncunun[satir-1][sutun+k]='B';
                matris_yazdir(oyuncunun,oyun_kenar);
                printf("Gemiyi batirdiniz!!!\n");
            }
            if(kontrol=='h')
                matris_yazdir(oyuncunun,oyun_kenar);

        }
        else if(bilgisayarin[satir-1][sutun]==1 && bilgisayarin[satir-1][sutun+1]==0)//bu nokta geminin sag ucu ise
        {
            while(ch=='g')  // var olan geminin boyutunun belirlenmesi
            {
                if(bilgisayarin[satir-1][sutun-gemi_boyut]==1)
                    gemi_boyut++;
                else
                    ch='c';
            }
            for(k=1; k<=gemi_boyut; k++) //geminin batmasi icin butun karakterlerin girilip girilmediginin kontrolu
            {
                if(bilgisayarin[satir-1][sutun-k]==1 && oyuncunun[satir-1][sutun-k]!='I')
                    kontrol='h';

            }
            if(kontrol=='h')
                matris_yazdir(oyuncunun,oyun_kenar);

            else if(kontrol=='e') //butun karakterler girildiyse gemiyi batiriyoruz.
            {
                for(k=0; k<gemi_boyut; k++)
                    oyuncunun[satir-1][sutun-k]='B';
                matris_yazdir(oyuncunun,oyun_kenar);
                printf("Bir gemi batirdiniz\n");
            }
        }
        else  //ısabet edilen nokta geminin ortasında bir nokta ise
        {
            while(bilgisayarin[satir-1][sutun+tersyon]==1 && bilgisayarin[satir-1][sutun-tersyon]==1)  // var olan geminin boyutunun belirlenmesi
            {
                gemi_boyut+=2;
                tersyon++;
            }
            while(bilgisayarin[satir-1][sutun+tersyon]==1 || bilgisayarin[satir-1][sutun-tersyon]==1)
            {
                gemi_boyut++;
                tersyon++;
            }


            while(bilgisayarin[satir-1][sutun+sag]==1)  // isabet edilen noktanın saginda kac nokta var.
            {
                sagdaki++;
                sag++;
            }
            soldaki=gemi_boyut-(sagdaki+1);
            for(k=1; k<=sagdaki; k++) //(sagdan)geminin batmasi icin butun karakterlerin girilip girilmediginin kontrolu
            {
                if(bilgisayarin[satir-1][sutun+k]==1 && oyuncunun[satir-1][sutun+k]!='I')
                    kontrol='h';

            }
            if(kontrol!='h')  //sagdakilerin hepsi daha onceden isabet etmis ise
            {

                for(k=0; k<=soldaki; k++) //(soldan)geminin batmasi icin butun karakterlerin girilip girilmediginin kontrolu
                {
                    if(bilgisayarin[satir-1][sutun-k]==1 && oyuncunun[satir-1][sutun-k]!='I')
                        kontrol='h';
                }

            }

            if(kontrol=='e')  //butun karakterler girildiyse gemiyi batiriyoruz.
            {

                for(k=1; k<=sagdaki; k++)
                    oyuncunun[satir-1][sutun+k]='B';
                for(k=0; k<=soldaki; k++)
                    oyuncunun[satir-1][sutun-k]='B';
                matris_yazdir(oyuncunun,oyun_kenar);
                printf("Bir gemi batirdiniz\n");
            }
        }

    }
    else  ////Gemi mutlaka düşeyde
    {
        if(bilgisayarin[satir-1-1][sutun]==0 && bilgisayarin[satir-1+1][sutun]==1) //isabet edilen nokta geminin üst ucu ise
        {

            while(bilgisayarin[satir-1+gemi_boyut][sutun]==1)  // var olan geminin boyutunun belirlenmesi
            {
                gemi_boyut++;
            }
            for(k=1; k<=gemi_boyut; k++) //geminin batmasi icin butun karakterlerin girilip girilmediginin kontrolu
            {
                if(bilgisayarin[satir-1+k][sutun]==1 && oyuncunun[satir-1+k][sutun]!='I')
                    kontrol='h';

            }

            if(kontrol=='e') //butun karakterler girildiyse gemiyi batiriyoruz.
            {
                for(k=0; k<gemi_boyut; k++)
                    oyuncunun[satir-1+k][sutun]='B';
                matris_yazdir(oyuncunun,oyun_kenar);
                printf("Bir gemi batirdiniz\n");
            }

        }
        else if(bilgisayarin[satir-1-1][sutun]!=0 && bilgisayarin[satir-1+1][sutun]==0)//bu nokta geminin en alt ucu ise
        {
            while(bilgisayarin[satir-1-gemi_boyut][sutun]==1)  // var olan geminin boyutunun belirlenmesi
            {
                gemi_boyut++;
            }
            for(k=1; k<=gemi_boyut; k++) //geminin batmasi icin butun karakterlerin girilip girilmediðinin kontrolu
            {
                if(bilgisayarin[satir-1-k][sutun]==1 && oyuncunun[satir-1-k][sutun]!='I')
                    kontrol='h';

            }

            if(kontrol=='e') //butun karakterler girildiyse gemiyi batiriyoruz.
            {

                for(k=0; k<gemi_boyut; k++)
                    oyuncunun[satir-1-k][sutun]='B';
                matris_yazdir(oyuncunun,oyun_kenar);
                printf("Bir gemi batirdiniz\n");
            }
        }
        else//ısabet edilen nokta geminin ortasında bir nokta ise
        {
            while(bilgisayarin[satir-1+tersyon][sutun]==1 && bilgisayarin[satir-1-tersyon][sutun]==1)  // var olan geminin boyutunun belirlenmesi
            {
                gemi_boyut+=2;     // isabet edilen noktanın hem altında hem üstünde ise boyutu 2 artır.
                tersyon++;
            }
            while(bilgisayarin[satir-1+tersyon][sutun]==1 && bilgisayarin[satir-1-tersyon][sutun]==1)
            {
                gemi_boyut++;          // isabet edilen noktanın ya altında ya da üstünde ise boyutu 1 artır.
                tersyon++;
            }


            while(bilgisayarin[satir-1+alt][sutun]==1)  // isabet edilen noktanın altinda kac nokta var.
            {
                alttaki++;
                alt++;
            }
            ustteki=gemi_boyut-(alttaki+1);
            for(k=1; k<=alttaki; k++) //(alttan)geminin batmasi icin butun karakterlerin girilip girilmediginin kontrolu
            {
                if(bilgisayarin[satir-1+k][sutun]==1 && oyuncunun[satir-1+k][sutun]!='I')
                    kontrol='h';

            }
            for(k=1; k<=ustteki; k++) //(üstten)geminin batmasi icin butun karakterlerin girilip girilmediginin kontrolu
            {
                if(bilgisayarin[satir-1-k][sutun]==1 && oyuncunun[satir-1-k][sutun]!='I')
                    kontrol='h';
            }

            if(kontrol=='e')  //butun karakterler girildiyse gemiyi batiriyoruz.
            {

                for(k=1; k<=alttaki; k++)
                    oyuncunun[satir-1+k][sutun]='B';//batirma islemleri
                for(k=0; k<=ustteki; k++)
                    oyuncunun[satir-1-k][sutun]='B';//''
                matris_yazdir(oyuncunun,oyun_kenar);
                printf("Bir gemi batirdiniz\n");
            }

        }
        if(kontrol=='h')
            matris_yazdir(oyuncunun,oyun_kenar);
    }

}


char bitti_mi(int bilgisayarin[][24],char oyuncunun[][24],int oyun_kenar)// butun gemiler batti mi oyun bitsin...
{
    // bilgisayar ve oyuncunu atis yaptigi matris karsilastirilir ve cakisirsa tamamen oyun bitirmek icin uygun deger  doner
    char k='c',ch='g';
    int i,j;

    for(i=0; i<oyun_kenar; i++)
    {
        for(j=0; j<oyun_kenar; j++)
        {
            if(oyuncunun[i][j]!='B' && bilgisayarin[i][j]!=1)//burada gemiler tamamen bulundu mu tarama yapılır
            {
                ch='c';
                break;
            }
        }
        if(ch=='c')
            break;
    }

    if(ch=='g')//
    {

        k='g';
    }
    return k;// bulundu bulunmadi deger doner g ise deger gemi batimi bitmis olur ve atislar biter

}

