---
title: DataGrid Denetiminde Varsayılan Klavye ve Fare Davranışı
ms.date: 03/30/2017
helpviewer_keywords:
- DataGrid [WPF], keyboard behavior
- DataGrid [WPF], mouse behavior
- keyboard behavior [WPF], DataGrid
- mouse behavior [WPF], DataGrid
ms.assetid: 563b8854-ca39-4d97-8235-17eaa0f93c8d
ms.openlocfilehash: 6be464ce85bd3ba91dd6e6cc810ec7d04edc0c3d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083328"
---
# <a name="default-keyboard-and-mouse-behavior-in-the-datagrid-control"></a>DataGrid Denetiminde Varsayılan Klavye ve Fare Davranışı
Bu konu, kullanıcılar ile nasıl etkileşim kurabileceğine açıklar <xref:System.Windows.Controls.DataGrid> klavyeyi ve fareyi kullanarak denetimi.  
  
 İle tipik etkileşimler <xref:System.Windows.Controls.DataGrid> gezinti, seçim ve düzenleme içerir. Seçim davranışı tarafından etkilenir <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> ve <xref:System.Windows.Controls.DataGrid.SelectionUnit%2A> özellikleri. Bu konuda açıklanan davranışa neden varsayılan değerler <xref:System.Windows.Controls.DataGridSelectionMode.Extended?displayProperty=nameWithType> ve <xref:System.Windows.Controls.DataGridSelectionUnit.FullRow?displayProperty=nameWithType>. Bu değerlerin değiştirilmesi, açıklanan farklı davranışa neden olabilir. Bir hücre düzenleme modunda olduğunda düzenleme denetiminin standart klavye davranışı geçersiz kılabilir <xref:System.Windows.Controls.DataGrid>.  
  
## <a name="default-keyboard-behavior"></a>Varsayılan klavye davranışı  
 Varsayılan klavye davranışı aşağıdaki tabloda <xref:System.Windows.Controls.DataGrid>.  
  
|Anahtar veya anahtar birleşimi|Açıklama|  
|----------------------------|-----------------|  
|AŞAĞI OK|Odağı geçerli hücreyi doğrudan hücrede taşır. Son satıra odağı ise aşağı ok tuşuna basarak hiçbir şey yapmaz.|  
|YUKARI OK|Odağı geçerli hücrenin doğrudan üstündeki taşır. İlk satırda odağı ise Yukarı Ok tuşuna basarak hiçbir şey yapmaz.|  
|SOL OK|Odağı önceki hücrenin sıradaki taşır. Odağı sıradaki ilk hücrenin ise, sol ok tuşuna basarak hiçbir şey yapmaz.|  
|SAĞ OK|Odağı satır içinde sonraki hücreye taşır. Odağı satırın son hücreye ise, sağ ok tuşuna basarak hiçbir şey yapmaz.|  
|HOME|Odağı geçerli satırda ilk hücrenin taşır.|  
|END|Odağı geçerli satırda son hücreye taşır.|  
|PAGE DOWN|Satırları gruplandırılmışsa tarafından tam olarak görüntülenen satırların sayısı denetimi aşağıya doğru kayar. Odağı sütunları değiştirmeden tam olarak görüntülenen son satıra taşır.<br /><br /> Satırları gruplandırılmışsa, odağı son satıra taşır <xref:System.Windows.Controls.DataGrid> sütunları değiştirmeden.|  
|AYARLAMA SAYFASI|Satırları gruplandırılmışsa denetimi tarafından tam olarak görüntülenen satırların sayısı yukarı kaydırır. Odağı bir sütun değiştirmeden görüntülenen ilk satıra taşır.<br /><br /> Satırları gruplandırılmışsa, odağı ilk satıra taşır <xref:System.Windows.Controls.DataGrid> sütunları değiştirmeden.|  
|TAB|Odağı geçerli satırda sonraki hücreyi taşır. Odağı satırın son hücreye ise, odak sonraki satırda ilk hücrenin taşır. Odağı denetimi son hücreye ise, odak sonraki denetime üst kapsayıcının sekme sırası taşır.<br /><br /> Geçerli hücreyi düzenleme modu ve odak değiştirilmeden önce geçerli satırı uzağa taşımak için SEKMESİNDE nedenleri odak tuşuna basarak, satır için yapılan tüm değişiklikler kaydedilmeden ise.|  
|SHIFT+TAB|Odağı önceki hücrenin geçerli satırda taşır. Odağı satırın ilk hücreye ise, odağı son hücreye önceki satıra taşır. Odağı, ilk hücrenin denetiminde ise, odağı üst kapsayıcının sekme sırası önceki denetimi taşır.<br /><br /> Geçerli hücreyi düzenleme modu ve odak değiştirilmeden önce geçerli satırı uzağa taşımak için SEKMESİNDE nedenleri odak tuşuna basarak, satır için yapılan tüm değişiklikler kaydedilmeden ise.|  
|CTRL + AŞAĞI OK|Odağı geçerli sütunun son hücreye taşır.|  
|CTRL + YUKARI OK|Odağı geçerli sütundaki ilk hücrenin taşır.|  
|CTRL + SAĞ OK|Odağı geçerli satırda son hücreye taşır.|  
|CTRL + SOL OK|Odağı geçerli satırda ilk hücrenin taşır.|  
|CTRL+HOME|Odağı denetimindeki ilk hücrenin taşır.|  
|CTRL+END|Odağı denetimi son hücreye taşır.|  
|CTRL+PAGE DOWN|SAYFA aşağı ile aynıdır.|  
|CTRL+PAGE UP|Sayfa Yukarı aynıdır.|  
|F2|Varsa <xref:System.Windows.Controls.DataGrid.IsReadOnly%2A?displayProperty=nameWithType> özelliği `false` ve <xref:System.Windows.Controls.DataGridColumn.IsReadOnly%2A?displayProperty=nameWithType> özelliği `false` geçerli sütunun geçerli hücreyi hücre düzenleme moduna geçirir.|  
|ENTER|Geçerli hücreyi ve satır değişiklikleri kaydeder ve odak geçerli hücreyi doğrudan hücrede taşır. Son satıra odağı ise odağı taşımadan değişiklikleri kaydeder.|  
|ESC|Denetim düzenleme modunda ise düzenlemeyi iptal eder ve denetimi yapılan tüm değişiklikler geri döner. Temel alınan veri kaynağı uygulayan <xref:System.ComponentModel.IEditableObject>, ikinci kez ESC tuşuna basarak düzenleme modunu tüm satırı için iptal eder.|  
|GERİ AL|İmleci önceki karakteri bir hücre düzenleme yaparken siler.|  
|DELETE|Karakter, sonra imleci bir hücre düzenleme yaparken siler.|  
|CTRL+ENTER|Herhangi bir değişiklik geçerli hücreyi odağı taşımadan kaydeder.|  
|CTRL+A|Varsa <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> ayarlanır <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, tüm satırları seçer <xref:System.Windows.Controls.DataGrid>.|  
  
## <a name="selection-keys"></a>Seçim tuşları  
 Varsa <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> özelliği <xref:System.Windows.Controls.DataGridSelectionMode.Extended>Gezinti davranışı değişmez ancak kaydırma (CTRL + SHIFT dahil) basarak klavye ile gezinme çok satır seçimi değiştirir. Gezinti başlamadan önce denetim geçerli satırdaki bir yer işareti satır olarak işaretler. SHIFT tuşuna basarak gittiğinizde seçimi bağlantı satır ile geçerli satırı arasındaki tüm satırları içerir.  
  
 Aşağıdaki seçim tuşları çok satırlı seçimini değiştirin.  
  
-   SHIFT + AŞAĞI OK  
  
-   SHIFT + YUKARI OK  
  
-   SHIFT+PAGE DOWN  
  
-   ÜST KARAKTER + PAGE UP  
  
-   CTRL + SHIFT + AŞAĞI OK  
  
-   CTRL + SHIFT + YUKARI OK  
  
-   CTRL+SHIFT+HOME  
  
-   CTRL+SHIFT+END  
  
## <a name="default-mouse-behavior"></a>Fare davranışı  
 Varsayılan fare davranışı aşağıdaki tabloda <xref:System.Windows.Controls.DataGrid>.  
  
|Fare eylemi|Açıklama|  
|------------------|-----------------|  
|Seçili olmayan bir satıra tıklayın|Geçerli satır ve tıklanan hücre geçerli hücreyi tıklanan satırı getirir.|  
|Geçerli hücreyi tıklatın|Geçerli bir hücre düzenleme moduna geçirir.|  
|Sütun üst bilgi hücresini sürükleyin|Varsa <xref:System.Windows.Controls.DataGrid.CanUserReorderColumns%2A?displayProperty=nameWithType> özelliği `true` ve <xref:System.Windows.Controls.DataGridColumn.CanUserReorder%2A?displayProperty=nameWithType> özelliği `true` geçerli sütun için bir sütun taşır, böylece yeni bir konuma bırakılabilir.|  
|Sütun üst bilgisi ayırıcı sürükleyin|Varsa <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=nameWithType> özelliği `true` ve <xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=nameWithType> özelliği `true` geçerli sütunun sütun yeniden boyutlandırır.|  
|Sütun üst bilgisi ayırıcı çift tıklayın|Varsa <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=nameWithType> özelliği `true` ve <xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=nameWithType> özelliği `true` otomatik boyutları geçerli sütun için sütun kullanarak <xref:System.Windows.Controls.DataGridLength.Auto%2A> boyutlandırma modunu.|  
|Bir sütun üst bilgisi hücreyi tıklatın|Varsa <xref:System.Windows.Controls.DataGrid.CanUserSortColumns%2A?displayProperty=nameWithType> özelliği `true` ve <xref:System.Windows.Controls.DataGridColumn.CanUserSort%2A?displayProperty=nameWithType> özelliği `true` sütunu geçerli sütunun sıralar.<br /><br /> Zaten sıralanmış bir sütunun başlığına tıklayarak bu sütunun sıralama yönünü ters.<br /><br /> SHIFT tuşuna basarak birden çok sütun başlığına tıklayarak tıklanan sırada birden çok sütuna göre sıralama.|  
|CTRL + bir satıra tıklayın|Varsa <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> ayarlanır <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, bitişik olmayan birden çok satır seçimi değiştirir.<br /><br /> Satır zaten seçili değilse, satırı öğenin seçimi kaldırılır.|  
|SHIFT + bir satıra tıklayın|Varsa <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> ayarlanır <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, bitişik bir çok satır seçimi değiştirir.|  
|Bir satır grubu üst bilgisi tıklayın|Genişletir veya daraltır grubu.|  
|Tümünü Seç üst sol köşesindeki düğmeye tıklayın <xref:System.Windows.Controls.DataGrid>|Varsa <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> ayarlanır <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, tüm satırları seçer <xref:System.Windows.Controls.DataGrid>.|  
  
## <a name="mouse-selection"></a>Fare seçimi  
 Varsa <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> özelliği <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, bir satır CTRL veya SHIFT tuşuna tıklayarak çok satır seçimi değiştirir.  
  
 CTRL tuşunu basılı tutun bir satırı tıklattığınızda, diğer tüm satırları, şu anki seçimi durumlarına sahip satır seçimi durumunu değiştirir. Bitişik olmayan satırları seçmek için bunu yapın.  
  
 SHIFT tuşuna basarak bir satırı tıklattığınızda, seçimi geçerli satırı tıklatın önce geçerli satırın bir konumda yer alan bir yer işareti satırı arasındaki tüm satırları içerir. Geçerli satırı, ancak bağlantı satır kaydırma basarken sonraki tıklama değiştirin. Bitişik satır aralığı seçmek için bunu yapın.  
  
 Bitişik satır bitişik olmayan aralıkları seçmek için CTRL + SHIFT birleştirilebilir. Bunu yapmak için SHIFT kullanarak ilk aralığı Seç + daha önce açıklandığı gibi tıklayın. İlk dizi satır seçtikten sonra CTRL tuşunu kullanın + sonraki aralıktaki ilk satırını seçin ve CTRL + SHIFT tuşuna basarak Son satırda sonraki Aralık'a tıklayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.DataGrid>
- <xref:System.Windows.Controls.DataGrid.SelectionMode%2A>
