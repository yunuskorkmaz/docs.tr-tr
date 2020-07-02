---
ms.openlocfilehash: c3e39e49747be709977d7fba3c39b59f5575c40d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620724"
---
### <a name="xmlschemaexception-now-sets-line-positions-properly"></a><span data-ttu-id="9ecd8-101">XmlSchemaException artık satır konumlarını düzgün şekilde ayarlıyor</span><span class="sxs-lookup"><span data-stu-id="9ecd8-101">XmlSchemaException now sets line positions properly</span></span>

#### <a name="details"></a><span data-ttu-id="9ecd8-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="9ecd8-102">Details</span></span>

<span data-ttu-id="9ecd8-103"><xref:System.Xml.Linq.LoadOptions.SetLineInfo>Değer Load yöntemine geçirilirse ve bir doğrulama hatası oluşursa, <xref:System.Xml.Schema.XmlSchemaException.LineNumber> ve <xref:System.Xml.Schema.XmlSchemaException.LinePosition> özellikleri artık satır bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="9ecd8-103">If the <xref:System.Xml.Linq.LoadOptions.SetLineInfo> value is passed to the Load method and a validation error occurs, the <xref:System.Xml.Schema.XmlSchemaException.LineNumber> and <xref:System.Xml.Schema.XmlSchemaException.LinePosition> properties now contain line information.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="9ecd8-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="9ecd8-104">Suggestion</span></span>

<span data-ttu-id="9ecd8-105"><xref:System.Xml.Schema.XmlSchemaException.LineNumber> <xref:System.Xml.Schema.XmlSchemaException.LinePosition> XML yükleme sırasında SetLineInfo kullanıldığında, ayarlanmayacak ve ayarlanmayacak olan özel durum işleme kodu güncellenmelidir.</span><span class="sxs-lookup"><span data-stu-id="9ecd8-105">Exception-handling code that assumes <xref:System.Xml.Schema.XmlSchemaException.LineNumber> and <xref:System.Xml.Schema.XmlSchemaException.LinePosition> will not be set should be updated since these properties will now be set properly when SetLineInfo is used while loading XML.</span></span>

| <span data-ttu-id="9ecd8-106">Name</span><span class="sxs-lookup"><span data-stu-id="9ecd8-106">Name</span></span>    | <span data-ttu-id="9ecd8-107">Değer</span><span class="sxs-lookup"><span data-stu-id="9ecd8-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="9ecd8-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="9ecd8-108">Scope</span></span>   |<span data-ttu-id="9ecd8-109">Edge</span><span class="sxs-lookup"><span data-stu-id="9ecd8-109">Edge</span></span>|
|<span data-ttu-id="9ecd8-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="9ecd8-110">Version</span></span>|<span data-ttu-id="9ecd8-111">4,5</span><span class="sxs-lookup"><span data-stu-id="9ecd8-111">4.5</span></span>|
|<span data-ttu-id="9ecd8-112">Tür</span><span class="sxs-lookup"><span data-stu-id="9ecd8-112">Type</span></span>|<span data-ttu-id="9ecd8-113">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="9ecd8-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9ecd8-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="9ecd8-114">Affected APIs</span></span>

-<xref:System.Xml.Linq.LoadOptions.SetLineInfo?displayProperty=nameWithType></li></ul>|
