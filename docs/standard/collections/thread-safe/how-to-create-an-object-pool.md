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
# <a name="how-to-create-an-object-pool-by-using-a-concurrentbag"></a><span data-ttu-id="d0cad-102">Nasıl yapılır: ConcurrentBag Kullanarak Nesne Havuzu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d0cad-102">How to: Create an Object Pool by Using a ConcurrentBag</span></span>
<span data-ttu-id="d0cad-103">Bu örnek, bir nesne havuzunu uygulamak için eşzamanlı bir paket kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="d0cad-103">This example shows how to use a concurrent bag to implement an object pool.</span></span> <span data-ttu-id="d0cad-104">Nesne havuzları, bir sınıfın birden çok örneği gerektiren durumlarda uygulama performansını iyileştirebilir ve sınıfın oluşturulması veya yok olması pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="d0cad-104">Object pools can improve application performance in situations where you require multiple instances of a class and the class is expensive to create or destroy.</span></span> <span data-ttu-id="d0cad-105">İstemci programı yeni bir nesne istediğinde, nesne havuzu önce oluşturulmuş ve havuza döndürülen bir tane sağlamaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="d0cad-105">When a client program requests a new object, the object pool first attempts to provide one that has already been created and returned to the pool.</span></span> <span data-ttu-id="d0cad-106">Hiçbiri kullanılabilir değilse, yalnızca yeni bir nesne oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d0cad-106">If none is available, only then is a new object created.</span></span>  
  
 <span data-ttu-id="d0cad-107"><xref:System.Collections.Concurrent.ConcurrentBag%601>, özellikle de aynı iş parçacığı öğeleri ekleyip kaldırırken hızlı ekleme ve kaldırmayı desteklediğinden, nesneleri depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d0cad-107"><xref:System.Collections.Concurrent.ConcurrentBag%601> is used to store the objects because it supports fast insertion and removal, especially when the same thread is both adding and removing items.</span></span> <span data-ttu-id="d0cad-108">Bu örnek, <xref:System.Collections.Concurrent.ConcurrentQueue%601> ve <xref:System.Collections.Concurrent.ConcurrentStack%601>gibi, paket veri yapısının uyguladığı <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>etrafında oluşturulacak şekilde daha da genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="d0cad-108">This example could be further augmented to be built around a <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>, which the bag data structure implements, as do <xref:System.Collections.Concurrent.ConcurrentQueue%601> and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0cad-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="d0cad-109">Example</span></span>  
 [!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)]
 [!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]  
  
## <a name="see-also"></a><span data-ttu-id="d0cad-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0cad-110">See also</span></span>

- [<span data-ttu-id="d0cad-111">İş Parçacığı Güvenli Koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="d0cad-111">Thread-Safe Collections</span></span>](../../../../docs/standard/collections/thread-safe/index.md)
