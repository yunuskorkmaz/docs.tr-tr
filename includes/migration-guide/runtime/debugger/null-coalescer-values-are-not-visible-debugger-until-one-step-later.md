---
ms.openlocfilehash: 907c4aa5573c392a68afad0a4d937eadcd556440
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620609"
---
### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a><span data-ttu-id="ccb64-101">Null birleştirme değerleri, bir adım daha sonra bir adımla hata ayıklayıcıda görünmez</span><span class="sxs-lookup"><span data-stu-id="ccb64-101">Null coalescer values are not visible in debugger until one step later</span></span>

#### <a name="details"></a><span data-ttu-id="ccb64-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="ccb64-102">Details</span></span>

<span data-ttu-id="ccb64-103">.NET Framework 4,5 ' deki bir hata, çerçevenin 64 bit sürümünde çalışırken atama işlemi yürütüldükten hemen sonra, null birleştirme işlemi yoluyla ayarlanan değerlerin hata ayıklayıcıda görünür olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="ccb64-103">A bug in the .NET Framework 4.5 causes values set via a null coalescing operation to not be visible in the debugger immediately after the assignment operation is executed when running on the 64-bit version of the Framework.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ccb64-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="ccb64-104">Suggestion</span></span>

<span data-ttu-id="ccb64-105">Hata ayıklayıcıda ek bir zaman adımlamak, yerel/alanın değerinin doğru güncelleştirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="ccb64-105">Stepping one additional time in the debugger will cause the local/field's value to be correctly updated.</span></span> <span data-ttu-id="ccb64-106">Ayrıca, bu sorun 4,6 .NET Framework düzeltilmiştir; Framework 'ün bu sürümüne yükseltmek sorunu çözmelidir.</span><span class="sxs-lookup"><span data-stu-id="ccb64-106">Also, this issue has been fixed in the .NET Framework 4.6; upgrading to that version of the Framework should solve the issue.</span></span>

| <span data-ttu-id="ccb64-107">Name</span><span class="sxs-lookup"><span data-stu-id="ccb64-107">Name</span></span>    | <span data-ttu-id="ccb64-108">Değer</span><span class="sxs-lookup"><span data-stu-id="ccb64-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ccb64-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="ccb64-109">Scope</span></span>   |<span data-ttu-id="ccb64-110">Edge</span><span class="sxs-lookup"><span data-stu-id="ccb64-110">Edge</span></span>|
|<span data-ttu-id="ccb64-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="ccb64-111">Version</span></span>|<span data-ttu-id="ccb64-112">4,5</span><span class="sxs-lookup"><span data-stu-id="ccb64-112">4.5</span></span>|
|<span data-ttu-id="ccb64-113">Tür</span><span class="sxs-lookup"><span data-stu-id="ccb64-113">Type</span></span>|<span data-ttu-id="ccb64-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="ccb64-114">Runtime</span></span>|
