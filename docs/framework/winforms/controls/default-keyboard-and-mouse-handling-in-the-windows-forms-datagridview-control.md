---
title: Windows Forms DataGridView denetiminde varsayılan klavye ve fare işleme
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
ms.openlocfilehash: 97b8c8c3e418586bbc0053c358a2924484115a26
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969138"
---
# <a name="default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView denetiminde varsayılan klavye ve fare işleme

Aşağıdaki tablolarda, kullanıcıların klavye ve fare aracılığıyla <xref:System.Windows.Forms.DataGridView> denetimle nasıl etkileşime girebileceği açıklanır.  
  
> [!NOTE]
> Klavye davranışını özelleştirmek için gibi standart klavye olaylarını <xref:System.Windows.Forms.Control.KeyDown>işleyebilirsiniz. Ancak, düzenleme modunda, barındırılan düzenleme denetimi klavye girişini alır ve klavye olayları <xref:System.Windows.Forms.DataGridView> denetim için oluşmaz. Denetim olaylarını işlemek için işleyicileri bir <xref:System.Windows.Forms.DataGridView.EditingControlShowing> olay işleyicisindeki düzen denetimine ekleyin. Alternatif olarak, <xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.DataGridView.ProcessDialogKey%2A> ve <xref:System.Windows.Forms.DataGridView.ProcessDataGridViewKey%2A> yöntemlerini geçersiz kılarak bir alt sınıfta klavye davranışını özelleştirebilirsiniz.  
  
## <a name="default-keyboard-handling"></a>Varsayılan klavye işleme  
  
### <a name="basic-navigation-and-entry-keys"></a>Temel gezinti ve giriş anahtarları  
  
|Anahtar veya anahtar birleşimi|Açıklama|  
|----------------------------|-----------------|  
|AŞAĞI OK|Odağı geçerli hücrenin hemen altındaki hücreye taşınır. Odak son satırdaysa, hiçbir şey yapmaz.|  
|SOL OK|Odağı satırdaki bir önceki hücreye kaydırır. Odak satırdaki ilk hücredeyse hiçbir şey yapmaz.|  
|SAĞ OK|Odağı satırdaki sonraki hücreye kaydırır. Odak satırdaki son hücredeyse hiçbir şey yapmaz.|  
|YUKARI OK|Odağı doğrudan geçerli hücrenin üzerindeki hücreye kaydırır. Odak ilk satırdaysa, hiçbir şey yapmaz.|  
|SAYFA|Odağı geçerli satırdaki ilk hücreye kaydırır.|  
|END|Odağı geçerli satırdaki son hücreye kaydırır.|  
|SAYFA AŞAĞI|Denetimi tam olarak görüntülenen satır sayısına göre aşağı kaydırır. Odağı sütunları değiştirmeden son tam olarak görüntülenmiş satıra kaydırır.|  
|SAYFA YUKARI|Denetimi tam olarak görüntülenen satır sayısına göre yukarı kaydırır. Sütunları değiştirmeden, odağı ilk görüntülenmiş satıra kaydırır.|  
|TAB|Özellik değeri ise `false`, odağı geçerli satırdaki sonraki hücreye taşınır. <xref:System.Windows.Forms.DataGridView.StandardTab%2A> Odak satırın son hücresinde zaten yer alıyorsa, odağı sonraki satırdaki ilk hücreye taşınır. Odak denetimin son hücresdeyse, odağı üst kapsayıcının sekme düzeninde sonraki denetime taşıtır.<br /><br /> Özellik değeri ise `true`, üst kapsayıcının sekme düzeninde odağı sonraki denetime taşınır. <xref:System.Windows.Forms.DataGridView.StandardTab%2A>|  
|SHIFT+TAB|Özellik değeri ise `false`, odağı geçerli satırdaki önceki hücreye taşınır. <xref:System.Windows.Forms.DataGridView.StandardTab%2A> Odak satırın ilk hücresinde zaten varsa, odağı önceki satırdaki son hücreye taşınır. Odak denetimin ilk hücresdeyse, odağı üst kapsayıcının sekme düzeninde önceki denetime taşıtır.<br /><br /> Özellik değeri ise `true`, üst kapsayıcının sekme düzeninde odağı önceki denetime taşınır. <xref:System.Windows.Forms.DataGridView.StandardTab%2A>|  
|CTRL + SEKME|Özellik değeri ise `false`, üst kapsayıcının sekme düzeninde odağı sonraki denetime taşınır. <xref:System.Windows.Forms.DataGridView.StandardTab%2A><br /><br /> Özellik değeri ise `true`, odağı geçerli satırdaki sonraki hücreye taşınır. <xref:System.Windows.Forms.DataGridView.StandardTab%2A> Odak satırın son hücresinde zaten yer alıyorsa, odağı sonraki satırdaki ilk hücreye taşınır. Odak denetimin son hücresdeyse, odağı üst kapsayıcının sekme düzeninde sonraki denetime taşıtır.|  
|CTRL + SHIFT + TAB|Özellik değeri ise `false`, üst kapsayıcının sekme düzeninde odağı önceki denetime taşınır. <xref:System.Windows.Forms.DataGridView.StandardTab%2A><br /><br /> Özellik değeri ise `true`, odağı geçerli satırdaki önceki hücreye taşınır. <xref:System.Windows.Forms.DataGridView.StandardTab%2A> Odak satırın ilk hücresinde zaten varsa, odağı önceki satırdaki son hücreye taşınır. Odak denetimin ilk hücresdeyse, odağı üst kapsayıcının sekme düzeninde önceki denetime taşıtır.|  
|CTRL + OK|Odağı, okun yönündeki en uzak hücreye taşınır.|  
|CTRL + HOME|Odağı denetimdeki ilk hücreye taşınır.|  
|CTRL + END|Odağı denetimdeki son hücreye kaydırır.|  
|CTRL + PAGE AŞAĞI/YUKARI|SAYFA aşağı veya sayfa yukarı ile aynıdır.|  
|F2|<xref:System.Windows.Forms.DataGridView.EditMode%2A> Özellik değeri <xref:System.Windows.Forms.DataGridViewEditMode.EditOnF2> veya<xref:System.Windows.Forms.DataGridViewEditMode.EditOnKeystrokeOrF2>ise, geçerli hücreyi hücre düzenleme moduna geçirir.|
|F3|<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> Özellik<xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>değeri ise geçerli sütunu sıralar. Geçerli sütun başlığına tıklanmakla aynıdır. .NET Framework 4.7.2 bu yana kullanılabilir. Bu özelliği etkinleştirmek için, uygulamaların .NET Framework 4.7.2 veya üzeri sürümlerini hedeflemesi veya AppContext anahtarlarını kullanarak açıkça erişilebilirlik geliştirmelerini kabul etmelidir.|  
|F4|Geçerli hücre bir <xref:System.Windows.Forms.DataGridViewComboBoxCell>ise, hücreyi düzenleme moduna geçirir ve açılan listeyi görüntüler.|  
|ALT + YUKARI/AŞAĞI OK|Geçerli hücre bir <xref:System.Windows.Forms.DataGridViewComboBoxCell>ise, hücreyi düzenleme moduna geçirir ve açılan listeyi görüntüler.|  
|BOŞLU|Geçerli <xref:System.Windows.Forms.DataGridViewButtonCell>hücre bir, <xref:System.Windows.Forms.DataGridViewCheckBoxCell> <xref:System.Windows.Forms.DataGridView.CellClick> veya ise, ve<xref:System.Windows.Forms.DataGridView.CellContentClick> olaylarını oluşturur. <xref:System.Windows.Forms.DataGridViewLinkCell> Geçerli hücre bir <xref:System.Windows.Forms.DataGridViewButtonCell>ise düğmeye de basar. Geçerli hücre bir <xref:System.Windows.Forms.DataGridViewCheckBoxCell>ise, denetim durumunu da değiştirir.|  
|ENTER|Geçerli hücrede ve satırda yapılan tüm değişiklikleri kaydeder ve odağı doğrudan geçerli hücrenin altındaki hücreye hareket ettirir. Odak son satırdaysa, odağı taşımadan tüm değişiklikleri kaydeder.|  
|LARINA|Denetim düzenleme modundaysa, düzenleme işlemini iptal eder. Denetim düzenleme modunda değilse, denetim, düzenleme veya sanal modu destekleyen bir veri kaynağına bağlıysa, satır düzeyi kayıt kapsamıyla uygulanmış olan tüm değişiklikleri geri döndürür.|  
|GERI AL|Bir hücreyi düzenlediğinizde ekleme noktasının öncesindeki karakteri siler.|  
|DELETE|Bir hücreyi düzenlediğinizde ekleme noktasının ardından karakteri siler.|  
|CTRL + ENTER|Odağı taşımadan geçerli hücrede yapılan tüm değişiklikleri kaydeder. Ayrıca Denetim, satır düzeyi işleme kapsamıyla, denetimin veya sanal modun desteklediği bir veri kaynağına bağlıysa geçerli satırda yapılan değişiklikleri de kaydeder.|  
|CTRL + 0|Hücre düzenlenebildiği takdirde, geçerli hücreye bir <xref:System.DBNull.Value?displayProperty=nameWithType> değer girer. Varsayılan olarak, bir <xref:System.DBNull> hücre değeri için görüntüleme değeri, geçerli hücre için etkin olan <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> özelliğinin <xref:System.Windows.Forms.DataGridViewCellStyle> değeridir.|  
  
### <a name="selection-keys"></a>Seçim tuşları

 Özelliği olarak `false` ayarlanmışsa ve<xref:System.Windows.Forms.DataGridView.SelectionMode%2A> özelliği olarak<xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>ayarlanırsa, gezinti tuşlarını kullanarak geçerli hücreyi değiştirmek seçimi yeni hücre olarak değiştirir. <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> SHIFT, CTRL ve ALT tuşları bu davranışı etkilemez.  
  
 Ya <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> da olarak ayarlandıysa, aynı davranış oluşur ancak aşağıdaki eklemelerle birlikte. <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>  
  
|Anahtar veya anahtar birleşimi|Açıklama|  
|----------------------------|-----------------|  
|SHIFT + ARA ÇUBUĞU|Tam satırı veya sütunu seçer (satır veya sütun başlığına tıklanması ile aynıdır).|  
|Gezinti tuşu (ok tuşu, sayfa yukarı/aşağı, GIRIŞ, BITIŞ)|Tam bir satır veya sütun seçilirse, geçerli hücreyi yeni bir satır veya sütun olarak değiştirmek seçimi tam yeni satıra veya sütuna (seçim moduna bağlı olarak) kaydırır.|  
  
 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> , Olarak `false` ayarlanır ve <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> veya olarak<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>ayarlanırsa, klavye kullanarak geçerli hücreyi yeni bir satır veya sütun olarak değiştirmek seçimi tam yeni satıra veya sütuna taşıdır. <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> SHIFT, CTRL ve ALT tuşları bu davranışı etkilemez.  
  
 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> Olarak`true`ayarlanırsa, gezinti davranışı değişmez ancak SHIFT (CTRL + SHIFT dahil) tuşlarına basıldığında klavyeyle gezinmek çok hücreli bir seçimi değiştirecektir. Gezinme başlamadan önce, Denetim geçerli hücreyi bir tutturucu hücresi olarak işaretler. SHIFT tuşuna basarak gittiğinizde, seçim, yer işareti hücresi ve geçerli hücre arasındaki tüm hücreleri içerir. Denetimdeki diğer hücreler zaten seçildiyse seçili olmaya devam eder, ancak klavye gezintisi bunları bir bağlantı hücresi ve geçerli hücre arasına geçici olarak yerleştiriyorsa, bunlar seçilmemiş hale gelebilir.  
  
 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> , Olarak `true` ayarlanır ve <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> veya olarak<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>ayarlanırsa, yer işareti hücresi ve geçerli hücre davranışı aynıdır, ancak yalnızca tam satırlar veya sütunlar seçili veya seçilmemiş olur. <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>  
  
## <a name="default-mouse-handling"></a>Varsayılan fare işleme
  
### <a name="basic-mouse-handling"></a>Temel fare işleme
  
> [!NOTE]
> Sol fare düğmesine sahip bir hücreye tıklamak her zaman geçerli hücreyi değiştirir. Sağ fare düğmesi ile bir hücreye tıklamak, kullanılabilir olduğunda bir kısayol menüsü açar.  
  
|Fare eylemi|Açıklama|  
|------------------|-----------------|  
|Sol fare düğmesi aşağı|Tıklanan hücreyi geçerli hücreyi yapar ve <xref:System.Windows.Forms.DataGridView.CellMouseDown?displayProperty=nameWithType> olayı başlatır.|  
|Sol fare düğmesi yukarı|<xref:System.Windows.Forms.DataGridView.CellMouseUp?displayProperty=nameWithType> Olayı başlatır|  
|Sol fare düğmesine tıklama|<xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> Ve<xref:System.Windows.Forms.DataGridView.CellMouseClick?displayProperty=nameWithType> olaylarını oluşturur|  
|Sol fare düğmesi aşağı, sütun üst bilgi hücresine sürükleyin|<xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> Özelliği ise`true`, sütunu yeni bir konuma bırakılacak şekilde taşımalıdır.|  
  
### <a name="mouse-selection"></a>Fare seçimi

 Orta fare düğmesi veya fare tekerleği ile ilişkili seçim davranışı yok.  
  
 Özelliği olarak `false` ayarlanmışsa ve<xref:System.Windows.Forms.DataGridView.SelectionMode%2A> özelliği olarak<xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>ayarlanırsa, aşağıdaki davranış oluşur. <xref:System.Windows.Forms.DataGridView.MultiSelect%2A>  
  
|Fare eylemi|Açıklama|  
|------------------|-----------------|  
|Sol fare düğmesine tıklayın|Kullanıcı bir hücreye tıkladığında yalnızca geçerli hücreyi seçer. Kullanıcı bir satır veya sütun başlığına tıkladığında seçim davranışı yoktur.|  
|Sağ fare düğmesine tıklayın|Varsa bir kısayol menüsü görüntüler.|  
  
 Aynı davranış, <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> veya <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>olarak ayarlandığında oluşur, ancak seçim moduna bağlı olarak, bir satır veya sütun başlığına tıklamak tam satırı veya sütunu seçer ve geçerli hücreyi satır veya sütundaki ilk hücreye ayarlar.  
  
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> Veya olarak<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>ayarlanırsa, bir satırdaki veya sütundaki herhangi bir hücreye tıklamak tam satır veya sütunu seçer. <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>  
  
 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> Olarak`true`ayarlanırsa, CTRL veya SHIFT tuşlarına basarak bir hücreye tıklamak çok hücreli bir seçimi değiştirecektir.  
  
 CTRL tuşuna basarak bir hücreye tıkladığınızda, diğer tüm hücreler geçerli seçim durumlarını koruurken hücre seçim durumunu değiştirir.  
  
 SHIFT tuşuna basarak bir hücreye veya hücre dizisine tıkladığınızda, seçim geçerli hücre ve ilk tıklamadan önce geçerli hücrenin konumunda bulunan bir yer işareti hücresi arasındaki tüm hücreleri içerir. İşaretçiyi birden çok hücrede tıklattığınızda ve sürüklediğinizde, yer işareti hücresi sürükleme işleminin başlangıcında tıklanan hücredir. SHIFT tuşuna basıldığında sonraki tıklama, geçerli hücreyi Değiştir, ancak tutturucu hücresi. Denetimdeki diğer hücreler zaten seçildiyse seçili olmaya devam eder, ancak fare gezintisi bunları bir bağlantı hücresi ve geçerli hücre arasına geçici olarak yerleştiriyorsa seçilmemiş olabilirler.  
  
 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> , Olarak `true` ayarlanmışsa ve <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> veya olarak<xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>ayarlanırsa (seçim moduna bağlı olarak) bir satır veya sütun başlığına tıkladığınızda (seçim moduna bağlı olarak), bu tür bir tam satır veya sütun <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> seçim var. Aksi takdirde, seçimi temizler ve tam satırlar veya sütunlar için yeni bir seçim başlatılır. Ancak CTRL tuşuna basarak bir satır veya sütun başlığına tıkladığınızda, geçerli seçimi değiştirmeden Geçerli seçimden tıklanmış satırı veya sütunu ekler veya kaldırır.  
  
 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> , <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> Olarak `true` ayarlanır ve<xref:System.Windows.Forms.DataGridView.SelectionMode%2A> ya<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>da olarak ayarlanırsa, SHIFT veya CTRL tuşlarına basıldığında yalnızca tam satırlar ve sütunlar etkilenirken, bir hücreye tıklanması aynı şekilde davranır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- [DataGridView Denetimi](datagridview-control-windows-forms.md)
