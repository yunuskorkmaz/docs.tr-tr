---
ms.openlocfilehash: 4cc91e7c6054fdb8e96cecf7120df5b9f25de56c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59805331"
---
### <a name="mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a><span data-ttu-id="c7731-101">MEF katalogları IEnumerable uygulamak ve bu nedenle bundan böyle bir seri hale getirici oluşturmak için kullanılabilir</span><span class="sxs-lookup"><span data-stu-id="c7731-101">MEF catalogs implement IEnumerable and therefore can no longer be used to create a serializer</span></span>

|   |   |
|---|---|
|<span data-ttu-id="c7731-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="c7731-102">Details</span></span>|<span data-ttu-id="c7731-103">.NET Framework 4.5 ile başlayarak, MEF katalogları IEnumerable uygulamak ve bu nedenle bundan böyle bir seri hale getirici oluşturmak için kullanılabilir (<xref:System.Xml.Serialization.XmlSerializer?displayProperty=name> nesne).</span><span class="sxs-lookup"><span data-stu-id="c7731-103">Starting with the .NET Framework 4.5, MEF catalogs implement IEnumerable and therefore can no longer be used to create a serializer (<xref:System.Xml.Serialization.XmlSerializer?displayProperty=name> object).</span></span> <span data-ttu-id="c7731-104">MEF kataloğu seri hale getirilmeye çalışıldığında bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="c7731-104">Trying to serialize a MEF catalog throws an exception.</span></span>|
|<span data-ttu-id="c7731-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="c7731-105">Suggestion</span></span>|<span data-ttu-id="c7731-106">Artık bir seri hale getirici oluşturmak için MEF kullanabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="c7731-106">Can no longer use MEF to create a serializer</span></span>|
|<span data-ttu-id="c7731-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="c7731-107">Scope</span></span>|<span data-ttu-id="c7731-108">Ana</span><span class="sxs-lookup"><span data-stu-id="c7731-108">Major</span></span>|
|<span data-ttu-id="c7731-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="c7731-109">Version</span></span>|<span data-ttu-id="c7731-110">4,5</span><span class="sxs-lookup"><span data-stu-id="c7731-110">4.5</span></span>|
|<span data-ttu-id="c7731-111">Tür</span><span class="sxs-lookup"><span data-stu-id="c7731-111">Type</span></span>|<span data-ttu-id="c7731-112">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="c7731-112">Runtime</span></span>|
