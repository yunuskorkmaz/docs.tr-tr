---
title: Birleştirme işlemleri (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 39ab4854-ac84-4738-9d0b-3cb79be84db4
ms.openlocfilehash: 6113949986aafdcaa2afa55d0a56d8e2186811b7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527867"
---
# <a name="join-operations-visual-basic"></a>Birleştirme işlemleri (Visual Basic)
A *birleştirme* iki veri kaynaklarının bir veri kaynağı nesneleri başka bir veri kaynağındaki ortak bir özniteliği paylaşan nesnelerle işbirliğidir.  
  
 Birleştirme, veri kaynakları birbirleriyle ilişkilerini doğrudan izlenemiyor hedef sorgularda önemli bir işlemdir. Bu, aşağıdakiler gibi modellenmiştir olmayan nesneler arasında bir bağıntı gelebilir nesne yönelimli programlama, geriye doğru tek yönlü bir ilişkinin yönü. Tek yönlü bir ilişkinin bir özellik türü şehri olan bir müşteri sınıf örneğidir ancak Şehir sınıfı müşteri nesnesi koleksiyonu bir özelliğe sahip değildir. Şehir nesnelerin bir listesini varsa ve tüm müşteriler, her şehirde bulmak istediğiniz bulmak için bir birleştirme işlemi'ni kullanabilirsiniz.  
  
 LINQ framework içinde sağlanan birleşim yöntemleri <xref:System.Linq.Enumerable.Join%2A> ve <xref:System.Linq.Enumerable.GroupJoin%2A>. Bu yöntemler equijoins ya da bunların anahtarların eşitlik bakımından göre iki veri kaynağı ile eşleşen birleştirmeler gerçekleştirin. (Transact-SQL destekler karşılaştırması için örneğin 'küçüktür' işleci 'equals' dışındaki operatörlere katılın.) İlişkisel veritabanı koşullarında <xref:System.Linq.Enumerable.Join%2A> uygulayan bir iç birleştirme, birleşim türü içinde yalnızca diğer veri kümesinde bir eşleşmeye sahip nesneler döndürülür. <xref:System.Linq.Enumerable.GroupJoin%2A> Yöntemi eşdeğeri yoktur doğrudan ilişkisel veritabanı bağlamında, ancak İç birleşimler sol dış birleştirmeler ve bir üst kümesi uygular. Diğer veri kaynağında ilişkili hiçbir öğe olsa bile bir sol dış birleşim ilk (soldaki) veri kaynağının her öğe döndüren bir birleştirme ' dir.  
  
 Aşağıdaki çizimde, iki ve öğeleri bir iç birleştirme veya bir sol dış birleşim dahil edilen bu kümeleri içinde kavramsal bir görünümü gösterir.  
  
 ![İç gösteren iki örtüşen daireler&#47;dış. ](../../../../csharp/programming-guide/concepts/linq/media/joincircles.png "JoinCircles")  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem adı|Açıklama|Visual Basic sorgu ifade sözdizimi|Daha fazla bilgi|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Birleştirme|Anahtar Seçici işlevlerine göre iki diziyi birleştirir ve değer çiftlerini ayıklar.|`From x In …, y In … Where x.a = y.a`<br /><br /> -veya-<br /><br /> `Join … [As …]In … On …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|GroupJoin|İki sıranın anahtar Seçici işlevleri ve grupları her öğe için sonuçlar temelinde birleştirir.|`Group Join … In … On …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq>
- [Standart sorgu işleçlerine genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Anonim Tipler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Birleşimler ve Çapraz Ürün Sorguları Düzenleme](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)
- [Join Yan Tümcesi](../../../../visual-basic/language-reference/queries/join-clause.md)
- [Nasıl yapılır: Dosyalardan içerik (LINQ) (Visual Basic) katılın](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md)
- [Nasıl yapılır: (LINQ) (Visual Basic) birden fazla kaynaktan nesne koleksiyonları doldurma](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)
