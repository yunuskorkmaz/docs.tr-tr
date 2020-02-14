---
title: marshalCleanupError MDA
ms.date: 03/30/2017
helpviewer_keywords:
- cleanup operations
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
- marshaling cleanup error
- MarshalCleanupError MDA
- memory, cleanup errors
ms.assetid: 2f5d9e7c-ae51-4155-a435-54347aa1f091
ms.openlocfilehash: 1a14c548ce960d53f47934595171189db28edfbb
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216150"
---
# <a name="marshalcleanuperror-mda"></a>marshalCleanupError MDA
`marshalCleanupError` yönetilen hata ayıklama Yardımcısı (MDA), ortak dil çalışma zamanı (CLR), yerel ve yönetilen kod sınırları arasında veri türlerini hazırlama için kullanılan geçici yapıları ve belleği temizlemeye çalışırken bir hatayla karşılaştığında etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Yerel ve yönetilen kod geçişleri yaparken bir bellek sızıntısı oluşur, iş parçacığı kültürü gibi çalışma zamanı durumu geri yüklenmez veya <xref:System.Runtime.InteropServices.SafeHandle> Temizleme sırasında hatalar oluşur.  
  
## <a name="cause"></a>Nedeni  
 Geçici yapılar temizlenirken beklenmeyen bir hata oluştu.  
  
## <a name="resolution"></a>Çözüm  
 Hata için tüm <xref:System.Runtime.InteropServices.SafeHandle> yıkıcıyı, sonlandırıcıyı ve özel sıralayıcı uygulamalarını gözden geçirin.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA, CLR üzerinde hiçbir etkisi yoktur.  
  
## <a name="output"></a>Çıktı  
 Temizleme sırasında başarısız olan işlemi bildiren bir ileti.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshalCleanupError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma için Hazırlama](../interop/interop-marshaling.md)
