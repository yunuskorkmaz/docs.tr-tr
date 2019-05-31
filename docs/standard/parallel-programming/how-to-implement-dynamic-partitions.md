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
ms.openlocfilehash: 5719c6afc1c5efc6138f0a4931d1725a6f20909a
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66424040"
---
# <a name="how-to-implement-dynamic-partitions"></a>Nasıl yapılır: Dinamik Bölümleri Uygulama

Aşağıdaki örnek, özel bir uygulama gösterilmektedir <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> dinamik bölümlemeyi uygular ve belirli bir aşırı kullanılan <xref:System.Threading.Tasks.Parallel.ForEach%2A> ve PLINQ.  
  
## <a name="example"></a>Örnek

Bir bölüm çağırdığında <xref:System.Collections.IEnumerator.MoveNext%2A> Numaralandırıcıda Numaralandırıcı bölüm bir liste öğesi sağlar. PLINQ söz konusu olduğunda ve <xref:System.Threading.Tasks.Parallel.ForEach%2A>, bölüm bir <xref:System.Threading.Tasks.Task> örneği. Geçerli dizin için erişim isteklerini aynı anda birden çok iş parçacığında olmuyor çünkü eşitlenir.  

[!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner02.cs#OrderableListPartitioner)]
[!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  

Bu, her bir öbeği oluşan bir öğe bölümleme öbek örneğidir. Aynı anda daha fazla öğe sağlayarak üzerinde kilit çekişmeyi azaltmak ve teorik olarak daha hızlı performans elde. Ancak, tüm iş tamamlanana kadar tüm iş parçacıklarının meşgul tutmak için belirli bir noktada daha büyük öbekler Yük Dengeleme ilave bir mantık gerektirebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

* [PLINQ ve TPL için Özel Bölümleyiciler](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
* [Nasıl yapılır: Statik bölümleme için bir Bölümleyici uygulama](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
