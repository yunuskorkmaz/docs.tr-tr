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
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a><span data-ttu-id="9f55c-102">Mayı DataContractJsonSerializer ile denetim karakterlerinin serileştirilmesi</span><span class="sxs-lookup"><span data-stu-id="9f55c-102">Mitigation: Serialization of Control Characters with the DataContractJsonSerializer</span></span>

<span data-ttu-id="9f55c-103">.NET Framework 4,7 ' den başlayarak, denetim karakterlerinin ile serileştirildiği yol ECMAScript V6 ve V8 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ile uyumlu olarak değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9f55c-103">Starting with the .NET Framework 4.7, the way in which control characters are serialized with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> has changed to conform to ECMAScript V6 and V8.</span></span> 
 
## <a name="impact"></a><span data-ttu-id="9f55c-104">Etki</span><span class="sxs-lookup"><span data-stu-id="9f55c-104">Impact</span></span>

<span data-ttu-id="9f55c-105">.NET Framework 4.6.2 ve <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> önceki sürümlerinde,, ve `\t`gibi bazı özel denetim karakterlerini `\b` `\f`ECMAScript V6 ve V8 standartlarıyla uyumlu olacak şekilde serileştirmedi.</span><span class="sxs-lookup"><span data-stu-id="9f55c-105">In the .NET framework 4.6.2 and earlier versions, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> did not serialize some special control characters, such as `\b`, `\f`, and `\t`, in a way that was compatible with the ECMAScript V6 and V8 standards.</span></span>

<span data-ttu-id="9f55c-106">.NET Framework 4,7 ' den başlayarak .NET Framework sürümlerini hedefleyen uygulamalar için, bu denetim karakterlerinin serileştirilmesi ECMAScript V6 ve V8 ile uyumludur.</span><span class="sxs-lookup"><span data-stu-id="9f55c-106">For apps that target versions of the .NET Framework starting with the .NET Framework 4.7, serialization of these control characters is compatible with ECMAScript V6 and V8.</span></span> <span data-ttu-id="9f55c-107">Aşağıdaki API 'Ler etkilenir:</span><span class="sxs-lookup"><span data-stu-id="9f55c-107">The following APIs are affected:</span></span>

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 

## <a name="mitigation"></a><span data-ttu-id="9f55c-108">Azaltma</span><span class="sxs-lookup"><span data-stu-id="9f55c-108">Mitigation</span></span>

<span data-ttu-id="9f55c-109">.NET Framework 4,7 ' den başlayarak .NET Framework sürümlerini hedefleyen uygulamalar için, bu davranış varsayılan olarak etkinleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9f55c-109">For apps that target versions of the .NET Framework starting with the .NET Framework 4.7, this behavior is enabled by default.</span></span>

<span data-ttu-id="9f55c-110">Bu davranış istenmediğinde, App. config veya Web. config dosyasının `<runtime>` bölümüne aşağıdaki satırı ekleyerek bu özelliği devre dışı bırakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9f55c-110">If this behavior is not desirable, you can opt out of this feature by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```
 
## <a name="see-also"></a><span data-ttu-id="9f55c-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f55c-111">See also</span></span>

- [<span data-ttu-id="9f55c-112">.NET Framework 4,7 'de yeniden hedefleme değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="9f55c-112">Retargeting Changes in the .NET Framework 4.7</span></span>](retargeting-changes-in-the-net-framework-4-7.md)
