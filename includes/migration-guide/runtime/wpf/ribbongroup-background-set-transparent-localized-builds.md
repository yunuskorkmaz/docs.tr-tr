---
ms.openlocfilehash: a3ba42868577ac20ea2e082f90fc4973a1bfe108
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622385"
---
### <a name="ribbongroup-background-is-set-to-transparent-in-localized-builds"></a><span data-ttu-id="94d4b-101">RibbonGroup arka planı yerelleştirilmiş derlemelerde saydam olarak ayarlandı</span><span class="sxs-lookup"><span data-stu-id="94d4b-101">RibbonGroup background is set to transparent in localized builds</span></span>

#### <a name="details"></a><span data-ttu-id="94d4b-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="94d4b-102">Details</span></span>

<span data-ttu-id="94d4b-103"><xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName>yerelleştirilmiş derlemelerin arka planı her zaman saydam fırçayla boyanmıştır ve bu, kötü Kullanıcı arabirimi deneyimine yol açar.</span><span class="sxs-lookup"><span data-stu-id="94d4b-103"><xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName> background on localized builds was always painted with Transparent brush, resulting in poor UI experience.</span></span> <span data-ttu-id="94d4b-104">Bu, için yerelleştirilmiş kaynakları güncelleştirerek .NET Framework 4,7 WPF düzeltmesinde düzeltilir, bu da <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName> doğru fırçanın seçili olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="94d4b-104">This is fixed in .NET Framework 4.7 WPF fix by updating the localized resources for <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName>, which in turn ensures that the correct brush is selected.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="94d4b-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="94d4b-105">Suggestion</span></span>

<span data-ttu-id="94d4b-106">.NET Framework 4,7 ' ye yükseltin</span><span class="sxs-lookup"><span data-stu-id="94d4b-106">Upgrade to .NET Framework 4.7</span></span>

| <span data-ttu-id="94d4b-107">Name</span><span class="sxs-lookup"><span data-stu-id="94d4b-107">Name</span></span>    | <span data-ttu-id="94d4b-108">Değer</span><span class="sxs-lookup"><span data-stu-id="94d4b-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="94d4b-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="94d4b-109">Scope</span></span>   |<span data-ttu-id="94d4b-110">Edge</span><span class="sxs-lookup"><span data-stu-id="94d4b-110">Edge</span></span>|
|<span data-ttu-id="94d4b-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="94d4b-111">Version</span></span>|<span data-ttu-id="94d4b-112">4.6.2</span><span class="sxs-lookup"><span data-stu-id="94d4b-112">4.6.2</span></span>|
|<span data-ttu-id="94d4b-113">Tür</span><span class="sxs-lookup"><span data-stu-id="94d4b-113">Type</span></span>|<span data-ttu-id="94d4b-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="94d4b-114">Runtime</span></span>|
