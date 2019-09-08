---
title: DataRow 'ı karşılaştırma (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8fe0eadf-297b-487c-8d4b-7816753c2883
ms.openlocfilehash: 30a782f5e37e867c7a0e4dfd800f4b2c2836d070
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784932"
---
# <a name="comparing-datarows-linq-to-dataset"></a>DataRow 'ı karşılaştırma (LINQ to DataSet)
[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]eşit olup olmadığını görmek için kaynak öğeleri karşılaştırmak üzere çeşitli küme işleçlerini tanımlar. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]aşağıdaki küme işleçlerini sağlar:  
  
- <xref:System.Linq.Enumerable.Distinct%2A>  
  
- <xref:System.Linq.Enumerable.Union%2A>  
  
- <xref:System.Linq.Enumerable.Intersect%2A>  
  
- <xref:System.Linq.Enumerable.Except%2A>  
  
 Bu işleçler, <xref:System.Collections.Generic.IEqualityComparer%601.GetHashCode%2A> her öğe koleksiyonunda ve <xref:System.Collections.Generic.IEqualityComparer%601.Equals%2A> yöntemlerini çağırarak kaynak öğeleri karşılaştırır. A <xref:System.Data.DataRow>durumunda, bu işleçler, tablo verileri üzerinden ayarlama işlemlerine yönelik ideal davranış olmayan bir başvuru karşılaştırması gerçekleştirir. Ayarlanan işlemler için, genellikle öğe değerlerinin öğe başvurularına eşit olup olmadığını belirlemektir. Bu nedenle, <xref:System.Data.DataRowComparer> sınıfı LINQ to DataSet eklenmiştir. Bu sınıf, satır değerlerini karşılaştırmak için kullanılabilir.  
  
 Sınıfı için <xref:System.Data.DataRow>bir değer karşılaştırma uygulamasını içerir, bu nedenle bu sınıf gibi <xref:System.Linq.Enumerable.Distinct%2A>ayarlama işlemleri için kullanılabilir. <xref:System.Data.DataRowComparer> Bu sınıf doğrudan başlatılamaz; Bunun yerine, <xref:System.Data.DataRowComparer%601>özelliğinin bir örneğini döndürmek için kullanılması gerekir. <xref:System.Data.DataRowComparer.Default%2A> Daha sonra <xref:System.Data.DataRow> yöntemi çağrılır ve Karşılaştırılacak iki nesne giriş parametresi olarak geçirilir. <xref:System.Data.DataRowComparer%601.Equals%2A> Yöntemi, her `true` iki <xref:System.Data.DataRow> nesnede sıralı sütun değeri kümesi eşitse döndürür; Aksi takdirde, `false`. <xref:System.Data.DataRowComparer%601.Equals%2A>  
  
## <a name="example"></a>Örnek  
 Bu örnek, `Intersect` her iki tabloda görünen kişileri döndürmek için kullanır.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek iki satırı karşılaştırır ve karma kodlarını alır.  
  
 [!code-vb[DP LINQ to DataSet Examples#CompareDifferentRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#comparedifferentrows)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataRowComparer>
- [DataSet’e Veri Yükleme](loading-data-into-a-dataset.md)
- [LINQ to DataSet Örnekleri](linq-to-dataset-examples.md)
