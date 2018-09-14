---
title: join tümcesi (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- join
- join_CSharpKeyword
helpviewer_keywords:
- join clause [C#]
- join keyword [C#]
ms.assetid: 76e9df84-092c-41a6-9537-c3f1cbd7f0fb
ms.openlocfilehash: dee11c1ab754e515c69f330a5919776cbcb1e775
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45587681"
---
# <a name="join-clause-c-reference"></a>join tümcesi (C# Başvurusu)

`join` Yan tümcesi, nesne modelinde hiçbir doğrudan ilişkisi olan farklı kaynak dizilerinden öğelerini ilişkilendirmek için kullanışlıdır. Her kaynak öğeleri eşitlik için karşılaştırılması gereken bazı değeri paylaşmak tek gereksinim olmasıdır. Örneğin, bir yiyecek dağıtımcısı, belirli bir ürünü tedarikçileri listesini ve alıcıların listesi sahip olabilir. A `join` yan tümcesi, örneğin, üreticiler listesini oluşturmak için kullanılabilir ve tüm aynı olan alıcılar bu ürünün belirtilen bölge.

A `join` yan tümcesi, iki kaynak dizileri girdi alır. Her bir dizideki öğelerin olması veya diğer dizisindeki karşılık gelen bir özellik için karşılaştırılabilir bir özelliği içerir. `join` Yan tümcesi, özel kullanarak eşitlik için belirtilen anahtarları karşılaştırır `equals` anahtar sözcüğü. Tarafından gerçekleştirilen tüm birleştirmeler `join` yan tümcesi olan equijoins. Çıkışı şeklini bir `join` yan tümcesi yapmakta olduğunuz birleştirme belirli türüne göre değişir. En yaygın üç birleşim türleri şunlardır:

- İç birleştirme

- Grup birleştirme

- Sol dış birleştirme

## <a name="inner-join"></a>İç birleştirme

Aşağıdaki örnek, basit bir iç equijoin gösterir. Bu sorgu düz dizisi üretir "ürün adı / kategorisi" çiftleri. Aynı kategori dize birden çok öğe görünür. Bir öğeyi, `categories` eşleşen yok `products`, bu kategoriye sonuçlarında görünmez.

[!code-csharp[cscsrefQueryKeywords#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#24)]

Daha fazla bilgi için [iç birleştirmeler gerçekleştirme](../../linq/perform-inner-joins.md).

## <a name="group-join"></a>Grup birleştirme

A `join` yan tümcesiyle birlikte bir `into` ifadesi, bir grup birleştirme çağrılır.

[!code-csharp[cscsrefQueryKeywords#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#25)]

Grup birleştirme sağ tarafındaki kaynak dizideki eşleşen öğelerin bir veya daha fazla sol kaynak dizisinin öğelerini ilişkilendirir bir hiyerarşik bir sonuç dizisi üretir. Grup birleştirme eşdeğeri ilişkisel koşullarını vardır. Bu temelde bir nesne dizisidir.

Öğenin sol kaynakta, eşleştirilecek öğe için doğru kaynak sırasından bulunursa `join` yan tümcesi, o öğe için boş bir dizi üretir. Sonuç dizisi gruplar halinde düzenlenir. Bu nedenle, group JOIN hala temelde iç-equijoin olmasıdır.

Grup birleştirme sonuçlarını seçmeniz yeterlidir, öğelere erişebilirsiniz, ancak bunlar üzerinde eşleşen anahtar tanımlayamaz. Bu nedenle, önceki örnekte gösterildiği gibi anahtar adı olan yeni bir türe group JOIN sonuçlarını seçin genel olarak daha yararlı olur.

Ayrıca, bir grup birleştirme sonucu başka bir alt sorgu oluşturucu olarak kullanabilirsiniz:

[!code-csharp[cscsrefQueryKeywords#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#26)]

Daha fazla bilgi için [gruplandırılmış birleştirmeler gerçekleştirme](../../linq/perform-grouped-joins.md).

## <a name="left-outer-join"></a>Sol dış birleştirme

Eşleşen bir öğe doğru sırada olsa bile bir sol dış birleştirme, soldaki kaynak dizisindeki tüm öğeleri, döndürülür. Bir sol dış birleştirme gerçekleştirmek için [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], kullanın `DefaultIfEmpty` sol taraftaki öğesi herhangi bir eşleşme varsa üretmek için bir varsayılan sağ taraftaki öğesi belirtmek için bir grup birleştirme birlikte yöntemi. Kullanabileceğiniz `null` olarak herhangi bir referans için varsayılan değer türü veya bir kullanıcı tanımlı tür belirtebilirsiniz. Aşağıdaki örnekte, bir kullanıcı tarafından tanımlanan varsayılan türü gösterilmiştir:

[!code-csharp[cscsrefQueryKeywords#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#27)]

Daha fazla bilgi için [sol dış birleştirmeler gerçekleştirme](../../linq/perform-left-outer-joins.md).

## <a name="the-equals-operator"></a>Eşittir işleci

A `join` yan tümcesi equijoin gerçekleştirir. Diğer bir deyişle, iki anahtar eşitlik yalnızca temel eşleşmeleri ile kullanabilirsiniz. Karşılaştırma "büyük" veya "eşit değildir" gibi diğer türleri desteklenmez. Tüm birleştirmeler equijoins, olduğunu netleştirmek için `join` yan tümcesi kullanan `equals` anahtar sözcüğü yerine `==` işleci. `equals` Anahtar sözcüğü yalnızca kullanılabilir bir `join` yan tümcesi ve farklıdır `==` önemli bir şekilde işleci. İle `equals`sol ok tuşu dış kaynak dizisini tüketir ve sağ ok tuşu iç kaynak kullanır. Yalnızca sol tarafındaki kapsamda dış kaynağıdır `equals` ve iç kaynak yalnızca işlecin sağ tarafındaki kapsamda sırasıdır.

## <a name="non-equijoins"></a>Olmayan equijoins

Çapraz birleştirme ve diğer özel birleştirme işlemleri olmayan-equijoins, birden çok kullanarak gerçekleştirebileceğiniz `from` yeni dizileri bağımsız olarak bir sorguya tanıtmak amacıyla yan tümceler. Daha fazla bilgi için [özel birleştirme işlemleri gerçekleştirme](../../linq/perform-custom-join-operations.md).

## <a name="joins-on-object-collections-vs-relational-tables"></a>Nesnesi koleksiyonlar ilişkisel tabloları ve birleşimler

İçinde bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu ifadesinde, birleştirme işlemleri, nesne koleksiyonları üzerinde gerçekleştirilir. Nesne koleksiyonları "iki ilişkisel tabloları tam olarak aynı şekilde katılamaz". İçinde [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], açık `join` yan tümceleri, yalnızca iki kaynak dizileri tarafından herhangi bir ilişki bağlanmayan gereklidir. İle çalışırken [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], yabancı anahtar tabloları nesne modelinde birincil tablo özellikleri olarak temsil edilir. Örneğin, Northwind veritabanında yabancı anahtar ilişkisi Siparişler tablosu ile müşteri tablosu vardır. Tablolar için nesne modeli eşlediğinizde, müşteri sınıfı bu müşteriyle ilgili Siparişler topluluğu içeren bir sipariş özelliğine sahiptir. Aslında, birleştirme zaten sizin için yapılmıştır.

Bağlamında ilgili tablolar üzerinden sorgulama hakkında daha fazla bilgi için [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], bkz: [nasıl yapılır: veritabanı ilişkilerini eşleme](../../../framework/data/adonet/sql/linq/how-to-map-database-relationships.md).

## <a name="composite-keys"></a>Bileşik anahtarlar

Bir bileşik anahtarı kullanılarak birden çok değer eşitliği test edebilirsiniz. Daha fazla bilgi için [bileşik anahtarlar kullanarak birleştirme](../../linq/join-by-using-composite-keys.md). Bileşik anahtarlar da kullanılabilir bir `group` yan tümcesi.

## <a name="example"></a>Örnek

Aşağıdaki örnek, aynı eşleşen anahtarlar kullanılarak bir iç birleştirme, bir grup katma ve aynı veri kaynaklarında bir sol dış birleştirme sonuçlarının karşılaştırır. Bazı ek bir kod sonuçları konsol açıklamak için bu örnekleri eklenir.

[!code-csharp[cscsrefQueryKeywords#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#23)]

## <a name="remarks"></a>Açıklamalar

A `join` tarafından izlenmiyor yan tümcesi `into` erişimcisine bir <xref:System.Linq.Enumerable.Join%2A> yöntem çağrısı. A `join` takip yan tümcesi `into` çevrildiğinde bir <xref:System.Linq.Enumerable.GroupJoin%2A> yöntem çağrısı.

## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu anahtar sözcükleri (LINQ)](query-keywords.md)
- [Dil ile Tümleşik Sorgu (LINQ)](../../linq/index.md)
- [Birleştirme İşlemleri](../../programming-guide/concepts/linq/join-operations.md)
- [group yan tümcesi](group-clause.md)
- [Sol dış birleştirmeler gerçekleştirme](../../linq/perform-left-outer-joins.md)
- [İç birleşimler gerçekleştirme](../../linq/perform-inner-joins.md)
- [Gruplanmış birleşimler gerçekleştirme](../../linq/perform-grouped-joins.md)
- [Join yan tümcesinin sonuçlarını sıralama](../../linq/order-the-results-of-a-join-clause.md)
- [Bileşik anahtarlar kullanarak birleştirme](../../linq/join-by-using-composite-keys.md)
- [Visual Studio için uyumlu veritabanı sistemleri](/visualstudio/data-tools/installing-database-systems-tools-and-samples)