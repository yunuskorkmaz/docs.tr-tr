---
ms.openlocfilehash: be496cd586f149ca9fd851d6aa00186e8080c66f
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84680335"
---
### <a name="winforms-methods-now-throw-argumentnullexception"></a>WinForms yöntemleri şimdi ArgumentNullException oluşturur

Bazı Windows Forms Yöntemler artık <xref:System.ArgumentNullException> , daha önce bir oluşturduklarında null bağımsız değişkenler oluşturur <xref:System.NullReferenceException> .

#### <a name="change-description"></a>Açıklamayı Değiştir

Daha önce, belirli Windows Forms Yöntemler, <xref:System.NullReferenceException> null olan bir bağımsız değişken geçirtiyse bir oluşturdu. .NET 5,0 ' den başlayarak, bu yöntemler artık <xref:System.ArgumentNullException> bunun yerine null bağımsız değişkenler oluşturur.

<xref:System.ArgumentNullException>.NET çalışma zamanının davranışına uygun bir şekilde oluşturuluyor. Ayrıca, bir bağımsız değişkenin null ve hangi bağımsız değişkeni olduğunu açıkça bir şekilde iletişim kurarak hata ayıklama deneyimini geliştirir.

#### <a name="version-introduced"></a>Sunulan sürüm

.NET 5,0

#### <a name="recommended-action"></a>Önerilen eylem

Bu yöntemlerin herhangi birini çağırırsanız ve kodunuz Şu anda bir <xref:System.NullReferenceException> boş bağımsız değişken için yakalar, <xref:System.ArgumentNullException> bunun yerine bir kullanın. Ayrıca, belirtilen yöntemlere null bağımsız değişkenlerin geçirilmesini engellemek için kodu güncellemeyi göz önünde bulundurun.

#### <a name="category"></a>Kategori

Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

Aşağıdaki tabloda etkilenen Yöntemler ve parametreler listelenmektedir:

> [!div class="mx-tdBreakAll"]
> | Yöntem | Parametre adı | Sürüm eklendi |
> |-|-|-|
> | <xref:System.Windows.Forms.Control.ControlCollection.%23ctor(System.Windows.Forms.Control)> | `owner` | 5,0 Preview 1 |
> | <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=nameWithType> | `item` | 5,0 Preview 1 |
> | <xref:System.Windows.Forms.TableLayoutControlCollection.%23ctor(System.Windows.Forms.TableLayoutPanel)> | `container` | 5,0 Preview 1 |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)?displayProperty=nameWithType> | `e` | 5,0 Preview 1 |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType> | `e` | 5,0 Preview 1 |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType> | `e` | 5,0 Preview 1 |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)?displayProperty=nameWithType> | `e` | 5,0 Preview 1 |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)?displayProperty=nameWithType> > | `e` | 5,0 Preview 1 |
> | <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)?displayProperty=nameWithType> | `dataGridViewCellStyle` | 5,0 Preview 2 |
> | <xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType> | `data` | 5,0 Preview 2 |
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.%23ctor(System.Windows.Forms.ListBox)> | `owner` | 5,0 Preview 5 |
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.CopyTo(System.Array,System.Int32)?displayProperty=nameWithType> | `destination` | 5,0 Preview 5 |
> | <xref:System.Windows.Forms.ListViewGroup.System%23Runtime%23Serialization%23ISerializable%23GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | `info` | 5,0 Preview 5 |
> | <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.%23ctor(System.String,System.Int32,System.Int32)> | `className` | 5,0 Preview 5 |

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
- `M:System.Windows.Forms.ListViewGroup.System%23Runtime%23Serialization%23ISerializable%23GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)`
- `M:System.Windows.Forms.VisualStyles.VisualStyleRenderer.%23ctor(System.String,System.Int32,System.Int32)`
- `M:System.Windows.Forms.ListBox.IntegerCollection.%23ctor(System.Windows.Forms.ListBox)`
- `M:System.Windows.Forms.ListBox.IntegerCollection.CopyTo(System.Array,System.Int32)`

-->
