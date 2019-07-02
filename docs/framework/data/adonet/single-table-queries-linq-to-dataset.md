---
title: Tek tablolu sorgular (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b74bcf8-3f87-449f-bff7-6bcb0d69d212
ms.openlocfilehash: 87a2f6853136b4b3e622968327bde01c9862bfdf
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504639"
---
# <a name="single-table-queries-linq-to-dataset"></a>Tek tablolu sorgular (LINQ to DataSet)
[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] İş sorguları, uygulayan veri kaynaklarında <xref:System.Collections.Generic.IEnumerable%601> arabirimi veya <xref:System.Linq.IQueryable%601> arabirimi. <xref:System.Data.DataTable> Çağırmanız gerekir böylece sınıf ya da arabirimi uygulamıyor <xref:System.Data.DataTableExtensions.AsEnumerable%2A> kullanmak istiyorsanız yöntemi <xref:System.Data.DataTable> kaynağı olarak `From` yan tümcesi bir [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] sorgu.  
  
 Aşağıdaki örnek, tüm çevrimiçi siparişler SalesOrderHeader tablosundan alır ve sipariş kimliği, sipariş tarihi ve sipariş numarası konsola çıkarır.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where1)]  
 [!code-vb[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where1)] 
  
 Yerel değişken sorgu standart sorgu işleçleri bir veya daha fazla sorgu işleçleri veya uygulayarak bir veya daha fazla bilgi kaynakları üzerinde çalışır, bir sorgu ifadesinde, veya LINQ to DataSet, işleçler için belirlibaşlatılır<xref:System.Data.DataSet>sınıfı. Önceki örnekteki sorgu ifadesinde iki standart sorgu işleçlerinin kullanır: `Where` ve `Select`.  
  
 `Where` Yan tümcesi filtreleyen bir koşula göre sırası, bu durumda `OnlineOrderFlag` ayarlanır `true`. `Select` İşleci ayırır ve işleç için geçirilen bağımsız değişkenler yakalayan bir numaralandırma nesnesi döndürür. Bu örnek yukarıda, anonim bir tür üç özellik ile oluşturulur: `SalesOrderID`, `OrderDate`, ve `SalesOrderNumber`. Bu üç özellik değerlerini değerleri ayarlanır `SalesOrderID`, `OrderDate`, ve `SalesOrderNumber` sütunlarından `SalesOrderHeader` tablo.  
  
 `foreach` Döngü sonra tarafından döndürülen bir numaralandırma nesnesi numaralandırır `Select` ve sorgu sonuçları verir. Sorgu olduğundan bir <xref:System.Linq.Enumerable> türü, uygulayan <xref:System.Collections.Generic.IEnumerable%601>, sorgu değerlendirmesi, sorgu değişkeni kullanarak üzerinden yinelenir kadar ertelenmiştir `foreach` döngü. Ertelenen sorgu değerlendirme gibi birden çok kez, her zaman büyük olasılıkla farklı sonuçlar verir olabilen değerleri değerlendirilmiş tutulması için sorgular sağlar.  
  
 <xref:System.Data.DataRowExtensions.Field%2A> Yöntemi sütun değerlerine erişim sağlayan bir <xref:System.Data.DataRow> ve <xref:System.Data.DataRowExtensions.SetField%2A> (önceki örnekte gösterilmiştir değil) sütun değerlerini ayarlar bir <xref:System.Data.DataRow>. Her iki <xref:System.Data.DataRowExtensions.Field%2A> yöntemi ve <xref:System.Data.DataRowExtensions.SetField%2A> yöntemi işlemek boş değer atanabilir türleri açıkça null değerler için denetlenecek zorunda kalmazsınız. Her iki yöntemlerdir genel yöntemler, ayrıca, dönüş türü dönüştürme yok anlamına gelir. Önceden mevcut olan sütun erişimcisinde kullanabileceğinizi <xref:System.Data.DataRow> (örneğin, `o["OrderDate"]`), ancak bunun yapılması bu nedenle içerseydi, uygun bir tür dönüş nesnesi.  Sütun null ise kullanarak değerin boş olup olmadığını denetlemek sahip <xref:System.Data.DataRow.IsNull%2A> yöntemi. Daha fazla bilgi için [genel alan ve SetField yöntemleri](../../../../docs/framework/data/adonet/generic-field-and-setfield-methods-linq-to-dataset.md).  
  
 Genel parametre içinde belirtilen veri türü Not `T` , <xref:System.Data.DataRowExtensions.Field%2A> yöntemi ve <xref:System.Data.DataRowExtensions.SetField%2A> yöntemi, temel alınan değerinin türü eşleşmelidir veya bir <xref:System.InvalidCastException> oluşturulur. Belirtilen sütun adı bir sütun adını da ayrıca eşleşmelidir <xref:System.Data.DataSet> veya <xref:System.ArgumentException> oluşturulur. Sorgu yürütülürken her iki durumda da, çalışma zamanı veri numaralandırma sırasında özel durum oluşturulur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tablolar Arası Sorgular](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)
- [Türü Belirtilmiş DataSet’leri Sorgulama](../../../../docs/framework/data/adonet/querying-typed-datasets.md)
- [Genel Alan ve SetField Yöntemleri](../../../../docs/framework/data/adonet/generic-field-and-setfield-methods-linq-to-dataset.md)
