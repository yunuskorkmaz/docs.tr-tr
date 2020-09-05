---
ms.openlocfilehash: 6f22d6211ec9238fd1c7786643ca95db02bfca64
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497127"
---
### <a name="mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a><span data-ttu-id="f6e22-101">MEF katalogları IEnumerable arabirimini uygular ve bu nedenle artık seri hale getirici oluşturmak için kullanılamaz</span><span class="sxs-lookup"><span data-stu-id="f6e22-101">MEF catalogs implement IEnumerable and therefore can no longer be used to create a serializer</span></span>

#### <a name="details"></a><span data-ttu-id="f6e22-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="f6e22-102">Details</span></span>

<span data-ttu-id="f6e22-103">.NET Framework 4,5 ' den başlayarak MEF katalogları IEnumerable 'ı uygular ve bu nedenle artık seri hale getirici (nesne) oluşturmak için kullanılamaz <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="f6e22-103">Starting with the .NET Framework 4.5, MEF catalogs implement IEnumerable and therefore can no longer be used to create a serializer (<xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> object).</span></span> <span data-ttu-id="f6e22-104">MEF kataloğu seri hale getirilmeye çalışıldığında bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="f6e22-104">Trying to serialize a MEF catalog throws an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f6e22-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="f6e22-105">Suggestion</span></span>

<span data-ttu-id="f6e22-106">Bir serileştirici oluşturmak için artık MEF kullanılamıyor</span><span class="sxs-lookup"><span data-stu-id="f6e22-106">Can no longer use MEF to create a serializer</span></span>

| <span data-ttu-id="f6e22-107">Name</span><span class="sxs-lookup"><span data-stu-id="f6e22-107">Name</span></span>    | <span data-ttu-id="f6e22-108">Değer</span><span class="sxs-lookup"><span data-stu-id="f6e22-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f6e22-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="f6e22-109">Scope</span></span>   |<span data-ttu-id="f6e22-110">Ana</span><span class="sxs-lookup"><span data-stu-id="f6e22-110">Major</span></span>|
|<span data-ttu-id="f6e22-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="f6e22-111">Version</span></span>|<span data-ttu-id="f6e22-112">4,5</span><span class="sxs-lookup"><span data-stu-id="f6e22-112">4.5</span></span>|
|<span data-ttu-id="f6e22-113">Tür</span><span class="sxs-lookup"><span data-stu-id="f6e22-113">Type</span></span>|<span data-ttu-id="f6e22-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="f6e22-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="f6e22-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="f6e22-115">Affected APIs</span></span>

<span data-ttu-id="f6e22-116">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="f6e22-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
