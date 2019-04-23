---
title: MDA Sıralama
ms.date: 03/30/2017
helpviewer_keywords:
- marshaling, run-time errors
- marshaling MDA
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: 5433b1f8-b0e5-40c9-a49a-0e5bd213363d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 463c8e42e76a61eb0820c1af72c20d004161ad25
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59184476"
---
# <a name="marshaling-mda"></a>MDA Sıralama
`marshaling` Yönetilen hata ayıklama Yardımcısı (MDA), bir yöntem parametresi veya bir yapının bir alan için bilgi sıralama yukarı CLR kümeleri kullanırken etkinleştirilir. Bu MDA, JIT olarak derlenmiş derlemelerde çalışmaz.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı üzerindeki etkisi  
 Bu mda'nın CLR üzerinde etkisi yoktur.  
  
## <a name="output"></a>Çıkış  
 MDA, yönetilen ve yönetilmeyen bağlamları ve yapısı veya türünü içeren bir yöntem parametresi veya alan türünü görüntüler.  Bir alan için çıktının bir örneği verilmiştir:  
  
```  
Marshaling from 'Char' to 'ANSI char'  
name="assembly!Namespace.Class::myChar  
```  
  
## <a name="configuration"></a>Yapılandırma  
 MDA yapılandırma, bildirilen sıralama bilgileri dahil olan alan veya yöntem adları göre filtrelemenize izin verir.  Aşağıdaki örnek kullanımını gösterir `methodFilter`, `fieldFilter`, ve `match` filtre belirtmek için öğeleri.  Ayar `name` özniteliği için bir yıldız işareti (*), her şeyi eşleşir.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma için Hazırlama](../../../docs/framework/interop/interop-marshaling.md)
