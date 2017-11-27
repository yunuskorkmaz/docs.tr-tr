---
title: "Nasıl yapılır: Dinamik Bölümleri Uygulama"
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
helpviewer_keywords: tasks, how to create a dynamic partitioner
ms.assetid: c875ad12-a161-43e6-ad1c-3d6927c536a7
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d1e5dc93997918e0f7da29fa1f94c434a556f19f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-dynamic-partitions"></a>Nasıl yapılır: Dinamik Bölümleri Uygulama
Aşağıdaki örnek, bir özel uygulamak gösterilmektedir <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> dinamik bölümleme uygular ve belirli aşırı kullanılan <xref:System.Threading.Tasks.Parallel.ForEach%2A> PLINQ gelen ve giden.  
  
## <a name="example"></a>Örnek  
 Bir bölüm çağırır her zaman <xref:System.Collections.IEnumerator.MoveNext%2A> Numaralayıcı üzerinde Numaralandırıcı bölümü olan bir liste öğesi sağlar. PLINQ söz konusu olduğunda ve <xref:System.Threading.Tasks.Parallel.ForEach%2A>, bölüm bir <xref:System.Threading.Tasks.Task> örneği. İstekleri aynı anda birden çok iş parçacığı üzerinde gerçekleştiği olduğundan, geçerli dizin için erişim eşitlenir.  
  
 [!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#04)]
 [!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  
  
 Bu, her bir öbeğin bir öğe oluşan bölümleme öbek örneğidir. Aynı anda daha fazla öğe sağlayarak kilit çakışması azaltın ve teorik olarak daha hızlı performans elde. Ancak, tüm iş parçacıklarının tüm iş yapılana kadar meşgul tutmak için belirli bir noktada daha büyük öbek ek yük dengeleme mantık gerektirebilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [PLINQ ve TPL için özel Bölümleyiciler](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)  
 [Nasıl yapılır: statik bölümleme için bir Bölümleyici uygulama](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
