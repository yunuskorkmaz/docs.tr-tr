---
title: (LINQ to DataSet) DataRow karşılaştırma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8fe0eadf-297b-487c-8d4b-7816753c2883
ms.openlocfilehash: 2b45a4629474c394c8e49c41a7a98fc1181e124b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59077179"
---
# <a name="comparing-datarows-linq-to-dataset"></a>(LINQ to DataSet) DataRow karşılaştırma
[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] eşit olup olmadığını görmek için kaynak öğeleri karşılaştırmak için çeşitli küme işleci tanımlar. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] Aşağıdaki işleçler kümesi sağlar:  
  
-   <xref:System.Linq.Enumerable.Distinct%2A>  
  
-   <xref:System.Linq.Enumerable.Union%2A>  
  
-   <xref:System.Linq.Enumerable.Intersect%2A>  
  
-   <xref:System.Linq.Enumerable.Except%2A>  
  
 Bu işleçler çağırarak kaynak öğeleri karşılaştırma <xref:System.Collections.Generic.IEqualityComparer%601.GetHashCode%2A> ve <xref:System.Collections.Generic.IEqualityComparer%601.Equals%2A> öğelerinin her koleksiyonu yöntemleri. Durumunda, bir <xref:System.Data.DataRow>, genellikle ayarlama işlemleri için ideal davranışı sekmeli veriler üzerinde değil, bir başvuru karşılaştırması, bu işleçler gerçekleştirin. Ayarlama işlemleri için genellikle öğe değerlerini eşit olup olmadığı ve öğesi başvuruları belirlemek istersiniz. Bu nedenle, <xref:System.Data.DataRowComparer> sınıfı eklendi [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]. Bu sınıf, satır değerlerini karşılaştırmak için kullanılabilir.  
  
 <xref:System.Data.DataRowComparer> Sınıfı içeren bir değer karşılaştırma uygulaması <xref:System.Data.DataRow>, böylece bu sınıf kümesi işlemleri için aşağıdaki gibi kullanılabilir <xref:System.Linq.Enumerable.Distinct%2A>. Bu sınıf doğrudan oluşturulamaz; Bunun yerine, <xref:System.Data.DataRowComparer.Default%2A> özelliği örneği döndürmek için kullanılması gereken <xref:System.Data.DataRowComparer%601>. <xref:System.Data.DataRowComparer%601.Equals%2A> Yöntemi çağrıldıktan sonra ve iki <xref:System.Data.DataRow> Karşılaştırılacak nesne içinde giriş parametre olarak geçirilir. <xref:System.Data.DataRowComparer%601.Equals%2A> Yöntemi döndürür `true` sütun kümesini hem de değerleri, <xref:System.Data.DataRow> nesneler eşit; Aksi takdirde `false`.  
  
## <a name="example"></a>Örnek  
 Bu örnekte `Intersect` her iki tabloda görünen kişileri dönün.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, iki satır karşılaştırır ve karma kodlarını alır.  
  
 [!code-vb[DP LINQ to DataSet Examples#CompareDifferentRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#comparedifferentrows)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataRowComparer>
- [DataSet’e Veri Yükleme](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [LINQ to DataSet Örnekleri](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
