# nukilinc
[Homework-1]Ekrana 3 farklı şekli çizebilen bir program yazıyorum. Ana program içinde kullanıcıdan istediği şekli seçmesini istiyor [1: Düz Üçgen, 2: Ters Üçgen, 3: Elmas, 0: Çıkış] ve sonrasında o şeklin boyutunu kullanıcıdan bekliyorum. Sadece geçerli boyut verileri için çizim yapılmalı.
/*
 * nursena kılınç
 *Homework-1
 */

#include <iostream>
#include <stdlib.h> /* atoi -> char * parametreyi int turune donusturmek icin kullanilacak */

using namespace std;

/* Sekil turlerini gostermek icin C dilindekine benzer sekilde sabitler tanimlaniyor.
Bu sabitler programinin okunulabilirligini arttirmaya yariyor.*/
#define DUZ_UCGEN 1
#define TERS_UCGEN 2
#define ELMAS 3

/*Bu fonksiyon ekrana yıldızlardan oluşan bir üçgen yazar.
Fonksiyon sadece [3, 15] aralığındaki tek sayılarda çalışır.
Uygun parametre gönderilmezse ekrana hiçbir şey yazdırmadan çıkar.*/
void duzUcgen( int deger )
{
    int i, j;
    int yildizSayisi = 0;
    int boslukSayisi = deger - 1;
    

    if( ( deger >= 3 ) && ( deger <= 15 ) && ( deger % 2 != 0 )){

         /* İlk For satır sayısını yazdırır (üçgenin boyu) */
         for(i=0; i < ( deger + 1 ) / 2 ; i++){        

        /* İkinci For ile boşluk yazdırılır */
             for(j=0; j<boslukSayisi; j++){
                 cout << " "; 
	     }  

             /* Üçüncü For ise Ekrana Yildiz yazdirir */
             for(j=0; j <= yildizSayisi; j++){
                  cout << "*"; 
	     }          

        /* Her Yildiz yazdırma işleminden sonra aşağı inilir */
           cout << endl;               

        /* Her aşağı indiğinde 2 tane fazladan yildiz yazdırmak için yildizSayisi 2 artirilir */
           yildizSayisi += 2;          

        /* Her aşağı indildiğinde Boşluk sayısının 1 azalması lazım */
           boslukSayisi--;
        
       }
    }
}

/* Bu fonksiyon ekrana yıldızlardan oluşan ters bir üçgen yazar.
Fonksiyon sadece[3, 15] aralığındaki tek sayılarda çalışır.
Uygun parametre gönderilmezse ekrana hiçbir şey yazdırmadan çıkar. */
void tersUcgen(int deger)
{
   int i, j;
   int yildizSayisi=deger-1;
   int boslukSayisi = deger - 1;
   

  
   if( ( deger >= 3 ) && ( deger <= 15 ) && ( deger % 2 != 0) ){
	   
	 /* İlk For satır sayısını yazdırır (üçgenin boyu) */
        for( i=0; i < ( deger + 1 ) / 2; i++ ){        

             /* İkinci For ile boşluk yazdırılır */
            for( j=0; j < boslukSayisi; j++ ){
                cout << " ";  
		} 

            /* Üçüncü For ise Ekrana Yildiz yazdirir */
            for( j=0; j <= yildizSayisi; j++ ){
                cout <<"*";           
		}

        /* Her Yildiz yazdırma işleminden sonra aşağı inilir */
           cout << endl;               

        /* Her aşağı indiğinde 2 tane fazladan yildiz yazdırmak için yildizSayisi 2 artirilir */
           yildizSayisi -= 2; 

        /* Her aşağı indildiğinde Boşluk sayısının 1 azalması lazım */
           boslukSayisi++;
                
        }
    }
}

/*Bu fonksiyon ekrana yıldızlardan oluşan bir elmas şekli yazar.
Fonksiyon sadece [5, 15] aralığındaki tek sayılarda çalışır.
Uygun parametre gönderilmezse ekrana hiçbir şey yazdırmadan çıkar.*/
void elmas(int deger){
	
	int i, j;
	int yildizSayisi=0, boslukSayisi=deger-1;
	
	if( ( deger >= 5 ) && ( deger <= 15 ) && ( deger % 2 != 0 )){
		
		for( i = 0; i < ( deger + 1 ) / 2; i++ ){
			for( j = 0; j < boslukSayisi; j++ ){
				cout << " ";
			}
			for( j = 0; j <= yildizSayisi; j++ ){
				cout << "*";
			}
			cout << endl;
			boslukSayisi--;
			yildizSayisi += 2;
		}
		
		yildizSayisi -= 4;
		boslukSayisi = (deger+1)/2; 
		
		for( i = 0; i < ( deger + 1 ) / 2; i++ ){
			for( j = 0; j < boslukSayisi; j++ ){
				cout << " ";
			}
			for( j = 0; j <= yildizSayisi; j++ ){
				cout << "*";
			}
			cout << endl;
			boslukSayisi++;
			yildizSayisi -= 2;
		}
	}
}

int main(int argc, char *argv[]){
	/* Programi komut satirindan calistirmak icin program_ismi + sekil turu + sekil boyutu
	  seklinde parametreler girilir. Burada program ismi de bir parametre gibi sayilir.
	*/
	if (argc != 3)
		return -1; // Parametre sayisi programi calistirmak icin uygun degil

	// Girilen parametrelere uygun sekli ekrana yazdir
	if (atoi(argv[1]) == DUZ_UCGEN)
		duzUcgen(atoi(argv[2]));
	else if (atoi(argv[1]) == TERS_UCGEN)
		tersUcgen(atoi(argv[2]));
	else if (atoi(argv[1]) == ELMAS)
		elmas(atoi(argv[2]));

	return 0;
}
