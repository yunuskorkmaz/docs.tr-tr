---
title: "Nasıl yapılır: Bir BlockingCollection'daki Öğeleri Kaldırmak için ForEach Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, how to enumerate blocking collectoin
ms.assetid: 2096103c-22f7-420d-b631-f102bc33a6dd
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 823cde5ddd06d3b5cc2ad03327fc38e7651ed74d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-use-foreach-to-remove-items-in-a-blockingcollection"></a>Nasıl yapılır: Bir BlockingCollection'daki Öğeleri Kaldırmak için ForEach Kullanma
Öğelerden alma yanı sıra bir <xref:System.Collections.Concurrent.BlockingCollection%601> kullanarak <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> ve <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> yöntemini de kullanabilirsiniz bir [foreach](~/docs/csharp/language-reference/keywords/foreach-in.md) ([her](~/docs/visual-basic/language-reference/statements/for-each-next-statement.md) Visual Basic'te) ekleme olana kadar öğeleri kaldırmak için tamamlandı ve boş bir koleksiyondur. Bu adlı bir *numaralandırma diziyi* veya *numaralandırma tüketen* olduğundan, tipik bir aksine `foreach` (`For Each`) döngü, bu Numaralandırıcının kaldırarak kaynak koleksiyonu değiştirir öğeler.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tüm öğeleri kaldırmak gösterilmiştir bir <xref:System.Collections.Concurrent.BlockingCollection%601> kullanarak bir `foreach` (`For Each`) döngü.  
  
 [!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
 [!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]  
  
 Bu örnekte bir `foreach` ile döngü <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> numaralandırılan gibi Koleksiyondan kaldırılacak her bir öğeyi neden Süren akıştaki yöntemi. <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>herhangi bir zamanda koleksiyonundaki öğeleri sayısının üst sınırını belirler. Bu şekilde koleksiyonunda numaralandırma tüketici iş parçacığı yoksa öğeleri kullanılabilir veya koleksiyon boş olup olmadığını engeller. Bu örnekte engelleme ilgili bir sorun, tüketilen daha hızlı öğeleri üretici iş parçacığı ekler için değil.  
  
 Öğeleri üretici iş parçacıkları tarafından eklenen aynı sırayla numaralandırılır garantisi yoktur.  
  
 Değişiklik yapmadan toplamasını için yalnızca kullanın `foreach` (`For Each`) olmadan <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> yöntemi. Ancak, bu tür bir numaralandırma zaman içinde kesin bir noktada koleksiyonunun bir anlık görüntü temsil ettiğini anlamak önemlidir. Başka bir iş parçacığı ekleme veya aynı anda döngü yürütme sırasında öğeleri kaldırma, döngü koleksiyonu gerçek durumunu gösterebilir değil.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 [Paralel Programlama](../../../../docs/standard/parallel-programming/index.md)
