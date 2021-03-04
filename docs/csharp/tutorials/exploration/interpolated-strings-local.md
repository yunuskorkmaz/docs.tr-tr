---
title: Dize ilişkilendirme-C# öğreticisi
description: Bu öğreticide, biçimlendirilen ifade sonuçlarını daha büyük bir dizeye eklemek için C# dize ilişkilendirme özelliğinin nasıl kullanılacağı gösterilmektedir.
ms.date: 10/23/2018
ms.openlocfilehash: a80f6d6b118a9dfc4e9ada2122dfc374a137fb4e
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102103211"
---
# <a name="use-string-interpolation-to-construct-formatted-strings"></a>Biçimlendirilen dizeler oluşturmak için dize ilişkilendirmeyi kullanın

Bu öğretici, tek bir sonuç dizesine değer eklemek için C# [dize ilişkilendirmeyi](../../language-reference/tokens/interpolated.md) nasıl kullanacağınızı öğretir. C# kodu yazar ve bunu derleyip çalıştırmanın sonuçlarını görürsünüz. Öğretici, bir dizeye değer ekleme ve bu değerleri farklı şekillerde biçimlendirme işlemlerinin nasıl yapılacağını gösteren bir dizi ders içerir.

Bu öğreticide, geliştirme için kullanabileceğiniz bir makineniz olması beklenir. [10 dakika içinde Merhaba Dünya](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) .NET öğreticisi, Windows, Linux veya MacOS 'ta yerel geliştirme ortamınızı ayarlamaya yönelik yönergeler içerir. Bu öğreticinin [etkileşimli sürümünü](interpolated-strings.yml) tarayıcınızda de tamamlayabilirsiniz.

## <a name="create-an-interpolated-string"></a>İlişkilendirilmiş dize oluşturma

*Enterpolasyonlu* adlı bir dizin oluşturun. Geçerli dizin yapın ve bir konsol penceresinden aşağıdaki komutu çalıştırın:

```dotnetcli
dotnet new console
```

Bu komut geçerli dizinde yeni bir .NET Core konsol uygulaması oluşturur.

En sevdiğiniz düzenleyicide *program.cs* açın ve satırı `Console.WriteLine("Hello World!");` aşağıdaki kodla değiştirin, burada `<name>` adınızla değiştirin:

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```

Konsol pencerenizi yazarak bu kodu deneyin `dotnet run` . Programı çalıştırdığınızda program, karşılamada adınızı içeren tek bir dize görüntüler. Yöntem çağrısına dahil edilen dize, <xref:System.Console.WriteLine%2A> bir *enterpolasyonlu dize ifadesidir*. Bu, gömülü kod içeren bir dizeden tek bir dize (*sonuç dizesi* olarak adlandırılır) oluşturmanızı sağlayan bir şablon türüdür. İlişkilendirilmiş dizeler özellikle bir dizeye değer eklerken veya dizeleri birleştirirken kolaylık sağlar.

Şu basit örnek her ilişkilendirilmiş dizenin sahip olması gereken iki öğeyi içerir:

- Açma tırnak işareti karakterinden önce `$` karakteriyle başlayan bir dize sabit değeri. `$` sembolü ile tırnak işareti karakteri arasında boşluk olamaz. (Bir tane eklerseniz ne olacağını görmek isterseniz, karakterden sonra bir boşluk ekleyin `$` , dosyayı kaydedin ve konsol penceresine yazarak programı yeniden çalıştırın `dotnet run` . C# derleyicisi bir hata iletisi görüntülüyor, "Error CS1056: beklenmeyen karakter ' $ '".)

- Bir veya daha fazla *ilişkilendirme ifadesi*. Enterpolasyon ifadesi bir açma ve kapatma ayracı (ve) ile belirtilir `{` `}` . Ayraçlar arasında bir değer (`null` dahil) döndüren herhangi bir C# ifadesini ekleyebilirsiniz.

Biraz daha farklı veri türleriyle daha fazla dize ilişkilendirme örneği deneyelim.

## <a name="include-different-data-types"></a>Farklı veri türleri ekleme

Önceki bölümde, bir dizeyi diğerinin içine eklemek için dize ilişkilendirmeyi kullandınız. Enterpolasyon ifadesinin sonucu herhangi bir veri türünde olabilir, ancak. Enterpolasyonlu bir dizedeki çeşitli veri türlerinin değerlerini ekleyelim.

Aşağıdaki örnekte, ilk olarak bir özelliği ve yöntemi olan bir [sınıf](../../programming-guide/classes-and-structs/classes.md) veri türü tanımladık `Vegetable` `Name` [](../../properties.md) `ToString` [](../../methods.md), bu, yönteminin davranışını [geçersiz kılar](../../language-reference/keywords/override.md) <xref:System.Object.ToString?displayProperty=nameWithType> . [ `public` Erişim değiştiricisi](../../language-reference/keywords/public.md) , bu yöntemi bir örneğin dize gösterimini almak için herhangi bir istemci kodu için kullanılabilir hale getirir `Vegetable` . Örnekte, `Vegetable.ToString` yöntemi `Name` oluşturucuda başlatılan özelliğin değerini döndürür `Vegetable` [](../../programming-guide/classes-and-structs/constructors.md):

```csharp
public Vegetable(string name) => Name = name;
```

Ardından `Vegetable` işlecini kullanarak adlı sınıfının bir örneğini oluşturur `item` ve Oluşturucu için bir [ `new` ](../../language-reference/operators/new-operator.md) ad sağlar `Vegetable` :

```csharp
var item = new Vegetable("eggplant");
```

Son olarak, `item` değişkeni de bir <xref:System.DateTime> değer, <xref:System.Decimal> değer ve bir `Unit` [numaralandırma](../../language-reference/builtin-types/enum.md) değeri içeren bir enterpolasyonlu dizeye dahil ediyoruz. Düzenleyicinizdeki tüm C# kodunu aşağıdaki kodla değiştirin ve sonra `dotnet run` çalıştırmak için komutunu kullanın:

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

`item`Enterpolasyonlu dizedeki enterpolasyon ifadesinin sonuç dizesinde "eggbitki" metnine çözümlendiğine unutmayın. Yani, ifade sonucunun türü bir dize olmadığında, sonuç aşağıdaki şekilde bir dizeye çözülür:

- Enterpolasyon ifadesi olarak değerlendirilirse `null` , boş bir dize ("" veya <xref:System.String.Empty?displayProperty=nameWithType> ) kullanılır.

- İlişkilendirme ifadesi olarak değerlendirilmiyorsa `null` , genellikle `ToString` sonuç türünün yöntemi çağırılır. Yöntemi uygulamasını güncelleştirerek bunu test edebilirsiniz `Vegetable.ToString` . `ToString`Her tür bu yöntemin bir uygulamasını kullandığından yöntemi uygulamanız gerekmez. Bunu test etmek için `Vegetable.ToString` örnekteki yöntemin tanımını (bunu yapmak için, önüne bir açıklama simgesi koyun) yorum yapın `//` . Çıktıda, "eggbitki" dizesinin yerine, yöntemin varsayılan davranışı olan tam nitelikli tür adı (Bu örnekteki "Vegetable") bulunur <xref:System.Object.ToString?displayProperty=nameWithType> . `ToString`Bir numaralandırma değeri için yönteminin varsayılan davranışı değerin dize gösterimini döndürmektir.

Bu örnekteki çıktıda, tarih çok kesin (eggbitki fiyatı her saniye değişmez) ve fiyat değeri bir para birimi göstermez. Sonraki bölümde, ifade sonuçlarının dize temsillerini biçimini denetleyerek bu sorunları nasıl düzelteceğinizi öğreneceksiniz.

## <a name="control-the-formatting-of-interpolation-expressions"></a>Enterpolasyon ifadelerinin biçimlendirmesini denetleme

Önceki bölümde, sonuç dizesine hatalı biçimli iki dize eklenmiştir. Biri tarih ve saat değeriydi, bunlardan yalnızca tarih değeri uygundu. İkincisi, para birimi birimini göstermediğiniz bir fiyattır. Her iki sorun da kolayca giderilebilir. Dize ilişkilendirme, belirli türlerin biçimlendirilmesini denetleyen *Biçim dizelerini* belirtmenize olanak tanır. `Console.WriteLine`Aşağıdaki satırda gösterildiği gibi, tarih ve fiyat ifadelerine yönelik biçim dizelerini dahil etmek için önceki örnekteki çağrısını değiştirin:

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```

Bir biçim dizesini, iki nokta üst üste (":") ve biçim dizesiyle birlikte enterpolasyon ifadesini izleyerek belirtirsiniz. “d”, kısa tarih biçimini ifade eden [standart tarih ve saat biçimi dizesidir](../../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier). “C2”, ondalık ayırıcıdan sonra gelen iki basamakla para birimi değeri olarak bir sayıyı ifade eden [standart sayısal biçim dizesidir](../../../standard/base-types/standard-numeric-format-strings.md#currency-format-specifier-c).

.NET kitaplıklarında bulunan birçok tür, önceden tanımlanmış bir biçim dizeleri kümesini destekler. Bunlara tüm sayısal türlerin yanı sıra tarih ve saat türleri de dahildir. Biçim dizelerini destekleyen türlerin tam listesi için [.NET’teki Biçimlendirme Türleri](../../../standard/base-types/formatting-types.md) başlıklı makalede bulunan [Biçim Dizeleri ve .NET Sınıfı Kitaplık Türleri](../../../standard/base-types/formatting-types.md#format-strings-and-net-types) bölümüne bakın.

Metin düzenleyicinizdeki biçim dizelerini değiştirmeyi deneyin ve her değişiklik yaptığınızda, değişikliklerin tarih ve saat ve sayısal değer biçimlendirmesini nasıl etkilediğini görmek için programı yeniden çalıştırın. `{date:d}` içindeki “d”yi “t” olarak (kısa saat biçimini görüntülemek için), “y” olarak (yılı ve ayı görüntülemek için) ve “yyyy” olarak (yılı dört basamaklı sayı olarak görüntülemek için) değiştirin. `{price:C2}` içindeki “C2”yi “e” olarak (üstel gösterim için) ve “F3” olarak (ondalık ayırıcıdan sonra üç basamak içeren sayısal bir değer için) değiştirin.

Biçimlendirmeyi denetlemenin yanı sıra, sonuç dizesinde bulunan biçimlendirilmiş dizelerin alan genişliğini ve hizalamasını da denetleyebilirsiniz. Sonraki bölümde bunu nasıl yapacağınızı öğreneceksiniz.

## <a name="control-the-field-width-and-alignment-of-interpolation-expressions"></a>Enterpolasyon ifadelerinin alan genişliğini ve hizalamasını denetleme

Genellikle, bir enterpolasyon ifadesinin sonucu dize olarak biçimlendirildiğinde, bu dize öndeki veya sondaki boşluklar olmadan bir sonuç dizesine dahil edilir. Özellikle bir veri kümesiyle çalışırken, alan genişliğini denetleyebilmekte ve metin hizalaması daha okunabilir bir çıktı oluşturulmasına yardımcı olur. Bunu görmek için, metin düzenleyicinizdeki tüm kodu aşağıdaki kodla değiştirin ve ardından `dotnet run` programı yürütmek için yazın:

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

Yazarların adları sola hizalanır ve yazdığı başlıklar sağa hizalanır. Bir ilişkilendirme ifadesinden sonra bir virgül (",") ekleyerek ve *en az* alan genişliğini belirterek hizalamayı belirlersiniz. Belirtilen değer pozitif bir sayıysa, alan sağa hizalanır. Negatif bir sayı ise, alan sola hizalanır.

Ve kodundan negatif işaretleri kaldırmayı deneyin `{"Author",-25}` `{title.Key,-25}` ve aşağıdaki kod olduğu gibi örneği yeniden çalıştırın:

```csharp
Console.WriteLine($"|{"Author",25}|{"Title",30}|");
foreach (var title in titles)
   Console.WriteLine($"|{title.Key,25}|{title.Value,30}|");
```

Bu kez, yazar bilgileri sağa hizalanır.

Tek bir ilişkilendirme ifadesi için bir hizalama belirleyicisi ve biçim dizesi birleştirebilirsiniz. Bunu yapmak için önce hizalamayı, ardından iki nokta üst üste ve biçim dizesini belirtin. Yöntemi içindeki tüm kodu, `Main` tanımlı alan genişlikleri olan üç biçimli dizeyi görüntüleyen aşağıdaki kodla değiştirin. Ardından, komutunu girerek programı çalıştırın `dotnet run` .

```csharp
Console.WriteLine($"[{DateTime.Now,-20:d}] Hour [{DateTime.Now,-10:HH}] [{1063.342,15:N2}] feet");
```

Çıktı aşağıdakine benzer şekilde görünür:

```console
[04/14/2018          ] Hour [16        ] [       1,063.34] feet
```

Dize ilişkilendirme öğreticisini tamamladınız.

Daha fazla bilgi için bkz. [dize ilişkilendirme](../../language-reference/tokens/interpolated.md) konusu ve C# öğreticisinde [dize ilişkilendirme](../string-interpolation.md) .
