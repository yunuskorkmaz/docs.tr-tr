---
ms.openlocfilehash: 75c7385bceec2595683d1c0d97a7df9264e3bf0b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496925"
---
### <a name="xmlserializer-fails-while-serializing-a-type-that-hides-an-accessible-member-with-an-inaccessible-one"></a><span data-ttu-id="39276-101">XmlSerializer, erişilebilir bir üyeyi, erişilemeyen bir üyeyi gizleyen bir tür serileştirirken başarısız oluyor</span><span class="sxs-lookup"><span data-stu-id="39276-101">XmlSerializer fails while serializing a type that hides an accessible member with an inaccessible one</span></span>

#### <a name="details"></a><span data-ttu-id="39276-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="39276-102">Details</span></span>

<span data-ttu-id="39276-103">Türetilmiş bir tür serileştirilirken, <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> tür, ana tür üzerinde daha önce erişilebilen (örneğin, genel, örneğin) aynı ada sahip bir alan veya özellik içeriyorsa, erişilebilir bir alanı veya özelliği (' New ' anahtar sözcüğü aracılığıyla) içeren bir alan veya özellik içeriyorsa, bu başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="39276-103">When serializing a derived type, the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> can fail if the type contains an inaccessible field or property that hides (via the 'new' keyword) a field or property of the same name that was previously accessible (public, for example) on the base type.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="39276-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="39276-104">Suggestion</span></span>

<span data-ttu-id="39276-105">Bu sorun, yeni bir <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> (örneğin, genel olarak işaretlenerek) tarafından erişilebilen yeni ve gizlenebildiği için çözülebilir. Alternatif olarak, aşağıdaki yapılandırma ayarı 4,0 davranışa dönüşecektir <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> , bu da sorunu düzeltir:</span><span class="sxs-lookup"><span data-stu-id="39276-105">This problem can be solved by making the new, hiding member accessible to the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> (by marking it public, for example).Alternatively, the following config setting will revert to 4.0 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> behavior, which will fix the problem:</span></span><pre><code class="lang-xml">&lt;system.xml.serialization&gt;&#13;&#10;&lt;xmlSerializer useLegacySerializerGeneration=&quot;true&quot; /&gt;&#13;&#10;&lt;/system.xml.serialization&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="39276-106">Name</span><span class="sxs-lookup"><span data-stu-id="39276-106">Name</span></span>    | <span data-ttu-id="39276-107">Değer</span><span class="sxs-lookup"><span data-stu-id="39276-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="39276-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="39276-108">Scope</span></span>   |<span data-ttu-id="39276-109">İkincil</span><span class="sxs-lookup"><span data-stu-id="39276-109">Minor</span></span>|
|<span data-ttu-id="39276-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="39276-110">Version</span></span>|<span data-ttu-id="39276-111">4,5</span><span class="sxs-lookup"><span data-stu-id="39276-111">4.5</span></span>|
|<span data-ttu-id="39276-112">Tür</span><span class="sxs-lookup"><span data-stu-id="39276-112">Type</span></span>|<span data-ttu-id="39276-113">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="39276-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="39276-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="39276-114">Affected APIs</span></span>

- <xref:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.TextWriter,System.Object)?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.Serialize(System.Object,System.Xml.Serialization.XmlSerializationWriter)?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object)?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.Stream,System.Object,System.Xml.Serialization.XmlSerializerNamespaces)?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.TextWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces)?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces)?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces,System.String,System.String)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.Stream,System.Object)`
- `M:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.TextWriter,System.Object)`
- `M:System.Xml.Serialization.XmlSerializer.Serialize(System.Object,System.Xml.Serialization.XmlSerializationWriter)`
- `M:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object)`
- `M:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.Stream,System.Object,System.Xml.Serialization.XmlSerializerNamespaces)`
- `M:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.TextWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces)`
- `M:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces)`
- `M:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces,System.String)`
- `M:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces,System.String,System.String)`

-->
