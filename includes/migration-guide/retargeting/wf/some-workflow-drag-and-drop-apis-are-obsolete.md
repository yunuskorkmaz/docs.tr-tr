---
ms.openlocfilehash: 297af393e86c65e84ea7271d98eab36dbc6dbb0e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774478"
---
### <a name="some-workflow-drag-and-drop-apis-are-obsolete"></a>Bazı iş akışı sürükle ve bırak API artık kullanılmıyor

|   |   |
|---|---|
|Ayrıntılar|Bu iş akışı sürükle ve bırak API artık kullanılmıyor ve 4.5 karşı uygulamayı yeniden oluşturulursa derleyici uyarılarına neden olur.|
|Öneri|Yeni <xref:System.Activities.Presentation.DragDropHelper?displayProperty=name> birden fazla nesneyle işlemlerini destekleyen API'ler bunun yerine kullanılmalıdır. Alternatif olarak, derleme uyarıları gizlenebilir veya daha eski bir derleyici kullanılarak önlenebilir. API'leri hala desteklenmektedir.|
|Kapsam|İkincil|
|Sürüm|4,5|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Activities.Presentation.DragDropHelper.DoDragMove(System.Activities.Presentation.WorkflowViewElement,System.Windows.Point)?displayProperty=nameWithType></li><li><xref:System.Activities.Presentation.DragDropHelper.GetCompositeView(System.Windows.DragEventArgs)?displayProperty=nameWithType></li><li><xref:System.Activities.Presentation.DragDropHelper.GetDraggedModelItem(System.Windows.DragEventArgs)?displayProperty=nameWithType></li><li><xref:System.Activities.Presentation.DragDropHelper.GetDroppedObject(System.Windows.DependencyObject,System.Windows.DragEventArgs,System.Activities.Presentation.EditingContext)?displayProperty=nameWithType></li></ul>|
