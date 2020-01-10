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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711278"
---
# <a name="how-to-create-an-object-pool-by-using-a-concurrentbag"></a>Nasıl yapılır: ConcurrentBag Kullanarak Nesne Havuzu Oluşturma
Bu örnek, bir nesne havuzunu uygulamak için eşzamanlı bir paket kullanmayı gösterir. Nesne havuzları, bir sınıfın birden çok örneği gerektiren durumlarda uygulama performansını iyileştirebilir ve sınıfın oluşturulması veya yok olması pahalıdır. İstemci programı yeni bir nesne istediğinde, nesne havuzu önce oluşturulmuş ve havuza döndürülen bir tane sağlamaya çalışır. Hiçbiri kullanılabilir değilse, yalnızca yeni bir nesne oluşturulur.  
  
 <xref:System.Collections.Concurrent.ConcurrentBag%601>, özellikle de aynı iş parçacığı öğeleri ekleyip kaldırırken hızlı ekleme ve kaldırmayı desteklediğinden, nesneleri depolamak için kullanılır. Bu örnek, <xref:System.Collections.Concurrent.ConcurrentQueue%601> ve <xref:System.Collections.Concurrent.ConcurrentStack%601>gibi, paket veri yapısının uyguladığı <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>etrafında oluşturulacak şekilde daha da genişletilebilir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)]
 [!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş Parçacığı Güvenli Koleksiyonları](../../../../docs/standard/collections/thread-safe/index.md)
