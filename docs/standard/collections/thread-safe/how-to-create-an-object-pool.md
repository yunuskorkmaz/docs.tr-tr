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
# <a name="create-an-object-pool-by-using-a-concurrentbag"></a><span data-ttu-id="f1ba3-102">Bir ConcurrentBag kullanarak nesne havuzu oluşturma</span><span class="sxs-lookup"><span data-stu-id="f1ba3-102">Create an object pool by using a ConcurrentBag</span></span>

<span data-ttu-id="f1ba3-103">Bu örnek, bir <xref:System.Collections.Concurrent.ConcurrentBag%601> nesne havuzunu uygulamak için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f1ba3-103">This example shows how to use a <xref:System.Collections.Concurrent.ConcurrentBag%601> to implement an object pool.</span></span> <span data-ttu-id="f1ba3-104">Nesne havuzları, bir sınıfın birden çok örneği gerektiren durumlarda uygulama performansını iyileştirebilir ve sınıfın oluşturulması veya yok olması pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="f1ba3-104">Object pools can improve application performance in situations where you require multiple instances of a class and the class is expensive to create or destroy.</span></span> <span data-ttu-id="f1ba3-105">İstemci programı yeni bir nesne istediğinde, nesne havuzu önce oluşturulmuş ve havuza döndürülen bir tane sağlamaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="f1ba3-105">When a client program requests a new object, the object pool first attempts to provide one that has already been created and returned to the pool.</span></span> <span data-ttu-id="f1ba3-106">Hiçbiri kullanılabilir değilse, yalnızca yeni bir nesne oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f1ba3-106">If none is available, only then is a new object created.</span></span>

<span data-ttu-id="f1ba3-107">, <xref:System.Collections.Concurrent.ConcurrentBag%601> Özellikle de aynı iş parçacığı öğeleri ekleyip kaldırırken hızlı ekleme ve kaldırma özelliğini desteklediğinden, nesneleri depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f1ba3-107">The <xref:System.Collections.Concurrent.ConcurrentBag%601> is used to store the objects because it supports fast insertion and removal, especially when the same thread is both adding and removing items.</span></span> <span data-ttu-id="f1ba3-108">Bu örnek, <xref:System.Collections.Concurrent.IProducerConsumerCollection%601> , ve gibi paket veri yapısının uyguladığı bir etrafında yerleşik olarak daha da Genişletilebilir <xref:System.Collections.Concurrent.ConcurrentQueue%601> <xref:System.Collections.Concurrent.ConcurrentStack%601> .</span><span class="sxs-lookup"><span data-stu-id="f1ba3-108">This example could be further augmented to be built around a <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>, which the bag data structure implements, as do <xref:System.Collections.Concurrent.ConcurrentQueue%601> and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>

> [!TIP]
> <span data-ttu-id="f1ba3-109">Bu makalede, nesneleri yeniden kullanım için depolamak üzere temeldeki bir eşzamanlı türe sahip bir nesne havuzu uygulamanızın nasıl yazılacağı tanımlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f1ba3-109">This article defines how to write your own implementation of an object pool with an underlying concurrent type to store objects for reuse.</span></span> <span data-ttu-id="f1ba3-110">Ancak, <xref:Microsoft.Extensions.ObjectPool.ObjectPool%601?displayProperty=nameWithType> tür ad alanı altında zaten var <xref:Microsoft.Extensions.ObjectPool?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="f1ba3-110">However, the <xref:Microsoft.Extensions.ObjectPool.ObjectPool%601?displayProperty=nameWithType> type already exists under the <xref:Microsoft.Extensions.ObjectPool?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="f1ba3-111">Bir çok ek özellik içeren kendi uygulamanızı oluşturmadan önce kullanılabilir türü kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="f1ba3-111">Consider using the available type before creating your own implementation, which includes many additional features.</span></span>

## <a name="example"></a><span data-ttu-id="f1ba3-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="f1ba3-112">Example</span></span>

[!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)]
[!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]

## <a name="see-also"></a><span data-ttu-id="f1ba3-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1ba3-113">See also</span></span>

- [<span data-ttu-id="f1ba3-114">İş parçacığı güvenli Koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="f1ba3-114">Thread-Safe Collections</span></span>](index.md)
