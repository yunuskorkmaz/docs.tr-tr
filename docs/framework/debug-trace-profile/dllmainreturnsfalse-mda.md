---
title: dllMainReturnsFalse MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed debugging assistants (MDAs), DllMain returns false
- DllMainReturnsFalse MDA
- DllMain function
- MDAs (managed debugging assistants), DllMain returns false
ms.assetid: e2abdd04-f571-4b97-8c16-2221b8588429
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eb5de2b1c41d102fbf9fc47db0ff3d8bd72a3bcd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="dllmainreturnsfalse-mda"></a>dllMainReturnsFalse MDA
`dllMainReturnsFalse` Yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilirse, yönetilen `DllMain` DLL_PROCESS_ATTACH, sebeple adlı bir kullanıcı derlemesi işlevinin FALSE döndürür.  
  
## <a name="symptoms"></a>Belirtiler  
 `DllMain` İşlevi döndürülen FALSE, onu düzgün yürütmediği olduğunu belirtir. Bunun nedeni belirlenmemiş sorunlara neden olabilir `DllMain` işlevleri genellikle önemli başlatma kodunu içerir.  
  
## <a name="cause"></a>Sebep  
 `DllMain` İşlevi DLL başlatma yük üzerine DLL_PROCESS_ATTACH nedeni ile çağrıldı. FALSE değeri döndürülürse, bu DLL başlatma başarısız oldu anlamına gelir.  
  
## <a name="resolution"></a>Çözüm  
 Kodu çözümleme `DllMain` başarısız DLL işlevini ve başlatma hatanın nedenini belirleyin.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı etkisi  
 Bu MDA CLR üzerinde etkisi yoktur. Dönüş değeri hakkında verileri yalnızca raporları `DllMain`.  
  
## <a name="output"></a>Çıkış  
 Belirten bir ileti bir `DllMain` DLL_PROCESS_ATTACH, nedeni adlı işlevi, döndürülen FALSE. Yalnızca bu MDA etkinleştirildiğine dikkat edin `DllMain` yönetilen kodda uygulanır.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dllMainReturnsFalse />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
