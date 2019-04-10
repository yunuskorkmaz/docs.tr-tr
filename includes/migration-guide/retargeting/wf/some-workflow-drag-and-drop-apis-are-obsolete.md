---
ms.openlocfilehash: 297af393e86c65e84ea7271d98eab36dbc6dbb0e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234858"
---
### <a name="some-workflow-drag-and-drop-apis-are-obsolete"></a><span data-ttu-id="79e5a-101">Bazı iş akışı sürükle ve bırak API artık kullanılmıyor</span><span class="sxs-lookup"><span data-stu-id="79e5a-101">Some WorkFlow drag-and-drop APIs are obsolete</span></span>

|   |   |
|---|---|
|<span data-ttu-id="79e5a-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="79e5a-102">Details</span></span>|<span data-ttu-id="79e5a-103">Bu iş akışı sürükle ve bırak API artık kullanılmıyor ve 4.5 karşı uygulamayı yeniden oluşturulursa derleyici uyarılarına neden olur.</span><span class="sxs-lookup"><span data-stu-id="79e5a-103">This WorkFlow drag-and-drop API is obsolete and will cause compiler warnings if the app is rebuilt against 4.5.</span></span>|
|<span data-ttu-id="79e5a-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="79e5a-104">Suggestion</span></span>|<span data-ttu-id="79e5a-105">Yeni <xref:System.Activities.Presentation.DragDropHelper?displayProperty=name> birden fazla nesneyle işlemlerini destekleyen API'ler bunun yerine kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="79e5a-105">New <xref:System.Activities.Presentation.DragDropHelper?displayProperty=name> APIs that support operations with multiple objects should be used instead.</span></span> <span data-ttu-id="79e5a-106">Alternatif olarak, derleme uyarıları gizlenebilir veya daha eski bir derleyici kullanılarak önlenebilir.</span><span class="sxs-lookup"><span data-stu-id="79e5a-106">Alternatively, the build warnings can be suppressed or they can be avoided by using an older compiler.</span></span> <span data-ttu-id="79e5a-107">API'leri hala desteklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="79e5a-107">The APIs are still supported.</span></span>|
|<span data-ttu-id="79e5a-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="79e5a-108">Scope</span></span>|<span data-ttu-id="79e5a-109">İkincil</span><span class="sxs-lookup"><span data-stu-id="79e5a-109">Minor</span></span>|
|<span data-ttu-id="79e5a-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="79e5a-110">Version</span></span>|<span data-ttu-id="79e5a-111">4,5</span><span class="sxs-lookup"><span data-stu-id="79e5a-111">4.5</span></span>|
|<span data-ttu-id="79e5a-112">Tür</span><span class="sxs-lookup"><span data-stu-id="79e5a-112">Type</span></span>|<span data-ttu-id="79e5a-113">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="79e5a-113">Retargeting</span></span>|
|<span data-ttu-id="79e5a-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="79e5a-114">Affected APIs</span></span>|<ul><li><xref:System.Activities.Presentation.DragDropHelper.DoDragMove(System.Activities.Presentation.WorkflowViewElement,System.Windows.Point)?displayProperty=nameWithType></li><li><xref:System.Activities.Presentation.DragDropHelper.GetCompositeView(System.Windows.DragEventArgs)?displayProperty=nameWithType></li><li><xref:System.Activities.Presentation.DragDropHelper.GetDraggedModelItem(System.Windows.DragEventArgs)?displayProperty=nameWithType></li><li><xref:System.Activities.Presentation.DragDropHelper.GetDroppedObject(System.Windows.DependencyObject,System.Windows.DragEventArgs,System.Activities.Presentation.EditingContext)?displayProperty=nameWithType></li></ul>|
