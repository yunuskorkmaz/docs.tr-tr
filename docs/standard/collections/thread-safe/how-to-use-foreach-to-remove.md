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
ms.openlocfilehash: 46638d2cd8078fefebc0eacc4b8f7798ffe178ff
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288907"
---
# <a name="use-foreach-to-remove-items-in-a-blockingcollection"></a>Bir BlockingCollection içindeki öğeleri kaldırmak için foreach kullanma

Ve metodunu kullanarak öğesinden öğeleri almaya ek olarak <xref:System.Collections.Concurrent.BlockingCollection%601> <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> , ekleme tamamlanana ve koleksiyon boş olana kadar öğeleri kaldırmak için bir [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ([her biri için](../../../visual-basic/language-reference/statements/for-each-next-statement.md) Visual Basic) de kullanabilirsiniz <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> . Bu, tipik () döngüsünün aksine, bu Numaralandırıcı bir *numaralandırma* veya kullanma *numaralandırması* olarak adlandırılır `foreach` , çünkü `For Each` Bu Numaralandırıcı, öğeleri kaldırarak kaynak koleksiyonu değiştirir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir <xref:System.Collections.Concurrent.BlockingCollection%601> `foreach` () döngüsü kullanarak içindeki tüm öğelerin nasıl kaldırılacağını gösterir `For Each` .

[!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
[!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]

Bu örnek `foreach` <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> , tüketim iş parçacığında yöntemi ile bir döngüsü kullanır ve bu, her öğenin, numaralandırıldıktan sonra koleksiyondan kaldırılmasına neden olur. <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>Koleksiyonda bulunan en fazla öğe sayısını istediğiniz zaman sınırlandırır. Koleksiyonun bu şekilde numaralandırılması, hiçbir öğe yoksa veya koleksiyon boşsa tüketici iş parçacığını engeller. Bu örnekte, üretici iş parçacığı tüketilerek daha hızlı öğe eklediğinden engelleyici bir sorun değildir.

, <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> Bir döndürür `IEnumerable<T>` , bu nedenle Order garanti edilemez. Ancak, dahili olarak bir <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> temel koleksiyon türü olarak kullanılır. Bu, ilk ilk çıkar (FIFO) Sıralamalı nesneleri sıradan sıradan çıkar. Eşzamanlı olarak yapılan çağrılar <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> yapılırsa, bu kişiler yarışacaktır. Tek bir Numaralandırmadaki bir öğe tüketilen (sıraya alınmış) bir öğe diğer içinde gözlemlenemez.

Koleksiyonu değiştirmeden numaralandırmak için, `foreach` yöntemi olmadan () kullanmanız yeterlidir `For Each` <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> . Ancak, bu tür bir numaralandırma, bir koleksiyonun anlık görüntüsünü, zaman içinde kesin bir noktada temsil ettiğini anlamak önemlidir. Diğer iş parçacıkları, döngüyü yürütürken eşzamanlı olarak öğe ekliyor veya kaldırdıysanız, döngü koleksiyonun gerçek durumunu temsil edemeyebilir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Paralel programlama](../../parallel-programming/index.md)
