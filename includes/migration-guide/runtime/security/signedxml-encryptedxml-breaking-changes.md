---
ms.openlocfilehash: 5c8ea3565fbe599dd53a71ba8bd339704f7d7f8a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497076"
---
### <a name="signedxml-and-encryptedxml-breaking-changes"></a><span data-ttu-id="7c763-101">SignedXml ve EncryptedXml kırılmaya yönelik değişiklikler</span><span class="sxs-lookup"><span data-stu-id="7c763-101">SignedXml and EncryptedXml Breaking Changes</span></span>

#### <a name="details"></a><span data-ttu-id="7c763-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="7c763-102">Details</span></span>

<span data-ttu-id="7c763-103">.NET Framework 4.6.2 ' de güvenlik düzeltmeleri <xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=fullName> ve <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=fullName> farklı çalışma zamanı davranışlarına yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="7c763-103">In .NET Framework 4.6.2, Security fixes in <xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=fullName> and <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=fullName> lead to different run-time behaviors.</span></span> <span data-ttu-id="7c763-104">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="7c763-104">For example,</span></span><ul><li><span data-ttu-id="7c763-105">Bir belgede aynı özniteliğe sahip birden fazla öğe varsa <code>id</code> ve imza imza kökü olarak bu öğelerden birini hedefliyorsa, belge artık geçersiz olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="7c763-105">If a document has multiple elements with the same <code>id</code> attribute and a signature targets one of those elements as the root of the signature, the document will now be considered invalid.</span></span></li><li><span data-ttu-id="7c763-106">Başvurularda kurallı olmayan XPath dönüştürme algoritmaları kullanan belgeler artık geçersiz olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="7c763-106">Documents using non-canonical XPath transform algorithms in references are now considered invalid.</span></span></li><li><span data-ttu-id="7c763-107">Başvurularda kurallı olmayan XSLT dönüştürme algoritmaları kullanan belgeler artık geçersiz olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="7c763-107">Documents using non-canonical XSLT transform algorithms in references are now consider invalid.</span></span></li><li><span data-ttu-id="7c763-108">Dış kaynak bağlantısı kesilen imzaları kullanan tüm programlar bunu yapamayacak.</span><span class="sxs-lookup"><span data-stu-id="7c763-108">Any program making use of external resource detached signatures will be unable to do so.</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="7c763-109">Öneri</span><span class="sxs-lookup"><span data-stu-id="7c763-109">Suggestion</span></span>

<span data-ttu-id="7c763-110">Geliştiriciler <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform> , ve ' nin kullanımını ve <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform> <xref:System.Security.Cryptography.Xml.Transform> belge alıcısından bu yana türetilmiş türleri işleyemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="7c763-110">Developers might want to review the usage of <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform> and <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform>, as well as types derived from <xref:System.Security.Cryptography.Xml.Transform> since a document receiver may not be able to process it.</span></span>

| <span data-ttu-id="7c763-111">Name</span><span class="sxs-lookup"><span data-stu-id="7c763-111">Name</span></span>    | <span data-ttu-id="7c763-112">Değer</span><span class="sxs-lookup"><span data-stu-id="7c763-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7c763-113">Kapsam</span><span class="sxs-lookup"><span data-stu-id="7c763-113">Scope</span></span>   |<span data-ttu-id="7c763-114">İkincil</span><span class="sxs-lookup"><span data-stu-id="7c763-114">Minor</span></span>|
|<span data-ttu-id="7c763-115">Sürüm</span><span class="sxs-lookup"><span data-stu-id="7c763-115">Version</span></span>|<span data-ttu-id="7c763-116">4.6.2</span><span class="sxs-lookup"><span data-stu-id="7c763-116">4.6.2</span></span>|
|<span data-ttu-id="7c763-117">Tür</span><span class="sxs-lookup"><span data-stu-id="7c763-117">Type</span></span>|<span data-ttu-id="7c763-118">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="7c763-118">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="7c763-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="7c763-119">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Xml.Transform?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Xml.XmlDsigXPathTransform?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Security.Cryptography.Xml.Transform`
- `T:System.Security.Cryptography.Xml.XmlDsigXPathTransform`
- `T:System.Security.Cryptography.Xml.XmlDsigXsltTransform`

-->
