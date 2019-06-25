---
title: Genel alan ve SetField yöntemleri (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1883365f-9d6c-4ccb-9187-df309f47706d
ms.openlocfilehash: 9a2913de6534612455c14858f6baffea8ef78976
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2019
ms.locfileid: "67347486"
---
# <a name="generic-field-and-setfield-methods-linq-to-dataset"></a>Genel alan ve SetField yöntemleri (LINQ to DataSet)
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] için genişletme yöntemleri sağlar <xref:System.Data.DataRow> sütun değerleri erişmek için sınıf: <xref:System.Data.DataRowExtensions.Field%2A> yöntemi ve <xref:System.Data.DataRowExtensions.SetField%2A> yöntemi. Bu yöntemler, geliştiriciler, özellikle ilgili null değerler için sütun değerlerini daha kolay erişim sağlar. <xref:System.Data.DataSet> Kullanan <xref:System.DBNull.Value?displayProperty=nameWithType> ise null değerleri temsil etmek için [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] kullanan <xref:System.Nullable> ve <xref:System.Nullable%601> türleri. Önceden mevcut olan sütun erişimcisi kullanarak <xref:System.Data.DataRow> dönüş nesnenin uygun türe gerektirir. Belirli bir alanda varsa bir <xref:System.Data.DataRow> açıkça null değerini denetlemelidir döndüren null olabilir çünkü <xref:System.DBNull.Value?displayProperty=nameWithType> ve örtük olarak başka bir tür verir tür atama bir <xref:System.InvalidCastException>. Aşağıdaki örnekte, <xref:System.Data.DataRow.IsNull%2A?displayProperty=nameWithType> yöntemi değil denetlemek için kullanılan bir null değer için özel durum dizin oluşturucu döndürdüyse <xref:System.DBNull.Value?displayProperty=nameWithType> ve yayınlayacağınızı denenen bir <xref:System.String>.  
  
 [!code-csharp[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#whereisnull)]
 [!code-vb[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#whereisnull)]  
  
 <xref:System.Data.DataRowExtensions.Field%2A> Yöntemi sütun değerlerine erişim sağlayan bir <xref:System.Data.DataRow> ve <xref:System.Data.DataRowExtensions.SetField%2A> sütun değerlerini ayarlar bir <xref:System.Data.DataRow>. Her iki <xref:System.Data.DataRowExtensions.Field%2A> yöntemi ve <xref:System.Data.DataRowExtensions.SetField%2A> yöntemi işlemek boş değer atanabilir türleri açıkça null değerler önceki örnekte olduğu gibi olup olmadığını denetlemek zorunda kalmazsınız. Dönüş türü dönüştürme yapmak zorunda kalmazsınız iki genel yöntemler de yöntemlerdir.  
  
 Aşağıdaki örnekte <xref:System.Data.DataRowExtensions.Field%2A> yöntemi.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where3)]
 [!code-vb[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where3)]  
  
 Genel parametre içinde belirtilen veri türü Not `T` , <xref:System.Data.DataRowExtensions.Field%2A> yöntemi ve <xref:System.Data.DataRowExtensions.SetField%2A> yöntemi, temel alınan değerinin türüyle eşleşmelidir. Aksi takdirde, bir <xref:System.InvalidCastException> özel durumu oluşturulur. Belirtilen sütun adı bir sütun adını da ayrıca eşleşmelidir <xref:System.Data.DataSet>, veya bir <xref:System.ArgumentException> oluşturulur. Sorgu yürütülürken her iki durumda da, çalışma zamanında verilerin numaralandırma sırasında özel durum oluşturulur.  
  
 <xref:System.Data.DataRowExtensions.SetField%2A> Yöntemin kendisi, herhangi bir tür dönüştürmeleri gerçekleştirmez. Bu, ancak bir tür dönüştürme gerçekleşmez anlamına gelmez. <xref:System.Data.DataRowExtensions.SetField%2A> Yöntemi gösterir ADO.NET davranışı <xref:System.Data.DataRow> sınıfı. Tür dönüştürme tarafından gerçekleştirilmesi <xref:System.Data.DataRow> nesne ve dönüştürülen değeri ardından kaydedilmesi için <xref:System.Data.DataRow> nesne.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataRowExtensions>
