---
title: DataGridView denetiminde varsayılan klavye ve fare işleme
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
ms.openlocfilehash: 36defff02450b40265c9b6801380cab78eabe5f3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746123"
---
# <a name="default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView denetiminde varsayılan klavye ve fare işleme

Aşağıdaki tablolarda, kullanıcıların klavye ve fare aracılığıyla <xref:System.Windows.Forms.DataGridView> denetimiyle nasıl etkileşime girebileceği açıklanır.  
  
> [!NOTE]
> Klavye davranışını özelleştirmek için, <xref:System.Windows.Forms.Control.KeyDown>gibi standart klavye olaylarını işleyebilirsiniz. Ancak, düzenleme modunda, barındırılan düzenleme denetimi klavye girişini alır ve <xref:System.Windows.Forms.DataGridView> denetimi için klavye olayları oluşmaz. Denetim olaylarını işlemek için işleyicileri bir <xref:System.Windows.Forms.DataGridView.EditingControlShowing> olay işleyicisindeki düzen denetimine iliştirin. Alternatif olarak, <xref:System.Windows.Forms.DataGridView.ProcessDialogKey%2A> ve <xref:System.Windows.Forms.DataGridView.ProcessDataGridViewKey%2A> yöntemlerini geçersiz kılarak <xref:System.Windows.Forms.DataGridView> bir alt sınıfta klavye davranışını özelleştirebilirsiniz.  
  
## <a name="default-keyboard-handling"></a>Varsayılan klavye işleme  
  
### <a name="basic-navigation-and-entry-keys"></a>Temel gezinti ve giriş anahtarları  
  
|Anahtar veya anahtar birleşimi|Açıklama|  
|----------------------------|-----------------|  
|AŞAĞı OK|Odağı geçerli hücrenin hemen altındaki hücreye taşınır. Odak son satırdaysa, hiçbir şey yapmaz.|  
|SOL OK|Odağı satırdaki bir önceki hücreye kaydırır. Odak satırdaki ilk hücredeyse hiçbir şey yapmaz.|  
|SAĞ OK|Odağı satırdaki sonraki hücreye kaydırır. Odak satırdaki son hücredeyse hiçbir şey yapmaz.|  
|YUKARı OK|Odağı doğrudan geçerli hücrenin üzerindeki hücreye kaydırır. Odak ilk satırdaysa, hiçbir şey yapmaz.|  
|SAYFA|Odağı geçerli satırdaki ilk hücreye kaydırır.|  
|END|Odağı geçerli satırdaki son hücreye kaydırır.|  
|SAYFA AŞAĞı|Denetimi tam olarak görüntülenen satır sayısına göre aşağı kaydırır. Odağı sütunları değiştirmeden son tam olarak görüntülenmiş satıra kaydırır.|  
|SAYFA YUKARı|Denetimi tam olarak görüntülenen satır sayısına göre yukarı kaydırır. Sütunları değiştirmeden, odağı ilk görüntülenmiş satıra kaydırır.|  
|TAB|<xref:System.Windows.Forms.DataGridView.StandardTab%2A> Özellik değeri `false`, odağı geçerli satırdaki sonraki hücreye taşınır. Odak satırın son hücresinde zaten yer alıyorsa, odağı sonraki satırdaki ilk hücreye taşınır. Odak denetimin son hücresdeyse, odağı üst kapsayıcının sekme düzeninde sonraki denetime taşıtır.<br /><br /> <xref:System.Windows.Forms.DataGridView.StandardTab%2A> Özellik değeri `true`ise, üst kapsayıcının sekme düzeninde odağı sonraki denetime taşınır.|  
|SHIFT+TAB|<xref:System.Windows.Forms.DataGridView.StandardTab%2A> Özellik değeri `false`, odağı geçerli satırdaki bir önceki hücreye kaydırır. Odak satırın ilk hücresinde zaten varsa, odağı önceki satırdaki son hücreye taşınır. Odak denetimin ilk hücresdeyse, odağı üst kapsayıcının sekme düzeninde önceki denetime taşıtır.<br /><br /> <xref:System.Windows.Forms.DataGridView.StandardTab%2A> Özellik değeri `true`ise, üst kapsayıcının sekme düzeninde odağı önceki denetime taşınır.|  
|CTRL+SEKME|<xref:System.Windows.Forms.DataGridView.StandardTab%2A> Özellik değeri `false`ise, üst kapsayıcının sekme düzeninde odağı sonraki denetime taşınır.<br /><br /> <xref:System.Windows.Forms.DataGridView.StandardTab%2A> Özellik değeri `true`, odağı geçerli satırdaki sonraki hücreye taşınır. Odak satırın son hücresinde zaten yer alıyorsa, odağı sonraki satırdaki ilk hücreye taşınır. Odak denetimin son hücresdeyse, odağı üst kapsayıcının sekme düzeninde sonraki denetime taşıtır.|  
|CTRL + SHIFT + TAB|<xref:System.Windows.Forms.DataGridView.StandardTab%2A> Özellik değeri `false`ise, üst kapsayıcının sekme düzeninde odağı önceki denetime taşınır.<br /><br /> <xref:System.Windows.Forms.DataGridView.StandardTab%2A> Özellik değeri `true`, odağı geçerli satırdaki bir önceki hücreye kaydırır. Odak satırın ilk hücresinde zaten varsa, odağı önceki satırdaki son hücreye taşınır. Odak denetimin ilk hücresdeyse, odağı üst kapsayıcının sekme düzeninde önceki denetime taşıtır.|  
|CTRL + ok|Odağı, okun yönündeki en uzak hücreye taşınır.|  
|CTRL + HOME|Odağı denetimdeki ilk hücreye taşınır.|  
|CTRL + END|Odağı denetimdeki son hücreye kaydırır.|  
|CTRL + PAGE AŞAĞı/YUKARı|SAYFA aşağı veya sayfa yukarı ile aynıdır.|  
|F2|<xref:System.Windows.Forms.DataGridView.EditMode%2A> Özellik değeri <xref:System.Windows.Forms.DataGridViewEditMode.EditOnF2> veya <xref:System.Windows.Forms.DataGridViewEditMode.EditOnKeystrokeOrF2>ise, geçerli hücreyi hücre düzenleme moduna geçirir.|
|F3|<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> Özellik değeri <xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>ise geçerli sütunu sıralar. Geçerli sütun başlığına tıklanmakla aynıdır. .NET Framework 4.7.2 bu yana kullanılabilir. Bu özelliği etkinleştirmek için, uygulamaların .NET Framework 4.7.2 veya üzeri sürümlerini hedeflemesi veya AppContext anahtarlarını kullanarak açıkça erişilebilirlik geliştirmelerini kabul etmelidir.|  
|F4|Geçerli hücre bir <xref:System.Windows.Forms.DataGridViewComboBoxCell>, hücreyi düzenleme moduna geçirir ve açılan listeyi görüntüler.|  
|ALT + YUKARı/AŞAĞı OK|Geçerli hücre bir <xref:System.Windows.Forms.DataGridViewComboBoxCell>, hücreyi düzenleme moduna geçirir ve açılan listeyi görüntüler.|  
|ARA ÇUBUĞU|Geçerli hücre bir <xref:System.Windows.Forms.DataGridViewButtonCell>, <xref:System.Windows.Forms.DataGridViewLinkCell>veya <xref:System.Windows.Forms.DataGridViewCheckBoxCell>ise, <xref:System.Windows.Forms.DataGridView.CellClick> ve <xref:System.Windows.Forms.DataGridView.CellContentClick> olaylarını yükseltir. Geçerli hücre bir <xref:System.Windows.Forms.DataGridViewButtonCell>ise düğmeye de basar. Geçerli hücre bir <xref:System.Windows.Forms.DataGridViewCheckBoxCell>ise, denetim durumunu da değiştirir.|  
|ENTER|Geçerli hücrede ve satırda yapılan tüm değişiklikleri kaydeder ve odağı doğrudan geçerli hücrenin altındaki hücreye hareket ettirir. Odak son satırdaysa, odağı taşımadan tüm değişiklikleri kaydeder.|  
|LARıNA|Denetim düzenleme modundaysa, düzenleme işlemini iptal eder. Denetim düzenleme modunda değilse, denetim, düzenleme veya sanal modu destekleyen bir veri kaynağına bağlıysa, satır düzeyi kayıt kapsamıyla uygulanmış olan tüm değişiklikleri geri döndürür.|  
|GERI al|Bir hücreyi düzenlediğinizde ekleme noktasının öncesindeki karakteri siler.|  
|DELETE|Bir hücreyi düzenlediğinizde ekleme noktasının ardından karakteri siler.|  
|CTRL + ENTER|Odağı taşımadan geçerli hücrede yapılan tüm değişiklikleri kaydeder. Ayrıca Denetim, satır düzeyi işleme kapsamıyla, denetimin veya sanal modun desteklediği bir veri kaynağına bağlıysa geçerli satırda yapılan değişiklikleri de kaydeder.|  
|CTRL + 0|Hücre düzenlenebildiği takdirde, geçerli hücreye bir <xref:System.DBNull.Value?displayProperty=nameWithType> değeri girer. Varsayılan olarak, bir <xref:System.DBNull> hücre değeri için görüntüleme değeri, geçerli hücre için etkin <xref:System.Windows.Forms.DataGridViewCellStyle> <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> özelliğinin değeridir.|  
  
### <a name="selection-keys"></a>Seçim tuşları

 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> özelliği `false` olarak ayarlanırsa ve <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> özelliği <xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>olarak ayarlandıysa, gezinti tuşlarını kullanarak geçerli hücreyi değiştirmek seçimi yeni hücreye değiştirir. SHIFT, CTRL ve ALT tuşları bu davranışı etkilemez.  
  
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> veya <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>olarak ayarlandıysa, aynı davranış oluşur, ancak aşağıdaki eklemelerle gerçekleşir.  
  
|Anahtar veya anahtar birleşimi|Açıklama|  
|----------------------------|-----------------|  
|SHIFT + ara çubuğu|Tam satırı veya sütunu seçer (satır veya sütun başlığına tıklanması ile aynıdır).|  
|Gezinti tuşu (ok tuşu, sayfa yukarı/aşağı, GIRIŞ, BITIŞ)|Tam bir satır veya sütun seçilirse, geçerli hücreyi yeni bir satır veya sütun olarak değiştirmek seçimi tam yeni satıra veya sütuna (seçim moduna bağlı olarak) kaydırır.|  
  
 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> `false` olarak ayarlanırsa <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> veya <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>olarak ayarlanırsa, klavyeyi kullanarak geçerli hücreyi yeni bir satır veya sütun olarak değiştirmek seçimi tam yeni satır veya sütuna taşıdır. SHIFT, CTRL ve ALT tuşları bu davranışı etkilemez.  
  
 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> `true`olarak ayarlanırsa, gezinti davranışı değişmez ancak SHIFT (CTRL + SHIFT dahil) tuşlarına basıldığında klavyeyle gezinmek çok hücreli bir seçimi değiştirecektir. Gezinme başlamadan önce, Denetim geçerli hücreyi bir tutturucu hücresi olarak işaretler. SHIFT tuşuna basarak gittiğinizde, seçim, yer işareti hücresi ve geçerli hücre arasındaki tüm hücreleri içerir. Denetimdeki diğer hücreler zaten seçildiyse seçili olmaya devam eder, ancak klavye gezintisi bunları bir bağlantı hücresi ve geçerli hücre arasına geçici olarak yerleştiriyorsa, bunlar seçilmemiş hale gelebilir.  
  
 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> `true` olarak ayarlanırsa <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> veya <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>olarak ayarlanırsa, yer işareti hücresi ve geçerli hücrenin davranışı aynıdır, ancak yalnızca tam satırlar veya sütunlar seçili veya seçilmemiş olur.  
  
## <a name="default-mouse-handling"></a>Varsayılan fare işleme
  
### <a name="basic-mouse-handling"></a>Temel fare işleme
  
> [!NOTE]
> Sol fare düğmesine sahip bir hücreye tıklamak her zaman geçerli hücreyi değiştirir. Sağ fare düğmesi ile bir hücreye tıklamak, kullanılabilir olduğunda bir kısayol menüsü açar.  
  
|Fare eylemi|Açıklama|  
|------------------|-----------------|  
|Sol fare düğmesi aşağı|Tıklanan hücreyi geçerli hücreyi yapar ve <xref:System.Windows.Forms.DataGridView.CellMouseDown?displayProperty=nameWithType> olayını yükseltir.|  
|Sol fare düğmesi yukarı|<xref:System.Windows.Forms.DataGridView.CellMouseUp?displayProperty=nameWithType> olayını başlatır|  
|Sol fare düğmesine tıklama|<xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> ve <xref:System.Windows.Forms.DataGridView.CellMouseClick?displayProperty=nameWithType> olaylarını yükseltir|  
|Sol fare düğmesi aşağı, sütun üst bilgi hücresine sürükleyin|<xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> özelliği `true`, sütunu yeni bir konuma bırakılacak şekilde taşımalıdır.|  
  
### <a name="mouse-selection"></a>Fare seçimi

 Orta fare düğmesi veya fare tekerleği ile ilişkili seçim davranışı yok.  
  
 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> özelliği `false` olarak ayarlanırsa ve <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> özelliği <xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>olarak ayarlanırsa, aşağıdaki davranış oluşur.  
  
|Fare eylemi|Açıklama|  
|------------------|-----------------|  
|Sol fare düğmesine tıklayın|Kullanıcı bir hücreye tıkladığında yalnızca geçerli hücreyi seçer. Kullanıcı bir satır veya sütun başlığına tıkladığında seçim davranışı yoktur.|  
|Sağ fare düğmesine tıklayın|Varsa bir kısayol menüsü görüntüler.|  
  
 Aynı davranış, <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> veya <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>olarak ayarlandığında oluşur, ancak seçim moduna bağlı olarak, bir satır veya sütun başlığına tıklamak tam satırı veya sütunu seçer ve geçerli hücreyi satır veya sütundaki ilk hücreye ayarlar.  
  
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> veya <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>olarak ayarlandıysa, bir satırdaki veya sütundaki herhangi bir hücreye tıklamak tam satır veya sütunu seçer.  
  
 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> `true`olarak ayarlanırsa, CTRL veya SHIFT tuşlarına basarak bir hücreye tıkladığınızda bir çok hücreli seçim değiştirilir.  
  
 CTRL tuşuna basarak bir hücreye tıkladığınızda, diğer tüm hücreler geçerli seçim durumlarını koruurken hücre seçim durumunu değiştirir.  
  
 SHIFT tuşuna basarak bir hücreye veya hücre dizisine tıkladığınızda, seçim geçerli hücre ve ilk tıklamadan önce geçerli hücrenin konumunda bulunan bir yer işareti hücresi arasındaki tüm hücreleri içerir. İşaretçiyi birden çok hücrede tıklattığınızda ve sürüklediğinizde, yer işareti hücresi sürükleme işleminin başlangıcında tıklanan hücredir. SHIFT tuşuna basıldığında sonraki tıklama, geçerli hücreyi Değiştir, ancak tutturucu hücresi. Denetimdeki diğer hücreler zaten seçildiyse seçili olmaya devam eder, ancak fare gezintisi bunları bir bağlantı hücresi ve geçerli hücre arasına geçici olarak yerleştiriyorsa seçilmemiş olabilirler.  
  
 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> `true` olarak ayarlanırsa <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> veya <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>olarak ayarlanırsa, bir satır veya sütun başlığına tıklamak (seçim moduna bağlı olarak), bu tür bir seçim varsa, SHIFT tuşuna basıldığında var olan tam satır veya sütun seçimini değiştirecek. Aksi takdirde, seçimi temizler ve tam satırlar veya sütunlar için yeni bir seçim başlatılır. Ancak CTRL tuşuna basarak bir satır veya sütun başlığına tıkladığınızda, geçerli seçimi değiştirmeden Geçerli seçimden tıklanmış satırı veya sütunu ekler veya kaldırır.  
  
 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> `true` olarak ayarlanırsa <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> veya <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>olarak ayarlanırsa, SHIFT veya CTRL tuşlarına basıldığında yalnızca tam satırlar ve sütunlar etkilenirken aynı şekilde davranır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- [DataGridView Denetimi](datagridview-control-windows-forms.md)
