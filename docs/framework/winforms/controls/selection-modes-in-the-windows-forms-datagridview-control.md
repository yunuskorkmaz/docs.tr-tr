---
title: Windows Forms DataGridView Denetimindeki Seçim Modları
ms.date: 03/30/2017
helpviewer_keywords:
- selection [Windows Forms], modes in DataGridView control
- DataGridView control [Windows Forms], selection mode
ms.assetid: a3ebfd3d-0525-479d-9d96-d9e017289b36
ms.openlocfilehash: dfe26e4749e6bff2d0ccdff47c6ea0b301880772
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960464"
---
# <a name="selection-modes-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetimindeki Seçim Modları
Bazen uygulamanızın bir <xref:System.Windows.Forms.DataGridView> denetim içindeki kullanıcı seçimlerini temel alan eylemler gerçekleştirmesini isteyebilirsiniz. Eylemlere bağlı olarak, olası seçim türlerini kısıtlamak isteyebilirsiniz. Örneğin, uygulamanızın Şu anda seçili olan kayıt için bir rapor yazdırabildiğini varsayalım. Bu durumda, bir satırdaki herhangi bir yere tıklamak her <xref:System.Windows.Forms.DataGridView> zaman tüm satırı seçecek ve böylece tek seferde yalnızca bir satır seçilebilmek için denetimi yapılandırmak isteyebilirsiniz.  
  
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> Özelliği aşağıdaki<xref:System.Windows.Forms.DataGridViewSelectionMode> sabit listesi değerlerinden birine ayarlayarak izin verilen seçimleri belirtebilirsiniz.  
  
|DataGridViewSelectionMode değeri|Açıklama|  
|-------------------------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>|Bir hücreye tıklamak onu seçer. Satır ve sütun üst bilgileri seçim için kullanılamaz.|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>|Bir hücreye tıklamak onu seçer. Bir sütun başlığına tıkladığınızda sütunun tamamı seçilir. Sütun başlıkları sıralama için kullanılamaz.|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>|Bir hücreye veya sütun başlığına tıkladığınızda sütunun tamamı seçilir. Sütun başlıkları sıralama için kullanılamaz.|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>|Bir hücreye veya bir satır başlığına tıkladığınızda satırın tamamı seçilir.|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>|Varsayılan seçim modu. Bir hücreye tıklamak onu seçer. Bir satır başlığına tıkladığınızda satırın tamamı seçilir.|  
  
> [!NOTE]
> Çalışma zamanında seçim modunun değiştirilmesi, geçerli seçimi otomatik olarak temizler.  
  
 Varsayılan olarak, kullanıcılar fareyle sürükleyerek birden çok satır, sütun veya hücre seçebilir, bir seçimi genişletmeyi veya değiştirmeyi seçerken CTRL veya SHIFT tuşuna basarak veya denetimdeki tüm hücreleri seçmek için sol üst başlık hücresine tıklayabilirsiniz. Bu davranışı engellemek için <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> özelliğini olarak `false`ayarlayın.  
  
 <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> Ve<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> modları, kullanıcıların sütunları seçip DELETE tuşuna basarak satırları silmesine izin verir. Kullanıcılar yalnızca geçerli hücre düzenleme modunda olmadığında satırları silebilir, <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> özelliği olarak `true`ayarlanır ve temel alınan veri kaynağı Kullanıcı odaklı satır silmeyi destekler. Bu ayarların programlı satır silme işlemini önleyemediğini unutmayın.  
  
## <a name="programmatic-selection"></a>Programlı seçim  
 Geçerli seçim modu, programlama seçiminin ve Kullanıcı seçiminin davranışını kısıtlar. Denetimde bulunan herhangi bir hücre, satır veya sütun `Selected` özelliğini ayarlayarak, geçerli seçimi programlı bir şekilde değiştirebilirsiniz. <xref:System.Windows.Forms.DataGridView> Seçim moduna bağlı olarak, denetimdeki <xref:System.Windows.Forms.DataGridView.SelectAll%2A> tüm hücreleri de seçebilirsiniz. Seçimi temizlemek için <xref:System.Windows.Forms.DataGridView.ClearSelection%2A> yöntemini kullanın.  
  
 Özelliği olarak `true`ayarlandıysa, öğesinin `Selected` özelliğini değiştirerek bu öğeleri seçime <xref:System.Windows.Forms.DataGridView> ekleyebilir veya seçimden kaldırabilirsiniz. <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> Aksi takdirde, `Selected` `true` özelliği bir öğe için olarak ayarlamak, diğer öğeleri seçimden otomatik olarak kaldırır.  
  
 <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> Özelliğin değerini değiştirmenin geçerli seçimi değiştirmediğini unutmayın.  
  
 Şu anda seçili olan hücre, satır veya <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>sütunların bir koleksiyonunu, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> <xref:System.Windows.Forms.DataGridView> , ve <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> denetiminin özellikleri aracılığıyla alabilirsiniz. Denetimdeki her hücre seçildiğinde bu özelliklere erişmek verimsiz değildir. Bu durumda bir performans cezasından kaçınmak için öncelikle <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> yöntemini kullanın. Ayrıca, seçilen hücre, satır veya sütun sayısını öğrenmek için bu koleksiyonlara erişme verimsiz olabilir. Bunun <xref:System.Windows.Forms.DataGridView.GetCellCount%2A>yerine, <xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A> değerini<xref:System.Windows.Forms.DataGridViewElementStates.Selected> geçirerek, veya <xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A> metodunu kullanmanız gerekir.  
  
> [!TIP]
>  Seçilen hücrelerin programlı kullanımını gösteren örnek kod, <xref:System.Windows.Forms.DataGridView> sınıfa genel bakış bölümünde bulunabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.MultiSelect%2A>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridViewSelectionMode>
- [Windows Forms DataGridView Denetimi ile Seçim ve Pano Kullanımı](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView denetiminin seçim modunu ayarlama](how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control.md)
