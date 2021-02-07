---
description: 'Daha fazla bilgi edinin: birleştirme ve çapraz ürün sorguları'
title: Birleşimler ve Çapraz Ürün Sorguları Düzenleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8072ede-0521-4670-9bec-1778ceeb875b
ms.openlocfilehash: 1adee3576d7b30d6ec9a9c4e920befcd21dd9e85
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739124"
---
# <a name="formulate-joins-and-cross-product-queries"></a>Birleşimler ve Çapraz Ürün Sorguları Düzenleme

Aşağıdaki örneklerde, birden çok tablodan sonuçların nasıl birleştirileceğini gösterilmektedir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `From` `from` Londra 'daki müşterilerin tüm siparişlerini seçmek için Visual Basic (C# ' deki yan tümce) yan tümcesinde yabancı anahtar gezintisi kullanır.  
  
 [!code-csharp[DLinqQueryExamples#47](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#47)]
 [!code-vb[DLinqQueryExamples#47](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#47)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `Where` Birleşik Devletler içindeki yan yana `where` filtrelemek için Visual Basic (C# ' deki yan tümce) yan tümcesinde yabancı anahtar gezintisi kullanır `Products` `Supplier` .  
  
 [!code-csharp[DLinqQueryExamples#48](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#48)]
 [!code-vb[DLinqQueryExamples#48](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#48)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `From` `from` Seattle 'daki çalışanları filtrelemek ve bölgelerini listelemek için Visual Basic (C# ' deki yan tümce) yan tümcesinde yabancı anahtar gezintisi kullanır.  
  
 [!code-csharp[DLinqQueryExamples#49](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#49)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `Select` `select` bir çalışanın birbirlerine ve her iki çalışanın de aynı olduğu yere rapor ettiği çalışan çiftlerini filtrelemek için Visual Basic (C# ' deki yan tümce) yan tümcesinde yabancı anahtar gezintisini kullanır `City` .  
  
 [!code-csharp[DLinqQueryExamples#50](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#50)]
 [!code-vb[DLinqQueryExamples#50](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki Visual Basic örnek tüm müşteriler ve siparişler için, siparişlerin müşterilerle eşleştiğinden emin olur ve bu listedeki her müşteri için bir kişi adı sağlanır.  
  
 [!code-vb[DLinqQueryExamples#50v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50v)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek iki tablo ve proje sonucunu açık bir şekilde iki tablo olarak birleştirir.  
  
 [!code-csharp[DLinqQueryExamples#51](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#51)]
 [!code-vb[DLinqQueryExamples#51](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#51)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, her birinin üç tablo ve proje sonucunu açıkça birleştirir.  
  
 [!code-csharp[DLinqQueryExamples#52](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#52)]
 [!code-vb[DLinqQueryExamples#52](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#52)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek kullanılarak nasıl elde edilecek gösterilmektedir `LEFT OUTER JOIN` `DefaultIfEmpty()` . `DefaultIfEmpty()`Yöntemi, için olmadığında null değerini döndürür `Order` `Employee` .  
  
 [!code-csharp[DLinqQueryExamples#53](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#53)]
 [!code-vb[DLinqQueryExamples#53](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#53)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, bir `let` birleşimden kaynaklanan bir ifadeyi projeler.  
  
 [!code-csharp[DLinqQueryExamples#54](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#54)]
 [!code-vb[DLinqQueryExamples#54](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#54)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek bir `join` bileşik anahtarla bir gösterir.  
  
 [!code-csharp[DLinqQueryExamples#55](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#55)]
 [!code-vb[DLinqQueryExamples#55](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#55)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, bir `join` tarafın null yapılabilir olduğunu ve diğerinin ne şekilde olduğunu gösterir.  
  
 [!code-csharp[DLinqQueryExamples#56](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#56)]
 [!code-vb[DLinqQueryExamples#56](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#56)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu örnekleri](query-examples.md)
