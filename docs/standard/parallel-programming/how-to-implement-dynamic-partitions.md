---
title: 'Nasıl yapılır: Dinamik Bölümleri Uygulama'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to create a dynamic partitioner
ms.assetid: c875ad12-a161-43e6-ad1c-3d6927c536a7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8bffc25cb5c3ae3671fdf6018158b81549c360e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580438"
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
