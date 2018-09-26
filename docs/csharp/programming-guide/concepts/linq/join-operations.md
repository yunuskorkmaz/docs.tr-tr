---
title: Birleştirme işlemleri (C#)
ms.date: 07/20/2015
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
ms.openlocfilehash: f03d5cf14525a6d23240747c2f377348bf608782
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47193063"
---
# <a name="join-operations-c"></a>Birleştirme işlemleri (C#)
A *birleştirme* iki veri kaynaklarının bir veri kaynağı nesneleri başka bir veri kaynağındaki ortak bir özniteliği paylaşan nesnelerle işbirliğidir.  
  
 Birleştirme, veri kaynakları birbirleriyle ilişkilerini doğrudan izlenemiyor hedef sorgularda önemli bir işlemdir. Bu, aşağıdakiler gibi modellenmiştir olmayan nesneler arasında bir bağıntı gelebilir nesne yönelimli programlama, geriye doğru tek yönlü bir ilişkinin yönü. Tek yönlü bir ilişkinin bir özellik türü şehri olan bir müşteri sınıf örneğidir ancak Şehir sınıfı müşteri nesnesi koleksiyonu bir özelliğe sahip değildir. Şehir nesnelerin bir listesini varsa ve tüm müşteriler, her şehirde bulmak istediğiniz bulmak için bir birleştirme işlemi'ni kullanabilirsiniz.  
  
 LINQ framework içinde sağlanan birleşim yöntemleri <xref:System.Linq.Enumerable.Join%2A> ve <xref:System.Linq.Enumerable.GroupJoin%2A>. Bu yöntemler equijoins ya da bunların anahtarların eşitlik bakımından göre iki veri kaynağı ile eşleşen birleştirmeler gerçekleştirin. (Transact-SQL destekler karşılaştırması için örneğin 'küçüktür' işleci 'equals' dışındaki operatörlere katılın.) İlişkisel veritabanı koşullarında <xref:System.Linq.Enumerable.Join%2A> uygulayan bir iç birleştirme, birleşim türü içinde yalnızca diğer veri kümesinde bir eşleşmeye sahip nesneler döndürülür. <xref:System.Linq.Enumerable.GroupJoin%2A> Yöntemi eşdeğeri yoktur doğrudan ilişkisel veritabanı bağlamında, ancak İç birleşimler sol dış birleştirmeler ve bir üst kümesi uygular. Diğer veri kaynağında ilişkili hiçbir öğe olsa bile bir sol dış birleşim ilk (soldaki) veri kaynağının her öğe döndüren bir birleştirme ' dir.  
  
 Aşağıdaki çizimde, iki ve öğeleri bir iç birleştirme veya bir sol dış birleşim dahil edilen bu kümeleri içinde kavramsal bir görünümü gösterir.  
  
 ![İç gösteren iki örtüşen daireler&#47;dış. ](../../../../csharp/programming-guide/concepts/linq/media/joincircles.png "JoinCircles")  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem adı|Açıklama|C# sorgu ifade sözdizimi|Daha fazla bilgi|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Birleştirme|Anahtar Seçici işlevlerine göre iki diziyi birleştirir ve değer çiftlerini ayıklar.|`join … in … on … equals …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|GroupJoin|İki sıranın anahtar Seçici işlevleri ve grupları her öğe için sonuçlar temelinde birleştirir.|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.Linq>  
- [Standart sorgu işleçlerine genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
- [Anonim Tipler](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
- [Birleşimler ve Çapraz Ürün Sorguları Düzenleme](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)  
- [join yan tümcesi](../../../../csharp/language-reference/keywords/join-clause.md)  
- [Nasıl yapılır: bileşik anahtarlar kullanarak birleştirme](../../../../csharp/programming-guide/linq-query-expressions/how-to-join-by-using-composite-keys.md)  
- [Nasıl yapılır: birleştirme dosyalardan içerik (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md)  
- [Nasıl yapılır: Join tümcesinin sonuçlarını sıralama](../../../../csharp/programming-guide/linq-query-expressions/how-to-order-the-results-of-a-join-clause.md)  
- [Nasıl yapılır: özel birleştirme işlemleri gerçekleştirme](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-custom-join-operations.md)  
- [Nasıl yapılır: gruplandırılmış birleştirmeler gerçekleştirme](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md)  
- [Nasıl yapılır: iç birleştirmeler gerçekleştirme](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md)  
- [Nasıl yapılır: sol dış birleştirmeler gerçekleştirme](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-left-outer-joins.md)  
- [Nasıl yapılır: (LINQ) (C#) birden fazla kaynaktan nesne koleksiyonları doldurma](../../../../csharp/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)
