---
ms.openlocfilehash: 598df2121b480d411dac9c5571772a4a8d22b5ff
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620634"
---
### <a name="mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a><span data-ttu-id="8a116-101">MEF katalogları IEnumerable arabirimini uygular ve bu nedenle artık seri hale getirici oluşturmak için kullanılamaz</span><span class="sxs-lookup"><span data-stu-id="8a116-101">MEF catalogs implement IEnumerable and therefore can no longer be used to create a serializer</span></span>

#### <a name="details"></a><span data-ttu-id="8a116-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="8a116-102">Details</span></span>

<span data-ttu-id="8a116-103">.NET Framework 4,5 ' den başlayarak MEF katalogları IEnumerable 'ı uygular ve bu nedenle artık seri hale getirici (nesne) oluşturmak için kullanılamaz <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="8a116-103">Starting with the .NET Framework 4.5, MEF catalogs implement IEnumerable and therefore can no longer be used to create a serializer (<xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> object).</span></span> <span data-ttu-id="8a116-104">MEF kataloğu seri hale getirilmeye çalışıldığında bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="8a116-104">Trying to serialize a MEF catalog throws an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8a116-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="8a116-105">Suggestion</span></span>

<span data-ttu-id="8a116-106">Bir serileştirici oluşturmak için artık MEF kullanılamıyor</span><span class="sxs-lookup"><span data-stu-id="8a116-106">Can no longer use MEF to create a serializer</span></span>

| <span data-ttu-id="8a116-107">Name</span><span class="sxs-lookup"><span data-stu-id="8a116-107">Name</span></span>    | <span data-ttu-id="8a116-108">Değer</span><span class="sxs-lookup"><span data-stu-id="8a116-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8a116-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="8a116-109">Scope</span></span>   |<span data-ttu-id="8a116-110">Ana</span><span class="sxs-lookup"><span data-stu-id="8a116-110">Major</span></span>|
|<span data-ttu-id="8a116-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="8a116-111">Version</span></span>|<span data-ttu-id="8a116-112">4,5</span><span class="sxs-lookup"><span data-stu-id="8a116-112">4.5</span></span>|
|<span data-ttu-id="8a116-113">Tür</span><span class="sxs-lookup"><span data-stu-id="8a116-113">Type</span></span>|<span data-ttu-id="8a116-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="8a116-114">Runtime</span></span>|
