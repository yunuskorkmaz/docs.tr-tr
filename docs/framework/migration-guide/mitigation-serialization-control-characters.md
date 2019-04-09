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
ms.openlocfilehash: 3355841298e039652eb81918eac98186c1a1f833
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59182133"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a><span data-ttu-id="b34ef-102">Azaltma: Denetim karakteri DataContractJsonSerializer ile seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="b34ef-102">Mitigation: Serialization of Control Characters with the DataContractJsonSerializer</span></span>

<span data-ttu-id="b34ef-103">.NET Framework 4.7 ile hangi denetiminde karakterleri ile serileştirilme şeklini başlangıç <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ECMAScript V6 ve V8 değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="b34ef-103">Starting with the .NET Framework 4.7, the way in which control characters are serialized with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> has changed to conform to ECMAScript V6 and V8.</span></span> 
 
## <a name="impact"></a><span data-ttu-id="b34ef-104">Etki</span><span class="sxs-lookup"><span data-stu-id="b34ef-104">Impact</span></span>

<span data-ttu-id="b34ef-105">.NET framework 4.6.2 ve önceki sürümlerinde, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> bazı özel denetim karakterleri gibi serileştirmek değil `\b`, `\f`, ve `\t`, ECMAScript V6 ve V8 standartları ile uyumlu bir şekilde.</span><span class="sxs-lookup"><span data-stu-id="b34ef-105">In the .NET framework 4.6.2 and earlier versions, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> did not serialize some special control characters, such as `\b`, `\f`, and `\t`, in a way that was compatible with the ECMAScript V6 and V8 standards.</span></span>

<span data-ttu-id="b34ef-106">.NET Framework 4.7 ile başlayan .NET Framework sürümlerini hedefleyen uygulamalar için bu denetim karakterleri serileştirilmesi V8 ECMAScript V6 ile uyumludur.</span><span class="sxs-lookup"><span data-stu-id="b34ef-106">For apps that target versions of the .NET Framework starting with the .NET Framework 4.7, serialization of these control characters is compatible with ECMAScript V6 and V8.</span></span> <span data-ttu-id="b34ef-107">Aşağıdaki API'leri etkilenir:</span><span class="sxs-lookup"><span data-stu-id="b34ef-107">The following APIs are affected:</span></span>

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>

## <a name="mitigation"></a><span data-ttu-id="b34ef-108">Azaltma</span><span class="sxs-lookup"><span data-stu-id="b34ef-108">Mitigation</span></span>

<span data-ttu-id="b34ef-109">.NET Framework 4.7 ile başlayan .NET Framework sürümlerini hedefleyen uygulamalar için bu davranışı varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="b34ef-109">For apps that target versions of the .NET Framework starting with the .NET Framework 4.7, this behavior is enabled by default.</span></span>

<span data-ttu-id="b34ef-110">Bu davranış arzu değil ise, aşağıdaki satırı ekleyerek bu özelliği seçebilirsiniz `<runtime>` app.config veya web.config dosyasının:</span><span class="sxs-lookup"><span data-stu-id="b34ef-110">If this behavior is not desirable, you can opt out of this feature by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```
 
## <a name="see-also"></a><span data-ttu-id="b34ef-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b34ef-111">See also</span></span>

- [<span data-ttu-id="b34ef-112">.NET Framework 4.7 yeniden hedefleme değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="b34ef-112">Retargeting Changes in the .NET Framework 4.7</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)
