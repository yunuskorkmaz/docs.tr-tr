---
title: 'Nasıl yapılır: ConcurrentBag Kullanarak Nesne Havuzu Oluşturma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- object pool, in .NET Framework
ms.assetid: 0480e7ff-b6f9-480e-a889-2ed4264d8372
ms.openlocfilehash: 888521eb5c3c3169c4b39a26e82fef2e35c286d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711278"
---
# <a name="how-to-create-an-object-pool-by-using-a-concurrentbag"></a>Nasıl yapılır: ConcurrentBag Kullanarak Nesne Havuzu Oluşturma
Bu örnek, nesne havuzu uygulamak için eşzamanlı bir torbanın nasıl kullanılacağını gösterir. Nesne havuzları, bir sınıfın birden çok örneğine ihtiyaç duyduğunuz ve sınıfın oluşturmak veya yok etmek pahalı olduğu durumlarda uygulama performansını artırabilir. İstemci programı yeni bir nesne istediğinde, nesne havuzu önce zaten oluşturulmuş ve havuza döndürülen bir nesne havuzunu sağlamaya çalışır. Hiçbiri yoksa, yalnızca o zaman oluşturulan yeni bir nesnedir.  
  
 <xref:System.Collections.Concurrent.ConcurrentBag%601>hızlı ekleme ve kaldırmayı desteklediği için nesneleri depolamak için kullanılır, özellikle de aynı iş parçacığı öğeleri hem ekliyor hem de kaldırıyorsa. Bu örnek, torba veri yapısının <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>uyguladığı bir , etrafında inşa edilecek <xref:System.Collections.Concurrent.ConcurrentQueue%601> <xref:System.Collections.Concurrent.ConcurrentStack%601>şekilde daha da artırılabilir, yapmak ve .  
  
## <a name="example"></a>Örnek  
 [!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)]
 [!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş Parçacığı Koleksiyonları](../../../../docs/standard/collections/thread-safe/index.md)
