---
title: "Nasıl yapılır: Öğeleri Tek Tek Ekleme ve Bir BlockingCollection'dan ve Alma"
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, blocking dictionary
ms.assetid: 38f2f3d8-15e5-4bf4-9c83-2b5b6f22bad1
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 74518f6f56f65668d4c7f073a79c9e7de27d7978
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45516665"
---
# <a name="how-to-add-and-take-items-individually-from-a-blockingcollection"></a><span data-ttu-id="33004-102">Nasıl yapılır: Öğeleri Tek Tek Ekleme ve Bir BlockingCollection'dan ve Alma</span><span class="sxs-lookup"><span data-stu-id="33004-102">How to: Add and Take Items Individually from a BlockingCollection</span></span>
<span data-ttu-id="33004-103">Bu örnek nasıl öğelerinden ekleyip gösterir bir <xref:System.Collections.Concurrent.BlockingCollection%601> bir engelleyici ve engelleyici olmayan bir şekilde.</span><span class="sxs-lookup"><span data-stu-id="33004-103">This example shows how to add and remove items from a <xref:System.Collections.Concurrent.BlockingCollection%601> in both a blocking and a non-blocking manner.</span></span> <span data-ttu-id="33004-104">Daha fazla bilgi için <xref:System.Collections.Concurrent.BlockingCollection%601>, bkz: [BlockingCollection genel bakışı](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).</span><span class="sxs-lookup"><span data-stu-id="33004-104">For more information on <xref:System.Collections.Concurrent.BlockingCollection%601>, see [BlockingCollection Overview](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).</span></span>  
  
 <span data-ttu-id="33004-105">Numaralandırma örneği için bir <xref:System.Collections.Concurrent.BlockingCollection%601> boş ve daha fazla öğe eklenecek kadar bkz [nasıl yapılır: bir BlockingCollection öğeleri kaldırmak için ForEach kullanım](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md).</span><span class="sxs-lookup"><span data-stu-id="33004-105">For an example of how to enumerate a <xref:System.Collections.Concurrent.BlockingCollection%601> until it is empty and no more elements will be added, see [How to: Use ForEach to Remove Items in a BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="33004-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="33004-106">Example</span></span>  
 <span data-ttu-id="33004-107">Bu ilk örnekte, böylece işlemleri geçici olarak koleksiyon geçerli olduğunda engeller ve eklemek için öğeleri (çekerken) boş veya (eklerken) maksimum kapasite veya belirtilen zaman aşımı süresi dolduysa gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="33004-107">This first example shows how to add and take items so that the operations will block if the collection is either temporarily empty (when taking) or at maximum capacity (when adding), or if a specified timeout period has elapsed.</span></span> <span data-ttu-id="33004-108">Oluşturucuda belirtilen en yüksek kapasiteli Blockingcollection'a oluşturulduğunda kapasite üst sınırı engelleme yalnızca etkin olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="33004-108">Note that blocking on maximum capacity is only enabled when the BlockingCollection has been created with a maximum capacity specified in the constructor.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#01](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example01.cs#01)]
 [!code-vb[CDS_BlockingCollection#01](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/simpleblocking.vb#01)]  
  
## <a name="example"></a><span data-ttu-id="33004-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="33004-109">Example</span></span>  
 <span data-ttu-id="33004-110">Bu ikinci örnek ekleyin ve böylece işlemleri değil engeller öğeleri almak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="33004-110">This second example shows how to add and take items so that the operations will not block.</span></span> <span data-ttu-id="33004-111">Hiçbir öğe varsa, sınırlanmış bir koleksiyon üzerinde en yüksek kapasite sınırına veya zaman aşımı süresi dolduysa, ardından <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> veya <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> işlem false döndürür.</span><span class="sxs-lookup"><span data-stu-id="33004-111">If no item is present, maximum capacity on a bounded collection has been reached, or the timeout period has elapsed, then the <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> or <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> operation returns false.</span></span> <span data-ttu-id="33004-112">Böylece, iş parçacığı bir süre için bazı diğer faydalı iş yapmak ve sonra yeniden yeni bir öğe almak veya daha önce eklenemedi aynı öğeyi eklemeyi denediğinizde deneyin.</span><span class="sxs-lookup"><span data-stu-id="33004-112">This allows the thread to do some other useful work for a while and then try again later to either retrieve a new item, or try to add the same item that could not be added previously.</span></span> <span data-ttu-id="33004-113">Programı iptal erişirken uygulamak nasıl de gösterir. bir <xref:System.Collections.Concurrent.BlockingCollection%601>.</span><span class="sxs-lookup"><span data-stu-id="33004-113">The program also demonstrates how to implement cancellation when accessing a <xref:System.Collections.Concurrent.BlockingCollection%601>.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#02](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example02.cs#02)]
 [!code-vb[CDS_BlockingCollection#02](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/nonblockingbc.vb#02)]  
  
## <a name="see-also"></a><span data-ttu-id="33004-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="33004-114">See also</span></span>

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
- [<span data-ttu-id="33004-115">BlockingCollection’a Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="33004-115">BlockingCollection Overview</span></span>](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)
