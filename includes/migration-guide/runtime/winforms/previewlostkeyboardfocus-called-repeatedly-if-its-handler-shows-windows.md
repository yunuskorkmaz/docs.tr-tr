---
ms.openlocfilehash: addfd55fd01b13e9088e4706ff846fc624aafa68
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235933"
---
### <a name="previewlostkeyboardfocus-is-called-repeatedly-if-its-handler-shows-a-windows-forms-message-box"></a>İşleyici, bir Windows Forms ileti kutusu görünüyorsa PreviewLostKeyboardFocus art arda çağrılır

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5, çağırma başlayarak <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> gelen bir <xref:System.Windows.UIElement.PreviewLostKeyboardFocus> işleyici ileti kutusu kapatıldığında, büyük olasılıkla ileti kutuları sonsuz bir döngüde kaynaklanan yeniden harekete işleyicinin neden olur.|
|Öneri|Bu sorunu çözmek için iki seçenek vardır:<ol><li>Çağırarak kalmayabilir <xref:System.Windows.MessageBox.Show%2A?displayProperty=nameWithType> yerine <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType>.</li><li>İleti kutusu göstererek kalmayabilir bir <xref:System.Windows.UIElement.LostKeyboardFocus?displayProperty=nameWithType> olay işleyicisi (başlangıcı yerine sonundan bir <xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=name> olay işleyicisi).</li></ol>|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Windows.ContentElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.IInputElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.UIElement3D.PreviewLostKeyboardFocus?displayProperty=nameWithType></li></ul>|
