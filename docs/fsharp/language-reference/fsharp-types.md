---
title: F# Türleri
description: 'F # ve F # türleri nasıl adlı ve açıklanan kullanılan türleri hakkında bilgi edinin.'
ms.date: 05/16/2016
ms.openlocfilehash: bdbb89dc751970ac31fe102df009f0bff6388e52
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="f-types"></a>F# Türleri

Bu konuda, F # ve F # türleri nasıl adlı ve açıklanan kullanılan türleri açıklanmaktadır.


## <a name="summary-of-f-types"></a>F # türleri özeti
Bazı türleri kabul *ilkel türler*, Boolean türünde gibi `bool` ve bayt ve karakter türleri dahil çeşitli boyutlarda Entegral ve kayan nokta türleri. Bu tür açıklanan [ilkel türler](primitive-types.md).

Dili için yerleşik olan diğer türleri diziler, listeler, dizileri, dizileri, kayıtları içerir ve birleşimler. Diğer .NET dilleri ile deneyimi varsa ve F # öğrenme olduğundan, bu türlerinin her biri için konular okumanız gerekir. Bu türleri hakkında daha fazla bilgi için bağlantılar dahil edilmiştir [ilgili konular](https://msdn.microsoft.com/library/#rel) bölümüne. Bu F #-belirli türleri işlevsel programlama dili için ortak olan programlama stillerini destekler. Bu tür birçok bu türlerinde ortak işlemlerini destekleyen F # kitaplığı modüllerde ilişkilendirdiniz.

Bir işlev türü parametre türleri hakkında bilgi içerir ve dönüş türü.

.NET Framework nesne türleri, arabirim türleri, temsilci türleri ve diğerleri kaynağıdır. Diğer bir .NET dilinde gibi kendi nesne türleri tanımlayabilirsiniz.

Ayrıca, F # kodu adlandırıldığı diğer adlar tanımlayabilirsiniz *yazın kısaltmalar*, türleri için diğer adlar olan. Tür kısaltmaları türü gelecekte değişebilir ve türüne bağlıdır kod değiştirmekten kaçınmak istediğiniz zaman kullanabilirsiniz. Ya da bir türü kısaltması kod okuduğunuzdan ve anladığınızdan kolaylaştırabilir bir tür için bir kolay ad olarak kullanabilirsiniz.

F # işlevsel programlama aklınızda ile tasarlanmış yararlı koleksiyon türleri sağlar. Bu koleksiyon türleri kullanarak stilde daha işlevsel kod yazmanıza yardımcı olur. Daha fazla bilgi için bkz: [F # koleksiyon türleri](fsharp-collection-types.md).


## <a name="syntax-for-types"></a>Türler için sözdizimi
F # kodunda, genellikle türlerinin adlarını yazma sahiptir. Söz dizimi form her türüne sahip ve bu tür ek açıklamaları, Özet yöntem bildirimleri, temsilci bildirimleri, imzalar ve diğer yapıların söz dizimi formlarda kullanın. Yorumlayıcı yeni bir program yapı bildirme her yorumlayıcı türü için yapı ve sözdizimi adını yazdırır. Bu sözdizimi yalnızca kullanıcı tanımlı bir tür için tanımlayıcı veya yerleşik tanımlayıcısı olarak böyle olabilir `int` veya `string`, ancak daha karmaşık türleri için sözdizimi daha karmaşıktır.

Aşağıdaki tabloda, F # türleri türü sözdizimi yönlerini gösterir.



|Tür|Type sözdizimi|Örnekler|
|----|-----------|--------|
|ilkel tür|*tür adı*|`int`<br /><br />`float`<br /><br />`string`|
|toplama türü (sınıfı, yapısı, UNION, kayıt, liste ve benzeri)|*tür adı*|`System.DateTime`<br /><br />`Color`|
|türü kısaltması|*tür kısaltması adı*|`bigint`|
|tam olarak nitelenmiş tür|*namespaces.Type adı*<br /><br />veya<br /><br />*Modules.Type adı*<br /><br />veya<br /><br />*namespaces.Modules.Type adı*|`System.IO.StreamWriter`|
|dizi|*tür adı*[] veya<br /><br />*tür adı* dizisi|`int[]`<br /><br />`array<int>`<br /><br />`int array`|
|İki boyutlu dizi|*tür adı*[,]|`int[,]`<br /><br />`float[,]`|
|Üç boyutlu dizi|*tür adı*[,]|`float[,,]`|
|Tanımlama grubu|*türü Ad1* &#42; *türü ad2* ...|Örneğin, `(1,'b',3)` türüne sahip `int * char * int`|
|genel tür|*tür parametresi* *genel tür adı*<br /><br />veya<br /><br />*genel tür adı*&lt;*türü parametre listesi*&gt;|`'a list`<br /><br />`list<'a>`<br /><br />`Dictionary<'key, 'value>`|
|oluşturulan türü (sağlanan belirli tür bağımsız değişkeni olan genel bir tür)|*tür bağımsız değişkeni* *genel tür adı*<br /><br />veya<br /><br />*genel tür adı*&lt;*türü bağımsız değişken listesi*&gt;|`int option`<br /><br />`string list`<br /><br />`int ref`<br /><br />`option<int>`<br /><br />`list<string>`<br /><br />`ref<int>`<br /><br />`Dictionary<int, string>`|
|tek bir parametre olan işlevi türü|*parametre type1*  - &gt; *dönüş türü*|İsteyen bir işlevi bir `int` ve döndüren bir `string` türüne sahip `int -> string`|
|birden çok parametre olan işlevi türü|*parametre type1*  - &gt; *parametresi type2*  - &gt; ... -&gt; *dönüş türü*|İsteyen bir işlevi bir `int` ve `float` ve döndüren bir `string` türüne sahip `int -> float -> string`|
|bir parametre olarak daha yüksek sıra işlevi|(*işlev türü*)|`List.map` türüne sahip `('a -> 'b) -> 'a list -> 'b list`|
|temsilci|Temsilci *işlev türü*|`delegate of unit -> int`|
|Esnek türü|#*tür adı*|`#System.Windows.Forms.Control`<br /><br />`#seq<int>`|

## <a name="related-topics"></a>İlgili Konular


|Konu|Açıklama|
|-----|-----------|
|[İlkel Türler](primitive-types.md)|Tam sayı türleri, Boolean türünde ve karakter türleri gibi yerleşik basit türleri açıklanmaktadır.|
|[Birim Türü](unit-type.md)|Açıklar `unit` türü, bir değere sahip ve () tarafından belirtilen bir türü; eşdeğer `void` C# ve `Nothing` Visual Basic'te.|
|[Demetler](tuples.md)|Tanımlama grubu, çiftleri, Üçlü, quadruples ve benzeri gruplandırılmış herhangi bir türde ilişkili değerleri içeren bir türü açıklanmaktadır.|
|[Seçenekler](options.md)|Seçeneği, bir değere sahip veya boş bir türü açıklanmaktadır.|
|[Listeler](lists.md)|Öğeleri sıralı, sabit dizi listelerini açıklar tüm aynı türde.|
|[Diziler](arrays.md)|Bitişik bir bellek bloğu kaplar ve sabit boyutludur değişebilir öğeleri aynı türde kümesi sıralı diziler açıklar.|
|[Diziler](sequences.md)|Mantıksal bir değer dizisini temsil eden dizisi türü açıklanır; tek tek değerleri yalnızca gerektiğinde hesaplanır.|
|[Kayıtlar](records.md)|Kayıt türü, küçük bir adlandırılmış değerler toplamasını açıklar.|
|[Ayrılmış Birleşimler](discriminated-unions.md)|Ayrılmış birleşim türü değerleri olası türleri kümesi herhangi biri olabilir bir tür açıklar.|
|[İşlevler](functions/index.md)|İşlev değerleri açıklanmaktadır.|
|[Sınıflar](classes.md)|Sınıf türü, bir .NET başvurusu türüne karşılık gelen bir nesne türü açıklanmaktadır. Sınıf türleri üyeleri, özellikler, uygulanan arabirimler ve bir taban türü içerebilir.|
|[Yapılar](structures.md)|Açıklar `struct` türü, bir .NET değer türüne karşılık gelen bir nesne türü. `struct` Türü genellikle veri küçük bir toplamasını temsil eder.|
|[Arabirimler](interfaces.md)|Bazı işlevler sağlar, ancak hiçbir veri içeren üyelerin kümesini temsil eden türler arabirimi türleri açıklanmaktadır. Bir arabirim türü kullanışlı olması için bir nesne türü tarafından uygulanmalıdır.|
|[Temsilciler](delegates.md)|Bir nesne olarak bir işlevi temsil temsilci türünü tanımlar.|
|[Sabit Listeleri](enumerations.md)|Değerleri bir adlandırılmış değerler kümesine ait numaralandırma türleri açıklanmaktadır.|
|[Öznitelikler](attributes.md)|Başka bir tür için meta verileri belirtmek için kullanılan öznitelikleri açıklanmaktadır.|
|[Özel Durum Türleri](exception-handling/exception-types.md)|Hata bilgilerini belirtmek özel durumlar açıklanmaktadır.|
