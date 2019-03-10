---
title: Windows Forms DataGridView Denetimindeki Seçim Modları
ms.date: 03/30/2017
helpviewer_keywords:
- selection [Windows Forms], modes in DataGridView control
- DataGridView control [Windows Forms], selection mode
ms.assetid: a3ebfd3d-0525-479d-9d96-d9e017289b36
ms.openlocfilehash: 931df04bbe6b8448030e26cd2cc2c904865ac0d3
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57717309"
---
# <a name="selection-modes-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetimindeki Seçim Modları
Uygulamanızın içinde kullanıcı seçimlerine göre eylemleri gerçekleştirmek için bazen istediğiniz bir <xref:System.Windows.Forms.DataGridView> denetimi. Eylemler bağlı olarak, mümkün olan seçim türlerini sınırlamak isteyebilirsiniz. Örneğin, uygulamanızın seçili olan kaydı için bir rapor yazdırabilir varsayalım. Bu durumda, yapılandırma isteyebilirsiniz <xref:System.Windows.Forms.DataGridView> denetimi bir satır her zaman herhangi bir yere tıklayarak böylece tüm satırı seçer ve bu nedenle aynı anda yalnızca bir satır seçilebilir.  
  
 Ayarlayarak izin seçimleri belirtebilirsiniz <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> aşağıdakilerden birini özelliğini <xref:System.Windows.Forms.DataGridViewSelectionMode> sabit listesi değerleri.  
  
|DataGridViewSelectionMode value|Açıklama|  
|-------------------------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>|Bir hücreye tıklayıp seçer. Satır ve sütun üst bilgilerinin seçimi için kullanılamaz.|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>|Bir hücreye tıklayıp seçer. Bir sütun başlığına tıklayarak tüm sütunu seçer. Sütun başlıkları, sıralama için kullanılamaz.|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>|Bir hücreyi veya bir sütun başlığına tıklayarak tüm sütunu seçer. Sütun başlıkları, sıralama için kullanılamaz.|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>|Bir hücreyi veya bir satır üst bilgisi tıklayarak tüm satırı seçer.|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>|Varsayılan seçim modu. Bir hücreye tıklayıp seçer. Bir satır başlığına tıklayarak tüm satırı seçer.|  
  
> [!NOTE]
>  Seçim modu çalışma zamanında otomatik olarak değiştirme geçerli seçim temizlenir.  
  
 Varsayılan olarak, kullanıcıların birden fazla satır, sütun veya hücre fare ile sürükleyerek genişletin veya bir seçimi değiştirmek için seçme veya tüm hücreleri denetimi seçmek için sol üst başlığı hücreye tıklayıp CTRL veya SHIFT tuşuna basarak seçebilirsiniz. Bu davranışı engellemek için ayarlanmış <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> özelliğini `false`.  
  
 <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> Ve <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> modları kullanıcıların bunları seçerek ve DELETE tuşuna basarak satırları silmek olanak tanır. Kullanıcıları, satır silebilir, yalnızca geçerli hücre düzenleme modunda olmadığında <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> özelliği `true`, temel alınan veri kaynağına kullanıcı temelli satır silmeyi destekler. Bu ayarları program Satır silme engellemez unutmayın.  
  
## <a name="programmatic-selection"></a>Programlı seçimi  
 Geçerli seçim modunu programlı seçimi ve bunun yanı sıra kullanıcı seçimine davranışını kısıtlar. Ayarlayarak geçerli seçimi programlama yoluyla değiştirebilirsiniz `Selected` özelliği herhangi bir hücre, satır veya sütun mevcut <xref:System.Windows.Forms.DataGridView> denetimi. Tüm hücreleri denetiminde seçebilirsiniz <xref:System.Windows.Forms.DataGridView.SelectAll%2A> seçim moduna bağlı olarak bir yöntem. Seçimi temizlemek için kullanmak <xref:System.Windows.Forms.DataGridView.ClearSelection%2A> yöntemi.  
  
 Varsa <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> özelliği `true`, ekleyebileceğiniz <xref:System.Windows.Forms.DataGridView> öğelerine veya bunları değiştirerek seçimden Kaldır `Selected` öğesinin özelliği. Aksi takdirde, ayarı `Selected` özelliğini `true` için bir öğe diğer öğeleri seçimden otomatik olarak kaldırır.  
  
 Değerinin değiştirilmesi Not <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> özelliği geçerli seçimi değiştirmez.  
  
 Şu anda seçili hücre, satır veya sütun aracılığıyla koleksiyonunu alabilirsiniz <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>, ve <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> özelliklerini <xref:System.Windows.Forms.DataGridView> denetimi. Her hücreye bir Denetim seçildiğinde, bu özelliklerine erişme yetersizdir. Bu durumda bir performans cezası önlemek için <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> yöntemi ilk. Ayrıca, seçilen hücre sayısını belirlemek için bu koleksiyonlara erişmek, satırlar veya sütunlar verimsiz olabilir. Bunun yerine, kullanmanız <xref:System.Windows.Forms.DataGridView.GetCellCount%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A>, veya <xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A> tümleştirilmesidir yöntemi <xref:System.Windows.Forms.DataGridViewElementStates.Selected> değeri.  
  
> [!TIP]
>  Seçili hücreleri programlı kullanımını gösteren kod örneği bulunabilir <xref:System.Windows.Forms.DataGridView> sınıfına genel bakış.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.MultiSelect%2A>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridViewSelectionMode>
- [Windows Forms DataGridView Denetimi ile Seçim ve Pano Kullanımı](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView denetiminin seçim modunu ayarlama](how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control.md)
