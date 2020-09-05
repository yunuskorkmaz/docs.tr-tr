---
ms.openlocfilehash: 04d1c1162dc79bbcb0578c6661466f4d58a57acc
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496937"
---
### <a name="xmlschemaexception-now-sets-line-positions-properly"></a><span data-ttu-id="d45b8-101">XmlSchemaException artık satır konumlarını düzgün şekilde ayarlıyor</span><span class="sxs-lookup"><span data-stu-id="d45b8-101">XmlSchemaException now sets line positions properly</span></span>

#### <a name="details"></a><span data-ttu-id="d45b8-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="d45b8-102">Details</span></span>

<span data-ttu-id="d45b8-103"><xref:System.Xml.Linq.LoadOptions.SetLineInfo>Değer Load yöntemine geçirilirse ve bir doğrulama hatası oluşursa, <xref:System.Xml.Schema.XmlSchemaException.LineNumber> ve <xref:System.Xml.Schema.XmlSchemaException.LinePosition> özellikleri artık satır bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="d45b8-103">If the <xref:System.Xml.Linq.LoadOptions.SetLineInfo> value is passed to the Load method and a validation error occurs, the <xref:System.Xml.Schema.XmlSchemaException.LineNumber> and <xref:System.Xml.Schema.XmlSchemaException.LinePosition> properties now contain line information.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="d45b8-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="d45b8-104">Suggestion</span></span>

<span data-ttu-id="d45b8-105"><xref:System.Xml.Schema.XmlSchemaException.LineNumber> <xref:System.Xml.Schema.XmlSchemaException.LinePosition> XML yükleme sırasında SetLineInfo kullanıldığında, ayarlanmayacak ve ayarlanmayacak olan özel durum işleme kodu güncellenmelidir.</span><span class="sxs-lookup"><span data-stu-id="d45b8-105">Exception-handling code that assumes <xref:System.Xml.Schema.XmlSchemaException.LineNumber> and <xref:System.Xml.Schema.XmlSchemaException.LinePosition> will not be set should be updated since these properties will now be set properly when SetLineInfo is used while loading XML.</span></span>

| <span data-ttu-id="d45b8-106">Name</span><span class="sxs-lookup"><span data-stu-id="d45b8-106">Name</span></span>    | <span data-ttu-id="d45b8-107">Değer</span><span class="sxs-lookup"><span data-stu-id="d45b8-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d45b8-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="d45b8-108">Scope</span></span>   |<span data-ttu-id="d45b8-109">Edge</span><span class="sxs-lookup"><span data-stu-id="d45b8-109">Edge</span></span>|
|<span data-ttu-id="d45b8-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="d45b8-110">Version</span></span>|<span data-ttu-id="d45b8-111">4,5</span><span class="sxs-lookup"><span data-stu-id="d45b8-111">4.5</span></span>|
|<span data-ttu-id="d45b8-112">Tür</span><span class="sxs-lookup"><span data-stu-id="d45b8-112">Type</span></span>|<span data-ttu-id="d45b8-113">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="d45b8-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="d45b8-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="d45b8-114">Affected APIs</span></span>

- <xref:System.Xml.Linq.LoadOptions.SetLineInfo?displayProperty=nameWithType>

<!--

#### Affected APIs

- `F:System.Xml.Linq.LoadOptions.SetLineInfo`

-->
