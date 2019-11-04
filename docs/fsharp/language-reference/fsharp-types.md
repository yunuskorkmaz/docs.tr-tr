---
title: F# Türleri
description: "' De F# kullanılan türler ve F# türlerin adlandırılması ve açıklaması hakkında bilgi edinin."
ms.date: 05/16/2016
ms.openlocfilehash: 8f2526dce46d53a92c01c9347e1ed97681a45ecc
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425302"
---
# <a name="f-types"></a>F# Türleri

Bu konu, içinde F# kullanılan türleri ve türlerin adlandırılması ve açıklanme biçimini F# açıklar.

## <a name="summary-of-f-types"></a>F# Türlerin Özeti

Bazı türler, Boolean türü `bool` ve integral ve kayan nokta türleri gibi *basit türler*(örneğin, bayt ve karakter türlerini içerir) olarak değerlendirilir. Bu türler [temel türler](basic-types.md)bölümünde açıklanmıştır.

Dilde yerleşik olan diğer türler arasında tanımlama grupları, listeler, diziler, sıralar, kayıtlar ve ayırt edici birleşimler bulunur. Diğer .NET dilleri ile deneyiminiz varsa ve öğrenilleriniz F#varsa, bu türlerin her biri için konuları Okumalısınız. Bu türler hakkında daha fazla bilgi için bağlantılar, bu konunun [Ilgili konular](https://msdn.microsoft.com/library/#rel) bölümüne eklenmiştir. Bu F#özel türler, fonksiyonel programlama dilleri için ortak olan programlama stillerini destekler. Bu türlerin çoğunda kitaplıkta ilişkili modüller vardır ve F# bu türler üzerinde yaygın işlemleri destekler.

İşlevin türü, parametre türleri ve dönüş türü hakkında bilgi içerir.

.NET Framework, nesne türlerinin, arabirim türlerinin, temsilci türlerinin ve diğer kullanıcıların kaynağıdır. Kendi nesne türlerinizi, diğer herhangi bir .NET dilinde olduğu gibi tanımlayabilirsiniz.

Ayrıca, F# kod, türler için alternatif adlar olan *tür kısaltmaları*olarak adlandırılan diğer adları tanımlayabilir. Tür kısaltmalarının, gelecekte değişiklik olabileceği ve türe bağlı olan kodun değiştirilmesini önlemek istediğiniz durumlarda kullanabilirsiniz. Ya da bir tür kısaltmayı, kodun daha kolay okunmasını ve anlaşılmasını sağlayan bir tür için kolay bir ad olarak kullanabilirsiniz.

F#fonksiyonel programlama ile tasarlanan yararlı koleksiyon türlerini göz önünde bulundurun. Bu koleksiyon türlerini kullanmak, stilde daha işlevsel olan kodu yazmanıza yardımcı olur. Daha fazla bilgi için bkz [ F# . koleksiyon türleri](fsharp-collection-types.md).

## <a name="syntax-for-types"></a>Türler için sözdizimi

F# Kodda, genellikle türlerin adlarını yazmanız gerekir. Her tür bir sözdizimsel biçimine sahiptir ve bu sözdizimsel formları tür ek açıklamalarında, Soyut yöntem bildirimlerinde, temsilci bildirimlerinde, imzalarda ve diğer yapılara kullanırsınız. Yorumlayıcıda yeni bir program yapısı bildirdiğinizde, yorumlayıcı yapının adını ve türünün sözdizimini yazar. Bu söz dizimi yalnızca Kullanıcı tanımlı bir tür için tanımlayıcı veya `int` ya da `string`gibi bir yerleşik tanımlayıcı olabilir, ancak daha karmaşık türler için sözdizimi daha karmaşıktır.

Aşağıdaki tabloda türler için F# tür sözdiziminin yönleri gösterilmektedir.

|Tür|Tür sözdizimi|Örnekler|
|----|-----------|--------|
|ilkel tür|*tür adı*|`int`<br /><br />`float`<br /><br />`string`|
|Toplam türü (sınıf, yapı, birleşim, kayıt, Enum, vb.)|*tür adı*|`System.DateTime`<br /><br />`Color`|
|tür kısaltması|*tür kısaltması-adı*|`bigint`|
|tam nitelikli tür|*ad alanları. tür-adı*<br /><br />veya<br /><br />*modüller. tür-adı*<br /><br />veya<br /><br />*Namespaces. modüller. Type-Name*|`System.IO.StreamWriter`|
|dizi|*tür adı*[] veya<br /><br />*tür adı* dizisi|`int[]`<br /><br />`array<int>`<br /><br />`int array`|
|iki boyutlu dizi|*tür adı*[,]|`int[,]`<br /><br />`float[,]`|
|üç boyutlu dizi|*tür adı*[,,]|`float[,,]`|
|Le|*tür-name1* &#42; *Type-AD2* ...|Örneğin, `(1,'b',3)` türü `int * char * int`|
|Genel tür|*tür-parametre* *genel-tür-adı*<br /><br />veya<br /><br />*genel tür adı*&lt;*türü-parametre-listesi*&gt;|`'a list`<br /><br />`list<'a>`<br /><br />`Dictionary<'key, 'value>`|
|oluşturulmuş tür (belirli bir tür bağımsız değişkenine sahip olan genel bir tür)|*tür-bağımsız değişken* *genel-tür-adı*<br /><br />veya<br /><br />*genel tür adı*&lt;*türü-bağımsız değişken listesi*&gt;|`int option`<br /><br />`string list`<br /><br />`int ref`<br /><br />`option<int>`<br /><br />`list<string>`<br /><br />`ref<int>`<br /><br />`Dictionary<int, string>`|
|tek parametreye sahip işlev türü|*Parameter-type1* -&gt; *dönüş türü*|Bir `int` alan ve `string` türü döndüren bir işlev `int -> string`|
|birden çok parametreye sahip işlev türü|*Parameter-type1* -&gt; *parametresi-type2* -&gt;...-&gt; *Return-Type*|Bir `int` ve `float` alan ve bir `string` türü döndüren bir işlev `int -> float -> string`|
|bir parametre olarak daha yüksek sıralı işlev|(*işlev türü*)|`List.map` türü `('a -> 'b) -> 'a list -> 'b list`|
|temsilci|*işlev türü* temsilcisi|`delegate of unit -> int`|
|esnek tür|#*türü-adı*|`#System.Windows.Forms.Control`<br /><br />`#seq<int>`|

## <a name="related-topics"></a>İlgili Konular

|Konu|Açıklama|
|-----|-----------|
|[İlkel Türler](basic-types.md)|İntegral türleri, Boole türü ve karakter türleri gibi yerleşik basit türleri açıklar.|
|[Birim Türü](unit-type.md)|Bir değere sahip olan ve () ile belirtilen `unit` türü tanımlar. Visual Basic içindeki `void` C# ve `Nothing` eşdeğerdir.|
|[Demetler](tuples.md)|Çiftler, Üçlü ve çeyrek Rupisi gibi gruplanmış herhangi bir türdeki ilişkili değerlerden oluşan tür tanımlama grubu türünü açıklar.|
|[Seçenekler](options.md)|Bir değeri olan veya boş olabilecek bir tür olan seçenek türünü açıklar.|
|[Listeler](lists.md)|Aynı türden tümü sıralanmış, sabit öğe dizileri olan listeleri açıklar.|
|[Diziler](arrays.md)|Ardışık bir bellek bloğunu kaplayan ve sabit boyutta olan aynı türde kesilebilir öğe kümesi olan dizileri açıklar.|
|[Diziler](sequences.md)|Bir mantıksal değer serisini temsil eden dizi türünü açıklar; tek değerler yalnızca gerekli olduğu gibi hesaplanır.|
|[Kayıtlar](records.md)|Adlandırılmış değerlerin küçük bir toplamı olan kayıt türünü açıklar.|
|[Ayrılmış Birleşimler](discriminated-unions.md)|Değerleri olası bir tür kümesinden herhangi biri olabilecek bir tür olan ayırt edici birleşim türünü açıklar.|
|[İşlevler](./functions/index.md)|İşlev değerlerini açıklar.|
|[Sınıflar](classes.md)|.NET başvuru türüne karşılık gelen bir nesne türü olan sınıf türünü açıklar. Sınıf türleri Üyeler, özellikler, uygulanan arabirimler ve temel bir tür içerebilir.|
|[Yapılar](structures.md)|.NET değer türüne karşılık gelen bir nesne türü olan `struct` türünü açıklar. `struct` türü genellikle küçük bir veri toplamasını temsil eder.|
|[Arabirimler](interfaces.md)|Belirli işlevselliği sağlayan, ancak hiçbir veri içermeyen bir üye kümesini temsil eden türler olan arabirim türlerini açıklar. Bir arabirim türünün yararlı olması için bir nesne türü tarafından uygulanması gerekir.|
|[Temsilciler](delegates.md)|Bir işlevi bir nesne olarak temsil eden temsilci türünü açıklar.|
|[Sabit Listeleri](enumerations.md)|Değerleri bir adlandırılmış değerler kümesine ait olan numaralandırma türlerini açıklar.|
|[Öznitelikler](attributes.md)|Diğer bir tür için meta verileri belirtmek için kullanılan öznitelikleri açıklar.|
|[Özel Durum Türleri](./exception-handling/exception-types.md)|Hata bilgilerini belirten özel durumları açıklar.|
