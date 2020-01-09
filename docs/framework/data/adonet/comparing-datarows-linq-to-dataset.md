---
title: DataRow 'ı karşılaştırma (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8fe0eadf-297b-487c-8d4b-7816753c2883
ms.openlocfilehash: fbd642fb3da6d664df9076b8d7576865d516727e
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634904"
---
# <a name="comparing-datarows-linq-to-dataset"></a>DataRow 'ı karşılaştırma (LINQ to DataSet)
Dil ile tümleşik sorgu (LINQ), eşit olup olmadığını görmek için kaynak öğeleri karşılaştırmak üzere çeşitli küme işleçlerini tanımlar. LINQ aşağıdaki set işleçlerini sağlar:  
  
- <xref:System.Linq.Enumerable.Distinct%2A>  
  
- <xref:System.Linq.Enumerable.Union%2A>  
  
- <xref:System.Linq.Enumerable.Intersect%2A>  
  
- <xref:System.Linq.Enumerable.Except%2A>  
  
 Bu işleçler, her öğe koleksiyonunda <xref:System.Collections.Generic.IEqualityComparer%601.GetHashCode%2A> ve <xref:System.Collections.Generic.IEqualityComparer%601.Equals%2A> yöntemlerini çağırarak kaynak öğeleri karşılaştırır. <xref:System.Data.DataRow>söz konusu olduğunda, bu işleçler, tablo verileri üzerinden ayarlama işlemlerine yönelik ideal davranış olmayan bir başvuru karşılaştırması gerçekleştirir. Ayarlanan işlemler için, genellikle öğe değerlerinin öğe başvurularına eşit olup olmadığını belirlemektir. Bu nedenle, <xref:System.Data.DataRowComparer> sınıfı LINQ to DataSet eklenmiştir. Bu sınıf, satır değerlerini karşılaştırmak için kullanılabilir.  
  
 <xref:System.Data.DataRowComparer> sınıfı, <xref:System.Data.DataRow>için bir değer karşılaştırma uygulamasını içerir, bu nedenle bu sınıf <xref:System.Linq.Enumerable.Distinct%2A>gibi ayarlama işlemleri için kullanılabilir. Bu sınıf doğrudan başlatılamaz; Bunun yerine, <xref:System.Data.DataRowComparer.Default%2A> özelliği, <xref:System.Data.DataRowComparer%601>örneğini döndürmek için kullanılmalıdır. <xref:System.Data.DataRowComparer%601.Equals%2A> yöntemi daha sonra çağrılır ve Karşılaştırılacak iki <xref:System.Data.DataRow> nesnesi giriş parametresi olarak geçirilir. <xref:System.Data.DataRowComparer%601.Equals%2A> yöntemi, her iki <xref:System.Data.DataRow> nesnelerinde sıralı sütun değerleri kümesi eşitse `true` döndürür; Aksi takdirde, `false`.  
  
## <a name="example"></a>Örnek  
 Bu örnek, her iki tabloda görünen kişileri döndürmek için `Intersect` kullanır.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek iki satırı karşılaştırır ve karma kodlarını alır.  
  
 [!code-vb[DP LINQ to DataSet Examples#CompareDifferentRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#comparedifferentrows)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataRowComparer>
- [DataSet’e Veri Yükleme](loading-data-into-a-dataset.md)
- [LINQ to DataSet Örnekleri](linq-to-dataset-examples.md)
