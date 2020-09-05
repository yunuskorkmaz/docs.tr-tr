---
ms.openlocfilehash: 4394e69dafeb6cce2d7719a67bbce396d3bc1086
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497409"
---
### <a name="wpf-datatemplate-elements-are-now-visible-to-uia"></a><span data-ttu-id="3a5e6-101">WPF DataTemplate öğeleri artık UıA 'ye görünür</span><span class="sxs-lookup"><span data-stu-id="3a5e6-101">WPF DataTemplate elements are now visible to UIA</span></span>

#### <a name="details"></a><span data-ttu-id="3a5e6-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="3a5e6-102">Details</span></span>

<span data-ttu-id="3a5e6-103">Daha önce, <xref:System.Windows.DataTemplate?displayProperty=fullName> öğeler UI Otomasyonu için görünmezdi.</span><span class="sxs-lookup"><span data-stu-id="3a5e6-103">Previously, <xref:System.Windows.DataTemplate?displayProperty=fullName> elements were invisible to UI Automation.</span></span> <span data-ttu-id="3a5e6-104">4,5 ' den başlayarak UI Otomasyonu bu öğeleri algılar.</span><span class="sxs-lookup"><span data-stu-id="3a5e6-104">Beginning in 4.5, UI Automation will detect these elements.</span></span> <span data-ttu-id="3a5e6-105">Bu pek çok durumda kullanışlıdır, ancak öğeleri içermeyen UıA ağaçlarına bağlı testleri kesebilir <xref:System.Windows.DataTemplate?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="3a5e6-105">This is useful in many cases, but can break tests that depend on UIA trees not containing <xref:System.Windows.DataTemplate?displayProperty=fullName> elements.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3a5e6-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="3a5e6-106">Suggestion</span></span>

<span data-ttu-id="3a5e6-107">Bu uygulama için UI Otomasyon testlerinin, artık daha önce görünmeyen öğeler de dahil olmak üzere UIA ağacı için hesabınıza güncelleştirilmeleri gerekebilir <xref:System.Windows.DataTemplate?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="3a5e6-107">UI Automation tests for this app may need updated to account for the UIA tree now including previously invisible <xref:System.Windows.DataTemplate?displayProperty=fullName> elements.</span></span> <span data-ttu-id="3a5e6-108">Örneğin, bazı öğelerin yanında olması beklenen testlerin, artık arasında daha önce görünmeyen UıA öğelerini beklemesi gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="3a5e6-108">For example, tests that expect some elements to be next to each other may now need to expect previously invisible UIA elements in between.</span></span> <span data-ttu-id="3a5e6-109">Veya UıA öğelerine yönelik belirli sayımlar veya dizinlere dayanan testler yeni değerlerle güncelleştirilmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="3a5e6-109">Or tests that rely on certain counts or indexes for UIA elements may need updated with new values.</span></span>

| <span data-ttu-id="3a5e6-110">Name</span><span class="sxs-lookup"><span data-stu-id="3a5e6-110">Name</span></span>    | <span data-ttu-id="3a5e6-111">Değer</span><span class="sxs-lookup"><span data-stu-id="3a5e6-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3a5e6-112">Kapsam</span><span class="sxs-lookup"><span data-stu-id="3a5e6-112">Scope</span></span>   |<span data-ttu-id="3a5e6-113">Edge</span><span class="sxs-lookup"><span data-stu-id="3a5e6-113">Edge</span></span>|
|<span data-ttu-id="3a5e6-114">Sürüm</span><span class="sxs-lookup"><span data-stu-id="3a5e6-114">Version</span></span>|<span data-ttu-id="3a5e6-115">4,5</span><span class="sxs-lookup"><span data-stu-id="3a5e6-115">4.5</span></span>|
|<span data-ttu-id="3a5e6-116">Tür</span><span class="sxs-lookup"><span data-stu-id="3a5e6-116">Type</span></span>|<span data-ttu-id="3a5e6-117">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="3a5e6-117">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="3a5e6-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="3a5e6-118">Affected APIs</span></span>

- <xref:System.Windows.DataTemplate.%23ctor>
- <xref:System.Windows.DataTemplate.%23ctor(System.Object)>

<!--

#### Affected APIs

- `M:System.Windows.DataTemplate.#ctor`
- `M:System.Windows.DataTemplate.#ctor(System.Object)`

-->
