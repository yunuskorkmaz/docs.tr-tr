---
ms.openlocfilehash: 8cc4f2ba2923774ef4e4e6861a89a7797ca988e1
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621379"
---
### <a name="signedxml-and-encryptedxml-breaking-changes"></a><span data-ttu-id="fc75b-101">SignedXml ve EncryptedXml kırılmaya yönelik değişiklikler</span><span class="sxs-lookup"><span data-stu-id="fc75b-101">SignedXml and EncryptedXml Breaking Changes</span></span>

#### <a name="details"></a><span data-ttu-id="fc75b-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="fc75b-102">Details</span></span>

<span data-ttu-id="fc75b-103">.NET Framework 4.6.2 ' de güvenlik düzeltmeleri <xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=fullName> ve <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=fullName> farklı çalışma zamanı davranışlarına yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="fc75b-103">In .NET Framework 4.6.2, Security fixes in <xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=fullName> and <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=fullName> lead to different run-time behaviors.</span></span> <span data-ttu-id="fc75b-104">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="fc75b-104">For example,</span></span><ul><li><span data-ttu-id="fc75b-105">Bir belgede aynı özniteliğe sahip birden fazla öğe varsa <code>id</code> ve imza imza kökü olarak bu öğelerden birini hedefliyorsa, belge artık geçersiz olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="fc75b-105">If a document has multiple elements with the same <code>id</code> attribute and a signature targets one of those elements as the root of the signature, the document will now be considered invalid.</span></span></li><li><span data-ttu-id="fc75b-106">Başvurularda kurallı olmayan XPath dönüştürme algoritmaları kullanan belgeler artık geçersiz olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="fc75b-106">Documents using non-canonical XPath transform algorithms in references are now considered invalid.</span></span></li><li><span data-ttu-id="fc75b-107">Başvurularda kurallı olmayan XSLT dönüştürme algoritmaları kullanan belgeler artık geçersiz olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="fc75b-107">Documents using non-canonical XSLT transform algorithms in references are now consider invalid.</span></span></li><li><span data-ttu-id="fc75b-108">Dış kaynak bağlantısı kesilen imzaları kullanan tüm programlar bunu yapamayacak.</span><span class="sxs-lookup"><span data-stu-id="fc75b-108">Any program making use of external resource detached signatures will be unable to do so.</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="fc75b-109">Öneri</span><span class="sxs-lookup"><span data-stu-id="fc75b-109">Suggestion</span></span>

<span data-ttu-id="fc75b-110">Geliştiriciler <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform> , ve ' nin kullanımını ve <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform> <xref:System.Security.Cryptography.Xml.Transform> belge alıcısından bu yana türetilmiş türleri işleyemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="fc75b-110">Developers might want to review the usage of <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform> and <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform>, as well as types derived from <xref:System.Security.Cryptography.Xml.Transform> since a document receiver may not be able to process it.</span></span>

| <span data-ttu-id="fc75b-111">Name</span><span class="sxs-lookup"><span data-stu-id="fc75b-111">Name</span></span>    | <span data-ttu-id="fc75b-112">Değer</span><span class="sxs-lookup"><span data-stu-id="fc75b-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="fc75b-113">Kapsam</span><span class="sxs-lookup"><span data-stu-id="fc75b-113">Scope</span></span>   |<span data-ttu-id="fc75b-114">İkincil</span><span class="sxs-lookup"><span data-stu-id="fc75b-114">Minor</span></span>|
|<span data-ttu-id="fc75b-115">Sürüm</span><span class="sxs-lookup"><span data-stu-id="fc75b-115">Version</span></span>|<span data-ttu-id="fc75b-116">4.6.2</span><span class="sxs-lookup"><span data-stu-id="fc75b-116">4.6.2</span></span>|
|<span data-ttu-id="fc75b-117">Tür</span><span class="sxs-lookup"><span data-stu-id="fc75b-117">Type</span></span>|<span data-ttu-id="fc75b-118">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="fc75b-118">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="fc75b-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="fc75b-119">Affected APIs</span></span>

-<xref:System.Security.Cryptography.Xml.Transform?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.XmlDsigXPathTransform?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform?displayProperty=nameWithType></li></ul>|
