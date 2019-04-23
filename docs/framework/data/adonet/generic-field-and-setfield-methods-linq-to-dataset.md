---
title: Genel alan ve SetField yöntemleri (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1883365f-9d6c-4ccb-9187-df309f47706d
ms.openlocfilehash: 7c7f1fef5d1fa575cd6d3bfdb7e6cbbea79ade28
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59086019"
---
# <a name="generic-field-and-setfield-methods-linq-to-dataset"></a>Genel alan ve SetField yöntemleri (LINQ to DataSet)
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] için genişletme yöntemleri sağlar <xref:System.Data.DataRow> sütun değerleri erişmek için sınıf: <xref:System.Data.DataRowExtensions.Field%2A> yöntemi ve <xref:System.Data.DataRowExtensions.SetField%2A> yöntemi. Bu yöntemler, geliştiriciler, özellikle ilgili null değerler için sütun değerlerini daha kolay erişim sağlar. <xref:System.Data.DataSet> Kullanan <xref:System.DBNull.Value> ise null değerleri temsil etmek için [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] sürümünde boş değer atanabilir tür desteği kullanan [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)]. Önceden mevcut olan sütun erişimcisi kullanarak <xref:System.Data.DataRow> dönüş nesnenin uygun türe gerektirir. Belirli bir alanda varsa bir <xref:System.Data.DataRow> açıkça null değerini denetlemelidir döndüren null olabilir çünkü <xref:System.DBNull.Value> ve örtük olarak başka bir tür verir tür atama bir <xref:System.InvalidCastException>. Aşağıdaki örnekte, <xref:System.Data.DataRow.IsNull%2A> yöntemi değil denetlemek için kullanılan bir null değer için özel durum dizin oluşturucu döndürdüyse <xref:System.DBNull.Value> ve yayınlayacağınızı denenen bir <xref:System.String>.  
  
 [!code-csharp[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#whereisnull)]
 [!code-vb[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#whereisnull)]  
  
 <xref:System.Data.DataRowExtensions.Field%2A> Yöntemi sütun değerlerine erişim sağlayan bir <xref:System.Data.DataRow> ve <xref:System.Data.DataRowExtensions.SetField%2A> sütun değerlerini ayarlar bir <xref:System.Data.DataRow>. Her iki <xref:System.Data.DataRowExtensions.Field%2A> yöntemi ve <xref:System.Data.DataRowExtensions.SetField%2A> yöntemi işlemek boş değer atanabilir türleri açıkça null değerler önceki örnekte olduğu gibi olup olmadığını denetlemek zorunda kalmazsınız. Dönüş türü dönüştürme yapmak zorunda kalmazsınız iki genel yöntemler de yöntemlerdir.  
  
 Aşağıdaki örnekte <xref:System.Data.DataRowExtensions.Field%2A> yöntemi.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where3)]
 [!code-vb[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where3)]  
  
 Genel parametre içinde belirtilen veri türü Not `T` , <xref:System.Data.DataRowExtensions.Field%2A> yöntemi ve <xref:System.Data.DataRowExtensions.SetField%2A> yöntemi, temel alınan değerinin türüyle eşleşmelidir. Aksi takdirde, bir <xref:System.InvalidCastException> özel durumu oluşturulur. Belirtilen sütun adı bir sütun adını da ayrıca eşleşmelidir <xref:System.Data.DataSet>, veya bir <xref:System.ArgumentException> oluşturulur. Sorgu yürütülürken her iki durumda da, çalışma zamanında verilerin numaralandırma sırasında özel durum oluşturulur.  
  
 <xref:System.Data.DataRowExtensions.SetField%2A> Yöntemin kendisi, herhangi bir tür dönüştürmeleri gerçekleştirmez. Bu, ancak bir tür dönüştürme gerçekleşmez anlamına gelmez. <xref:System.Data.DataRowExtensions.SetField%2A> Yöntemi kullanıma sunan [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] davranışını <xref:System.Data.DataRow> sınıfı. Tür dönüştürme tarafından gerçekleştirilmesi <xref:System.Data.DataRow> nesne ve dönüştürülen değeri ardından kaydedilmesi için <xref:System.Data.DataRow> nesne.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataRowExtensions>
