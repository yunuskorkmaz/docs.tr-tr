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
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a><span data-ttu-id="64441-102">Azaltma: DataContractJsonSerializer ile kontrol karakterlerinin serileştirilmesi</span><span class="sxs-lookup"><span data-stu-id="64441-102">Mitigation: Serialization of control characters with the DataContractJsonSerializer</span></span>

<span data-ttu-id="64441-103">.NET Framework 4.7 ile başlayarak, kontrol karakterlerinin serihale <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> getirilme şekli ECMAScript V6 ve V8'e uyacak şekilde değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="64441-103">Starting with .NET Framework 4.7, the way in which control characters are serialized with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> has changed to conform to ECMAScript V6 and V8.</span></span>

## <a name="impact"></a><span data-ttu-id="64441-104">Etki</span><span class="sxs-lookup"><span data-stu-id="64441-104">Impact</span></span>

<span data-ttu-id="64441-105">.NET Framework 4.6.2 ve önceki <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> sürümlerde, ECMAScript V6 `\b`ve `\f` `\t`V8 standartlarıyla uyumlu bir şekilde bazı özel kontrol karakterleri serihale getirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="64441-105">In .NET Framework 4.6.2 and earlier versions, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> did not serialize some special control characters, such as `\b`, `\f`, and `\t`, in a way that was compatible with the ECMAScript V6 and V8 standards.</span></span>

<span data-ttu-id="64441-106">.NET Framework 4.7 ile başlayan .NET Framework sürümlerini hedefleyen uygulamalar için bu kontrol karakterlerinin serihale getirilmesi ECMAScript V6 ve V8 ile uyumludur.</span><span class="sxs-lookup"><span data-stu-id="64441-106">For apps that target versions of .NET Framework starting with .NET Framework 4.7, serialization of these control characters is compatible with ECMAScript V6 and V8.</span></span> <span data-ttu-id="64441-107">Aşağıdaki API'ler etkilenir:</span><span class="sxs-lookup"><span data-stu-id="64441-107">The following APIs are affected:</span></span>

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>

## <a name="mitigation"></a><span data-ttu-id="64441-108">Risk azaltma</span><span class="sxs-lookup"><span data-stu-id="64441-108">Mitigation</span></span>

<span data-ttu-id="64441-109">.NET Framework 4.7 ile başlayan .NET Framework sürümlerini hedefleyen uygulamalar için bu davranış varsayılan olarak etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="64441-109">For apps that target versions of .NET Framework starting with .NET Framework 4.7, this behavior is enabled by default.</span></span>

<span data-ttu-id="64441-110">Bu davranış istenmiyorsa, app.config veya web.config dosyasının `<runtime>` bölümüne aşağıdaki satırı ekleyerek bu özelliği devre dışı kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="64441-110">If this behavior is not desirable, you can opt out of this feature by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```

## <a name="see-also"></a><span data-ttu-id="64441-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64441-111">See also</span></span>

- [<span data-ttu-id="64441-112">Uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="64441-112">Application compatibility</span></span>](application-compatibility.md)
