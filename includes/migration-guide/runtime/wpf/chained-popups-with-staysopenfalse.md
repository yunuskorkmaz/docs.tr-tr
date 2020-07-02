---
ms.openlocfilehash: 171b7a3a962f8259e64b88f1ae893e649b5f24bb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621396"
---
### <a name="chained-popups-with-staysopenfalse"></a><span data-ttu-id="61688-101">StaysOpen ile zincirleme açılan pencere = yanlış</span><span class="sxs-lookup"><span data-stu-id="61688-101">Chained Popups with StaysOpen=False</span></span>

#### <a name="details"></a><span data-ttu-id="61688-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="61688-102">Details</span></span>

<span data-ttu-id="61688-103">Açılan pencerenin dışına tıkladığınızda StaysOpen = false içeren bir açılan pencere kapatılacak.</span><span class="sxs-lookup"><span data-stu-id="61688-103">A Popup with StaysOpen=False is supposed to close when you click outside the Popup.</span></span> <span data-ttu-id="61688-104">İki veya daha fazla açılan pencere zincirleme olduğunda (yani bir diğeri içeriyorsa), aşağıdakiler dahil olmak üzere çok sayıda sorun oluştu:</span><span class="sxs-lookup"><span data-stu-id="61688-104">When two or more such Popups are chained (i.e. one contains another), there were many problems, including:</span></span><ul><li><span data-ttu-id="61688-105">İki düzey açın, P2 dışını, ancak P1 içinde tıklayın.</span><span class="sxs-lookup"><span data-stu-id="61688-105">Open two levels, click outside P2 but inside P1.</span></span>  <span data-ttu-id="61688-106">Hiçbir şey olmaz.</span><span class="sxs-lookup"><span data-stu-id="61688-106">Nothing happens.</span></span></li><li><span data-ttu-id="61688-107">İki düzey açın, P1 dış P1 öğesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="61688-107">Open two levels, click outside P1.</span></span>  <span data-ttu-id="61688-108">Her iki açılır pencere da kapanır.</span><span class="sxs-lookup"><span data-stu-id="61688-108">Both popups close.</span></span></li><li><span data-ttu-id="61688-109">İki düzeyi açın ve kapatın.</span><span class="sxs-lookup"><span data-stu-id="61688-109">Open and close two levels.</span></span>  <span data-ttu-id="61688-110">Sonra P2 açmayı yeniden deneyin.</span><span class="sxs-lookup"><span data-stu-id="61688-110">Then try to open P2 again.</span></span>  <span data-ttu-id="61688-111">Hiçbir şey olmaz.</span><span class="sxs-lookup"><span data-stu-id="61688-111">Nothing happens.</span></span></li><li><span data-ttu-id="61688-112">Üç düzey açmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="61688-112">Try to open three levels.</span></span>  <span data-ttu-id="61688-113">Yapamazsınız.</span><span class="sxs-lookup"><span data-stu-id="61688-113">You can't.</span></span>  <span data-ttu-id="61688-114">(Hiçbir şey olmaz ya da ilk iki düzey, tıkladığınıza bağlı olarak kapanır.) Bu durumlar (ve diğer çeşitler) artık beklenen şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="61688-114">(Either nothing happens or the first two levels close, depending on where you click.) These cases (and other variants) now work as expected.</span></span></li></ul>

| <span data-ttu-id="61688-115">Name</span><span class="sxs-lookup"><span data-stu-id="61688-115">Name</span></span>    | <span data-ttu-id="61688-116">Değer</span><span class="sxs-lookup"><span data-stu-id="61688-116">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="61688-117">Kapsam</span><span class="sxs-lookup"><span data-stu-id="61688-117">Scope</span></span>   |<span data-ttu-id="61688-118">Edge</span><span class="sxs-lookup"><span data-stu-id="61688-118">Edge</span></span>|
|<span data-ttu-id="61688-119">Sürüm</span><span class="sxs-lookup"><span data-stu-id="61688-119">Version</span></span>|<span data-ttu-id="61688-120">4.7.1</span><span class="sxs-lookup"><span data-stu-id="61688-120">4.7.1</span></span>|
|<span data-ttu-id="61688-121">Tür</span><span class="sxs-lookup"><span data-stu-id="61688-121">Type</span></span>|<span data-ttu-id="61688-122">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="61688-122">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="61688-123">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="61688-123">Affected APIs</span></span>

-<xref:System.Windows.Controls.Primitives.Popup.StaysOpen?displayProperty=nameWithType></li></ul>|
