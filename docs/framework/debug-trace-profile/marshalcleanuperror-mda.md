---
title: marshalCleanupError MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cleanup operations
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
- marshaling cleanup error
- MarshalCleanupError MDA
- memory, cleanup errors
ms.assetid: 2f5d9e7c-ae51-4155-a435-54347aa1f091
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 641d12131f1502ce1ef00c6cf3889c803bd9fce3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="marshalcleanuperror-mda"></a>marshalCleanupError MDA
`marshalCleanupError` Yönetilen hata ayıklama Yardımcısı (MDA), ortak dil çalışma zamanı (CLR) geçici yapılar ve yerel ve yönetilen kod sınırlar arasında veri türlerini sıralama için kullanılan bellek temizleme girişimi sırasında bir hatayla karşılaştığında etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Bellek sızıntısı oluşuyor yerel ve yönetilen kod geçiş yaparken, çalışma zamanı durum iş parçacığı kültürünü geri yüklenmemiş veya hataları gerçekleştirilir gibi <xref:System.Runtime.InteropServices.SafeHandle> temizleme.  
  
## <a name="cause"></a>Sebep  
 Geçici yapılarını temizleme sırasında beklenmeyen bir hata oluştu.  
  
## <a name="resolution"></a>Çözüm  
 Tüm gözden <xref:System.Runtime.InteropServices.SafeHandle> yıkıcı, Sonlandırıcı ve hataları için özel sıralayıcı uygulamaları.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı etkisi  
 Bu MDA CLR üzerinde etkisi yoktur.  
  
## <a name="output"></a>Çıkış  
 Temizleme sırasında başarısız olan işlem raporlama iletisi.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshalCleanupError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Birlikte Çalışma için Hazırlama](../../../docs/framework/interop/interop-marshaling.md)
