---
title: "Nasıl yapılır: Bir BlockingCollection'daki Öğeleri Kaldırmak için ForEach Kullanma"
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, how to enumerate blocking collectoin
ms.assetid: 2096103c-22f7-420d-b631-f102bc33a6dd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 44b71ed726af585259b015c608e49d8c81e4e22a
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2018
ms.locfileid: "46710676"
---
# <a name="how-to-use-foreach-to-remove-items-in-a-blockingcollection"></a>Nasıl yapılır: Bir BlockingCollection'daki Öğeleri Kaldırmak için ForEach Kullanma
Öğeleri alma yanı sıra bir <xref:System.Collections.Concurrent.BlockingCollection%601> kullanarak <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> ve <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> yöntemini de kullanabilirsiniz bir [foreach](~/docs/csharp/language-reference/keywords/foreach-in.md) ([her](~/docs/visual-basic/language-reference/statements/for-each-next-statement.md) Visual Basic'te) ekleme olana kadar öğeleri kaldırmak için tamamlandı ve boş bir koleksiyondur. Bu olarak adlandırılır bir *numaralandırma diziyi* veya *numaralandırma tüketen* olduğundan, tipik bir aksine `foreach` (`For Each`) döngü, bu Numaralandırıcının kaynak koleksiyonu kaldırarak değiştirir öğeleri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tüm öğeleri kaldırmak gösterilmiştir bir <xref:System.Collections.Concurrent.BlockingCollection%601> kullanarak bir `foreach` (`For Each`) döngü.  
  
 [!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
 [!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]  
  
 Bu örnekte bir `foreach` ile döngü <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> yöntemi kullanan akıştaki her öğesi, tıklamanızdır Koleksiyondan kaldırılacak neden olur. <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> herhangi bir zamanda koleksiyondaki öğeleri maksimum sayısını sınırlar. Koleksiyonu bu şekilde, tüketicinin iş parçacığıyla hiçbir öğesi yok veya varsa koleksiyon boş olup olmadığını engeller. Bu örnekte engelleyen önemli öğeleri kullanılabilir daha hızlı üretici iş parçacığı ekler için değil.  
  
 Aynı sırada üretici iş parçacıkları tarafından eklenen öğeler numaralandırılır garantisi yoktur.  
  
 Değişiklik yapmadan derlemesini için yalnızca kullanın `foreach` (`For Each`) olmadan <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> yöntemi. Ancak, bu tür bir sabit listesi bir anlık görüntü zaman içinde kesin bir noktada koleksiyonun gösterdiğini anlamak önemlidir. Diğer iş parçacıklarını ekliyor veya döngü eşzamanlı olarak yürütülmesi sırasında öğeleri kaldırma, ardından döngü koleksiyonu gerçek durumuyla temsil edemeyebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
- [Paralel Programlama](../../../../docs/standard/parallel-programming/index.md)
