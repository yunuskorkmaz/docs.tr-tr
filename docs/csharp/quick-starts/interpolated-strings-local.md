---
title: İlişkilendirme Öğreticisi - C# yerel quickstarts dize
description: Bu Hızlı Başlangıç, C# dize ilişkilendirme özelliği daha büyük bir dize biçimlendirilmiş ifade sonuçlarında için nasıl kullanılacağını gösterir.
author: rpetrusha
ms.author: ronpet
ms.date: 04/14/2018
ms.topic: get-started-article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 7ef904e30475d2cc0584f2baf56bc33a68e172d4
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="string-interpolation"></a>Dize ilişkilendirme

Bu hızlı başlangıç C# kullanmayı öğretir [dize ilişkilendirme](../language-reference/tokens/interpolated.md) tek bir sonuç dizeye değerleri eklemek için. C# kod yazma ve derleme ve onu çalıştırma sonuçları görüntüleyin. Hızlı başlangıç değerleri bir dize olarak ekleyin ve bu değerler farklı şekillerde biçimlendirmek nasıl Göster dersleri bir dizi içerir.

Bu Hızlı Başlangıç, geliştirme için kullanabileceğiniz bir makine olmasını bekler. .NET konu [Get Started 10 dakika içinde](https://www.microsoft.com/net/core) Mac, PC ya da Linux yerel geliştirme ortamınızı ayarlamak için yönergeler içerir. Hızlı bir genel bakış kullandığınız komutların bulunduğu [yerel quickstarts giriş](local-environment.md) daha fazla bilgi için bağlantılar ile birlikte. Aynı zamanda gerçekleştirebileceğinizi [etkileşimli sürüm](interpolated-strings.yml) tarayıcınızda Bu hızlı başlangıç.

## <a name="create-an-interpolated-string"></a>Ara değerli bir dize oluşturma

Adlı bir dizin oluşturun **Ara değerli**. Geçerli dizin olun ve bir konsol penceresinden aşağıdaki komutu çalıştırın:

```console
dotnet new console
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

Diğer veri türlerine sahip birkaç daha fazla dize ilişkilendirme örnek deneyelim.

## <a name="include-different-data-types"></a>Farklı veri türlerini içerir

Önceki bölümde dize ilişkilendirme içinde başka bir dize eklemek için kullanılır. Ara değerli ifade sonucu herhangi bir veri türü yine de olabilir. Şimdi Ara değerli bir dize çeşitli veri türlerinin değerlerini içerir.

Aşağıdaki örnekte, ilk olarak, bir özel veri türü tanımlarız `Vegetable` olan `Name` [özelliği](../properties.md) ve `ToString` yöntemi. İstemci kodu dize gösterimini almak için bu yöntemi kullanmak bir `Vegetable` örneği. Örnekte `Vegetable.ToString` yöntemi değerini döndürür `Name` konumunda başlatılan özelliği `Vegetable` Oluşturucusu:

```csharp
public Vegetable(string name) => Name = name;
```

Örneği oluşturuyoruz `Vegetable` kullanarak türü `new` anahtar sözcüğü ve Oluşturucusu name parametresi sağlanarak `Vegetable`:

```csharp
var item = new Vegetable("eggplant");
```

Son olarak, eklediğimiz `item` de içeren bir ara değerli dizesine değişken bir <xref:System.DateTime> değeri, bir <xref:System.Decimal> değeri ve `Unit` [numaralandırması](../programming-guide/enumeration-types.md) değeri. Tüm düzenleyicinizde C# kodu aşağıdaki kodla değiştirin ve sonra `dotnet run` komutu çalıştırmak için:

```csharp
using System;

public class Vegetable
{
   public Vegetable(string name) => Name = name;
   
   public string Name { get; }
   
   public override string ToString() => Name;
}

public class Program
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

Unutmayın Ara değerli ifade `item` Ara değerli dizesinde çözümler sonuç dizesinde "eggplant" metin. İfade sonucunun türü dize olmadığı durumlarda, sonuç aşağıdaki biçimde bir dizeye çözülmüş nedeni:

- Ara değerli ifade değerlendirilirse `null`, boş bir dize ("", veya <xref:System.String.Empty?displayProperty=nameWithType>) kullanılır.

- Ara değerli ifadesini değerlendiremedi değil, `null`, genellikle `ToString` sonuç türü yöntemi çağrılır. Bu uygulanması güncelleştirerek test `Vegetable.ToString` yöntemi. Hatta değil uygulayabilir `ToString` her C# veri türü bu yöntem bazı uygulaması olduğundan yöntemi. Test için açıklama tanımı `Vegetable.ToString` örnekte yöntemi (Bunu yapmak için bir açıklama simgesini put `//` önüne). Çıktıda varsayılan davranışı olan tam olarak nitelenmiş tür adıyla ("Vegetable" Bu örnekte), "eggplant" dizesi değiştirilir, <xref:System.Object.ToString?displayProperty=nameWithType> yöntemi. Varsayılan davranışını `ToString` bir numaralandırma türü için yöntemidir numaralandırma tanımı sırasında kullanılan bir değeri dize gösterimini dönün.

Bu örnek çıkışı, tarih (eggplant fiyat saniyede değiştirmez) çok kesin ve Fiyat değerini para birimi göstermez. Sonraki bölümde, dize ifadesi sonuçları gösterimlerini biçimini kontrol ederek bu sorunları gidermeye yönelik bilgi edineceksiniz.

## <a name="control-the-formatting-of-interpolated-expressions"></a>Ara değerli ifadelerin biçimlendirme denetimi

Önceki bölümde, iki hatalı biçimlendirilmiş dizeler sonuç dizeye eklendi. Bir yalnızca tarih uygun bir tarih ve saat değeri idi. İkinci para birimi, birim belirtmek istemediğiniz bir fiyat oluştu. Her iki adresine kolay sorunlardır. Dize ilişkilendirme belirtmenize olanak sağlar *biçim dizeleri* kontrol eden biçimlendirme belirli tür. Çağrı değiştirme `Console.WriteLine` önceki örnekten tarih ve fiyat ifadeler için biçim dizeleri aşağıdaki satırda gösterildiği gibi ekleyin:

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```

Ara değerli ifadesi iki nokta ile izleyerek bir biçim dizesi belirtin (":") ve biçim dizesi. "d" bir [standart tarih ve saat biçim dizesi](../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) kısa tarih biçiminde temsil eden. "C2" olan bir [standart sayısal biçim dizesi](../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) bir sayı olarak iki basamaklı bir para birimi değeri ondalık ayırıcıdan sonra temsil eden.

.NET kitaplıklarına türlerinde bir dizi önceden tanımlanmış bir biçim dizeleri kümesini destekler. Bu, tüm sayısal türler ve tarih ve saat türleri içerir. Biçim dizeleri destekleyen türler tam bir listesi için bkz: [biçim dizeleri ve .NET sınıf kitaplığı türleri](../../standard/base-types/formatting-types.md#stringRef) içinde [.NET biçimlendirme türleri](../../standard/base-types/formatting-types.md) makalesi.

Biçim dizeleri, metin düzenleyici ve, tarih ve saat ile sayısal değerin biçimlendirme değişikliklerin nasıl etkilediğini görmek için programı yeniden çalıştırın, bir değişiklik yaptığınızda değiştirmeyi deneyin. "D" değiştirmek `{date:d}` "(kısa saat biçimine görüntülemek için) t", "(yıl ve ay görüntülemek için) y" ve "yyyy" (yılı dört basamaklı bir sayı görüntülemek için). "C2" değiştirmek `{price:C2}` "e" (üstel gösterimde) ve (için ondalık ayırıcıdan sonra üç basamaklı sayısal bir değer) "F3".

Biçimlendirme denetleme ek olarak sonuç dizesinde bulunan biçimlendirilmiş dizeler hizalamasını ve alan genişliği de denetleyebilirsiniz. Sonraki bölümde, bunun nasıl yapılacağı öğreneceksiniz.

## <a name="control-the-field-width-and-alignment-of-interpolated-expressions"></a>Ara değerli ifadeleri hizalamasını ve alan genişliği denetleme

Ara değerli bir ifadenin sonucu dize olarak biçimlendirildiğinde normalde, bu dize bir sonuç dizesinde başında veya sonunda boşluk dahil edilir. Özellikle, bir veri kümesiyle bir alan genişliği denetim sahibi çalışırken ve metin hizalamasını daha okunabilir bir çıktı oluşturmak için yardımcı olur. Bu, bir metin düzenleyicisinde tüm kodu aşağıdaki kodla değiştirin görmek için yazın `dotnet run` programı çalıştırmak için:

```csharp
using System;
using System.Collections.Generic;

public class Example
{
   public static void Main()
   {
      var titles = new Dictionary<string, string>()
      {
          ["Doyle, Arthur Conan"] = "Hound of the Baskervilles, The",
          ["London, Jack"] = "Call of the Wild, The",
          ["Shakespeare, William"] = "Tempest, The"
      };

      Console.WriteLine("Author and Title List");
      Console.WriteLine();
      Console.WriteLine($"|{"Author",-25}|{"Title",30}|");
      foreach (var title in titles)
         Console.WriteLine($"|{title.Key,-25}|{title.Value,30}|");
   }
}
```

Yazarları adlarının sola hizalı ve bunlar yazdı başlıklarını sağa hizalı. Virgül ekleyerek hizalamasını belirtin (",") Ara değerli bir ifade sonra ve belirleme *minimum* alan genişliği. Belirtilen değer pozitif bir sayı ise, sağa hizalı alanıdır. Negatif bir sayı ise, sola hizalı alanıdır.

Gelen negatif işaretler kaldırmayı deneyin `{"Author",-25}` ve `{title.Key,-25}` kod ve aşağıdaki kodu yaptığı gibi örneği yeniden çalıştırın:

```csharp
Console.WriteLine($"|{"Author",25}|{"Title",30}|");
foreach (var title in titles)
   Console.WriteLine($"|{title.Key,25}|{title.Value,30}|");
```

Bu süre, yazar sağa hizalı bilgilerdir.

Hizalama belirticisi ve tek bir ara değerli ifade için bir biçim dizesi birleştirebilirsiniz. Bunu yapmak için ardından iki nokta ve biçim dizesi hizalama önce belirtin. Tüm içinde kod değiştirmek `Main` üç biçimlendirilmiş dizelerle görüntüleyen yöntemi aşağıdaki kod ile tanımlanan genişlikleriyle. Ardından girerek programı çalıştırın `dotnet run` komutu.

```csharp
Console.WriteLine($"[{DateTime.Now,-20:d}] Hour [{DateTime.Now,-10:HH}] [{1063.342,15:N2}] feet");
```

Çıktı aşağıdakine benzer görünür:

```console
[04/14/2018          ] Hour [16        ] [       1,063.34] feet
```

Dize ilişkilendirme quickstart tamamladınız.

İle devam edebilirsiniz [listesinde koleksiyonu](arrays-and-collections.md) kendi geliştirme ortamında hızlı başlangıç.

Dize ilişkilendirme hakkında daha fazla bilgi [dize ilişkilendirme](../language-reference/tokens/interpolated.md) C# Başvurusu'nda başlığı.
