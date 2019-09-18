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
ms.openlocfilehash: 3a49bdce78c1445cd25de8755ded0f27a4902937
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052811"
---
# <a name="exceptionswallowedoncallfromcom-mda"></a>exceptionSwallowedOnCallFromCom MDA
Yönetilen `exceptionSwallowedOnCallFromCOM` hata ayıklama Yardımcısı (MDA), yönetilmeyen bir HRESULT dönüş türüne sahip olmayan bir yöntem aracılığıyla com 'dan çağrılan ortak dil çalışma zamanı (CLR) kodundan bir özel durum oluştuğunda etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  
 COM 'tan yönetilen bileşen çağrısı, FALSE veya 0 değeri ile döndürür. Alternatif olarak, yöntemin bir void dönüş türü varsa, yöntemin yürütülmesi sırasında bir özel durumun oluşturulduğunu belirten bir işaret olmayabilir. Bu durumda, özel durum sessizce yakalanacaktır ve yürütme COM çağıranına döndürülür.  
  
## <a name="cause"></a>Sebep  
 Bir özel durum oluşturuldu, ancak bunu raporlamak için geçerli bir yol yok.  
  
## <a name="resolution"></a>Çözüm  
 Yalnızca bilgilendirme, bir hatanın göstergesi olması gerekmez.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA, CLR üzerinde hiçbir etkisi yoktur. Yalnızca sessizce yakalanan özel durumlarla ilgili verileri raporlar.  
  
## <a name="output"></a>Çıkış  
 Yöntem adı, tür adı ve özel durum iletisi içeren bilgilendirici ileti.  
  
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
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma için Hazırlama](../interop/interop-marshaling.md)
