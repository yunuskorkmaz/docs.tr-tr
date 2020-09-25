---
title: Genel alan ve SetField Yöntemleri (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1883365f-9d6c-4ccb-9187-df309f47706d
ms.openlocfilehash: 9deda11592389dd799477bdc027d59a0be0036da
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200663"
---
# <a name="generic-field-and-setfield-methods-linq-to-dataset"></a>Genel alan ve SetField Yöntemleri (LINQ to DataSet)

LINQ to DataSet <xref:System.Data.DataRow> sütun değerlerine erişmek için sınıfa uzantı yöntemleri sağlar: <xref:System.Data.DataRowExtensions.Field%2A> yöntemi ve <xref:System.Data.DataRowExtensions.SetField%2A> yöntemi. Bu yöntemler, özellikle null değerlerle ilgili olarak geliştiricilerin sütun değerlerine daha kolay erişim sağlar. <xref:System.Data.DataSet> <xref:System.DBNull.Value?displayProperty=nameWithType> Null değerleri temsil eden kullanır, ancak LINQ <xref:System.Nullable> ve <xref:System.Nullable%601> türlerini kullanır. ' De önceden var olan sütun erişimcisinin kullanılması, <xref:System.Data.DataRow> dönüş nesnesini uygun türe dönüştürmeyi gerektirir. İçindeki belirli bir alan <xref:System.Data.DataRow> null olabilir, döndürme <xref:System.DBNull.Value?displayProperty=nameWithType> ve dolaylı olarak başka bir türe atama, bir null değeri açıkça denetlemeniz gerekir <xref:System.InvalidCastException> . Aşağıdaki örnekte, <xref:System.Data.DataRow.IsNull%2A?displayProperty=nameWithType> yöntemi null değeri denetlemek için kullanılmazsa, dizin oluşturucunun döndürdüğü <xref:System.DBNull.Value?displayProperty=nameWithType> ve kendisine dönüştürmeye çalıştığı durumlarda bir özel durum oluşturulur <xref:System.String> .  
  
 [!code-csharp[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#whereisnull)]
 [!code-vb[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#whereisnull)]  
  
 Yöntemi, bir <xref:System.Data.DataRowExtensions.Field%2A> ' ın sütun değerlerine <xref:System.Data.DataRow> ve <xref:System.Data.DataRowExtensions.SetField%2A> içindeki sütun değerlerini ayarlar ' a erişim sağlar <xref:System.Data.DataRow> . Hem <xref:System.Data.DataRowExtensions.Field%2A> Yöntem hem de <xref:System.Data.DataRowExtensions.SetField%2A> Yöntem null yapılabilir değer türlerini işler, bu nedenle önceki örnekte olduğu gibi null değerleri açıkça denetlemeniz gerekmez. Her iki yöntem de genel yöntemlerdir, bu nedenle dönüş türünü dönüştürmek zorunda değilsiniz.  
  
 Aşağıdaki örnek <xref:System.Data.DataRowExtensions.Field%2A> yöntemini kullanır.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where3)]
 [!code-vb[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where3)]  
  
 Yönteminin genel parametresinde belirtilen veri türünün `T` <xref:System.Data.DataRowExtensions.Field%2A> ve <xref:System.Data.DataRowExtensions.SetField%2A> yönteminin temel alınan değerin türüyle eşleşmesi gerektiğini unutmayın. Aksi takdirde, bir <xref:System.InvalidCastException> özel durum oluşturulur. Belirtilen sütun adı aynı zamanda içindeki bir sütunun adıyla eşleşmelidir <xref:System.Data.DataSet> veya <xref:System.ArgumentException> oluşturulacak. Her iki durumda da, sorgu yürütüldüğünde verilerin numaralandırılması sırasında çalışma zamanında özel durum oluşturulur.  
  
 <xref:System.Data.DataRowExtensions.SetField%2A>Metodun kendisi herhangi bir tür dönüştürmesi gerçekleştirmez. Bununla birlikte, bir tür dönüştürme gerçekleşmeyecektir. <xref:System.Data.DataRowExtensions.SetField%2A>Yöntemi, sınıfının ADO.NET davranışını gösterir <xref:System.Data.DataRow> . Nesne tarafından bir tür dönüştürme gerçekleştirilebilir <xref:System.Data.DataRow> ve dönüştürülen değer <xref:System.Data.DataRow> nesneye kaydedilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataRowExtensions>
