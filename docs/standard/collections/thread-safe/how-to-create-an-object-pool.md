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
# <a name="how-to-create-an-object-pool-by-using-a-concurrentbag"></a><span data-ttu-id="86c76-102">Nasıl yapılır: ConcurrentBag Kullanarak Nesne Havuzu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="86c76-102">How to: Create an Object Pool by Using a ConcurrentBag</span></span>
<span data-ttu-id="86c76-103">Bu örnek, nesne havuzu uygulamak için eşzamanlı bir torbanın nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="86c76-103">This example shows how to use a concurrent bag to implement an object pool.</span></span> <span data-ttu-id="86c76-104">Nesne havuzları, bir sınıfın birden çok örneğine ihtiyaç duyduğunuz ve sınıfın oluşturmak veya yok etmek pahalı olduğu durumlarda uygulama performansını artırabilir.</span><span class="sxs-lookup"><span data-stu-id="86c76-104">Object pools can improve application performance in situations where you require multiple instances of a class and the class is expensive to create or destroy.</span></span> <span data-ttu-id="86c76-105">İstemci programı yeni bir nesne istediğinde, nesne havuzu önce zaten oluşturulmuş ve havuza döndürülen bir nesne havuzunu sağlamaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="86c76-105">When a client program requests a new object, the object pool first attempts to provide one that has already been created and returned to the pool.</span></span> <span data-ttu-id="86c76-106">Hiçbiri yoksa, yalnızca o zaman oluşturulan yeni bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="86c76-106">If none is available, only then is a new object created.</span></span>  
  
 <span data-ttu-id="86c76-107"><xref:System.Collections.Concurrent.ConcurrentBag%601>hızlı ekleme ve kaldırmayı desteklediği için nesneleri depolamak için kullanılır, özellikle de aynı iş parçacığı öğeleri hem ekliyor hem de kaldırıyorsa.</span><span class="sxs-lookup"><span data-stu-id="86c76-107"><xref:System.Collections.Concurrent.ConcurrentBag%601> is used to store the objects because it supports fast insertion and removal, especially when the same thread is both adding and removing items.</span></span> <span data-ttu-id="86c76-108">Bu örnek, torba veri yapısının <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>uyguladığı bir , etrafında inşa edilecek <xref:System.Collections.Concurrent.ConcurrentQueue%601> <xref:System.Collections.Concurrent.ConcurrentStack%601>şekilde daha da artırılabilir, yapmak ve .</span><span class="sxs-lookup"><span data-stu-id="86c76-108">This example could be further augmented to be built around a <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>, which the bag data structure implements, as do <xref:System.Collections.Concurrent.ConcurrentQueue%601> and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="86c76-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="86c76-109">Example</span></span>  
 [!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)]
 [!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]  
  
## <a name="see-also"></a><span data-ttu-id="86c76-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86c76-110">See also</span></span>

- [<span data-ttu-id="86c76-111">İş Parçacığı Koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="86c76-111">Thread-Safe Collections</span></span>](../../../../docs/standard/collections/thread-safe/index.md)
