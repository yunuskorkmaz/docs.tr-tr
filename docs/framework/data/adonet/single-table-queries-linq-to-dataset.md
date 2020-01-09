---
title: Tek tablo sorguları (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b74bcf8-3f87-449f-bff7-6bcb0d69d212
ms.openlocfilehash: 1f4462f617eb81d30f893b52bdc674e1eee8961c
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634774"
---
# <a name="single-table-queries-linq-to-dataset"></a>Tek tablo sorguları (LINQ to DataSet)
Dil ile tümleşik sorgu (LINQ) sorguları <xref:System.Collections.Generic.IEnumerable%601> arabirimini veya <xref:System.Linq.IQueryable%601> arabirimini uygulayan veri kaynakları üzerinde çalışır. <xref:System.Data.DataTable> sınıfı her iki arabirimi de uygulamıyor, bu nedenle <xref:System.Data.DataTable> bir LINQ sorgusunun `From` yan tümcesinde kaynak olarak kullanmak istiyorsanız <xref:System.Data.DataTableExtensions.AsEnumerable%2A> yöntemini çağırmanız gerekir.  
  
 Aşağıdaki örnek, SalesOrderHeader tablosundan gelen tüm çevrimiçi siparişleri alır ve sipariş KIMLIĞINI, sipariş tarihini ve sipariş numarasını konsola verir.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where1)]  
 [!code-vb[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where1)] 
  
 Yerel değişken sorgusu, standart sorgu işleçlerinden bir veya daha fazla sorgu işleci uygulayarak bir veya daha fazla bilgi kaynağında çalışan bir sorgu ifadesiyle başlatılır ve bu durumda, <xref:System.Data.DataSet> sınıfına özgü işleçler LINQ to DataSet. Önceki örnekteki sorgu ifadesi standart sorgu işleçlerinin ikisini kullanır: `Where` ve `Select`.  
  
 `Where` yan tümcesi, bir koşula göre diziyi filtreleyerek, bu durumda `OnlineOrderFlag` `true`olarak ayarlanmıştır. `Select` işleci, işlecine geçirilen bağımsız değişkenleri yakalayan bir sıralanabilir nesne ayırır ve döndürür. Yukarıdaki örnekte, anonim bir tür üç özellik ile oluşturulur: `SalesOrderID`, `OrderDate`ve `SalesOrderNumber`. Bu üç özellik değerleri, `SalesOrderHeader` tablosundan `SalesOrderID`, `OrderDate`ve `SalesOrderNumber` sütunlarının değerlerine ayarlanır.  
  
 `foreach` döngüsü daha sonra `Select` tarafından döndürülen sıralanabilir nesneyi numaralandırır ve sorgu sonuçlarını verir. Sorgu, <xref:System.Collections.Generic.IEnumerable%601>uygulayan <xref:System.Linq.Enumerable> bir tür olduğundan, sorgu değişkeni `foreach` döngüsü kullanılarak yinelenene kadar sorgu değerlendirmesi ertelenir. Ertelenmiş sorgu değerlendirmesi, sorguların birden çok kez değerlendirilebilecek, her seferinde farklı sonuçlar veren değerler olarak tutulmasını sağlar.  
  
 <xref:System.Data.DataRowExtensions.Field%2A> yöntemi bir <xref:System.Data.DataRow> sütun değerlerine erişim sağlar ve <xref:System.Data.DataRowExtensions.SetField%2A> (önceki örnekte gösterilmez) <xref:System.Data.DataRow>sütun değerlerini ayarlar. <xref:System.Data.DataRowExtensions.Field%2A> yöntemi ve <xref:System.Data.DataRowExtensions.SetField%2A> yöntemi null yapılabilir türleri işler, bu nedenle null değerleri açıkça denetlemeniz gerekmez. Her iki yöntem de genel yöntemlerdir, bu da dönüş türünü dönüştürmek zorunda değilsiniz anlamına gelir. Önceden var olan sütun erişimcisini <xref:System.Data.DataRow> (örneğin, `o["OrderDate"]`) kullanabilirsiniz, ancak bunu yapmak için return nesnesini uygun türe atamalısınız.  Sütun null yapılabilir ise, <xref:System.Data.DataRow.IsNull%2A> yöntemini kullanarak değerin null olup olmadığını denetlemeniz gerekir. Daha fazla bilgi için bkz. [Genel alan ve SetField yöntemleri](generic-field-and-setfield-methods-linq-to-dataset.md).  
  
 <xref:System.Data.DataRowExtensions.Field%2A> yönteminin ve <xref:System.Data.DataRowExtensions.SetField%2A> yönteminin genel parametresinde belirtilen veri türünün, temel alınan değerin türüyle eşleşmesi gerektiğini veya bir <xref:System.InvalidCastException> `T`. Belirtilen sütun adı ayrıca <xref:System.Data.DataSet> bir sütunun adıyla eşleşmelidir veya bir <xref:System.ArgumentException> atılır. Her iki durumda da, sorgu yürütüldüğünde çalışma zamanı veri numaralandırmasında özel durum oluşturulur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tablolar Arası Sorgular](cross-table-queries-linq-to-dataset.md)
- [Türü Belirtilmiş DataSet’leri Sorgulama](querying-typed-datasets.md)
- [Genel Alan ve SetField Yöntemleri](generic-field-and-setfield-methods-linq-to-dataset.md)
