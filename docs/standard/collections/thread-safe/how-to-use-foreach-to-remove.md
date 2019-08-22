---
title: "Nasıl yapılır: Bir BlockingCollection'daki Öğeleri Kaldırmak için ForEach Kullanma"
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, how to enumerate blocking collection
ms.assetid: 2096103c-22f7-420d-b631-f102bc33a6dd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 10fa77f6948a10959db5f79c37692eba67d47ecd
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666545"
---
# <a name="how-to-use-foreach-to-remove-items-in-a-blockingcollection"></a><span data-ttu-id="f26b6-102">Nasıl yapılır: Bir BlockingCollection'daki Öğeleri Kaldırmak için ForEach Kullanma</span><span class="sxs-lookup"><span data-stu-id="f26b6-102">How to: Use ForEach to Remove Items in a BlockingCollection</span></span>

<span data-ttu-id="f26b6-103">Ve<xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> <xref:System.Collections.Concurrent.BlockingCollection%601> [metodunu kullanarak](../../../csharp/language-reference/keywords/foreach-in.md) öğesinden öğeleri almaya ek olarak, ekleme tamamlanana ve koleksiyon boş olana kadar öğeleri kaldırmak için bir foreach ([her biri için](../../../visual-basic/language-reference/statements/for-each-next-statement.md) Visual Basic) de kullanabilirsiniz. <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A></span><span class="sxs-lookup"><span data-stu-id="f26b6-103">In addition to taking items from a <xref:System.Collections.Concurrent.BlockingCollection%601> by using the <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> and <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> method, you can also use a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ([For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) in Visual Basic) to remove items until adding is completed and the collection is empty.</span></span> <span data-ttu-id="f26b6-104">Bu, `foreach` tipik ( `For Each`) döngüsünün aksine, bu Numaralandırıcı bir numaralandırma veya kullanma *numaralandırması* olarak adlandırılır, çünkü bu Numaralandırıcı, öğeleri kaldırarak kaynak koleksiyonu değiştirir.</span><span class="sxs-lookup"><span data-stu-id="f26b6-104">This is called a *mutating enumeration* or *consuming enumeration* because, unlike a typical `foreach` (`For Each`) loop, this enumerator modifies the source collection by removing items.</span></span>

## <a name="example"></a><span data-ttu-id="f26b6-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="f26b6-105">Example</span></span>

<span data-ttu-id="f26b6-106">Aşağıdaki örnek, bir <xref:System.Collections.Concurrent.BlockingCollection%601> `foreach` (`For Each`) döngüsü kullanarak içindeki tüm öğelerin nasıl kaldırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f26b6-106">The following example shows how to remove all the items in a <xref:System.Collections.Concurrent.BlockingCollection%601> by using a `foreach` (`For Each`) loop.</span></span>

[!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
[!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]

<span data-ttu-id="f26b6-107">Bu örnek, tüketim `foreach` iş parçacığında <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> yöntemi ile bir döngüsü kullanır ve bu, her öğenin, numaralandırıldıktan sonra koleksiyondan kaldırılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="f26b6-107">This example uses a `foreach` loop with the <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> method in the consuming thread, which causes each item to be removed from the collection as it is enumerated.</span></span> <span data-ttu-id="f26b6-108"><xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>Koleksiyonda bulunan en fazla öğe sayısını istediğiniz zaman sınırlandırır.</span><span class="sxs-lookup"><span data-stu-id="f26b6-108"><xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> limits the maximum number of items that are in the collection at any time.</span></span> <span data-ttu-id="f26b6-109">Koleksiyonun bu şekilde numaralandırılması, hiçbir öğe yoksa veya koleksiyon boşsa tüketici iş parçacığını engeller.</span><span class="sxs-lookup"><span data-stu-id="f26b6-109">Enumerating the collection in this way blocks the consumer thread if no items are available or if the collection is empty.</span></span> <span data-ttu-id="f26b6-110">Bu örnekte, üretici iş parçacığı tüketilerek daha hızlı öğe eklediğinden engelleyici bir sorun değildir.</span><span class="sxs-lookup"><span data-stu-id="f26b6-110">In this example blocking is not a concern because the producer thread adds items faster than they can be consumed.</span></span>

<span data-ttu-id="f26b6-111">Öğelerin üretici iş parçacıkları tarafından eklendikleri sırada numaralandırıldıkları garanti yoktur.</span><span class="sxs-lookup"><span data-stu-id="f26b6-111">There is no guarantee that the items are enumerated in the same order in which they are added by the producer threads.</span></span>

<span data-ttu-id="f26b6-112">Koleksiyonu değiştirmeden numaralandırmak için, `foreach` <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> yöntemi olmadan (`For Each`) kullanmanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="f26b6-112">To enumerate the collection without modifying it, just use `foreach` (`For Each`) without the <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> method.</span></span> <span data-ttu-id="f26b6-113">Ancak, bu tür bir numaralandırma, bir koleksiyonun anlık görüntüsünü, zaman içinde kesin bir noktada temsil ettiğini anlamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="f26b6-113">However, it is important to understand that this kind of enumeration represents a snapshot of the collection at a precise point in time.</span></span> <span data-ttu-id="f26b6-114">Diğer iş parçacıkları, döngüyü yürütürken eşzamanlı olarak öğe ekliyor veya kaldırdıysanız, döngü koleksiyonun gerçek durumunu temsil edemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="f26b6-114">If other threads are adding or removing items concurrently while you are executing the loop, then the loop might not represent the actual state of the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="f26b6-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f26b6-115">See also</span></span>

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [<span data-ttu-id="f26b6-116">Paralel Programlama</span><span class="sxs-lookup"><span data-stu-id="f26b6-116">Parallel Programming</span></span>](../../../../docs/standard/parallel-programming/index.md)
