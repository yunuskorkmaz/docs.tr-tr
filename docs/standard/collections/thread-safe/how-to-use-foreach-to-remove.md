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
# <a name="how-to-use-foreach-to-remove-items-in-a-blockingcollection"></a>Nasıl yapılır: Bir BlockingCollection'daki Öğeleri Kaldırmak için ForEach Kullanma

Ve<xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> <xref:System.Collections.Concurrent.BlockingCollection%601> [metodunu kullanarak](../../../csharp/language-reference/keywords/foreach-in.md) öğesinden öğeleri almaya ek olarak, ekleme tamamlanana ve koleksiyon boş olana kadar öğeleri kaldırmak için bir foreach ([her biri için](../../../visual-basic/language-reference/statements/for-each-next-statement.md) Visual Basic) de kullanabilirsiniz. <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> Bu, `foreach` tipik ( `For Each`) döngüsünün aksine, bu Numaralandırıcı bir numaralandırma veya kullanma *numaralandırması* olarak adlandırılır, çünkü bu Numaralandırıcı, öğeleri kaldırarak kaynak koleksiyonu değiştirir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir <xref:System.Collections.Concurrent.BlockingCollection%601> `foreach` (`For Each`) döngüsü kullanarak içindeki tüm öğelerin nasıl kaldırılacağını gösterir.

[!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
[!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]

Bu örnek, tüketim `foreach` iş parçacığında <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> yöntemi ile bir döngüsü kullanır ve bu, her öğenin, numaralandırıldıktan sonra koleksiyondan kaldırılmasına neden olur. <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>Koleksiyonda bulunan en fazla öğe sayısını istediğiniz zaman sınırlandırır. Koleksiyonun bu şekilde numaralandırılması, hiçbir öğe yoksa veya koleksiyon boşsa tüketici iş parçacığını engeller. Bu örnekte, üretici iş parçacığı tüketilerek daha hızlı öğe eklediğinden engelleyici bir sorun değildir.

Öğelerin üretici iş parçacıkları tarafından eklendikleri sırada numaralandırıldıkları garanti yoktur.

Koleksiyonu değiştirmeden numaralandırmak için, `foreach` <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> yöntemi olmadan (`For Each`) kullanmanız yeterlidir. Ancak, bu tür bir numaralandırma, bir koleksiyonun anlık görüntüsünü, zaman içinde kesin bir noktada temsil ettiğini anlamak önemlidir. Diğer iş parçacıkları, döngüyü yürütürken eşzamanlı olarak öğe ekliyor veya kaldırdıysanız, döngü koleksiyonun gerçek durumunu temsil edemeyebilir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Paralel Programlama](../../../../docs/standard/parallel-programming/index.md)
