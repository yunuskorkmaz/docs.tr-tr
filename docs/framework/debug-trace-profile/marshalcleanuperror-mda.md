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
ms.openlocfilehash: 2399f72b6efcdf69d8ff4bb3bce541073063c750
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59096595"
---
# <a name="marshalcleanuperror-mda"></a>marshalCleanupError MDA
`marshalCleanupError` Yönetilen hata ayıklama Yardımcısı (MDA), ortak dil çalışma zamanı (CLR) geçici yapılar ve veri türleri yerel ve yönetilen kod sınırları arasında sıralama için kullanılan bellek temizleme girişimi sırasında bir hatayla karşılaştığında etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Yerel ve yönetilen kod geçiş yaparken bir bellek sızıntısı olur, çalışma zamanı durumu gibi iş parçacığı kültürünü geri yüklenmez veya içinde bir hata oluşmamasına <xref:System.Runtime.InteropServices.SafeHandle> temizleme.  
  
## <a name="cause"></a>Sebep  
 Geçici yapıları temizlenirken beklenmeyen bir hata oluştu.  
  
## <a name="resolution"></a>Çözüm  
 Tüm gözden <xref:System.Runtime.InteropServices.SafeHandle> yok Edicisi, Sonlandırıcı ve hatalar için özel bir Sıralayıcı uygulamalar.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı üzerindeki etkisi  
 Bu mda'nın CLR üzerinde etkisi yoktur.  
  
## <a name="output"></a>Çıkış  
 Temizleme sırasında başarısız olan işlem raporlama bir ileti.  
  
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
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma için Hazırlama](../../../docs/framework/interop/interop-marshaling.md)
