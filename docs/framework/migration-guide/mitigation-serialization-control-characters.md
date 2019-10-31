---
title: 'Risk azaltma: DataContractJsonSerializer ile denetim karakterlerinin serileştirilmesi'
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
ms.openlocfilehash: 5f8218d0f369f25b1add501fdc975d6dccfe90fa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126144"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a>Risk azaltma: DataContractJsonSerializer ile denetim karakterlerinin serileştirilmesi

.NET Framework 4,7 ' den başlayarak, denetim karakterlerinin <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ile serileştirilme yöntemi ECMAScript V6 ve V8 ile uyumlu olacak şekilde değiştirilmiştir. 
 
## <a name="impact"></a>Etki

.NET Framework 4.6.2 ve önceki sürümlerde <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, `\b`, `\f`ve `\t`gibi bazı özel denetim karakterlerini ECMAScript V6 ve V8 standartlarıyla uyumlu olacak şekilde serileştirmedi.

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
