---
ms.openlocfilehash: add3ff8faed2e7fab245e5b6f1b9158b7bdd06f5
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567364"
---
### <a name="cellformatting-event-not-raised-if-tooltip-is-shown"></a>Araç ipucu gösterildiğinde CellFormatting olayı oluşturulmaz

Bir <xref:System.Windows.Forms.DataGridView>, bir fare ve klavye aracılığıyla seçildiğinde bir hücrenin metin ve hata araç ipuçlarını gösterir. Bir araç ipucu gösteriliyorsa <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> olayı oluşturulmaz.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 3,1 ' den önce, `true` olarak ayarlanan <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> özelliği olan bir <xref:System.Windows.Forms.DataGridView>, hücrenin bir fare ile üzerine gelindiğinde bir hücrenin metin ve hataları için bir araç ipucu gösterdi. Klavye aracılığıyla bir hücre seçildiğinde araç ipuçları gösterilmez (örneğin, sekme tuşunu, kısayol tuşlarını veya ok gezintisini kullanarak). Kullanıcı bir hücreyi düzenlediyseniz ve sonra <xref:System.Windows.Forms.DataGridView> hala düzenleme modundayken, <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> özelliği ayarlanmamış bir hücrenin üzerine gelindiğinde, hücrede görüntülenecek hücre metnini biçimlendirmek için <xref:System.Windows.Forms.DataGridView.CellFormatting> bir olay harekete geçirilir.

.NET Core 3,1 ' den başlayarak erişilebilirlik standartlarını karşılamak için, <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> özelliği `true` olarak ayarlanmış bir <xref:System.Windows.Forms.DataGridView>, bir hücrenin metin ve hatalarının yalnızca hücre üzerine gelindiğinde değil, ancak klavye aracılığıyla seçilme durumunda olmayan bir gösterir. Bu değişikliğin bir sonucu olarak, <xref:System.Windows.Forms.DataGridView> düzenleme modundayken, <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> özelliği ayarlanmış olmayan hücreler üzerine gelindiğinde <xref:System.Windows.Forms.DataGridView.CellFormatting> *olayı oluşturulmaz.* Vurgulanan hücrenin içeriği hücrede görüntülenmek yerine bir araç ipucu olarak gösterildiğinden olay oluşturulmaz.

#### <a name="version-introduced"></a>Sunulan sürüm

3,1

#### <a name="recommended-action"></a>Önerilen eylem

<xref:System.Windows.Forms.DataGridView> düzenleme modundayken <xref:System.Windows.Forms.DataGridView.CellFormatting> olayına bağlı tüm kodları yeniden düzenleyin.

#### <a name="category"></a>Kategori

Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!-- 

### Affected APIs

- Not detectable via API analysis.

-->
