---
title: DataContractJsonSerializer ile denetim karakterlerinin serileştirilmesi
description: Denetim karakterlerinin serileştirilmesi .NET Framework 4,7 ' deki ECMAScript V6 ve V8 uyumlu olacak şekilde nasıl değiştiği hakkında bilgi edinin.
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
ms.openlocfilehash: a317884da014097a7a60aef2cef4ec146ccb04f7
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475391"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a>Risk azaltma: DataContractJsonSerializer ile denetim karakterlerinin serileştirilmesi

.NET Framework 4,7 ' den başlayarak, denetim karakterlerinin ile serileştirildiği yol <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ECMAScript V6 ve V8 ile uyumlu olarak değiştirilmiştir.

## <a name="impact"></a>Etki

.NET Framework 4.6.2 ve önceki sürümlerde,, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ve gibi bazı özel denetim karakterlerini `\b` `\f` `\t` ECMAScript V6 ve V8 standartlarıyla uyumlu olacak şekilde serileştirmedi.

.NET Framework 4,7 ' den başlayarak .NET Framework sürümlerini hedefleyen uygulamalar için, bu denetim karakterlerinin serileştirilmesi ECMAScript V6 ve V8 ile uyumludur. Aşağıdaki API 'Ler etkilenir:

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>

## <a name="mitigation"></a>Risk azaltma

.NET Framework 4,7 ' den başlayarak .NET Framework sürümlerini hedefleyen uygulamalar için, bu davranış varsayılan olarak etkinleştirilmiştir.

Bu davranış istenmediğinde, `<runtime>` app.config veya web.config dosyasının bölümüne aşağıdaki satırı ekleyerek bu özelliği devre dışı bırakabilirsiniz:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama uyumluluğu](application-compatibility.md)
