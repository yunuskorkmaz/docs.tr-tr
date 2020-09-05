---
ms.openlocfilehash: af8de731ee93d0bfb01042d894f5730570dcdd78
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496718"
---
### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a><span data-ttu-id="71b16-101">Null birleştirme değerleri, bir adım daha sonra bir adımla hata ayıklayıcıda görünmez</span><span class="sxs-lookup"><span data-stu-id="71b16-101">Null coalescer values are not visible in debugger until one step later</span></span>

#### <a name="details"></a><span data-ttu-id="71b16-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="71b16-102">Details</span></span>

<span data-ttu-id="71b16-103">.NET Framework 4,5 ' deki bir hata, çerçevenin 64 bit sürümünde çalışırken atama işlemi yürütüldükten hemen sonra, null birleştirme işlemi yoluyla ayarlanan değerlerin hata ayıklayıcıda görünür olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="71b16-103">A bug in the .NET Framework 4.5 causes values set via a null coalescing operation to not be visible in the debugger immediately after the assignment operation is executed when running on the 64-bit version of the Framework.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="71b16-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="71b16-104">Suggestion</span></span>

<span data-ttu-id="71b16-105">Hata ayıklayıcıda ek bir zaman adımlamak, yerel/alanın değerinin doğru güncelleştirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="71b16-105">Stepping one additional time in the debugger will cause the local/field's value to be correctly updated.</span></span> <span data-ttu-id="71b16-106">Ayrıca, bu sorun 4,6 .NET Framework düzeltilmiştir; Framework 'ün bu sürümüne yükseltmek sorunu çözmelidir.</span><span class="sxs-lookup"><span data-stu-id="71b16-106">Also, this issue has been fixed in the .NET Framework 4.6; upgrading to that version of the Framework should solve the issue.</span></span>

| <span data-ttu-id="71b16-107">Name</span><span class="sxs-lookup"><span data-stu-id="71b16-107">Name</span></span>    | <span data-ttu-id="71b16-108">Değer</span><span class="sxs-lookup"><span data-stu-id="71b16-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="71b16-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="71b16-109">Scope</span></span>   |<span data-ttu-id="71b16-110">Edge</span><span class="sxs-lookup"><span data-stu-id="71b16-110">Edge</span></span>|
|<span data-ttu-id="71b16-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="71b16-111">Version</span></span>|<span data-ttu-id="71b16-112">4,5</span><span class="sxs-lookup"><span data-stu-id="71b16-112">4.5</span></span>|
|<span data-ttu-id="71b16-113">Tür</span><span class="sxs-lookup"><span data-stu-id="71b16-113">Type</span></span>|<span data-ttu-id="71b16-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="71b16-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="71b16-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="71b16-115">Affected APIs</span></span>

<span data-ttu-id="71b16-116">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="71b16-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
