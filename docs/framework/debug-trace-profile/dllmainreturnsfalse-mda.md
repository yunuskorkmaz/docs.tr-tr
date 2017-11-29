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
ms.openlocfilehash: 91d2dfefc8de49770ec5c0b0083767bbb4b76c0b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
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
 [Yönetilen hata ayıklama Yardımcıları ile hataları tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
