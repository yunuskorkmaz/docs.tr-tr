---
ms.openlocfilehash: 6bb8c87af66e744514fb43e628c6423487342ac2
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72887852"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a><span data-ttu-id="d49dc-101">Dokunmatik özellikli sistemlerde System. Windows. Input. PenContext. Disable için çağrılar bir ArgumentException oluşturabilir</span><span class="sxs-lookup"><span data-stu-id="d49dc-101">Calls to System.Windows.Input.PenContext.Disable on touch-enabled systems may throw an ArgumentException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="d49dc-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="d49dc-102">Details</span></span>|<span data-ttu-id="d49dc-103">Bazı durumlarda, dokunmatik özellikli sistemlerde iç **System. Windows. Int32. PenContext. Disable** yöntemine yapılan çağrılar, yeniden giriş nedeniyle işlenmemiş bir <code>T:System.ArgumentException</code> oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="d49dc-103">Under some circumstances, calls to the internal **System.Windows.Intput.PenContext.Disable** method on touch-enabled systems may throw an unhandled <code>T:System.ArgumentException</code> because of reentrancy.</span></span>|
|<span data-ttu-id="d49dc-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="d49dc-104">Suggestion</span></span>|<span data-ttu-id="d49dc-105">Bu sorun 4,7 .NET Framework giderilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d49dc-105">This issue has been addressed in the .NET Framework 4.7.</span></span> <span data-ttu-id="d49dc-106">Özel durumu engellemek için, .NET Framework .NET Framework 4,7 ' den başlayarak bir sürümüne yükseltin.</span><span class="sxs-lookup"><span data-stu-id="d49dc-106">To prevent the exception, upgrade to a version of the .NET Framework starting with the .NET Framework 4.7.</span></span>|
|<span data-ttu-id="d49dc-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="d49dc-107">Scope</span></span>|<span data-ttu-id="d49dc-108">Kenar</span><span class="sxs-lookup"><span data-stu-id="d49dc-108">Edge</span></span>|
|<span data-ttu-id="d49dc-109">Version</span><span class="sxs-lookup"><span data-stu-id="d49dc-109">Version</span></span>|<span data-ttu-id="d49dc-110">4.6.1</span><span class="sxs-lookup"><span data-stu-id="d49dc-110">4.6.1</span></span>|
|<span data-ttu-id="d49dc-111">Tür</span><span class="sxs-lookup"><span data-stu-id="d49dc-111">Type</span></span>|<span data-ttu-id="d49dc-112">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="d49dc-112">Retargeting</span></span>|
