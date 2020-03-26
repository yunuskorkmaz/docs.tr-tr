---
title: Genel Alan ve SetField Yöntemleri (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1883365f-9d6c-4ccb-9187-df309f47706d
ms.openlocfilehash: d7ddee775e91c6be6166a091997afd58113cfe6b
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249109"
---
# <a name="generic-field-and-setfield-methods-linq-to-dataset"></a>Genel Alan ve SetField Yöntemleri (LINQ to DataSet)
LINQ to DataSet, sütun <xref:System.Data.DataRow> değerlerine erişmek için <xref:System.Data.DataRowExtensions.Field%2A> sınıfa <xref:System.Data.DataRowExtensions.SetField%2A> uzantı yöntemleri sağlar: yöntem ve yöntem. Bu yöntemler, özellikle null değerleri ile ilgili geliştiriciler için sütun değerlerine daha kolay erişim sağlar. Null <xref:System.Data.DataSet> <xref:System.DBNull.Value?displayProperty=nameWithType> değerlerini temsil etmek için kullanır, <xref:System.Nullable> LINQ kullanır ve <xref:System.Nullable%601> türleri ise. Önceden varolan sütun aksesuarını <xref:System.Data.DataRow> kullanmak, iade nesnesini uygun türe dökmenizi gerektirir. Bir alandaki belirli <xref:System.Data.DataRow> bir alan null olabilirse, null değerini <xref:System.DBNull.Value?displayProperty=nameWithType> açıkça denetlemeniz gerekir, çünkü geri <xref:System.InvalidCastException>dönen ve dolaylı olarak başka bir türe döküm bir . Aşağıdaki örnekte, <xref:System.Data.DataRow.IsNull%2A?displayProperty=nameWithType> yöntem null değerini denetlemek için kullanılmadıysa, dizinleyici döndürür <xref:System.DBNull.Value?displayProperty=nameWithType> ve bir <xref:System.String>'e dökmeye çalışırsa bir özel durum atılır  
  
 [!code-csharp[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#whereisnull)]
 [!code-vb[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#whereisnull)]  
  
 Yöntem, <xref:System.Data.DataRowExtensions.Field%2A> a <xref:System.Data.DataRow> ve <xref:System.Data.DataRowExtensions.SetField%2A> kümeler sütun değerlerinin sütun <xref:System.Data.DataRow>değerlerine erişim sağlar. Hem <xref:System.Data.DataRowExtensions.Field%2A> yöntem <xref:System.Data.DataRowExtensions.SetField%2A> hem de yöntem geçersiz değer türlerini işler, bu nedenle önceki örnekte olduğu gibi null değerlerini açıkça denetlemeniz gerekmez. Her iki yöntem de genel yöntemlerdir, bu nedenle dönüş türünü dökmek zorunda kalmamanız gerekmez.  
  
 Aşağıdaki örnekyöntemi <xref:System.Data.DataRowExtensions.Field%2A> kullanır.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where3)]
 [!code-vb[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where3)]  
  
 Yöntemin genel parametresinde `T` belirtilen veri türünün ve yöntemin <xref:System.Data.DataRowExtensions.SetField%2A> temel değerin türüyle eşleşmesi gerektiğini unutmayın. <xref:System.Data.DataRowExtensions.Field%2A> Aksi takdirde, bir <xref:System.InvalidCastException> özel durum atılır. Belirtilen sütun adı da bir sütunun adı <xref:System.Data.DataSet>eşleşmesi gerekir , ya da bir <xref:System.ArgumentException> atılacak. Her iki durumda da, sorgu yürütüldüğünde verilerin numaralandırması sırasında özel durum çalışma zamanında atılır.  
  
 Yöntemin <xref:System.Data.DataRowExtensions.SetField%2A> kendisi herhangi bir tür dönüştürme gerçekleştirmez. Ancak bu, bir tür dönüştürmesinin gerçekleşeceği anlamına gelmez. Yöntem, <xref:System.Data.DataRowExtensions.SetField%2A> sınıfın ADO.NET davranışını <xref:System.Data.DataRow> ortaya çıkarır. Bir tür dönüştürme <xref:System.Data.DataRow> nesne tarafından gerçekleştirilebilir ve dönüştürülen değer <xref:System.Data.DataRow> daha sonra nesneye kaydedilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataRowExtensions>
