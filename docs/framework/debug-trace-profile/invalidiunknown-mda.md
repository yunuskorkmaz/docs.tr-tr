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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ea7f48ab61c16cb0430717074f1b1feab4827763
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052601"
---
# <a name="invalidiunknown-mda"></a>invalidIUnknown MDA
Yerel koddan yönetilen koda geçersiz `IUnknown` bir işaretçi geçirildiğinde yönetilenhataayıklamaYardımcısı(MDA)etkinleştirilir.`invalidIUnknown` Arabirim için sorgulandığında başarı geri dönemezse.`IUnknown` `IUnknown`  
  
## <a name="symptoms"></a>Belirtiler  
 Bağımsız değişken sıralaması sırasında COM arabirim işaretçisi sıralaması sırasında beklenmeyen bir hata oluştu.  
  
## <a name="cause"></a>Sebep  
 CLR 'ye `QueryInterface` geçirilen com arabiriminde yanlış bir uygulama.  
  
## <a name="resolution"></a>Çözüm  
 `QueryInterface` Uygulamayı düzeltin.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA, CLR üzerinde hiçbir etkisi yoktur.  
  
## <a name="output"></a>Çıkış  
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
