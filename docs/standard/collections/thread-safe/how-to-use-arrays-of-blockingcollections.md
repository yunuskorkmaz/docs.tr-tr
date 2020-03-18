---
title: 'Nasıl yapılır: Ardışık Düzende Engelleme Koleksiyonu Dizilerini Kullanma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, blocking collections in pipeline
ms.assetid: a39c7ec3-3ad7-4f4d-8fe4-b3e9dbabe2ed
ms.openlocfilehash: 397c438bacd1cfed1613efef61e9d7266d55ea47
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711265"
---
# <a name="how-to-use-arrays-of-blocking-collections-in-a-pipeline"></a>Nasıl yapılır: Ardışık Düzende Engelleme Koleksiyonu Dizilerini Kullanma
Aşağıdaki örnek, statik yöntemlerle <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> nesne dizilerinin nasıl <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> kullanılacağını ve <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> bileşenler arasında hızlı ve esnek veri aktarımını nasıl uygulayacağımı gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, her nesnenin giriş koleksiyonundan verileri aynı anda aldığı, dönüştürdettiği ve çıktı koleksiyonuna aktardığı temel bir ardışık uygulama gösterir.  
  
 [!code-csharp[CDS_BlockingCollection#07](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example07.cs#07)]
 [!code-vb[CDS_BlockingCollection#07](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/bcpipeline.vb#07)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [İş Parçacığı Koleksiyonları](../../../../docs/standard/collections/thread-safe/index.md)
