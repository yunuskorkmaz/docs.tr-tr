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
ms.openlocfilehash: b2d46264113cb4c961f6c4b971b5986bdd9eb6a7
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44080754"
---
# <a name="how-to-implement-dynamic-partitions"></a>Nasıl yapılır: Dinamik Bölümleri Uygulama
Aşağıdaki örnek, özel bir uygulama gösterilmektedir <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> dinamik bölümlemeyi uygular ve belirli bir aşırı kullanılan <xref:System.Threading.Tasks.Parallel.ForEach%2A> ve PLINQ.  
  
## <a name="example"></a>Örnek  
 Bir bölüm çağırdığında <xref:System.Collections.IEnumerator.MoveNext%2A> Numaralandırıcıda Numaralandırıcı bölüm bir liste öğesi sağlar. PLINQ söz konusu olduğunda ve <xref:System.Threading.Tasks.Parallel.ForEach%2A>, bölüm bir <xref:System.Threading.Tasks.Task> örneği. Geçerli dizin için erişim isteklerini aynı anda birden çok iş parçacığında olmuyor çünkü eşitlenir.  
  
 [!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#04)]
 [!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  
  
 Bu, her bir öbeği oluşan bir öğe bölümleme öbek örneğidir. Aynı anda daha fazla öğe sağlayarak üzerinde kilit çekişmeyi azaltmak ve teorik olarak daha hızlı performans elde. Ancak, tüm iş tamamlanana kadar tüm iş parçacıklarının meşgul tutmak için belirli bir noktada daha büyük öbekler Yük Dengeleme ilave bir mantık gerektirebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [PLINQ ve TPL için Özel Bölümleyiciler](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)  
- [Nasıl yapılır: Statik Bölümleme için bir Bölümleyici Uygulama](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
