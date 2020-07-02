---
ms.openlocfilehash: 06c699281c8890ac65be1d282b72b54774acc280
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620711"
---
### <a name="wpf-datatemplate-elements-are-now-visible-to-uia"></a><span data-ttu-id="aba2f-101">WPF DataTemplate öğeleri artık UıA 'ye görünür</span><span class="sxs-lookup"><span data-stu-id="aba2f-101">WPF DataTemplate elements are now visible to UIA</span></span>

#### <a name="details"></a><span data-ttu-id="aba2f-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="aba2f-102">Details</span></span>

<span data-ttu-id="aba2f-103">Daha önce, <xref:System.Windows.DataTemplate?displayProperty=fullName> öğeler UI Otomasyonu için görünmezdi.</span><span class="sxs-lookup"><span data-stu-id="aba2f-103">Previously, <xref:System.Windows.DataTemplate?displayProperty=fullName> elements were invisible to UI Automation.</span></span> <span data-ttu-id="aba2f-104">4,5 ' den başlayarak UI Otomasyonu bu öğeleri algılar.</span><span class="sxs-lookup"><span data-stu-id="aba2f-104">Beginning in 4.5, UI Automation will detect these elements.</span></span> <span data-ttu-id="aba2f-105">Bu pek çok durumda kullanışlıdır, ancak öğeleri içermeyen UıA ağaçlarına bağlı testleri kesebilir <xref:System.Windows.DataTemplate?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="aba2f-105">This is useful in many cases, but can break tests that depend on UIA trees not containing <xref:System.Windows.DataTemplate?displayProperty=fullName> elements.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="aba2f-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="aba2f-106">Suggestion</span></span>

<span data-ttu-id="aba2f-107">Bu uygulama için UI Otomasyon testlerinin, artık daha önce görünmeyen öğeler de dahil olmak üzere UIA ağacı için hesabınıza güncelleştirilmeleri gerekebilir <xref:System.Windows.DataTemplate?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="aba2f-107">UI Automation tests for this app may need updated to account for the UIA tree now including previously invisible <xref:System.Windows.DataTemplate?displayProperty=fullName> elements.</span></span> <span data-ttu-id="aba2f-108">Örneğin, bazı öğelerin yanında olması beklenen testlerin, artık arasında daha önce görünmeyen UıA öğelerini beklemesi gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="aba2f-108">For example, tests that expect some elements to be next to each other may now need to expect previously invisible UIA elements in between.</span></span> <span data-ttu-id="aba2f-109">Veya UıA öğelerine yönelik belirli sayımlar veya dizinlere dayanan testler yeni değerlerle güncelleştirilmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="aba2f-109">Or tests that rely on certain counts or indexes for UIA elements may need updated with new values.</span></span>

| <span data-ttu-id="aba2f-110">Name</span><span class="sxs-lookup"><span data-stu-id="aba2f-110">Name</span></span>    | <span data-ttu-id="aba2f-111">Değer</span><span class="sxs-lookup"><span data-stu-id="aba2f-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="aba2f-112">Kapsam</span><span class="sxs-lookup"><span data-stu-id="aba2f-112">Scope</span></span>   |<span data-ttu-id="aba2f-113">Edge</span><span class="sxs-lookup"><span data-stu-id="aba2f-113">Edge</span></span>|
|<span data-ttu-id="aba2f-114">Sürüm</span><span class="sxs-lookup"><span data-stu-id="aba2f-114">Version</span></span>|<span data-ttu-id="aba2f-115">4,5</span><span class="sxs-lookup"><span data-stu-id="aba2f-115">4.5</span></span>|
|<span data-ttu-id="aba2f-116">Tür</span><span class="sxs-lookup"><span data-stu-id="aba2f-116">Type</span></span>|<span data-ttu-id="aba2f-117">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="aba2f-117">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="aba2f-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="aba2f-118">Affected APIs</span></span>

-<xref:System.Windows.DataTemplate.%23ctor></li><li><xref:System.Windows.DataTemplate.%23ctor(System.Object)></li></ul>|
