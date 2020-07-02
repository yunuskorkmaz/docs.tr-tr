---
ms.openlocfilehash: b6cb7edcd6bed50efdf59f3321320ac8cd1b1ab8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617288"
---
### <a name="some-workflow-drag-and-drop-apis-are-obsolete"></a><span data-ttu-id="3314a-101">Bazı Iş akışı sürükle ve bırak API 'Leri artık kullanılmıyor</span><span class="sxs-lookup"><span data-stu-id="3314a-101">Some WorkFlow drag-and-drop APIs are obsolete</span></span>

#### <a name="details"></a><span data-ttu-id="3314a-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="3314a-102">Details</span></span>

<span data-ttu-id="3314a-103">Bu Iş akışı sürükle ve bırak API 'SI eskidir ve uygulama 4,5 ' ye karşı yeniden derlenmeye yönelik derleyici uyarılarına neden olur.</span><span class="sxs-lookup"><span data-stu-id="3314a-103">This WorkFlow drag-and-drop API is obsolete and will cause compiler warnings if the app is rebuilt against 4.5.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3314a-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="3314a-104">Suggestion</span></span>

<span data-ttu-id="3314a-105"><xref:System.Activities.Presentation.DragDropHelper?displayProperty=fullName>Bunun yerine birden çok nesne içeren işlemleri destekleyen yeni API 'ler kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3314a-105">New <xref:System.Activities.Presentation.DragDropHelper?displayProperty=fullName> APIs that support operations with multiple objects should be used instead.</span></span> <span data-ttu-id="3314a-106">Alternatif olarak, derleme uyarıları bastırılabilir veya eski bir derleyici kullanılarak kaçınılabilir.</span><span class="sxs-lookup"><span data-stu-id="3314a-106">Alternatively, the build warnings can be suppressed or they can be avoided by using an older compiler.</span></span> <span data-ttu-id="3314a-107">API 'Ler hala desteklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="3314a-107">The APIs are still supported.</span></span>

| <span data-ttu-id="3314a-108">Name</span><span class="sxs-lookup"><span data-stu-id="3314a-108">Name</span></span>    | <span data-ttu-id="3314a-109">Değer</span><span class="sxs-lookup"><span data-stu-id="3314a-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3314a-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="3314a-110">Scope</span></span>   | <span data-ttu-id="3314a-111">İkincil</span><span class="sxs-lookup"><span data-stu-id="3314a-111">Minor</span></span>       |
| <span data-ttu-id="3314a-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="3314a-112">Version</span></span> | <span data-ttu-id="3314a-113">4,5</span><span class="sxs-lookup"><span data-stu-id="3314a-113">4.5</span></span>         |
| <span data-ttu-id="3314a-114">Tür</span><span class="sxs-lookup"><span data-stu-id="3314a-114">Type</span></span>    | <span data-ttu-id="3314a-115">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="3314a-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="3314a-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="3314a-116">Affected APIs</span></span>

- <xref:System.Activities.Presentation.DragDropHelper.DoDragMove(System.Activities.Presentation.WorkflowViewElement,System.Windows.Point)?displayProperty=nameWithType>
- <xref:System.Activities.Presentation.DragDropHelper.GetCompositeView(System.Windows.DragEventArgs)?displayProperty=nameWithType>
- <xref:System.Activities.Presentation.DragDropHelper.GetDraggedModelItem(System.Windows.DragEventArgs)?displayProperty=nameWithType>
- <xref:System.Activities.Presentation.DragDropHelper.GetDroppedObject(System.Windows.DependencyObject,System.Windows.DragEventArgs,System.Activities.Presentation.EditingContext)?displayProperty=nameWithType>
