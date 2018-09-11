---
title: SpinWait
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- synchronization primitives, SpinWait
ms.assetid: 36012f42-34e5-4f86-adf4-973f433ed6c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1ff8b5b75d1d69d3d8c88810de1311540a239c52
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44273417"
---
# <a name="spinwait"></a>SpinWait
<xref:System.Threading.SpinWait?displayProperty=nameWithType> alt düzey senaryolarda çekirdek olayları için gerekli olan çekirdek geçişleri ve pahalı bağlam anahtarları önlemek için kullanabileceğiniz bir hafif eşitleme türüdür. Bir kaynak saat, uzun süre boyunca bekletilmesini beklenmiyor çok çekirdekli bilgisayarlarda bir bekleyen iş parçacığı birkaç düzine veya birkaç yüz döngüler için kullanıcı modunda çalıştırın ve kaynak almak için yeniden denemek daha verimli olabilir. Ardından kaynak dönen sonra kullanılabilir haldeyse, birkaç bin döngü kaydettiniz. Kaynak hala kullanılabilir değil ise, yalnızca birkaç döngüleri harcadığınız sonra çekirdek tabanlı bekleme yine de girebilirsiniz. Bu dönen ardından bekleyen birlikte, bazen olarak adlandırılır bir *iki aşamalı bir bekleme işlemini*.  
  
 <xref:System.Threading.SpinWait> çekirdek olayları gibi kaydırma .NET Framework türleri ile birlikte kullanılmak üzere tasarlanmış <xref:System.Threading.ManualResetEvent>. <xref:System.Threading.SpinWait> Ayrıca tek başına yalnızca bir programda temel dönen işlevselliği için kullanılabilir.  
  
 <xref:System.Threading.SpinWait> yalnızca boş bir döngü var. Genel durum dönen doğru davranışı sağlamak için dikkatli bir şekilde gerçekleştirilir ve yeterince dönüyorsa kendisini bağlam anahtarları başlatır (kabaca bir çekirdek geçişi için gereken süre uzunluğunu). Örneğin, ilgili tek çekirdekli bilgisayarlarda <xref:System.Threading.SpinWait> iş parçacığının zaman dilimi verir hemen tüm iş parçacıkları üzerinde devam eden dönen blokları iletmek için. <xref:System.Threading.SpinWait> Bekleyen iş parçacığı daha yüksek öncelikli iş parçacıkları veya çöp toplayıcı engellemesini önleyecek bile çok çekirdekli makinelere de verir. Bu nedenle, kullanıyorsanız bir <xref:System.Threading.SpinWait> iki aşamalı beklemeyi işleminde, önce çekirdek bekleme çağırma olan öneririz <xref:System.Threading.SpinWait> kendisi bir içerik anahtarı başlatır. <xref:System.Threading.SpinWait> sağlar <xref:System.Threading.SpinWait.NextSpinWillYield%2A> yapılan her çağrı önce denetleyebilirsiniz özelliği <xref:System.Threading.SpinWait.SpinOnce%2A>. Özellik döndürdüğünde `true`, kendi bekleme işlemi başlatın. Bir örnek için bkz. [nasıl yapılır: kullanım bir Two-Phase bekleme işlemini uygulamak için SpinWait](../../../docs/standard/threading/how-to-use-spinwait-to-implement-a-two-phase-wait-operation.md).  
  
 Aşamalı bir bekleme işlemini gerçekleştirmiyorsanız, ancak bazı koşul true olana kadar yalnızca dönen etkinleştirebilirsiniz <xref:System.Threading.SpinWait> bağlama gerçekleştirmek için iyi vatandaşı Windows işletim sistemi ortamında olmasını geçer. Aşağıdaki basit örnekte gösterildiği bir <xref:System.Threading.SpinWait> kilitsizdir yığında. Yüksek performanslı, iş parçacığı yığını gerekiyorsa kullanmayı <xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType>.  
  
 [!code-csharp[CDS_SpinWait#05](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait.cs#05)]
 [!code-vb[CDS_SpinWait#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/cds_spinwait1.vb#05)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Thread.SpinWait%2A>  
- [İş Parçacığı Nesneleri ve Özellikleri](../../../docs/standard/threading/threading-objects-and-features.md)
