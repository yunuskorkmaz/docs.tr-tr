---
title: Genel alan ve SetField Yöntemleri (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1883365f-9d6c-4ccb-9187-df309f47706d
ms.openlocfilehash: 310eb3ccecc3159234ed362ed044be7ad704dde4
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634839"
---
# <a name="generic-field-and-setfield-methods-linq-to-dataset"></a>Genel alan ve SetField Yöntemleri (LINQ to DataSet)
LINQ to DataSet, sütun değerlerine erişmek için <xref:System.Data.DataRow> sınıfına uzantı yöntemleri sağlar: <xref:System.Data.DataRowExtensions.Field%2A> yöntemi ve <xref:System.Data.DataRowExtensions.SetField%2A> yöntemi. Bu yöntemler, özellikle null değerlerle ilgili olarak geliştiricilerin sütun değerlerine daha kolay erişim sağlar. <xref:System.Data.DataSet>, null değerleri temsil etmek için <xref:System.DBNull.Value?displayProperty=nameWithType> kullanır, ancak LINQ <xref:System.Nullable> ve <xref:System.Nullable%601> türlerini kullanır. <xref:System.Data.DataRow> ' de önceden var olan sütun erişimcisinin kullanılması, dönüş nesnesini uygun türe dönüştürmeyi gerektirir. <xref:System.Data.DataRow> belirli bir alan null olduğunda, <xref:System.DBNull.Value?displayProperty=nameWithType> döndüren ve örtük olarak başka bir türe atan bir <xref:System.InvalidCastException>oluşturan null değeri açıkça kontrol etmeniz gerekir. Aşağıdaki örnekte, <xref:System.Data.DataRow.IsNull%2A?displayProperty=nameWithType> yöntemi null değeri denetlemek için kullanılmazsa, dizin oluşturucunun <xref:System.DBNull.Value?displayProperty=nameWithType> döndüğü ve bir <xref:System.String>dönüştürmeye çalıştığı durumlarda bir özel durum oluşturulur.  
  
 [!code-csharp[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#whereisnull)]
 [!code-vb[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#whereisnull)]  
  
 <xref:System.Data.DataRowExtensions.Field%2A> yöntemi bir <xref:System.Data.DataRow> sütun değerlerine erişim sağlar ve <xref:System.Data.DataRowExtensions.SetField%2A> <xref:System.Data.DataRow>sütun değerlerini ayarlar. Hem <xref:System.Data.DataRowExtensions.Field%2A> yöntemi hem de <xref:System.Data.DataRowExtensions.SetField%2A> yöntemi null yapılabilir türleri işler, bu nedenle önceki örnekte olduğu gibi null değerleri açıkça denetlemeniz gerekmez. Her iki yöntem de genel yöntemlerdir, bu nedenle dönüş türünü dönüştürmek zorunda değilsiniz.  
  
 Aşağıdaki örnekte <xref:System.Data.DataRowExtensions.Field%2A> yöntemi kullanılmaktadır.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where3)]
 [!code-vb[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where3)]  
  
 <xref:System.Data.DataRowExtensions.Field%2A> yönteminin genel `T` parametresinde belirtilen veri türünün ve <xref:System.Data.DataRowExtensions.SetField%2A> yönteminin temel alınan değerin türüyle eşleşmesi gerektiğini unutmayın. Aksi takdirde, <xref:System.InvalidCastException> bir özel durum oluşturulur. Belirtilen sütun adı ayrıca <xref:System.Data.DataSet>bir sütunun adıyla eşleşmelidir veya bir <xref:System.ArgumentException> atılır. Her iki durumda da, sorgu yürütüldüğünde verilerin numaralandırılması sırasında çalışma zamanında özel durum oluşturulur.  
  
 <xref:System.Data.DataRowExtensions.SetField%2A> yöntemi herhangi bir tür dönüştürmesi gerçekleştirmez. Bununla birlikte, bir tür dönüştürme gerçekleşmeyecektir. <xref:System.Data.DataRowExtensions.SetField%2A> yöntemi <xref:System.Data.DataRow> sınıfının ADO.NET davranışını kullanıma sunar. <xref:System.Data.DataRow> nesne tarafından bir tür dönüştürme gerçekleştirilebilir ve dönüştürülen değer daha sonra <xref:System.Data.DataRow> nesnesine kaydedilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataRowExtensions>
