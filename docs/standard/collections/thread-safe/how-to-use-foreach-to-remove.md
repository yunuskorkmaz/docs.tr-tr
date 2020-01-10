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
# <a name="how-to-use-foreach-to-remove-items-in-a-blockingcollection"></a>Nasıl yapılır: Bir BlockingCollection'daki Öğeleri Kaldırmak için ForEach Kullanma

<xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> ve <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> yöntemini kullanarak bir <xref:System.Collections.Concurrent.BlockingCollection%601> öğe almaya ek olarak, ekleme tamamlanana ve koleksiyon boş olana kadar öğeleri kaldırmak için de [ForEach](../../../csharp/language-reference/keywords/foreach-in.md) ([her biri için](../../../visual-basic/language-reference/statements/for-each-next-statement.md) Visual Basic olarak) kullanabilirsiniz. Bu, tipik bir `foreach` (`For Each`) döngüsünün aksine, bu Numaralandırıcı bir *numaralandırma* veya *numaralandırma* kullanma olarak adlandırılır, çünkü bu Numaralandırıcı, öğeleri kaldırarak kaynak koleksiyonu değiştirir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir <xref:System.Collections.Concurrent.BlockingCollection%601> `foreach` (`For Each`) döngüsü kullanarak tüm öğelerin nasıl kaldırılacağını gösterir.

[!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
[!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]

Bu örnek, tüketim iş parçacığında <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> yöntemi ile `foreach` döngüsünü kullanır ve bu, her öğenin numaralandırıldıkça koleksiyondan kaldırılmasına neden olur. <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> koleksiyonda bulunan en fazla öğe sayısını istediğiniz zaman kısıtlar. Koleksiyonun bu şekilde numaralandırılması, hiçbir öğe yoksa veya koleksiyon boşsa tüketici iş parçacığını engeller. Bu örnekte, üretici iş parçacığı tüketilerek daha hızlı öğe eklediğinden engelleyici bir sorun değildir.

Öğelerin üretici iş parçacıkları tarafından eklendikleri sırada numaralandırıldıkları garanti yoktur.

Koleksiyonu değiştirmeden numaralandırmak için <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> yöntemi olmadan `foreach` (`For Each`) kullanmanız yeterlidir. Ancak, bu tür bir numaralandırma, bir koleksiyonun anlık görüntüsünü, zaman içinde kesin bir noktada temsil ettiğini anlamak önemlidir. Diğer iş parçacıkları, döngüyü yürütürken eşzamanlı olarak öğe ekliyor veya kaldırdıysanız, döngü koleksiyonun gerçek durumunu temsil edemeyebilir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Paralel Programlama](../../../../docs/standard/parallel-programming/index.md)
