---
title: SpinWait
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
- synchronization primitives, SpinWait
ms.assetid: 36012f42-34e5-4f86-adf4-973f433ed6c6
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 1e67dd59464de09a35941d91ef984db6b7779b8c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="spinwait"></a>SpinWait
<xref:System.Threading.SpinWait?displayProperty=nameWithType>alt düzey senaryolarda çekirdek olaylar için gerekli olan çekirdek geçişleri ve pahalı İçerik Geçişi önlemek için kullanabileceğiniz bir basit eşitleme türüdür. Bir kaynak süresi, uzun bir süre için tutulması için beklenmiyor çok çekirdekli bilgisayarlarda, bir bekleyen iş parçacığı kullanıcı modunda birkaç düzine ya da birkaç yüz döngüsü boyunca Döndür ve kaynak almak için Yeniden Dene'yi daha etkili olabilir. Ardından kaynak dönen sonra kullanılabilir durumdaysa, birkaç bin döngüsü kaydettiniz. Kaynak hala kullanılabilir değil ise, daha sonra yalnızca birkaç döngüleri harcadığınız ve hala çekirdek tabanlı bekleme girebilirsiniz. Bu dönen ardından bekleyen birleşimi, bazen olarak adlandırılır bir *iki aşamalı beklemeyi işlemi*.  
  
 <xref:System.Threading.SpinWait>çekirdek olaylar gibi sarmalamak .NET Framework türleri ile birlikte kullanılmak üzere tasarlanmış <xref:System.Threading.ManualResetEvent>. <xref:System.Threading.SpinWait>Ayrıca tek başına yalnızca bir programda temel dönen işlevselliği için kullanılabilir.  
  
 <xref:System.Threading.SpinWait>daha fazlasını boş bir döngü var. Dikkatle genel durumu için doğru dönen davranışı sağlamak için uygulanır ve yetecek kadar uzun süre dönerek, kendisini İçerik Geçişi başlatır (kabaca bir çekirdek geçiş için gereken süre uzunluğunu). Örneğin, bilgisayarlardaki tek çekirdek, <xref:System.Threading.SpinWait> iş parçacığının zaman dilimi verir hemen tüm iş parçacıklarının ilerlemeyi dönen blokları iletmek için. <xref:System.Threading.SpinWait>daha yüksek öncelikli iş parçacıkları veya atık toplayıcı Engellemesi bekleyen iş parçacığı önlemek için bile çok çekirdekli makinelere de üretir. Bu nedenle, kullanıyorsanız bir <xref:System.Threading.SpinWait> iki aşamalı beklemeyi işleminde, önce çekirdek bekleme çağırma olan öneririz <xref:System.Threading.SpinWait> kendisini bir içerik anahtarı başlatır. <xref:System.Threading.SpinWait>sağlar <xref:System.Threading.SpinWait.NextSpinWillYield%2A> her çağrı için önce kontrol edebilirsiniz özelliği <xref:System.Threading.SpinWait.SpinOnce%2A>. Özellik döndüğünde `true`, kendi bekleme işlemi başlatın. Bir örnek için bkz: [nasıl yapılır: kullanım bekleyin Two-Phase işlemini uygulamak için SpinWait](../../../docs/standard/threading/how-to-use-spinwait-to-implement-a-two-phase-wait-operation.md).  
  
 Aşamalı bir bekleme işlemini gerçekleştirmiyorsanız, ancak bazı koşul true olana kadar yalnızca dönmesini etkinleştirebilirsiniz <xref:System.Threading.SpinWait> onun bağlamı gerçekleştirmek için Windows işletim sistemi ortamında iyi vatandaşı olmasını geçer. Aşağıdaki temel örnekte gösterildiği bir <xref:System.Threading.SpinWait> kilidi serbest yığınında. Yüksek performanslı, iş parçacığı yığın gerekiyorsa kullanmayı <xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType>.  
  
 [!code-csharp[CDS_SpinWait#05](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait.cs#05)]
 [!code-vb[CDS_SpinWait#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/cds_spinwait1.vb#05)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading.Thread.SpinWait%2A>  
 [İş Parçacığı Nesneleri ve Özellikleri](../../../docs/standard/threading/threading-objects-and-features.md)
