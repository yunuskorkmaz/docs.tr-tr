---
ms.openlocfilehash: b736ab743a628fdcbc53c5ee51551e5dad986885
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888155"
---
### <a name="cellformatting-event-not-raised-if-tooltip-is-shown"></a>Araç ipucu gösterilirse CellFormatting olayı yükseltilmez

Şimdi, <xref:System.Windows.Forms.DataGridView> bir fare tarafından gezinildiğinde ve klavye den seçildiğinde hücrenin metin ve hata araç uçlarını gösterir. Bir araç ipucu gösterilirse, <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> olay yükseltilmez.

#### <a name="change-description"></a>Açıklamayı değiştir

.NET Core 3.1'den <xref:System.Windows.Forms.DataGridView> önce, <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> hücre `true` fare tarafından havada yken hücre metni ve hataları için bir araç ucu gösterebilecek özellik ayarlanmış bir özellik. Bir hücre klavye den seçildiğinde (örneğin, Sekme tuşu, kısayol tuşları veya ok gezintisi kullanılarak) araç ipuçları gösterilmedi. Kullanıcı bir hücreyi düzenlediyse ve <xref:System.Windows.Forms.DataGridView> daha sonra, düzenleme modundayken, <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> özellik kümesi olmayan bir hücrenin <xref:System.Windows.Forms.DataGridView.CellFormatting> üzerinde gezinilmişse, hücremetnini hücrede görüntülenmek üzere biçimlendirmek için bir olay yükseltildi.

.NET Core 3.1'den başlayarak erişilebilirlik <xref:System.Windows.Forms.DataGridView> standartlarını karşılamak <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> için, `true` hücrenin metniiçin araç ipuçlarını ve yalnızca hücre havada yken değil, klavye aracılığıyla seçildiğinde de hatalar için araç ipuçlarını gösteren bir özellik kümesi vardır. Bu değişikliğin bir sonucu <xref:System.Windows.Forms.DataGridView.CellFormatting> olarak, <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> özellik kümesi olmayan hücreler akışlı olduğunda <xref:System.Windows.Forms.DataGridView> olay *yükseltilmez.* Havada gezinilen hücrenin içeriği hücrede görüntülenmek yerine bir araç ucu olarak gösterildiğinden, olay yükseltilmez.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3.1

#### <a name="recommended-action"></a>Önerilen eylem

Düzenleme modundayken <xref:System.Windows.Forms.DataGridView.CellFormatting> <xref:System.Windows.Forms.DataGridView> olaya bağlı olan herhangi bir kodu yeniden düzenleme.

#### <a name="category"></a>Kategori

Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

None

<!-- 

### Affected APIs

Not detectable via API analysis.

-->
