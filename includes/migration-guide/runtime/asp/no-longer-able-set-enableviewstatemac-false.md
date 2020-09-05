---
ms.openlocfilehash: c1793bb51f7da9169e912078fde202d0d62a4183
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496510"
---
### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a><span data-ttu-id="e3f32-101">EnableViewStateMac 'i artık false olarak ayarlayaamayacak</span><span class="sxs-lookup"><span data-stu-id="e3f32-101">No longer able to set EnableViewStateMac to false</span></span>

#### <a name="details"></a><span data-ttu-id="e3f32-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="e3f32-102">Details</span></span>

<span data-ttu-id="e3f32-103">ASP.NET artık geliştiricilerin veya belirlemesine izin vermez <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code> .</span><span class="sxs-lookup"><span data-stu-id="e3f32-103">ASP.NET no longer allows developers to specify <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> or <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>.</span></span> <span data-ttu-id="e3f32-104">Görünüm durumu iletisi kimlik doğrulama kodu (MAC) artık katıştırılmış görünüm durumundaki tüm istekler için zorlanır.</span><span class="sxs-lookup"><span data-stu-id="e3f32-104">The view state message authentication code (MAC) is now enforced for all requests with embedded view state.</span></span> <span data-ttu-id="e3f32-105">Yalnızca EnableViewStateMac özelliğini açıkça ayarlamış olan uygulamalar <code>false</code> etkilenir.</span><span class="sxs-lookup"><span data-stu-id="e3f32-105">Only apps that explicitly set the EnableViewStateMac property to <code>false</code> are affected.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e3f32-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="e3f32-106">Suggestion</span></span>

<span data-ttu-id="e3f32-107">EnableViewStateMac 'in doğru olması gerekir ve sonuçta elde edilen MAC hatalarının çözümlenmesi gerekir ( [Bu](https://support.microsoft.com/kb/2915218)kılavuzda açıklandığı gıbı, Mac hatalarına neden olan Özellikler ' e bağlı olarak birden çok çözüm içeren).</span><span class="sxs-lookup"><span data-stu-id="e3f32-107">EnableViewStateMac must be assumed to be true, and any resulting MAC errors must be resolved (as explained in [this guidance](https://support.microsoft.com/kb/2915218), which contains multiple resolutions depending on the specifics of what is causing MAC errors).</span></span>

| <span data-ttu-id="e3f32-108">Name</span><span class="sxs-lookup"><span data-stu-id="e3f32-108">Name</span></span>    | <span data-ttu-id="e3f32-109">Değer</span><span class="sxs-lookup"><span data-stu-id="e3f32-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e3f32-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="e3f32-110">Scope</span></span>   |<span data-ttu-id="e3f32-111">Ana</span><span class="sxs-lookup"><span data-stu-id="e3f32-111">Major</span></span>|
|<span data-ttu-id="e3f32-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="e3f32-112">Version</span></span>|<span data-ttu-id="e3f32-113">4.5.2</span><span class="sxs-lookup"><span data-stu-id="e3f32-113">4.5.2</span></span>|
|<span data-ttu-id="e3f32-114">Tür</span><span class="sxs-lookup"><span data-stu-id="e3f32-114">Type</span></span>|<span data-ttu-id="e3f32-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="e3f32-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="e3f32-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="e3f32-116">Affected APIs</span></span>

<span data-ttu-id="e3f32-117">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="e3f32-117">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
