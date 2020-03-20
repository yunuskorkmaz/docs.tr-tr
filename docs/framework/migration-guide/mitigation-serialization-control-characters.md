---
title: DataContractJsonSerializer ile kontrol karakterlerinin serileştirilmesi
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
ms.openlocfilehash: b60b78f9ee944552fafbe75754ecd29d60dd4093
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181206"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a>Azaltma: DataContractJsonSerializer ile kontrol karakterlerinin serileştirilmesi

.NET Framework 4.7 ile başlayarak, kontrol karakterlerinin serihale <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> getirilme şekli ECMAScript V6 ve V8'e uyacak şekilde değiştirildi.

## <a name="impact"></a>Etki

.NET Framework 4.6.2 ve önceki <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> sürümlerde, ECMAScript V6 `\b`ve `\f` `\t`V8 standartlarıyla uyumlu bir şekilde bazı özel kontrol karakterleri serihale getirilmiştir.

.NET Framework 4.7 ile başlayan .NET Framework sürümlerini hedefleyen uygulamalar için bu kontrol karakterlerinin serihale getirilmesi ECMAScript V6 ve V8 ile uyumludur. Aşağıdaki API'ler etkilenir:

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>

## <a name="mitigation"></a>Risk azaltma

.NET Framework 4.7 ile başlayan .NET Framework sürümlerini hedefleyen uygulamalar için bu davranış varsayılan olarak etkinleştirilir.

Bu davranış istenmiyorsa, app.config veya web.config dosyasının `<runtime>` bölümüne aşağıdaki satırı ekleyerek bu özelliği devre dışı kullanabilirsiniz:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama uyumluluğu](application-compatibility.md)
