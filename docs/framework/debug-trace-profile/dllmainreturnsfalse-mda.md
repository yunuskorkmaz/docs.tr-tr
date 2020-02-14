---
title: dllMainReturnsFalse MDA
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), DllMain returns false
- DllMainReturnsFalse MDA
- DllMain function
- MDAs (managed debugging assistants), DllMain returns false
ms.assetid: e2abdd04-f571-4b97-8c16-2221b8588429
ms.openlocfilehash: 0b413521e0a2dc06c2ff0be642f080eaf541202f
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216441"
---
# <a name="dllmainreturnsfalse-mda"></a>dllMainReturnsFalse MDA
`dllMainReturnsFalse` yönetilen hata ayıklama Yardımcısı (MDA), bir Kullanıcı derlemesinin yönetilen `DllMain` işlevi, neden DLL_PROCESS_ATTACH çağrıldığında etkinleştirilir, FALSE döndürür.  
  
## <a name="symptoms"></a>Belirtiler  
 `DllMain` işlevi, doğru şekilde yürütülmediğini belirten yanlış döndürdü. `DllMain` işlevler tipik olarak önemli başlatma kodu içerdiği için bu, belirlenmemiş sorunlara neden olabilir.  
  
## <a name="cause"></a>Nedeni  
 `DllMain` işlevi, yükleme sonrasında DLL başlatma için DLL_PROCESS_ATTACH neden ile çağırılır. YANLıŞ döndürürse, DLL başlatması başarısız oldu demektir.  
  
## <a name="resolution"></a>Çözüm  
 Başarısız DLL 'nin `DllMain` işlevinin kodunu çözümleyin ve başlatma hatasının nedenini belirler.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA, CLR üzerinde hiçbir etkisi yoktur. Yalnızca `DllMain`için dönüş değeri hakkındaki verileri raporlar.  
  
## <a name="output"></a>Çıktı  
 DLL_PROCESS_ATTACH nedeni için çağrılan `DllMain` işlevinin yanlış döndürüldüğünü belirten bir ileti. Bu MDA 'ın yalnızca `DllMain` yönetilen kodda uygulanmışsa etkinleştirildiğini unutmayın.  
  
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
