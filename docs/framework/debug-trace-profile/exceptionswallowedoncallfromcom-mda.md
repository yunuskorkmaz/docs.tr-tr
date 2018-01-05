---
title: exceptionSwallowedOnCallFromCom MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, informational
- informational messages
- managed debugging assistants (MDAs), exceptions
- exception handling, managed debugging assistants
- MDAs (managed debugging assistants), exceptions
- ExceptionSwallowedOnCallFromCOM MDA
ms.assetid: 55d6ab12-f251-4aab-aa64-aacbe9d9f974
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c20c4e0b6c1c711b2044bc3ba32d00447220cb8b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="exceptionswallowedoncallfromcom-mda"></a>exceptionSwallowedOnCallFromCom MDA
`exceptionSwallowedOnCallFromCOM` Yönetilen hata ayıklama Yardımcısı (MDA) kodundan COM dönüş türü bir yönetilmeyen HRESULT sahip olmayan bir yöntem adlı ortak dil çalışma zamanı (CLR) bir özel durum oluştuğunda etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Yönetilen bir bileşen için bir arama COM bağlantısını FALSE veya 0 değerine sahip döndürür. Alternatif olarak, yöntemin dönüş türü void varsa, olabilir yönteminin yürütülmesi sırasında özel durum oluştu hiçbir belirti. Bu durumda, özel durum sessizce yakalanan ve yürütme COM çağırana döndürür.  
  
## <a name="cause"></a>Sebep  
 Özel durum oluştu, ancak bunu bildirmek için geçerli bir yolu yoktur.  
  
## <a name="resolution"></a>Çözüm  
 Yalnızca, hatanın mutlaka hatırlanması bilgilendirici.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı etkisi  
 Bu MDA CLR üzerinde etkisi yoktur. Yalnızca veri sessizce Yakalanan özel durumlar hakkında raporlar.  
  
## <a name="output"></a>Çıkış  
 Yöntem adı, türü adı ve özel durum iletisi içeren bilgi iletisi.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <exceptionSwallowedOnCallFromCom />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Birlikte Çalışma için Hazırlama](../../../docs/framework/interop/interop-marshaling.md)
