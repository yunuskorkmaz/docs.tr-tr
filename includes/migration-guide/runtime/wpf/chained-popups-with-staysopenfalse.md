---
ms.openlocfilehash: 7bf5f7e8a49acc2918dd0d68a1c54a5c277091b0
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497370"
---
### <a name="chained-popups-with-staysopenfalse"></a><span data-ttu-id="c5e5a-101">StaysOpen ile zincirleme açılan pencere = yanlış</span><span class="sxs-lookup"><span data-stu-id="c5e5a-101">Chained Popups with StaysOpen=False</span></span>

#### <a name="details"></a><span data-ttu-id="c5e5a-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="c5e5a-102">Details</span></span>

<span data-ttu-id="c5e5a-103">Açılan pencerenin dışına tıkladığınızda StaysOpen = false içeren bir açılan pencere kapatılacak.</span><span class="sxs-lookup"><span data-stu-id="c5e5a-103">A Popup with StaysOpen=False is supposed to close when you click outside the Popup.</span></span> <span data-ttu-id="c5e5a-104">İki veya daha fazla açılan pencere zincirleme olduğunda (yani bir diğeri içeriyorsa), aşağıdakiler dahil olmak üzere çok sayıda sorun oluştu:</span><span class="sxs-lookup"><span data-stu-id="c5e5a-104">When two or more such Popups are chained (i.e. one contains another), there were many problems, including:</span></span><ul><li><span data-ttu-id="c5e5a-105">İki düzey açın, P2 dışını, ancak P1 içinde tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c5e5a-105">Open two levels, click outside P2 but inside P1.</span></span>  <span data-ttu-id="c5e5a-106">Hiçbir şey olmaz.</span><span class="sxs-lookup"><span data-stu-id="c5e5a-106">Nothing happens.</span></span></li><li><span data-ttu-id="c5e5a-107">İki düzey açın, P1 dış P1 öğesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c5e5a-107">Open two levels, click outside P1.</span></span>  <span data-ttu-id="c5e5a-108">Her iki açılır pencere da kapanır.</span><span class="sxs-lookup"><span data-stu-id="c5e5a-108">Both popups close.</span></span></li><li><span data-ttu-id="c5e5a-109">İki düzeyi açın ve kapatın.</span><span class="sxs-lookup"><span data-stu-id="c5e5a-109">Open and close two levels.</span></span>  <span data-ttu-id="c5e5a-110">Sonra P2 açmayı yeniden deneyin.</span><span class="sxs-lookup"><span data-stu-id="c5e5a-110">Then try to open P2 again.</span></span>  <span data-ttu-id="c5e5a-111">Hiçbir şey olmaz.</span><span class="sxs-lookup"><span data-stu-id="c5e5a-111">Nothing happens.</span></span></li><li><span data-ttu-id="c5e5a-112">Üç düzey açmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="c5e5a-112">Try to open three levels.</span></span>  <span data-ttu-id="c5e5a-113">Yönetemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5e5a-113">You can't.</span></span>  <span data-ttu-id="c5e5a-114">(Hiçbir şey olmaz ya da ilk iki düzey, tıkladığınıza bağlı olarak kapanır.) Bu durumlar (ve diğer çeşitler) artık beklenen şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="c5e5a-114">(Either nothing happens or the first two levels close, depending on where you click.) These cases (and other variants) now work as expected.</span></span></li></ul>

| <span data-ttu-id="c5e5a-115">Name</span><span class="sxs-lookup"><span data-stu-id="c5e5a-115">Name</span></span>    | <span data-ttu-id="c5e5a-116">Değer</span><span class="sxs-lookup"><span data-stu-id="c5e5a-116">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c5e5a-117">Kapsam</span><span class="sxs-lookup"><span data-stu-id="c5e5a-117">Scope</span></span>   |<span data-ttu-id="c5e5a-118">Edge</span><span class="sxs-lookup"><span data-stu-id="c5e5a-118">Edge</span></span>|
|<span data-ttu-id="c5e5a-119">Sürüm</span><span class="sxs-lookup"><span data-stu-id="c5e5a-119">Version</span></span>|<span data-ttu-id="c5e5a-120">4.7.1</span><span class="sxs-lookup"><span data-stu-id="c5e5a-120">4.7.1</span></span>|
|<span data-ttu-id="c5e5a-121">Tür</span><span class="sxs-lookup"><span data-stu-id="c5e5a-121">Type</span></span>|<span data-ttu-id="c5e5a-122">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="c5e5a-122">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="c5e5a-123">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="c5e5a-123">Affected APIs</span></span>

- <xref:System.Windows.Controls.Primitives.Popup.StaysOpen?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Windows.Controls.Primitives.Popup.StaysOpen`

-->
