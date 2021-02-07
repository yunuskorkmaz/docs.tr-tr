---
description: 'Daha fazla bilgi edinin: nasıl yapılır: koleksiyona sınırlama ve engelleme Işlevi ekleme'
title: 'Nasıl yapılır: Koleksiyona Sınırlama ve Engelleme İşlevi Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- thread-safe collections, custom blocking collections
ms.assetid: 4c2492de-3876-4873-b5a1-000bb404d770
ms.openlocfilehash: c44febe0a7b2155c61b12c280d830ad7b028d326
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99676072"
---
# <a name="how-to-add-bounding-and-blocking-functionality-to-a-collection"></a>Nasıl yapılır: Koleksiyona Sınırlama ve Engelleme İşlevi Ekleme

Bu örnek <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType> , sınıfında arabirimini uygulayarak ve sonra bir sınıf örneğini bir için iç depolama mekanizması olarak kullanarak özel bir koleksiyon sınıfına nasıl sınırlama ve engelleme işlevselliği ekleneceğini gösterir <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> . Sınırlama ve engelleme hakkında daha fazla bilgi için bkz. [BlockingCollection genel bakış](blockingcollection-overview.md).  
  
## <a name="example"></a>Örnek  

 Özel koleksiyon sınıfı, öncelik düzeylerinin bir nesne dizisi olarak temsil edildiği temel bir öncelik kuyruğudur <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> . Her sıra içinde ek sıralama yapılmaz.  
  
 İstemci kodunda, üç görev başlatılır. İlk görev, yürütme sırasında herhangi bir noktada iptali etkinleştirmek üzere klavye vuruşları için yalnızca yoklar. İkinci görev üretici iş parçacığıdır; engelleme koleksiyonuna yeni öğeler ekler ve her öğeye rastgele bir değer temelinde öncelik verir. Üçüncü görev, öğeleri kullanılabilir hale geldiğinde koleksiyondan kaldırır.  
  
 İş parçacıklarından birini diğerinin daha hızlı çalıştırmasını sağlayarak uygulamanın davranışını ayarlayabilirsiniz. Üretici daha hızlı çalışırsa, blok koleksiyon, Oluşturucu üzerinde belirtilen öğelerin sayısını zaten içeriyorsa öğelerin eklenmesini engellediğini fark eder. Tüketici daha hızlı çalışırsa, tüketici yeni bir öğenin eklenmesini beklediği için engelleme işlevini fark edeceksiniz.  
  
 [!code-csharp[CDS_BlockingCollection#06](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/prodcon.cs#06)]  
  
 Varsayılan olarak, bir için depolama alanı <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş parçacığı güvenli Koleksiyonlar](index.md)
