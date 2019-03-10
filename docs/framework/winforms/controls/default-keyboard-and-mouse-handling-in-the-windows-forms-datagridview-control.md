---
title: Varsayılan klavye ve fare Windows Forms DataGridView denetiminde
ms.date: 02/13/2018
helpviewer_keywords:
- data grids [Windows Forms], mouse handling
- DataGridView control [Windows Forms], navigation keys
- keyboards [Windows Forms], default handling in DataGridView control
- DataGridView control [Windows Forms], keyboard handling
- mouse [Windows Forms], default handling in DataGridView control
- DataGridView control [Windows Forms], mouse handling
- navigation keys [Windows Forms], DataGridView control
ms.assetid: 4519b928-bfc8-4e8b-bb9c-b1e76a0ca552
ms.openlocfilehash: 56585bf91a559844f15aede4519706674357a924
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708320"
---
# <a name="default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control"></a>Varsayılan klavye ve fare Windows Forms DataGridView denetiminde

Aşağıdaki tablolar ile kullanıcıların nasıl etkileşim kurabileceğine açıklamaktadır <xref:System.Windows.Forms.DataGridView> denetim klavye ve fare.  
  
> [!NOTE]
>  Klavye davranışı özelleştirmek için standart klavye olaylarını gibi işleyebilir <xref:System.Windows.Forms.Control.KeyDown>. Klavye olaylarını için gerçekleşmez ve düzenleme modunda, barındırılan düzenleme denetiminin ancak klavye girişini alır. <xref:System.Windows.Forms.DataGridView> denetimi. Düzenleme denetim olaylarını işlemek için düzenleme denetiminde İşleyicileriniz ekleme bir <xref:System.Windows.Forms.DataGridView.EditingControlShowing> olay işleyicisi. Klavye davranışı alternatif olarak, özelleştirebileceğiniz bir <xref:System.Windows.Forms.DataGridView> kılarak alt <xref:System.Windows.Forms.DataGridView.ProcessDialogKey%2A> ve <xref:System.Windows.Forms.DataGridView.ProcessDataGridViewKey%2A> yöntemleri.  
  
## <a name="default-keyboard-handling"></a>Varsayılan klavye işleme  
  
### <a name="basic-navigation-and-entry-keys"></a>Temel gezinti ve giriş anahtarları  
  
|Anahtar veya anahtar birleşimi|Açıklama|  
|----------------------------|-----------------|  
|AŞAĞI OK|Odağı geçerli hücreyi doğrudan hücrede taşır. Odağı Son satırda ise, hiçbir şey yapmaz.|  
|SOL OK|Odağı önceki hücrenin sıradaki taşır. Odağı sıradaki ilk hücrenin ise, hiçbir şey yapmaz.|  
|SAĞ OK|Odağı satır içinde sonraki hücreye taşır. Odağı satırın son hücreye ise, hiçbir şey yapmaz.|  
|YUKARI OK|Odağı geçerli hücrenin doğrudan üstündeki taşır. Odağı ilk satırda ise, hiçbir şey yapmaz.|  
|HOME|Odağı geçerli satırda ilk hücrenin taşır.|  
|END|Odağı geçerli satırda son hücreye taşır.|  
|PAGE DOWN|Tam olarak görüntülenen satırların sayısı tarafından denetimi aşağıya doğru kayar. Odağı sütunları değiştirmeden tam olarak görüntülenen son satıra taşır.|  
|AYARLAMA SAYFASI|Denetim tam olarak görüntülenen satırların sayısı yukarı kaydırır. Odağı bir sütun değiştirmeden görüntülenen ilk satıra taşır.|  
|TAB|Varsa <xref:System.Windows.Forms.DataGridView.StandardTab%2A> özellik değeri `false`, odağı geçerli satırda sonraki hücreyi taşır. Odağı satırın son hücreye ise, odak sonraki satırda ilk hücrenin taşır. Odağı denetimi son hücreye ise, odak sonraki denetime üst kapsayıcının sekme sırası taşır.<br /><br /> Varsa <xref:System.Windows.Forms.DataGridView.StandardTab%2A> özellik değeri `true`, odağı üst kapsayıcının sekme sırası sonraki denetime gider.|  
|SHIFT+TAB|Varsa <xref:System.Windows.Forms.DataGridView.StandardTab%2A> özellik değeri `false`, odağı önceki hücrenin geçerli satırda taşır. Odağı satırın ilk hücreye ise, odağı son hücreye önceki satıra taşır. Odağı, ilk hücrenin denetiminde ise, odağı üst kapsayıcının sekme sırası önceki denetimi taşır.<br /><br /> Varsa <xref:System.Windows.Forms.DataGridView.StandardTab%2A> özellik değeri `true`, odağı üst kapsayıcının sekme sırası önceki denetimi taşır.|  
|CTRL+TAB|Varsa <xref:System.Windows.Forms.DataGridView.StandardTab%2A> özellik değeri `false`, odağı üst kapsayıcının sekme sırası sonraki denetime gider.<br /><br /> Varsa <xref:System.Windows.Forms.DataGridView.StandardTab%2A> özellik değeri `true`, odağı geçerli satırda sonraki hücreyi taşır. Odağı satırın son hücreye ise, odak sonraki satırda ilk hücrenin taşır. Odağı denetimi son hücreye ise, odak sonraki denetime üst kapsayıcının sekme sırası taşır.|  
|CTRL+SHIFT+TAB|Varsa <xref:System.Windows.Forms.DataGridView.StandardTab%2A> özellik değeri `false`, odağı üst kapsayıcının sekme sırası önceki denetimi taşır.<br /><br /> Varsa <xref:System.Windows.Forms.DataGridView.StandardTab%2A> özellik değeri `true`, odağı önceki hücrenin geçerli satırda taşır. Odağı satırın ilk hücreye ise, odağı son hücreye önceki satıra taşır. Odağı, ilk hücrenin denetiminde ise, odağı üst kapsayıcının sekme sırası önceki denetimi taşır.|  
|CTRL + OK|Odağı yön okun en uzak hücresinde taşır.|  
|CTRL+HOME|Odağı denetimindeki ilk hücrenin taşır.|  
|CTRL+END|Odağı denetimi son hücreye taşır.|  
|CTRL+PAGE DOWN/UP|PAGE DOWN veya sayfa yukarı aynıdır.|  
|F2|Geçerli hücreyi hücre düzenleme moduna koyar <xref:System.Windows.Forms.DataGridView.EditMode%2A> özellik değeri <xref:System.Windows.Forms.DataGridViewEditMode.EditOnF2> veya <xref:System.Windows.Forms.DataGridViewEditMode.EditOnKeystrokeOrF2>.|
|F3|Varsa geçerli sütunun sıralar <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> özellik değeri <xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>. Bu geçerli bir sütun başlığına tıklayarak ile aynıdır. .NET Framework 4.7.2 sürümünden itibaren kullanılabilir. Bu özelliği etkinleştirmek için uygulamaları .NET Framework 4.7.2 veya sonraki sürümlerini hedefleyen veya açıkça AppContext anahtarlar kullanılarak erişilebilirlik artışlarını iyileştirilmiş gerekir.|  
|F4|Geçerli hücreyi ise bir <xref:System.Windows.Forms.DataGridViewComboBoxCell>, hücre düzenleme moduna geçirir ve aşağı açılan liste görüntüler.|  
|ALT + YUKARI/AŞAĞI OK|Geçerli hücreyi ise bir <xref:System.Windows.Forms.DataGridViewComboBoxCell>, hücre düzenleme moduna geçirir ve aşağı açılan liste görüntüler.|  
|ALANI|Geçerli hücreyi ise bir <xref:System.Windows.Forms.DataGridViewButtonCell>, <xref:System.Windows.Forms.DataGridViewLinkCell>, veya <xref:System.Windows.Forms.DataGridViewCheckBoxCell>, başlatır <xref:System.Windows.Forms.DataGridView.CellClick> ve <xref:System.Windows.Forms.DataGridView.CellContentClick> olayları. Geçerli hücreyi ise bir <xref:System.Windows.Forms.DataGridViewButtonCell>, ayrıca düğmesine bastığında. Geçerli hücreyi ise bir <xref:System.Windows.Forms.DataGridViewCheckBoxCell>, ayrıca onay durumunu değiştirir.|  
|ENTER|Geçerli hücreyi ve satır değişiklikleri kaydeder ve odak geçerli hücreyi doğrudan hücrede taşır. Son satıra odağı ise odağı taşımadan değişiklikleri kaydeder.|  
|ESC|Denetim düzenleme modunda ise düzenleme iptal eder. Denetim düzenleme modunda değilse, Denetim düzenleme destekleyen bir veri kaynağına bağlıysa geçerli satıra yapılan tüm değişiklikler geri döner veya satır düzeyi kayıt kapsamı ile sanal modu uygulanmıştır.|  
|GERİ AL|Ekleme noktasını önceki karakteri bir hücre düzenleme yaparken siler.|  
|DELETE|Karakter, bir hücre düzenleme ekleme noktasından sonra siler.|  
|CTRL+ENTER|Herhangi bir değişiklik geçerli hücreyi odağı taşımadan kaydeder. Ayrıca olan denetim düzenleme ya da sanal modunu destekleyen bir veri kaynağına bağlıysa geçerli satırın herhangi bir değişiklik uygulandıktan işlemeler satır işleme kapsam düzeyi.|  
|CTRL+0|Girer bir <xref:System.DBNull.Value?displayProperty=nameWithType> hücrenin düzenlenebilir ise geçerli bir hücreye değeri. Varsayılan olarak, görüntüleme değeri için bir <xref:System.DBNull> hücre değerdir değerini <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> özelliği <xref:System.Windows.Forms.DataGridViewCellStyle> geçerli hücreyi için etkin.|  
  
### <a name="selection-keys"></a>Seçim tuşları

 Varsa <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> özelliği `false` ve <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> özelliği <xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>, gezinti tuşlarını kullanarak geçerli hücreyi değiştirmek, yeni hücreye seçimi değiştirir. Kaydırma, CTRL ve ALT tuşları, bu davranışı etkilemez.  
  
 Varsa <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> ayarlanır <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> veya <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, aynı davranış oluşur, ancak aşağıdaki eklemelerle.  
  
|Anahtar veya anahtar birleşimi|Açıklama|  
|----------------------------|-----------------|  
|SHIFT + ARA ÇUBUĞU|Tam satır veya sütun (satır veya sütun başlığına tıklayarak aynı) seçer.|  
|Gezinti tuş (ok, sayfa/Detaydan çıkma, ev, son)|Tam satır veya sütun seçiliyse, yeni bir satır veya sütun için geçerli hücreyi değiştirme tam yeni satır veya sütun (seçim modu) bağlı olarak seçimi taşır.|  
  
 Varsa <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> ayarlanır `false` ve <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> ayarlanır <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> veya <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, klavye kullanarak yeni bir satır veya sütun için geçerli hücreyi değiştirme taşır seçimi tam ve yeni satır veya sütun. Kaydırma, CTRL ve ALT tuşları, bu davranışı etkilemez.  
  
 Varsa <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> ayarlanır `true`Gezinti davranışı değişmez ancak kaydırma (CTRL + SHIFT dahil) basarak klavye ile gezinme birden çok hücre seçimi değiştirir. Gezinti başlamadan önce denetimin geçerli hücreyi bir yer işareti hücreye işaretler. SHIFT tuşuna basarak gittiğinizde, seçimi geçerli hücreyi bağlantı hücrenin arasındaki tüm hücreleri içerir. Zaten seçili halde klavye ile gezinme geçici olarak bunları geçerli hücreyi bağlantı hücre arasında yerleştirirse, seçili olmayan durdurabilir, diğer denetiminde hücrelerin seçili kalır.  
  
 Varsa <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> ayarlanır `true` ve <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> ayarlanır <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> veya <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, geçerli hücreyi ve Hücre tutturma davranışını aynıdır, ancak yalnızca tam satır veya sütun seçilmedi veya seçimi kaldırıldı.  
  
## <a name="default-mouse-handling"></a>Varsayılan fare işleme
  
### <a name="basic-mouse-handling"></a>Temel Fare işleme
  
> [!NOTE]
>  Her zaman bir hücre farenin sol düğmesine tıklayarak geçerli hücreyi değiştirir. Biri kullanılabilir olduğunda bir hücrenin sağ fare düğmesine tıklayarak bir kısayol menüsü açılır.  
  
|Fare eylemi|Açıklama|  
|------------------|-----------------|  
|Sol fare düğmesini basılı|Tıklanan hücre geçerli hücreyi yapar ve başlatır <xref:System.Windows.Forms.DataGridView.CellMouseDown?displayProperty=nameWithType> olay.|  
|Sol fare düğmesine ayarlama|Başlatır <xref:System.Windows.Forms.DataGridView.CellMouseUp?displayProperty=nameWithType> olay|  
|Sol fare düğmesine tıklayın|Başlatır <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> ve <xref:System.Windows.Forms.DataGridView.CellMouseClick?displayProperty=nameWithType> olayları|  
|Sol fare düğmesini basılı ve sütun başlık hücresindeki sürükleyin|Varsa <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> özelliği `true`, böylece yeni bir konuma bırakılabilir sütun taşınır.|  
  
### <a name="mouse-selection"></a>Fare seçimi

 Orta fare düğmesine veya fare tekerleğini ile ilişkili hiçbir seçimi davranıştır.  
  
 Varsa <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> özelliği `false` ve <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> özelliği <xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>, aşağıdaki davranış oluşur.  
  
|Fare eylemi|Açıklama|  
|------------------|-----------------|  
|Sol fare düğmesine tıklayın|Kullanıcı bir hücreye tıklarsa yalnızca geçerli hücreyi seçer. Kullanıcı bir satır veya sütun üstbilgisini tıklarsa seçim davranışı yok.|  
|Sağ fare düğmesine tıklayın|Varsa bir kısayol menü görüntüler.|  
  
 Aynı davranış olduğunda <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> ayarlanır <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> veya <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, seçim moduna bağlı olarak bir satır veya sütun üstbilgisini tıklatmak tam satır veya sütun seçin ve satır veya sütunun ilk hücreye geçerli hücreyi ayarlama hariç.  
  
 Varsa <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> ayarlanır <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> veya <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, herhangi bir satır veya sütun hücresinde tıklayarak seçebilir tam satır veya sütun.  
  
 Varsa <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> ayarlanır `true`, CTRL ya da SHIFT basılı tutarak bir hücreye tıklayıp birden çok hücre seçimi değiştirir.  
  
 CTRL tuşunu basılı tutun bir hücreyi tıklatın, diğer tüm hücreler geçerli seçimi durumlarına sahip hücrenin seçimi durumunu değiştirir.  
  
 SHIFT tuşuna basarak bir hücreyi veya hücre bir dizi tıkladığınızda tüm hücreler geçerli hücreyi ve ilk tıklama önce geçerli hücrenin bir konumda yer alan bir yer işareti hücre arasında seçim içerir. Tıklayın ve işaretçiyi arasında birden çok hücre sürükleyin, yer işareti hücrenin sürükleme işleminin başında tıklanan hücre olur. Geçerli hücreyi ancak bağlantı hücre sonraki tıklama, SHIFT tuşuna basılı değiştirin. Zaten seçili halde fare gezinme geçici olarak bunları geçerli hücreyi bağlantı hücre arasında yerleştirirse, seçili olmayan durdurabilir, diğer denetiminde hücrelerin seçili kalır.  
  
 Varsa <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> ayarlanır `true` ve <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> ayarlanır <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> veya <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, SHIFT tuşuna basarak (seçim modu) bağlı olarak bir satır veya sütun başlığını tıklatarak Değiştir tam satır veya sütun var olan bir seçim Eğer böyle bir Seçim yok. Aksi takdirde, bu seçimi temizleyin ve tam satır veya sütun yeni bir seçim Başlat. CTRL tuşunu basılı tutun bir satır veya sütun başlığını tıklatarak ancak ekler veya tıklanan satır veya sütun geçerli seçim yoksa geçerli seçimi değiştirmeden çıkarır.  
  
 Varsa <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> ayarlanır `true` ve <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> ayarlanır <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> veya <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>sütunları etkilenen ve SHIFT veya CTRL tuşuna basarak çalışırken bir hücreye tıklayıp, yalnızca tam satır dışında aynı şekilde davranır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- [DataGridView Denetimi](datagridview-control-windows-forms.md)
