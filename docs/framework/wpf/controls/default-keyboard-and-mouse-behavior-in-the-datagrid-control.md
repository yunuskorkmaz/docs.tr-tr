---
title: DataGrid Denetiminde Varsayılan Klavye ve Fare Davranışı
ms.date: 03/30/2017
helpviewer_keywords:
- DataGrid [WPF], keyboard behavior
- DataGrid [WPF], mouse behavior
- keyboard behavior [WPF], DataGrid
- mouse behavior [WPF], DataGrid
ms.assetid: 563b8854-ca39-4d97-8235-17eaa0f93c8d
ms.openlocfilehash: 559b84d3e6b5ece6c71f17e6766cac4ec14824cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="default-keyboard-and-mouse-behavior-in-the-datagrid-control"></a>DataGrid Denetiminde Varsayılan Klavye ve Fare Davranışı
Bu konuda, kullanıcıların ile nasıl etkileşim kurabileceğine açıklanmaktadır <xref:System.Windows.Controls.DataGrid> klavye ve fare kullanarak denetim.  
  
 Tipik etkileşimler <xref:System.Windows.Controls.DataGrid> gezinti, seçim ve düzenleme içerir. Seçimi davranışı tarafından etkilenir <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> ve <xref:System.Windows.Controls.DataGrid.SelectionUnit%2A> özellikleri. Bu konuda açıklanan davranışa neden varsayılan değerler <xref:System.Windows.Controls.DataGridSelectionMode.Extended?displayProperty=nameWithType> ve <xref:System.Windows.Controls.DataGridSelectionUnit.FullRow?displayProperty=nameWithType>. Bu değerlerin değiştirilmesi açıklanan farklı davranışlara neden. Bir hücre düzenleme modunda olduğunda, düzenleme denetimi standart klavye davranışını geçersiz kılabilir <xref:System.Windows.Controls.DataGrid>.  
  
## <a name="default-keyboard-behavior"></a>Varsayılan klavye davranışı  
 Aşağıdaki tabloda varsayılan klavye davranışı listelenmektedir <xref:System.Windows.Controls.DataGrid>.  
  
|Anahtar veya anahtar birleşimi|Açıklama|  
|----------------------------|-----------------|  
|AŞAĞI OK|Odağı hücrede doğrudan geçerli hücreyi taşır. Odağı son satırdaysa aşağı ok tuşuna basarak hiçbir şey yapmaz.|  
|YUKARI OK|Odağı doğrudan geçerli hücrenin üstündeki taşır. Odağı ilk satırda ise, Yukarı Ok tuşuna basarak hiçbir şey yapmaz.|  
|SOL OK|Önceki hücre satırda odağı taşır. Odağı sıradaki ilk hücrenin ise, sol ok tuşuna basarak hiçbir şey yapmaz.|  
|SAĞ OK|Odağı satırda sonraki hücreye taşır. Odağı satırın son hücresinde ise, sağ ok tuşuna basarak hiçbir şey yapmaz.|  
|GİRİŞ|Geçerli satırda ilk hücrenin odağı taşır.|  
|END|Geçerli satırda son hücreye odağı taşır.|  
|PAGE DOWN|Satır gruplandırılmaz, Denetim aşağı tam olarak görüntülenen satırların sayısı ile kayar. Odağı sütunlar değiştirmeden son tam olarak görüntülenen satır taşır.<br /><br /> Satır gruplandırılır odağı son satırında taşınır <xref:System.Windows.Controls.DataGrid> sütunları değiştirmeden.|  
|PAGE UP|Satır gruplandırılmaz, denetim tam olarak görüntülenen satırların sayısı ile yukarı kayar. Sütunları değiştirmeden ilk görüntülenen satır odağı taşır.<br /><br /> Satır gruplandırılır, ilk satırda odağı taşınır <xref:System.Windows.Controls.DataGrid> sütunları değiştirmeden.|  
|TAB|Geçerli satırda sonraki hücrenin odağı taşır. Odağı satırın son hücreye ise, ilk hücrenin sonraki satırda odağı taşır. Odağı denetimi son hücresinde ise, odağı üst kapsayıcı sekme sırasını bir sonraki denetime taşır.<br /><br /> Geçerli hücreyi düzenleme modu ve odak değiştirilmeden önce geçerli satır başında taşımak için sekme nedenler odaklanması tuşuna basarak, satır için yapılan tüm değişiklikler kaydedilmeden kullanılıyorsa.|  
|SHIFT+TAB|Geçerli satırda önceki hücrenin odağı taşır. Odağı satırın ilk hücreye ise, önceki satırdaki son hücreye odağı taşır. Odağı denetimi ilk hücresinde ise, üst öğe kapsayıcısı sekme sırasını, önceki denetimi odağı taşır.<br /><br /> Geçerli hücreyi düzenleme modu ve odak değiştirilmeden önce geçerli satır başında taşımak için sekme nedenler odaklanması tuşuna basarak, satır için yapılan tüm değişiklikler kaydedilmeden kullanılıyorsa.|  
|CTRL + AŞAĞI OK|Odağı geçerli sütun son hücreye taşır.|  
|CTRL + YUKARI OK|Odağı geçerli sütunun ilk hücreye taşır.|  
|CTRL + SAĞ OK|Geçerli satırda son hücreye odağı taşır.|  
|CTRL + SOL OK|Geçerli satırda ilk hücrenin odağı taşır.|  
|CTRL + HOME|Odağı denetimi ilk hücreye taşır.|  
|CTRL + END|Odağı denetimi son hücreye taşır.|  
|CTRL + PAGE DOWN|PAGE DOWN ile aynıdır.|  
|CTRL + PAGE UP|PAGE UP ile aynıdır.|  
|F2|Varsa <xref:System.Windows.Controls.DataGrid.IsReadOnly%2A?displayProperty=nameWithType> özelliği `false` ve <xref:System.Windows.Controls.DataGridColumn.IsReadOnly%2A?displayProperty=nameWithType> özelliği `false` geçerli sütun için geçerli hücreyi hücre düzenleme moduna geçirir.|  
|ENTER|Geçerli hücreyi ve satır değişiklikleri kaydeder ve bir hücrede doğrudan geçerli hücreyi odağı taşır. Odağı son satırdaysa odağı taşımadan değişiklikleri kaydeder.|  
|ESC|Denetim düzenleme modunda ise düzenlemeyi iptal eder ve denetimde yapılan tüm değişiklikler geri döner. Implements temel alınan veri kaynağı, <xref:System.ComponentModel.IEditableObject>, ikinci kez ESC tuşuna basarak tüm satırı için düzenleme modundan iptal eder.|  
|GERİ AL|Bir hücre düzenleme imleci önceki karakteri siler.|  
|DELETE|Karakter imleci sonra bir hücre düzenleme yaparken siler.|  
|CTRL + ENTER|Herhangi bir değişiklik odağı taşımadan geçerli hücreyi kaydeder.|  
|CTRL + A|Varsa <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> ayarlanır <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, tüm satırları seçer <xref:System.Windows.Controls.DataGrid>.|  
  
## <a name="selection-keys"></a>Seçim anahtarları  
 Varsa <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> özelliği ayarlanmış <xref:System.Windows.Controls.DataGridSelectionMode.Extended>Gezinti davranış değişmez ancak SHIFT (CTRL + SHIFT dahil) basarak klavye ile gezinme çok satır seçimi değiştirir. Gezinti başlamadan önce denetim geçerli satırda bir bağlantı satır olarak işaretler. SHIFT basılı tutarken gittiğinizde seçimi bağlantı satır ve geçerli satır arasındaki tüm satırları içerir.  
  
 Aşağıdaki seçim anahtarlarını çok satır seçimi değiştirin.  
  
-   SHIFT + AŞAĞI OK  
  
-   SHIFT + YUKARI OK  
  
-   ÜST KARAKTER + PAGE DOWN  
  
-   ÜST KARAKTER + PAGE UP  
  
-   CTRL + SHIFT + AŞAĞI OK  
  
-   CTRL + SHIFT + YUKARI OK  
  
-   CTRL + SHIFT + HOME  
  
-   CTRL + SHIFT + END  
  
## <a name="default-mouse-behavior"></a>Varsayılan fare davranışı  
 Aşağıdaki tabloda varsayılan fare davranışı listelenmektedir <xref:System.Windows.Controls.DataGrid>.  
  
|Fare eylemi|Açıklama|  
|------------------|-----------------|  
|Seçili bir satıra tıklayın|Tıklatılan satır geçerli satır ve tıklatılan hücrenin geçerli hücreyi hale getirir.|  
|Geçerli hücreyi tıklatın|Geçerli hücreyi düzenleme moduna geçirir.|  
|Sütun üst bilgi hücresini sürükleyin|Varsa <xref:System.Windows.Controls.DataGrid.CanUserReorderColumns%2A?displayProperty=nameWithType> özelliği `true` ve <xref:System.Windows.Controls.DataGridColumn.CanUserReorder%2A?displayProperty=nameWithType> özelliği `true` geçerli sütun için bir sütun taşır, böylece yeni bir konuma bırakılabilir.|  
|Sütun başlığı ayırıcı sürükleyin|Varsa <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=nameWithType> özelliği `true` ve <xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=nameWithType> özelliği `true` geçerli sütunu için sütun yeniden boyutlandırır.|  
|Sütun başlığı ayırıcı çift tıklatın|Varsa <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=nameWithType> özelliği `true` ve <xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=nameWithType> özelliği `true` otomatik boyutları geçerli sütun için sütun kullanarak <xref:System.Windows.Controls.DataGridLength.Auto%2A> boyutlandırma modunu.|  
|Bir sütun başlığını hücreyi tıklatın|Varsa <xref:System.Windows.Controls.DataGrid.CanUserSortColumns%2A?displayProperty=nameWithType> özelliği `true` ve <xref:System.Windows.Controls.DataGridColumn.CanUserSort%2A?displayProperty=nameWithType> özelliği `true` geçerli sütunu için sütun sıralar.<br /><br /> Zaten sıralanmış bir sütun başlığını tıklatarak bu sütunun sıralama yönünü tersine çevir.<br /><br /> Tıklanan sırayla birden çok sütuna göre birden çok sütun üstbilgilerini tıklatarak sıralayacağını SHIFT tuşuna basarak.|  
|CTRL + bir satıra tıklayın|Varsa <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> ayarlanır <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, bitişik olmayan birden çok satır seçimi değiştirir.<br /><br /> Satır zaten seçili ise, satır seçimini kaldırır.|  
|SHIFT + bir satıra tıklayın|Varsa <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> ayarlanır <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, bitişik çok satır seçimi değiştirir.|  
|Bir satır grubu başlığını tıklatın|Genişletir veya grup daraltır.|  
|Sol üst köşesinde Tümünü Seç düğmesini tıklatın <xref:System.Windows.Controls.DataGrid>|Varsa <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> ayarlanır <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, tüm satırları seçer <xref:System.Windows.Controls.DataGrid>.|  
  
## <a name="mouse-selection"></a>Fare seçimi  
 Varsa <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> özelliği ayarlanmış <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, CTRL veya SHIFT tuşuna basarak çalışırken bir satıra tıklayarak birden çok satır seçimi değiştirir.  
  
 CTRL tuşunu basılı tutun bir satır tıklattığınızda, diğer tüm satırlar, geçerli seçim durumları tutarken satır seçimi durumu değişir. Bitişik olmayan satırları seçmek için bunu yapabilirsiniz.  
  
 SHIFT basarak bir satır tıklattığınızda Seçimi geçerli satır tıklatın önce geçerli satır konumunda bulunan bir bağlantı satır arasındaki tüm satırları içerir. Geçerli satırda, ancak bağlantı satır SHIFT tuşuna basarak sırasında sonraki tıklama değiştirin. Bitişik satır bir aralık seçmek için bunu yapabilirsiniz.  
  
 Bitişik olmayan aralıkları bitişik satır seçmek için CTRL + SHIFT birleştirilebilir. Bunu yapmak için SHIFT kullanarak ilk aralık seçmek + daha önce açıklandığı gibi tıklayın. İlk aralıktaki satırları seçtikten sonra CTRL kullanın + sonraki aralıktaki ilk satırını seçin ve CTRL + SHIFT basılı tutarken sonraki aralığı son satırında'ye tıklayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.DataGrid>  
 <xref:System.Windows.Controls.DataGrid.SelectionMode%2A>
