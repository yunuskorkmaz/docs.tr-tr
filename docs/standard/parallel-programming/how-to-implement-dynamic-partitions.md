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
helpviewer_keywords:
- tasks, how to create a dynamic partitioner
ms.assetid: c875ad12-a161-43e6-ad1c-3d6927c536a7
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 9b08c387c9b10a9d6fa8728a7fce87a7894a37fa
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-implement-dynamic-partitions"></a>Nasıl yapılır: Dinamik Bölümleri Uygulama
Aşağıdaki örnek, bir özel uygulamak gösterilmektedir <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> dinamik bölümleme uygular ve belirli aşırı kullanılan <xref:System.Threading.Tasks.Parallel.ForEach%2A> PLINQ gelen ve giden.  
  
## <a name="example"></a>Örnek  
 Bir bölüm çağırır her zaman <xref:System.Collections.IEnumerator.MoveNext%2A> Numaralayıcı üzerinde Numaralandırıcı bölümü olan bir liste öğesi sağlar. PLINQ söz konusu olduğunda ve <xref:System.Threading.Tasks.Parallel.ForEach%2A>, bölüm bir <xref:System.Threading.Tasks.Task> örneği. İstekleri aynı anda birden çok iş parçacığı üzerinde gerçekleştiği olduğundan, geçerli dizin için erişim eşitlenir.  
  
 [!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#04)]
 [!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  
  
 Bu, her bir öbeğin bir öğe oluşan bölümleme öbek örneğidir. Aynı anda daha fazla öğe sağlayarak kilit çakışması azaltın ve teorik olarak daha hızlı performans elde. Ancak, tüm iş parçacıklarının tüm iş yapılana kadar meşgul tutmak için belirli bir noktada daha büyük öbek ek yük dengeleme mantık gerektirebilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [PLINQ ve TPL için Özel Bölümleyiciler](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)  
 [Nasıl yapılır: Statik Bölümleme için bir Bölümleyici Uygulama](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
