---
ms.openlocfilehash: 4a34a64eba72ea24c1d830566565ce4fbee8e5b7
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721475"
---
### <a name="cellformatting-event-not-raised-if-tooltip-is-shown"></a>Araç ipucu gösterildiğinde CellFormatting olayı oluşturulmaz

<xref:System.Windows.Forms.DataGridView>Şimdi bir fare ve klavye aracılığıyla seçildiğinde bir hücrenin metin ve hata araç ipuçlarını gösterir. Bir araç ipucu gösteriliyorsa, <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> olay oluşturulmaz.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 3,1 ' den önce, <xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> özelliği, `true` hücrenin bir fare tarafından nasıl ele alındığı zaman bir hücrenin metin ve hataları için bir araç ipucu gösterilmişti olarak ayarlanmıştır. Klavye aracılığıyla bir hücre seçildiğinde araç ipuçları gösterilmez (örneğin, sekme tuşunu, kısayol tuşlarını veya ok gezintisini kullanarak). Kullanıcı bir hücreyi düzenlediyseniz ve sonra <xref:System.Windows.Forms.DataGridView> hala düzenleme modundayken, özelliği ayarlanmış olmayan bir hücrenin üzerine gelindiğinde, hücrede <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> <xref:System.Windows.Forms.DataGridView.CellFormatting> görüntülenecek hücre metnini biçimlendirmek için bir olay harekete geçirildi.

.NET Core 3,1 ' den başlayarak erişilebilirlik standartlarını karşılamak için, özelliği, bir <xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> `true` hücrenin metin ve hataları yalnızca hücre üzerine gelindiğinde değil, ancak klavye aracılığıyla seçilme durumunda olmayan bir hücrenin metin ve hatalarının araç ipuçlarını gösterir. Bu değişikliğin bir sonucu olarak, <xref:System.Windows.Forms.DataGridView.CellFormatting> özellik kümesi olmayan hücreler *not* <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> düzenleme modunda olduğunda olay oluşturulmaz <xref:System.Windows.Forms.DataGridView> . Vurgulanan hücrenin içeriği hücrede görüntülenmek yerine bir araç ipucu olarak gösterildiğinden olay oluşturulmaz.

#### <a name="version-introduced"></a>Sunulan sürüm

3,1

#### <a name="recommended-action"></a>Önerilen eylem

<xref:System.Windows.Forms.DataGridView.CellFormatting>Düzenleme modundayken olaya bağlı tüm kodu <xref:System.Windows.Forms.DataGridView> yeniden düzenleyin.

#### <a name="category"></a>Kategori

Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

Yok

<!-- 

#### Affected APIs

Not detectable via API analysis.

-->
