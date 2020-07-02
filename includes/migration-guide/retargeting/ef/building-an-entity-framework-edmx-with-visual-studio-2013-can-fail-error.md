---
ms.openlocfilehash: c5099f610569f7788bb829a2153006d20d8a4ea2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615758"
---
### <a name="building-an-entity-framework-edmx-with-visual-studio-2013-can-fail-with-error-msb4062-if-using-the-entitydeploysplit-or-entityclean-tasks"></a><span data-ttu-id="f7da5-101">Visual Studio 2013 ile bir Entity Framework edmx oluşturma işlemi, EntityDeploySplit veya EntityClean görevleri kullanılıyorsa MSB4062 hatasıyla başarısız olabilir</span><span class="sxs-lookup"><span data-stu-id="f7da5-101">Building an Entity Framework edmx with Visual Studio 2013 can fail with error MSB4062 if using the EntityDeploySplit or EntityClean tasks</span></span>

#### <a name="details"></a><span data-ttu-id="f7da5-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="f7da5-102">Details</span></span>

<span data-ttu-id="f7da5-103">MSBuild 12.0 araçlarındaki (Visual Studio 2013’e dahildir) MSBuild dosya konumları değiştirilmiş ve eski Entity Framework hedef dosyalarının geçersiz olmasına neden olmuştur.</span><span class="sxs-lookup"><span data-stu-id="f7da5-103">MSBuild 12.0 tools (included in Visual Studio 2013) changed MSBuild file locations, causing older Entity Framework targets files to be invalid.</span></span> <span data-ttu-id="f7da5-104">Sonuç olarak, `EntityDeploySplit` ve `EntityClean` görevleri `Microsoft.Data.Entity.Build.Tasks.dll` dosyasını bulamadıkları için başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="f7da5-104">The result is that `EntityDeploySplit` and `EntityClean` tasks fail because they are unable to find `Microsoft.Data.Entity.Build.Tasks.dll`.</span></span> <span data-ttu-id="f7da5-105">Bu kesintinin bir .NET Framework değişikliğinden değil bir araç takımı (MSBuild/VS) değişikliğinden kaynaklandığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="f7da5-105">Note that this break is because of a toolset (MSBuild/VS) change, not because of a .NET Framework change.</span></span> <span data-ttu-id="f7da5-106">.NET Framework’ü yükseltirken değil, yalnızca geliştirici araçlarını yükseltirken oluşur.</span><span class="sxs-lookup"><span data-stu-id="f7da5-106">It will only occur when upgrading developer tools, not when merely upgrading the .NET Framework.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f7da5-107">Öneri</span><span class="sxs-lookup"><span data-stu-id="f7da5-107">Suggestion</span></span>

<span data-ttu-id="f7da5-108">Entity Framework hedef dosyaları, .NET Framework 4.6 sürümünden başlayarak yeni MSBuild düzeniyle çalışmak için düzeltildi.</span><span class="sxs-lookup"><span data-stu-id="f7da5-108">Entity Framework targets files are fixed to work with the new MSBuild layout beginning in the .NET Framework 4.6.</span></span> <span data-ttu-id="f7da5-109">Bu Framework sürümüne yükseltmek bu sorunu çözecektir.</span><span class="sxs-lookup"><span data-stu-id="f7da5-109">Upgrading to that version of the Framework will fix this issue.</span></span> <span data-ttu-id="f7da5-110">Alternatif olarak, [Bu geçici çözüm](https://stackoverflow.com/a/24249247/131944) hedefler dosyalarını doğrudan düzeltme için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f7da5-110">Alternatively, [this workaround](https://stackoverflow.com/a/24249247/131944) can be used to patch the targets files directly.</span></span>

| <span data-ttu-id="f7da5-111">Name</span><span class="sxs-lookup"><span data-stu-id="f7da5-111">Name</span></span>    | <span data-ttu-id="f7da5-112">Değer</span><span class="sxs-lookup"><span data-stu-id="f7da5-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f7da5-113">Kapsam</span><span class="sxs-lookup"><span data-stu-id="f7da5-113">Scope</span></span>   | <span data-ttu-id="f7da5-114">Ana</span><span class="sxs-lookup"><span data-stu-id="f7da5-114">Major</span></span>       |
| <span data-ttu-id="f7da5-115">Sürüm</span><span class="sxs-lookup"><span data-stu-id="f7da5-115">Version</span></span> | <span data-ttu-id="f7da5-116">4.5.1</span><span class="sxs-lookup"><span data-stu-id="f7da5-116">4.5.1</span></span>       |
| <span data-ttu-id="f7da5-117">Tür</span><span class="sxs-lookup"><span data-stu-id="f7da5-117">Type</span></span>    | <span data-ttu-id="f7da5-118">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="f7da5-118">Retargeting</span></span> |
