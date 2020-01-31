---
title: Join Işlemler (C#)
ms.date: 07/20/2015
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
no-loc:
- Join
- GroupJoin
ms.openlocfilehash: 6e2ec1a0c8120f6869b7c0a196b77d118762a8dd
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868011"
---
# <a name="join-operations-c"></a>JOIN Işlemleri (C#)

İki veri kaynağının *birleşimi* , bir veri kaynağındaki nesnelerin, başka bir veri kaynağında ortak bir özniteliği paylaşan nesnelerle ilişkilendirilmesi.  
  
 Birleştirme, birbirleriyle ilişkilerini hedefleyen veri kaynaklarını hedef alan sorgularda önemli bir işlemdir. Nesne odaklı programlamada bu, tek yönlü bir ilişkinin geriye doğru yönü gibi Modellenmemiş nesneler arasındaki bir bağıntı anlamına gelebilir. Tek yönlü ilişki örneği, şehir türünde bir özelliği olan bir müşteri sınıfıdır, ancak City sınıfı, müşteri nesnelerinin bir koleksiyonu olan bir özelliğine sahip değildir. Bir şehir nesneleri listeniz varsa ve her bir şehirde tüm müşterileri bulmak istiyorsanız, bunları bulmak için bir JOIN işlemi kullanabilirsiniz.  
  
 LINQ çerçevesinde sunulan JOIN yöntemleri <xref:System.Linq.Enumerable.Join%2A> ve <xref:System.Linq.Enumerable.GroupJoin%2A>. Bu yöntemler, anahtarlarının eşitliğine göre iki veri kaynağıyla eşleşen eş birleştirmeleri veya birleştirmeleri gerçekleştirir. (Karşılaştırma için Transact-SQL ' Equals ' dışındaki bir JOIN işleçlerini destekler, örneğin ' küçüktür ' işleci.) İlişkisel veritabanı koşullarında <xref:System.Linq.Enumerable.Join%2A>, yalnızca diğer veri kümesinde eşleşme olan nesnelerin döndürüldüğü bir birleşim türü olan bir iç birleşim uygular. <xref:System.Linq.Enumerable.GroupJoin%2A> yönteminin ilişkisel veritabanı terimlerinde doğrudan eşdeğeri yoktur, ancak iç birleştirmeler ve sol dış birleşimlerin bir üst kümesini uygular. Sol dış birleşim, diğer veri kaynağında bağıntılı bir öğesi olmasa bile, ilk (soldaki) veri kaynağının her bir öğesini döndüren birleşimdir.  
  
 Aşağıdaki çizimde, iki kümenin kavramsal görünümü ve bu kümeler içindeki öğelerin bir iç birleşime veya bir sol dış birleşime dahil olduğu gösterilmektedir.  
  
 ![İç&#47;dıştaki gösteren iki çakışan daire.](./media/join-operations/join-method-overlapping-circles.png)  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem adı|Açıklama|C#Sorgu Ifadesi söz dizimi|Daha fazla bilgi|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Join|Anahtar Seçici işlevlerine göre iki diziyi birleştirir ve değer çiftlerini ayıklar.|`join … in … on … equals …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|GroupJoin|Anahtar Seçici işlevlerine göre iki diziyi birleştirir ve her öğe için elde edilen eşleşmeleri gruplandırır.|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Sorgu ifadesi söz dizimi örnekleri
  
### Join  
  
Aşağıdaki örnek, belirli bir değere göre iki diziyi birleştirmek için `join … in … on … equals …` yan tümcesini kullanır:
  
[!code-csharp[Join](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQJoinOperation/CS/JoinOperation.cs#Join)]  

### GroupJoin  

Aşağıdaki örnek, belirli bir değere göre iki diziyi birleştirmek için `join … in … on … equals … into …` yan tümcesini kullanır ve her öğe için elde edilen eşleşmeleri gruplandırır:
  
[!code-csharp[GroupJoin](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQJoinOperation/CS/JoinOperation.cs#GroupJoin)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq>
- [Standart sorgu Işleçlerine genelC#bakış ()](./standard-query-operators-overview.md)
- [Anonim Tipler](../../classes-and-structs/anonymous-types.md)
- [Birleşimler ve Çapraz Ürün Sorguları Düzenleme](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)
- [join yan tümcesi](../../../language-reference/keywords/join-clause.md)
- [bileşik anahtarlar kullanarak Join](../../../linq/join-by-using-composite-keys.md)
- [Benzer olmayan dosyalardaki (LINQ) (C#) içerik ekleme](./how-to-join-content-from-dissimilar-files-linq.md)
- [Join yan tümcesinin sonuçlarını sıralama](../../../linq/order-the-results-of-a-join-clause.md)
- [Özel birleştirme işlemleri gerçekleştirme](../../../linq/perform-custom-join-operations.md)
- [Gruplanmış birleşimler gerçekleştirme](../../../linq/perform-grouped-joins.md)
- [İç birleşimler gerçekleştirme](../../../linq/perform-inner-joins.md)
- [Sol dış birleştirmeler gerçekleştirme](../../../linq/perform-left-outer-joins.md)
- [Birden çok kaynaktan nesne koleksiyonları doldurma (LINQ) (C#)](./how-to-populate-object-collections-from-multiple-sources-linq.md)
