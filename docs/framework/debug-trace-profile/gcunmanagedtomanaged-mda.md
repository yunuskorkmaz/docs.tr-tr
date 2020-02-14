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
ms.openlocfilehash: dd4080870ae88da8d4e2055369cd36f3981f2eac
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216449"
---
# <a name="gcunmanagedtomanaged-mda"></a>gcUnmanagedToManaged MDA
`gcUnmanagedToManaged` yönetilen hata ayıklama Yardımcısı (MDA), bir iş parçacığı yönetilmeyenden yönetilen koddan her geçiş yaptığında çöp toplamaya neden olur.  
  
## <a name="symptoms"></a>Belirtiler  
 COM ve platform Invoke kullanılarak yönetilmeyen Kullanıcı bileşenlerini çalıştıran bir uygulama, CLR 'de belirleyici olmayan bir erişim ihlaline neden oluyor.  
  
## <a name="cause"></a>Nedeni  
 Bir uygulama yönetilmeyen Kullanıcı bileşenleri çalıştırıyorsa, bu bileşenler atık toplanan yığını bozmuş olabilir. Bu, çöp toplayıcı nesne grafiğine kılavuzluk etmeye çalıştığında CLR 'de erişim ihlaline neden olur.  
  
## <a name="resolution"></a>Çözüm  
 Bu yardımcıyı etkinleştirmek, yönetilmeyen bileşenin atık toplanan yığını ihlal etmesiyle ilgili süreyi ve bir çöp toplamanın her yönetilen geçişten önce gerçekleşmesini zorlayarak meydana gelir.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bir iş parçacığı yönetilmeyenden yönetilen koddan her geçiş yaptığında çöp toplamaya neden olur.  
  
## <a name="output"></a>Çıktı  
 Bu MDA hiçbir çıkış üretmez.  
  
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
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
- [gcManagedToUnmanaged](gcmanagedtounmanaged-mda.md)
- [Birlikte Çalışma için Hazırlama](../interop/interop-marshaling.md)
