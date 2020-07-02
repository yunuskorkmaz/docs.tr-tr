---
ms.openlocfilehash: cecb7b2abd4f57fdaacb0ea373cc19dc3cd9b24a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620543"
---
### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a><span data-ttu-id="88076-101">EnableViewStateMac 'i artık false olarak ayarlayaamayacak</span><span class="sxs-lookup"><span data-stu-id="88076-101">No longer able to set EnableViewStateMac to false</span></span>

#### <a name="details"></a><span data-ttu-id="88076-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="88076-102">Details</span></span>

<span data-ttu-id="88076-103">ASP.NET artık geliştiricilerin veya belirlemesine izin vermez <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code> .</span><span class="sxs-lookup"><span data-stu-id="88076-103">ASP.NET no longer allows developers to specify <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> or <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>.</span></span> <span data-ttu-id="88076-104">Görünüm durumu iletisi kimlik doğrulama kodu (MAC) artık katıştırılmış görünüm durumundaki tüm istekler için zorlanır.</span><span class="sxs-lookup"><span data-stu-id="88076-104">The view state message authentication code (MAC) is now enforced for all requests with embedded view state.</span></span> <span data-ttu-id="88076-105">Yalnızca EnableViewStateMac özelliğini açıkça ayarlamış olan uygulamalar <code>false</code> etkilenir.</span><span class="sxs-lookup"><span data-stu-id="88076-105">Only apps that explicitly set the EnableViewStateMac property to <code>false</code> are affected.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="88076-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="88076-106">Suggestion</span></span>

<span data-ttu-id="88076-107">EnableViewStateMac 'in doğru olması gerekir ve sonuçta elde edilen MAC hatalarının çözümlenmesi gerekir ( [Bu](https://support.microsoft.com/kb/2915218)kılavuzda açıklandığı gıbı, Mac hatalarına neden olan Özellikler ' e bağlı olarak birden çok çözüm içeren).</span><span class="sxs-lookup"><span data-stu-id="88076-107">EnableViewStateMac must be assumed to be true, and any resulting MAC errors must be resolved (as explained in [this guidance](https://support.microsoft.com/kb/2915218), which contains multiple resolutions depending on the specifics of what is causing MAC errors).</span></span>

| <span data-ttu-id="88076-108">Name</span><span class="sxs-lookup"><span data-stu-id="88076-108">Name</span></span>    | <span data-ttu-id="88076-109">Değer</span><span class="sxs-lookup"><span data-stu-id="88076-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="88076-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="88076-110">Scope</span></span>   |<span data-ttu-id="88076-111">Ana</span><span class="sxs-lookup"><span data-stu-id="88076-111">Major</span></span>|
|<span data-ttu-id="88076-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="88076-112">Version</span></span>|<span data-ttu-id="88076-113">4.5.2</span><span class="sxs-lookup"><span data-stu-id="88076-113">4.5.2</span></span>|
|<span data-ttu-id="88076-114">Tür</span><span class="sxs-lookup"><span data-stu-id="88076-114">Type</span></span>|<span data-ttu-id="88076-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="88076-115">Runtime</span></span>|
