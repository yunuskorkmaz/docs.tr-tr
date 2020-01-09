---
title: Çapraz tablo sorguları (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6819a16f-8656-41af-a54d-dfec0cb66366
ms.openlocfilehash: 8f9a538482580134fa876866dfe394c3dfc7de2a
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634891"
---
# <a name="cross-table-queries-linq-to-dataset"></a>Çapraz tablo sorguları (LINQ to DataSet)
Tek bir tabloyu sorgulamaya ek olarak, LINQ to DataSet çapraz tablo sorguları da gerçekleştirebilirsiniz. Bu, bir *JOIN*kullanılarak yapılır. Bir JOIN, bir ürün veya kişi KIMLIĞI gibi başka bir veri kaynağında ortak bir özniteliği paylaşan nesneler ile tek bir veri kaynağındaki nesnelerin ilişkilendirmesidir. Nesne odaklı programlamada, nesneler arasındaki ilişkilerin, her nesne başka bir nesneye başvuran bir üyeye sahip olduğundan, kolayca gezinilmesi oldukça kolaydır. Öte yandan, dış veritabanı tablolarında, ilişkilerde gezinmek doğrudan değildir. Veritabanı tabloları yerleşik ilişkiler içermez. Bu gibi durumlarda, her kaynaktaki öğeleri eşleştirmek için JOIN işlemi kullanılabilir. Örneğin, ürün bilgilerini ve satış bilgilerini içeren iki tablo verildiğinde, satış bilgilerini ve ürünleri aynı satış siparişi için eşleştirmek üzere bir JOIN işlemi kullanabilirsiniz.  
  
 Dil ile tümleşik sorgu (LINQ) çerçevesi, <xref:System.Linq.Enumerable.Join%2A> ve <xref:System.Linq.Enumerable.GroupJoin%2A>iki JOIN işleci sağlar. Bu işleçler *eş birleştirme*gerçekleştirir: diğer bir deyişle, yalnızca anahtarları eşitse iki veri kaynağıyla eşleşen birleşimler. (Bunun aksine, Transact-SQL, `less than` işleci gibi `equals`dışında, JOIN işleçlerini destekler.)  
  
 İlişkisel veritabanı koşullarında <xref:System.Linq.Enumerable.Join%2A> bir iç birleşim uygular. Bir iç birleşim, yalnızca karşıt veri kümesinde eşleşme olan nesnelerin döndürüldüğü bir tür birleşimdir.  
  
 <xref:System.Linq.Enumerable.GroupJoin%2A> işleçlerinde, ilişkisel veritabanı koşullarında doğrudan eşdeğer olmaz; Bunlar, İç birleştirmeler ve sol dış birleştirmeler için bir üst küme uygular. Sol dış birleşim, ikinci koleksiyonda bağıntılı bir öğesi olmasa bile, ilk (sol) koleksiyonun her bir öğesini döndüren birleşimdir.  
  
 Birleşimler hakkında daha fazla bilgi için bkz. [birleştirme işlemleri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb397908(v=vs.120)).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Ağustos ayının ayına ait çevrimiçi siparişleri almak için AdventureWorks örnek veritabanından `SalesOrderHeader` ve `SalesOrderDetail` tablolarının geleneksel bir birleştirmesini gerçekleştirir.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#join)]
 [!code-vb[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataSet’leri Sorgulama](querying-datasets-linq-to-dataset.md)
- [Tek Tablolu Sorgular](single-table-queries-linq-to-dataset.md)
- [Türü Belirtilmiş DataSet’leri Sorgulama](querying-typed-datasets.md)
- [Birleştirme İşlemleri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb397908(v=vs.120))
- [LINQ to DataSet Örnekleri](linq-to-dataset-examples.md)
