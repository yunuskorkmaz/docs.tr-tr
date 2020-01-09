---
title: DataContractJsonSerializer ile denetim karakterlerinin serileştirilmesi
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
ms.openlocfilehash: 209f7827e61ef72de1d64fad46dc9f241fa6edef
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346580"
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

- [Uygulama uyumluluğu](application-compatibility.md)
