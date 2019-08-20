---
title: JOIN Işlemleri (C#)
ms.date: 07/20/2015
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
ms.openlocfilehash: 95661e2d0d7f4f0e75c1fa1b10e1f322923189b1
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592085"
---
# <a name="join-operations-c"></a>JOIN Işlemleri (C#)
İki veri kaynağının *birleşimi* , bir veri kaynağındaki nesnelerin, başka bir veri kaynağında ortak bir özniteliği paylaşan nesnelerle ilişkilendirilmesi.  
  
 Birleştirme, birbirleriyle ilişkilerini hedefleyen veri kaynaklarını hedef alan sorgularda önemli bir işlemdir. Nesne odaklı programlamada bu, tek yönlü bir ilişkinin geriye doğru yönü gibi Modellenmemiş nesneler arasındaki bir bağıntı anlamına gelebilir. Tek yönlü ilişki örneği, şehir türünde bir özelliği olan bir müşteri sınıfıdır, ancak City sınıfı, müşteri nesnelerinin bir koleksiyonu olan bir özelliğine sahip değildir. Bir şehir nesneleri listeniz varsa ve her bir şehirde tüm müşterileri bulmak istiyorsanız, bunları bulmak için bir JOIN işlemi kullanabilirsiniz.  
  
 LINQ çerçevesinde sunulan JOIN yöntemleri ve ' <xref:System.Linq.Enumerable.Join%2A> <xref:System.Linq.Enumerable.GroupJoin%2A>dir. Bu yöntemler, anahtarlarının eşitliğine göre iki veri kaynağıyla eşleşen eş birleştirmeleri veya birleştirmeleri gerçekleştirir. (Karşılaştırma için Transact-SQL ' Equals ' dışındaki bir JOIN işleçlerini destekler, örneğin ' küçüktür ' işleci.) İlişkisel veritabanı koşullarında, <xref:System.Linq.Enumerable.Join%2A> bir iç birleşim ve yalnızca diğer veri kümesinde eşleşme olan nesnelerin döndürüldüğü bir birleşim türü uygular. <xref:System.Linq.Enumerable.GroupJoin%2A> Metodun ilişkisel veritabanı terimlerinde doğrudan eşdeğeri yoktur, ancak iç birleştirmeler ve sol dış birleştirmeler üst kümesini uygular. Sol dış birleşim, diğer veri kaynağında bağıntılı bir öğesi olmasa bile, ilk (soldaki) veri kaynağının her bir öğesini döndüren birleşimdir.  
  
 Aşağıdaki çizimde, iki kümenin kavramsal görünümü ve bu kümeler içindeki öğelerin bir iç birleşime veya bir sol dış birleşime dahil olduğu gösterilmektedir.  
  
 ![İç&#47;dıştaki gösteren iki çakışan daire.](./media/join-operations/join-method-overlapping-circles.png)  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem adı|Açıklama|C#Sorgu Ifadesi söz dizimi|Daha fazla bilgi|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Birleştirme|Anahtar Seçici işlevlerine göre iki diziyi birleştirir ve değer çiftlerini ayıklar.|`join … in … on … equals …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|GroupJoin|Anahtar Seçici işlevlerine göre iki diziyi birleştirir ve her öğe için elde edilen eşleşmeleri gruplandırır.|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq>
- [Standart sorgu Işleçlerine genelC#bakış ()](./standard-query-operators-overview.md)
- [Anonim Tipler](../../classes-and-structs/anonymous-types.md)
- [Birleşimler ve Çapraz Ürün Sorguları Düzenleme](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)
- [join yan tümcesi](../../../language-reference/keywords/join-clause.md)
- [Nasıl yapılır: Bileşik anahtarlar kullanarak birleştirin](../../linq-query-expressions/how-to-join-by-using-composite-keys.md)
- [Nasıl yapılır: Benzer olmayan dosyalardaki (LINQ) (C#) içerik birleştirin](./how-to-join-content-from-dissimilar-files-linq.md)
- [Nasıl yapılır: JOIN yan tümcesinin sonuçlarını sıralama](../../linq-query-expressions/how-to-order-the-results-of-a-join-clause.md)
- [Nasıl yapılır: Özel JOIN Işlemleri gerçekleştirme](../../linq-query-expressions/how-to-perform-custom-join-operations.md)
- [Nasıl yapılır: Gruplanmış birleşimler gerçekleştirme](../../linq-query-expressions/how-to-perform-grouped-joins.md)
- [Nasıl yapılır: Iç birleştirmeler gerçekleştirme](../../linq-query-expressions/how-to-perform-inner-joins.md)
- [Nasıl yapılır: Sol dış birleştirmeler gerçekleştirme](../../linq-query-expressions/how-to-perform-left-outer-joins.md)
- [Nasıl yapılır: Birden çok kaynaktan nesne koleksiyonları doldurma (LINQ) (C#)](./how-to-populate-object-collections-from-multiple-sources-linq.md)
