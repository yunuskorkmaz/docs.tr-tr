---
ms.openlocfilehash: 38c35f3f6f2262d06409690d2326d9b982e1ec86
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59805225"
---
### <a name="managed-browser-hosting-controls-from-the-net-framework-11-and-20-are-blocked"></a><span data-ttu-id="4a8c1-101">Yönetilen tarayıcı barındırma denetimleri .NET Framework 1.1 ve 2.0 engellenir</span><span class="sxs-lookup"><span data-stu-id="4a8c1-101">Managed browser hosting controls from the .NET Framework 1.1 and 2.0 are blocked</span></span>

|   |   |
|---|---|
|<span data-ttu-id="4a8c1-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="4a8c1-102">Details</span></span>|<span data-ttu-id="4a8c1-103">Bu kontrollerin barındırılması Internet Explorer'da engellenir.</span><span class="sxs-lookup"><span data-stu-id="4a8c1-103">Hosting these controls is blocked in Internet Explorer.</span></span>|
|<span data-ttu-id="4a8c1-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="4a8c1-104">Suggestion</span></span>|<span data-ttu-id="4a8c1-105">Internet Explorer tarayıcı barındırma kontrollerini kullanan bir uygulamayı başlatmakta başarısız olacaktır.</span><span class="sxs-lookup"><span data-stu-id="4a8c1-105">Internet Explorer will fail to launch an application that uses managed browser hosting controls.</span></span> <span data-ttu-id="4a8c1-106">Kayıt defteri alt anahtarı değerini ayarlayarak önceki davranış geri yüklenebilir <code>HKLM/SOFTWARE/MICROSOFT/.NETFramework</code> için <code>1</code> x86 için sistemleri ve x64 32 bitlik işlemler için sistemleri ve ayarlayarak <code>EnableIEHosting</code> kayıtdefterialtanahtarınındeğerini<code>HKLM/SOFTWARE/Wow6432Node/Microsoft/.NETFramework</code>için <code>1</code> x64 64 bitlik işlemler için sistemler.</span><span class="sxs-lookup"><span data-stu-id="4a8c1-106">The previous behavior can be restored by setting the EnableIEHosting value of the registry subkey <code>HKLM/SOFTWARE/MICROSOFT/.NETFramework</code> to <code>1</code> for x86 systems and for 32-bit processes on x64 systems, and by setting the <code>EnableIEHosting</code> value of the registry subkey <code>HKLM/SOFTWARE/Wow6432Node/Microsoft/.NETFramework</code> to <code>1</code> for 64-bit processes on x64 systems.</span></span>|
|<span data-ttu-id="4a8c1-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="4a8c1-107">Scope</span></span>|<span data-ttu-id="4a8c1-108">İkincil</span><span class="sxs-lookup"><span data-stu-id="4a8c1-108">Minor</span></span>|
|<span data-ttu-id="4a8c1-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="4a8c1-109">Version</span></span>|<span data-ttu-id="4a8c1-110">4,5</span><span class="sxs-lookup"><span data-stu-id="4a8c1-110">4.5</span></span>|
|<span data-ttu-id="4a8c1-111">Tür</span><span class="sxs-lookup"><span data-stu-id="4a8c1-111">Type</span></span>|<span data-ttu-id="4a8c1-112">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="4a8c1-112">Runtime</span></span>|
