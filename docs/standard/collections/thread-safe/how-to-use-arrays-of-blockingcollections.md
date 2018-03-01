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
# <a name="how-to-use-arrays-of-blocking-collections-in-a-pipeline"></a><span data-ttu-id="4651e-102">Nasıl yapılır: Ardışık Düzende Engelleme Koleksiyonu Dizilerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="4651e-102">How to: Use Arrays of Blocking Collections in a Pipeline</span></span>
<span data-ttu-id="4651e-103">Aşağıdaki örnek dizileri kullanmayı gösterir <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> statik yöntemleriyle gibi nesneleri <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> ve <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> bileşenleri arasında hızlı ve esnek veri aktarımını uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="4651e-103">The following example shows how to use arrays of <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> objects with static methods such as <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> and <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> to implement fast and flexible data transfer between components.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4651e-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="4651e-104">Example</span></span>  
 <span data-ttu-id="4651e-105">Aşağıdaki örnekte, her nesne, dönüştürme ve çıktı koleksiyona geçirme giriş koleksiyonu, verileri aynı anda sürüyor temel ardışık düzen uygulaması gösterir.</span><span class="sxs-lookup"><span data-stu-id="4651e-105">The following example demonstrates a basic pipeline implementation in which each object is concurrently taking data from the input collection, transforming it, and passing it to the output collection.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#07](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example07.cs#07)]
 [!code-vb[CDS_BlockingCollection#07](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/bcpipeline.vb#07)]  
  
## <a name="see-also"></a><span data-ttu-id="4651e-106">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4651e-106">See Also</span></span>  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 [<span data-ttu-id="4651e-107">İş Parçacığı Güvenli Koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="4651e-107">Thread-Safe Collections</span></span>](../../../../docs/standard/collections/thread-safe/index.md)
