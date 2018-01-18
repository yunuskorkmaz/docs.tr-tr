---
title: "DataRow (LINQ-DataSet) karşılaştırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 8fe0eadf-297b-487c-8d4b-7816753c2883
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 78f3e701e63d83a8aa6ae1350ed10229e0200d37
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="comparing-datarows-linq-to-dataset"></a>DataRow (LINQ-DataSet) karşılaştırma
[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]eşit olup olmadığını görmek için kaynağı öğeleri karşılaştırmak için çeşitli kümesi işleçleri tanımlar. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]Aşağıdaki kümesi işleçleri sağlar:  
  
-   <xref:System.Linq.Enumerable.Distinct%2A>  
  
-   <xref:System.Linq.Enumerable.Union%2A>  
  
-   <xref:System.Linq.Enumerable.Intersect%2A>  
  
-   <xref:System.Linq.Enumerable.Except%2A>  
  
 Bu işleçlere çağırarak kaynağı öğeleri karşılaştırma <xref:System.Collections.Generic.IEqualityComparer%601.GetHashCode%2A> ve <xref:System.Collections.Generic.IEqualityComparer%601.Equals%2A> öğelerinin her koleksiyon yöntemleri. Durumunda bir <xref:System.Data.DataRow>, bu operatörler genellikle ayarlama işlemleri için ideal davranışı üzerinde tablo veri değil bir başvuru karşılaştırma gerçekleştirin. Ayarlama işlemleri için genellikle öğesi değerlerin eşit olup ve öğesi başvuruları belirlemek istiyor. Bu nedenle, <xref:System.Data.DataRowComparer> sınıfı eklenmiştir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]. Bu sınıf, satır değerlerini karşılaştırmak için kullanılabilir.  
  
 <xref:System.Data.DataRowComparer> Sınıfı için bir değer karşılaştırma uygulama içerir <xref:System.Data.DataRow>, bu sınıf için ayarlama işlemleri gibi kullanılabilmesi için <xref:System.Linq.Enumerable.Distinct%2A>. Bu sınıf doğrudan örneği oluşturulamıyor; Bunun yerine, <xref:System.Data.DataRowComparer.Default%2A> özelliği kullanılan, bir örneğini döndürmek için <xref:System.Data.DataRowComparer%601>. <xref:System.Data.DataRowComparer%601.Equals%2A> Yöntemi çağrıldıktan sonra ve iki <xref:System.Data.DataRow> Karşılaştırılacak nesneler geçirilir giriş parametreleri olarak. <xref:System.Data.DataRowComparer%601.Equals%2A> Yöntemi döndürür `true` ise sıralanmış bir sütun kümesini her ikisinde de değerleri <xref:System.Data.DataRow> nesneleri eşit; Aksi takdirde `false`.  
  
## <a name="example"></a>Örnek  
 Bu örnekte `Intersect` her iki tabloda görünür kişiler döndürülecek.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnekte, iki satır karşılaştırır ve karma kodlarını alır.  
  
 [!code-vb[DP LINQ to DataSet Examples#CompareDifferentRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#comparedifferentrows)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Data.DataRowComparer>  
 [DataSet’e Veri Yükleme](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [LINQ to DataSet Örnekleri](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
