---
title: invalidIUnknown MDA
description: Yerel koddan yönetilen koda geçersiz bir IUnknown işaretçisi geçirildiğinde etkinleştirilen invalidIUnknown Managed hata ayıklama Yardımcısı 'nı (MDA) gözden geçirin.
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid IUnknown pointer
- InvalidIUnknown MDA
- invalid IUnknown pointers
- IUnknown pointers
- managed debugging assistants (MDAs), invalid IUnknown pointer
ms.assetid: c7924771-a16b-40fe-b337-ce51dcdf6a12
ms.openlocfilehash: 65d704463ed746390ff1710b590bf080013bf53d
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: tr-TR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051733"
---
# <a name="invalidiunknown-mda"></a>invalidIUnknown MDA
`invalidIUnknown`Yerel koddan yönetilen koda geçersiz bir işaretçi geçirildiğinde yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilir `IUnknown` . `IUnknown`Arabirim için sorgulandığında başarı geri dönemezse `IUnknown` .  
  
## <a name="symptoms"></a>Belirtiler  
 Bağımsız değişken sıralaması sırasında COM arabirim işaretçisi sıralaması sırasında beklenmeyen bir hata oluştu.  
  
## <a name="cause"></a>Nedeni  
 `QueryInterface`Clr 'ye GEÇIRILEN com arabiriminde yanlış bir uygulama.  
  
## <a name="resolution"></a>Çözüm  
 Uygulamayı düzeltin `QueryInterface` .  
  
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
- [Birlikte Çalışma Hazırlama](../interop/interop-marshaling.md)
