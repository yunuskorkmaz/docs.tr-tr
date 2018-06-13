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
ms.openlocfilehash: 4f83e260e41acd7c8fff03cf7df0832bab229911
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568504"
---
# <a name="how-to-add-and-take-items-individually-from-a-blockingcollection"></a><span data-ttu-id="5a3ff-102">Nasıl yapılır: Öğeleri Tek Tek Ekleme ve Bir BlockingCollection'dan ve Alma</span><span class="sxs-lookup"><span data-stu-id="5a3ff-102">How to: Add and Take Items Individually from a BlockingCollection</span></span>
<span data-ttu-id="5a3ff-103">Bu örnek öğelerinden ekleyip gösterilmektedir bir <xref:System.Collections.Concurrent.BlockingCollection%601> bir engelleme ve engelleyici olmayan bir şekilde.</span><span class="sxs-lookup"><span data-stu-id="5a3ff-103">This example shows how to add and remove items from a <xref:System.Collections.Concurrent.BlockingCollection%601> in both a blocking and a non-blocking manner.</span></span> <span data-ttu-id="5a3ff-104">Daha fazla bilgi için <xref:System.Collections.Concurrent.BlockingCollection%601>, bkz: [BlockingCollection genel bakışı](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5a3ff-104">For more information on <xref:System.Collections.Concurrent.BlockingCollection%601>, see [BlockingCollection Overview](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).</span></span>  
  
 <span data-ttu-id="5a3ff-105">Numaralandırmak nasıl bir örneği için bir <xref:System.Collections.Concurrent.BlockingCollection%601> boş olduğu ve daha fazla öğe eklenecek kadar bkz [nasıl yapılır: bir BlockingCollection öğeleri kaldırmak için kullanım ForEach](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md).</span><span class="sxs-lookup"><span data-stu-id="5a3ff-105">For an example of how to enumerate a <xref:System.Collections.Concurrent.BlockingCollection%601> until it is empty and no more elements will be added, see [How to: Use ForEach to Remove Items in a BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="5a3ff-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="5a3ff-106">Example</span></span>  
 <span data-ttu-id="5a3ff-107">Bu ilk örnek ya da geçici olarak koleksiyonudur işlemlerini engeller böylece eklemek ve almak için öğeleri (alırken) boş nasıl veya (eklerken) maksimum kapasite veya belirtilen zaman aşımı süresi geçti gösterir.</span><span class="sxs-lookup"><span data-stu-id="5a3ff-107">This first example shows how to add and take items so that the operations will block if the collection is either temporarily empty (when taking) or at maximum capacity (when adding), or if a specified timeout period has elapsed.</span></span> <span data-ttu-id="5a3ff-108">BlockingCollection oluşturucuda belirtilen en yüksek kapasiteli oluşturulduğunda maksimum kapasite engelleme yalnızca etkin olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5a3ff-108">Note that blocking on maximum capacity is only enabled when the BlockingCollection has been created with a maximum capacity specified in the constructor.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#01](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example01.cs#01)]
 [!code-vb[CDS_BlockingCollection#01](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/simpleblocking.vb#01)]  
  
## <a name="example"></a><span data-ttu-id="5a3ff-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="5a3ff-109">Example</span></span>  
 <span data-ttu-id="5a3ff-110">Bu ikinci örnek ekleme ve işlemleri değil engeller öğeleri alın gösterir.</span><span class="sxs-lookup"><span data-stu-id="5a3ff-110">This second example shows how to add and take items so that the operations will not block.</span></span> <span data-ttu-id="5a3ff-111">Öğe varsa, sınırlı bir koleksiyonda maksimum kapasite ulaşıldı veya zaman aşımı süresi geçti, sonra <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> veya <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> işlemi false döndürür.</span><span class="sxs-lookup"><span data-stu-id="5a3ff-111">If no item is present, maximum capacity on a bounded collection has been reached, or the timeout period has elapsed, then the <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> or <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> operation returns false.</span></span> <span data-ttu-id="5a3ff-112">Bu, bazı diğer yararlı için biraz çalışmanız ve sonra yeniden daha sonra yeni bir öğe almak ya da daha önce eklenemedi aynı öğe eklemeyi denemek iş parçacığı sağlar.</span><span class="sxs-lookup"><span data-stu-id="5a3ff-112">This allows the thread to do some other useful work for a while and then try again later to either retrieve a new item, or try to add the same item that could not be added previously.</span></span> <span data-ttu-id="5a3ff-113">Program ayrıca iptal erişirken uygulamak gösterilmiştir bir <xref:System.Collections.Concurrent.BlockingCollection%601>.</span><span class="sxs-lookup"><span data-stu-id="5a3ff-113">The program also demonstrates how to implement cancellation when accessing a <xref:System.Collections.Concurrent.BlockingCollection%601>.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#02](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example02.cs#02)]
 [!code-vb[CDS_BlockingCollection#02](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/nonblockingbc.vb#02)]  
  
## <a name="see-also"></a><span data-ttu-id="5a3ff-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5a3ff-114">See Also</span></span>  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 [<span data-ttu-id="5a3ff-115">BlockingCollection’a Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5a3ff-115">BlockingCollection Overview</span></span>](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)
