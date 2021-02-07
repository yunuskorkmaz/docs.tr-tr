---
description: 'Hakkında daha fazla bilgi edinin: Single-Table sorguları (LINQ to DataSet)'
title: Single-Table sorguları (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b74bcf8-3f87-449f-bff7-6bcb0d69d212
ms.openlocfilehash: a4b6ce2a60eeafc9221d838d1b86c9964774df60
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718765"
---
# <a name="single-table-queries-linq-to-dataset"></a>Single-Table sorguları (LINQ to DataSet)

Language-Integrated Query (LINQ) sorguları arabirimini veya arabirimi uygulayan veri kaynakları üzerinde çalışır <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Linq.IQueryable%601> . <xref:System.Data.DataTable>Sınıf her iki arabirimi de uygulamıyor, bu nedenle <xref:System.Data.DataTableExtensions.AsEnumerable%2A> <xref:System.Data.DataTable> `From` bir LINQ sorgusunun yan tümcesinde kaynak olarak kullanmak istiyorsanız yöntemini çağırmanız gerekir.  
  
 Aşağıdaki örnek, SalesOrderHeader tablosundan gelen tüm çevrimiçi siparişleri alır ve sipariş KIMLIĞINI, sipariş tarihini ve sipariş numarasını konsola verir.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where1)]  
 [!code-vb[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where1)]
  
 Yerel değişken sorgusu, standart sorgu işleçlerinden bir veya daha fazla sorgu işleci uygulayarak bir veya daha fazla bilgi kaynağında çalışan bir sorgu ifadesiyle başlatılır. Bu durumda, sınıfa özgü işleçler LINQ to DataSet <xref:System.Data.DataSet> . Önceki örnekteki sorgu ifadesi standart sorgu işleçlerinin ikisini kullanır: `Where` ve `Select` .  
  
 `Where`Yan tümcesi, bir koşula göre sırayı, bu durumda `OnlineOrderFlag` olarak ayarlandığı şekilde filtreler `true` . `Select`İşleci, işlecine geçirilen bağımsız değişkenleri yakalayan bir sıralanabilir nesne ayırır ve döndürür. Yukarıdaki örnekte, anonim bir tür üç özellik ile oluşturulur: `SalesOrderID` , `OrderDate` , ve `SalesOrderNumber` . Bu üç özellik değerleri `SalesOrderID` , `OrderDate` tablosundan,, ve sütunlarının değerlerine ayarlanır `SalesOrderNumber` `SalesOrderHeader` .  
  
 `foreach`Döngü daha sonra tarafından döndürülen sıralanabilir nesneyi numaralandırır `Select` ve sorgu sonuçlarını verir. Sorgu bir tür olduğundan, sorgu <xref:System.Linq.Enumerable> <xref:System.Collections.Generic.IEnumerable%601> değişkeni döngü kullanılarak tekrarlandırılana kadar sorgu değerlendirmesi ertelenir `foreach` . Ertelenmiş sorgu değerlendirmesi, sorguların birden çok kez değerlendirilebilecek, her seferinde farklı sonuçlar veren değerler olarak tutulmasını sağlar.  
  
 <xref:System.Data.DataRowExtensions.Field%2A>Yöntemi, bir öğesinin sütun değerlerine erişim sağlar <xref:System.Data.DataRow> ve <xref:System.Data.DataRowExtensions.SetField%2A> (önceki örnekte gösterilmez), içindeki sütun değerlerini ayarlar <xref:System.Data.DataRow> . Hem <xref:System.Data.DataRowExtensions.Field%2A> yöntemi hem de <xref:System.Data.DataRowExtensions.SetField%2A> yöntemi null yapılabilir değer türlerini işler, bu nedenle null değerleri açıkça denetlemeniz gerekmez. Her iki yöntem de genel yöntemlerdir, bu da dönüş türünü dönüştürmek zorunda değilsiniz anlamına gelir. ' De önceden var olan sütun erişimcisini kullanabilirsiniz <xref:System.Data.DataRow> (örneğin, `o["OrderDate"]` ), ancak bunu yapmak için return nesnesini uygun türe atamalısınız.  Sütun null yapılabilir bir değer türünde ise, yöntemini kullanarak değerin null olup olmadığını kontrol etmeniz gerekir <xref:System.Data.DataRow.IsNull%2A> . Daha fazla bilgi için bkz. [Genel alan ve SetField yöntemleri](generic-field-and-setfield-methods-linq-to-dataset.md).  
  
 Yöntemin ve yöntemin genel parametresinde belirtilen veri türünün, `T` <xref:System.Data.DataRowExtensions.Field%2A> <xref:System.Data.DataRowExtensions.SetField%2A> temel alınan değerin türüyle veya oluşturulacak şekilde eşleşmesi gerektiğini unutmayın <xref:System.InvalidCastException> . Belirtilen sütun adı aynı zamanda içindeki bir sütunun adıyla eşleşmelidir <xref:System.Data.DataSet> veya bir <xref:System.ArgumentException> oluşturulur. Her iki durumda da, sorgu yürütüldüğünde çalışma zamanı veri numaralandırmasında özel durum oluşturulur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tablolar Arası Sorgular](cross-table-queries-linq-to-dataset.md)
- [Türü Belirtilmiş DataSet’leri Sorgulama](querying-typed-datasets.md)
- [Genel Alan ve SetField Yöntemleri](generic-field-and-setfield-methods-linq-to-dataset.md)
