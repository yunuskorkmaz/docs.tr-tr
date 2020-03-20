---
ms.openlocfilehash: 6bb8c87af66e744514fb43e628c6423487342ac2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "72887852"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a><span data-ttu-id="0b2a7-101">System.Windows.Input.PenContext.Disable touch-enabled sistemlere aramalar bir ArgumentException atabilir</span><span class="sxs-lookup"><span data-stu-id="0b2a7-101">Calls to System.Windows.Input.PenContext.Disable on touch-enabled systems may throw an ArgumentException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="0b2a7-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="0b2a7-102">Details</span></span>|<span data-ttu-id="0b2a7-103">Bazı durumlarda, dokunma özellikli sistemlerde dahili **System.Windows.Intput.PenContext.Disable** yöntemi ne <code>T:System.ArgumentException</code> çağrıları reentrancy nedeniyle işlenmemiş atabilir.</span><span class="sxs-lookup"><span data-stu-id="0b2a7-103">Under some circumstances, calls to the internal **System.Windows.Intput.PenContext.Disable** method on touch-enabled systems may throw an unhandled <code>T:System.ArgumentException</code> because of reentrancy.</span></span>|
|<span data-ttu-id="0b2a7-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="0b2a7-104">Suggestion</span></span>|<span data-ttu-id="0b2a7-105">Bu sorun .NET Framework 4.7'de ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="0b2a7-105">This issue has been addressed in the .NET Framework 4.7.</span></span> <span data-ttu-id="0b2a7-106">İstisnayı önlemek için .NET Framework 4.7 ile başlayan bir .NET Framework sürümüne yükseltin.</span><span class="sxs-lookup"><span data-stu-id="0b2a7-106">To prevent the exception, upgrade to a version of the .NET Framework starting with the .NET Framework 4.7.</span></span>|
|<span data-ttu-id="0b2a7-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="0b2a7-107">Scope</span></span>|<span data-ttu-id="0b2a7-108">Edge</span><span class="sxs-lookup"><span data-stu-id="0b2a7-108">Edge</span></span>|
|<span data-ttu-id="0b2a7-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="0b2a7-109">Version</span></span>|<span data-ttu-id="0b2a7-110">4.6.1</span><span class="sxs-lookup"><span data-stu-id="0b2a7-110">4.6.1</span></span>|
|<span data-ttu-id="0b2a7-111">Tür</span><span class="sxs-lookup"><span data-stu-id="0b2a7-111">Type</span></span>|<span data-ttu-id="0b2a7-112">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="0b2a7-112">Retargeting</span></span>|
