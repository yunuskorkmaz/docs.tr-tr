---
title: Tek Tablolu Sorgular (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b74bcf8-3f87-449f-bff7-6bcb0d69d212
ms.openlocfilehash: 89c90fd217285fac449aba40682aa947fcfb3a07
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249096"
---
# <a name="single-table-queries-linq-to-dataset"></a>Tek Tablolu Sorgular (LINQ to DataSet)
Dil-Tümleşik Sorgu (LINQ) <xref:System.Collections.Generic.IEnumerable%601> sorguları, arabirimi <xref:System.Linq.IQueryable%601> veya arabirimi uygulayan veri kaynakları üzerinde çalışır. Sınıf <xref:System.Data.DataTable> her iki arabirimi de uygulamaz, bu nedenle bir <xref:System.Data.DataTable> LINQ sorgusunun `From` yan tümcesinde kaynak olarak kullanmak istiyorsanız <xref:System.Data.DataTableExtensions.AsEnumerable%2A> yöntemi aramanız gerekir.  
  
 Aşağıdaki örnek, SalesOrderHeader tablosundan tüm çevrimiçi siparişleri alır ve sipariş kimliğini, sipariş tarihini ve sipariş numarasını konsola verir.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where1)]  
 [!code-vb[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where1)]
  
 Yerel değişken sorgusu, standart sorgu işleçlerinden veya LINQ'dan DataSet'e bir veya daha fazla sorgu işleci uygulayarak bir veya daha fazla <xref:System.Data.DataSet> bilgi kaynağında çalışan bir sorgu ifadesiyle başolarak başolarak başolarak başolarak adlanır. Önceki örnekteki sorgu ifadesi, standart sorgu işleçlerinden ikisini kullanır: `Where` ve `Select`.  
  
 Yan `Where` tümce, sırayı bir koşula göre `OnlineOrderFlag` filtreler, `true`bu durumda dizi . İşleç, `Select` işleç geçirilen bağımsız değişkenleri yakalayan bir sayısal nesne ayırır ve döndürür. Bu yukarıdaki örnekte, anonim bir tür `SalesOrderID`üç `OrderDate`özellikleri `SalesOrderNumber`ile oluşturulur: , ve . Bu üç özelliğin `SalesOrderID`değerleri , , `OrderDate`ve `SalesOrderNumber` `SalesOrderHeader` sütunlar tablodaki değerleri ayarlanır.  
  
 Döngü `foreach` daha sonra döndürülen `Select` sayısal nesneyi kaydeder ve sorgu sonuçlarını verir. Sorgu uygulayan <xref:System.Linq.Enumerable> bir tür <xref:System.Collections.Generic.IEnumerable%601>olduğundan, sorgu değişkeni `foreach` döngü kullanılarak üzerinde yinelenene kadar sorgunun değerlendirilmesi ertelenir. Ertelenmiş sorgu değerlendirmesi, sorguların her seferinde farklı sonuçlar elde ederek birden çok kez değerlendirilebilecek değerler olarak tutulmasını sağlar.  
  
 Yöntem <xref:System.Data.DataRowExtensions.Field%2A> a sütun değerlerine erişim <xref:System.Data.DataRow> sağlar <xref:System.Data.DataRowExtensions.SetField%2A> ve (önceki örnekte gösterilmez) <xref:System.Data.DataRow>bir . sütun değerlerini ayarlar . Hem <xref:System.Data.DataRowExtensions.Field%2A> yöntem <xref:System.Data.DataRowExtensions.SetField%2A> hem de yöntem nullable değer türlerini işler, bu nedenle null değerleri açıkça denetlemeniz gerekmez. Her iki yöntem de genel yöntemlerdir, bu da dönüş türünü atmanız gerekolmadığı anlamına gelir. Önceden varolan sütun aksesuarını <xref:System.Data.DataRow> (örneğin, ) `o["OrderDate"]`kullanabilirsiniz, ancak bunu yapmak için iade nesnesini uygun türe dökmeniz gerekir.  Sütun nullable değer türü <xref:System.Data.DataRow.IsNull%2A> ise, yöntemi kullanarak değerin null olup olmadığını kontrol etniz gerekir. Daha fazla bilgi için [Genel Alan ve SetField Yöntemleri'ne](generic-field-and-setfield-methods-linq-to-dataset.md)bakın.  
  
 Yöntem <xref:System.Data.DataRowExtensions.SetField%2A> ve yöntemin genel parametresinde <xref:System.InvalidCastException> `T` belirtilen veri türünün, temel değerin türüyle eşleşmesi veya atılacağına dikkat edin. <xref:System.Data.DataRowExtensions.Field%2A> Belirtilen sütun adı da bir sütunun <xref:System.Data.DataSet> <xref:System.ArgumentException> adı veya bir atAtılacak eşleşmesi gerekir. Her iki durumda da, sorgu yürütüldüğünde özel durum çalışma zamanı veri numaralandırmasında atılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tablolar Arası Sorgular](cross-table-queries-linq-to-dataset.md)
- [Türü Belirtilmiş DataSet’leri Sorgulama](querying-typed-datasets.md)
- [Genel Alan ve SetField Yöntemleri](generic-field-and-setfield-methods-linq-to-dataset.md)
