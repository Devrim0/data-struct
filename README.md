# data struct
package veri.yapilari.iknci.odevogrenci.txt.ders.txt;

import java.io.File;
import java.io.FileNotFoundException;
import java.io.PrintWriter;
import java.util.Scanner;

class ogrenci {

    ogrenci ileri;
    ogrenci dersekle;
    int numara;
    String isim, soyad,sinif;  //ogrencilerin bilgisi....

    public ogrenci(int numara, String isim, String soyad, String sinif) {
        this.numara = numara;
        this.isim = isim;
        this.soyad = soyad;
        this.sinif = sinif;
        ileri = null;
        dersekle = null;
    }

}

class ders {

    String derskodu, dersadi, derssinifi;  //ders bilgilerin tanimlanmasi....
    ders dersasagi, ders1asagi;

    public ders() {
    }

    public ders(String derskodu, String dersadi, String derssinifi) {
        this.derskodu = derskodu;
        this.dersadi = dersadi;
        this.derssinifi = derssinifi;
        dersasagi = null;
        ders1asagi = null;
    }

}      //OGRENCİ VE DERS BİLGİLERİ BLİSTEDE GOSTERİLECEK.....

class bliste {

    ders dersson, tmp1, dersson2, dersbas;
    ogrenci bas, son, tmp;

    public bliste() {
        bas = null;
        son = null;
        dersbas = null;
        dersson = null;
        dersson2 = null;
    }

    void sonaekle(ogrenci yeni) { //A) ŞIKKI; OGRENCİ EKLEME

        if (son == null || bas==null) {
            bas = yeni;
            son = yeni;
        } else {
            son.ileri =yeni;
           son = yeni;
        }
        System.out.print(yeni.numara + "   " + yeni.isim + "  " + yeni.soyad + "   " + yeni.sinif + "===>");

    }

    void dersekle(ders yeni1) { //DERSLERİ EŞİT OLAN ogrenciler
        tmp = bas;

        while (tmp != null) {
            if (tmp.sinif == null ? yeni1.derssinifi == null : tmp.sinif.equals(yeni1.derssinifi)) {
                if (dersson == null || dersbas==null) {
                    dersson = yeni1;
                    dersbas = yeni1;

                } else {

                    dersson.dersasagi = yeni1;
                    dersson = yeni1;
                   
                }
    System.out.println(tmp.isim + "  " + tmp.sinif + " ____>> " + yeni1.derskodu + "  " + yeni1.dersadi + "  " + yeni1.derssinifi + " ");
            }

            tmp = tmp.ileri;
            
        }
    }

    void derslistele() {
        tmp = bas;
        
        while (tmp != null){//ogrenci
            tmp1 = dersbas;
            while(tmp1!=null){ //ders
           
 if (tmp.sinif == null ? tmp1.derssinifi == null : tmp.sinif.equals(tmp1.derssinifi)) {

System.out.print(tmp.isim + "  " + tmp.sinif + " ____>> " + tmp1.derskodu + "  " + tmp1.dersadi + "  " + tmp1.derssinifi + " ");}
   tmp1=tmp1.dersasagi;}
            System.out.println("---->>>"+"null");
      tmp = tmp.ileri;      
        }

    }
void ogrencibul(ogrenci gelen){
 int numara=3453;      
tmp1=dersbas;
while(tmp1!=null){
if(gelen.numara==numara){
if (gelen.sinif == null ? tmp1.derssinifi == null : gelen.sinif.equals(tmp1.derssinifi)) {
System.out.println(gelen.numara+"  "+gelen.isim + "  " + gelen.sinif + " ____>> " + tmp1.derskodu + "  " + tmp1.dersadi + "  " + tmp1.derssinifi + " ");
}}
tmp1=tmp1.dersasagi;
 
}
    
}
    
    }


public class YENIbLISTE {

    public static void main(String[] args) {
      
        bliste b = new bliste();
        try {

            Scanner k = new Scanner(f1);

            while (k.hasNext()) {

                numaraoku = k.nextInt();
                isim = k.next();
                soyad = k.next();
                derslik = k.next();

                b.sonaekle(new ogrenci(numaraoku, isim, soyad, derslik));

                 //  System.out.println(numaraoku+isim+soyad+derslik);
            }
            System.out.println(-1);

        } catch (FileNotFoundException ex) {
        }
        bliste ders1 = new bliste();
        bliste ders2 = new bliste();
        System.out.println("DERS EKLEME");
        try {

            Scanner k2 = new Scanner(f2);

            while (k2.hasNext()) {
                derskodu = k2.next();
                dersismi = k2.next();
                derssinifi = k2.next();
                b.dersekle(new ders(derskodu, dersismi, derssinifi));
            }

        } catch (FileNotFoundException ex) {
        }

        System.out.println("LİSTELEME");

        b.derslistele();
        System.out.println("LİSTEDE OLAN OGRENCİNİN DERSLERİNİ GOSTERME");
try {

            Scanner k = new Scanner(f1);

            while (k.hasNext()) {
                numaraoku = k.nextInt();
                isim = k.next();
                soyad = k.next();
                derslik = k.next();

                b.ogrencibul(new ogrenci(numaraoku, isim, soyad, derslik));
            }
           

        } catch (FileNotFoundException ex) {
        }
    }
} 
