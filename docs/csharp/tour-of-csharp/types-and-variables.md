---
title: C#Türler ve değişkenler - Turu C# dil
description: Türleri tanımlama ve değişkenleri bildirme hakkında bilgi edininC#
ms.date: 08/10/2016
ms.assetid: f8a8051e-0049-43f1-b594-9c84cc7b1224
ms.openlocfilehash: 5159d75c601bbcb8248a11993a4aaf39299734f0
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57846616"
---
# <a name="types-and-variables"></a>Türler ve değişkenler

C# türlerinde iki tür vardır: *değer türleri* ve *başvuru türleri*. Başvuru türlerinin değişkenleri başvuruları kendi verilerine depolamak ise, değer türlerinin değişkenleri kendi verilerini doğrudan içerir, ikincisi nesneler olarak bilinen. Başvuru türleri ile bu iki değişken aynı nesneye başvurmak mümkün ve dolayısıyla işlemler diğer değişkenin başvurduğu nesneyi etkileyebilir bir değişken üzerinde mümkün olur. Değer türleri ile her değişkenleri kendi veri kopyasını sahip ve işlemlerin bir diğerini etkilemesi olanaklı değildir (dışındaki durumunda `ref` ve `out` parametresi değişkenleri).

C#ın değer türleri içinde daha bölünür *basit türler*, *Numaralandırma türleri*, *yapı türleri*, ve *boş değer atanabilen değer türleri*. C#ın başvuru türleri olarak daha bölünür *sınıf türleri*, *arabirim türleri*, *dizisi, türlerini*, ve *temsilci türleri*.

Genel bir bakış verilmiştir C#'s tür sistemi.

* Değer türleri
    - Basit türler
        * İmzalı tam sayı: `sbyte`, `short`, `int`, `long`
        * İşaretsiz integral: `byte`, `ushort`, `uint`, `ulong`
        * Unicode karakter sayısı: `char`
        * IEEE kayan nokta: `float`, `double`
        * Yüksek duyarlıklı ondalık: `decimal`
        * Boole: `bool`
    - Numaralandırma türleri
        * Formun kullanıcı tanımlı türler `enum E {...}`
    - Yapı türleri
        * Formun kullanıcı tanımlı türler `struct S {...}`
    - Boş değer atanabilen değer türleri
        * Diğer tüm değer türleri ile uzantıları bir `null` değeri
* Başvuru türleri
    - Sınıf türleri
        * Diğer tüm türlerin Ultimate temel sınıf: `object`
        * Unicode dizelerini: `string`
        * Formun kullanıcı tanımlı türler `class C {...}`
    - Arabirim türleri
        * Formun kullanıcı tanımlı türler `interface I {...}`
    - Dizi türleri
        * Tek ve örneğin, çok boyutlu `int[]` ve `int[,]`
    - Temsilci türleri
        * Formun kullanıcı tanımlı türler `delegate int D(...)`

Sekiz integral türleri, 8-bit, 16-bit, 32-bit ve 64-bit işaretli veya işaretsiz form değerleri için destek sağlar.

İki kayan nokta türleri `float` ve `double`, 32-bit tek duyarlıklı ve 64-bit çift duyarlıklı IEC 60559 biçimleri, sırasıyla kullanılarak temsil edilir.

`decimal` Türüdür finansal ve parasal hesaplamalar için uygun bir 128-bit veri türü.

C#ın `bool` türü Boolean değerlerini temsil edecek şekilde kullanılır — ya da değerler `true` veya `false`.

Karakter ve dize işleme C# dilinde Unicode kodlaması kullanır. `char` Türünü bir UTF-16 kod birimini temsil eder ve `string` türü UTF-16 kod birimlerini dizisini temsil eder.

Bu özetler C#ait sayısal türler.

* İmzalı tam sayı
    - `sbyte`:  8 bit, -128 ile 127 arasındadır
    - `short`: 16 bit ile 32.767 -32.768 arasındadır
    - `int`  : 32 bit, aralık 2,147,483,648 ila 2,147,483,647
    - `long` : 64 bit,-9,223,372,036,854,775,808 9.223.372.036.854.775.807 ile arasındadır
* İşaretsiz tamsayı
    - `byte`   :  8 bit, 0 ile 255 arasında
    - `ushort` : 16 bit, 0 ile 65.535 arasında
    - `uint`   : 32 bit ve aralığı 0'dan 4.294.967.295'e kadar
    - `ulong`  : 64 bit, aralığı 0-18,446,744,073,709,551,615
* Kayan nokta
    - `float`  : 32 bit aralığı 1.5 × 10'dan<sup>-45</sup> 3.4 × 10<sup>38</sup>, 7 basamaklı duyarlık
    - `double` : 64 bit aralığı 5.0 × 10'dan<sup>-324</sup> 1.7 × 10<sup>308</sup>, 15 basamaklı duyarlık
* Ondalık
    - `decimal` : 128 bit aralığı olan en az-7.9 × 10<sup>-28</sup> 7,9 × 10<sup>28</sup>, en az 28 basamaklı duyarlık ile

C# programları kullanım *tür bildirimleri* yeni türler oluşturmak için. Bir tür bildirimi, adı ve yeni türün üyeleri belirtir. Beş C#'s türleri kategorilerini kullanıcı tanımlanabilir: Sınıf türleri, yapı türleri, arabirim türleri, sabit listesi türleri ve temsilci türleri.

A `class` veri üyelerine (alanları) ve işlev üyeleri (yöntemler, özellikler ve diğerleri) içeren bir veri yapısı türü tanımlar. Sınıf türleri tek devralma ve çok biçimlilik, yapabildiği türetilmiş sınıfları genişletmek ve temel sınıflar specialize mekanizmaları destekler.

A `struct` temsil ettiği bir yapıya veri üyeleri ve işlev üyeleri içeren türü sınıf türüne benzerdir. Ancak, farklı sınıflar, yapılar değer türleri ve genellikle yığın ayırma gerektirmez. Yapı türleri, kullanıcı tarafından belirtilen devralma desteklemez ve tüm yapı türleri örtülü olarak tür devralmasına `object`.

Bir `interface` türü genel işlev üyeleri adlandırılmış bir dizi bir sözleşmeyi tanımlar. A `class` veya `struct` uygulayan bir `interface` arabirimin işlev üyeleri uygulamaları sağlamanız gerekir. Bir `interface` birden fazla temel Ara birimden devralabilir ve bir `class` veya `struct` birden fazla arabirim uygulayabilir.

A `delegate` türü belirli bir parametre listesi ve dönüş türü olan yöntemlere başvuruları temsil eder. Temsilciler, yöntemleri değişkenine atanır ve parametre olarak geçirilen varlıklar olarak değerlendirmek mümkün kılar. Temsilciler, işlevsel dillerde tarafından sağlanan işlev türlerine benzer. Ayrıca diğer dillerde bulunan işlev işaretçileri kavramına benzer ancak işlev işaretçileri, nesne yönelimli ve tür kullanımı uyumlu temsilciler.

`class`, `struct`, `interface` Ve `delegate` yapabildiği bunlar parametreli diğer türlerle tüm destek genel türler, türleri.

Bir `enum` adlandırılmış sabitler ile farklı bir tür türüdür. Her `enum` türünde sekiz integral türlerinden biri olması gereken bir temel türü. Değerleri kümesi bir `enum` türü, temel alınan tür değerleri kümesi ile aynı.

C# tek ve çoklu dimensional dizilerini herhangi bir türde destekler. Yukarıda listelenen türlerinin aksine, dizi türleri kullanılabilmesi için önce bildirilmiş gerekmez. Bunun yerine, dizi türleri bir tür adı köşeli ayraç içine uygulayarak oluşturulur. Örneğin, `int[]` , tek boyutlu bir dizidir `int`, `int[,]` iki boyutlu bir dizidir `int`, ve `int[][]` tek boyutlu dizi tek boyutlu bir dizidir `int`.

Boş değer atanabilen değer türleri de kullanılabilmesi için önce bildirilmiş gerekmez. Her değer atanamayan değer türü `T` karşılık gelen null yapılabilir değer türü olduğundan `T?`, ek bir değeri tutabilir `null`. Örneğin, `int?` herhangi bir 32 bit tamsayı veya değeri bir arada tutan bir türdür `null`.

C#kullanıcının herhangi bir türde bir değer işlenebilir şekilde tür sistemi birleşik bir `object`. C# ' de her tür doğrudan veya dolaylı olarak türetir `object` sınıf türü, ve `object` tüm türlerin ultimate temel sınıftır. Başvuru türlerindeki değerleri nesneler olarak değer türü olarak yalnızca görüntüleyerek edilir `object`. Değer türlerinin değerleri nesneler olarak gerçekleştirerek edilir *kutulama* ve *kutudan çıkarma işlemlerini*. Aşağıdaki örnekte, bir `int` değerinin `object` ve yeniden geri `int`.

[!code-csharp[Boxing](../../../samples/snippets/csharp/tour/types-and-variables/Program.cs#L1-L10)]

Ne zaman bir değer türünün bir değer türüne dönüştürülür `object`e `object` değerini tutacak bir "kutusu" olarak da adlandırılan örneği ayrılır ve değer kutuya kopyalanır. Buna karşılık, bir `object` başvuru, bir değer türü için atandığında, bir onay yapılır başvurulan `object` doğru değer türünün bir kutu ve kutudaki değer denetimi başarılı olursa kopyalanır.

C#tür birleşik sistem etkili bir şekilde anlamına gelir değer türleri nesneleri "isteğe bağlı." olabilir Birleştirme türü kullanan genel amaçlı kitaplıkları nedeniyle `object` başvuru türleri ve değer türleri ile kullanılabilir.

Birkaç türü vardır, *değişkenleri* C# ' ta alanlar, dizi öğeleri, yerel değişkenleri ve parametreleri dahil. Değişkenleri temsil eden, depolama konumları ve her değişken değerlerin neler olması belirleyen bir türe sahip aşağıda gösterildiği gibi bir değişkende depolanır.

* NULL olmayan değer türü
    - Bu kesin türde bir değer
* Null değer türü
    - A `null` değeri ya da bu kesin türde bir değer
* nesne
    - A `null` başvuru, bir nesneye bir başvuru türünün bir başvuru veya herhangi bir değer türünün kutulanmış bir değer başvurusu
* Sınıf türü
    - A `null` başvuru, bu sınıf türünün bir örneğine başvuru veya bu sınıf türünden türetilmiş bir sınıfın bir örneğine başvuru
* Arabirim türü
    - A `null` başvuru, bu arabirim türünü uygulayıp bir sınıf türünün bir örneğine başvuru veya paketlenmiş değere bu arabirim türünü uygulayıp bir değer türü başvurusu
* Dizi türü
    - A `null` başvuru, dizi türü bir örneğe bir başvuru veya uyumlu dizi türünde bir örneğe bir başvuru
* Temsilci türü
    - A `null` başvurusu veya bir örneğini uyumlu temsilci türü başvurusu

> [!div class="step-by-step"]
> [Önceki](program-structure.md)
> [İleri](expressions.md)
