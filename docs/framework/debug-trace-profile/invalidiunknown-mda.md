---
title: invalidIUnknown MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid IUnknown pointer
- InvalidIUnknown MDA
- invalid IUnknown pointers
- IUnknown pointers
- managed debugging assistants (MDAs), invalid IUnknown pointer
ms.assetid: c7924771-a16b-40fe-b337-ce51dcdf6a12
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ff88f8bc544c95a4fe5149cd517d9157d5ac23c7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="invalidiunknown-mda"></a>invalidIUnknown MDA
`invalidIUnknown` Yönetilen hata ayıklama Yardımcısı (MDA) geçersiz bir zaman etkinleştirilirse `IUnknown` işaretçi yerel koddan yönetilen koda geçirilir. `IUnknown` İçin sorgulandığında başarı döndürülecek başarısız `IUnknown` arabirimi.  
  
## <a name="symptoms"></a>Belirtiler  
 Bağımsız değişken sıralama sırasında bir COM arabirimi işaretçisi hazırlama beklenmeyen bir hata oluşur.  
  
## <a name="cause"></a>Sebep  
 Yanlış bir `QueryInterface` COM arabirimi üzerindeki uygulama için CLR geçirildi.  
  
## <a name="resolution"></a>Çözüm  
 Düzeltmek `QueryInterface` uygulaması.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı etkisi  
 Bu MDA CLR üzerinde etkisi yoktur.  
  
## <a name="output"></a>Çıkış  
 Hatanın açıklaması.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidIUnknown />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Birlikte Çalışma için Hazırlama](../../../docs/framework/interop/interop-marshaling.md)
