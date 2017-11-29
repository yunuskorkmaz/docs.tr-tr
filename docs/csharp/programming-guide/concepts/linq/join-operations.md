---
title: "Birleştirme işlemleri (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 158d035985dae0d1c1daf0f276a9df7b913f2263
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="join-operations-c"></a>Birleştirme işlemleri (C#)
A *birleştirme* iki veri kaynağının bir veri kaynağındaki nesneleri başka bir veri kaynağındaki ortak bir özniteliği paylaşan nesnelerle ilişkidir.  
  
 Birleştirme ilişkilerini birbirleriyle doğrudan izlenemiyor veri kaynakları hedef sorgularda önemli bir işlemdir. Nesne odaklı programlama, bu, aşağıdaki gibi modellenir olmayan nesneler arasında bir ilişki anlamına gelebilir geriye doğru tek yönlü bir ilişkinin yönü. Tek yönlü bir ilişkinin Şehir türünde bir özellik olan bir müşteri sınıfı örneğidir ancak Şehir sınıfı müşteri nesneler koleksiyonunun bir özellik içermiyor. Şehir nesnelerin bir listesini varsa ve her şehirde tüm müşteriler bulmak istediğiniz, bunları bulmak için bir birleştirme işlemi'ni kullanabilirsiniz.  
  
 LINQ Framework'te sağlanan birleşim yöntemleri <xref:System.Linq.Enumerable.Join%2A> ve <xref:System.Linq.Enumerable.GroupJoin%2A>. Bu yöntemler equijoins veya eşleşen iki veri kaynağı kendi anahtarları eşitlik bakımından tabanlı birleşimler gerçekleştirin. (Transact-SQL destekler karşılaştırma için örneğin 'değerinden' işleci 'eşittir' dışındaki operatörlere katılın.) İlişkisel veritabanı terimleriyle <xref:System.Linq.Enumerable.Join%2A> birleşim türü bir iç birleştirme uygular, diğer veri kümesindeki bir eşleşme olan nesneler döndürülür içinde. <xref:System.Linq.Enumerable.GroupJoin%2A> Yöntemi doğrudan bir eşdeğer ilişkisel veritabanı bağlamında olsa da, bir üst İç birleşimler sol dış birleştirmeler ve uygular. Diğer veri kaynağında ilişkili öğe sahip olsa bile bir sol dış birleşim ilk (soldaki) veri kaynağının her öğe döndüren bir birleşim ' dir.  
  
 Aşağıdaki çizimde iki kümesi ve bir iç birleştirme veya sol dış birleşim dahil bu kümeleri içinde öğelerin kavramsal görünümünü gösterir.  
  
 ![İç &#47; gösteren iki çakışan daireye dış. ] (../../../../csharp/programming-guide/concepts/linq/media/joincircles.png "JoinCircles")  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem adı|Açıklama|C# sorgu ifade sözdizimi|Daha Fazla Bilgi|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Birleştirme|Anahtar Seçici işlevlerini tabanlı iki sıraları birleştirir ve değer çiftlerini ayıklar.|`join … in … on … equals …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|GroupJoin|İki sıraları anahtar Seçici işlevleri ve grupları her öğe için sonuçta elde edilen eşleşen temelinde birleştirir.|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Linq>  
 [Standart sorgu işleçlerine genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Anonim türler](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
 [Birleştirmeler ve çapraz ürün sorgularını düzenleme](http://msdn.microsoft.com/library/d8072ede-0521-4670-9bec-1778ceeb875b)  
 [Join tümcesi](../../../../csharp/language-reference/keywords/join-clause.md)  
 [Nasıl yapılır: bileşik anahtarlar kullanarak birleştirme](../../../../csharp/programming-guide/linq-query-expressions/how-to-join-by-using-composite-keys.md)  
 [Nasıl yapılır: (LINQ) (C#) farklı dosyalardan içerik birleştirme](../../../../csharp/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md)  
 [Nasıl yapılır: Join tümcesinin sonuçlarını sıralama](../../../../csharp/programming-guide/linq-query-expressions/how-to-order-the-results-of-a-join-clause.md)  
 [Nasıl yapılır: özel birleştirme işlemleri gerçekleştirme](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-custom-join-operations.md)  
 [Nasıl yapılır: gruplandırılmış birleştirmeler gerçekleştirme](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md)  
 [Nasıl yapılır: iç birleştirmeler gerçekleştirme](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md)  
 [Nasıl yapılır: sol dış birleştirmeler gerçekleştirme](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-left-outer-joins.md)  
 [Nasıl yapılır: (LINQ) (C#) birden fazla kaynaktan nesne koleksiyonları doldurma](../../../../csharp/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)
