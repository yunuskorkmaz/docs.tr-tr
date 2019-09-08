---
title: Projeksiyonlar Düzenleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
ms.openlocfilehash: 0dfd5d951750de2ab918c51dd9f4f2deeb8a6318
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793824"
---
# <a name="formulate-projections"></a>Projeksiyonlar Düzenleme
Aşağıdaki örneklerde, içindeki Visual Basic `select` C# ve `Select` içindeki deyimin, sorgu projeksiyonlarını biçimlendirmek için diğer özelliklerle nasıl birleştirileceği gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 `Select` Aşağıdaki örnek, için`select` C# birdiziiletişimadıdöndürmeküzereVisualBasic(içindekiyantümce)içindeyantümcesini`Customers`kullanır.  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, için `Select` C#`select` bir`Customers`dizi iletişim adı ve telefon numarası döndürmek üzere Visual Basic (içindeki yan tümce) ve *anonim türlerde* yan tümcesini kullanır.  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, çalışanlar için `Select` bir ad ve telefon`select` numarası sırası C#döndürmek üzere Visual Basic (içindeki yan tümce) ve *anonim türlerde* yan tümcesini kullanır. `Name` `Phone` Ve alanları tek bir alan`HomePhone` () içinde birleştirilir ve alan, sonuçta elde edilen dizide olarak yeniden adlandırılır. `LastName` `FirstName`  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, içinde `Select` C#Visual Basic (`select` yan tümce) ve *anonim türler* içindeki yan tümcesini kullanarak tüm `ProductID`s 'leri ve adlı `HalfPrice`bir hesaplanmış değeri döndürür. Bu değer 2 ile `UnitPrice` bölünmüş olarak ayarlanır.  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir ürün `Select` adı ve ürün kullanılabilirliği`select` dizisi döndürmek C#için Visual Basic (içindeki yan tümce) ve *koşul deyimi* içinde yan tümcesini kullanır.  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, çalışanların adlarının bir `Select` dizisini döndürmek`select` için bir C#Visual Basic yan tümcesini (içinde yan tümce) ve *bilinen bir türü* (adı) kullanır.  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Londra `Select` 'daki `Where` müşterilere yönelik olarak`select` filtrelenmiş `where` bir C#iletişim adları *dizisi* döndürmek için Visual Basic (ve içinde) kullanır.  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, müşteriler hakkında `Select` verilerin *şekillendirilmiş bir alt kümesini* döndürmek C#için Visual Basic (`select` içindeki yan tümce) ve *anonim türlerde* bir yan tümce kullanır.  
  
 [!code-csharp[DLinqQueryExamples#64](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#64)]
 [!code-vb[DLinqQueryExamples#64](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#64)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, aşağıdaki sonuçları döndürmek için iç içe geçmiş sorguları kullanır:  
  
- Tüm siparişlerin ve bunlara karşılık gelen `OrderID`sözleşmelerinin sırası.  
  
- Bir iskontonun bulunduğu sıradaki öğelerin alt sırası.  
  
- Sevkiyat maliyeti dahil değilse kaydedilen para miktarı.  
  
 [!code-csharp[DLinqQueryExamples#65](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#65)]
 [!code-vb[DLinqQueryExamples#65](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#65)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Örnekleri](query-examples.md)
