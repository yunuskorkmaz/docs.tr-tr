---
title: C#Türler ve değişkenler- C# dilin turu
description: İçinde türleri tanımlama ve değişkenleri bildirme hakkında bilgi edininC#
ms.date: 08/10/2016
ms.assetid: f8a8051e-0049-43f1-b594-9c84cc7b1224
ms.openlocfilehash: 863f37714da06ca55c8c9092f06c445995d47ce3
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739153"
---
# <a name="types-and-variables"></a>Türler ve değişkenler

' De C#iki tür tür vardır: *değer türleri* ve *başvuru türleri*. Değer türlerinin değişkenleri doğrudan verilerini içerir, ancak başvuru türündeki değişkenler verilerine başvuruları depolar, ikincisi ise nesneler olarak bilinir. Başvuru türleriyle, iki değişkenin aynı nesneye başvurması ve bu nedenle bir değişkende işlemler için diğer değişken tarafından başvurulan nesneyi etkilemesi mümkündür. Değer türleriyle, her birinin kendi verilerinin bir kopyasına sahip olduğu ve bir üzerindeki işlemler (`ref` ve `out` parametre değişkenlerinin olması dışında) üzerinde işlemler için mümkün değildir.

C#öğesinin değer türleri, *basit türler*, *sabit listesi türleri*, *yapı türleri*ve *null yapılabilir değer türlerine*daha da bölünür. C#öğesinin başvuru türleri, *Sınıf türlerine*, *arabirim türlerine*, *dizi türlerine*ve *temsilci türlerine*daha da ayrılır.

Aşağıdakiler, tür sistemine genel bir C#bakış sağlar.

- [Değer türleri][ValueTypes]
  - [Basit türler][SimpleTypes]
    - İmzalanan integral: `sbyte`, `short`, `int`, `long`
    - İşaretsiz integral: `byte`, `ushort`, `uint`, `ulong`
    - Unicode karakterler: `char`
    - IEEE ikili kayan nokta: `float`, `double`
    - Yüksek duyarlıklı ondalık kayan nokta: `decimal`
    - Boolean: `bool`
  - [Sabit listesi türleri][EnumTypes]
    - Formun Kullanıcı tanımlı türleri `enum E {...}`
  - [Yapı türleri][StructTypes]
    - Formun Kullanıcı tanımlı türleri `struct S {...}`
  - [Null yapılabilir değer türleri][NullableTypes]
    - `null` bir değere sahip diğer tüm değer türlerinin uzantıları
- [Başvuru türleri][ReferenceTypes]
  - [Sınıf türleri][ClassTypes]
    - Diğer tüm türlerin Ultimate temel sınıfı: `object`
    - Unicode dizeleri: `string`
    - Formun Kullanıcı tanımlı türleri `class C {...}`
  - [Arabirim türleri][InterfaceTypes]
    - Formun Kullanıcı tanımlı türleri `interface I {...}`
  - [Dizi türleri][ArrayTypes]
    - Tek ve çok boyutlu, örneğin `int[]` ve `int[,]`
  - [Temsilci türleri][DelegateTypes]
    - Formun Kullanıcı tanımlı türleri `delegate int D(...)`

[ValueTypes]: ../language-reference/keywords/value-types-table.md
[SimpleTypes]: ../language-reference/keywords/value-types.md#simple-types
[EnumTypes]: ../language-reference/keywords/enum.md
[StructTypes]: ../language-reference/keywords/struct.md
[NullableTypes]: ../language-reference/builtin-types/nullable-value-types.md
[ReferenceTypes]: ../language-reference/keywords/reference-types.md
[ClassTypes]: ../language-reference/keywords/class.md
[InterfaceTypes]: ../language-reference/keywords/interface.md
[DelegateTypes]: ../language-reference/keywords/delegate.md
[ArrayTypes]: ../programming-guide/arrays/index.md

Sayısal türler hakkında daha fazla bilgi için bkz. [Integral türleri](../language-reference/builtin-types/integral-numeric-types.md) ve [kayan nokta türleri tablosu](../language-reference/builtin-types/floating-point-numeric-types.md).

C#`bool` türü, Boole değerlerini (`true` ya da `false`olan değerler) temsil etmek için kullanılır.

İçindeki C# karakter ve dize işleme Unicode kodlaması kullanır. `char` türü bir UTF-16 kod birimini temsil eder ve `string` türü bir UTF-16 kod birimi dizisini temsil eder.

C#programlar yeni türler oluşturmak için *tür bildirimleri* kullanır. Tür bildiriminde yeni türün adı ve üyeleri belirtilir. C#Türlerin beş kategorisi Kullanıcı tarafından tanımlanabilir: sınıf türleri, yapı türleri, arabirim türleri, sabit listesi türleri ve temsilci türleri.

`class` türü, veri üyeleri (alanlar) ve işlev üyeleri (Yöntemler, Özellikler ve diğerleri) içeren bir veri yapısını tanımlar. Sınıf türleri, tek devralma ve çok biçimlilik destekler, türetilmiş sınıfların temel sınıfları genişletebileceği ve özelleştireceği mekanizmalar.

`struct` türü, veri üyeleri ve işlev üyeleri olan bir yapıyı temsil eden bir sınıf türüne benzerdir. Ancak, sınıfların aksine yapılar değer türlerdir ve genellikle yığın ayırmayı gerektirmez. Yapı türleri Kullanıcı tarafından belirtilen devralmayı desteklemez ve `object`türünden dolaylı olarak devralınan tüm yapı türleri.

`interface` türü, bir sözleşmeyi adlandırılmış bir ortak işlev üyeleri kümesi olarak tanımlar. `interface` uygulayan bir `class` veya `struct`, arabirimin işlev üyelerinin uygulamalarını sağlamalıdır. `interface` birden çok temel arabirimden devralınabilir ve bir `class` veya `struct` birden çok arabirim uygulayabilir.

`delegate` türü, belirli bir parametre listesi ve dönüş türü olan yöntemlere yapılan başvuruları temsil eder. Temsilciler, yöntemleri değişkenlere atanabilecek ve parametre olarak geçirilen varlıklar olarak işleme olanağı tanır. Temsilciler, işlevsel diller tarafından sunulan işlev türlerine benzerdir. Bunlar aynı zamanda diğer bazı dillerde bulunan işlev işaretçileri kavramıyla benzerdir, ancak işlev işaretçilerinden farklı olarak Temsilciler nesne yönelimli ve tür açısından güvenlidir.

`class`, `struct`, `interface` ve `delegate` türleri tüm genel türler destekler ve diğer türlerle parametrelenebilir.

`enum` türü, adlandırılmış sabitleri olan ayrı bir türdür. Her `enum` türü, sekiz integral türünden biri olması gereken temel bir tür içerir. `enum` bir türün değer kümesi, temel alınan türün değerleri kümesiyle aynıdır.

C#herhangi bir türdeki tek ve çok boyutlu dizileri destekler. Yukarıda listelenen türlerin aksine,, kullanılmadan önce dizi türlerinin bildirilmesini gerektirmez. Bunun yerine, dizi türleri Köşeli parantezlerle bir tür adı izleyerek oluşturulur. Örneğin, `int[]` tek boyutlu bir `int`dizisidir, `int[,]` iki boyutlu bir `int`dizisidir ve `int[][]` tek boyutlu bir dizi `int`tek boyutlu dizisidir.

Null yapılabilir değer türlerinin kullanılabilmesi için önce de bildirilmesini gerekmez. Her null yapılamayan değer türü için `T`, `null`ek bir değer içerebilen karşılık gelen null yapılabilir bir değer türü `T?`vardır. Örneğin `int?`, 32 bitlik herhangi bir tamsayıyı veya `null`değer içerebilen bir türdür.

C#tür sistemi, herhangi türden bir değer `object`olarak işlenemeyeceği şekilde birleştirilmiştir. Her tür doğrudan C# veya dolaylı olarak `object` sınıf türünden türetilir ve `object` tüm türlerin en son temel sınıfıdır. Başvuru türlerinin değerleri, `object`türü olarak değerleri görüntüleyerek nesne olarak değerlendirilir. Değer türlerinin değerleri, *kutulama* ve *kutudan çıkarma işlemleri*gerçekleştirerek nesneler olarak değerlendirilir. Aşağıdaki örnekte, bir `int` değeri `object` dönüştürülür ve `int`' ye yeniden geri döndürülür.

[!code-csharp[Boxing](../../../samples/snippets/csharp/tour/types-and-variables/Program.cs#L1-L10)]

Değer türünün bir değeri `object`türüne dönüştürüldüğünde, "Box" olarak da bilinen bir `object` örneği değeri tutacak şekilde ayrılır ve değer bu kutuya kopyalanır. Buna karşılık, bir `object` başvurusu bir değer türüne yayınlanırsa, başvurulan `object` doğru değer türünün bir kutusu olduğunu ve denetim başarılı olursa, kutudaki değer kopyalanır.

C#öğesinin Birleşik tür sistemi etkin bir şekilde değer türlerinin "isteğe bağlı" nesneler olabileceği anlamına gelir. Birleşme nedeniyle `object` türü kullanan genel amaçlı kitaplıklar, hem başvuru türleri hem de değer türleriyle kullanılabilir.

İçinde C#alanlar, dizi öğeleri, yerel değişkenler ve parametreler dahil olmak üzere birkaç tür *değişken* vardır. Değişkenler, depolama konumlarını temsil eder ve her değişken, aşağıda gösterildiği gibi, değişkende hangi değerlerin depolanabileceğini belirleyen bir tür içerir.

- Null yapılamayan değer türü
  - Bu tam türden bir değer
- Null yapılabilir değer türü
  - Bir `null` değeri veya bu tam türde bir değer
- nesne
  - `null` başvurusu, herhangi bir başvuru türünün nesnesine başvuru veya herhangi bir değer türünün paketlenmiş değerine başvuru
- Sınıf türü
  - `null` başvurusu, bu sınıf türünün bir örneğine başvuru veya bu sınıf türünden türetilmiş bir sınıfın örneğine başvuru
- Arabirim türü
  - `null` başvurusu, bu arabirim türünü uygulayan bir sınıf türü örneğine başvuru veya bu arabirim türünü uygulayan bir değer türünün paketlenmiş değerine başvuru
- Dizi türü
  - `null` başvurusu, bu dizi türünün bir örneğine başvuru veya uyumlu bir dizi türü örneğine başvuru
- Temsilci türü
  - `null` başvurusu veya uyumlu bir temsilci türü örneğine başvuru

> [!div class="step-by-step"]
> [Önceki](program-structure.md)
> [İleri](expressions.md)
