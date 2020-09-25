---
title: DataRow 'ı karşılaştırma (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8fe0eadf-297b-487c-8d4b-7816753c2883
ms.openlocfilehash: 8cce52734c83e42312d71806d4151ef21e4df0ba
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203806"
---
# <a name="comparing-datarows-linq-to-dataset"></a>DataRow 'ı karşılaştırma (LINQ to DataSet)

Dil ile tümleşik sorgu (LINQ), eşit olup olmadığını görmek için kaynak öğeleri karşılaştırmak üzere çeşitli küme işleçlerini tanımlar. LINQ aşağıdaki set işleçlerini sağlar:  
  
- <xref:System.Linq.Enumerable.Distinct%2A>  
  
- <xref:System.Linq.Enumerable.Union%2A>  
  
- <xref:System.Linq.Enumerable.Intersect%2A>  
  
- <xref:System.Linq.Enumerable.Except%2A>  
  
 Bu işleçler, <xref:System.Collections.Generic.IEqualityComparer%601.GetHashCode%2A> her öğe koleksiyonunda ve yöntemlerini çağırarak kaynak öğeleri karşılaştırır <xref:System.Collections.Generic.IEqualityComparer%601.Equals%2A> . A durumunda <xref:System.Data.DataRow> , bu işleçler, tablo verileri üzerinden ayarlama işlemlerine yönelik ideal davranış olmayan bir başvuru karşılaştırması gerçekleştirir. Ayarlanan işlemler için, genellikle öğe değerlerinin öğe başvurularına eşit olup olmadığını belirlemektir. Bu nedenle, <xref:System.Data.DataRowComparer> sınıfı LINQ to DataSet eklenmiştir. Bu sınıf, satır değerlerini karşılaştırmak için kullanılabilir.  
  
 <xref:System.Data.DataRowComparer>Sınıfı için bir değer karşılaştırma uygulamasını içerir <xref:System.Data.DataRow> , bu nedenle bu sınıf gibi ayarlama işlemleri için kullanılabilir <xref:System.Linq.Enumerable.Distinct%2A> . Bu sınıf doğrudan başlatılamaz; Bunun yerine, <xref:System.Data.DataRowComparer.Default%2A> özelliğinin bir örneğini döndürmek için kullanılması gerekir <xref:System.Data.DataRowComparer%601> . <xref:System.Data.DataRowComparer%601.Equals%2A>Daha sonra yöntemi çağrılır ve <xref:System.Data.DataRow> Karşılaştırılacak iki nesne giriş parametresi olarak geçirilir. <xref:System.Data.DataRowComparer%601.Equals%2A>Yöntemi, `true` her iki nesnede sıralı sütun değeri kümesi eşitse döndürür <xref:System.Data.DataRow> ; Aksi takdirde, `false` .  
  
## <a name="example"></a>Örnek  

 Bu örnek `Intersect` , her iki tabloda görünen kişileri döndürmek için kullanır.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
### <a name="example"></a>Örnek  

 Aşağıdaki örnek iki satırı karşılaştırır ve karma kodlarını alır.  
  
 [!code-vb[DP LINQ to DataSet Examples#CompareDifferentRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#comparedifferentrows)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataRowComparer>
- [DataSet’e Veri Yükleme](loading-data-into-a-dataset.md)
- [LINQ to DataSet Örnekleri](linq-to-dataset-examples.md)
