---
title: "Nasıl yapılır: Ardışık Düzende Engelleme Koleksiyonu Dizilerini Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, blocking collections in pipeline
ms.assetid: a39c7ec3-3ad7-4f4d-8fe4-b3e9dbabe2ed
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 753c58686e943f5753c76a8d695f4401c4a69952
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-use-arrays-of-blocking-collections-in-a-pipeline"></a>Nasıl yapılır: Ardışık Düzende Engelleme Koleksiyonu Dizilerini Kullanma
Aşağıdaki örnek dizileri kullanmayı gösterir <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> statik yöntemleriyle gibi nesneleri <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> ve <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> bileşenleri arasında hızlı ve esnek veri aktarımını uygulamak için.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, her nesne, dönüştürme ve çıktı koleksiyona geçirme giriş koleksiyonu, verileri aynı anda sürüyor temel ardışık düzen uygulaması gösterir.  
  
 [!code-csharp[CDS_BlockingCollection#07](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example07.cs#07)]
 [!code-vb[CDS_BlockingCollection#07](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/bcpipeline.vb#07)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 [İş Parçacığı Güvenli Koleksiyonları](../../../../docs/standard/collections/thread-safe/index.md)
