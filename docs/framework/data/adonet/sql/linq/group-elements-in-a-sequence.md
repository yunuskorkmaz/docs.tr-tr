---
title: Dizideki Öğeleri Gruplama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1d50c8b4-f550-4775-bbb6-eab6e874cb43
ms.openlocfilehash: bc490b579e841a0e9b3724fe0e8789cc9411683d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782186"
---
# <a name="group-elements-in-a-sequence"></a>Dizideki Öğeleri Gruplama
<xref:System.Linq.Enumerable.GroupBy%2A> İşleci bir sıranın öğelerini gruplandırır. Aşağıdaki örnekler Northwind veritabanını kullanır.  
  
> [!NOTE]
> <xref:System.Linq.Enumerable.GroupBy%2A> Sorgularda null sütun değerleri bazen bir <xref:System.InvalidOperationException>oluşturabilir. Daha fazla bilgi için [sorun giderme](troubleshooting.md)konusunun "GroupBy InvalidOperationException" bölümüne bakın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bölümlerine `Products` göre `CategoryID`.  
  
 [!code-csharp[DLinqQueryExamples#27](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#27)]
 [!code-vb[DLinqQueryExamples#27](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#27)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, her <xref:System.Linq.Enumerable.Max%2A> biri `CategoryID`için en fazla birim fiyatını bulmak için kullanır.  
  
 [!code-csharp[DLinqQueryExamples#28](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#28)]
 [!code-vb[DLinqQueryExamples#28](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#28)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek ortalamasını, her birinin `UnitPrice` `CategoryID`ortalamasını bulmak için kullanır.  
  
 [!code-csharp[DLinqQueryExamples#29](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#29)]
 [!code-vb[DLinqQueryExamples#29](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#29)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, her <xref:System.Linq.Queryable.Sum%2A> birinin `CategoryID`toplamını `UnitPrice` bulmak için kullanır.  
  
 [!code-csharp[DLinqQueryExamples#30](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#30)]
 [!code-vb[DLinqQueryExamples#30](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#30)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, her <xref:System.Linq.Queryable.Count%2A> birinin `CategoryID`içindeki Discontinued `Products` sayısını bulmak için kullanır.  
  
 [!code-csharp[DLinqQueryExamples#31](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#31)]
 [!code-vb[DLinqQueryExamples#31](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#31)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, en az 10 `where` ürüne sahip tüm kategorileri bulmak için aşağıdaki yan tümceyi kullanır.  
  
 [!code-csharp[DLinqQueryExamples#32](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#32)]
 [!code-vb[DLinqQueryExamples#32](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#32)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek ürünlerini ve `CategoryID` `SupplierID`ile gruplandırır.  
  
 [!code-csharp[DLinqQueryExamples#33](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#33)]
 [!code-vb[DLinqQueryExamples#33](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#33)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek iki ürün dizisini döndürür. İlk sıra, birim fiyatı 10 ' dan küçük veya buna eşit olan ürünleri içerir. İkinci sıra, birim fiyatı 10 ' dan büyük olan ürünleri içerir.  
  
 [!code-csharp[DLinqQueryExamples#34](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#34)]
 [!code-vb[DLinqQueryExamples#34](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#34)]  
  
## <a name="example"></a>Örnek  
 <xref:System.Linq.Queryable.GroupBy%2A> İşleci yalnızca tek bir anahtar bağımsız değişkeni alabilir. Birden fazla anahtarla gruplandırmalısınız, aşağıdaki örnekte olduğu gibi anonim bir tür oluşturmanız gerekir:  
  
 [!code-csharp[DLinqQueryExamples#35](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#35)]
 [!code-vb[DLinqQueryExamples#35](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#35)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Örnekleri](query-examples.md)
- [Örnek Veritabanları İndirme](downloading-sample-databases.md)
