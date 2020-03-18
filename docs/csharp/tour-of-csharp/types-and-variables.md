---
title: C# Türleri ve Değişkenleri - C# dilinin turu
description: "C'de türleri tanımlama ve değişkenleri bildirme hakkında bilgi edinin #"
ms.date: 02/25/2020
ms.assetid: f8a8051e-0049-43f1-b594-9c84cc7b1224
ms.openlocfilehash: b2a5255a243c12543a1cd59b5724b6c826306e04
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159097"
---
# <a name="types-and-variables"></a>Türleri ve değişkenleri

C#'da iki tür tür vardır: *değer türleri* ve *başvuru türleri.* Değer türlerinin değişkenleri doğrudan kendi verilerini içerirken, başvuru türlerinin değişkenleri kendi verilerine referanslar depolar, ikincisi ise nesne olarak bilinir. Başvuru türleri ile, iki değişkenin aynı nesneye başvurması ve böylece bir değişkenüzerindeki işlemlerin diğer değişken tarafından başvurulan nesneyi etkilemesi mümkündür. Değer türleri ile, değişkenlerin her birinin kendi veri kopyası vardır ve bir tanesindeki işlemlerin diğerini etkilemesi mümkün değildir (parametre değişkenleri `ref` hariç). `out`

C#'ın değer türleri *daha basit türleri,* *enum türleri,* *yapı türleri*ve *nullable değer türleri*ayrılır. C#'ın başvuru türleri *sınıf türleri,* *arabirim türleri,* *dizi türleri*ve temsilci türleri olarak daha da *ayrılmıştır.*

Aşağıdaki anahat, C#'ın tür sistemine genel bir bakış sağlar.

- [Değer türleri][ValueTypes]
  - [Basit türler][SimpleTypes]
    - İmzalı `sbyte`integral: , `short`, `int`,`long`
    - İmzasız `byte`integral: `ushort` `uint`, , ,`ulong`
    - Unicode karakterleri:`char`
    - IEEE ikili kayan `float`noktası: ,`double`
    - Yüksek hassasiyetli ondalık kayan nokta:`decimal`
    - Boolean:`bool`
  - [Enum türleri][EnumTypes]
    - Formun kullanıcı tanımlı türleri`enum E {...}`
  - [Yapı türünün][StructTypes]
    - Formun kullanıcı tanımlı türleri`struct S {...}`
  - [Nullable değer türleri][NullableTypes]
    - `null` Değeri olan diğer tüm değer türlerinin uzantıları
- [Başvuru türleri][ReferenceTypes]
  - [Sınıf türleri][ClassTypes]
    - Diğer tüm türlerin nihai taban sınıfı:`object`
    - Unicode dizeleri:`string`
    - Formun kullanıcı tanımlı türleri`class C {...}`
  - [Arayüz türleri][InterfaceTypes]
    - Formun kullanıcı tanımlı türleri`interface I {...}`
  - [Dizi türleri][ArrayTypes]
    - Örneğin tek ve çok boyutlu `int[]` ve`int[,]`
  - [Temsilci türleri][DelegateTypes]
    - Formun kullanıcı tanımlı türleri`delegate int D(...)`

[ValueTypes]: ../language-reference/builtin-types/value-types.md
[SimpleTypes]: ../language-reference/builtin-types/value-types.md#built-in-value-types
[EnumTypes]: ../language-reference/builtin-types/enum.md
[StructTypes]: ../language-reference/builtin-types/struct.md
[NullableTypes]: ../language-reference/builtin-types/nullable-value-types.md
[ReferenceTypes]: ../language-reference/keywords/reference-types.md
[ClassTypes]: ../language-reference/keywords/class.md
[InterfaceTypes]: ../language-reference/keywords/interface.md
[DelegateTypes]: ../language-reference/keywords/delegate.md
[ArrayTypes]: ../programming-guide/arrays/index.md

Sayısal türleri hakkında daha fazla bilgi [için, İntegral türleri](../language-reference/builtin-types/integral-numeric-types.md) ve [Kayan nokta türleri tablosuna](../language-reference/builtin-types/floating-point-numeric-types.md)bakın.

C#'ın `bool` türü Boolean değerlerini temsil etmek için `true` `false`kullanılır.

C#'daki karakter ve dize işleme, Unicode kodlaması kullanır. Tür `char` bir UTF-16 kod birimini `string` temsil eder ve tür UTF-16 kod birimlerinin bir dizi temsil eder.

C# programları yeni türler oluşturmak için *tür bildirimleri* kullanır. Bir tür bildirimi, yeni türün adını ve üyelerini belirtir. C#'ın beş tür kategorisi kullanıcı tarafından tanımlanabilir: sınıf türleri, yapı türleri, arabirim türleri, enum türleri ve temsilci türleri.

Tür, `class` veri üyeleri (alanlar) ve işlev üyeleri (yöntemler, özellikler ve diğerleri) içeren bir veri yapısı tanımlar. Sınıf türleri tek kalıtım ve çok biçimliliği destekler, bu şekilde türemiş sınıfların temel sınıfları genişletebileceği ve özellebildiği mekanizmalar.

Bir `struct` tür, veri üyeleri ve işlev üyeleri ile bir yapı temsil eden bir sınıf türüne benzer. Ancak, sınıfların aksine, structs değer türleri dir ve genellikle yığın ayırma gerektirmez. Yapı türleri kullanıcı tarafından belirtilen devralmayı desteklemez ve tüm yapı türleri `object`örtülü olarak türden devralır.

Bir `interface` tür, sözleşmeyi adlandırılmış bir ortak işlev üyesi kümesi olarak tanımlar. A `class` `struct` veya bir `interface` uygular arabirimin işlev üyelerinin uygulamalarını sağlamalıdır. Bir, `interface` birden çok temel arabirimden devralınabilir ve birden `class` çok arabirim `struct` uygulayabilir.

Bir `delegate` tür, belirli bir parametre listesi ve dönüş türüne sahip yöntemlere yapılan başvuruları temsil eder. Temsilciler, yöntemleri değişkenlere atanabilen ve parametre olarak geçirilebilen varlıklar olarak ele alabilen varlıklar olarak ele alabilmektir. Temsilciler, işlevsel diller tarafından sağlanan işlev türlerine benzerdir. Ayrıca, diğer bazı dillerde bulunan işlev işaretçileri kavramına da benzerler. Işlev işaretçilerinaksine, temsilciler nesne yönelimli ve tür güvenlidir.

Tüm `class` `struct`destek `interface`jeneriklerini, diğer türlerle parametreye getirebilecekleri , ve `delegate` türleri.

Bir `enum` tür, adlandırılmış sabitleri olan farklı bir türdür. Her `enum` tür, sekiz integral türünden biri olmalıdır altta yatan bir türü vardır. Bir `enum` türün değer kümesi, alttaki türün değerleri kümesiyle aynıdır.

C# her türden tek ve çok boyutlu dizileri destekler. Yukarıda listelenen türlerden farklı olarak, dizi türlerinin kullanılmadan önce bildirilmesi gerekmez. Bunun yerine, dizi türleri kare ayraçlı bir tür adı izleyerek oluşturulur. Örneğin, `int[]` tek boyutlu bir dizi `int` `int[,]` , iki boyutlu bir `int`dizi `int[][]` , ve tek boyutlu bir dizi `int`.

Kullanılabilir değer türleri de kullanılabilir önce bildirilmesi gerekir. Her nullable değer türü `T`için, ek bir değer `T?`tutabilir karşılık gelen bir `null`nullable değer türü vardır. Örneğin, `int?` herhangi bir 32-bit tamsayı veya değer `null`tutabilirsiniz bir türüdür.

C#'ın tür sistemi, herhangi bir türdeki bir değerin `object`.' olarak kabul edilebildiği şekilde birleştirilmiştir. C#'daki her tür doğrudan veya dolaylı `object` olarak sınıf `object` türünden türetilmiştir ve her türlü nihai taban sınıfıdır. Başvuru türlerinin değerleri, değerleri yalnızca tür `object`olarak görüntüleyerek nesne olarak kabul edilir. Değer türlerinin *değerleri, kutulama* ve *kutulama işlemleri*gerçekleştirerek nesne olarak kabul edilir. Aşağıdaki örnekte, `int` bir değer 'e `object` dönüştürülür `int`ve tekrar .

[!code-csharp[Boxing](../../../samples/snippets/csharp/tour/types-and-variables/Program.cs#L1-L10)]

Bir değer türünün değeri türe `object`dönüştürüldüğünde, "kutu" olarak da adlandırılan bir `object` örnek, değeri tutmak için ayrılır ve değer bu kutuya kopyalanır. Tersine, bir `object` başvuru bir değer türüne atıldığında, başvurulan `object` değer türünden bir kutu olduğuna ve denetim başarılı olursa, kutudaki değerin kopyalandığından bir denetim yapılır.

C#'ın birleşik tip sistemi, değer türlerinin "isteğe bağlı" nesneler haline gelebileceği anlamına gelir. Birleştirme nedeniyle, türü `object` kullanan genel amaçlı kitaplıklar hem başvuru türleri hem de değer türleri ile kullanılabilir.

C#'da alanlar, dizi öğeleri, yerel *değişkenler* ve parametreler dahil olmak üzere çeşitli değişken türleri vardır. Değişkenler depolama konumlarını temsil eder ve her değişkenin aşağıda gösterildiği gibi değişkende hangi değerlerin depolanabileceğini belirleyen bir türü vardır.

- Nullable değer türü
  - Bu tür bir değer
- Nullable değer türü
  - Bir `null` değer veya bu tür bir değer
- object
  - Bir `null` başvuru, herhangi bir başvuru türünden bir nesneye başvuru veya herhangi bir değer türünün kutulanmış değerine başvuru
- Sınıf türü
  - Bir `null` başvuru, bu sınıf türünden bir örneğe başvuru veya bu sınıf türünden türetilen bir sınıf örneğine başvuru
- Arayüz türü
  - Bir `null` başvuru, bu arabirim türünü uygulayan sınıf türü örneğine başvuru veya bu arabirim türünü uygulayan bir değer türünün kutulanmış değerine başvuru
- Dizi türü
  - Bir `null` başvuru, bu dizi türünden bir örneğe başvuru veya uyumlu bir dizi türü örneğine başvuru
- Temsilci türü
  - Uyumlu `null` bir temsilci türü örneğine başvuru veya başvuru

> [!div class="step-by-step"]
> [Önceki](program-structure.md)
> [Sonraki](expressions.md)
