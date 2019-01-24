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
ms.openlocfilehash: 31f946fa01f3d6334011098d12483445159ce54a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54738124"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a>Azaltma: Denetim karakteri DataContractJsonSerializer ile seri hale getirme

.NET Framework 4.7 ile hangi denetiminde karakterleri ile serileştirilme şeklini başlangıç <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ECMAScript V6 ve V8 değiştirildi. 
 
## <a name="impact"></a>Etki

.NET framework 4.6.2 ve önceki sürümlerinde, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> bazı özel denetim karakterleri gibi serileştirmek değil `\b`, `\f`, ve `\t`, ECMAScript V6 ve V8 standartları ile uyumlu bir şekilde.

.NET Framework 4.7 ile başlayan .NET Framework sürümlerini hedefleyen uygulamalar için bu denetim karakterleri serileştirilmesi V8 ECMAScript V6 ile uyumludur. Aşağıdaki API'leri etkilenir:

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>
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
