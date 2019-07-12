---
ms.openlocfilehash: 0778285ef1b5702bd79743038a1bd21ba04612d6
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804373"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a><span data-ttu-id="7063f-101">Dokunmatik özellikli sistemlerde System.Windows.Input.PenContext.Disable çağrıları ArgumentException atabilir.</span><span class="sxs-lookup"><span data-stu-id="7063f-101">Calls to System.Windows.Input.PenContext.Disable on touch-enabled systems may throw an ArgumentException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="7063f-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="7063f-102">Details</span></span>|<span data-ttu-id="7063f-103">Bazı durumlarda, iç ağa çağırır <strong>System.Windows.Intput.PenContext.Disable</strong> Dokunmatik özellikli sistemlerinde yöntemi işlenmeyen bir throw <code>T:System.ArgumentException</code> yeniden giriş nedeniyle.</span><span class="sxs-lookup"><span data-stu-id="7063f-103">Under some circumstances, calls to the internal <strong>System.Windows.Intput.PenContext.Disable</strong> method on touch-enabled systems may throw an unhandled <code>T:System.ArgumentException</code> because of reentrancy.</span></span>|
|<span data-ttu-id="7063f-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="7063f-104">Suggestion</span></span>|<span data-ttu-id="7063f-105">.NET Framework 4.7 bu sorun giderilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7063f-105">This issue has been addressed in the .NET Framework 4.7.</span></span> <span data-ttu-id="7063f-106">Özel durum önlemek için .NET Framework 4.7 ile başlayan .NET Framework'ün bir sürüme yükseltin.</span><span class="sxs-lookup"><span data-stu-id="7063f-106">To prevent the exception, upgrade to a version of the .NET Framework starting with the .NET Framework 4.7.</span></span>|
|<span data-ttu-id="7063f-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="7063f-107">Scope</span></span>|<span data-ttu-id="7063f-108">Kenar</span><span class="sxs-lookup"><span data-stu-id="7063f-108">Edge</span></span>|
|<span data-ttu-id="7063f-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="7063f-109">Version</span></span>|<span data-ttu-id="7063f-110">4.6.1</span><span class="sxs-lookup"><span data-stu-id="7063f-110">4.6.1</span></span>|
|<span data-ttu-id="7063f-111">Tür</span><span class="sxs-lookup"><span data-stu-id="7063f-111">Type</span></span>|<span data-ttu-id="7063f-112">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="7063f-112">Retargeting</span></span>|

