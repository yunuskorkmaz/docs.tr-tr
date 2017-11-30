---
title: "C# türleri ve değişkenleri - C# dili turu"
description: "Türlerini tanımlama ve C# değişkenleri bildirme hakkında bilgi edinin"
keywords: ".NET, csharp, türü, türü, değer türü başvurusu"
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: f8a8051e-0049-43f1-b594-9c84cc7b1224
ms.openlocfilehash: 1f1031384520b9ed37246361da8bbc1b42addb0b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="types-and-variables"></a>Türleri ve değişkenler

C# türleri iki tür vardır: *değer türleri* ve *başvuru türleri*. Başvuru türleri değişkenlerinin verilerini başvurularını depolamak ancak değer türleri değişkenlerinin doğrudan verilerini içeren ikinci nesneler olarak bilinen. Başvuru türleri ile aynı nesneye başvurmak iki değişken için olası ve böylece olası bir değişkeni tarafından başvurulan nesne etkilemek için bir değişken üzerinde işlemler için. Değer türleri ile her kendi verilerin kopyasını değişkenleriniz ve bir diğer etkileyen işlemler için mümkün değildir (dışındaki durumunda `ref` ve `out` parametre değişkenleri).

C# ' ın değer türleri içinde daha bölünür *basit türler*, *enum türleri*, *struct türleri*, ve *boş değer atanabilen değer türleri*. C# ' nin başvuru türleri içine daha bölünür *sınıf türleri*, *arabirim türleri*, *dizi türleri*, ve *temsilci türleri*.

C# ' ın tür sistemi genel bir bakış sağlar.

* Değer türleri
    - Basit türler
        * İntegral imzalı: `sbyte`, `short`, `int`,`long`
        * İmzasız integral: `byte`, `ushort`, `uint`,`ulong`
        * Unicode karakter sayısı:`char`
        * IEEE kayan nokta: `float`,`double`
        * Yüksek duyarlıklı ondalık:`decimal`
        * Mantıksal değer:`bool`
    - Numaralandırma türleri
        * Formun kullanıcı tanımlı türler`enum E {...}`
    - Struct türleri
        * Formun kullanıcı tanımlı türler`struct S {...}`
    - boş değer atanabilen değer türleri
        * Diğer tüm değer türlerinde uzantılarını bir `null` değeri
* Başvuru türleri
    - Sınıf türleri
        * Tüm diğer türleri Ultimate temel sınıfını:`object`
        * Unicode dizelerini:`string`
        * Formun kullanıcı tanımlı türler`class C {...}`
    - Arabirim türleri
        * Formun kullanıcı tanımlı türler`interface I {...}`
    - Dizi türleri
        * Tek ve örneğin, çok boyutlu `int[]` ve`int[,]`
    - Temsilci türleri
        * Formun kullanıcı tanımlı türler`delegate int D(...)`

Sekiz tam sayı türleri, 8 bit, 16 bit, 32 bit ve 64-bit işaretli veya işaretsiz formdaki değerler için destek sağlar.

İki kayan nokta türleri `float` ve `double`, 32-bit tek duyarlıklı ve 64-bit çift duyarlıklı IEC 60559 biçimleri, sırasıyla kullanarak temsil edilir.

`decimal` Türüdür finansal ve para hesaplamaları için uygun bir 128-bit veri türü.

C# 's `bool` türü Boole değerleri belirtmek için kullanılan — ya da olan değerleri `true` veya `false`.

Karakter ve C# ' ta işleme dize Unicode kodlama kullanır. `char` Türünü UTF-16 kod birimi temsil eder ve `string` türü UTF-16 kod birimleri dizisini temsil eder.

C# ' ın sayısal türler özetler.

* İmzalı tam sayıdan kaymaya
    - `sbyte`: 8 bit, aralığı -128 127'den
    - `short`: 16 bit, -32.768 32.767 arasındadır
    - `int`: 32 bit, -2.147.483.648 2.147.483.647 arasındadır
    - `long`: 64 bit, 9,223,372,036,854,775,807 ile –9,223,372,036,854,775,808 arasındadır
* İmzasız tam sayıdan kaymaya
    - `byte`: 8 bit aralık 0 - 255
    - `ushort`: 16 bit aralığı 0'dan - 65.535
    - `uint`: 32 bit aralığı 0'dan - 4.294.967.295
    - `ulong`: 64 bit aralığı 0'dan - 18,446,744,073,709,551,615
* Kayan nokta
    - `float`: 32 bit arasında 1.5 × 10'dan<sup>−45</sup> -3.4 × 10<sup>38</sup>, 7 basamaklı duyarlık
    - `double`: 64 bit arasında 5.0 × 10'dan<sup>−324</sup> -1.7 × 10<sup>308</sup>, 15 basamaklı duyarlık
* Ondalık
    - `decimal`: 128 bit, aralığı olan en az –7.9 × 10<sup>−28</sup> -7,9 × 10<sup>28</sup>, en az 28 basamaklı duyarlık ile
    
C# programları kullanım *yazın bildirimleri* yeni türleri oluşturmak için. Tür bildirimi adını ve yeni türün üyeleri belirtir. Beş türleri kategorilerini C# ' ın kullanıcı tanımlanabilir: Sınıf türleri, yapı türleri, arabirim türleri, numaralandırma türleri ve temsilci türleri.

A `class` türü veri üyeleri (alanları) ve işlev üyeleri (yöntemler, özellikler ve diğerleri) içeren bir veri yapısını tanımlar. Sınıf türleri tek devralma ve çok biçimlilik, yapabildiği türetilen sınıflar genişletmek ve temel sınıflar specialize mekanizmalarını destekler.

A `struct` türü benzer bir sınıf türü içeren veri üyeleri ve işlev üyeleri ile bir yapıyı temsil eder. Ancak, farklı sınıflar, yapılar değer türleri ve genellikle yığın ayırma gerektirmez. Struct türleri, kullanıcı tarafından belirtilen devralma desteklemez ve tüm yapı türleri örtük olarak türünden devralan `object`.

Bir `interface` türünü tanımlayan bir sözleşme adlandırılmış kümesi ortak işlevi üyeleri olarak. A `class` veya `struct` uygulayan bir `interface` arabiriminin işlevi üyeleri uygulamalarını belirtmelidir. Bir `interface` birden fazla temel arabirimlerinden devralma ve bir `class` veya `struct` birden çok arabirim uygulayabilir.

A `delegate` türü belirli parametre listesi ve dönüş türü yöntemleriyle başvurular temsil eder. Temsilciler yöntemleri değişkenleri için atanan ve parametre olarak geçirilen varlıklar olarak değerlendirmek mümkün kılar. Temsilciler işlevsel dilleri tarafından sağlanan işlev türleri benzer. Ayrıca diğer bazı dillerde bulunan işlev işaretçileri kavramı benzer, ancak işlev işaretçileri, nesne yönelimli ve tür kullanımı uyumlu temsilciler.

`class`, `struct`, `interface` Ve `delegate` yapabildiği bunlar parametreli diğer türleri ile tüm destek genel türler, türleri.

Bir `enum` türüdür adlandırılmış sabitler ile farklı bir tür. Her `enum` türü sekiz tam sayı türlerinden birini olmalıdır bir temel türe sahip. Değerleri kümesi bir `enum` türüdür temel alınan türü değerleri kümesi ile aynı.

C# tek ve birden çok dimensional diziler herhangi bir türde destekler. Yukarıda listelenen türlerinin aksine, dizi türleri kullanılabilmesi için önce bildirilmesi gerekmez. Bunun yerine, dizi türleri köşeli tür adıyla izleyerek oluşturulur. Örneğin, `int[]` , tek boyutlu bir dizi `int`, `int[,]` iki boyutlu bir dizisidir `int`, ve `int[][]` tek boyutlu dizi, tek boyutlu bir dizi `int`.

Boş değer atanabilen değer türleri de kullanılabilmesi için önce bildirilmesi gerekmez. Her bir null değer türü için `T` karşılık gelen bir boş değer atanabilen değer türü `T?`, hangi ek bir değer tutmak `null`. Örneğin, `int?` herhangi bir 32 bit tamsayı veya değeri tutabilen bir tür `null`.

C# ' ın tür sistemi herhangi bir türde bir değer işlenebilir, birleşik bir `object`. C# her tür doğrudan veya dolaylı olarak türetilen `object` sınıf türü, ve `object` her türlü ultimate temel sınıftır. Başvuru türleri değerleri kabul edilir nesneler olarak değerleri türü olarak yalnızca görüntüleyerek `object`. Değer türleri değerleri kabul edilir nesneler olarak gerçekleştirerek *kutulama* ve *kutudan çıkarma işlemleri*. Aşağıdaki örnekte, bir `int` değeri için dönüştürülür `object` ve yeniden geri `int`.

[!code-csharp[Boxing](../../../samples/snippets/csharp/tour/types-and-variables/Program.cs#L1-L10)]

Ne zaman bir değer türü değeri dönüştürülür yazmak için `object`, bir `object` örneği, bir "kutusu" olarak da bilinir değeri tutmak için ayrılır ve değeri bu kutuya kopyalanır. Buna karşılık, ne zaman bir `object` başvuru değer türüne dönüştürme, bir onay yapılan başvurulan `object` bir kutudur doğru değer türü ve kutudaki değer denetimi başarılı olursa, kopyalanır.

Değer türleri nesnelerde "isteğe bağlı." hale gelebilir C# ' ın birleşik tür sistemi etkili bir şekilde anlamına gelir Birleştirici türünü kullanan genel amaçlı kitaplıkları nedeniyle `object` başvuru türleri ve değer türleri ile kullanılabilir.

Birden fazla tür vardır, *değişkenleri* C# ' ta alanları, dizi öğeleri, yerel değişkenleri ve parametreleri de dahil olmak üzere. Değişkenleri temsil depolama konumları ve her değişken ne değerler olabilir belirleyen bir türe sahip aşağıda gösterildiği gibi değişkende depolanır.

* Olamayan değer türü
    - Bu tam türünde bir değer
* Boş değer atanabilir değer türü
    - A `null` değeri veya tam türü değeri
* nesne
    - A `null` başvurusu, tüm başvuru türünde bir nesneye başvuru veya herhangi bir değer türde paketlenmiş değere başvurusu
* Sınıf türü
    - A `null` başvurusu, bu sınıf türünün bir örneği için bir başvuru veya bu sınıf türden türetilmiş bir sınıf örneği başvurusu
* Arabirim türü
    - A `null` başvurusu, bu arabirim türü uygulayan bir sınıf türünün bir örneği için bir başvuru veya paketlenmiş değere bu arabirim türü uygulayan bir değer türü başvurusu
* Dizi türü
    - A `null` başvurusu, dizi türü bir örneğine başvuru veya uyumlu dizi türünün bir örneği başvurusu
* Temsilci türü
    - A `null` bir başvuru veya uyumlu temsilci türünün bir örneği için

>[!div class="step-by-step"]
[Önceki](program-structure.md)
[sonraki](expressions.md)
