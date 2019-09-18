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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ab3690cac28ef572b19cadb632662590d1ea04c7
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052475"
---
# <a name="marshalcleanuperror-mda"></a>marshalCleanupError MDA
Ortak `marshalCleanupError` dil çalışma zamanı (CLR), yerel ve yönetilen kod sınırları arasında veri türlerini sıralama için kullanılan geçici yapıları ve belleği temizlemeye çalışırken bir hatayla karşılaştığında, yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Yerel ve yönetilen kod geçişleri yaparken bellek sızıntısı oluşur, iş parçacığı kültürü gibi çalışma zamanı durumu geri yüklenmez veya temizleme sırasında <xref:System.Runtime.InteropServices.SafeHandle> hatalar oluşur.  
  
## <a name="cause"></a>Sebep  
 Geçici yapılar temizlenirken beklenmeyen bir hata oluştu.  
  
## <a name="resolution"></a>Çözüm  
 Hatalar için <xref:System.Runtime.InteropServices.SafeHandle> tüm yıkıcıyı, sonlandırıcıyı ve özel sıralayıcı uygulamalarını inceleyin.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA, CLR üzerinde hiçbir etkisi yoktur.  
  
## <a name="output"></a>Çıkış  
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
