---
ms.openlocfilehash: 1f85b1ce95ca07329aff77af4ec894622e0818d1
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606713"
---
### <a name="workflow-30-types-are-obsolete"></a><span data-ttu-id="91893-101">WorkFlow 3.0 türleri kullanım dışı</span><span class="sxs-lookup"><span data-stu-id="91893-101">WorkFlow 3.0 types are obsolete</span></span>

#### <a name="details"></a><span data-ttu-id="91893-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="91893-102">Details</span></span>

<span data-ttu-id="91893-103">Windows Workflow Foundation (WWF) 3.0 API’leri (System.Workflow ad alanından gelenler) artık kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="91893-103">Windows Workflow Foundation (WWF) 3.0 APIs (those from the System.Workflow namespace) are now obsolete.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="91893-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="91893-104">Suggestion</span></span>

<span data-ttu-id="91893-105">Bunun yerine yeni WWF 4.0 API’leri (System.Activities içinde) kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="91893-105">New WWF 4.0 APIs (in System.Activities) should be used instead.</span></span> <span data-ttu-id="91893-106">Yeni API’leri kullanmak için bir örnek [burada](~/docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md) ve daha ayrıntılı yönergeler [burada](/archive/blogs/workflowteam/wf3-types-marked-obsolete-in-net-4-5) bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="91893-106">An example of using the new APIs can be found [here](~/docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md) and further guidance is available [here](/archive/blogs/workflowteam/wf3-types-marked-obsolete-in-net-4-5).</span></span> <span data-ttu-id="91893-107">Alternatif olarak, WWF 3.0 API’leri hala desteklendiğinden bunlar kullanılabilir ve derleme zamanı uyarısı gizlenerek veya daha eski bir derleyici kullanılarak bu uyarı önlenebilir.</span><span class="sxs-lookup"><span data-stu-id="91893-107">Alternatively, since the WWF 3.0 APIs are still supported, they may be used and the build-time warning avoided either by suppressing it or by using an older compiler.</span></span>

| <span data-ttu-id="91893-108">Name</span><span class="sxs-lookup"><span data-stu-id="91893-108">Name</span></span>    | <span data-ttu-id="91893-109">Değer</span><span class="sxs-lookup"><span data-stu-id="91893-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="91893-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="91893-110">Scope</span></span>   | <span data-ttu-id="91893-111">Ana</span><span class="sxs-lookup"><span data-stu-id="91893-111">Major</span></span>       |
| <span data-ttu-id="91893-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="91893-112">Version</span></span> | <span data-ttu-id="91893-113">4,5</span><span class="sxs-lookup"><span data-stu-id="91893-113">4.5</span></span>         |
| <span data-ttu-id="91893-114">Tür</span><span class="sxs-lookup"><span data-stu-id="91893-114">Type</span></span>    | <span data-ttu-id="91893-115">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="91893-115">Retargeting</span></span> |
