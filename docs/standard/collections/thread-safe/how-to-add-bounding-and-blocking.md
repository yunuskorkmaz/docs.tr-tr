---
title: "Nasıl yapılır: Koleksiyona Sınırlama ve Engelleme İşlevi Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- thread-safe collections, custom blocking collections
ms.assetid: 4c2492de-3876-4873-b5a1-000bb404d770
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7fe57d99382c3472d0af5e5f64f7b237692b921b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-add-bounding-and-blocking-functionality-to-a-collection"></a><span data-ttu-id="0e369-102">Nasıl yapılır: Koleksiyona Sınırlama ve Engelleme İşlevi Ekleme</span><span class="sxs-lookup"><span data-stu-id="0e369-102">How to: Add Bounding and Blocking Functionality to a Collection</span></span>
<span data-ttu-id="0e369-103">Bu örnek sınırlama ve engelleme işlevi bir özel koleksiyon sınıfına uygulayarak nasıl ekleneceğini gösterir <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType> arabirim sınıfında ve dahili depolama mekanizması olarak bir sınıf örneği kullanarak bir <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0e369-103">This example shows how to add bounding and blocking functionality to a custom collection class by implementing the <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType> interface in the class, and then using a class instance as the internal storage mechanism for a <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0e369-104">Sınırlama ve engelleme hakkında daha fazla bilgi için bkz: [BlockingCollection genel bakışı](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0e369-104">For more information about bounding and blocking, see [BlockingCollection Overview](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e369-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="0e369-105">Example</span></span>  
 <span data-ttu-id="0e369-106">Özel koleksiyon sınıfı içinde öncelik düzeyleri temsil edilen bir dizi gibi bir temel öncelik sırasıdır <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="0e369-106">The custom collection class is a basic priority queue in which the priority levels are represented as an array of <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> objects.</span></span> <span data-ttu-id="0e369-107">Hiçbir ek sıralama her sıra içinde gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="0e369-107">No additional ordering is performed within each queue.</span></span>  
  
 <span data-ttu-id="0e369-108">İstemci kodu üç görev başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="0e369-108">In the client code, three tasks are started.</span></span> <span data-ttu-id="0e369-109">Yürütme sırasında herhangi bir noktada iptal etkinleştirmek için klavye vuruşları için ilk görev yalnızca yoklar.</span><span class="sxs-lookup"><span data-stu-id="0e369-109">The first task just polls for keyboard strokes to enable cancellation at any point during execution.</span></span> <span data-ttu-id="0e369-110">İkinci görev üretici parçacığıdır; engelleme koleksiyona yeni öğeler ekler ve her bir öğeyi rastgele bir değere göre bir öncelik verir.</span><span class="sxs-lookup"><span data-stu-id="0e369-110">The second task is the producer thread; it adds new items to the blocking collection and gives each item a priority based on a random value.</span></span> <span data-ttu-id="0e369-111">Üçüncü görev öğeleri kullanılabilir olduklarında koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="0e369-111">The third task removes items from the collection as they become available.</span></span>  
  
 <span data-ttu-id="0e369-112">Diğer daha hızlı çalıştırma iş parçacığı birini yaparak uygulama davranışına göre ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e369-112">You can adjust the behavior of the application by making one of the threads run faster than the other.</span></span> <span data-ttu-id="0e369-113">Üretici daha hızlı çalıştırıyorsa, bu zaten oluşturucuda belirtilen öğe sayısını içeriyorsa eklenmesini öğeleri engelleme koleksiyonu engeller gibi sınırlayıcı işlevselliği fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="0e369-113">If the producer runs faster, you will notice the bounding functionality as the blocking collection prevents items from being added if it already contains the number of items that is specified in the constructor.</span></span> <span data-ttu-id="0e369-114">Tüketici daha hızlı çalıştırıyorsa, engelleme işlevine tüketici olarak eklenmesi için yeni bir öğe için bekleyeceği fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="0e369-114">If the consumer runs faster, you will notice the blocking functionality as the consumer waits for a new item to be added.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#06](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/prodcon.cs#06)]  
  
 <span data-ttu-id="0e369-115">Varsayılan olarak, depolama alanı için bir <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> olan <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0e369-115">By default, the storage for a <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> is <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e369-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0e369-116">See Also</span></span>  
 [<span data-ttu-id="0e369-117">İş Parçacığı Güvenli Koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="0e369-117">Thread-Safe Collections</span></span>](../../../../docs/standard/collections/thread-safe/index.md)
