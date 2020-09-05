---
ms.openlocfilehash: d6405573e476ce18513938b500041adefbeeef1b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496901"
---
### <a name="ribbongroup-background-is-set-to-transparent-in-localized-builds"></a><span data-ttu-id="c2dce-101">RibbonGroup arka planı yerelleştirilmiş derlemelerde saydam olarak ayarlandı</span><span class="sxs-lookup"><span data-stu-id="c2dce-101">RibbonGroup background is set to transparent in localized builds</span></span>

#### <a name="details"></a><span data-ttu-id="c2dce-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="c2dce-102">Details</span></span>

<span data-ttu-id="c2dce-103"><xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName> yerelleştirilmiş derlemelerin arka planı her zaman saydam fırçayla boyanmıştır ve bu, kötü Kullanıcı arabirimi deneyimine yol açar.</span><span class="sxs-lookup"><span data-stu-id="c2dce-103"><xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName> background on localized builds was always painted with Transparent brush, resulting in poor UI experience.</span></span> <span data-ttu-id="c2dce-104">Bu, için yerelleştirilmiş kaynakları güncelleştirerek .NET Framework 4,7 WPF düzeltmesinde düzeltilir, bu da <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName> doğru fırçanın seçili olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c2dce-104">This is fixed in .NET Framework 4.7 WPF fix by updating the localized resources for <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName>, which in turn ensures that the correct brush is selected.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c2dce-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="c2dce-105">Suggestion</span></span>

<span data-ttu-id="c2dce-106">.NET Framework 4,7 ' ye yükseltin</span><span class="sxs-lookup"><span data-stu-id="c2dce-106">Upgrade to .NET Framework 4.7</span></span>

| <span data-ttu-id="c2dce-107">Name</span><span class="sxs-lookup"><span data-stu-id="c2dce-107">Name</span></span>    | <span data-ttu-id="c2dce-108">Değer</span><span class="sxs-lookup"><span data-stu-id="c2dce-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c2dce-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="c2dce-109">Scope</span></span>   |<span data-ttu-id="c2dce-110">Edge</span><span class="sxs-lookup"><span data-stu-id="c2dce-110">Edge</span></span>|
|<span data-ttu-id="c2dce-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="c2dce-111">Version</span></span>|<span data-ttu-id="c2dce-112">4.6.2</span><span class="sxs-lookup"><span data-stu-id="c2dce-112">4.6.2</span></span>|
|<span data-ttu-id="c2dce-113">Tür</span><span class="sxs-lookup"><span data-stu-id="c2dce-113">Type</span></span>|<span data-ttu-id="c2dce-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="c2dce-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="c2dce-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="c2dce-115">Affected APIs</span></span>

<span data-ttu-id="c2dce-116">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="c2dce-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
