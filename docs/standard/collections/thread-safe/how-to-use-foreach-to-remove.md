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
ms.openlocfilehash: f9a858dea74be63634f887c4204aefa8ac338ad0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711239"
---
# <a name="how-to-use-foreach-to-remove-items-in-a-blockingcollection"></a><span data-ttu-id="235a1-102">Nasıl yapılır: Bir BlockingCollection'daki Öğeleri Kaldırmak için ForEach Kullanma</span><span class="sxs-lookup"><span data-stu-id="235a1-102">How to: Use ForEach to Remove Items in a BlockingCollection</span></span>

<span data-ttu-id="235a1-103"><xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> ve <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> yöntemini kullanarak bir <xref:System.Collections.Concurrent.BlockingCollection%601> öğe almaya ek olarak, ekleme tamamlanana ve koleksiyon boş olana kadar öğeleri kaldırmak için de [ForEach](../../../csharp/language-reference/keywords/foreach-in.md) ([her biri için](../../../visual-basic/language-reference/statements/for-each-next-statement.md) Visual Basic olarak) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="235a1-103">In addition to taking items from a <xref:System.Collections.Concurrent.BlockingCollection%601> by using the <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> and <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> method, you can also use a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ([For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) in Visual Basic) to remove items until adding is completed and the collection is empty.</span></span> <span data-ttu-id="235a1-104">Bu, tipik bir `foreach` (`For Each`) döngüsünün aksine, bu Numaralandırıcı bir *numaralandırma* veya *numaralandırma* kullanma olarak adlandırılır, çünkü bu Numaralandırıcı, öğeleri kaldırarak kaynak koleksiyonu değiştirir.</span><span class="sxs-lookup"><span data-stu-id="235a1-104">This is called a *mutating enumeration* or *consuming enumeration* because, unlike a typical `foreach` (`For Each`) loop, this enumerator modifies the source collection by removing items.</span></span>

## <a name="example"></a><span data-ttu-id="235a1-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="235a1-105">Example</span></span>

<span data-ttu-id="235a1-106">Aşağıdaki örnek, bir <xref:System.Collections.Concurrent.BlockingCollection%601> `foreach` (`For Each`) döngüsü kullanarak tüm öğelerin nasıl kaldırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="235a1-106">The following example shows how to remove all the items in a <xref:System.Collections.Concurrent.BlockingCollection%601> by using a `foreach` (`For Each`) loop.</span></span>

[!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
[!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]

<span data-ttu-id="235a1-107">Bu örnek, tüketim iş parçacığında <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> yöntemi ile `foreach` döngüsünü kullanır ve bu, her öğenin numaralandırıldıkça koleksiyondan kaldırılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="235a1-107">This example uses a `foreach` loop with the <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> method in the consuming thread, which causes each item to be removed from the collection as it is enumerated.</span></span> <span data-ttu-id="235a1-108"><xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> koleksiyonda bulunan en fazla öğe sayısını istediğiniz zaman kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="235a1-108"><xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> limits the maximum number of items that are in the collection at any time.</span></span> <span data-ttu-id="235a1-109">Koleksiyonun bu şekilde numaralandırılması, hiçbir öğe yoksa veya koleksiyon boşsa tüketici iş parçacığını engeller.</span><span class="sxs-lookup"><span data-stu-id="235a1-109">Enumerating the collection in this way blocks the consumer thread if no items are available or if the collection is empty.</span></span> <span data-ttu-id="235a1-110">Bu örnekte, üretici iş parçacığı tüketilerek daha hızlı öğe eklediğinden engelleyici bir sorun değildir.</span><span class="sxs-lookup"><span data-stu-id="235a1-110">In this example blocking is not a concern because the producer thread adds items faster than they can be consumed.</span></span>

<span data-ttu-id="235a1-111">Öğelerin üretici iş parçacıkları tarafından eklendikleri sırada numaralandırıldıkları garanti yoktur.</span><span class="sxs-lookup"><span data-stu-id="235a1-111">There is no guarantee that the items are enumerated in the same order in which they are added by the producer threads.</span></span>

<span data-ttu-id="235a1-112">Koleksiyonu değiştirmeden numaralandırmak için <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> yöntemi olmadan `foreach` (`For Each`) kullanmanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="235a1-112">To enumerate the collection without modifying it, just use `foreach` (`For Each`) without the <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> method.</span></span> <span data-ttu-id="235a1-113">Ancak, bu tür bir numaralandırma, bir koleksiyonun anlık görüntüsünü, zaman içinde kesin bir noktada temsil ettiğini anlamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="235a1-113">However, it is important to understand that this kind of enumeration represents a snapshot of the collection at a precise point in time.</span></span> <span data-ttu-id="235a1-114">Diğer iş parçacıkları, döngüyü yürütürken eşzamanlı olarak öğe ekliyor veya kaldırdıysanız, döngü koleksiyonun gerçek durumunu temsil edemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="235a1-114">If other threads are adding or removing items concurrently while you are executing the loop, then the loop might not represent the actual state of the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="235a1-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="235a1-115">See also</span></span>

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [<span data-ttu-id="235a1-116">Paralel Programlama</span><span class="sxs-lookup"><span data-stu-id="235a1-116">Parallel Programming</span></span>](../../../../docs/standard/parallel-programming/index.md)
