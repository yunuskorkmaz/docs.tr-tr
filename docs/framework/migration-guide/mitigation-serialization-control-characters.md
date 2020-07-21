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
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a><span data-ttu-id="7a7d8-103">Risk azaltma: DataContractJsonSerializer ile denetim karakterlerinin serileştirilmesi</span><span class="sxs-lookup"><span data-stu-id="7a7d8-103">Mitigation: Serialization of control characters with the DataContractJsonSerializer</span></span>

<span data-ttu-id="7a7d8-104">.NET Framework 4,7 ' den başlayarak, denetim karakterlerinin ile serileştirildiği yol <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ECMAScript V6 ve V8 ile uyumlu olarak değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7a7d8-104">Starting with .NET Framework 4.7, the way in which control characters are serialized with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> has changed to conform to ECMAScript V6 and V8.</span></span>

## <a name="impact"></a><span data-ttu-id="7a7d8-105">Etki</span><span class="sxs-lookup"><span data-stu-id="7a7d8-105">Impact</span></span>

<span data-ttu-id="7a7d8-106">.NET Framework 4.6.2 ve önceki sürümlerde,, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ve gibi bazı özel denetim karakterlerini `\b` `\f` `\t` ECMAScript V6 ve V8 standartlarıyla uyumlu olacak şekilde serileştirmedi.</span><span class="sxs-lookup"><span data-stu-id="7a7d8-106">In .NET Framework 4.6.2 and earlier versions, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> did not serialize some special control characters, such as `\b`, `\f`, and `\t`, in a way that was compatible with the ECMAScript V6 and V8 standards.</span></span>

<span data-ttu-id="7a7d8-107">.NET Framework 4,7 ' den başlayarak .NET Framework sürümlerini hedefleyen uygulamalar için, bu denetim karakterlerinin serileştirilmesi ECMAScript V6 ve V8 ile uyumludur.</span><span class="sxs-lookup"><span data-stu-id="7a7d8-107">For apps that target versions of .NET Framework starting with .NET Framework 4.7, serialization of these control characters is compatible with ECMAScript V6 and V8.</span></span> <span data-ttu-id="7a7d8-108">Aşağıdaki API 'Ler etkilenir:</span><span class="sxs-lookup"><span data-stu-id="7a7d8-108">The following APIs are affected:</span></span>

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>

## <a name="mitigation"></a><span data-ttu-id="7a7d8-109">Risk azaltma</span><span class="sxs-lookup"><span data-stu-id="7a7d8-109">Mitigation</span></span>

<span data-ttu-id="7a7d8-110">.NET Framework 4,7 ' den başlayarak .NET Framework sürümlerini hedefleyen uygulamalar için, bu davranış varsayılan olarak etkinleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7a7d8-110">For apps that target versions of .NET Framework starting with .NET Framework 4.7, this behavior is enabled by default.</span></span>

<span data-ttu-id="7a7d8-111">Bu davranış istenmediğinde, `<runtime>` app.config veya web.config dosyasının bölümüne aşağıdaki satırı ekleyerek bu özelliği devre dışı bırakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7a7d8-111">If this behavior is not desirable, you can opt out of this feature by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```

## <a name="see-also"></a><span data-ttu-id="7a7d8-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a7d8-112">See also</span></span>

- [<span data-ttu-id="7a7d8-113">Uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="7a7d8-113">Application compatibility</span></span>](application-compatibility.md)
