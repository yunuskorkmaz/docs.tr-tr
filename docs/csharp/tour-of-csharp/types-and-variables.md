---
title: C# türleri ve değişkenleri-C# dilinin turu
description: "C 'de türleri tanımlama ve değişkenleri bildirme hakkında bilgi edinin #"
ms.date: 04/24/2020
ms.assetid: f8a8051e-0049-43f1-b594-9c84cc7b1224
ms.openlocfilehash: a14291d1eec4d090b0275875326c5a580e5abe9d
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174133"
---
# <a name="types-and-variables"></a>Türler ve değişkenler

C# ' de iki tür tür vardır: *değer türleri* ve *başvuru türleri*. Değer türlerinin değişkenleri doğrudan verilerini içerir, ancak başvuru türündeki değişkenler verilerine başvuruları depolar, ikincisi ise nesneler olarak bilinir. Başvuru türleriyle, iki değişken aynı nesneye başvuruda bulunmak ve bu nedenle bir değişkendeki işlemler diğer değişken tarafından başvurulan nesneyi etkilemek için mümkündür. Değer türleriyle, her birinin kendi verilerinin bir kopyasına sahiptir ve bir üzerindeki işlemler, diğerini etkileme ( `ref` ve `out` parametre değişkenleri hariç) için kullanılamaz.

C# ' nin değer türleri, *basit türlere*, *enum türlerine*, *yapı türlerine*ve *null yapılabilir değer türlerine*daha fazla bölünmüştür. C# ' nin başvuru türleri, *Sınıf türlerine*, *arabirim türlerine*, *dizi türlerine*ve *temsilci türlerine*daha fazla bölünmüştür.

Aşağıdaki ana hat C# tür sistemine genel bir bakış sağlar.

- [Değer türleri][ValueTypes]
  - [Basit türler][SimpleTypes]
    - İmzalanan integral: `sbyte` , `short` , `int` ,`long`
    - İşaretsiz integral: `byte` , `ushort` , `uint` ,`ulong`
    - Unicode karakterler:`char`
    - IEEE ikili kayan nokta: `float` ,`double`
    - Yüksek duyarlıklı ondalık kayan nokta:`decimal`
    - Boolean`bool`
  - [Sabit listesi türleri][EnumTypes]
    - Formun Kullanıcı tanımlı türleri`enum E {...}`
  - [Yapı türleri][StructTypes]
    - Formun Kullanıcı tanımlı türleri`struct S {...}`
  - [Boş değer atanabilen değer türleri][NullableTypes]
    - Bir değere sahip diğer tüm değer türlerinin uzantıları `null`
  - [Demet değer türleri][TupleTypes]
    - Formun Kullanıcı tanımlı türleri`(T1, T2, ...)`
- [Başvuru türleri][ReferenceTypes]
  - [Sınıf türleri][ClassTypes]
    - Diğer tüm türlerin Ultimate temel sınıfı:`object`
    - Unicode dizeleri:`string`
    - Formun Kullanıcı tanımlı türleri`class C {...}`
  - [Arabirim türleri][InterfaceTypes]
    - Formun Kullanıcı tanımlı türleri`interface I {...}`
  - [Dizi türleri][ArrayTypes]
    - Tek ve çok boyutlu, örneğin `int[]` ve`int[,]`
  - [Temsilci türleri][DelegateTypes]
    - Formun Kullanıcı tanımlı türleri`delegate int D(...)`

[ValueTypes]: ../language-reference/builtin-types/value-types.md
[SimpleTypes]: ../language-reference/builtin-types/value-types.md#built-in-value-types
[EnumTypes]: ../language-reference/builtin-types/enum.md
[StructTypes]: ../language-reference/builtin-types/struct.md
[NullableTypes]: ../language-reference/builtin-types/nullable-value-types.md
[TupleTypes]: ../language-reference/builtin-types/value-tuples.md
[ReferenceTypes]: ../language-reference/keywords/reference-types.md
[ClassTypes]: ../language-reference/keywords/class.md
[InterfaceTypes]: ../language-reference/keywords/interface.md
[DelegateTypes]: ../language-reference/keywords/delegate.md
[ArrayTypes]: ../programming-guide/arrays/index.md

Sayısal türler hakkında daha fazla bilgi için bkz. [Integral türleri](../language-reference/builtin-types/integral-numeric-types.md) ve [kayan nokta türleri tablosu](../language-reference/builtin-types/floating-point-numeric-types.md).

C# `bool` türü, Boole değerlerini (veya olan değerler) temsil etmek için kullanılır `true` `false` .

C# ' de karakter ve dize işleme Unicode kodlaması kullanır. `char`Tür BIR UTF-16 kod birimini temsil eder ve `string` tür bir UTF-16 kod birimi dizisini temsil eder.

C# programları yeni türler oluşturmak için *tür bildirimleri* kullanır. Tür bildiriminde yeni türün adı ve üyeleri belirtilir. C# tür kategorilerinin sayısı Kullanıcı tarafından tanımlanabilir: sınıf türleri, yapı türleri, arabirim türleri, sabit listesi türleri ve temsilci türleri.

Bir `class` tür, veri üyeleri (alanlar) ve işlev üyeleri (Yöntemler, Özellikler ve diğerleri) içeren bir veri yapısını tanımlar. Sınıf türleri, tek devralma ve çok biçimlilik destekler, türetilmiş sınıfların temel sınıfları genişletebileceği ve özelleştireceği mekanizmalar.

Bir `struct` tür, veri üyeleri ve işlev üyeleri olan bir yapıyı temsil eden bir sınıf türüne benzerdir. Ancak, sınıfların aksine yapılar değer türlerdir ve genellikle yığın ayırmayı gerektirmez. Yapı türleri Kullanıcı tarafından belirtilen devralmayı desteklemez ve tüm yapı türleri örtülü olarak türünden devralınır `object` .

Bir `interface` tür, bir sözleşmeyi adlandırılmış bir ortak işlev üyeleri kümesi olarak tanımlar. `class`Uygulayan bir veya `struct` `interface` , arabirimin işlev üyelerinin uygulamalarını sağlamalıdır. `interface`, Birden fazla taban arabiriminden devralınabilir ve bir `class` veya `struct` birden çok arabirim uygulayabilir.

Bir `delegate` tür, belirli bir parametre listesi ve dönüş türü olan yöntemlere yapılan başvuruları temsil eder. Temsilciler, yöntemleri değişkenlere atanabilecek ve parametre olarak geçirilen varlıklar olarak işleme olanağı tanır. Temsilciler, işlevsel diller tarafından sunulan işlev türlerine benzerdir. Ayrıca, diğer bazı dillerde bulunan işlev işaretçileri kavramına de benzer. İşlev işaretçilerinden farklı olarak, temsilciler nesne odaklı ve tür açısından güvenlidir.

`class`,, `struct` `interface` Ve `delegate` türleri tüm genel türleri destekler, diğer türlerle parametrelenebilir.

Bir `enum` tür, adlandırılmış sabitleri olan ayrı bir türdür. Her `enum` türün, sekiz integral türünden biri olması gereken temel bir türü vardır. Bir türün değer kümesi, `enum` temel alınan türün değerleri kümesiyle aynıdır.

C#, herhangi bir türdeki tek ve çok boyutlu dizileri destekler. Yukarıda listelenen türlerin aksine, kullanılmadan önce dizi türlerinin bildirilmesini gerekmez. Bunun yerine, dizi türleri Köşeli parantezlerle bir tür adı izleyerek oluşturulur. Örneğin, `int[]` tek boyutlu bir diziyse `int` , iki boyutlu bir dizidir ve tek boyutlu dizi tek boyutlu `int[,]` `int` bir dizidir `int[][]` `int` .

Null yapılabilir değer türlerinin kullanılabilmesi için önce de bildirilmesini gerekmez. Null olamayan her değer türü için, `T` karşılık gelen bir null değer türü vardır ve `T?` Bu, ek bir değer tutabilir `null` . Örneğin, `int?` 32 bitlik herhangi bir tamsayıyı veya değeri tutabilecek bir türdür `null` .

C# tür sistemi, herhangi bir türde bir değer olarak işlenemeyeceği şekilde birleştirilmiştir `object` . C# içindeki her tür doğrudan veya dolaylı olarak `object` sınıf türünden türetilir ve `object` tüm türlerin en son temel sınıfıdır. Başvuru türlerinin değerleri, yalnızca değerleri tür olarak görüntüleyerek nesne olarak değerlendirilir `object` . Değer türlerinin değerleri, *kutulama* ve *kutudan çıkarma işlemleri*gerçekleştirerek nesneler olarak değerlendirilir. Aşağıdaki örnekte, bir değeri öğesine `int` dönüştürülüp `object` öğesine yeniden döndürülür `int` .

[!code-csharp[Boxing](../../../samples/snippets/csharp/tour/types-and-variables/Program.cs#L1-L10)]

Bir başvuru için bir değer türü değeri atandığında `object` , değeri tutmak için bir "Box" tahsis edilir. Bu kutu bir başvuru türünün örneğidir ve değer bu kutuya kopyalanır. Buna karşılık, bir `object` Başvuru bir değer türüne yayınlandığınızda, başvurulan `object` öğesinin doğru değer türünün bir kutusu olduğunu belirten bir denetim yapılır. Denetim başarılı olursa, kutudaki değer değer türüne kopyalanır.

C# ' nin Birleşik tür sistemi etkin bir şekilde değer türlerinin `object` "istek üzerine" başvuru olarak işleneceği anlamına gelir. Birleşme nedeniyle, türü kullanılan genel amaçlı kitaplıklar, `object` `object` başvuru türleri ve değer türleri dahil, öğesinden türetilen tüm türlerle birlikte kullanılabilir.

C# ' de alanlar, dizi öğeleri, yerel değişkenler ve parametreler gibi çeşitli türlerde *değişkenler* vardır. Değişkenler, depolama konumlarını temsil eder ve her değişken, aşağıda gösterildiği gibi, değişkende hangi değerlerin depolanabileceğini belirleyen bir tür içerir.

- Null yapılamayan değer türü
  - Bu tam türden bir değer
- Null yapılabilir değer türü
  - `null`Bu tam türün değeri veya değeri
- nesne
  - `null`Başvuru, herhangi bir başvuru türünün nesnesine başvuru veya herhangi bir değer türünün paketlenmiş değerine başvuru
- Sınıf türü
  - `null`Başvuru, bu sınıf türünün bir örneğine başvuru veya bu sınıf türünden türetilmiş bir sınıfın örneğine başvuru
- Arabirim türü
  - `null`Başvuru, bu arabirim türünü uygulayan bir sınıf türü örneğine başvuru veya bu arabirim türünü uygulayan bir değer türünün paketlenmiş değerine başvuru
- Dizi türü
  - `null`Başvuru, bu dizi türü örneğine başvuru veya uyumlu bir dizi türü örneğine başvuru
- Temsilci türü
  - `null`Uyumlu bir temsilci türü örneğine başvuru veya başvuru

> [!div class="step-by-step"]
> [Önceki](program-structure.md) 
>  [Sonraki](expressions.md)
