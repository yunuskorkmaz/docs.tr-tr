---
title: Varsayılan klavye ve fare Windows Forms DataGridView denetiminde işleme
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
ms.openlocfilehash: b0ed468fe7d38fbeda90d5347338bce14059b730
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control"></a>Varsayılan klavye ve fare Windows Forms DataGridView denetiminde işleme

Aşağıdaki tablolar ile kullanıcıların nasıl etkileşim kurabileceğine açıklamaktadır <xref:System.Windows.Forms.DataGridView> denetim klavye ve fare aracılığıyla.  
  
> [!NOTE]
>  Klavye davranışını özelleştirmek için standart klavye olayları gibi işleyebilirsiniz <xref:System.Windows.Forms.Control.KeyDown>. Düzenleme modunda, ancak, barındırılan düzenleme denetimi klavye girişi alır ve klavye olaylarının için gerçekleşmez <xref:System.Windows.Forms.DataGridView> denetim. Düzenleme denetim olayları işlemek için işleyicileri düzenleme denetiminde ekleme bir <xref:System.Windows.Forms.DataGridView.EditingControlShowing> olay işleyicisi. Alternatif olarak, klavye davranışını özelleştirebilirsiniz bir <xref:System.Windows.Forms.DataGridView> kılarak subclass <xref:System.Windows.Forms.DataGridView.ProcessDialogKey%2A> ve <xref:System.Windows.Forms.DataGridView.ProcessDataGridViewKey%2A> yöntemleri.  
  
## <a name="default-keyboard-handling"></a>Varsayılan klavye işleme  
  
### <a name="basic-navigation-and-entry-keys"></a>Temel gezinme ve giriş tuşlar  
  
|Anahtar veya anahtar birleşimi|Açıklama|  
|----------------------------|-----------------|  
|AŞAĞI OK|Odağı hücrede doğrudan geçerli hücreyi taşır. Odağı son satırdaysa hiçbir şey yapmaz.|  
|SOL OK|Önceki hücre satırda odağı taşır. Odağı sıradaki ilk hücrenin ise, hiçbir şey yapmaz.|  
|SAĞ OK|Odağı satırda sonraki hücreye taşır. Odağı satırın son hücresinde ise, hiçbir şey yapmaz.|  
|YUKARI OK|Odağı doğrudan geçerli hücrenin üstündeki taşır. Odağı ilk satırda ise, hiçbir şey yapmaz.|  
|GİRİŞ|Geçerli satırda ilk hücrenin odağı taşır.|  
|END|Geçerli satırda son hücreye odağı taşır.|  
|PAGE DOWN|Denetim aşağı tam olarak görüntülenen satırların sayısı ile birlikte kayar. Odağı sütunlar değiştirmeden son tam olarak görüntülenen satır taşır.|  
|PAGE UP|Denetim yukarı tam olarak görüntülenen satırların sayısı ile birlikte kayar. Sütunları değiştirmeden ilk görüntülenen satır odağı taşır.|  
|TAB|Varsa <xref:System.Windows.Forms.DataGridView.StandardTab%2A> özellik değeri `false`, geçerli satırda sonraki hücrenin odağı taşır. Odağı satırın son hücreye ise, ilk hücrenin sonraki satırda odağı taşır. Odağı denetimi son hücresinde ise, odağı üst kapsayıcı sekme sırasını bir sonraki denetime taşır.<br /><br /> Varsa <xref:System.Windows.Forms.DataGridView.StandardTab%2A> özellik değeri `true`, üst öğe kapsayıcısı sekme sırasını bir sonraki denetime odağı taşır.|  
|SHIFT+TAB|Varsa <xref:System.Windows.Forms.DataGridView.StandardTab%2A> özellik değeri `false`, önceki hücrenin geçerli satırda odağı taşır. Odağı satırın ilk hücreye ise, önceki satırdaki son hücreye odağı taşır. Odağı denetimi ilk hücresinde ise, üst öğe kapsayıcısı sekme sırasını, önceki denetimi odağı taşır.<br /><br /> Varsa <xref:System.Windows.Forms.DataGridView.StandardTab%2A> özellik değeri `true`, üst öğe kapsayıcısı sekme sırasını, önceki denetimi odağı taşır.|  
|CTRL + SEKME|Varsa <xref:System.Windows.Forms.DataGridView.StandardTab%2A> özellik değeri `false`, üst öğe kapsayıcısı sekme sırasını bir sonraki denetime odağı taşır.<br /><br /> Varsa <xref:System.Windows.Forms.DataGridView.StandardTab%2A> özellik değeri `true`, geçerli satırda sonraki hücrenin odağı taşır. Odağı satırın son hücreye ise, ilk hücrenin sonraki satırda odağı taşır. Odağı denetimi son hücresinde ise, odağı üst kapsayıcı sekme sırasını bir sonraki denetime taşır.|  
|CTRL + SHIFT + SEKME|Varsa <xref:System.Windows.Forms.DataGridView.StandardTab%2A> özellik değeri `false`, üst öğe kapsayıcısı sekme sırasını, önceki denetimi odağı taşır.<br /><br /> Varsa <xref:System.Windows.Forms.DataGridView.StandardTab%2A> özellik değeri `true`, önceki hücrenin geçerli satırda odağı taşır. Odağı satırın ilk hücreye ise, önceki satırdaki son hücreye odağı taşır. Odağı denetimi ilk hücresinde ise, üst öğe kapsayıcısı sekme sırasını, önceki denetimi odağı taşır.|  
|CTRL + OK|Ok yönünü en uzak hücreye odağı taşır.|  
|CTRL + HOME|Odağı denetimi ilk hücreye taşır.|  
|CTRL + END|Odağı denetimi son hücreye taşır.|  
|CTRL + PAGE DOWN/YUKARI|PAGE DOWN veya PAGE UP aynıdır.|  
|F2|Geçerli hücreyi hücre düzenleme moduna koyar <xref:System.Windows.Forms.DataGridView.EditMode%2A> özellik değeri <xref:System.Windows.Forms.DataGridViewEditMode.EditOnF2> veya <xref:System.Windows.Forms.DataGridViewEditMode.EditOnKeystrokeOrF2>.|
|F3|Varsa geçerli sütun sıralar <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> özellik değeri <xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>. Geçerli sütun başlığını tıklatarak ile aynıdır. .NET Framework 4.7.2 sürümünden itibaren kullanılabilir. Bu özelliği etkinleştirmek için uygulamaları .NET Framework 4.7.2 veya sonraki sürümlerini hedefleyen veya açıkça AppContext anahtarları kullanılarak erişilebilirlik artışlarını opt gerekir.|  
|F4|Geçerli hücreyi ise bir <xref:System.Windows.Forms.DataGridViewComboBoxCell>, hücre düzenleme moduna geçer ve aşağı açılan listede görüntülenir.|  
|ALT + YUKARI/AŞAĞI OK|Geçerli hücreyi ise bir <xref:System.Windows.Forms.DataGridViewComboBoxCell>, hücre düzenleme moduna geçer ve aşağı açılan listede görüntülenir.|  
|ALANI|Geçerli hücreyi ise bir <xref:System.Windows.Forms.DataGridViewButtonCell>, <xref:System.Windows.Forms.DataGridViewLinkCell>, veya <xref:System.Windows.Forms.DataGridViewCheckBoxCell>, başlatır <xref:System.Windows.Forms.DataGridView.CellClick> ve <xref:System.Windows.Forms.DataGridView.CellContentClick> olaylar. Geçerli hücreyi ise bir <xref:System.Windows.Forms.DataGridViewButtonCell>, ayrıca düğmesine basarsa. Geçerli hücreyi ise bir <xref:System.Windows.Forms.DataGridViewCheckBoxCell>, ayrıca onay durumunu değiştirir.|  
|ENTER|Geçerli hücreyi ve satır değişiklikleri kaydeder ve bir hücrede doğrudan geçerli hücreyi odağı taşır. Odağı son satırdaysa odağı taşımadan değişiklikleri kaydeder.|  
|ESC|Denetim düzenleme modunda ise düzenlemeyi iptal eder. Denetim düzenleme modunda değilse, Denetim düzenleme destekleyen bir veri kaynağına bağlıysa geçerli satıra yapılan değişiklikleri geri döner veya sanal modu satır düzeyi yürütme kapsamıyla uygulanmıştır.|  
|GERİ AL|Bir hücre düzenleme ekleme noktasını önceki karakteri siler.|  
|DELETE|Karakter, bir hücre düzenleme yaparken sonra ekleme noktasını siler.|  
|CTRL + ENTER|Herhangi bir değişiklik odağı taşımadan geçerli hücreyi kaydeder. Ayrıca ile denetimi düzenleme veya sanal modunu destekleyen bir veri kaynağına bağlıysa geçerli satır yapılan değişiklikler uygulandıktan işlemeleri satır yürütme kapsam düzeyi.|  
|CTRL + 0|Girer bir <xref:System.DBNull.Value?displayProperty=nameWithType> hücre düzenlenebiliyorsa geçerli hücreye değer. Varsayılan olarak, görüntüleme değeri için bir <xref:System.DBNull> hücre değerdir değerini <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> özelliği <xref:System.Windows.Forms.DataGridViewCellStyle> geçerli hücreyi için etkin.|  
  
### <a name="selection-keys"></a>Seçim anahtarları

 Varsa <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> özelliği ayarlanmış `false` ve <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> özelliği ayarlanmış <xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>, geçerli hücreyi Gezinti anahtarları kullanılarak değiştirildiğinde, yeni hücreye seçimi değişir. Kaydırma, CTRL ve ALT anahtarları bu davranışını etkilemez.  
  
 Varsa <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> ayarlanır <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> veya <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, aynı davranış gerçekleşir, ancak aşağıdaki eklemelerle.  
  
|Anahtar veya anahtar birleşimi|Açıklama|  
|----------------------------|-----------------|  
|SHIFT + ARA ÇUBUĞU|Tam satır veya sütun (aynı satır veya sütun başlığını tıklatarak) seçer.|  
|Gezinti (tuş oku, sayfa yukarı/aşağı, giriş, bitiş)|Tam satır veya sütun seçiliyse, yeni bir satır veya sütun için geçerli hücreyi değiştirme seçimi tam ve yeni satır veya sütun (bağlı olarak seçim modu) taşır.|  
  
 Varsa <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> ayarlanır `false` ve <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> ayarlanır <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> veya <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, klavyeyi kullanarak yeni bir satır veya sütun için geçerli hücreyi değiştirilmesi taşır seçimi tam ve yeni satır veya sütun. Kaydırma, CTRL ve ALT anahtarları bu davranışını etkilemez.  
  
 Varsa <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> ayarlanır `true`Gezinti davranış değişmez ancak SHIFT (CTRL + SHIFT dahil) basarak klavye ile gezinme çok hücre seçimi değiştirir. Gezinti başlamadan önce denetim geçerli hücreyi bağlantı hücre olarak işaretler. SHIFT basılı tutarken gittiğinizde seçimi Hücre tutturma geçerli hücreyi arasındaki tüm hücreleri içerir. Diğer denetim hücrelerde zaten seçili ancak klavye gezinti geçici olarak bunları Hücre tutturma ve geçerli hücreyi arasında koyar bunlar seçilmemiş dönüşebilir seçili kalır.  
  
 Varsa <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> ayarlanır `true` ve <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> ayarlanır <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> veya <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, geçerli hücreyi ve Hücre tutturma davranışını aynıdır, ancak yalnızca tam satır veya sütun haline seçili veya seçilmemiş.  
  
## <a name="default-mouse-handling"></a>Varsayılan fare işleme
  
### <a name="basic-mouse-handling"></a>Temel Fare işleme
  
> [!NOTE]
>  Her zaman bir hücre sol fare düğmesini tıklatarak geçerli hücreyi değiştirir. Biri kullanılabilir olduğunda bir hücre farenin sağ düğmesiyle tıklatarak bir kısayol menüsü açılır.  
  
|Fare eylemi|Açıklama|  
|------------------|-----------------|  
|Sol fare düğmesini basılı|Geçerli hücreyi tıklatılan hücre oluşturur ve başlatır <xref:System.Windows.Forms.DataGridView.CellMouseDown?displayProperty=nameWithType> olay.|  
|Sol fare düğmesini|Başlatır <xref:System.Windows.Forms.DataGridView.CellMouseUp?displayProperty=nameWithType> olayı|  
|Sol fare düğmesini tıklatın|Başlatır <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> ve <xref:System.Windows.Forms.DataGridView.CellMouseClick?displayProperty=nameWithType> olayları|  
|Sol fare düğmesini basılı ve sütun üst bilgi hücresini üzerinde sürükleyin|Varsa <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> özelliği `true`, sütun taşır, böylece yeni bir konuma bırakılabilir.|  
  
### <a name="mouse-selection"></a>Fare seçimi

 Orta fare düğmesini veya fare tekerleği ile ilişkili hiçbir seçim davranıştır.  
  
 Varsa <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> özelliği ayarlanmış `false` ve <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> özelliği ayarlanmış <xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>, aşağıdaki davranış oluşur.  
  
|Fare eylemi|Açıklama|  
|------------------|-----------------|  
|Sol fare düğmesini tıklatın|Kullanıcı bir hücre tıklarsa yalnızca geçerli hücreyi seçer. Kullanıcı bir satır veya sütun üstbilgisini tıklarsa seçimi davranışı yok.|  
|Farenin sağ düğmesiyle tıklatın|Varsa bir kısayol menüsü görüntüler.|  
  
 Aynı davranış zaman <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> ayarlanır <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> veya <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, seçim modunu bağlı olarak bir satır veya sütun üstbilgisini tıklatmak tam satır veya sütun seçin ve satır veya sütun ilk hücreye geçerli hücreyi ayarlama dışında.  
  
 Varsa <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> ayarlanır <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> veya <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, herhangi bir satır veya sütun bir hücreyi tıklatarak seçebilir tam satır veya sütun.  
  
 Varsa <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> ayarlanır `true`, CTRL veya SHIFT tuşuna basarak sırasında bir hücre tıklatıldığında çok hücre seçimi değiştirir.  
  
 CTRL tuşunu basılı tutun bir hücreyi tıklatın, diğer tüm hücreleri geçerli seçim durumlarına tutarken hücre seçimi durumu değişir.  
  
 Bir hücrenin veya hücre bir dizi SHIFT basılı tutarken tıklattığınızda Seçimi geçerli hücreyi ilk tıklatma önce geçerli hücreyi konumunda bulunan bir bağlantı hücre arasındaki tüm hücreleri içerir. Birden çok hücreyi işaretçi sürükleyip Hücre tutturma sürükleme işleminin başında tıklanan hücre olur. Geçerli hücreyi, ancak bağlantı hücre SHIFT tuşuna basarak sırasında sonraki tıklama değiştirin. Diğer denetim hücrelerde zaten seçildi, ancak fare Gezinti geçici olarak bunları Hücre tutturma ve geçerli hücreyi arasında koyar bunlar seçilmemiş dönüşebilir seçili kalır.  
  
 Varsa <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> ayarlanır `true` ve <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> ayarlanır <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> veya <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, SHIFT basılı tutarken (seçim modu) bağlı olarak bir satır veya sütun başlığını tıklatarak değiştirirseniz varolan bir seçimi tam satır veya sütun bu tür bir Seçim bulunmaktadır. Aksi takdirde, bu seçimi kaldırın ve yeni bir seçim tam satır veya sütun başlatın. CTRL tuşunu basılı tutun bir satır veya sütun başlığını tıklatarak, ancak ekleyip tıklatılan satır veya sütun Geçerli seçimdeki Aksi takdirde geçerli seçim değiştirmeden kaldıracaktır.  
  
 Varsa <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> ayarlanır `true` ve <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> ayarlanır <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> veya <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, SHIFT veya CTRL tuşuna basarak çalışırken bir hücreyi tıklatın, yalnızca tam satır dışında aynı şekilde davranır ve sütunları etkilenmedi.  
  
## <a name="see-also"></a>Ayrıca bkz.

<xref:System.Windows.Forms.DataGridView>  
 [DataGridView Denetimi](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
