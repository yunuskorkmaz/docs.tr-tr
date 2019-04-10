---
ms.openlocfilehash: 4cc91e7c6054fdb8e96cecf7120df5b9f25de56c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235851"
---
### <a name="mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a><span data-ttu-id="7527f-101">MEF katalogları IEnumerable uygulamak ve bu nedenle bundan böyle bir seri hale getirici oluşturmak için kullanılabilir</span><span class="sxs-lookup"><span data-stu-id="7527f-101">MEF catalogs implement IEnumerable and therefore can no longer be used to create a serializer</span></span>

|   |   |
|---|---|
|<span data-ttu-id="7527f-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="7527f-102">Details</span></span>|<span data-ttu-id="7527f-103">.NET Framework 4.5 ile başlayarak, MEF katalogları IEnumerable uygulamak ve bu nedenle bundan böyle bir seri hale getirici oluşturmak için kullanılabilir (<xref:System.Xml.Serialization.XmlSerializer?displayProperty=name> nesne).</span><span class="sxs-lookup"><span data-stu-id="7527f-103">Starting with the .NET Framework 4.5, MEF catalogs implement IEnumerable and therefore can no longer be used to create a serializer (<xref:System.Xml.Serialization.XmlSerializer?displayProperty=name> object).</span></span> <span data-ttu-id="7527f-104">MEF kataloğu seri hale getirilmeye çalışıldığında bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="7527f-104">Trying to serialize a MEF catalog throws an exception.</span></span>|
|<span data-ttu-id="7527f-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="7527f-105">Suggestion</span></span>|<span data-ttu-id="7527f-106">Artık bir seri hale getirici oluşturmak için MEF kullanabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="7527f-106">Can no longer use MEF to create a serializer</span></span>|
|<span data-ttu-id="7527f-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="7527f-107">Scope</span></span>|<span data-ttu-id="7527f-108">Ana</span><span class="sxs-lookup"><span data-stu-id="7527f-108">Major</span></span>|
|<span data-ttu-id="7527f-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="7527f-109">Version</span></span>|<span data-ttu-id="7527f-110">4,5</span><span class="sxs-lookup"><span data-stu-id="7527f-110">4.5</span></span>|
|<span data-ttu-id="7527f-111">Tür</span><span class="sxs-lookup"><span data-stu-id="7527f-111">Type</span></span>|<span data-ttu-id="7527f-112">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="7527f-112">Runtime</span></span>|
