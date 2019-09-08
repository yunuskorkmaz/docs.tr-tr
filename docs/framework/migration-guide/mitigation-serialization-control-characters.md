---
title: Mayı DataContractJsonSerializer ile denetim karakterlerinin serileştirilmesi
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12b26c8cc01b7af1c3b345d2f274a1d25a19d689
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70789848"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a>Mayı DataContractJsonSerializer ile denetim karakterlerinin serileştirilmesi

.NET Framework 4,7 ' den başlayarak, denetim karakterlerinin ile serileştirildiği yol ECMAScript V6 ve V8 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ile uyumlu olarak değiştirilmiştir. 
 
## <a name="impact"></a>Etki

.NET Framework 4.6.2 ve <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> önceki sürümlerinde,, ve `\t`gibi bazı özel denetim karakterlerini `\b` `\f`ECMAScript V6 ve V8 standartlarıyla uyumlu olacak şekilde serileştirmedi.

.NET Framework 4,7 ' den başlayarak .NET Framework sürümlerini hedefleyen uygulamalar için, bu denetim karakterlerinin serileştirilmesi ECMAScript V6 ve V8 ile uyumludur. Aşağıdaki API 'Ler etkilenir:

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 

## <a name="mitigation"></a>Azaltma

.NET Framework 4,7 ' den başlayarak .NET Framework sürümlerini hedefleyen uygulamalar için, bu davranış varsayılan olarak etkinleştirilmiştir.

Bu davranış istenmediğinde, App. config veya Web. config dosyasının `<runtime>` bölümüne aşağıdaki satırı ekleyerek bu özelliği devre dışı bırakabilirsiniz:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```
 
## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework 4,7 'de yeniden hedefleme değişiklikleri](retargeting-changes-in-the-net-framework-4-7.md)
