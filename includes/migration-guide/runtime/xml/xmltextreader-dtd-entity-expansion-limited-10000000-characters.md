---
ms.openlocfilehash: e56d896f093d6cd28ed0d6640ba154e5d4593c6d
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496677"
---
### <a name="xmltextreader-dtd-entity-expansion-is-limited-to-10000000-characters"></a><span data-ttu-id="7c0fe-101">XmlTextReader DTD varlık genişletmesi 10.000.000 karakterle sınırlıdır</span><span class="sxs-lookup"><span data-stu-id="7c0fe-101">XmlTextReader DTD entity expansion is limited to 10,000,000 characters</span></span>

#### <a name="details"></a><span data-ttu-id="7c0fe-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="7c0fe-102">Details</span></span>

<span data-ttu-id="7c0fe-103">DTD varlık genişletmesi artık 10.000.000 karakterle sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="7c0fe-103">DTD entity expansion is now limited to 10,000,000 characters.</span></span> <span data-ttu-id="7c0fe-104">DTD varlık genişletme olmadan veya sınırlı DTD varlık genişletme ile XML dosyalarının yüklenmesi etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="7c0fe-104">Loading XML files without DTD entity expansion or with limited DTD entity expansion is unaffected.</span></span> <span data-ttu-id="7c0fe-105">10.000.000 karakteri aşan DTD varlıklarını içeren dosyalar yüklenemedi ve şimdi bir özel durum oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="7c0fe-105">Files with DTD entities that expand to more than 10,000,000 characters fail to load, and now throw an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7c0fe-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="7c0fe-106">Suggestion</span></span>

<span data-ttu-id="7c0fe-107">DTD varlık genişletmesi sınırı çok düşük 10.000.000 ise, bu değer özelliği ile geçersiz kılınabilir <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities> .</span><span class="sxs-lookup"><span data-stu-id="7c0fe-107">If the limit of DTD entity expansion is too low 10,000,000, the value can be overridden with the <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities> property.</span></span> <span data-ttu-id="7c0fe-108"><xref:System.Xml.XmlReaderSettings?displayProperty=fullName>Uygun değere sahip olan bir, <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities?displayProperty=fullName> <code>XmlReader.Create</code> <xref:System.Xml.XmlReaderSettings?displayProperty=fullName> (IE <xref:System.Xml.XmlReader.Create(System.String,System.Xml.XmlReaderSettings)> ) ile birlikte geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="7c0fe-108">An <xref:System.Xml.XmlReaderSettings?displayProperty=fullName> with the proper <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities?displayProperty=fullName> value can be passed to <code>XmlReader.Create</code> that takes <xref:System.Xml.XmlReaderSettings?displayProperty=fullName> (ie. <xref:System.Xml.XmlReader.Create(System.String,System.Xml.XmlReaderSettings)>)</span></span>

| <span data-ttu-id="7c0fe-109">Name</span><span class="sxs-lookup"><span data-stu-id="7c0fe-109">Name</span></span>    | <span data-ttu-id="7c0fe-110">Değer</span><span class="sxs-lookup"><span data-stu-id="7c0fe-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7c0fe-111">Kapsam</span><span class="sxs-lookup"><span data-stu-id="7c0fe-111">Scope</span></span>   |<span data-ttu-id="7c0fe-112">Edge</span><span class="sxs-lookup"><span data-stu-id="7c0fe-112">Edge</span></span>|
|<span data-ttu-id="7c0fe-113">Sürüm</span><span class="sxs-lookup"><span data-stu-id="7c0fe-113">Version</span></span>|<span data-ttu-id="7c0fe-114">4,5</span><span class="sxs-lookup"><span data-stu-id="7c0fe-114">4.5</span></span>|
|<span data-ttu-id="7c0fe-115">Tür</span><span class="sxs-lookup"><span data-stu-id="7c0fe-115">Type</span></span>|<span data-ttu-id="7c0fe-116">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="7c0fe-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="7c0fe-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="7c0fe-117">Affected APIs</span></span>

- <xref:System.Xml.XmlTextReader?displayProperty=nameWithType>
- <xref:System.Xml.XmlTextReader.%23ctor>
- <xref:System.Xml.XmlTextReader.%23ctor(System.IO.Stream)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.IO.Stream,System.Xml.XmlNameTable)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.IO.Stream,System.Xml.XmlNodeType,System.Xml.XmlParserContext)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.IO.TextReader)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.IO.TextReader,System.Xml.XmlNameTable)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.String)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.Stream)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.Stream,System.Xml.XmlNameTable)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.TextReader)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.TextReader,System.Xml.XmlNameTable)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.String,System.Xml.XmlNameTable)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.String,System.Xml.XmlNodeType,System.Xml.XmlParserContext)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.Xml.XmlNameTable)>

<!--

#### Affected APIs

- `T:System.Xml.XmlTextReader`
- `M:System.Xml.XmlTextReader.#ctor`
- `M:System.Xml.XmlTextReader.#ctor(System.IO.Stream)`
- `M:System.Xml.XmlTextReader.#ctor(System.IO.Stream,System.Xml.XmlNameTable)`
- `M:System.Xml.XmlTextReader.#ctor(System.IO.Stream,System.Xml.XmlNodeType,System.Xml.XmlParserContext)`
- `M:System.Xml.XmlTextReader.#ctor(System.IO.TextReader)`
- `M:System.Xml.XmlTextReader.#ctor(System.IO.TextReader,System.Xml.XmlNameTable)`
- `M:System.Xml.XmlTextReader.#ctor(System.String)`
- `M:System.Xml.XmlTextReader.#ctor(System.String,System.IO.Stream)`
- `M:System.Xml.XmlTextReader.#ctor(System.String,System.IO.Stream,System.Xml.XmlNameTable)`
- `M:System.Xml.XmlTextReader.#ctor(System.String,System.IO.TextReader)`
- `M:System.Xml.XmlTextReader.#ctor(System.String,System.IO.TextReader,System.Xml.XmlNameTable)`
- `M:System.Xml.XmlTextReader.#ctor(System.String,System.Xml.XmlNameTable)`
- `M:System.Xml.XmlTextReader.#ctor(System.String,System.Xml.XmlNodeType,System.Xml.XmlParserContext)`
- `M:System.Xml.XmlTextReader.#ctor(System.Xml.XmlNameTable)`

-->
