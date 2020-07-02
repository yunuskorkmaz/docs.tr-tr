---
ms.openlocfilehash: a44458484ea09c566defeabc9b604bd55d994e93
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617554"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a><span data-ttu-id="bab9d-101">Dokunmatik özellikli sistemlerde System. Windows. Input. PenContext. Disable için çağrılar bir ArgumentException oluşturabilir</span><span class="sxs-lookup"><span data-stu-id="bab9d-101">Calls to System.Windows.Input.PenContext.Disable on touch-enabled systems may throw an ArgumentException</span></span>

#### <a name="details"></a><span data-ttu-id="bab9d-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="bab9d-102">Details</span></span>

<span data-ttu-id="bab9d-103">Bazı durumlarda, dokunmatik özellikli sistemlerde iç **System. Windows. Int32. PenContext. Disable** yöntemine yapılan çağrılar, yeniden giriş nedeniyle işlenmemiş bir işlem oluşturabilir `T:System.ArgumentException` .</span><span class="sxs-lookup"><span data-stu-id="bab9d-103">Under some circumstances, calls to the internal **System.Windows.Intput.PenContext.Disable** method on touch-enabled systems may throw an unhandled `T:System.ArgumentException` because of reentrancy.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="bab9d-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="bab9d-104">Suggestion</span></span>

<span data-ttu-id="bab9d-105">Bu sorun 4,7 .NET Framework giderilmiştir.</span><span class="sxs-lookup"><span data-stu-id="bab9d-105">This issue has been addressed in the .NET Framework 4.7.</span></span> <span data-ttu-id="bab9d-106">Özel durumu engellemek için, .NET Framework .NET Framework 4,7 ' den başlayarak bir sürümüne yükseltin.</span><span class="sxs-lookup"><span data-stu-id="bab9d-106">To prevent the exception, upgrade to a version of the .NET Framework starting with the .NET Framework 4.7.</span></span>

| <span data-ttu-id="bab9d-107">Name</span><span class="sxs-lookup"><span data-stu-id="bab9d-107">Name</span></span>    | <span data-ttu-id="bab9d-108">Değer</span><span class="sxs-lookup"><span data-stu-id="bab9d-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="bab9d-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="bab9d-109">Scope</span></span>   | <span data-ttu-id="bab9d-110">Edge</span><span class="sxs-lookup"><span data-stu-id="bab9d-110">Edge</span></span>        |
| <span data-ttu-id="bab9d-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="bab9d-111">Version</span></span> | <span data-ttu-id="bab9d-112">4.6.1</span><span class="sxs-lookup"><span data-stu-id="bab9d-112">4.6.1</span></span>       |
| <span data-ttu-id="bab9d-113">Tür</span><span class="sxs-lookup"><span data-stu-id="bab9d-113">Type</span></span>    | <span data-ttu-id="bab9d-114">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="bab9d-114">Retargeting</span></span> |
