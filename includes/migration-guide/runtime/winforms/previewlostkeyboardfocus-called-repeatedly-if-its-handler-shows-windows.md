---
ms.openlocfilehash: 2aa6603e2ed77ffa94fbc6325cd5db50985bda6a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620681"
---
### <a name="previewlostkeyboardfocus-is-called-repeatedly-if-its-handler-shows-a-windows-forms-message-box"></a>PreviewLostKeyboardFocus, işleyicisi bir Windows Forms ileti kutusu gösteriyorsa, tekrar tekrar çağırılır

#### <a name="details"></a>Ayrıntılar

.NET Framework 4,5 ' den başlayarak, <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> bir <xref:System.Windows.UIElement.PreviewLostKeyboardFocus> işleyiciden çağırmak, ileti kutusu kapatıldığında işleyicinin yeniden başlatılmasına neden olur ve bu da muhtemelen ileti kutularından oluşan sonsuz bir döngüye neden olur.

#### <a name="suggestion"></a>Öneri

Bu sorunu geçici olarak çözmek için iki seçenek vardır:<ol><li>Yerine çağırarak bu durum önlenebilir <xref:System.Windows.MessageBox.Show%2A?displayProperty=nameWithType> <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> .</li><li>Bir <xref:System.Windows.UIElement.LostKeyboardFocus> olay işleyicisinden (bir olay işleyicisine karşılık gelen) ileti kutusu gösterilerek kaçınılabilir <xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=fullName> .</li></ol>

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4,5|
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Windows.ContentElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.IInputElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.UIElement3D.PreviewLostKeyboardFocus?displayProperty=nameWithType></li></ul>|
