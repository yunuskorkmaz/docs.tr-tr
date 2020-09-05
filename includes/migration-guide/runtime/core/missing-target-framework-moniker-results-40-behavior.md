---
ms.openlocfilehash: 49740d3b1890d72935e6e329a4f4be836ed70b25
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497241"
---
### <a name="missing-target-framework-moniker-results-in-40-behavior"></a><span data-ttu-id="0fd58-101">4,0 davranışında hedef Framework bilinen ad sonuçları eksik</span><span class="sxs-lookup"><span data-stu-id="0fd58-101">Missing Target Framework Moniker results in 4.0 behavior</span></span>

#### <a name="details"></a><span data-ttu-id="0fd58-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="0fd58-102">Details</span></span>

<span data-ttu-id="0fd58-103"><xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName>Derleme düzeyinde uygulanmamış uygulamalar, .NET Framework 4,0 ' nin semantiği (olağandışı KS) kullanılarak otomatik olarak çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="0fd58-103">Applications without a <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> applied at the assembly level will automatically run using the semantics (quirks) of the .NET Framework 4.0.</span></span> <span data-ttu-id="0fd58-104">Yüksek kaliteli olduğundan emin olmak için tüm ikili dosyaların, <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> derlendikleri .NET Framework sürümünü belirten bir ile açıkça ilişkilendirilmesi önerilir.</span><span class="sxs-lookup"><span data-stu-id="0fd58-104">To ensure high quality, it is recommended that all binaries be explicitly attributed with a <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> indicating the version of the .NET Framework they were built with.</span></span> <span data-ttu-id="0fd58-105">Bir proje dosyasında hedef çerçeve bilinen adının kullanılması, MSBuild 'in otomatik olarak uygulanmasına neden olacağını unutmayın <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="0fd58-105">Note that using a target framework moniker in a project file will cause MSBuild to automatically apply a <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="0fd58-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="0fd58-106">Suggestion</span></span>

<span data-ttu-id="0fd58-107"><xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName>Özniteliği doğrudan derlemeye ekleme yoluyla veya [Proje dosyasında ya da Visual Studio 'nun proje özellikleri GUI 'si aracılığıyla](https://devblogs.microsoft.com/visualstudio/visual-studio-managed-multi-targeting-part-1-concepts-target-framework-moniker-target-framework/)bir hedef çerçeve belirtilerek sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0fd58-107">A <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> should be supplied, either through adding the attribute directly to the assembly or by specifying a target framework in the [project file or through Visual Studio's project properties GUI](https://devblogs.microsoft.com/visualstudio/visual-studio-managed-multi-targeting-part-1-concepts-target-framework-moniker-target-framework/).</span></span>

| <span data-ttu-id="0fd58-108">Name</span><span class="sxs-lookup"><span data-stu-id="0fd58-108">Name</span></span>    | <span data-ttu-id="0fd58-109">Değer</span><span class="sxs-lookup"><span data-stu-id="0fd58-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="0fd58-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="0fd58-110">Scope</span></span>   |<span data-ttu-id="0fd58-111">Ana</span><span class="sxs-lookup"><span data-stu-id="0fd58-111">Major</span></span>|
|<span data-ttu-id="0fd58-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="0fd58-112">Version</span></span>|<span data-ttu-id="0fd58-113">4,5</span><span class="sxs-lookup"><span data-stu-id="0fd58-113">4.5</span></span>|
|<span data-ttu-id="0fd58-114">Tür</span><span class="sxs-lookup"><span data-stu-id="0fd58-114">Type</span></span>|<span data-ttu-id="0fd58-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="0fd58-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="0fd58-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="0fd58-116">Affected APIs</span></span>

<span data-ttu-id="0fd58-117">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="0fd58-117">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
