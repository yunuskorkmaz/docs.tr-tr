---
title: Joinİşlemler (C#)
ms.date: 07/20/2015
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
no-loc:
- Join
- GroupJoin
ms.openlocfilehash: 6e2ec1a0c8120f6869b7c0a196b77d118762a8dd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76868011"
---
# <a name="join-operations-c"></a>İşleme Katılma (C#)

İki veri kaynağının *birleştirilmesi,* bir veri kaynağındaki nesnelerin başka bir veri kaynağında ortak bir özniteliği paylaşan nesnelerle ilişkilendirilmesidir.  
  
 Birleştirme, birbirleriyle ilişkileri doğrudan izlenemeyen veri kaynaklarını hedefleyen sorgularda önemli bir işlemdir. Nesne yönelimli programlamada, bu, tek yönlü bir ilişkinin geriye doğru yönü gibi modellenmemiş nesneler arasında bir ilişki anlamına gelebilir. Tek yönlü bir ilişkinin bir örneği, Şehir türü özelliğine sahip bir Müşteri sınıfıdır, ancak Şehir sınıfının Müşteri nesneleri koleksiyonu olan bir özelliği yoktur. Şehir nesnelerinin bir listesi varsa ve her şehirdeki tüm müşterileri bulmak istiyorsanız, bunları bulmak için bir birleştirme işlemi kullanabilirsiniz.  
  
 LINQ çerçevesinde sağlanan birleştirme yöntemleri <xref:System.Linq.Enumerable.Join%2A> <xref:System.Linq.Enumerable.GroupJoin%2A>ve . Bu yöntemler, anahtarlarının eşitliğini temel alan iki veri kaynağıyla eşleşen equijoins gerçekleştirir veya birleştirir. (Karşılaştırma için, Transact-SQL 'eşittir' dışında birleştirme işleçleri destekler, örneğin 'daha az' işleci.) İlişkisel veritabanı terimlerinde, <xref:System.Linq.Enumerable.Join%2A> yalnızca diğer veri kümesinde eşleşmesi olan nesnelerin döndürüldildiği bir iç birleştirme türü uygular. Yöntem <xref:System.Linq.Enumerable.GroupJoin%2A> ilişkisel veritabanı açısından doğrudan eşdeğeri yoktur, ancak iç birleştirmeler ve sol dış birleştirmeler bir süper kümesi uygular. Sol dış birleştirme, diğer veri kaynağında ilişkili öğe olmasa bile, ilk (sol) veri kaynağının her öğesini döndüren bir birleştirmedir.  
  
 Aşağıdaki resimde, iki kümenin kavramsal görünümü ve bu kümeler içindeki iç birleştirme veya sol dış birleştirmede yer alan öğeler gösterilmektedir.  
  
 ![İç&#47;gösteren iki çakışan daire.](./media/join-operations/join-method-overlapping-circles.png)  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem Adı|Açıklama|C# Sorgu İfade Sözdizimi|Daha Fazla Bilgi|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Join|Anahtar seçici işlevlerine dayalı iki diziyi birleştirir ve değer çiftlerini ayıklar.|`join … in … on … equals …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|GroupJoin|Anahtar seçici işlevlerine dayalı iki diziyi birleştirir ve her öğe için elde edilen eşleşmeleri gruplandırmaz.|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Sorgu ifade sözdizimi örnekleri
  
### Join  
  
Aşağıdaki örnek, `join … in … on … equals …` belirli bir değere dayalı iki diziyi birleştirmek için yan tümceyi kullanır:
  
[!code-csharp[Join](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQJoinOperation/CS/JoinOperation.cs#Join)]  

### GroupJoin  

Aşağıdaki örnek, `join … in … on … equals … into …` belirli bir değere dayalı iki diziyi birleştirmek için yan tümceyi kullanır ve her öğe için elde edilen eşleşmeleri gruplar:
  
[!code-csharp[GroupJoin](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQJoinOperation/CS/JoinOperation.cs#GroupJoin)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq>
- [Standart Sorgu Operatörlerine Genel Bakış (C#)](./standard-query-operators-overview.md)
- [Anonim Türler](../../classes-and-structs/anonymous-types.md)
- [Birleşimler ve Çapraz Ürün Sorguları Düzenleme](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)
- [birleştirme yan tümcesi](../../../language-reference/keywords/join-clause.md)
- [Joinkompozit tuşlar kullanarak](../../../linq/join-by-using-composite-keys.md)
- [Farklı dosyalardan (LINQ) (C#) içerik birleştirme](./how-to-join-content-from-dissimilar-files-linq.md)
- [Join yan tümcesinin sonuçlarını sıralama](../../../linq/order-the-results-of-a-join-clause.md)
- [Özel birleştirme işlemleri gerçekleştirme](../../../linq/perform-custom-join-operations.md)
- [Gruplanmış birleşimler gerçekleştirme](../../../linq/perform-grouped-joins.md)
- [İç birleşimler gerçekleştirme](../../../linq/perform-inner-joins.md)
- [Sol dış birleşimler gerçekleştirme](../../../linq/perform-left-outer-joins.md)
- [Nesne koleksiyonları birden çok kaynaktan (LINQ) (C#) doldurma](./how-to-populate-object-collections-from-multiple-sources-linq.md)
