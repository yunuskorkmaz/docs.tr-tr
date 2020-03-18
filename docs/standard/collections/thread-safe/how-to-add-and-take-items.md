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
ms.openlocfilehash: 3f4270d2ec71421bad8974a3e5cd8f1d65db3b74
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711304"
---
# <a name="how-to-add-and-take-items-individually-from-a-blockingcollection"></a><span data-ttu-id="0abb2-102">Nasıl yapılır: Öğeleri Tek Tek Ekleme ve Bir BlockingCollection'dan ve Alma</span><span class="sxs-lookup"><span data-stu-id="0abb2-102">How to: Add and Take Items Individually from a BlockingCollection</span></span>
<span data-ttu-id="0abb2-103">Bu örnek, hem engelleme hem <xref:System.Collections.Concurrent.BlockingCollection%601> de engelleme olmayan bir şekilde öğelerin nasıl eklendiğini ve kaldırılmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0abb2-103">This example shows how to add and remove items from a <xref:System.Collections.Concurrent.BlockingCollection%601> in both a blocking and a non-blocking manner.</span></span> <span data-ttu-id="0abb2-104">Daha fazla <xref:System.Collections.Concurrent.BlockingCollection%601>bilgi için, [bkz.](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)</span><span class="sxs-lookup"><span data-stu-id="0abb2-104">For more information on <xref:System.Collections.Concurrent.BlockingCollection%601>, see [BlockingCollection Overview](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).</span></span>  
  
 <span data-ttu-id="0abb2-105">Boşalana ve başka öğe eklenene kadar a'yı <xref:System.Collections.Concurrent.BlockingCollection%601> nasıl sayısala rendelediğine dair bir örnek için [bkz.](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md)</span><span class="sxs-lookup"><span data-stu-id="0abb2-105">For an example of how to enumerate a <xref:System.Collections.Concurrent.BlockingCollection%601> until it is empty and no more elements will be added, see [How to: Use ForEach to Remove Items in a BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="0abb2-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="0abb2-106">Example</span></span>  
 <span data-ttu-id="0abb2-107">Bu ilk örnek, koleksiyonun geçici olarak boş alması (alırken) veya maksimum kapasitede (eklerken) veya belirli bir zaman aşımı süresi nin dolması durumunda işlemlerin engellemesi için öğelerin nasıl eklendiğini ve alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0abb2-107">This first example shows how to add and take items so that the operations will block if the collection is either temporarily empty (when taking) or at maximum capacity (when adding), or if a specified timeout period has elapsed.</span></span> <span data-ttu-id="0abb2-108">Maksimum kapasitede engellemenin yalnızca kurucuda belirtilen maksimum kapasiteyle BlockingCollection oluşturulduğunda etkinleştirildiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0abb2-108">Note that blocking on maximum capacity is only enabled when the BlockingCollection has been created with a maximum capacity specified in the constructor.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#01](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example01.cs#01)]
 [!code-vb[CDS_BlockingCollection#01](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/simpleblocking.vb#01)]  
  
## <a name="example"></a><span data-ttu-id="0abb2-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="0abb2-109">Example</span></span>  
 <span data-ttu-id="0abb2-110">Bu ikinci örnek, işlemlerin engellememesi için öğelerin nasıl eklendiğini ve alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0abb2-110">This second example shows how to add and take items so that the operations will not block.</span></span> <span data-ttu-id="0abb2-111">Öğe yoksa, sınırlanmış bir koleksiyondaki maksimum kapasiteye ulaşıldı veya zaman aşımı süresi <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> geçti, sonra veya <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> işlem yanlış döndürür.</span><span class="sxs-lookup"><span data-stu-id="0abb2-111">If no item is present, maximum capacity on a bounded collection has been reached, or the timeout period has elapsed, then the <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> or <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> operation returns false.</span></span> <span data-ttu-id="0abb2-112">Bu, iş parçacığının bir süre için başka yararlı işler yapmasına ve daha sonra yeni bir öğeyi almak için yeniden denemesine veya daha önce eklenemeyecek aynı öğeyi eklemeye çalışmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="0abb2-112">This allows the thread to do some other useful work for a while and then try again later to either retrieve a new item, or try to add the same item that could not be added previously.</span></span> <span data-ttu-id="0abb2-113">Program ayrıca bir <xref:System.Collections.Concurrent.BlockingCollection%601>.</span><span class="sxs-lookup"><span data-stu-id="0abb2-113">The program also demonstrates how to implement cancellation when accessing a <xref:System.Collections.Concurrent.BlockingCollection%601>.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#02](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example02.cs#02)]
 [!code-vb[CDS_BlockingCollection#02](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/nonblockingbc.vb#02)]  
  
## <a name="see-also"></a><span data-ttu-id="0abb2-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0abb2-114">See also</span></span>

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [<span data-ttu-id="0abb2-115">BlockingCollection Genel Bakışı</span><span class="sxs-lookup"><span data-stu-id="0abb2-115">BlockingCollection Overview</span></span>](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)
