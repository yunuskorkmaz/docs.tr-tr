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
# <a name="how-to-use-foreach-to-remove-items-in-a-blockingcollection"></a>Nasıl yapılır: Bir BlockingCollection'daki Öğeleri Kaldırmak için ForEach Kullanma

Öğeleri <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> ve <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> yöntemini <xref:System.Collections.Concurrent.BlockingCollection%601> kullanarak a'dan öğe almanın yanı sıra, ekleme tamamlanana ve koleksiyon boş olana kadar öğeleri kaldırmak için bir [foreach](../../../csharp/language-reference/keywords/foreach-in.md) (Visual Basic'teki Her biri[için)](../../../visual-basic/language-reference/statements/for-each-next-statement.md) de kullanabilirsiniz. Tipik bir `foreach` ()`For Each`döngüden farklı olarak, bu numaralandırma öğeleri kaldırarak kaynak toplamayı değiştirir, çünkü bu *mutasyona* uğrayan numaralandırma veya *tüketen numaralandırma* olarak adlandırılır.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, a <xref:System.Collections.Concurrent.BlockingCollection%601> `foreach` (`For Each`) döngüsü kullanılarak bir 'deki tüm öğelerin nasıl kaldırılılabildiğini gösterilmektedir.

[!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
[!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]

Bu örnek, `foreach` numaralandırılırken her öğenin koleksiyondan kaldırılmasına neden olan tüketen iş parçacığındaki <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> yöntemi içeren bir döngü kullanır. <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>herhangi bir zamanda koleksiyonda bulunan maksimum öğe sayısını sınırlar. Koleksiyonu bu şekilde dizine alma, öğe yoksa veya koleksiyon boşsa tüketici iş parçacığının engellenmesini engeller. Üretici iş parçacığı maddeleri tüketilebileceğinden daha hızlı eklediği için bu örnekte engelleme bir sorun değildir.

Maddelerin üretici iş parçacıkları tarafından eklendikleri sırayla numaralandırıldığının garantisi yoktur.

Koleksiyonu değiştirmeden oyalamak `foreach` `For Each` <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> için, yöntem olmadan ( ) kullanmanız yeterlidir. Ancak, bu tür numaralandırmanın koleksiyonun tam bir zamanda anlık görüntüsünü temsil ettiğini anlamak önemlidir. Döngüyü yürütürken diğer iş parçacıkları öğeleri aynı anda ekliyor veya kaldırıyorsa, döngü koleksiyonun gerçek durumunu temsil etmeyebilir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Paralel Programlama](../../../../docs/standard/parallel-programming/index.md)
