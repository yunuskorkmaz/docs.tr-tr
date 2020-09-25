---
title: Projeksiyonlar Düzenleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
ms.openlocfilehash: f0bc6dfcff7778ebc7156cbb039e13570c90467b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194407"
---
# <a name="formulate-projections"></a>Projeksiyonlar Düzenleme

Aşağıdaki örneklerde, `select` C# ve `Select` Visual Basic içindeki deyimin, sorgu projeksiyonlarını biçimlendirmek için diğer özelliklerle nasıl birleştirileceği gösterilmektedir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `Select` `select` için bir dizi iletişim adı döndürmek üzere Visual Basic (C# ' deki yan tümce) içinde yan tümcesini kullanır `Customers` .  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `Select` `select` için bir dizi iletişim adı ve telefon numarası döndürmek üzere Visual Basic (C# ' deki yan tümce) ve *anonim türler* içinde yan tümcesini kullanır `Customers` .  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `Select` `select` çalışanlar için bir ad ve telefon numarası sırası döndürmek üzere Visual Basic (C# ' deki yan tümce) ve *anonim türler* içinde yan tümcesini kullanır. `FirstName`Ve `LastName` alanları tek bir alan () içinde birleştirilir `Name` ve alan, `HomePhone` `Phone` sonuçta elde edilen dizide olarak yeniden adlandırılır.  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `Select` Visual Basic ( `select` C# ' deki yan tümce) ve *anonim türler* içindeki yan tümcesini ve ' nin bir dizisini `ProductID` ve adında bir hesaplanan değeri kullanır `HalfPrice` . Bu değer `UnitPrice` 2 ile bölünmüş olarak ayarlanır.  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, bir `Select` `select` ürün adı ve ürün kullanılabilirliği dizisi döndürmek için Visual Basic (C# ' deki yan tümce) ve *koşul deyimi* içinde yan tümcesini kullanır.  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `Select` çalışanların adlarının bir dizisini döndürmek için bir Visual Basic yan tümcesini ( `select` C# içinde yan tümce) ve *bilinen bir türü* (adı) kullanır.  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `Select` `Where` `select` `where` Londra 'daki müşterilere yönelik olarak *filtrelenmiş bir dizi* iletişim adı döndürmek için Visual Basic (ve C# ' de) kullanır.  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `Select` `select` müşteriler hakkında verilerin *şekillendirilmiş bir alt kümesini* döndürmek için Visual Basic (C# ' deki yan tümce) ve *anonim türler* ' de bir yan tümce kullanır.  
  
 [!code-csharp[DLinqQueryExamples#64](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#64)]
 [!code-vb[DLinqQueryExamples#64](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#64)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, aşağıdaki sonuçları döndürmek için iç içe geçmiş sorguları kullanır:  
  
- Tüm siparişlerin ve bunlara karşılık gelen sözleşmelerinin sırası `OrderID` .  
  
- Bir iskontonun bulunduğu sıradaki öğelerin alt sırası.  
  
- Sevkiyat maliyeti dahil değilse kaydedilen para miktarı.  
  
 [!code-csharp[DLinqQueryExamples#65](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#65)]
 [!code-vb[DLinqQueryExamples#65](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#65)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu örnekleri](query-examples.md)
