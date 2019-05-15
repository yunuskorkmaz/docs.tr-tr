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
ms.openlocfilehash: e7e316f874a2b559cb3fe9d64a9ec7cf25addbe5
ms.sourcegitcommit: 682c64df0322c7bda016f8bfea8954e9b31f1990
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2019
ms.locfileid: "65557773"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a><span data-ttu-id="c337e-102">Azaltma: Denetim karakteri DataContractJsonSerializer ile seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="c337e-102">Mitigation: Serialization of Control Characters with the DataContractJsonSerializer</span></span>

<span data-ttu-id="c337e-103">.NET Framework 4.7 ile hangi denetiminde karakterleri ile serileştirilme şeklini başlangıç <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ECMAScript V6 ve V8 değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="c337e-103">Starting with the .NET Framework 4.7, the way in which control characters are serialized with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> has changed to conform to ECMAScript V6 and V8.</span></span> 
 
## <a name="impact"></a><span data-ttu-id="c337e-104">Etki</span><span class="sxs-lookup"><span data-stu-id="c337e-104">Impact</span></span>

<span data-ttu-id="c337e-105">.NET framework 4.6.2 ve önceki sürümlerinde, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> bazı özel denetim karakterleri gibi serileştirmek değil `\b`, `\f`, ve `\t`, ECMAScript V6 ve V8 standartları ile uyumlu bir şekilde.</span><span class="sxs-lookup"><span data-stu-id="c337e-105">In the .NET framework 4.6.2 and earlier versions, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> did not serialize some special control characters, such as `\b`, `\f`, and `\t`, in a way that was compatible with the ECMAScript V6 and V8 standards.</span></span>

<span data-ttu-id="c337e-106">.NET Framework 4.7 ile başlayan .NET Framework sürümlerini hedefleyen uygulamalar için bu denetim karakterleri serileştirilmesi V8 ECMAScript V6 ile uyumludur.</span><span class="sxs-lookup"><span data-stu-id="c337e-106">For apps that target versions of the .NET Framework starting with the .NET Framework 4.7, serialization of these control characters is compatible with ECMAScript V6 and V8.</span></span> <span data-ttu-id="c337e-107">Aşağıdaki API'leri etkilenir:</span><span class="sxs-lookup"><span data-stu-id="c337e-107">The following APIs are affected:</span></span>

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 

## <a name="mitigation"></a><span data-ttu-id="c337e-108">Azaltma</span><span class="sxs-lookup"><span data-stu-id="c337e-108">Mitigation</span></span>

<span data-ttu-id="c337e-109">.NET Framework 4.7 ile başlayan .NET Framework sürümlerini hedefleyen uygulamalar için bu davranışı varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="c337e-109">For apps that target versions of the .NET Framework starting with the .NET Framework 4.7, this behavior is enabled by default.</span></span>

<span data-ttu-id="c337e-110">Bu davranış arzu değil ise, aşağıdaki satırı ekleyerek bu özelliği seçebilirsiniz `<runtime>` app.config veya web.config dosyasının:</span><span class="sxs-lookup"><span data-stu-id="c337e-110">If this behavior is not desirable, you can opt out of this feature by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```
 
## <a name="see-also"></a><span data-ttu-id="c337e-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c337e-111">See also</span></span>

- [<span data-ttu-id="c337e-112">.NET Framework 4.7 yeniden hedefleme değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="c337e-112">Retargeting Changes in the .NET Framework 4.7</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)
