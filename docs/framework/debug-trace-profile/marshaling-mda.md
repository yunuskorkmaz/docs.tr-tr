---
title: MDA Sıralama
description: CLR bir yöntem parametresi veya bir yapı alanı için sıralama bilgilerini ayarlarsa çağrılan, yönetilen hata ayıklama Yardımcısı 'nı (MDA) gözden geçirin.
ms.date: 03/30/2017
helpviewer_keywords:
- marshaling, run-time errors
- marshaling MDA
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: 5433b1f8-b0e5-40c9-a49a-0e5bd213363d
ms.openlocfilehash: afe54a2104e05f8fad57c7cbba4988b013aff761
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96271180"
---
# <a name="marshaling-mda"></a>MDA Sıralama

`marshaling`Yönetilen hata ayıklama Yardımcısı (MDA), clr bir yöntem parametresi veya bir yapının alanı için sıralama bilgilerini ayarlarsa etkinleştirilir. Bu MDA, JıT derlenmiş derlemeler için çalışmaz.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  

 Bu MDA, CLR üzerinde hiçbir etkisi yoktur.  
  
## <a name="output"></a>Çıkış  

 MDA, yönetilen ve yönetilmeyen bağlamlardaki parametre ya da alanın türünü ve türünü içeren yapıyı ya da yöntemi görüntüler.  Bir alan için çıktının bir örneği aşağıda verilmiştir:  
  
```output
Marshaling from 'Char' to 'ANSI char'  
name="assembly!Namespace.Class::myChar  
```  
  
## <a name="configuration"></a>Yapılandırma  

 MDA yapılandırması, bildirilen sıralama bilgilerini ilgili alana veya yöntem adlarına göre filtrelemenize izin verir.  Aşağıdaki örnek `methodFilter` , `fieldFilter` `match` filtre belirtmek için, ve öğelerinin kullanımını gösterir.  `name`Özniteliği bir yıldız işareti () olarak ayarlamak \* her şeyi eşleştirecektir.  
  
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
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma Hazırlama](../interop/interop-marshaling.md)
