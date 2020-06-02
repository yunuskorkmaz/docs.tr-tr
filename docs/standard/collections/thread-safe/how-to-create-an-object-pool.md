---
title: Bir ConcurrentBag kullanarak nesne havuzu oluşturma
ms.date: 05/01/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- object pool, in .NET Framework
ms.assetid: 0480e7ff-b6f9-480e-a889-2ed4264d8372
ms.openlocfilehash: 64d91162b27eba80fba63761d0a926e441b63440
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287867"
---
# <a name="create-an-object-pool-by-using-a-concurrentbag"></a>Bir ConcurrentBag kullanarak nesne havuzu oluşturma

Bu örnek, bir <xref:System.Collections.Concurrent.ConcurrentBag%601> nesne havuzunu uygulamak için nasıl kullanılacağını gösterir. Nesne havuzları, bir sınıfın birden çok örneği gerektiren durumlarda uygulama performansını iyileştirebilir ve sınıfın oluşturulması veya yok olması pahalıdır. İstemci programı yeni bir nesne istediğinde, nesne havuzu önce oluşturulmuş ve havuza döndürülen bir tane sağlamaya çalışır. Hiçbiri kullanılabilir değilse, yalnızca yeni bir nesne oluşturulur.

, <xref:System.Collections.Concurrent.ConcurrentBag%601> Özellikle de aynı iş parçacığı öğeleri ekleyip kaldırırken hızlı ekleme ve kaldırma özelliğini desteklediğinden, nesneleri depolamak için kullanılır. Bu örnek, <xref:System.Collections.Concurrent.IProducerConsumerCollection%601> , ve gibi paket veri yapısının uyguladığı bir etrafında yerleşik olarak daha da Genişletilebilir <xref:System.Collections.Concurrent.ConcurrentQueue%601> <xref:System.Collections.Concurrent.ConcurrentStack%601> .

> [!TIP]
> Bu makalede, nesneleri yeniden kullanım için depolamak üzere temeldeki bir eşzamanlı türe sahip bir nesne havuzu uygulamanızın nasıl yazılacağı tanımlanmaktadır. Ancak, <xref:Microsoft.Extensions.ObjectPool.ObjectPool%601?displayProperty=nameWithType> tür ad alanı altında zaten var <xref:Microsoft.Extensions.ObjectPool?displayProperty=fullName> . Bir çok ek özellik içeren kendi uygulamanızı oluşturmadan önce kullanılabilir türü kullanmayı düşünün.

## <a name="example"></a>Örnek

[!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)]
[!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]

## <a name="see-also"></a>Ayrıca bkz.

- [İş parçacığı güvenli Koleksiyonlar](index.md)
