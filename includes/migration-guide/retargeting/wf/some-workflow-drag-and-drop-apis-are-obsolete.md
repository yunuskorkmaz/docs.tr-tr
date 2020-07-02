---
ms.openlocfilehash: b6cb7edcd6bed50efdf59f3321320ac8cd1b1ab8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617288"
---
### <a name="some-workflow-drag-and-drop-apis-are-obsolete"></a>Bazı Iş akışı sürükle ve bırak API 'Leri artık kullanılmıyor

#### <a name="details"></a>Ayrıntılar

Bu Iş akışı sürükle ve bırak API 'SI eskidir ve uygulama 4,5 ' ye karşı yeniden derlenmeye yönelik derleyici uyarılarına neden olur.

#### <a name="suggestion"></a>Öneri

<xref:System.Activities.Presentation.DragDropHelper?displayProperty=fullName>Bunun yerine birden çok nesne içeren işlemleri destekleyen yeni API 'ler kullanılmalıdır. Alternatif olarak, derleme uyarıları bastırılabilir veya eski bir derleyici kullanılarak kaçınılabilir. API 'Ler hala desteklenmektedir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | İkincil       |
| Sürüm | 4,5         |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Activities.Presentation.DragDropHelper.DoDragMove(System.Activities.Presentation.WorkflowViewElement,System.Windows.Point)?displayProperty=nameWithType>
- <xref:System.Activities.Presentation.DragDropHelper.GetCompositeView(System.Windows.DragEventArgs)?displayProperty=nameWithType>
- <xref:System.Activities.Presentation.DragDropHelper.GetDraggedModelItem(System.Windows.DragEventArgs)?displayProperty=nameWithType>
- <xref:System.Activities.Presentation.DragDropHelper.GetDroppedObject(System.Windows.DependencyObject,System.Windows.DragEventArgs,System.Activities.Presentation.EditingContext)?displayProperty=nameWithType>
