---
ms.openlocfilehash: 26539011f0650c7a3bac9e1c41847561905fff58
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496583"
---
### <a name="managed-browser-hosting-controls-from-the-net-framework-11-and-20-are-blocked"></a><span data-ttu-id="80f46-101">.NET Framework 1,1 ve 2,0 ' den yönetilen tarayıcı barındıran denetimler engelleniyor</span><span class="sxs-lookup"><span data-stu-id="80f46-101">Managed browser hosting controls from the .NET Framework 1.1 and 2.0 are blocked</span></span>

#### <a name="details"></a><span data-ttu-id="80f46-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="80f46-102">Details</span></span>

<span data-ttu-id="80f46-103">Bu kontrollerin barındırılması Internet Explorer'da engellenir.</span><span class="sxs-lookup"><span data-stu-id="80f46-103">Hosting these controls is blocked in Internet Explorer.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="80f46-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="80f46-104">Suggestion</span></span>

<span data-ttu-id="80f46-105">Internet Explorer tarayıcı barındırma kontrollerini kullanan bir uygulamayı başlatmakta başarısız olacaktır.</span><span class="sxs-lookup"><span data-stu-id="80f46-105">Internet Explorer will fail to launch an application that uses managed browser hosting controls.</span></span> <span data-ttu-id="80f46-106">Önceki davranış, kayıt defteri alt anahtarının EnableIEHosting değerini <code>HKLM/SOFTWARE/MICROSOFT/.NETFramework</code> <code>1</code> x86 sistemleri için ve x64 sistemlerinde 32 bitlik süreçler için ve <code>EnableIEHosting</code> kayıt defteri alt anahtarının değerini <code>HKLM/SOFTWARE/Wow6432Node/Microsoft/.NETFramework</code> <code>1</code> x64 sistemlerinde 64 bit işlemlere ayarlayarak geri yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="80f46-106">The previous behavior can be restored by setting the EnableIEHosting value of the registry subkey <code>HKLM/SOFTWARE/MICROSOFT/.NETFramework</code> to <code>1</code> for x86 systems and for 32-bit processes on x64 systems, and by setting the <code>EnableIEHosting</code> value of the registry subkey <code>HKLM/SOFTWARE/Wow6432Node/Microsoft/.NETFramework</code> to <code>1</code> for 64-bit processes on x64 systems.</span></span>

| <span data-ttu-id="80f46-107">Name</span><span class="sxs-lookup"><span data-stu-id="80f46-107">Name</span></span>    | <span data-ttu-id="80f46-108">Değer</span><span class="sxs-lookup"><span data-stu-id="80f46-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="80f46-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="80f46-109">Scope</span></span>   |<span data-ttu-id="80f46-110">İkincil</span><span class="sxs-lookup"><span data-stu-id="80f46-110">Minor</span></span>|
|<span data-ttu-id="80f46-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="80f46-111">Version</span></span>|<span data-ttu-id="80f46-112">4,5</span><span class="sxs-lookup"><span data-stu-id="80f46-112">4.5</span></span>|
|<span data-ttu-id="80f46-113">Tür</span><span class="sxs-lookup"><span data-stu-id="80f46-113">Type</span></span>|<span data-ttu-id="80f46-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="80f46-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="80f46-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="80f46-115">Affected APIs</span></span>

<span data-ttu-id="80f46-116">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="80f46-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
