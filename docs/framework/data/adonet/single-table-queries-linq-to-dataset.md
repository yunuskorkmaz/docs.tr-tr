---
title: Tek tablo sorguları (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b74bcf8-3f87-449f-bff7-6bcb0d69d212
ms.openlocfilehash: 8807125bd61c71217ca96f3b5a38148ed100073b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794368"
---
# <a name="single-table-queries-linq-to-dataset"></a>Tek tablo sorguları (LINQ to DataSet)
[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]sorgular, <xref:System.Collections.Generic.IEnumerable%601> arabirimini <xref:System.Linq.IQueryable%601> veya arabirimini uygulayan veri kaynakları üzerinde çalışır. <xref:System.Data.DataTable> <xref:System.Data.DataTableExtensions.AsEnumerable%2A> [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] `From` Sınıf her iki arabirimi de uygulamıyor, bu nedenle bir sorgunun yan tümcesinde kaynak olarak kullanmak istiyorsanız yöntemini çağırmanız gerekir. <xref:System.Data.DataTable>  
  
 Aşağıdaki örnek, SalesOrderHeader tablosundan gelen tüm çevrimiçi siparişleri alır ve sipariş KIMLIĞINI, sipariş tarihini ve sipariş numarasını konsola verir.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where1)]  
 [!code-vb[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where1)] 
  
 Yerel değişken sorgusu, standart sorgu işleçlerinden bir veya daha fazla sorgu işleci uygulayarak bir veya daha fazla bilgi kaynağında çalışan bir sorgu ifadesiyle başlatılır ve bu durumda, LINQ to DataSet <xref:System.Data.DataSet>sınıf. Önceki örnekteki sorgu ifadesi standart sorgu işleçlerinin ikisini kullanır: `Where` ve. `Select`  
  
 Yan tümcesi, bir koşula göre sırayı, bu durumda `OnlineOrderFlag` olarak ayarlandığı şekilde `true`filtreler. `Where` `Select` İşleci, işlecine geçirilen bağımsız değişkenleri yakalayan bir sıralanabilir nesne ayırır ve döndürür. Yukarıdaki örnekte, anonim bir tür üç özellik ile oluşturulur: `SalesOrderID`, `OrderDate`, ve `SalesOrderNumber`. Bu üç `SalesOrderID`özellik değerleri, `SalesOrderHeader` tablosundan, `OrderDate`, ve `SalesOrderNumber` sütunlarının değerlerine ayarlanır.  
  
 Döngü daha sonra tarafından `Select` döndürülen sıralanabilir nesneyi numaralandırır ve sorgu sonuçlarını verir. `foreach` Sorgu bir tür <xref:System.Collections.Generic.IEnumerable%601>olduğundan <xref:System.Linq.Enumerable> , sorgu değişkeni `foreach` döngü kullanılarak tekrarlandırılana kadar sorgu değerlendirmesi ertelenir. Ertelenmiş sorgu değerlendirmesi, sorguların birden çok kez değerlendirilebilecek, her seferinde farklı sonuçlar veren değerler olarak tutulmasını sağlar.  
  
 Yöntemi, bir <xref:System.Data.DataRow> öğesinin sütun değerlerine erişim sağlar ve ( <xref:System.Data.DataRow>önceki örnekte <xref:System.Data.DataRowExtensions.SetField%2A> gösterilmez), içindeki sütun değerlerini ayarlar. <xref:System.Data.DataRowExtensions.Field%2A> Hem yöntemi hem <xref:System.Data.DataRowExtensions.SetField%2A> de yöntemi null yapılabilir türleri işler, bu nedenle null değerleri açıkça denetlemeniz gerekmez. <xref:System.Data.DataRowExtensions.Field%2A> Her iki yöntem de genel yöntemlerdir, bu da dönüş türünü dönüştürmek zorunda değilsiniz anlamına gelir. ' De <xref:System.Data.DataRow> önceden var olan sütun erişimcisini kullanabilirsiniz (örneğin, `o["OrderDate"]`), ancak bunu yapmak için return nesnesini uygun türe atamalısınız.  Sütun null yapılabilir ise, <xref:System.Data.DataRow.IsNull%2A> yöntemini kullanarak değerin null olup olmadığını kontrol etmeniz gerekir. Daha fazla bilgi için bkz. [Genel alan ve SetField yöntemleri](generic-field-and-setfield-methods-linq-to-dataset.md).  
  
 <xref:System.Data.DataRowExtensions.Field%2A> Yöntemin ve `T` <xref:System.InvalidCastException> yöntemin genel parametresinde belirtilen veri türünün, temel alınan değerin türüyle veya oluşturulacak şekilde eşleşmesi gerektiğini unutmayın. <xref:System.Data.DataRowExtensions.SetField%2A> Belirtilen sütun adı aynı zamanda içindeki <xref:System.Data.DataSet> bir sütunun adıyla eşleşmelidir veya bir <xref:System.ArgumentException> oluşturulur. Her iki durumda da, sorgu yürütüldüğünde çalışma zamanı veri numaralandırmasında özel durum oluşturulur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tablolar Arası Sorgular](cross-table-queries-linq-to-dataset.md)
- [Türü Belirtilmiş DataSet’leri Sorgulama](querying-typed-datasets.md)
- [Genel Alan ve SetField Yöntemleri](generic-field-and-setfield-methods-linq-to-dataset.md)
