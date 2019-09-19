---
title: Dize ilişkilendirme- C# öğretici
description: Bu öğreticide, dize ilişkilendirme özelliğinin, C# biçimlendirilen ifade sonuçlarını daha büyük bir dizeye eklemek için nasıl kullanılacağı gösterilmektedir.
author: rpetrusha
ms.author: ronpet
ms.date: 10/23/2018
ms.openlocfilehash: b2bbab5705d78525ccae6a90b4f4f2a91064a06b
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117841"
---
# <a name="use-string-interpolation-to-construct-formatted-strings"></a>Biçimlendirilen dizeler oluşturmak için dize ilişkilendirmeyi kullanın

Bu öğretici, tek bir sonuç dizesine C# değer eklemek için [dize ilişkilendirmeyi](../../language-reference/tokens/interpolated.md) nasıl kullanacağınızı öğretir. Kod yazar C# ve bunları derleyip çalıştırmaya ilişkin sonuçları görürsünüz. Öğretici, bir dizeye değer ekleme ve bu değerleri farklı şekillerde biçimlendirme işlemlerinin nasıl yapılacağını gösteren bir dizi ders içerir.

Bu öğreticide, geliştirme için kullanabileceğiniz bir makineniz olması beklenir. [10 dakika içinde Merhaba Dünya](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) .NET öğreticisi, yerel geliştirme ortamınızı Mac, PC veya Linux üzerinde ayarlamaya yönelik yönergeler içerir. Ayrıca, Bu öğreticinin [etkileşimli sürümünü](interpolated-strings.yml) tarayıcınızda tamamlayabilirsiniz.

## <a name="create-an-interpolated-string"></a>Enterpolasyonlu dize oluşturma

**Enterpolasyonlu**adlı bir dizin oluşturun. Geçerli dizin yapın ve bir konsol penceresinden aşağıdaki komutu çalıştırın:

```dotnetcli
dotnet new console
```

Bu komut geçerli dizinde yeni bir .NET Core konsol uygulaması oluşturur.

En sevdiğiniz düzenleyicide **program.cs** açın ve satırı `Console.WriteLine("Hello World!");` aşağıdaki kodla değiştirin, burada adınızla değiştirin: `<name>`

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```

Konsol pencerenizi yazarak `dotnet run` bu kodu deneyin. Programı çalıştırdığınızda, selamdaki adınızı içeren tek bir dize görüntüler. <xref:System.Console.WriteLine%2A> Yöntem çağrısına dahil edilen dize, bir *enterpolasyonlu dize ifadesidir*. Katıştırılmış kodu içeren bir dizeden tek bir dize ( *sonuç dizesi*olarak adlandırılır) oluşturmanıza imkan tanıyan bir şablon türüdür. Enterpolasyonlu dizeler, bir dizeye değer eklemek veya dizeleri birleştirmek (bir araya birleştirmek) için özellikle faydalıdır.

Bu basit örnek, her bir enterpolasyonlu dizenin sahip olması gereken iki öğeyi içerir:

- Açılış tırnak işareti karakterinden önce `$` karakteriyle başlayan bir dize sabit değeri. `$` Sembol ve tırnak işareti karakteri arasında boşluk olamaz. (Bir tane eklerseniz ne olacağını görmek isterseniz, `$` karakterden sonra bir boşluk ekleyin, dosyayı kaydedin ve konsol penceresine yazarak `dotnet run` programı yeniden çalıştırın. C# Derleyici bir hata iletisi görüntülüyor, "Error CS1056: Beklenmeyen karakter ' $ ' ".)

- Bir veya daha fazla *ilişkilendirme ifadesi*. Enterpolasyon ifadesi bir açma ve kapatma ayracı (`{` ve `}`) ile belirtilir. Küme ayraçları içinde ( C# dahil `null`) bir değer döndüren herhangi bir ifadeyi yerleştirebilirsiniz.

Biraz daha farklı veri türleriyle daha fazla dize ilişkilendirme örneği deneyelim.

## <a name="include-different-data-types"></a>Farklı veri türleri dahil et

Önceki bölümde, bir dizeyi diğerinin içine eklemek için dize ilişkilendirmeyi kullandınız. Enterpolasyon ifadesinin sonucu herhangi bir veri türünde olabilir, ancak. Enterpolasyonlu bir dizedeki çeşitli veri türlerinin değerlerini ekleyelim.

Aşağıdaki örnekte, ilk <xref:System.Object.ToString?displayProperty=nameWithType> olarak `Name` `Vegetable` [bir özelliği](../../properties.md) ve yöntemiolanbirsınıfveritürütanımladık,bu,yönteminindavranışınıgeçersizkılar.`ToString` [](../../programming-guide/classes-and-structs/classes.md) [](../../methods.md) [](../../language-reference/keywords/override.md) [ `public` Erişim değiştiricisi](../../language-reference/keywords/public.md) , bu yöntemi bir örneğin dize gösterimini almak için herhangi bir `Vegetable` istemci kodu için kullanılabilir hale getirir. Örnekte, `Vegetable.ToString` yöntemi [oluşturucuda](../../programming-guide/classes-and-structs/constructors.md)başlatılan `Name` `Vegetable` özelliğin değerini döndürür:

```csharp
public Vegetable(string name) => Name = name;
```

Ardından `Vegetable` `item` `Vegetable` [işlecini kullanarak adlı sınıfının bir örneğini oluşturur ve Oluşturucu için bir ad sağlar: `new` ](../../language-reference/operators/new-operator.md)

```csharp
var item = new Vegetable("eggplant");
```

`item` Son olarak, değişkeni de bir <xref:System.DateTime> değer, <xref:System.Decimal> değer ve bir `Unit` [numaralandırma](../../programming-guide/enumeration-types.md) değeri içeren bir enterpolasyonlu dizeye dahil ediyoruz. Düzenleyicinizdeki tüm C# kodu aşağıdaki kodla değiştirin ve sonra çalıştırmak için `dotnet run` komutunu kullanın:

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

Enterpolasyonlu dizedeki `item` enterpolasyon ifadesinin sonuç dizesinde "eggbitki" metnine çözümlendiğine unutmayın. Yani, ifade sonucunun türü bir dize olmadığında, sonuç aşağıdaki şekilde bir dizeye çözülür:

- Enterpolasyon ifadesi olarak `null`değerlendirilirse, boş bir dize ("" veya <xref:System.String.Empty?displayProperty=nameWithType>) kullanılır.

- İlişkilendirme ifadesi olarak `null`değerlendirilmiyorsa, `ToString` genellikle sonuç türünün yöntemi çağırılır. `Vegetable.ToString` Yöntemi uygulamasını güncelleştirerek bunu test edebilirsiniz. Her tür bu yöntemin bir uygulamasını kullandığından `ToString` yöntemi uygulamanız gerekmez. Bunu test etmek için örnekteki `Vegetable.ToString` yöntemin tanımını (bunu yapmak için, önüne bir açıklama `//`simgesi koyun) yorum yapın. Çıktıda, "eggbitki" dizesinin yerine, <xref:System.Object.ToString?displayProperty=nameWithType> yöntemin varsayılan davranışı olan tam nitelikli tür adı (Bu örnekteki "Vegetable") bulunur. Bir numaralandırma değeri için `ToString` yönteminin varsayılan davranışı değerin dize gösterimini döndürmektir.

Bu örnekteki çıktıda, tarih çok kesin (eggbitki fiyatı her saniye değişmez) ve fiyat değeri bir para birimi göstermez. Sonraki bölümde, ifade sonuçlarının dize temsillerini biçimini denetleyerek bu sorunları nasıl düzelteceğinizi öğreneceksiniz.

## <a name="control-the-formatting-of-interpolation-expressions"></a>Enterpolasyon ifadelerinin biçimlendirmesini denetleme

Önceki bölümde, sonuç dizesine hatalı biçimli iki dize eklenmiştir. Bunlardan biri, yalnızca tarihin uygun olduğu tarih ve saat değeridir. İkincisi, para birimi birimini göstermediğiniz bir fiyattır. Her iki sorunun de kolay bir şekilde ele alınır. Dize ilişkilendirme, belirli türlerin biçimlendirilmesini denetleyen *Biçim dizelerini* belirtmenize olanak tanır. Aşağıdaki satırda gösterildiği gibi `Console.WriteLine` , tarih ve fiyat ifadelerine yönelik biçim dizelerini dahil etmek için önceki örnekteki çağrısını değiştirin:

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```

Bir biçim dizesini, iki nokta üst üste (":") ve biçim dizesiyle birlikte enterpolasyon ifadesini izleyerek belirtirsiniz. "d", kısa tarih biçimini temsil eden [Standart bir tarih ve saat biçim dizesidir](../../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) . "C2", ondalık ayırıcıdan sonraki iki basamakla para birimi değeri olarak bir sayıyı temsil eden [Standart bir sayısal biçim dizesidir](../../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) .

.NET kitaplıklarında bulunan birçok tür, önceden tanımlanmış bir biçim dizeleri kümesini destekler. Bunlar, tüm sayısal türleri ve Tarih ve saat türlerini içerir. Biçim dizelerini destekleyen türlerin tüm listesi için bkz. [.net makalesindeki biçimlendirme türleri](../../../standard/base-types/formatting-types.md) ' nde [Biçim dizeleri ve .NET sınıf kitaplığı türleri](../../../standard/base-types/formatting-types.md#stringRef) .

Metin düzenleyicinizdeki biçim dizelerini değiştirmeyi deneyin ve her değişiklik yaptığınızda, değişikliklerin tarih ve saat ve sayısal değer biçimlendirmesini nasıl etkilediğini görmek için programı yeniden çalıştırın. İçindeki `{date:d}` "d" öğesini "t" olarak değiştirin (kısa saat biçimini göstermek için), "y" (yılı ve ayı göstermek için) ve "yyyy" (yılı dört basamaklı bir sayı olarak göstermek için). İçindeki `{price:C2}` "C2" öğesini "e" (üstel gösterim için) ve "F3" (ondalık ayırıcıdan sonra üç basamaklı bir sayısal değer için) olarak değiştirin.

Biçimlendirmeyi denetlemenin yanı sıra, sonuç dizesinde bulunan biçimlendirilmiş dizelerin alan genişliğini ve hizalamasını da denetleyebilirsiniz. Sonraki bölümde bunu nasıl yapacağınızı öğreneceksiniz.

## <a name="control-the-field-width-and-alignment-of-interpolation-expressions"></a>Enterpolasyon ifadelerinin alan genişliğini ve hizalamasını denetleme

Genellikle, bir enterpolasyon ifadesinin sonucu dize olarak biçimlendirildiğinde, bu dize öndeki veya sondaki boşluklar olmadan bir sonuç dizesine dahil edilir. Özellikle bir veri kümesiyle çalışırken, alan genişliğini denetleyebilmekte ve metin hizalaması daha okunabilir bir çıktı oluşturulmasına yardımcı olur. Bunu görmek için, metin düzenleyicinizdeki tüm kodu aşağıdaki kodla değiştirin ve ardından programı yürütmek için yazın `dotnet run` :

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

`{"Author",-25}` Ve`{title.Key,-25}` kodundan negatif işaretleri kaldırmayı deneyin ve aşağıdaki kod olduğu gibi örneği yeniden çalıştırın:

```csharp
Console.WriteLine($"|{"Author",25}|{"Title",30}|");
foreach (var title in titles)
   Console.WriteLine($"|{title.Key,25}|{title.Value,30}|");
```

Bu kez, yazar bilgileri sağa hizalanır.

Tek bir ilişkilendirme ifadesi için bir hizalama belirleyicisi ve biçim dizesi birleştirebilirsiniz. Bunu yapmak için önce hizalamayı, ardından iki nokta üst üste ve biçim dizesini belirtin. `Main` Yöntemi içindeki tüm kodu, tanımlı alan genişlikleri olan üç biçimli dizeyi görüntüleyen aşağıdaki kodla değiştirin. Ardından, `dotnet run` komutunu girerek programı çalıştırın.

```csharp
Console.WriteLine($"[{DateTime.Now,-20:d}] Hour [{DateTime.Now,-10:HH}] [{1063.342,15:N2}] feet");
```

Çıktı aşağıdakine benzer şekilde görünür:

```console
[04/14/2018          ] Hour [16        ] [       1,063.34] feet
```

Dize ilişkilendirme öğreticisini tamamladınız.

Daha fazla bilgi için bkz. [dize ilişkilendirme](../../language-reference/tokens/interpolated.md) konusu ve öğreticide [dize ilişkilendirme C# ](../../tutorials/string-interpolation.md) .
