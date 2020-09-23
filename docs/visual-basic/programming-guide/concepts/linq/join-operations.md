---
title: Birleştirme İşlemleri
ms.date: 07/20/2015
ms.assetid: 39ab4854-ac84-4738-9d0b-3cb79be84db4
ms.openlocfilehash: e69e060447c0103c3c47be0fb34cad90e88c4516
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077325"
---
# <a name="join-operations-visual-basic"></a>JOIN Işlemleri (Visual Basic)

İki veri kaynağının *birleşimi* , bir veri kaynağındaki nesnelerin, başka bir veri kaynağında ortak bir özniteliği paylaşan nesnelerle ilişkilendirilmesi.  
  
 Birleştirme, birbirleriyle ilişkilerini hedefleyen veri kaynaklarını hedef alan sorgularda önemli bir işlemdir. Nesne odaklı programlamada bu, tek yönlü bir ilişkinin geriye doğru yönü gibi Modellenmemiş nesneler arasındaki bir bağıntı anlamına gelebilir. Tek yönlü ilişki örneği, şehir türünde bir özelliği olan bir müşteri sınıfıdır, ancak City sınıfı, müşteri nesnelerinin bir koleksiyonu olan bir özelliğine sahip değildir. Bir şehir nesneleri listeniz varsa ve her bir şehirde tüm müşterileri bulmak istiyorsanız, bunları bulmak için bir JOIN işlemi kullanabilirsiniz.  
  
 LINQ çerçevesinde sunulan JOIN yöntemleri <xref:System.Linq.Enumerable.Join%2A> ve ' dir <xref:System.Linq.Enumerable.GroupJoin%2A> . Bu yöntemler, anahtarlarının eşitliğine göre iki veri kaynağıyla eşleşen eş birleştirmeleri veya birleştirmeleri gerçekleştirir. (Karşılaştırma için Transact-SQL ' Equals ' dışındaki bir JOIN işleçlerini destekler, örneğin ' küçüktür ' işleci.) İlişkisel veritabanı koşullarında, bir <xref:System.Linq.Enumerable.Join%2A> iç birleşim ve yalnızca diğer veri kümesinde eşleşme olan nesnelerin döndürüldüğü bir birleşim türü uygular. <xref:System.Linq.Enumerable.GroupJoin%2A>Metodun ilişkisel veritabanı terimlerinde doğrudan eşdeğeri yoktur, ancak iç birleştirmeler ve sol dış birleştirmeler üst kümesini uygular. Sol dış birleşim, diğer veri kaynağında bağıntılı bir öğesi olmasa bile, ilk (soldaki) veri kaynağının her bir öğesini döndüren birleşimdir.  
  
 Aşağıdaki çizimde, iki kümenin kavramsal görünümü ve bu kümeler içindeki öğelerin bir iç birleşime veya bir sol dış birleşime dahil olduğu gösterilmektedir.  
  
 ![İç&#47;dıştaki gösteren iki çakışan daire.](./media/join-operations/join-method-overlapping-circles.png)  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem adı|Description|Sorgu Ifadesi söz dizimini Visual Basic|Daha Fazla Bilgi|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Birleştir|Anahtar Seçici işlevlerine göre iki diziyi birleştirir ve değer çiftlerini ayıklar.|`From x In …, y In … Where x.a = y.a`<br /><br /> -veya-<br /><br /> `Join … [As …]In … On …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|GroupJoin|Anahtar Seçici işlevlerine göre iki diziyi birleştirir ve her öğe için elde edilen eşleşmeleri gruplandırır.|`Group Join … In … On …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq>
- [Standart sorgu Işleçlerine genel bakış (Visual Basic)](standard-query-operators-overview.md)
- [Anonim Türler](../../language-features/objects-and-classes/anonymous-types.md)
- [Birleşimler ve Çapraz Ürün Sorguları Düzenleme](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)
- [JOIN yan tümcesi](../../../language-reference/queries/join-clause.md)
- [Nasıl yapılır: farklı dosyalardan Içerik ekleme (LINQ) (Visual Basic)](how-to-join-content-from-dissimilar-files-linq.md)
- [Nasıl yapılır: birden çok kaynaktan nesne koleksiyonları doldurma (LINQ) (Visual Basic)](how-to-populate-object-collections-from-multiple-sources-linq.md)
