---
title: "Genel alan ve SetField yöntemleri (LINQ-DataSet)"
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
ms.assetid: 1883365f-9d6c-4ccb-9187-df309f47706d
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 7f71a6e380730ce3d622437b28a3722793524968
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="generic-field-and-setfield-methods-linq-to-dataset"></a>Genel alan ve SetField yöntemleri (LINQ-DataSet)
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]için genişletme yöntemleri sağlar <xref:System.Data.DataRow> sütun değerlerini erişmek için sınıf: <xref:System.Data.DataRowExtensions.Field%2A> yöntemi ve <xref:System.Data.DataRowExtensions.SetField%2A> yöntemi. Bu yöntemler, geliştiriciler, özellikle ilgili null değerler için sütun değerlerini daha kolay erişim sağlar. <xref:System.Data.DataSet> Kullanan <xref:System.DBNull.Value> ise null değerleri temsil etmek için [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] sunulan boş değer atanabilir tür destek kullanan [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)]. Önceden varolan sütun erişimcisi kullanarak <xref:System.Data.DataRow> dönüş nesnenin uygun türe gerektirir. Belirli bir alanda varsa bir <xref:System.Data.DataRow> null değerini açıkça denetlemelisiniz döndürmek için null olabilir <xref:System.DBNull.Value> ve örtük olarak başka bir tür döndürüleceğini atama bir <xref:System.InvalidCastException>. Aşağıdaki örnekte, <xref:System.Data.DataRow.IsNull%2A> yöntemi değil denetlemek için kullanılan bir null değer özel durum dizin oluşturucu döndürülürse <xref:System.DBNull.Value> ve hangisine yayınlayacağınızı denenen bir <xref:System.String>.  
  
 [!code-csharp[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#whereisnull)]
 [!code-vb[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#whereisnull)]  
  
 <xref:System.Data.DataRowExtensions.Field%2A> Yöntemi sütun değerlerine erişim sağlar bir <xref:System.Data.DataRow> ve <xref:System.Data.DataRowExtensions.SetField%2A> sütun değerleri ayarlayan bir <xref:System.Data.DataRow>. Her iki <xref:System.Data.DataRowExtensions.Field%2A> yöntemi ve <xref:System.Data.DataRowExtensions.SetField%2A> yöntemi işlemek boş değer atanabilir türler, böylece önceki örnekte olduğu gibi null değerler için açıkça denetleyin zorunda değildir. Dönüş türü cast gerekmez şekilde her iki yöntem genel yöntemler, ayrıca, değildir.  
  
 Aşağıdaki örnek kullanır <xref:System.Data.DataRowExtensions.Field%2A> yöntemi.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where3)]
 [!code-vb[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where3)]  
  
 Veri türü genel parametresinde belirtilen Not `T` , <xref:System.Data.DataRowExtensions.Field%2A> yöntemi ve <xref:System.Data.DataRowExtensions.SetField%2A> yöntemi, temel alınan değerin türü eşleşmelidir. Aksi halde, bir <xref:System.InvalidCastException> özel durum. Belirtilen sütun adı aynı zamanda bir sütunun adını uymalıdır <xref:System.Data.DataSet>, veya bir <xref:System.ArgumentException> oluşturulur. Sorgu çalıştırıldığında her iki durumda da, çalışma zamanında veri numaralandırma sırasında özel durum oluşur.  
  
 <xref:System.Data.DataRowExtensions.SetField%2A> Yöntemin kendisi hiçbir tür dönüşümleri gerçekleştirmez. Bu, ancak, bir tür dönüştürme gerçekleşmez anlamına gelmez. <xref:System.Data.DataRowExtensions.SetField%2A> Yöntemi çıkarır [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] davranışını <xref:System.Data.DataRow> sınıfı. Tür dönüşümü tarafından gerçekleştirilmek <xref:System.Data.DataRow> nesne ve dönüştürülen değer sonra kaydedilmesi için <xref:System.Data.DataRow> nesnesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Data.DataRowExtensions>
