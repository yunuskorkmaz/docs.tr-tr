---
title: 'Azaltma: Denetim karakteri DataContractJsonSerializer ile seri hale getirme'
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e7e316f874a2b559cb3fe9d64a9ec7cf25addbe5
ms.sourcegitcommit: 682c64df0322c7bda016f8bfea8954e9b31f1990
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2019
ms.locfileid: "65557773"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a>Azaltma: Denetim karakteri DataContractJsonSerializer ile seri hale getirme

.NET Framework 4.7 ile hangi denetiminde karakterleri ile serileştirilme şeklini başlangıç <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ECMAScript V6 ve V8 değiştirildi. 
 
## <a name="impact"></a>Etki

.NET framework 4.6.2 ve önceki sürümlerinde, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> bazı özel denetim karakterleri gibi serileştirmek değil `\b`, `\f`, ve `\t`, ECMAScript V6 ve V8 standartları ile uyumlu bir şekilde.

.NET Framework 4.7 ile başlayan .NET Framework sürümlerini hedefleyen uygulamalar için bu denetim karakterleri serileştirilmesi V8 ECMAScript V6 ile uyumludur. Aşağıdaki API'leri etkilenir:

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 

## <a name="mitigation"></a>Azaltma

.NET Framework 4.7 ile başlayan .NET Framework sürümlerini hedefleyen uygulamalar için bu davranışı varsayılan olarak etkindir.

Bu davranış arzu değil ise, aşağıdaki satırı ekleyerek bu özelliği seçebilirsiniz `<runtime>` app.config veya web.config dosyasının:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```
 
## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework 4.7 yeniden hedefleme değişiklikleri](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)
