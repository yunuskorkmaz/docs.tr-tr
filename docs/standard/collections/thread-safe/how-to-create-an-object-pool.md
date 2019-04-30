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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0bc0c6bebbab6e84c165f41300a4cb16c8746a07
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61644429"
---
# <a name="how-to-create-an-object-pool-by-using-a-concurrentbag"></a><span data-ttu-id="92f97-102">Nasıl yapılır: ConcurrentBag Kullanarak Nesne Havuzu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="92f97-102">How to: Create an Object Pool by Using a ConcurrentBag</span></span>
<span data-ttu-id="92f97-103">Bu örnek, nesne havuzu uygulamak için eşzamanlı Torbaların kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="92f97-103">This example shows how to use a concurrent bag to implement an object pool.</span></span> <span data-ttu-id="92f97-104">Nesne havuzları burada bir sınıfın birden çok örneği gerektirir ve sınıfı oluşturma veya yok et maliyetli durumlarda uygulama performansını iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="92f97-104">Object pools can improve application performance in situations where you require multiple instances of a class and the class is expensive to create or destroy.</span></span> <span data-ttu-id="92f97-105">Bir istemci programını yeni bir nesne istediğinde, nesne havuzu zaten oluşturulduğundan ve havuza geri döndürülen bir sağlamaya ilk çalışır.</span><span class="sxs-lookup"><span data-stu-id="92f97-105">When a client program requests a new object, the object pool first attempts to provide one that has already been created and returned to the pool.</span></span> <span data-ttu-id="92f97-106">Yoksa, ancak bundan sonra yeni bir nesne oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="92f97-106">If none is available, only then is a new object created.</span></span>  
  
 <span data-ttu-id="92f97-107"><xref:System.Collections.Concurrent.ConcurrentBag%601> özellikle aynı iş parçacığı hem öğeleri ekleme ve kaldırma sırasında hızlı ekleme ve kaldırma desteklediğinden, nesneleri depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="92f97-107"><xref:System.Collections.Concurrent.ConcurrentBag%601> is used to store the objects because it supports fast insertion and removal, especially when the same thread is both adding and removing items.</span></span> <span data-ttu-id="92f97-108">Bu örnek daha fazla geçici olarak oluşturulacak genişletilmesi bir <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>, olduğu gibi paket veri yapısı uygulayan <xref:System.Collections.Concurrent.ConcurrentQueue%601> ve <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span><span class="sxs-lookup"><span data-stu-id="92f97-108">This example could be further augmented to be built around a <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>, which the bag data structure implements, as do <xref:System.Collections.Concurrent.ConcurrentQueue%601> and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92f97-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="92f97-109">Example</span></span>  
 [!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)]
 [!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]  
  
## <a name="see-also"></a><span data-ttu-id="92f97-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92f97-110">See also</span></span>

- [<span data-ttu-id="92f97-111">İş Parçacığı Güvenli Koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="92f97-111">Thread-Safe Collections</span></span>](../../../../docs/standard/collections/thread-safe/index.md)
