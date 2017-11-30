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
ms.openlocfilehash: d68e3f8659b0d5fe212c58443fe9a8b42f9cef89
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Yönetilen hata ayıklama Yardımcıları ile hataları tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Birlikte çalışma hazırlama](../../../docs/framework/interop/interop-marshaling.md)
