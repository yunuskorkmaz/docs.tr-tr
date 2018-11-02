---
title: F# Türleri
description: Kullanılan türleri hakkında bilgi edinin F# ve nasıl F# türleri adlı ve açıklanmıştır.
ms.date: 05/16/2016
ms.openlocfilehash: bdbb89dc751970ac31fe102df009f0bff6388e52
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "33565595"
---
# <a name="f-types"></a>F# Türleri

Bu konuda kullanılan türleri açıklayan F# ve nasıl F# türleri adlı ve açıklanmıştır.


## <a name="summary-of-f-types"></a>Özeti F# türleri
Bazı türler olarak kabul edilir *ilkel türler*, Boole türü gibi `bool` ve bayt ve karakter türleri dahil çeşitli boyutlardaki integral ve kayan nokta türleri. Bu tür açıklanan [ilkel türler](primitive-types.md).

Dilinde yerleşik diğer türleri, diziler, listeler, diziler, dizileri, kayıtları içerir ve ayrılmış birleşimler. Diğer .NET dilleri ile deneyime sahiptir ve öğrenme F#, bu türlerinin her biri için konuları okumalısınız. Bu türleri hakkında daha fazla bilgi için bağlantılar dahil edilecek [ilgili konular](https://msdn.microsoft.com/library/#rel) bu konudaki. Bunlar F#-belirli türlerini destekleyen işlevsel programlama dillerinde ortak olan programlama stili. Bu tür birçok modüllerde ilişkilendirdiğiniz F# bu türlerinde ortak işlemleri destekleyen kitaplığı.

Bir işlev türü parametre türleri hakkında bilgi içerir ve dönüş türü.

.NET Framework nesne türlerini, arabirim türlerinde, temsilci türleri ve diğer kaynağıdır. Diğer bir .NET dilinde gibi kendi nesne türlerini tanımlayabilirsiniz.

Ayrıca, F# kod adlandırıldığı gibi diğer ad tanımlayabilirsiniz *tür kısaltmaları*, diğer adlar türleri için olan. Tür kısaltmaları türü gelecekte değişebilir ve türüne bağlıdır kodu değiştirmekten kaçının istediğinizde kullanabilirsiniz. Veya, bir türü kısaltması kod okumanız ve anlamanız daha kolay hale getirmek bir tür için bir kolay ad olarak kullanabilirsiniz.

F#işlevsel programlama aklınızda tasarlanmış yararlı koleksiyon türleri sağlar. Bu koleksiyon türleri kullanarak stilinde daha işlevsel kod yazmanıza yardımcı olur. Daha fazla bilgi için [ F# koleksiyon türleri](fsharp-collection-types.md).


## <a name="syntax-for-types"></a>Türleri için söz dizimi
İçinde F# kod, genellikle zorunda türlerinin adlarını yazın. Formu sözdizimsel her türünde ve bu tür ek açıklamaları, soyut yöntem bildirimleri, temsilci bildirimleri, imzalar ve diğer yapıları söz dizimsel formlarında kullanın. Yorumlayıcısı içinde yeni bir program yapısı bildirmek her yorumlayıcı türü için yapısı ve söz dizimi adı yazdırır. Bu sözdizimi yalnızca kullanıcı tanımlı bir tür için bir tanımlayıcı ya da bir yerleşik tanımlayıcı olarak böyle olabilir `int` veya `string`, ancak daha karmaşık türler için söz dizimi daha karmaşıktır.

Aşağıdaki tablo türü sözdizimi yönlerini gösterir F# türleri.



|Tür|Tür söz dizimi|Örnekler|
|----|-----------|--------|
|temel tür|*tür adı*|`int`<br /><br />`float`<br /><br />`string`|
|toplama türünü (sınıf, yapı, birleşim, kayıt, sabit listesi ve benzeri)|*tür adı*|`System.DateTime`<br /><br />`Color`|
|türü kısaltması|*tür kısaltması adı*|`bigint`|
|tam olarak nitelenmiş tür|*namespaces.Type adı*<br /><br />veya<br /><br />*Modules.Type adı*<br /><br />veya<br /><br />*namespaces.Modules.Type adı*|`System.IO.StreamWriter`|
|dizi|*tür adı*[] veya<br /><br />*tür adı* dizi|`int[]`<br /><br />`array<int>`<br /><br />`int array`|
|iki boyutlu dizi|*tür adı*[,]|`int[,]`<br /><br />`float[,]`|
|üç boyutlu dizi|*tür adı*[,]|`float[,,]`|
|Tanımlama grubu|*tür name1* &#42; *türü name2* ...|Örneğin, `(1,'b',3)` türüne sahip `int * char * int`|
|genel tür|*tür-parametresi* *genel tür adı*<br /><br />veya<br /><br />*genel tür adı*&lt;*tür parametresi listesi*&gt;|`'a list`<br /><br />`list<'a>`<br /><br />`Dictionary<'key, 'value>`|
|oluşturulan türü (sağlanan belirli tür bağımsız değişkeni olan genel bir tür)|*tür bağımsız değişkeni* *genel tür adı*<br /><br />veya<br /><br />*genel tür adı*&lt;*türü bağımsız değişken listesi*&gt;|`int option`<br /><br />`string list`<br /><br />`int ref`<br /><br />`option<int>`<br /><br />`list<string>`<br /><br />`ref<int>`<br /><br />`Dictionary<int, string>`|
|tek bir parametre içeren işlev türü|*parametre type1*  - &gt; *dönüş türü*|Alan bir işlev bir `int` ve döndüren bir `string` türüne sahip `int -> string`|
|birden çok parametre içeren işlev türü|*parametre type1*  - &gt; *parametresi type2*  - &gt; ... -&gt; *dönüş türü*|Alan bir işlev bir `int` ve `float` ve döndüren bir `string` türüne sahip `int -> float -> string`|
|daha yüksek sıralı işlev bir parametre olarak|(*işlev türü*)|`List.map` türüne sahip `('a -> 'b) -> 'a list -> 'b list`|
|temsilci|Temsilci *işlev türü*|`delegate of unit -> int`|
|Esnek türü|#*tür adı*|`#System.Windows.Forms.Control`<br /><br />`#seq<int>`|

## <a name="related-topics"></a>İlgili Konular


|Konu|Açıklama|
|-----|-----------|
|[İlkel Türler](primitive-types.md)|Tam sayı türleri, Boole türü ve karakter türleri gibi yerleşik basit türler açıklanmaktadır.|
|[Birim Türü](unit-type.md)|Açıklar `unit` türü, bir değer olan ve () tarafından belirtilen bir tür; eşdeğer `void` içinde C# ve `Nothing` Visual Basic'te.|
|[Demetler](tuples.md)|Demet türü, çiftleri, Üçlü, quadruples ve benzeri gruplandırılmış herhangi bir türde ilişkili değerleri içeren bir türü açıklar.|
|[Seçenekler](options.md)|Seçenek türü bir değere sahip veya boş bir türü açıklar.|
|[Listeler](lists.md)|Öğeleri dizi sıralı, sabit listelerini açıklar tümü aynı türde.|
|[Diziler](arrays.md)|Bitişik bir bellek bloğunu kaplar ve sabit boyutludur değişebilir öğeleri aynı türde kümesi sıralı diziler açıklar.|
|[Diziler](sequences.md)|Mantıksal bir değerler dizisini temsil eden dizisi türü açıklar; tek tek değerler yalnızca gerektiğinde hesaplanır.|
|[Kayıtlar](records.md)|Adlandırılmış değerler küçük bir toplu kayıt türünü tanımlar.|
|[Ayrılmış Birleşimler](discriminated-unions.md)|Ayrılmış birleşim türü değerleri olası türleri kümesi herhangi biri olabilir bir tür tanımlar.|
|[İşlevler](functions/index.md)|İşlev değerleri açıklar.|
|[Sınıflar](classes.md)|Sınıf türü, bir .NET başvurusu türüne karşılık gelen bir nesne türü açıklanır. Sınıf türleri, üyeler, özellikleri, uygulanan arabirimleri ve bir taban türü içerebilir.|
|[Yapılar](structures.md)|Açıklar `struct` türü, bir .NET değer türüne karşılık gelen bir nesne türü. `struct` Türü genellikle veri küçük bir toplamasını temsil eder.|
|[Arabirimler](interfaces.md)|Bazı işlevler sağlar, ancak hiçbir veri içeren üyelerin kümesini temsil eden türler arabirim türleri açıklanmaktadır. Bir arabirim türü kullanışlı olması için bir nesne türüne göre uygulanmalıdır.|
|[Temsilciler](delegates.md)|Bir işlev nesnesi olarak temsil eden bir temsilci türü açıklar.|
|[Sabit Listeleri](enumerations.md)|Numaralandırma türleri, değerleri bir adlandırılmış değerler kümesine ait açıklar.|
|[Öznitelikler](attributes.md)|Başka bir türü için meta verilerini belirtmek için kullanılan öznitelikleri açıklanmaktadır.|
|[Özel Durum Türleri](exception-handling/exception-types.md)|Hata bilgilerini belirten özel durumlar açıklanmaktadır.|
