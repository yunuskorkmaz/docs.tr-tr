---
title: "Nasıl yapılır: Öğeleri Tek Tek Ekleme ve Bir BlockingCollection'dan ve Alma"
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
helpviewer_keywords: thread-safe collections, blocking dictionary
ms.assetid: 38f2f3d8-15e5-4bf4-9c83-2b5b6f22bad1
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b365d6d3236919f65c840343ec3b33edebea758b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-and-take-items-individually-from-a-blockingcollection"></a>Nasıl yapılır: Öğeleri Tek Tek Ekleme ve Bir BlockingCollection'dan ve Alma
Bu örnek öğelerinden ekleyip gösterilmektedir bir <xref:System.Collections.Concurrent.BlockingCollection%601> engelleme ve engelleyici olmayan şekilde iki. Daha fazla bilgi için <xref:System.Collections.Concurrent.BlockingCollection%601>, bkz: [BlockingCollection genel bakışı](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).  
  
 Numaralandırmak nasıl bir örneği için bir <xref:System.Collections.Concurrent.BlockingCollection%601> boş olduğu ve daha fazla öğe eklenecek kadar bkz [nasıl yapılır: kullanım ForEach bir BlockingCollection öğeleri kaldırmak için](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md)  
  
## <a name="example"></a>Örnek  
 Bu ilk örnek nasıl ya da geçici olarak koleksiyonudur işlemlerini engeller böylece eklemek ve almak için öğeleri (alırken) boş veya (eklerken) maksimum kapasite veya belirtilen bir zaman aşımı süresi geçti gösterir. BlockingCollection oluşturucuda belirtilen en yüksek kapasiteli oluşturulduğunda maksimum kapasite engelleme yalnızca etkin olduğunu unutmayın.  
  
 [!code-csharp[CDS_BlockingCollection#01](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example01.cs#01)]
 [!code-vb[CDS_BlockingCollection#01](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/simpleblocking.vb#01)]  
  
## <a name="example"></a>Örnek  
 Bu ikinci örnek ekleme ve işlemleri değil engeller öğeleri alın gösterir. Öğe varsa veya bir sınırlanmış koleksiyonunda maksimum kapasite ulaşıldı veya zaman aşımı süresi geçti, sonra <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> veya <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> işlemi false döndürür. Bu süre için bazı başka yararlı iş yapmak ve sonra yeniden daha sonra yeni bir öğe almak ya da daha önce eklenemedi aynı öğe eklemeyi denediğinizde deneyin iş parçacığı sağlar. Program ayrıca iptal erişirken uygulamak gösterilmiştir bir <xref:System.Collections.Concurrent.BlockingCollection%601>.  
  
 [!code-csharp[CDS_BlockingCollection#02](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example02.cs#02)]
 [!code-vb[CDS_BlockingCollection#02](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/nonblockingbc.vb#02)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 [BlockingCollection genel bakışı](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)
