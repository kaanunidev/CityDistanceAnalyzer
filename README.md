# CityDistanceAnalyzer - Şehir ve İlçe Mesafe Analizi

## Proje Açıklaması

Bu proje, Türkiye'deki şehirler ve İzmir'in ilçeleri arasındaki mesafeleri analiz eden bir C# konsol uygulamasıdır. Proje, **Dijkstra algoritması** kullanarak en kısa yol hesaplamaları yapar ve bu sonuçları **Karayolları Genel Müdürlüğü**'nün verdiği gerçek mesafe verileriyle karşılaştırır.

## Özellikler

### 🗺️ Şehir Mesafe Analizi
- **81 Türk şehri** arasında mesafe hesaplaması
- Dijkstra algoritması ile en kısa yol bulma
- Karayolları Genel Müdürlüğü verileriyle karşılaştırma
- Maksimum ve minimum fark analizleri

### 🏘️ İlçe Mesafe Analizi
- **İzmir'in 30 ilçesi** arasında mesafe hesaplaması
- Gerçek mesafe verileriyle algoritma sonuçlarının karşılaştırılması
- Detaylı mesafe raporları

### 📊 Analiz Özellikleri
- En büyük mesafe farkını veren şehir/ilçe çiftlerini bulma
- En küçük mesafe farkını veren şehir/ilçe çiftlerini bulma
- Dijkstra algoritması vs gerçek mesafe karşılaştırmaları

## Teknik Detaylar

### Kullanılan Algoritmalar
- **Dijkstra Algoritması**: En kısa yol hesaplaması için
- **Matrix İşlemleri**: Mesafe verilerinin saklanması ve işlenmesi
- **Dictionary Yapıları**: Şehir ve ilçe isimlerinin yönetimi

### Veri Yapıları
- `cityDictionary`: 81 şehir ve komşuluk mesafeleri
- `districtDictionary`: İzmir'in 30 ilçesi ve mesafeleri
- `jagged_array_city`: Şehirler arası gerçek mesafeler
- `array_district`: İlçeler arası gerçek mesafeler

### Veri Dosyaları
- `sehirmesafe.txt`: Şehirler arası gerçek mesafe verileri
- `ilcemesafe.txt`: İlçeler arası gerçek mesafe verileri

## Kullanım

### Gereksinimler
- .NET 8.0 veya üzeri
- C# derleyicisi

### Çalıştırma
```bash
cd CityDistanceAnalyzer
dotnet run
```

## Çıktı Örneği

Program aşağıdaki bilgileri sağlar:

```
Adana - Mersin : 70.5 KM (Dijkstra Algorithm)
Adana - Mersin : 70 KM (General Directorate of Highways)
Difference Between Dijkstra Algorithm And General Directorate of Highways: 0.5KM

Maximum Difference: 125.3KM, Cities: Istanbul,Ankara
Minimum Difference: 0.1KM, Cities: Izmir Konak
```

## Proje Yapısı

```
CityDistanceAnalyzer/
├── Program.cs                    # Ana program dosyası
├── CityDistanceAnalyzer.csproj   # Proje yapılandırması
├── sehirmesafe.txt              # Şehir mesafe verileri
├── ilcemesafe.txt               # İlçe mesafe verileri
└── README.md                    # Bu dosya
```

## Algoritma Detayları

### Dijkstra Algoritması Implementasyonu
```csharp
static double[] ApplyDijkstra(double[,] matrix, int startingCity, int numberOfCities)
{
    // En kısa mesafeleri saklayan dizi
    double[] shortestDistances = new double[numberOfCities];
    // Ziyaret edilmiş düğümler
    bool[] isVisited = new bool[numberOfCities];
    
    // Priority queue benzeri yapı
    var list = new List<(double distance, int city)>();
    
    // Algoritma implementasyonu...
}
```

### Mesafe Karşılaştırması
Program, her şehir çifti için:
1. Dijkstra algoritması ile en kısa mesafeyi hesaplar
2. Gerçek mesafe verisini okur
3. Aradaki farkı hesaplar ve raporlar
4. İstatistiksel analizler yapar

## Geliştirici Notları

- Mesafe değerleri kilometre cinsinden saklanır
- 10000 değeri, iki şehir arasında doğrudan bağlantı olmadığını gösterir
- Algoritma, sadece komşu şehirler arasındaki doğrudan mesafeleri kullanır
- İlçe analizinde İzmir merkez odaklı hesaplamalar yapılır

## Sınıf Yapısı

### Ana Sınıf: `E`
```csharp
class E
{
    static Dictionary<string, List<double>> cityDictionary;
    static double[][] jagged_array_city;
    static double[,] city_matrix_81_81;
    
    static void Main()                    // Ana program akışı
    static double[] ApplyDijkstra()       // Dijkstra algoritması
    static void PrintDistances()         // Sonuç yazdırma
    static void fillCityDictionary()     // Şehir verilerini doldurma
    static void readFile()               // Dosya okuma
}
```

## Performans

- **Şehir Sayısı**: 81 Türk şehri
- **İlçe Sayısı**: 30 İzmir ilçesi
- **Algoritma Karmaşıklığı**: O(V² + E) - Dijkstra
- **Bellek Kullanımı**: Yaklaşık 10MB (matrisler için)
- **Çalışma Süresi**: 1-2 saniye

## Lisans

Bu proje eğitim amaçlı geliştirilmiştir.
