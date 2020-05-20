---
ms.openlocfilehash: ab8d801f3cdcfbeb6de20146754b26e3713d7dd6
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702482"
---
### <a name="winforms-methods-now-throw-argumentnullexception"></a>WinForms yöntemleri şimdi ArgumentNullException oluşturur

Bazı Windows Forms Yöntemler artık <xref:System.ArgumentNullException> , daha önce bir oluşturduklarında null bağımsız değişkenler oluşturur <xref:System.NullReferenceException> .

#### <a name="change-description"></a>Açıklamayı Değiştir

Daha önce, belirli Windows Forms Yöntemler, <xref:System.NullReferenceException> null olan bir bağımsız değişken geçirtiyse bir oluşturdu. .NET 5,0 ' den başlayarak, bu yöntemler artık <xref:System.ArgumentNullException> bunun yerine null bağımsız değişkenler oluşturur.

<xref:System.ArgumentNullException>.NET çalışma zamanının davranışına uygun bir şekilde oluşturuluyor. Ayrıca, bir bağımsız değişkenin null ve hangi bağımsız değişkeni olduğunu açıkça bir şekilde iletişim kurarak hata ayıklama deneyimini geliştirir.

#### <a name="version-introduced"></a>Sunulan sürüm

.NET 5,0 Preview 1 \
.NET 5,0 Preview 2

#### <a name="recommended-action"></a>Önerilen eylem

Bu yöntemlerin herhangi birini çağırırsanız ve kodunuz Şu anda bir <xref:System.NullReferenceException> boş bağımsız değişken için yakalar, <xref:System.ArgumentNullException> bunun yerine bir kullanın. Ayrıca, belirtilen yöntemlere null bağımsız değişkenlerin geçirilmesini engellemek için kodu güncellemeyi göz önünde bulundurun.

#### <a name="category"></a>Kategori

Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

.NET 5,0 Preview 1 ' den başlayarak:

- <xref:System.Windows.Forms.Control.ControlCollection.%23ctor(System.Windows.Forms.Control)>
- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.TableLayoutControlCollection.%23ctor(System.Windows.Forms.TableLayoutPanel)>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)?displayProperty=nameWithType>

.NET 5,0 Preview 2 ' den itibaren:

- <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType>( <xref:System.IO.Stream> yalnızca parametre için)

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.Control.ControlCollection.#ctor(System.Windows.Forms.Control)`
- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`
- `M:System.Windows.Forms.TableLayoutControlCollection.#ctor(System.Windows.Forms.TableLayoutPanel)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)`
- `M:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)`
- `M:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)`

-->
