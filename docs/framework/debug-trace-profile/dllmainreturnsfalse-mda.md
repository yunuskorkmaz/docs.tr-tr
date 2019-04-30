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
ms.openlocfilehash: fd987cea78d082eee26032d5f98a54dc0cd3e1d5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61754693"
---
# <a name="dllmainreturnsfalse-mda"></a>dllMainReturnsFalse MDA
`dllMainReturnsFalse` Yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilirse, yönetilen `DllMain` DLL_PROCESS_ATTACH, sebeple adlı bir kullanıcı derlemesinin işlev FALSE döndürür.  
  
## <a name="symptoms"></a>Belirtiler  
 `DllMain` İşlevi, düzgün çalıştırılamadı olduğunu belirten FALSE döndürdü. Bunun nedeni belirlenmemiş sorunlarına yol açabilir `DllMain` işlevleri genellikle önemli başlatma kodunu içerir.  
  
## <a name="cause"></a>Sebep  
 `DllMain` DLL başlatma sırasında yük DLL_PROCESS_ATTACH nedeni ile işlevi çağrılır. FALSE döndürürse, bu DLL başlatma başarısız oldu anlamına gelir.  
  
## <a name="resolution"></a>Çözüm  
 Kodu çözümleme `DllMain` başarısız DLL işlevini ve başlatma hatanın nedenini belirleyin.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı üzerindeki etkisi  
 Bu mda'nın CLR üzerinde etkisi yoktur. Dönüş değeri hakkında veri yalnızca raporlar `DllMain`.  
  
## <a name="output"></a>Çıkış  
 Belirten bir ileti bir `DllMain` nedeni DLL_PROCESS_ATTACH, çağrılan işlev, FALSE döndürdü. Yalnızca bu mda'nın etkinleştirilmiş olduğunu Not `DllMain` yönetilen kodda uygulanır.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dllMainReturnsFalse />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
