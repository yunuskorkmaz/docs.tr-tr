---
ms.openlocfilehash: afdf1e20db7dc564ddfb6028238604f97e00971a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614787"
---
### <a name="serialization-of-control-characters-with-datacontractjsonserializer-is-now-compatible-with-ecmascript-v6-and-v8"></a><span data-ttu-id="c7542-101">DataContractJsonSerializer ile denetim karakterlerinin serileştirilmesi artık ECMAScript V6 ve V8 ile uyumludur</span><span class="sxs-lookup"><span data-stu-id="c7542-101">Serialization of control characters with DataContractJsonSerializer is now compatible with ECMAScript V6 and V8</span></span>

#### <a name="details"></a><span data-ttu-id="c7542-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="c7542-102">Details</span></span>

<span data-ttu-id="c7542-103">.NET Framework 4.6.2 ve önceki sürümlerde, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=fullName> \b, \f ve \t gibi bazı özel denetim karakterlerini ECMAScript V6 ve V8 standartlarıyla uyumlu olacak şekilde serileştirmedi.</span><span class="sxs-lookup"><span data-stu-id="c7542-103">In .NET Framework 4.6.2 and earlier versions, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=fullName> did not serialize some special control characters, such as \b, \f, and \t, in a way that was compatible with the ECMAScript V6 and V8 standards.</span></span> <span data-ttu-id="c7542-104">.NET Framework 4,7 ' den başlayarak, bu denetim karakterlerinin serileştirilmesi ECMAScript V6 ve V8 ile uyumludur.</span><span class="sxs-lookup"><span data-stu-id="c7542-104">Starting with .NET Framework 4.7, serialization of these control characters is compatible with ECMAScript V6 and V8.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c7542-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="c7542-105">Suggestion</span></span>

<span data-ttu-id="c7542-106">.NET Framework 4,7 ' i hedefleyen uygulamalar için bu özellik varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="c7542-106">For apps that target the .NET Framework 4.7, this feature is enabled by default.</span></span> <span data-ttu-id="c7542-107">Bu davranış istenmediğinde, `<runtime>` app.config veya web.config dosyasının bölümüne aşağıdaki satırı ekleyerek bu özelliği devre dışı bırakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c7542-107">If this behavior is not desirable, you can opt out of this feature by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```

| <span data-ttu-id="c7542-108">Name</span><span class="sxs-lookup"><span data-stu-id="c7542-108">Name</span></span>    | <span data-ttu-id="c7542-109">Değer</span><span class="sxs-lookup"><span data-stu-id="c7542-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c7542-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="c7542-110">Scope</span></span>   | <span data-ttu-id="c7542-111">Edge</span><span class="sxs-lookup"><span data-stu-id="c7542-111">Edge</span></span>        |
| <span data-ttu-id="c7542-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="c7542-112">Version</span></span> | <span data-ttu-id="c7542-113">4,7</span><span class="sxs-lookup"><span data-stu-id="c7542-113">4.7</span></span>         |
| <span data-ttu-id="c7542-114">Tür</span><span class="sxs-lookup"><span data-stu-id="c7542-114">Type</span></span>    | <span data-ttu-id="c7542-115">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="c7542-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="c7542-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="c7542-116">Affected APIs</span></span>

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlDictionaryWriter,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlWriter,System.Object)?displayProperty=nameWithType>
