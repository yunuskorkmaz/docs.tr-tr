---
title: "Azaltma: Serileştirme DataContractJsonSerializer ile denetim karakterleri"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6da580d208736a64e2094f701fb4c1241a488322
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a>Azaltma: Serileştirme DataContractJsonSerializer ile denetim karakterleri

.NET Framework 4.7 ile hangi denetiminde karakter ile serileştirilir şekilde başlangıç <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ECMAScript V6 ve V8 uygun olarak değiştirildi. 
 
## <a name="impact"></a>Etki

.NET framework 4.6.2 ve önceki sürümlerde, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> bazı özel denetim karakterleri gibi seri değil `\b`, `\f`, ve `\t`, ECMAScript V6 ve V8 standartlarla uyumlu bir biçimde.

.NET Framework 4.7 ile başlayan .NET Framework sürümlerini hedefleyen uygulamalar için bu denetim karakterleri serileştirmek ECMAScript V6 ve V8 ile uyumludur. Aşağıdaki API'leri etkilenir:

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>

## <a name="mitigation"></a>Azaltma

.NET Framework 4.7 ile başlayan .NET Framework sürümlerini hedefleyen uygulamalar için bu davranışı varsayılan olarak etkindir.

Bu davranış arzu değilse, aşağıdaki satırı ekleyerek dışında bu özellik seçebilirsiniz `<runtime>` app.config veya web.config dosyasının:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```
 
## <a name="see-also"></a>Ayrıca bkz.
[.NET Framework 4.7 yeniden hedefleme değişiklikleri](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)
