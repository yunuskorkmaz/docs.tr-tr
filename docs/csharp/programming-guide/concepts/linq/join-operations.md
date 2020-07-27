---
title: :::no-loc(Join):::İşlemler (C#)
description: İki veri kaynağı birleşimi, nesneleri veri kaynakları genelinde bir özniteliği paylaşan nesnelerle ilişkilendirir. C# ' de LINQ çerçevesindeki JOIN yöntemleri hakkında bilgi edinin.
ms.date: 07/20/2015
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
no-loc:
- ':::no-loc(Join):::'
- ':::no-loc(GroupJoin):::'
ms.openlocfilehash: 1b453f1752edf0cc126f8e27dbdd9e91ad9143f3
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165695"
---
# <a name="no-locjoin-operations-c"></a>:::no-loc(Join):::İşlemler (C#)

İki veri kaynağının *birleşimi* , bir veri kaynağındaki nesnelerin, başka bir veri kaynağında ortak bir özniteliği paylaşan nesnelerle ilişkilendirilmesi.  
  
 :::no-loc(Join):::oluşturma, birbirleriyle ilişkilerini hedefleyen veri kaynaklarını hedef alan sorgularda önemli bir işlemdir. Nesne odaklı programlamada bu, tek yönlü bir ilişkinin geriye doğru yönü gibi Modellenmemiş nesneler arasındaki bir bağıntı anlamına gelebilir. Tek yönlü ilişki örneği, şehir türünde bir özelliği olan bir müşteri sınıfıdır, ancak City sınıfı, müşteri nesnelerinin bir koleksiyonu olan bir özelliğine sahip değildir. Bir şehir nesneleri listeniz varsa ve her bir şehirde tüm müşterileri bulmak istiyorsanız, bunları bulmak için bir JOIN işlemi kullanabilirsiniz.  
  
 LINQ çerçevesinde sunulan JOIN yöntemleri <xref:System.Linq.Enumerable.:::no-loc(Join):::%2A> ve ' dir <xref:System.Linq.Enumerable.:::no-loc(GroupJoin):::%2A> . Bu yöntemler, anahtarlarının eşitliğine göre iki veri kaynağıyla eşleşen eş birleştirmeleri veya birleştirmeleri gerçekleştirir. (Karşılaştırma için Transact-SQL ' Equals ' dışındaki bir JOIN işleçlerini destekler, örneğin ' küçüktür ' işleci.) İlişkisel veritabanı koşullarında, bir <xref:System.Linq.Enumerable.:::no-loc(Join):::%2A> iç birleşim ve yalnızca diğer veri kümesinde eşleşme olan nesnelerin döndürüldüğü bir birleşim türü uygular. <xref:System.Linq.Enumerable.:::no-loc(GroupJoin):::%2A>Metodun ilişkisel veritabanı terimlerinde doğrudan eşdeğeri yoktur, ancak iç birleştirmeler ve sol dış birleştirmeler üst kümesini uygular. Sol dış birleşim, diğer veri kaynağında bağıntılı bir öğesi olmasa bile, ilk (soldaki) veri kaynağının her bir öğesini döndüren birleşimdir.  
  
 Aşağıdaki çizimde, iki kümenin kavramsal görünümü ve bu kümeler içindeki öğelerin bir iç birleşime veya bir sol dış birleşime dahil olduğu gösterilmektedir.  
  
 ![İç&#47;dıştaki gösteren iki çakışan daire.](./media/join-operations/join-method-overlapping-circles.png)  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem adı|Açıklama|C# sorgu Ifadesi sözdizimi|Daha Fazla Bilgi|  
|-----------------|-----------------|---------------------------------|----------------------|  
|:::no-loc(Join):::|:::no-loc(Join):::anahtar Seçici işlevlerine dayanan ve değer çiftlerini çıkaran iki sıra.|`join … in … on … equals …`|<xref:System.Linq.Enumerable.:::no-loc(Join):::%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.:::no-loc(Join):::%2A?displayProperty=nameWithType>|  
|:::no-loc(GroupJoin):::|:::no-loc(Join):::iki sıra, anahtar Seçici işlevlerine dayalıdır ve her öğe için elde edilen eşleşmeleri gruplandırır.|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.:::no-loc(GroupJoin):::%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.:::no-loc(GroupJoin):::%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Sorgu ifadesi söz dizimi örnekleri
  
### :::no-loc(Join):::  
  
Aşağıdaki örnek, belirli bir `join … in … on … equals …` değere göre iki diziyi birleştirmek için yan tümcesini kullanır:
  
[!code-csharp[:::no-loc(Join):::](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQ:::no-loc(Join):::Operation/CS/:::no-loc(Join):::Operation.cs#:::no-loc(Join):::)]  

### :::no-loc(GroupJoin):::  

Aşağıdaki örnek, belirli bir `join … in … on … equals … into …` değere göre iki diziyi birleştirmek için yan tümcesini kullanır ve her öğe için elde edilen eşleşmeleri gruplandırır:
  
[!code-csharp[:::no-loc(GroupJoin):::](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQ:::no-loc(Join):::Operation/CS/:::no-loc(Join):::Operation.cs#:::no-loc(GroupJoin):::)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq>
- [Standart sorgu Işleçlerine genel bakış (C#)](./standard-query-operators-overview.md)
- [Anonim Türler](../../classes-and-structs/anonymous-types.md)
- [:::no-loc(Join):::Ve çoklu ürün sorgularını formüller](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)
- [join tümcesi](../../../language-reference/keywords/join-clause.md)
- [:::no-loc(Join):::bileşik anahtarlar kullanarak](../../../linq/join-by-using-composite-keys.md)
- [Benzer olmayan dosyalardaki (LINQ) içerik ekleme (C#)](./how-to-join-content-from-dissimilar-files-linq.md)
- [Join yan tümcesinin sonuçlarını sıralama](../../../linq/order-the-results-of-a-join-clause.md)
- [Özel birleştirme işlemleri gerçekleştirme](../../../linq/perform-custom-join-operations.md)
- [Gruplanmış birleşimler gerçekleştirme](../../../linq/perform-grouped-joins.md)
- [İç birleşimler gerçekleştirme](../../../linq/perform-inner-joins.md)
- [Sol dış birleşimler gerçekleştirme](../../../linq/perform-left-outer-joins.md)
- [Birden çok kaynaktan nesne koleksiyonlarını doldurma (LINQ) (C#)](./how-to-populate-object-collections-from-multiple-sources-linq.md)
