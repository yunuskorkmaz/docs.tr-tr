---
title: Windows Forms DataGridView Denetimindeki Seçim Modları
ms.date: 03/30/2017
helpviewer_keywords:
- selection [Windows Forms], modes in DataGridView control
- DataGridView control [Windows Forms], selection mode
ms.assetid: a3ebfd3d-0525-479d-9d96-d9e017289b36
ms.openlocfilehash: 43f3648a9c7d64fb4fb900c7df3f01bc18d729b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="selection-modes-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetimindeki Seçim Modları
İçindeki kullanıcı seçimleri temel eylemleri gerçekleştirmek için uygulamanızın bazen istediğiniz bir <xref:System.Windows.Forms.DataGridView> denetim. Eylemler bağlı olarak, olası seçimi türlerini sınırlamak isteyebilirsiniz. Örneğin, uygulamanız şu anda seçili kaydı için bir rapor yazdırabilirsiniz varsayalım. Bu durumda, yapılandırmak isteyebilirsiniz <xref:System.Windows.Forms.DataGridView> denetim satır içinde her zaman herhangi bir yere tıklayarak böylece tüm satırı seçer ve bu nedenle, aynı anda yalnızca bir satır seçilebilir.  
  
 Ayarlayarak izin seçimleri belirtebilirsiniz <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> aşağıdakilerden birini özelliğine <xref:System.Windows.Forms.DataGridViewSelectionMode> numaralandırma değerleri.  
  
|DataGridViewSelectionMode değeri|Açıklama|  
|-------------------------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>|Bir hücrenin tıklatılan. Satır ve sütun üstbilgilerini seçim için kullanılamaz.|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>|Bir hücrenin tıklatılan. Bir sütun başlığını tıklatarak tüm sütunu seçer. Sütun üstbilgileri, sıralama için kullanılamaz.|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>|Bir hücrenin veya bir sütun başlığını tıklatarak tüm sütunu seçer. Sütun üstbilgileri, sıralama için kullanılamaz.|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>|Bir hücrenin veya satırda bir başlık tıklatmak tüm satırı seçer.|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>|Varsayılan seçim modu. Bir hücrenin tıklatılan. Satırda bir başlık tıklatmak tüm satırı seçer.|  
  
> [!NOTE]
>  Seçim modu çalışma zamanında otomatik olarak değiştirme geçerli seçim temizler.  
  
 Varsayılan olarak, kullanıcıların birden çok satırları, sütunları veya hücreleri fareyle sürükleyerek genişletmek veya bir seçimi değiştirmek için seçerek ya da tüm hücreleri denetiminde seçmek için sol üst bilgi hücresini tıklatarak CTRL veya SHIFT tuşuna basarak seçebilirsiniz. Bu davranışı önlemek için ayarlanmış <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> özelliğine `false`.  
  
 <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> Ve <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> modları bunları seçerek ve DELETE tuşuna basarak satırları silmek kullanıcıların olanak tanır. Kullanıcıları, satırları silebilir, yalnızca geçerli hücre düzenleme modunda olmadığında <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> özelliği ayarlanmış `true`, ve veri kaynağındaki kullanıcı tabanlı satır silmeyi destekler. Bu ayarları programlı satır silme engellemez unutmayın.  
  
## <a name="programmatic-selection"></a>Programsal seçimi  
 Geçerli seçim modu programlı seçimi yanı sıra kullanıcı seçimi davranışını kısıtlar. Geçerli seçimin programlı olarak ayarlayarak değiştirebileceğiniz `Selected` herhangi bir hücre, satır veya sütun mevcut özelliği <xref:System.Windows.Forms.DataGridView> denetim. Denetimindeki tüm hücreleri seçebilirsiniz <xref:System.Windows.Forms.DataGridView.SelectAll%2A> seçim modu bağlı olarak yöntemi. Seçimi temizlemek için kullanmak <xref:System.Windows.Forms.DataGridView.ClearSelection%2A> yöntemi.  
  
 Varsa <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> özelliği ayarlanmış `true`, ekleyebileceğiniz <xref:System.Windows.Forms.DataGridView> öğelerine veya değiştirerek seçimden kaldırın `Selected` öğesi özelliği. Aksi takdirde, ayarı `Selected` özelliğine `true` bir öğe diğer öğeleri seçimden otomatik olarak kaldırır. için.  
  
 Bu değerinin değiştirilmesi Not <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> özelliği, geçerli seçim değiştirmez.  
  
 Seçili hücre, satır veya sütun aracılığıyla koleksiyonu alabilir <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>, ve <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> özelliklerini <xref:System.Windows.Forms.DataGridView> denetim. Her hücre denetimi seçildiğinde bu özellikleri erişim verimsiz olur. Bu durumda bir performans cezası önlemek için <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> yöntemi ilk. Ayrıca, seçilen hücre sayısını belirlemek için bu koleksiyonları erişme, satır veya sütun verimsiz olabilir. Bunun yerine, kullanmanız <xref:System.Windows.Forms.DataGridView.GetCellCount%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A>, veya <xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A> tümleştirilmesidir yöntemi <xref:System.Windows.Forms.DataGridViewElementStates.Selected> değeri.  
  
> [!TIP]
>  Seçili hücreleri programlı kullanımını gösteren kod örneği bulunabilir <xref:System.Windows.Forms.DataGridView> sınıfına genel bakış.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A>  
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>  
 <xref:System.Windows.Forms.DataGridViewSelectionMode>  
 [Windows Forms DataGridView Denetimi ile Seçim ve Pano Kullanımı](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)  
 [Nasıl yapılır: Windows Forms DataGridView Denetiminin Seçim Modunu Ayarlama](../../../../docs/framework/winforms/controls/how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control.md)
