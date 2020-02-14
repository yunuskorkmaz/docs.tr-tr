---
title: invalidIUnknown MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid IUnknown pointer
- InvalidIUnknown MDA
- invalid IUnknown pointers
- IUnknown pointers
- managed debugging assistants (MDAs), invalid IUnknown pointer
ms.assetid: c7924771-a16b-40fe-b337-ce51dcdf6a12
ms.openlocfilehash: 5df9a3f506d8c2de6f1a3125459adc2d59d510bf
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217361"
---
# <a name="invalidiunknown-mda"></a>invalidIUnknown MDA
`invalidIUnknown` yönetilen hata ayıklama Yardımcısı (MDA), yerel koddan yönetilen koda geçersiz bir `IUnknown` işaretçisi geçirildiğinde etkinleştirilir. `IUnknown`, `IUnknown` arabirimi için sorgulandığında başarıyı geri döndüremiyor.  
  
## <a name="symptoms"></a>Belirtiler  
 Bağımsız değişken sıralaması sırasında COM arabirim işaretçisi sıralaması sırasında beklenmeyen bir hata oluştu.  
  
## <a name="cause"></a>Nedeni  
 CLR 'ye geçirilen COM arabiriminde yanlış bir `QueryInterface` uygulama.  
  
## <a name="resolution"></a>Çözüm  
 `QueryInterface` uygulamasını düzeltin.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA, CLR üzerinde hiçbir etkisi yoktur.  
  
## <a name="output"></a>Çıktı  
 Hatanın açıklaması.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidIUnknown />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma için Hazırlama](../interop/interop-marshaling.md)
