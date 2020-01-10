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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711265"
---
# <a name="how-to-use-arrays-of-blocking-collections-in-a-pipeline"></a>Nasıl yapılır: Ardışık Düzende Engelleme Koleksiyonu Dizilerini Kullanma
Aşağıdaki örnek, bileşenler arasında hızlı ve esnek veri aktarımını uygulamak için <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> ve <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> gibi statik yöntemlerle <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> nesneleri dizilerinin nasıl kullanılacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, her bir nesnenin giriş koleksiyonundan eşzamanlı olarak veri aldığı, dönüştüren ve çıkış koleksiyonuna geçirdikleri temel bir ardışık düzen uygulamasını gösterir.  
  
 [!code-csharp[CDS_BlockingCollection#07](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example07.cs#07)]
 [!code-vb[CDS_BlockingCollection#07](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/bcpipeline.vb#07)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [İş Parçacığı Güvenli Koleksiyonları](../../../../docs/standard/collections/thread-safe/index.md)
