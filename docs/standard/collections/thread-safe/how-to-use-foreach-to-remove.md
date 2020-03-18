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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711239"
---
# <a name="how-to-use-foreach-to-remove-items-in-a-blockingcollection"></a><span data-ttu-id="66d34-102">Nasıl yapılır: Bir BlockingCollection'daki Öğeleri Kaldırmak için ForEach Kullanma</span><span class="sxs-lookup"><span data-stu-id="66d34-102">How to: Use ForEach to Remove Items in a BlockingCollection</span></span>

<span data-ttu-id="66d34-103">Öğeleri <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> ve <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> yöntemini <xref:System.Collections.Concurrent.BlockingCollection%601> kullanarak a'dan öğe almanın yanı sıra, ekleme tamamlanana ve koleksiyon boş olana kadar öğeleri kaldırmak için bir [foreach](../../../csharp/language-reference/keywords/foreach-in.md) (Visual Basic'teki Her biri[için)](../../../visual-basic/language-reference/statements/for-each-next-statement.md) de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66d34-103">In addition to taking items from a <xref:System.Collections.Concurrent.BlockingCollection%601> by using the <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> and <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> method, you can also use a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ([For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) in Visual Basic) to remove items until adding is completed and the collection is empty.</span></span> <span data-ttu-id="66d34-104">Tipik bir `foreach` ()`For Each`döngüden farklı olarak, bu numaralandırma öğeleri kaldırarak kaynak toplamayı değiştirir, çünkü bu *mutasyona* uğrayan numaralandırma veya *tüketen numaralandırma* olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="66d34-104">This is called a *mutating enumeration* or *consuming enumeration* because, unlike a typical `foreach` (`For Each`) loop, this enumerator modifies the source collection by removing items.</span></span>

## <a name="example"></a><span data-ttu-id="66d34-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="66d34-105">Example</span></span>

<span data-ttu-id="66d34-106">Aşağıdaki örnekte, a <xref:System.Collections.Concurrent.BlockingCollection%601> `foreach` (`For Each`) döngüsü kullanılarak bir 'deki tüm öğelerin nasıl kaldırılılabildiğini gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="66d34-106">The following example shows how to remove all the items in a <xref:System.Collections.Concurrent.BlockingCollection%601> by using a `foreach` (`For Each`) loop.</span></span>

[!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
[!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]

<span data-ttu-id="66d34-107">Bu örnek, `foreach` numaralandırılırken her öğenin koleksiyondan kaldırılmasına neden olan tüketen iş parçacığındaki <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> yöntemi içeren bir döngü kullanır.</span><span class="sxs-lookup"><span data-stu-id="66d34-107">This example uses a `foreach` loop with the <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> method in the consuming thread, which causes each item to be removed from the collection as it is enumerated.</span></span> <span data-ttu-id="66d34-108"><xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>herhangi bir zamanda koleksiyonda bulunan maksimum öğe sayısını sınırlar.</span><span class="sxs-lookup"><span data-stu-id="66d34-108"><xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> limits the maximum number of items that are in the collection at any time.</span></span> <span data-ttu-id="66d34-109">Koleksiyonu bu şekilde dizine alma, öğe yoksa veya koleksiyon boşsa tüketici iş parçacığının engellenmesini engeller.</span><span class="sxs-lookup"><span data-stu-id="66d34-109">Enumerating the collection in this way blocks the consumer thread if no items are available or if the collection is empty.</span></span> <span data-ttu-id="66d34-110">Üretici iş parçacığı maddeleri tüketilebileceğinden daha hızlı eklediği için bu örnekte engelleme bir sorun değildir.</span><span class="sxs-lookup"><span data-stu-id="66d34-110">In this example blocking is not a concern because the producer thread adds items faster than they can be consumed.</span></span>

<span data-ttu-id="66d34-111">Maddelerin üretici iş parçacıkları tarafından eklendikleri sırayla numaralandırıldığının garantisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="66d34-111">There is no guarantee that the items are enumerated in the same order in which they are added by the producer threads.</span></span>

<span data-ttu-id="66d34-112">Koleksiyonu değiştirmeden oyalamak `foreach` `For Each` <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> için, yöntem olmadan ( ) kullanmanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="66d34-112">To enumerate the collection without modifying it, just use `foreach` (`For Each`) without the <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> method.</span></span> <span data-ttu-id="66d34-113">Ancak, bu tür numaralandırmanın koleksiyonun tam bir zamanda anlık görüntüsünü temsil ettiğini anlamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="66d34-113">However, it is important to understand that this kind of enumeration represents a snapshot of the collection at a precise point in time.</span></span> <span data-ttu-id="66d34-114">Döngüyü yürütürken diğer iş parçacıkları öğeleri aynı anda ekliyor veya kaldırıyorsa, döngü koleksiyonun gerçek durumunu temsil etmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="66d34-114">If other threads are adding or removing items concurrently while you are executing the loop, then the loop might not represent the actual state of the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="66d34-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66d34-115">See also</span></span>

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [<span data-ttu-id="66d34-116">Paralel Programlama</span><span class="sxs-lookup"><span data-stu-id="66d34-116">Parallel Programming</span></span>](../../../../docs/standard/parallel-programming/index.md)
