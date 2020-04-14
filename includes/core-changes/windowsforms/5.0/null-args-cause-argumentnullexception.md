---
ms.openlocfilehash: fc0eec26073c299887b4748d0ad37e21c7294e84
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81274981"
---
### <a name="winforms-apis-now-throw-argumentnullexception"></a>WinForms API'ler şimdi ArgumentNullException atmak

Bazı Windows Forms yöntemleri <xref:System.ArgumentNullException> şimdi null bağımsız değişkenler <xref:System.NullReferenceException>için bir atmak, daha önce bir attı .

#### <a name="change-description"></a>Açıklamayı değiştir

Daha önce, bazı Windows <xref:System.NullReferenceException> Forms yöntemleri null bir argüman geçti eğer attı. .NET 5.0'dan başlayarak, <xref:System.ArgumentNullException> bu yöntemler artık null bağımsız değişkenler için bir şey atar.

.NET <xref:System.ArgumentNullException> çalışma zamanının davranışına uygun bir atma. Ayrıca, bir bağımsız değişkenin boş olduğunu ve hangi bağımsız değişken olduğunu açıkça ifade ederek hata ayıklama deneyimini geliştirir.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

.NET 5.0 Önizleme 1\
.NET 5.0 Önizleme 2

#### <a name="recommended-action"></a>Önerilen eylem

Bu yöntemlerden herhangi birini ararsanız ve <xref:System.NullReferenceException> kodunuz şu <xref:System.ArgumentNullException> anda null bağımsız değişkenler için yakalarsa, bunun yerine bir yakalama. Buna ek olarak, listelenen yöntemlere null bağımsız değişkenleri geçmesini önlemek için kodu güncelleştirmeyi düşünün.

#### <a name="category"></a>Kategori

Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

.NET 5.0 Önizleme 1'den başlayarak:

- <xref:System.Windows.Forms.Control.ControlCollection.%23ctor(System.Windows.Forms.Control)>
- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.TableLayoutControlCollection.%23ctor(System.Windows.Forms.TableLayoutPanel)>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)?displayProperty=nameWithType>

.NET 5.0 Önizleme 2'den başlayarak:

- <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType>(yalnızca <xref:System.IO.Stream> parametre için)

<!-- 

### Affected APIs

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
