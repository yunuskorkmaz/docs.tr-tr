---
title: "MDA Hazırlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- marshaling, run-time errors
- marshaling MDA
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: 5433b1f8-b0e5-40c9-a49a-0e5bd213363d
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 83b621f78e3ba4641540f6125ed14d600cc292d1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="marshaling-mda"></a>MDA Hazırlama
`marshaling` Yönetilen hata ayıklama Yardımcısı (MDA) CLR yöntem parametresi ya da bir yapı bir alan için bilgi sıralama yukarı ayarladığında etkinleştirilir. Bu MDA JIT derlenmiş derlemeler için çalışmaz.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı etkisi  
 Bu MDA CLR üzerinde etkisi yoktur.  
  
## <a name="output"></a>Çıkış  
 MDA yönetilen ve yönetilmeyen bağlamları ve yapısı veya türünü içeren yöntemi parametresi veya alan türünü görüntüler.  Bir alan için çıktının bir örnek verilmiştir:  
  
```  
Marshaling from 'Char' to 'ANSI char'  
name="assembly!Namespace.Class::myChar  
```  
  
## <a name="configuration"></a>Yapılandırma  
 MDA yapılandırma söz konusu alan veya yöntem adlarını temel alarak bildirilen sıralama bilgileri filtre etmenize olanak sağlar.  Aşağıdaki örnek kullanımı gösterilmiştir `methodFilter`, `fieldFilter`, ve `match` öğeleri filtreleri belirtin.  Ayarı `name` özniteliği için bir yıldız işareti (*) her şeyi eşleşir.  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshaling>  
      <methodFilter>  
        <match name="Method1"/>  
        <match name="Method2"/>  
      </methodFilter>  
      <fieldFilter>  
        <match name="Field1"/>  
        <match name="Field2"/>  
       </fieldFilter>  
    </marshaling>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Birlikte Çalışma için Hazırlama](../../../docs/framework/interop/interop-marshaling.md)
