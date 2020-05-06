---
title: Bir BlockingCollection içindeki öğeleri kaldırmak için foreach kullanma
ms.date: 05/04/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, how to enumerate blocking collection
ms.assetid: 2096103c-22f7-420d-b631-f102bc33a6dd
ms.openlocfilehash: 1255fcda89396ea8ff9abf6cf111e6dd9ea5a87d
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82861006"
---
# <a name="use-foreach-to-remove-items-in-a-blockingcollection"></a>Bir BlockingCollection içindeki öğeleri kaldırmak için foreach kullanma

<xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> Ve <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> <xref:System.Collections.Concurrent.BlockingCollection%601> metodunu kullanarak öğesinden öğeleri almaya ek olarak, ekleme tamamlanana ve koleksiyon boş olana kadar öğeleri kaldırmak <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> için bir [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ([her biri için](../../../visual-basic/language-reference/statements/for-each-next-statement.md) Visual Basic) de kullanabilirsiniz. `foreach` Bu, tipik (`For Each`) döngüsünün aksine, bu Numaralandırıcı bir *numaralandırma* veya kullanma *numaralandırması* olarak adlandırılır, çünkü bu Numaralandırıcı, öğeleri kaldırarak kaynak koleksiyonu değiştirir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir <xref:System.Collections.Concurrent.BlockingCollection%601> `foreach` (`For Each`) döngüsü kullanarak içindeki tüm öğelerin nasıl kaldırılacağını gösterir.

[!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
[!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]

Bu örnek, tüketim `foreach` iş parçacığında <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> yöntemi ile bir döngüsü kullanır ve bu, her öğenin, numaralandırıldıktan sonra koleksiyondan kaldırılmasına neden olur. <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>Koleksiyonda bulunan en fazla öğe sayısını istediğiniz zaman sınırlandırır. Koleksiyonun bu şekilde numaralandırılması, hiçbir öğe yoksa veya koleksiyon boşsa tüketici iş parçacığını engeller. Bu örnekte, üretici iş parçacığı tüketilerek daha hızlı öğe eklediğinden engelleyici bir sorun değildir.

, <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> Bir `IEnumerable<T>`döndürür, bu nedenle Order garanti edilemez. Ancak, dahili olarak <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> bir temel koleksiyon türü olarak kullanılır. Bu, ilk ilk çıkar (FIFO) Sıralamalı nesneleri sıradan sıradan çıkar. Eşzamanlı olarak <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> yapılan çağrılar yapılırsa, bu kişiler yarışacaktır. Tek bir Numaralandırmadaki bir öğe tüketilen (sıraya alınmış) bir öğe diğer içinde gözlemlenemez.

Koleksiyonu değiştirmeden numaralandırmak için, `foreach` `For Each` <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> yöntemi olmadan () kullanmanız yeterlidir. Ancak, bu tür bir numaralandırma, bir koleksiyonun anlık görüntüsünü, zaman içinde kesin bir noktada temsil ettiğini anlamak önemlidir. Diğer iş parçacıkları, döngüyü yürütürken eşzamanlı olarak öğe ekliyor veya kaldırdıysanız, döngü koleksiyonun gerçek durumunu temsil edemeyebilir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Paralel programlama](../../../../docs/standard/parallel-programming/index.md)
