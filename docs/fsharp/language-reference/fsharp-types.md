---
title: Türler
description: 'F # içinde kullanılan türler ve F # türlerinin nasıl adlandırıldığı ve açıklandığı hakkında bilgi edinin.'
ms.date: 08/15/2020
ms.openlocfilehash: a86d8e8f672d8399b02bb193ae04e1f0d46720b6
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812074"
---
# <a name="f-types"></a>F# Türleri

Bu konu, F # içinde kullanılan türleri ve F # türlerinin nasıl adlandırıldığını ve açıklandığını açıklamaktadır.

## <a name="summary-of-f-types"></a>F # türlerinin Özeti

Bazı türler, *primitive types* `bool` bayt ve karakter türleri dahil olmak üzere çeşitli boyutlarda Boole türü ve integral ve kayan nokta türleri gibi temel türler olarak değerlendirilir. Bu türler [temel türler](basic-types.md)bölümünde açıklanmıştır.

Dilde yerleşik olan diğer türler arasında tanımlama grupları, listeler, diziler, sıralar, kayıtlar ve ayırt edici birleşimler bulunur. Diğer .NET dilleri ile deneyiminiz varsa ve F # öğreniyor, bu türlerin her biri için konuları Okumalısınız. Bu F # özel türleri, fonksiyonel programlama dilleri için ortak olan programlama stillerini destekler. Bu türlerin çoğunda, F # kitaplığında bu türlerde yaygın işlemleri destekleyen ilişkili modüller vardır.

İşlevin türü, parametre türleri ve dönüş türü hakkında bilgi içerir.

.NET Framework, nesne türlerinin, arabirim türlerinin, temsilci türlerinin ve diğer kullanıcıların kaynağıdır. Kendi nesne türlerinizi, diğer herhangi bir .NET dilinde olduğu gibi tanımlayabilirsiniz.

Ayrıca, F # kodu türler için alternatif adlar olan *tür kısaltmaları*olarak adlandırılan diğer adları tanımlayabilir. Tür kısaltmalarının, gelecekte değişiklik olabileceği ve türe bağlı olan kodun değiştirilmesini önlemek istediğiniz durumlarda kullanabilirsiniz. Ya da bir tür kısaltmayı, kodun daha kolay okunmasını ve anlaşılmasını sağlayan bir tür için kolay bir ad olarak kullanabilirsiniz.

F #, işlevsel programlama ile tasarlanan yararlı koleksiyon türlerini aklınızda sunar. Bu koleksiyon türlerini kullanmak, stilde daha işlevsel olan kodu yazmanıza yardımcı olur. Daha fazla bilgi için bkz. [F # koleksiyon türleri](fsharp-collection-types.md).

## <a name="syntax-for-types"></a>Türler için sözdizimi

F # kodunda genellikle türlerin adlarını yazmanız gerekir. Her tür bir sözdizimsel biçimine sahiptir ve bu sözdizimsel formları tür ek açıklamalarında, Soyut yöntem bildirimlerinde, temsilci bildirimlerinde, imzalarda ve diğer yapılara kullanırsınız. Yorumlayıcıda yeni bir program yapısı bildirdiğinizde, yorumlayıcı yapının adını ve türünün sözdizimini yazar. Bu söz dizimi yalnızca Kullanıcı tanımlı bir tür için tanımlayıcı veya ya da gibi bir yerleşik tanımlayıcı olabilir, `int` `string` ancak daha karmaşık türler için sözdizimi daha karmaşıktır.

Aşağıdaki tabloda, F # türleri için tür sözdiziminin yönleri gösterilmektedir.

|Tür|Tür sözdizimi|Örnekler|
|----|-----------|--------|
|ilkel tür|*tür adı*|`int`<br /><br />`float`<br /><br />`string`|
|Toplam türü (sınıf, yapı, birleşim, kayıt, Enum, vb.)|*tür adı*|`System.DateTime`<br /><br />`Color`|
|tür kısaltması|*tür kısaltması-adı*|`bigint`|
|tam nitelikli tür|*ad alanları. tür-adı*<br /><br />veya<br /><br />*modüller. tür-adı*<br /><br />veya<br /><br />*Namespaces. modüller. Type-Name*|`System.IO.StreamWriter`|
|array|*tür adı*[] veya<br /><br />*tür adı* dizisi|`int[]`<br /><br />`array<int>`<br /><br />`int array`|
|iki boyutlu dizi|*tür adı*[,]|`int[,]`<br /><br />`float[,]`|
|üç boyutlu dizi|*tür adı*[,,]|`float[,,]`|
|tuple|*tür-name1* &#42; *türü-AD2* ...|Örneğin, `(1,'b',3)` türü `int * char * int`|
|Genel tür|*tür-parametre* *genel-tür-adı*<br /><br />veya<br /><br />*genel tür-adı* &lt; *tür-parametre-liste*&gt;|`'a list`<br /><br />`list<'a>`<br /><br />`Dictionary<'key, 'value>`|
|oluşturulmuş tür (belirli bir tür bağımsız değişkenine sahip olan genel bir tür)|*tür-bağımsız değişken* *genel-tür-adı*<br /><br />veya<br /><br />*genel tür-adı* &lt; *tür bağımsız değişken listesi*&gt;|`int option`<br /><br />`string list`<br /><br />`int ref`<br /><br />`option<int>`<br /><br />`list<string>`<br /><br />`ref<int>`<br /><br />`Dictionary<int, string>`|
|tek parametreye sahip işlev türü|*parametre-Type1*  - &gt; *dönüş türü*|`int`' A sahip olan ve bir türü döndüren bir işlev `string``int -> string`|
|birden çok parametreye sahip işlev türü|*parametre-Type1*  - &gt; *parametre-type2*  - &gt; ...- &gt; *Return-Type*|`int`Ve ' a alan `float` ve bir `string` türü döndüren bir işlev`int -> float -> string`|
|bir parametre olarak daha yüksek sıralı işlev|(*işlev türü*)|`List.map` türü vardır `('a -> 'b) -> 'a list -> 'b list`|
|temsilci|*işlev türü* temsilcisi|`delegate of unit -> int`|
|esnek tür|#*tür adı*|`#System.Windows.Forms.Control`<br /><br />`#seq<int>`|

## <a name="related-topics"></a>İlgili Konular

|Konu|Açıklama|
|-----|-----------|
|[İlkel Türler](basic-types.md)|İntegral türleri, Boole türü ve karakter türleri gibi yerleşik basit türleri açıklar.|
|[Birim Türü](unit-type.md)|`unit`Bir değere sahip olan ve () ile belirtilen, `void` C# ve Visual Basic ile eşdeğer olan türü açıklar `Nothing` .|
|[Tanımlama grupları](tuples.md)|Çiftler, Üçlü ve çeyrek Rupisi gibi gruplanmış herhangi bir türdeki ilişkili değerlerden oluşan tür tanımlama grubu türünü açıklar.|
|[Seçenekler](options.md)|Bir değeri olan veya boş olabilecek bir tür olan seçenek türünü açıklar.|
|[Listeler](lists.md)|Aynı türden tümü sıralanmış, sabit öğe dizileri olan listeleri açıklar.|
|[Diziler](arrays.md)|Ardışık bir bellek bloğunu kaplayan ve sabit boyutta olan aynı türde kesilebilir öğe kümesi olan dizileri açıklar.|
|[Diziler](sequences.md)|Bir mantıksal değer serisini temsil eden dizi türünü açıklar; tek değerler yalnızca gerekli olduğu gibi hesaplanır.|
|[Kayıtlar](records.md)|Adlandırılmış değerlerin küçük bir toplamı olan kayıt türünü açıklar.|
|[Ayrılmış Birleşimler](discriminated-unions.md)|Değerleri olası bir tür kümesinden herhangi biri olabilecek bir tür olan ayırt edici birleşim türünü açıklar.|
|[İşlevler](./functions/index.md)|İşlev değerlerini açıklar.|
|[Sınıflar](classes.md)|.NET başvuru türüne karşılık gelen bir nesne türü olan sınıf türünü açıklar. Sınıf türleri Üyeler, özellikler, uygulanan arabirimler ve temel bir tür içerebilir.|
|[Yapılar](structures.md)|`struct`.Net değer türüne karşılık gelen bir nesne türü olan türü açıklar. `struct`Tür genellikle küçük bir veri toplamasını temsil eder.|
|[Arabirimler](interfaces.md)|Belirli işlevselliği sağlayan, ancak hiçbir veri içermeyen bir üye kümesini temsil eden türler olan arabirim türlerini açıklar. Bir arabirim türünün yararlı olması için bir nesne türü tarafından uygulanması gerekir.|
|[Temsilciler](delegates.md)|Bir işlevi bir nesne olarak temsil eden temsilci türünü açıklar.|
|[Numaralandırmalar](enumerations.md)|Değerleri bir adlandırılmış değerler kümesine ait olan numaralandırma türlerini açıklar.|
|[Öznitelikler](attributes.md)|Diğer bir tür için meta verileri belirtmek için kullanılan öznitelikleri açıklar.|
|[Özel Durum Türleri](./exception-handling/exception-types.md)|Hata bilgilerini belirten özel durumları açıklar.|
