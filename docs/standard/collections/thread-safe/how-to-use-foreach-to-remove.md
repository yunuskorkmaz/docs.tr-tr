---
title: "Nasıl yapılır: Bir Blockingcollection'daki öğeleri kaldırmak için ForEach kullanma"
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
ms.openlocfilehash: 6d13f123953c32cae01df501c0e251ec29b0478b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57367511"
---
# <a name="how-to-use-foreach-to-remove-items-in-a-blockingcollection"></a><span data-ttu-id="1d127-102">Nasıl yapılır: Bir Blockingcollection'daki öğeleri kaldırmak için ForEach kullanma</span><span class="sxs-lookup"><span data-stu-id="1d127-102">How to: Use ForEach to Remove Items in a BlockingCollection</span></span>

<span data-ttu-id="1d127-103">Öğeleri alma yanı sıra bir <xref:System.Collections.Concurrent.BlockingCollection%601> kullanarak <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> ve <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> yöntemini de kullanabilirsiniz bir [foreach](~/docs/csharp/language-reference/keywords/foreach-in.md) ([her](~/docs/visual-basic/language-reference/statements/for-each-next-statement.md) Visual Basic'te) ekleme olana kadar öğeleri kaldırmak için tamamlandı ve boş bir koleksiyondur.</span><span class="sxs-lookup"><span data-stu-id="1d127-103">In addition to taking items from a <xref:System.Collections.Concurrent.BlockingCollection%601> by using the <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> and <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> method, you can also use a [foreach](~/docs/csharp/language-reference/keywords/foreach-in.md) ([For Each](~/docs/visual-basic/language-reference/statements/for-each-next-statement.md) in Visual Basic) to remove items until adding is completed and the collection is empty.</span></span> <span data-ttu-id="1d127-104">Bu olarak adlandırılır bir *numaralandırma diziyi* veya *numaralandırma tüketen* olduğundan, tipik bir aksine `foreach` (`For Each`) döngü, bu Numaralandırıcının kaynak koleksiyonu kaldırarak değiştirir öğeleri.</span><span class="sxs-lookup"><span data-stu-id="1d127-104">This is called a *mutating enumeration* or *consuming enumeration* because, unlike a typical `foreach` (`For Each`) loop, this enumerator modifies the source collection by removing items.</span></span>

## <a name="example"></a><span data-ttu-id="1d127-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="1d127-105">Example</span></span>

<span data-ttu-id="1d127-106">Aşağıdaki örnek, tüm öğeleri kaldırmak gösterilmiştir bir <xref:System.Collections.Concurrent.BlockingCollection%601> kullanarak bir `foreach` (`For Each`) döngü.</span><span class="sxs-lookup"><span data-stu-id="1d127-106">The following example shows how to remove all the items in a <xref:System.Collections.Concurrent.BlockingCollection%601> by using a `foreach` (`For Each`) loop.</span></span>

[!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
[!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]

<span data-ttu-id="1d127-107">Bu örnekte bir `foreach` ile döngü <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> yöntemi kullanan akıştaki her öğesi, tıklamanızdır Koleksiyondan kaldırılacak neden olur.</span><span class="sxs-lookup"><span data-stu-id="1d127-107">This example uses a `foreach` loop with the <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> method in the consuming thread, which causes each item to be removed from the collection as it is enumerated.</span></span> <span data-ttu-id="1d127-108"><xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> herhangi bir zamanda koleksiyondaki öğeleri maksimum sayısını sınırlar.</span><span class="sxs-lookup"><span data-stu-id="1d127-108"><xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> limits the maximum number of items that are in the collection at any time.</span></span> <span data-ttu-id="1d127-109">Koleksiyonu bu şekilde, tüketicinin iş parçacığıyla hiçbir öğesi yok veya varsa koleksiyon boş olup olmadığını engeller.</span><span class="sxs-lookup"><span data-stu-id="1d127-109">Enumerating the collection in this way blocks the consumer thread if no items are available or if the collection is empty.</span></span> <span data-ttu-id="1d127-110">Bu örnekte engelleyen önemli öğeleri kullanılabilir daha hızlı üretici iş parçacığı ekler için değil.</span><span class="sxs-lookup"><span data-stu-id="1d127-110">In this example blocking is not a concern because the producer thread adds items faster than they can be consumed.</span></span>

<span data-ttu-id="1d127-111">Aynı sırada üretici iş parçacıkları tarafından eklenen öğeler numaralandırılır garantisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="1d127-111">There is no guarantee that the items are enumerated in the same order in which they are added by the producer threads.</span></span>

<span data-ttu-id="1d127-112">Değişiklik yapmadan derlemesini için yalnızca kullanın `foreach` (`For Each`) olmadan <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1d127-112">To enumerate the collection without modifying it, just use `foreach` (`For Each`) without the <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> method.</span></span> <span data-ttu-id="1d127-113">Ancak, bu tür bir sabit listesi bir anlık görüntü zaman içinde kesin bir noktada koleksiyonun gösterdiğini anlamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="1d127-113">However, it is important to understand that this kind of enumeration represents a snapshot of the collection at a precise point in time.</span></span> <span data-ttu-id="1d127-114">Diğer iş parçacıklarını ekliyor veya döngü eşzamanlı olarak yürütülmesi sırasında öğeleri kaldırma, ardından döngü koleksiyonu gerçek durumuyla temsil edemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="1d127-114">If other threads are adding or removing items concurrently while you are executing the loop, then the loop might not represent the actual state of the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="1d127-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d127-115">See also</span></span>

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [<span data-ttu-id="1d127-116">Paralel Programlama</span><span class="sxs-lookup"><span data-stu-id="1d127-116">Parallel Programming</span></span>](../../../../docs/standard/parallel-programming/index.md)
