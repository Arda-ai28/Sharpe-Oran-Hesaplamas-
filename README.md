#include <stdio.h>

int main() {
    // Değişkenlerin tanımlanması
    // float: Ondalıklı sayılar için kullanılan veri tipi
    float yatirim_Getirisi, risksiz_Faiz_Orani, standart_Sapma,sharpe_Orani;
   
    printf("Lutfen Yatirim Getirisini giriniz: ");
    scanf("%f", &yatirim_Getirisi);

    printf("Lutfen Risksiz Faiz Oranini giriniz: ");
    scanf("%f", &risksiz_Faiz_Orani);

    printf("Lutfen Portfoyun Standart Sapmasini giriniz: ");
    scanf("%f", &standart_Sapma);

    // Girilen değerleri ondalık formata çevirme (15 -> 0.15)
    yatirim_Getirisi /= 100.0;
    risksiz_Faiz_Orani /= 100.0;
    standart_Sapma /= 100.0;

    // Hesaplama Bölümü 
    // Standart sapmanın sıfır olup olmadığını kontrol etme
    if (standart_Sapma == 0) {
        printf("\nHATA: Standart sapma (risk) sifir olamaz. Bolme hatasi!\n");
        return 1; // Hata kodu ile programı sonlandır
    }

    // Sharpe Oranı formülünün uygulanması
    // (Yatırım Getirisi - Risksiz Faiz Oranı) / Standart Sapma
    sharpe_Orani = (yatirim_Getirisi - risksiz_Faiz_Orani) / standart_Sapma;

    // Sonucu Ekrana Yazdırma ve Yorumlama Bölümü 
    printf("Hesaplanan Sharpe Orani: %.2f\n", sharpe_Orani); // Sonucu 2 ondalık basamakla yazdır

    // Sharpe Oranını genel kabul görmüş standartlara göre yorumlama
    if (sharpe_Orani >= 3.0) {
        printf("Yorum: Mukemmel! Alinan her birim riske karsilik cok yuksek bir ek getiri elde ediliyor.\n");
    } else if (sharpe_Orani >= 2.0) {
        printf("Yorum: Cok Iyi. Alinan riske gore elde edilen ek getiri oldukca tatmin edici.\n");
    } else if (sharpe_Orani >= 1.0) {
        printf("Yorum: Iyi. Portfoy, aldigi riske degecek bir ek getiri sagliyor.\n");
    } else if (sharpe_Orani > 0) {
        printf("Yorum: Zayif. Portfoy risksiz getiriden daha fazlasini kazandiriyor ancak risk/getiri dengesi cok verimli degil.\n");
    } else {
        printf("Yorum: Kotu. Portfoy, risksiz bir yatirimdan bile daha az getiri sagliyor. Bu riski almaya degmez.\n");
    }
    
    return 0; 
}
