---
title: Tek tablo sorguları (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b74bcf8-3f87-449f-bff7-6bcb0d69d212
ms.openlocfilehash: 17a2fcf54cae64d9443b0cc0e8a37e1002bbd394
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175362"
---
# <a name="single-table-queries-linq-to-dataset"></a>Tek tablo sorguları (LINQ to DataSet)

Dil ile tümleşik sorgu (LINQ) sorguları, arabirimini veya arabirimini uygulayan veri kaynakları üzerinde çalışır <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Linq.IQueryable%601> . <xref:System.Data.DataTable>Sınıf her iki arabirimi de uygulamıyor, bu nedenle <xref:System.Data.DataTableExtensions.AsEnumerable%2A> <xref:System.Data.DataTable> `From` bir LINQ sorgusunun yan tümcesinde kaynak olarak kullanmak istiyorsanız yöntemini çağırmanız gerekir.  
  
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
