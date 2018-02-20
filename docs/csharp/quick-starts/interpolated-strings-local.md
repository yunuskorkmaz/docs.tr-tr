---
title: "Ara değerli dizeler Öğreticisi - C# yerel quickstarts"
description: "Ara değerli dizeler hakkında bu quickstart incude büyük bir dizi deyimde sonucu için C# kod yazın."
author: rpetrusha
ms.author: ronpet
ms.date: 01/11/2018
ms.topic: get-started-article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: b6089b69eb350fce29f86f19f5abeb44acb4b6b4
ms.sourcegitcommit: 96cc82cac4650adfb65ba351506d8a8fbcd17b5c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2018
---
# <a name="interpolated-strings"></a>Ara değerli dizeler

Bu hızlı başlangıç Ara değerli dizeler C# dilinde bir tek çıkışına dizeye değerleri eklemek için nasıl kullanılacağını öğretir. C# kod yazma ve derleme ve onu çalıştırma sonuçları görüntüleyin. Hızlı başlangıç değerleri dizeleri eklemek ve bu değerler farklı şekillerde biçimlendirmek dersleri bir dizi içerir.

Bu Hızlı Başlangıç, geliştirme için kullanabileceğiniz bir makine olmasını bekler. .NET konu [Get Started 10 dakika içinde](https://www.microsoft.com/net/core) Mac, PC ya da Linux yerel geliştirme ortamınızı ayarlamak için yönergeler içerir. Hızlı bir genel bakış kullandığınız komutların bulunduğu [yerel quickstarts giriş](local-environment.md) daha fazla bilgi için bağlantılar ile birlikte. 

## <a name="create-an-interpolated-string"></a>Ara değerli bir dize oluşturma

Adlı bir dizin oluşturun **Ara değerli quickstart**. Geçerli dizin olun ve bir konsol penceresinden aşağıdaki komutu çalıştırın:

```console
dotnet new console -n interpolated -o .
```

Bu komut, geçerli dizinde yeni bir .NET Core konsol uygulaması oluşturur.

Açık **Program.cs** sık kullanılan Düzenleyicisi ve Değiştir satır `Console.WriteLine("Hello World!");` Burada, yerini aşağıdaki kodla `<name>` adıyla:

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```
Bu kod yazarak deneyin `dotnet run` konsol penceresinde. Programını çalıştırdığınızda, tebrik adınızı içeren tek bir dize görüntüler. Dahil dize <xref:System.Console.WriteLine%2A> yöntemi çağrısı bir *Ara değerli dize*. Tek bir dize oluşturmanıza olanak sağlayan şablon türüdür (adlı *neden dize*) bir dizeden katıştırılmış kodu içerir. Ara değerli dizeler değerleri bir dize veya dize (bir araya getirme) birleştirme eklemek için özellikle yararlıdır. 
    
Bu basit örnekte, her ara değerli bir dize olmalıdır iki öğeleri içerir: 

- İle başlayan bir değişmez dize değeri `$` açılış tırnak işaretlemeden önce karakter karakter. Arasında herhangi bir boşluk olamaz `$` simge ve tırnak işareti karakteri. (Görmek isterseniz ne olur bir eklerseniz, bir boşluk sonra `$` karakter, dosyayı kaydedin ve yazarak programı yeniden çalıştırın `dotnet run` konsol penceresinde. C# Derleyici bir hata iletisi görüntüler "hata CS1056: Beklenmeyen karakter '$'".) 

- Bir veya daha fazla *Ara değerli ifadeleri*. Ara değerli bir ifadenin bir açma ve kapatma parantezi tarafından belirtilir (`{` ve `}`). Bir değer döndürür herhangi C# ifade koyabilirsiniz (de dahil olmak üzere `null`) kaşlı ayraçlar içinde. 

Diğer veri türlerine sahip birkaç fazla ara değerli dize örnek deneyelim.
    
## <a name="include-different-data-types"></a>Farklı veri türlerini içerir

Önceki bölümde Ara değerli bir dize içinde başka bir dize eklemek için kullanılır. Ara değerli dize ifadesi ancak herhangi bir veri türü olabilir. Birden çok veri türlerinin değerlerine sahip bir ara değerli dize deneyelim. 
    
Aşağıdaki örnek, Ara değerli ifadelerle içerir bir `Vegetable` nesnesi, bir üyesi `Unit` numaralandırma, bir <xref:System.DateTime> değeri ve <xref:System.Decimal> değeri. Tüm düzenleyicinizde C# kodu aşağıdaki kodla değiştirin ve sonra `console run` komutu çalıştırmak için:

```csharp
using System;

public class Vegetable
{
   public Vegetable(string name) => Name = name;
   
   public string Name { get; }
   
   public override string ToString() => Name;
}

public class Example
{
   public enum Unit { item, pound, ounce, dozen };
   
   public static void Main()
   {
      var item = new Vegetable("eggplant");
      var date = DateTime.Now;
      var price = 1.99m;
      var unit = Unit.item;
      Console.WriteLine($"On {date}, the price of {item} was {price} per {unit}.");
   }
}
```
    
İkinci ifade Ara değerli Not dahildir `item` nesne konsolda görüntülenen sonuç dizesinde ve bu durumda "eggplant" dizesi sonuç dizesine eklenir. Ara değerli ifade türü bir dize değil, C# Derleyici aşağıdakileri yapar nedeni:

- Ara değerli ifade ise `null`, Ara değerli ifade boş bir dize döndürür ("", veya <xref:System.String.Empty?displayProperty=nameWithType>).

- Ara değerli ifade değilse `null`, `ToString` Ara değerli ifade türü yöntemi çağrılır. Bu tanımını yorum tarafından test `Vegetable.ToString` açıklama simgesini koyarak örnekte yöntemi (`//`), önünde. Çıktıda "eggplant" dize türü tarafından değiştirilir adı, "Meyve", varsayılan davranışını olduğu <xref:System.Object.ToString?displayProperty=nameWithType> yöntemi.   

Bu örnek çıkışı, tarih (eggplant fiyat ikinciye farklılık göstermez) çok kesin ve Fiyat değerini para birimi göstermez. Sonraki bölümde, Ara değerli ifadeleri tarafından döndürülen dize biçimi denetleyerek bu sorunları gidermeye yönelik bilgi edineceksiniz.

## <a name="control-the-formatting-of-interpolated-expressions"></a>Ara değerli ifadelerin biçimlendirme denetimi

Önceki bölümde, iki hatalı biçimlendirilmiş dizeler sonuç dizeye eklendi. Bir yalnızca tarih uygun bir tarih ve saat değeri idi. İkinci para birimi, birim belirtmeyen bir fiyat oluştu. Her iki adresine kolay sorunlardır. Ara değerli ifadeleri içerebilir *biçim dizeleri* kontrol eden biçimlendirme belirli tür. Çağrı değiştirme `Console.WriteLine` önceki örnekten tarih ve fiyat alanları için biçim belirticisi aşağıdaki satırda gösterildiği gibi ekleyin:

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```
    
Ara değerli ifade bir iki nokta üst üste ve biçim dizesi ile izleyerek bir biçim dizesi belirtin. "d" bir [standart tarih ve saat biçim dizesi](../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) kısa tarih biçiminde temsil eden. "C2" olan bir [standart sayısal biçim dizesi](../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) bir sayı olarak iki basamaklı bir para birimi değeri ondalık ayırıcıdan sonra temsil eden.

.NET standart kitaplıkları türlerinde bir dizi önceden tanımlanmış bir biçim dizeleri kümesini destekler. Bu, tüm sayısal türler ve tarih ve saat türleri içerir. Biçim dizeleri destekleyen türler tam bir listesi için bkz: [biçim dizeleri ve .NET sınıf kitaplığı türleri](../../standard/base-types/formatting-types.md#stringRef) içinde [.NET biçimlendirme türleri](../../standard/base-types/formatting-types.md) makalesi. Herhangi bir tür biçim dizeleri kümesi destekleyebilir ve varolan türleri için özel biçimlendirme sağlayan özel biçimlendirme uzantıları da geliştirebilirsiniz. Özel biçimlendirme sağlayarak hakkında bilgi için bir <xref:System.ICustomFormatter> uygulama, bkz: [özel biçimlendirme ICustomFormatter ile](../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter) içinde [.NET biçimlendirme türleri](../../standard/base-types/formatting-types.md) makale.

Biçim dizeleri, metin düzenleyici ve, tarih ve saat ile sayısal değerin biçimlendirme değişikliklerin nasıl etkilediğini görmek için programı yeniden çalıştırın, bir değişiklik yaptığınızda değiştirmeyi deneyin. "D" değiştirmek `{date:d}` "(kısa saat biçimine görüntülemek için) t", "(yıl ve ay görüntülemek için) y" ve "yyyy" (yılı dört basamaklı bir sayı görüntülemek için). "C2" değiştirmek `{price:C2}` "e" (üstel gösterimde) ve (için ondalık ayırıcıdan sonra üç basamaklı sayısal bir değer) "F3".

Biçimlendirme denetleme ek olarak, bir ara değerli ifadesi tarafından döndürülen dize hizalamasını ve alan genişliği de denetleyebilirsiniz. Sonraki bölümde, bunun nasıl yapılacağı öğreneceksiniz.

## <a name="control-the-field-width-and-alignment-of-interpolated-expressions"></a>Ara değerli ifadeleri hizalamasını ve alan genişliği denetleme

Normalde, bir ara değerli ifadesi tarafından döndürülen dize sonuç dizesinde yer aldığında, başında veya sonunda boşluk içeriyor. Özellikle, kullanmakta olduğunuz bir veri kümesi, Ara değerli ifadeler ile örneklerini alan genişliği ve onun hizalamasını belirtin olanak sağlar. Bu, bir metin düzenleyicisinde tüm kodu aşağıdaki kodla değiştirin görmek için yazın `console run` programı çalıştırmak için:
    
```csharp
using System;
using System.Collections.Generic;

public class Example
{
   public static void Main()
   {
      var titles = new Dictionary<string, string>();
      titles.Add("Doyle, Arthur Conan", "Hound of the Baskervilles, The");
      titles.Add("London, Jack", "Call of the Wild, The");
      titles.Add("Shakespeare, William", "Tempest, The");

      Console.WriteLine("Author and Title List");
      Console.WriteLine($"\n{"Author",-25}    {"Title",30}\n");
      foreach (var title in titles)
         Console.WriteLine($"{title.Key,-25}     {title.Value,30}");
   }
}
```
    
Yazarları adlarının sola hizalı ve bunlar yazdı başlıklarını sağa hizalı. Virgül ekleyerek hizalamasını belirtin (",") ifade ve alan genişliği belirleme sonra. Alan genişliği pozitif bir sayı ise, sağa hizalı alandır:

```text
{expression, width}
```

Alan genişliği negatif bir sayı ise, sola hizalı alandır:

```text
{expression, -width}
```

Gelen negatif işaretler kaldırmayı deneyin `{"Author",-25}` ve `{title.Key,-25}` Ara değerli ifadeleri ve aşağıdaki kodu yaptığı gibi örneği yeniden çalıştırın:

```csharp
Console.WriteLine($"\n{"Author",25}    {"Title",30}\n");
foreach (var title in titles)
   Console.WriteLine($"{title.Key,25}     {title.Value,30}");
```

Bu süre, yazar sağa hizalı bilgilerdir.

Bir alan genişliği ve tek bir ara değerli ifadede bir biçim dizesi birleştirebilirsiniz. Ardından bir iki nokta üst üste ve biçim dizesi alan genişliği önce gelir. Tüm içinde kod değiştirmek `Main` üç biçimlendirilmiş dizelerle görüntüleyen yöntemi aşağıdaki kod ile tanımlanan genişlikleriyle. Ardından girerek programı çalıştırın `dotnet run` komutu.

```csharp
Console.WriteLine($"{DateTime.Now,-20:d} Hour {DateTime.Now,-10:HH} {1063.342,15:N2} feet");
```
Çıktı aşağıdakine benzer görünür:

```console
1/11/2018            Hour 09                1,063.34 feet
```

Ara değerli dizeler hızlı başlangıç tamamladınız. 
    
İle devam edebilirsiniz [dizileri ve koleksiyonları](arrays-and-collections.md) kendi geliştirme ortamında hızlı başlangıç.

Ara değerli dizeler ile çalışma hakkında daha fazla bilgiyi [Ara değerli dizeler](../language-reference/keywords/interpolated-strings.md) C# Başvurusu'nda başlığı.

