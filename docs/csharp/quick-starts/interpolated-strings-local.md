---
title: Dize ilişkilendirme Öğreticisi - C# yerel hızlı başlangıçları
description: Bu hızlı başlangıçta C# dize ilişkilendirme özelliğinden daha büyük bir dizedeki biçimlendirilmiş bir ifade sonuçlarında için nasıl kullanılacağını gösterir.
author: rpetrusha
ms.author: ronpet
ms.date: 04/14/2018
ms.custom: mvc
ms.openlocfilehash: da111790ebbc299df16297650347045b9395a90f
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45617269"
---
# <a name="string-interpolation"></a>Dize ilişkilendirme

Bu hızlı başlangıçta, C# öğretilir [dize ilişkilendirme](../language-reference/tokens/interpolated.md) değerleri bir tek bir sonuç dizesine eklemek için. C# kodu yazacak ve derleyerek ve çalıştırarak bunu sonuçlarını göreceksiniz. Hızlı Başlangıç bir dizi değer bir dize olarak eklemek ve bu değerleri farklı yollarla biçimlendiren işlemini gösteren ders içerir.

Bu hızlı başlangıçta, geliştirme için kullanabileceğiniz bir makine olmasını bekliyor. .NET konu [10 dakika içinde kullanmaya başla](https://www.microsoft.com/net/core) Mac, PC veya Linux üzerinde yerel geliştirme ortamınızı ayarlamaya yönelik yönergeler içerir. Kullandığınız hesap komutları hızlı bir genel bakış yer [yerel hızlı başlangıçları giriş](local-environment.md) daha ayrıntılı bilgi için bağlantılarla birlikte. Ayrıca tamamlayabilirsiniz [etkileşimli sürüm](interpolated-strings.yml) tarayıcınızda Bu hızlı başlangıç.

## <a name="create-an-interpolated-string"></a>İlişkilendirilmiş dize oluşturma

Adlı bir dizin oluşturmak **ilişkilendirilmiş**. Geçerli dizin olun ve konsol penceresinden aşağıdaki komutu çalıştırın:

```console
dotnet new console
```

Bu komut geçerli dizinde yeni bir .NET Core konsol uygulaması oluşturur.

Açık **Program.cs** satırı değiştirin ve tercih ettiğiniz düzenleyiciyi `Console.WriteLine("Hello World!");` aşağıdaki kodla değiştirin burada `<name>` adınızla:

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```

Bu kod yazarak deneme `dotnet run` konsol pencerenizde. Programı çalıştırdığınızda karşılamada adınızı içeren tek bir dize görüntüler. İçinde yer alan dize <xref:System.Console.WriteLine%2A> yöntem çağrısında bir *ilişkilendirilmiş bir dizedir*. Tek bir dize olanak sağlayan bir şablon türüdür (adlı *sonuç dizesi*), gömülü kod içeren bir dizeden. İlişkilendirilmiş dizeler özellikle bir dize veya dizeleri birleştirirken (bir araya getirme) değerlerini eklemek için yararlıdır.

Bu basit örnek her ilişkilendirilmiş dizenin sahip olması gereken iki öğeyi içerir:

- İle başlayan bir dize sabit değeri `$` açma tırnak işareti karakterinden önce karakter karakter. Arasında boşluk olamaz `$` sembol ve tırnak işareti karakteri. (Görmek istiyorsanız, ne olacağını yaptığınızda, sonra boşluk Ekle `$` karakter, dosyayı kaydedin ve yazarak programı yeniden çalıştırın `dotnet run` konsol penceresinde. C# Derleyici bir hata iletisi görüntüler "CS1056 hata: Beklenmeyen karakter '$'".)

- Bir veya daha fazla *ilişkilendirilmiş ifade*. İlişkilendirilmiş ifade bir açma ve kapatma ayracı gösterilir (`{` ve `}`). Bir değer döndüren bir C# ifadesini ekleyebilirsiniz (dahil olmak üzere `null`) küme ayraçları içinde.

Diğer veri türlerinden bazılarıyla birkaç daha fazla dize ilişkilendirme örneği deneyelim.

## <a name="include-different-data-types"></a>Farklı veri türleri ekleme

Önceki bölümde, bir dizenin içine eklemek için dize ilişkilendirme kullanılır. İlişkilendirilmiş ifade sonucu herhangi bir veri türünde ancak olabilir. Şimdi bir aradeğerlendirme dizesinde değerleri çeşitli veri türlerini içerir.

Aşağıdaki örnekte, ilk olarak tanımlarız bir [sınıfı](../programming-guide/classes-and-structs/classes.md) veri türü `Vegetable` olan `Name` [özelliği](../properties.md) ve `ToString` [yöntemi](../methods.md), hangi [geçersiz kılmalar](../language-reference/keywords/override.md) davranışını <xref:System.Object.ToString?displayProperty=nameWithType> yöntemi. [ `public` Erişim değiştiricisi](../language-reference/keywords/public.md) bu yöntem herhangi bir istemci kod, dize gösterimini almaya kullanılabilmesini bir `Vegetable` örneği. Örnekte `Vegetable.ToString` yöntemi değerini döndürür `Name` sırasında başlatılır özelliği `Vegetable` [Oluşturucusu](../programming-guide/classes-and-structs/constructors.md):

```csharp
public Vegetable(string name) => Name = name;
```

Biz bir örneğini oluşturup `Vegetable` sınıfı kullanarak [ `new` anahtar sözcüğü](../language-reference/keywords/new-operator.md) Oluşturucusu bir name parametresi sağlayarak `Vegetable`:

```csharp
var item = new Vegetable("eggplant");
```

Son olarak, ekliyoruz `item` değişken de içeren ilişkilendirilmiş dize halinde bir <xref:System.DateTime> değeri bir <xref:System.Decimal> değeri ve bir `Unit` [numaralandırması](../programming-guide/enumeration-types.md) değeri. Tüm Düzenleyici C# kodu aşağıdaki kodla değiştirin ve ardından `dotnet run` komutu çalıştırmak için:

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
   public enum Unit { item, kilogram, gram, dozen };

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

Unutmayın ilişkilendirilmiş ifade `item` aradeğerlendirme dizesinde çözümleniyor sonuç dizesindeki "eggplant" metni. Deyim sonucu türü dize olmadığı durumlarda, sonuç şu şekilde bir dizeye çözümlenir çünkü:

- İlişkilendirilmiş ifade değerlendirilirse `null`, boş bir dize ("", veya <xref:System.String.Empty?displayProperty=nameWithType>) kullanılır.

- İlişkilendirilmiş ifade değerlendirme değil, `null`, genellikle `ToString` sonuç türü yöntemi çağrılır. Bu uygulamasını güncelleştirerek test `Vegetable.ToString` yöntemi. Bile uygulanması gerekmeyebilir `ToString` her türü bu yöntemin bazı uygulama olduğundan yöntemi. Bunu test etmek için tanımı için açıklama `Vegetable.ToString` örnekte yöntemi (Bunu yapmak için bir açıklama simgesini yerleştirmek `//`, önündeki). Çıkışta "eggplant" dizesi, varsayılan davranış, tam olarak nitelenmiş tür adıyla ("Vegetable" Bu örnekte), değiştirilir, <xref:System.Object.ToString?displayProperty=nameWithType> yöntemi. Varsayılan davranışını `ToString` yöntemi için bir sabit listesi değeri, değerin dize gösterimi döndürmektir.

Bu örnek çıktıda, (eggplant fiyatı, her saniye değişmez) kesin tarih ve Fiyat değerini para birimi göstermez. Sonraki bölümde, ifade sonuçları dize temsillerini biçimini denetleyerek bu sorunları gidermek nasıl öğreneceksiniz.

## <a name="control-the-formatting-of-interpolated-expressions"></a>İlişkilendirilmiş ifadelerin biçimlendirmesini denetleme

Önceki bölümde, sonuç dizesine yetersiz şekilde biçimlendirilmiş iki dize eklenmişti. Bir tarih yalnızca uygun bir tarih ve saat değeri oluştu. İkinci para biriminin göstermek istemediğiniz bir fiyattı. Her iki sorun da kolayca giderilebilir. Dize ilişkilendirme belirtmenize olanak tanır *biçim dizeleri* belirli türlerin biçimlendirmesini denetleyen. Çağrısını değiştirin `Console.WriteLine` aşağıdaki satırda gösterildiği gibi tarih ve fiyat ifadeler için biçim dizeleri dahil etmek için önceki örnekte:

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```

İki nokta ile ilişkilendirilmiş ifade izleyerek bir biçim dizesi belirtin (":") ve biçim dizesi. "d" bir [standart tarih ve saat biçim dizesi](../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) temsil eden kısa tarih biçimi. "C2" olan bir [standart sayısal biçim dizesi](../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) , bir sayı olarak iki basamakla para birimi değeri ondalık ayırıcıdan sonra temsil eder.

.NET kitaplıklarına türlerinde bir dizi önceden tanımlanmış bir dizi biçim dizesini destekler. Bunlar, tüm sayısal türlerin ve tarih ve saat türleri içerir. Biçim dizelerini destekleyen türler tam bir listesi için bkz. [biçim dizeleri ve .NET sınıfı kitaplık türleri](../../standard/base-types/formatting-types.md#stringRef) içinde [NET'teki biçimlendirme türleri](../../standard/base-types/formatting-types.md) makalesi.

Metin düzenleyici ve tarih ve saat ile sayısal biçimlendirme değişikliklerin nasıl etkilediğini görmek için programı yeniden çalıştırın ve değişiklik yaptığınızda her zaman'daki biçim dizelerini değiştirmeyi deneyin. "D" değiştirmek `{date:d}` "(kısa saat biçimini görüntülemek için) t", "(yıl ve ay görüntülemek için) y" ve "yyyy" (yılı dört basamaklı bir sayı görüntülemek için). "C2" değiştirmek `{price:C2}` (üstel gösterim için için) "e" ve "F3" (için ondalık ayırıcıdan sonra üç basamak içeren sayısal bir değer).

Biçimlendirmenin yanı sıra alan genişliğini ve sonuç dizesine eklenir biçimlendirilmiş dizeler hizalamasını da denetleyebilirsiniz. Sonraki bölümde, bunun nasıl yapılacağını öğreneceksiniz.

## <a name="control-the-field-width-and-alignment-of-interpolated-expressions"></a>Alan genişliğini ve hizalamasını ilişkilendirilmiş ifadeler denetim

İlişkilendirilmiş ifade sonucu dize olarak biçimlendirildiğinde normalde, bu dize bir sonuç dizesinde baştaki veya sondaki boşlukları dahil edilir. Özellikle bir veri kümesiyle bir alan genişliğini denetleyebilir çalışırken ve metin hizalamasını daha okunabilir bir çıktı oluşturmak için yardımcı olur. Ardından, metin düzenleyici tüm kodu aşağıdaki kodla değiştirin. Bu görmek için şunu yazın `dotnet run` programı çalıştırmak için:

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

Yazarlar adları sola hizalanmış ve bunlar yazdı başlıkları sağa hizalanır. Virgül ekleyerek hizalamayı belirtin (",") ilişkilendirilmiş bir ifadenin sonra ve belirleme *minimum* alan genişliği. Belirtilen değer pozitif bir sayıysa alan sağa hizalanır. Negatif bir sayı ise, alan sola hizalanır.

Negatif işaretlerini kaldırmayı deneyip `{"Author",-25}` ve `{title.Key,-25}` kodu ve şu kod gibi örneği tekrar çalıştırın:

```csharp
Console.WriteLine($"|{"Author",25}|{"Title",30}|");
foreach (var title in titles)
   Console.WriteLine($"|{title.Key,25}|{title.Value,30}|");
```

Bu kez, yazar bilgileri sağa hizalanır.

Hizalama tanımlayıcısı ve bir biçim dizesi için tek bir ilişkilendirilmiş ifadede birleştirebilirsiniz. Bunu yapmak için ardından iki nokta işareti ve biçim dizesi hizalama ilk olarak belirtin. Tüm kod içinde değiştirmek `Main` ile biçimlendirilmiş üç dizeyi görüntüleyen yöntemini aşağıdaki kodla alan genişlikleri tanımlı. Ardından girerek programı çalıştırın `dotnet run` komutu.

```csharp
Console.WriteLine($"[{DateTime.Now,-20:d}] Hour [{DateTime.Now,-10:HH}] [{1063.342,15:N2}] feet");
```

Çıktı aşağıdakine benzer olacaktır:

```console
[04/14/2018          ] Hour [16        ] [       1,063.34] feet
```

Dize ilişkilendirme hızlı başlangıcı tamamladığınıza göre.

İle devam edebilir [liste koleksiyon](arrays-and-collections.md) kendi geliştirme ortamında hızlı başlangıç.

Daha fazla bilgi için [dize ilişkilendirme](../language-reference/tokens/interpolated.md) konu ve [dize ilişkilendirme C#](../tutorials/string-interpolation.md) öğretici.
