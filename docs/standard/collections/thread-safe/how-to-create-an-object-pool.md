---
title: "Nasıl yapılır: ConcurrentBag Kullanarak Nesne Havuzu Oluşturma"
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
helpviewer_keywords: object pool, in .NET Framework
ms.assetid: 0480e7ff-b6f9-480e-a889-2ed4264d8372
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f7cb18157122d8bc053f34b21f623f3ab1e14305
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-an-object-pool-by-using-a-concurrentbag"></a>Nasıl yapılır: ConcurrentBag Kullanarak Nesne Havuzu Oluşturma
Bu örnek bir eş zamanlı paketi nesne havuzu uygulamak için nasıl kullanılacağını gösterir. Nesne havuzları bir sınıfın birden çok örneği gerektirir ve sınıfı oluşturmak veya silmek pahalıdır durumlarda uygulama performansını iyileştirebilir. Bir istemci programı yeni bir nesne istediğinde, nesne havuzu ilk zaten oluşturulduğundan ve havuza geri döner bir sağlamaya çalışır. Ancak bundan sonra yeni bir nesne yoksa, oluşturulur.  
  
 <xref:System.Collections.Concurrent.ConcurrentBag%601>özellikle iş parçacığı hem öğeler ekleme ve kaldırma zaman hızlı ekleme ve kaldırma, desteklediğinden, nesneleri depolamak için kullanılır. Bu örnek daha fazla geçici oluşturulacak engagement'ta bir <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>, yaptığınız gibi paketi veri yapısı uygulayan <xref:System.Collections.Concurrent.ConcurrentQueue%601> ve <xref:System.Collections.Concurrent.ConcurrentStack%601>.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)]
 [!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş parçacığı koleksiyonları](../../../../docs/standard/collections/thread-safe/index.md)
