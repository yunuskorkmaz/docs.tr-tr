---
title: exceptionSwallowedOnCallFromCom MDA
ms.date: 03/30/2017
helpviewer_keywords:
- messages, informational
- informational messages
- managed debugging assistants (MDAs), exceptions
- exception handling, managed debugging assistants
- MDAs (managed debugging assistants), exceptions
- ExceptionSwallowedOnCallFromCOM MDA
ms.assetid: 55d6ab12-f251-4aab-aa64-aacbe9d9f974
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4f076cbc556c7d9feff8a226f050743cd7728622
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61874451"
---
# <a name="exceptionswallowedoncallfromcom-mda"></a>exceptionSwallowedOnCallFromCom MDA
`exceptionSwallowedOnCallFromCOM` Yönetilen hata ayıklama Yardımcısı (MDA), bir özel durum COM'dan yönetilmeyen HRESULT dönüş türü olmayan bir yöntem adlı ortak dil çalışma zamanı (CLR) kodu oluşturulduğunda etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Bir çağrıdan yönetilen bir bileşeni için COM ile FALSE veya 0 değerini döndürür. Alternatif olarak, yöntemin dönüş türü void varsa olabilir herhangi bir gösterge metodu yürütülürken bir özel durum oluştu. Bu durumda, özel durumu sessizce yakalanır ve yürütme COM çağırana döner.  
  
## <a name="cause"></a>Sebep  
 Bir özel durum oluştu, ancak bunu bildirmek için geçerli bir yolu yoktur.  
  
## <a name="resolution"></a>Çözüm  
 Bilgilendirici yalnızca, bir hatanın mutlaka gösterir.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı üzerindeki etkisi  
 Bu mda'nın CLR üzerinde etkisi yoktur. Yalnızca veri sessizce Yakalanan özel durumlar hakkında raporlar.  
  
## <a name="output"></a>Çıkış  
 Yöntem adı, tür adı ve özel durum iletisi içeren bilgilendirme iletisi.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <exceptionSwallowedOnCallFromCom />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma için Hazırlama](../../../docs/framework/interop/interop-marshaling.md)
