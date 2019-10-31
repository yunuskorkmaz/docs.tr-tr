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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091417"
---
# <a name="how-to-implement-dynamic-partitions"></a>Nasıl yapılır: Dinamik Bölümleri Uygulama

Aşağıdaki örnek, dinamik bölümlendirme uygulayan özel bir <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> nasıl uygulanacağını gösterir ve PLıNQ 'ten <xref:System.Threading.Tasks.Parallel.ForEach%2A> belirli aşırı yüklerden kullanılabilir.  
  
## <a name="example"></a>Örnek

Numaralandırıcı üzerinde <xref:System.Collections.IEnumerator.MoveNext%2A> bir bölüm çağırdığında, Numaralandırıcı bölüm bir liste öğesiyle birlikte sağlar. PLıNQ ve <xref:System.Threading.Tasks.Parallel.ForEach%2A>söz konusu olduğunda, bölüm bir <xref:System.Threading.Tasks.Task> örneğidir. İstekler birden çok iş parçacığında eşzamanlı olarak yapıldığından, geçerli dizine erişim eşitlenir.  

[!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner02.cs#OrderableListPartitioner)]
[!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  

Bu, öbek bölümlendirme bir örneğidir ve her bir öbek bir öğeden oluşur. Tek seferde daha fazla öğe sağlayarak kilit üzerindeki çekişmeyi azaltabilir ve teorik olarak daha hızlı performans elde edersiniz. Ancak, bazı bir noktada, tüm işler tamamlanana kadar tüm iş parçacıklarını meşgul tutmak için daha büyük parçalar ek yük dengeleme mantığını gerektirebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

* [PLINQ ve TPL için Özel Bölümleyiciler](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
* [Nasıl yapılır: Statik Bölümleme için bir Bölümleyici Uygulama](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
