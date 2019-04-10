---
ms.openlocfilehash: 84f570cbbd97be79426e117d4c97ec182a397fd4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235839"
---
### <a name="ipad-should-not-be-used-in-custom-capabilities-file-because-it-is-now-a-browser-capability"></a><span data-ttu-id="e6074-101">Artık bir tarayıcı özelliği olduğundan IPad özel özellikleri dosyasında kullanılmamalıdır</span><span class="sxs-lookup"><span data-stu-id="e6074-101">IPad should not be used in custom capabilities file because it is now a browser capability</span></span>

|   |   |
|---|---|
|<span data-ttu-id="e6074-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="e6074-102">Details</span></span>|<span data-ttu-id="e6074-103">Özel özellikleri dosyasında kullanılmamalıdır .NET Framework 4. 5 ' başlayarak, iPad varsayılan ASP.NET tarayıcı yetenekleri dosyası bir tanımlayıcıda olduğundan</span><span class="sxs-lookup"><span data-stu-id="e6074-103">Beginning in .NET Framework 4.5, iPad is an identifier in the default ASP.NET browser capabilities file, so it should not be used in a custom capabilities file</span></span>|
|<span data-ttu-id="e6074-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="e6074-104">Suggestion</span></span>|<span data-ttu-id="e6074-105">İPad özgü özellikleri gerekirse, üzerinde önceden tanımlı bir ağ geçidi refID özellikleri ayarlayarak iPad davranışını değiştirmek gerekli &quot;IPad&quot; yerine yeni bir oluşturarak &quot;IPad&quot; Kimliğine göre kullanıcı aracısı eşleşen.</span><span class="sxs-lookup"><span data-stu-id="e6074-105">If iPad-specific capabilities are required, it is necessary to modify iPad behavior by setting capabilities on the pre-defined gateway refID &quot;IPad&quot; instead of by generating a new &quot;IPad&quot; ID by user agent matching.</span></span>|
|<span data-ttu-id="e6074-106">Kapsam</span><span class="sxs-lookup"><span data-stu-id="e6074-106">Scope</span></span>|<span data-ttu-id="e6074-107">Kenar</span><span class="sxs-lookup"><span data-stu-id="e6074-107">Edge</span></span>|
|<span data-ttu-id="e6074-108">Sürüm</span><span class="sxs-lookup"><span data-stu-id="e6074-108">Version</span></span>|<span data-ttu-id="e6074-109">4,5</span><span class="sxs-lookup"><span data-stu-id="e6074-109">4.5</span></span>|
|<span data-ttu-id="e6074-110">Tür</span><span class="sxs-lookup"><span data-stu-id="e6074-110">Type</span></span>|<span data-ttu-id="e6074-111">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="e6074-111">Runtime</span></span>|
