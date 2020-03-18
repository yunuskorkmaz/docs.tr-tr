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
ms.openlocfilehash: 3970566b4e3f51ce538c328d4e69b20ec22ec09b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73091417"
---
# <a name="how-to-implement-dynamic-partitions"></a>Nasıl yapılır: Dinamik Bölümleri Uygulama

Aşağıdaki örnek, dinamik bölümleme <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> uygulayan ve belirli aşırı yüklerden <xref:System.Threading.Tasks.Parallel.ForEach%2A> ve PLINQ'dan kullanılabilecek bir özelin nasıl uygulanacağını gösterir.  
  
## <a name="example"></a>Örnek

Bir bölüm her <xref:System.Collections.IEnumerator.MoveNext%2A> zaman bir bölüm enumerator çağırır, enumerator tek bir liste öğesi ile bölüm sağlar. PLINQ ve <xref:System.Threading.Tasks.Parallel.ForEach%2A>durumunda , bölüm bir <xref:System.Threading.Tasks.Task> örnektir. İstekler birden çok iş parçacığı üzerinde aynı anda gerçekleştiğinden, geçerli dizin erişim eşitlenir.  

[!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner02.cs#OrderableListPartitioner)]
[!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  

Bu, her bir öğenin bir öğeden oluşan yığın bölümleme örneğidir. Aynı anda daha fazla öğe sağlayarak, kilit üzerindeki çekişmeyi azaltabilir ve teorik olarak daha hızlı performans elde edebilirsiniz. Ancak, bir noktada, tüm iş bitene kadar tüm iş parçacığı meşgul tutmak için daha büyük parçalar ek yük dengeleme mantığı gerektirebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

* [PLINQ ve TPL için Özel Bölümleyiciler](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
* [Nasıl yapılır: Statik Bölümleme için bir Bölümleyici Uygulama](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
