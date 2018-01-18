---
title: Tek tablo sorgu (LINQ-DataSet)
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
ms.assetid: 0b74bcf8-3f87-449f-bff7-6bcb0d69d212
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 5ac58f5e98113150123b152dad8d2cc25c61cf97
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="single-table-queries-linq-to-dataset"></a>Tek tablo sorgu (LINQ-DataSet)
[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]İş uygulayan veri kaynaklarını sorguları <xref:System.Collections.Generic.IEnumerable%601> arabirimi veya <xref:System.Linq.IQueryable%601> arabirimi. <xref:System.Data.DataTable> Çağırmanız gerekir böylece sınıfı ya da arabirimini uygulamıyor <xref:System.Data.DataTableExtensions.AsEnumerable%2A> kullanmak istiyorsanız, yöntem <xref:System.Data.DataTable> bir kaynak olarak `From` yan tümcesinde bir [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] sorgu.  
  
 Aşağıdaki örnek, tüm çevrimiçi siparişleri SalesOrderHeader tablosundan alır ve düzeni kimliği, sipariş tarihi ve konsola sipariş numarası çıkarır.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where1)]  
 [!code-vb[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where1)] 
  
 Yerel değişken sorgu üzerinde bir veya daha fazla bilgi kaynakları da bir veya daha fazla sorgu işleçleri uygulayarak standart sorgu işleçleri çalışır bir sorgu ifadesi ile veya durumunda başlatılmadan [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], işleçler belirli<xref:System.Data.DataSet>sınıfı. Önceki örnekte sorgu ifadesi iki standart sorgu işleçleri kullanır: `Where` ve `Select`.  
  
 `Where` Yan tümcesi bir koşula göre sırası filtreleri, bu durumda `OnlineOrderFlag` ayarlanır `true`. `Select` İşleci ayırır ve işleci için geçirilen bağımsız değişkenler yakalayan bir numaralandırma nesnesi döndürür. Bu örnek yukarıda, üç özelliklere sahip anonim bir tür oluşturulur: `SalesOrderID`, `OrderDate`, ve `SalesOrderNumber`. Bu üç özellik değerleri değerleri ayarlanır `SalesOrderID`, `OrderDate`, ve `SalesOrderNumber` sütunlarından `SalesOrderHeader` tablo.  
  
 `foreach` Döngü sonra tarafından döndürülen numaralandırılabilir nesne numaralandırır `Select` ve sorgu sonuçları verir. Sorgu olduğundan bir <xref:System.Linq.Enumerable> türü, hangi uygulayan <xref:System.Collections.Generic.IEnumerable%601>, sorgu değerlendirmesinden sorgu değişkeni kullanarak üzerinden yinelendiğinde kadar ertelenir `foreach` döngü. Ertelenmiş sorgu değerlendirme olabilir değerler hesaplanan gibi birden çok kez, potansiyel olarak farklı sonuçlar sağlayan her zaman tutulması için sorgular sağlar.  
  
 <xref:System.Data.DataRowExtensions.Field%2A> Yöntemi sütun değerlerine erişim sağlar bir <xref:System.Data.DataRow> ve <xref:System.Data.DataRowExtensions.SetField%2A> (önceki örnekte gösterilmez) sütun değerleri ayarlayan bir <xref:System.Data.DataRow>. Her iki <xref:System.Data.DataRowExtensions.Field%2A> yöntemi ve <xref:System.Data.DataRowExtensions.SetField%2A> yöntemi işlemek boş değer atanabilir türler, böylece açıkça null değerleri kontrol zorunda değildir. Her iki yöntemlerdir genel yöntemler, ayrıca, dönüş türü cast gerekmez anlamına gelir. Önceden varolan sütun erişimcisi kullanabileceğinizi <xref:System.Data.DataRow> (örneğin, `o["OrderDate"]`), ancak bunun nedenle duyar dönüş nesnenin uygun türe için.  Sütun null atanabilir ise kullanarak değerin boş olup olmadığını denetlemek sahip <xref:System.Data.DataRow.IsNull%2A> yöntemi. Daha fazla bilgi için bkz: [genel alan ve SetField yöntemleri](../../../../docs/framework/data/adonet/generic-field-and-setfield-methods-linq-to-dataset.md).  
  
 Veri türü genel parametresinde belirtilen Not `T` , <xref:System.Data.DataRowExtensions.Field%2A> yöntemi ve <xref:System.Data.DataRowExtensions.SetField%2A> yöntemi, temel alınan değerin türü eşleşmelidir veya bir <xref:System.InvalidCastException> oluşturulur. Belirtilen sütun adı aynı zamanda bir sütunun adını uymalıdır <xref:System.Data.DataSet> veya bir <xref:System.ArgumentException> oluşturulur. Sorgu çalıştırıldığında her iki durumda da, çalışma zamanında veri numaralandırma sırasında özel durum oluşur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tablolar Arası Sorgular](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)  
 [Türü Belirtilmiş DataSet’leri Sorgulama](../../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 [Genel Alan ve SetField Yöntemleri](../../../../docs/framework/data/adonet/generic-field-and-setfield-methods-linq-to-dataset.md)
