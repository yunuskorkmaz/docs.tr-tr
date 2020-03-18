---
title: String enterpolasyonu - C# öğretici
description: Bu öğretici, daha büyük bir dize biçimlendirilmiş ifade sonuçlarını eklemek için C# dize enterpolasyon özelliğini nasıl kullanacağınızı gösterir.
ms.date: 10/23/2018
ms.openlocfilehash: 593f3a77370da73dfd5f090be98112327b86b1f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75346786"
---
# <a name="use-string-interpolation-to-construct-formatted-strings"></a>Biçimlendirilmiş dizeleri oluşturmak için dize enterpolasyonunu kullanma

Bu öğretici, değerleri tek bir sonuç dizesine eklemek için C# [dize enterpolasyonunu](../../language-reference/tokens/interpolated.md) nasıl kullanacağınızı öğretir. C# kodu yazar sınız ve derleme ve çalıştırma sonuçlarını görürsünüz. Öğretici, değerleri bir dize içine nasıl ekleyip bu değerleri farklı şekillerde biçimlendireceklerini gösteren bir dizi ders içerir.

Bu öğretici, geliştirme için kullanabileceğiniz bir makineniz olmasını bekler. .NET öğretici [Hello World 10 dakika içinde](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) Windows, Linux veya macOS'ta yerel geliştirme ortamınızı ayarlama talimatları na sahiptir. Ayrıca tarayıcınızda bu öğretici [interaktif sürümünü](interpolated-strings.yml) tamamlayabilirsiniz.

## <a name="create-an-interpolated-string"></a>İlişkilendirilmiş dize oluşturma

*Enterpolasyonadı*adlı bir dizin oluşturun. Geçerli dizini yapın ve konsol penceresinden aşağıdaki komutu çalıştırın:

```dotnetcli
dotnet new console
```

Bu komut, geçerli dizinde yeni bir .NET Core konsol uygulaması oluşturur.

En sevdiğiniz düzenleyicide *Program.cs* açın `Console.WriteLine("Hello World!");` ve satırı adınızı değiştirebileceğiniz `<name>` aşağıdaki kodla değiştirin:

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```

Konsol pencerenize `dotnet run` yazarak bu kodu deneyin. Programı çalıştırdığınızda program, karşılamada adınızı içeren tek bir dize görüntüler. <xref:System.Console.WriteLine%2A> Yöntem çağrısında yer alan *dize, enterpolasyonlu dize ifadesidir.* Bu, gömülü kod içeren bir dizeden tek bir dize (*sonuç dizesi* olarak adlandırılır) oluşturmanızı sağlayan bir şablon türüdür. İlişkilendirilmiş dizeler özellikle bir dizeye değer eklerken veya dizeleri birleştirirken kolaylık sağlar.

Şu basit örnek her ilişkilendirilmiş dizenin sahip olması gereken iki öğeyi içerir:

- Açma tırnak işareti karakterinden önce `$` karakteriyle başlayan bir dize sabit değeri. `$` sembolü ile tırnak işareti karakteri arasında boşluk olamaz. (Eğer bir tane eklerseniz ne olacağını görmek istiyorsanız, karakterden `$` sonra bir boşluk ekleyin, dosyayı `dotnet run` kaydedin ve konsol penceresine yazarak programı yeniden çalıştırın. C# derleyicisi bir hata iletisi görüntüler, "hata CS1056: Beklenmeyen karakter '$'".)

- Bir veya daha fazla *enterpolasyon ifadeleri*. Enterpolasyon ifadesi bir açma ve kapatma`{` `}`ayracı ile gösterilir ( ve). Ayraçlar arasında bir değer (`null` dahil) döndüren herhangi bir C# ifadesini ekleyebilirsiniz.

Diğer bazı veri türleri ile birkaç dize enterpolasyon örnekleri deneyelim.

## <a name="include-different-data-types"></a>Farklı veri türleri ekleme

Önceki bölümde, bir dizeyi diğerinin içine eklemek için dize enterpolasyonunu kullandınız. Bir enterpolasyon ifadesinin sonucu olsa da, herhangi bir veri türü olabilir. Çeşitli veri türlerinin değerlerini enterpolasyonlu bir dizeye ekleyelim.

Aşağıdaki örnekte, önce bir [özelliği](../../properties.md) `Vegetable` ve `Name` <xref:System.Object.ToString?displayProperty=nameWithType> [yöntemi](../../methods.md)olan `ToString` bir [sınıf](../../programming-guide/classes-and-structs/classes.md) veri türü (yöntemin davranışını [geçersiz kılan)](../../language-reference/keywords/override.md) tanımlarız. [ `public` Erişim değiştiricisi,](../../language-reference/keywords/public.md) bir örneğin dize gösterimini almak `Vegetable` için bu yöntemi herhangi bir istemci kodu için kullanılabilir hale getirir. Örnekte `Vegetable.ToString` `Name` `Vegetable` [yöntem, oluşturucuda](../../programming-guide/classes-and-structs/constructors.md)başharfe dönen özelliğin değerini döndürür:

```csharp
public Vegetable(string name) => Name = name;
```

Daha sonra [ `new` işleç](../../language-reference/operators/new-operator.md) `Vegetable` kullanarak `item` ve oluşturucu `Vegetable`için bir ad vererek adlı sınıfın bir örneği oluşturmak:

```csharp
var item = new Vegetable("eggplant");
```

Son olarak, `item` değişkeni bir <xref:System.DateTime> değer, bir <xref:System.Decimal> değer ve `Unit` [numaralandırma](../../language-reference/builtin-types/enum.md) değeri de içeren enterpolasyonlu bir dizeye dahil ediyoruz. Düzenleyicinizdeki C# kodunun tümünün yerine aşağıdaki kodu girin `dotnet run` ve çalıştırmak için komutu kullanın:

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

Enterpolasyon dizesinde enterpolasyon ifadesinin `item` sonuç dizesinde "patlıcan" metnine çözüldüğünü unutmayın. Bunun nedeni, ifade sonucunun türü bir dize olmadığında, sonucun aşağıdaki şekilde bir dize yle çözülmesidir:

- Enterpolasyon ifadesi , `null`boş bir dize (""veya <xref:System.String.Empty?displayProperty=nameWithType>) için değerlendirilirse.

- Enterpolasyon ifadesi ,genellikle sonuç `null`türünün `ToString` yöntemi olarak adlandırılır. `Vegetable.ToString` Yöntemin uygulanmasını güncelleştirerek bunu test edebilirsiniz. Her tür bu yöntemin `ToString` bazı uygulama olduğundan bile yöntemi uygulamak için gerek olmayabilir. Bunu test etmek için, örnekteki `Vegetable.ToString` yöntemin tanımını yorumla (bunu `//`yapmak için, önüne bir yorum sembolü koyun). Çıktıda, "patlıcan" dizesi, <xref:System.Object.ToString?displayProperty=nameWithType> yöntemin varsayılan davranışı olan tam nitelikli tür adı (bu örnekte "Sebze" ile) değiştirilir. Numaralandırma değeri `ToString` için yöntemin varsayılan davranışı, değerin dize temsilini döndürmektir.

Bu örnekten çıktıda, tarih çok kesindir (patlıcanın fiyatı her saniye değişmez) ve fiyat değeri bir birim para birimi göstermez. Sonraki bölümde, ifade sonuçlarının dize gösterimlerinin biçimini denetleyerek bu sorunları nasıl düzelteceğinizi öğreneceksiniz.

## <a name="control-the-formatting-of-interpolation-expressions"></a>Enterpolasyon ifadelerinin biçimlendirmesini denetleme

Önceki bölümde, iki kötü biçimlendirilmiş dizeleri sonuç dizesine eklenmiştir. Biri tarih ve saat değeriydi, bunlardan yalnızca tarih değeri uygundu. İkincisi, para birimini göstermeyen bir fiyattı. Her iki sorun da kolayca giderilebilir. String enterpolasyonu, belirli türlerin biçimlendirmesini denetleyen *biçim dizeleri* belirtmenizi sağlar. Aşağıdaki satırda `Console.WriteLine` gösterildiği gibi tarih ve fiyat ifadeleri için biçim dizeleri eklemek için önceki örnekten çağrıyı değiştirin:

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```

Bir iki nokta üst üste (":") ve biçim dizesi ile enterpolasyon ifadesini izleyerek bir biçim dizesi belirtirsiniz. “d”, kısa tarih biçimini ifade eden [standart tarih ve saat biçimi dizesidir](../../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier). “C2”, ondalık ayırıcıdan sonra gelen iki basamakla para birimi değeri olarak bir sayıyı ifade eden [standart sayısal biçim dizesidir](../../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier).

.NET kitaplıklarında bulunan bir dizi tür, önceden tanımlanmış biçim dizeleri kümesini destekler. Bunlara tüm sayısal türlerin yanı sıra tarih ve saat türleri de dahildir. Biçim dizelerini destekleyen türlerin tam listesi için [.NET’teki Biçimlendirme Türleri](../../../standard/base-types/formatting-types.md) başlıklı makalede bulunan [Biçim Dizeleri ve .NET Sınıfı Kitaplık Türleri](../../../standard/base-types/formatting-types.md#format-strings-and-net-types) bölümüne bakın.

Metin düzenleyicinizdeki biçim dizelerini değiştirmeyi deneyin ve her değişiklik yaptığınızda, değişikliklerin tarih ve saatin biçimlendirmesini ve sayısal değeri nasıl etkilediğini görmek için programı yeniden çalıştırın. `{date:d}` içindeki “d”yi “t” olarak (kısa saat biçimini görüntülemek için), “y” olarak (yılı ve ayı görüntülemek için) ve “yyyy” olarak (yılı dört basamaklı sayı olarak görüntülemek için) değiştirin. `{price:C2}` içindeki “C2”yi “e” olarak (üstel gösterim için) ve “F3” olarak (ondalık ayırıcıdan sonra üç basamak içeren sayısal bir değer için) değiştirin.

Biçimlendirmeyi denetlemeye ek olarak, sonuç dizesinde bulunan biçimlendirilmiş dizelerin alan genişliğini ve hizalanmasını da denetleyebilirsiniz. Bir sonraki bölümde, bunu nasıl yapacağınızı öğreneceksiniz.

## <a name="control-the-field-width-and-alignment-of-interpolation-expressions"></a>Enterpolasyon ifadelerinin alan genişliğini ve hizalanmasını denetleme

Normalde, bir enterpolasyon ifadesinin sonucu dize biçimlendirilmiş olduğunda, bu dize satır aralığı veya boşluklar izlemeden bir sonuç dizesine dahil edilir. Özellikle bir veri kümesiyle çalışırken, alan genişliğini ve metin hizalamasını denetlenebilmek daha okunabilir bir çıktı üretmeye yardımcı olur. Bunu görmek için, metin düzenleyicinizdeki tüm kodu aşağıdaki kodla değiştirin ve ardından programı yürütmek için yazın: `dotnet run`

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

Yazarların adları sol hizalı ve yazdıkları başlıklar sağ hizalı. Enterpolasyon ifadesinden sonra virgül (",") ekleyerek ve *minimum* alan genişliğini belirleyerek hizalamayı belirtirsiniz. Belirtilen değer pozitif bir sayıysa, alan doğru hizalanır. Negatif bir sayıysa, alan sol hizalıdır.

Negatif işaretleri `{"Author",-25}` ve `{title.Key,-25}` kodu kaldırmayı deneyin ve aşağıdaki kod gibi örneği yeniden çalıştırın:

```csharp
Console.WriteLine($"|{"Author",25}|{"Title",30}|");
foreach (var title in titles)
   Console.WriteLine($"|{title.Key,25}|{title.Value,30}|");
```

Bu kez, yazar bilgileri sağ hizalanmış.

Tek bir enterpolasyon ifadesi için bir hizalama belirtici ve biçim dizesi birleştirebilirsiniz. Bunu yapmak için önce hizalamayı, ardından bir üst üste ve biçim dizesini belirtin. Yöntemiçindeki `Main` tüm kodu, tanımlı alan genişliklerine sahip üç biçimlendirilmiş dize görüntüleyen aşağıdaki kodla değiştirin. Daha sonra komutu girerek programı çalıştırın. `dotnet run`

```csharp
Console.WriteLine($"[{DateTime.Now,-20:d}] Hour [{DateTime.Now,-10:HH}] [{1063.342,15:N2}] feet");
```

Çıktı aşağıdaki gibi bir şey görünüyor:

```console
[04/14/2018          ] Hour [16        ] [       1,063.34] feet
```

Dize enterpolasyon eğitimini tamamladınız.

Daha fazla bilgi için C# öğreticisinde [String enterpolasyon](../../language-reference/tokens/interpolated.md) konusuna ve [String enterpolasyonuna](../../tutorials/string-interpolation.md) bakın.
