---
title: gcUnmanagedToManaged MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), garbage collection
- GC unmanaged to managed
- transitioning threads unmanaged to managed code
- GcUnmanagedToManaged MDA
- threading [.NET Framework], garbage collection
- managed debugging assistants (MDAs), garbage collection
- threading [.NET Framework], managed debugging assistants
- garbage collection, run-time errors
- unmanaged to managed garbage collection
ms.assetid: 103eb3a3-1cf0-4406-8a9a-a7798fdc22d1
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3bc02f12a49ef65614114a056f9263f9ef7f5322
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="gcunmanagedtomanaged-mda"></a>gcUnmanagedToManaged MDA
`gcUnmanagedToManaged` Yönetilen hata ayıklama Yardımcısı (MDA) yönetilmeyen koddan yönetilen koda gelen bir iş parçacığı geçişleri her bir atık toplama neden olur.  
  
## <a name="symptoms"></a>Belirtiler  
 COM ve platform kullanarak çalışan yönetilmeyen kullanıcı bileşenleri çağırma uygulama CLR belirleyici olmayan erişim ihlali neden oluyor.  
  
## <a name="cause"></a>Sebep  
 Ardından uygulamanın yönetilmeyen kullanıcı bileşenleri çalışıyorsa, bu bileşenlerin çöpünün toplanma yığın bozulmuş. Çöp toplayıcı nesnesi grafik yol denediğinde bu CLR bir erişim ihlali neden olur.  
  
## <a name="resolution"></a>Çözüm  
 Bu yardımcı etkinleştirme ne zaman yönetilmeyen bileşen çöpünün toplanma yığın bozarsa ve erişim ihlali her yönetilen geçiş önce gerçekleşmesi için bir atık toplama zorlayarak durumda arasındaki süreyi azaltır.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı etkisi  
 İş parçacığı geçişleri yönetilmeyenden yönetilen kodu her bir atık toplama neden olur.  
  
## <a name="output"></a>Çıkış  
 Bu MDA herhangi bir çıktı oluşturmaz.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcUnmanagedToManaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [gcManagedToUnmanaged](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)  
 [Birlikte Çalışma için Hazırlama](../../../docs/framework/interop/interop-marshaling.md)
