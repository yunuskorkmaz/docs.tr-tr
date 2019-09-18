---
title: dllMainReturnsFalse MDA
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), DllMain returns false
- DllMainReturnsFalse MDA
- DllMain function
- MDAs (managed debugging assistants), DllMain returns false
ms.assetid: e2abdd04-f571-4b97-8c16-2221b8588429
author: mairaw
ms.author: mairaw
ms.openlocfilehash: adc05ae9bd357c142ff09de069aff446b5ea60e8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052853"
---
# <a name="dllmainreturnsfalse-mda"></a>dllMainReturnsFalse MDA
Yönetilen hata ayıklama Yardımcısı (MDA), DLL_PROCESS_ATTACH nedeni ile çağrılan `DllMain` bir Kullanıcı derlemesinin yönetilen işlevi false değerini döndürürse etkinleştirilir. `dllMainReturnsFalse`  
  
## <a name="symptoms"></a>Belirtiler  
 `DllMain` İşlev, doğru şekilde yürütülmediğini belirten yanlış olarak döndürüldü. Bu, `DllMain` işlev genellikle önemli başlatma kodu içerdiği için belirlenmeyen sorunlara neden olabilir.  
  
## <a name="cause"></a>Sebep  
 İşlev `DllMain` , yükleme sonrasında DLL_PROCESS_ATTACH for dll başlatması nedeniyle çağrılır. YANLıŞ döndürürse, DLL başlatması başarısız oldu demektir.  
  
## <a name="resolution"></a>Çözüm  
 Başarısız olan dll `DllMain` işlevinin kodunu çözümleyin ve başlatma hatasının nedenini belirler.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA, CLR üzerinde hiçbir etkisi yoktur. Yalnızca dönüş değeri `DllMain`ile ilgili verileri raporlar.  
  
## <a name="output"></a>Çıkış  
 DLL_PROCESS_ATTACH nedeni için çağrılan bir `DllMain` işlevin yanlış döndürüldüğünü belirten bir ileti. Bu mda 'ın yalnızca `DllMain` yönetilen kodda uygulanmışsa etkinleştirildiğini unutmayın.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dllMainReturnsFalse />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
