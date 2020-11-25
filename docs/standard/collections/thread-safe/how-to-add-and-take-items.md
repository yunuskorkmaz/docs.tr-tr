---
title: "Nasıl yapılır: Öğeleri Tek Tek Ekleme ve Bir BlockingCollection'dan ve Alma"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, blocking dictionary
ms.assetid: 38f2f3d8-15e5-4bf4-9c83-2b5b6f22bad1
ms.openlocfilehash: de65dbdcc3239016a16bc12f9254bb99637e45b4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733496"
---
# <a name="how-to-add-and-take-items-individually-from-a-blockingcollection"></a><span data-ttu-id="63d80-102">Nasıl yapılır: Öğeleri Tek Tek Ekleme ve Bir BlockingCollection'dan ve Alma</span><span class="sxs-lookup"><span data-stu-id="63d80-102">How to: Add and Take Items Individually from a BlockingCollection</span></span>

<span data-ttu-id="63d80-103">Bu örnek, bir <xref:System.Collections.Concurrent.BlockingCollection%601> engelleme ve engellenmeyen bir şekilde içindeki öğesinden öğe ekleme ve kaldırma işlemlerinin nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="63d80-103">This example shows how to add and remove items from a <xref:System.Collections.Concurrent.BlockingCollection%601> in both a blocking and a non-blocking manner.</span></span> <span data-ttu-id="63d80-104">Hakkında daha fazla bilgi için <xref:System.Collections.Concurrent.BlockingCollection%601> bkz. [BlockingCollection genel bakış](blockingcollection-overview.md).</span><span class="sxs-lookup"><span data-stu-id="63d80-104">For more information on <xref:System.Collections.Concurrent.BlockingCollection%601>, see [BlockingCollection Overview](blockingcollection-overview.md).</span></span>  
  
 <span data-ttu-id="63d80-105"><xref:System.Collections.Concurrent.BlockingCollection%601>Boş olana kadar bir veya daha fazla öğe eklenene kadar nasıl numaralandırılacağını gösteren bir örnek için bkz. [nasıl yapılır: bir BlockingCollection Içindeki öğeleri kaldırmak Için foreach kullanma](how-to-use-foreach-to-remove.md).</span><span class="sxs-lookup"><span data-stu-id="63d80-105">For an example of how to enumerate a <xref:System.Collections.Concurrent.BlockingCollection%601> until it is empty and no more elements will be added, see [How to: Use ForEach to Remove Items in a BlockingCollection](how-to-use-foreach-to-remove.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="63d80-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="63d80-106">Example</span></span>  

 <span data-ttu-id="63d80-107">Bu ilk örnek, koleksiyonun geçici olarak boş (alma sırasında) veya en yüksek kapasiteye (eklenirken) ya da belirtilen bir zaman aşımı süresi geçtiğinde işlemleri engelleyecek şekilde öğelerin nasıl ekleneceğini ve alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="63d80-107">This first example shows how to add and take items so that the operations will block if the collection is either temporarily empty (when taking) or at maximum capacity (when adding), or if a specified timeout period has elapsed.</span></span> <span data-ttu-id="63d80-108">Maksimum kapasiteden engelleme özelliğinin yalnızca, Oluşturucu içinde belirtilen en fazla kapasite ile BlockingCollection oluşturulduğunda etkinleştirildiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="63d80-108">Note that blocking on maximum capacity is only enabled when the BlockingCollection has been created with a maximum capacity specified in the constructor.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#01](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example01.cs#01)]
 [!code-vb[CDS_BlockingCollection#01](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/simpleblocking.vb#01)]  
  
## <a name="example"></a><span data-ttu-id="63d80-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="63d80-109">Example</span></span>  

 <span data-ttu-id="63d80-110">Bu ikinci örnek işlemlerin nasıl ekleneceğini ve öğelerin nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="63d80-110">This second example shows how to add and take items so that the operations will not block.</span></span> <span data-ttu-id="63d80-111">Hiçbir öğe yoksa, sınırlanmış bir koleksiyondaki maksimum kapasiteye ulaşıldı veya zaman aşımı süresi doldu, <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> ya da <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> işlem yanlış döndürür.</span><span class="sxs-lookup"><span data-stu-id="63d80-111">If no item is present, maximum capacity on a bounded collection has been reached, or the timeout period has elapsed, then the <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> or <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> operation returns false.</span></span> <span data-ttu-id="63d80-112">Bu, iş parçacığının bir süre boyunca başka bir faydalı iş yapmasına ve sonra yeni bir öğe almayı veya daha önce eklenemeyen aynı öğeyi eklemeyi denemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="63d80-112">This allows the thread to do some other useful work for a while and then try again later to either retrieve a new item, or try to add the same item that could not be added previously.</span></span> <span data-ttu-id="63d80-113">Program ayrıca bir öğesine erişirken iptalin nasıl uygulanacağını gösterir <xref:System.Collections.Concurrent.BlockingCollection%601> .</span><span class="sxs-lookup"><span data-stu-id="63d80-113">The program also demonstrates how to implement cancellation when accessing a <xref:System.Collections.Concurrent.BlockingCollection%601>.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#02](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example02.cs#02)]
 [!code-vb[CDS_BlockingCollection#02](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/nonblockingbc.vb#02)]  
  
## <a name="see-also"></a><span data-ttu-id="63d80-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="63d80-114">See also</span></span>

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [<span data-ttu-id="63d80-115">BlockingCollection Genel Bakışı</span><span class="sxs-lookup"><span data-stu-id="63d80-115">BlockingCollection Overview</span></span>](blockingcollection-overview.md)
