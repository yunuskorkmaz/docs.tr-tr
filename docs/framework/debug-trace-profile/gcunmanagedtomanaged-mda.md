---
title: gcUnmanagedToManaged MDA
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 66f662114868832f909d734a482e1dc9aefb841a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61754485"
---
# <a name="gcunmanagedtomanaged-mda"></a>gcUnmanagedToManaged MDA
`gcUnmanagedToManaged` Yönetilen hata ayıklama Yardımcısı (MDA) yönetilen kodu için yönetilmeyen bir iş parçacığı gelen geçiş her bir çöp toplamanın neden olur.  
  
## <a name="symptoms"></a>Belirtiler  
 COM ve platformu kullanarak çalışan yönetilmeyen kullanıcı bileşenleri çağırma uygulama CLR'de belirleyici olmayan erişim ihlaline neden oluyor.  
  
## <a name="cause"></a>Sebep  
 Ardından uygulamanın yönetilmeyen kullanıcı bileşenleri çalışıyorsa, bu bileşenlerin atık olarak toplanmış yığınla bozulmuş. Atık toplayıcı Nesne grafiğini yol denediğinde bu CLR'de erişim ihlaline neden olur.  
  
## <a name="resolution"></a>Çözüm  
 Bu Yardımcısı'nı etkinleştirme, yönetilmeyen bileşeni atık olarak toplanmış yığınla bozarsa ve bir çöp toplama, yönetilen her geçiş önce gerçekleşmesi için zorlayarak erişim ihlali durumda arasındaki süreyi azaltır.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı üzerindeki etkisi  
 Yönetilen kod için yönetilmeyen bir iş parçacığı geçişler her bir çöp toplamanın neden olur.  
  
## <a name="output"></a>Çıkış  
 Bu mda'nın herhangi bir çıktı üretmez.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcUnmanagedToManaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [gcManagedToUnmanaged](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)
- [Birlikte Çalışma için Hazırlama](../../../docs/framework/interop/interop-marshaling.md)
