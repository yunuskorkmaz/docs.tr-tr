---
description: 'Daha fazla bilgi edinin: nasıl yapılır: koleksiyona sınırlama ve engelleme Işlevi ekleme'
title: 'Nasıl yapılır: Koleksiyona Sınırlama ve Engelleme İşlevi Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- thread-safe collections, custom blocking collections
ms.assetid: 4c2492de-3876-4873-b5a1-000bb404d770
ms.openlocfilehash: c44febe0a7b2155c61b12c280d830ad7b028d326
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99676072"
---
# <a name="how-to-add-bounding-and-blocking-functionality-to-a-collection"></a><span data-ttu-id="e56c5-103">Nasıl yapılır: Koleksiyona Sınırlama ve Engelleme İşlevi Ekleme</span><span class="sxs-lookup"><span data-stu-id="e56c5-103">How to: Add Bounding and Blocking Functionality to a Collection</span></span>

<span data-ttu-id="e56c5-104">Bu örnek <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType> , sınıfında arabirimini uygulayarak ve sonra bir sınıf örneğini bir için iç depolama mekanizması olarak kullanarak özel bir koleksiyon sınıfına nasıl sınırlama ve engelleme işlevselliği ekleneceğini gösterir <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e56c5-104">This example shows how to add bounding and blocking functionality to a custom collection class by implementing the <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType> interface in the class, and then using a class instance as the internal storage mechanism for a <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e56c5-105">Sınırlama ve engelleme hakkında daha fazla bilgi için bkz. [BlockingCollection genel bakış](blockingcollection-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e56c5-105">For more information about bounding and blocking, see [BlockingCollection Overview](blockingcollection-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e56c5-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="e56c5-106">Example</span></span>  

 <span data-ttu-id="e56c5-107">Özel koleksiyon sınıfı, öncelik düzeylerinin bir nesne dizisi olarak temsil edildiği temel bir öncelik kuyruğudur <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e56c5-107">The custom collection class is a basic priority queue in which the priority levels are represented as an array of <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> objects.</span></span> <span data-ttu-id="e56c5-108">Her sıra içinde ek sıralama yapılmaz.</span><span class="sxs-lookup"><span data-stu-id="e56c5-108">No additional ordering is performed within each queue.</span></span>  
  
 <span data-ttu-id="e56c5-109">İstemci kodunda, üç görev başlatılır.</span><span class="sxs-lookup"><span data-stu-id="e56c5-109">In the client code, three tasks are started.</span></span> <span data-ttu-id="e56c5-110">İlk görev, yürütme sırasında herhangi bir noktada iptali etkinleştirmek üzere klavye vuruşları için yalnızca yoklar.</span><span class="sxs-lookup"><span data-stu-id="e56c5-110">The first task just polls for keyboard strokes to enable cancellation at any point during execution.</span></span> <span data-ttu-id="e56c5-111">İkinci görev üretici iş parçacığıdır; engelleme koleksiyonuna yeni öğeler ekler ve her öğeye rastgele bir değer temelinde öncelik verir.</span><span class="sxs-lookup"><span data-stu-id="e56c5-111">The second task is the producer thread; it adds new items to the blocking collection and gives each item a priority based on a random value.</span></span> <span data-ttu-id="e56c5-112">Üçüncü görev, öğeleri kullanılabilir hale geldiğinde koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="e56c5-112">The third task removes items from the collection as they become available.</span></span>  
  
 <span data-ttu-id="e56c5-113">İş parçacıklarından birini diğerinin daha hızlı çalıştırmasını sağlayarak uygulamanın davranışını ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e56c5-113">You can adjust the behavior of the application by making one of the threads run faster than the other.</span></span> <span data-ttu-id="e56c5-114">Üretici daha hızlı çalışırsa, blok koleksiyon, Oluşturucu üzerinde belirtilen öğelerin sayısını zaten içeriyorsa öğelerin eklenmesini engellediğini fark eder.</span><span class="sxs-lookup"><span data-stu-id="e56c5-114">If the producer runs faster, you will notice the bounding functionality as the blocking collection prevents items from being added if it already contains the number of items that is specified in the constructor.</span></span> <span data-ttu-id="e56c5-115">Tüketici daha hızlı çalışırsa, tüketici yeni bir öğenin eklenmesini beklediği için engelleme işlevini fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="e56c5-115">If the consumer runs faster, you will notice the blocking functionality as the consumer waits for a new item to be added.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#06](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/prodcon.cs#06)]  
  
 <span data-ttu-id="e56c5-116">Varsayılan olarak, bir için depolama alanı <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e56c5-116">By default, the storage for a <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> is <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e56c5-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e56c5-117">See also</span></span>

- [<span data-ttu-id="e56c5-118">İş parçacığı güvenli Koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="e56c5-118">Thread-Safe Collections</span></span>](index.md)
