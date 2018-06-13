---
title: ListBox Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ListBox
helpviewer_keywords:
- list boxes [Windows Forms], about list boxes
- ListBox control [Windows Forms], about ListBox control
ms.assetid: 37ea226b-6fc8-4c70-936a-c6af4e0cad4c
ms.openlocfilehash: d4cb423a6f32778695abeae725da9755b610d209
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537570"
---
# <a name="listbox-control-overview-windows-forms"></a>ListBox Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ListBox> denetimi, kullanıcı seçebileceği bir veya daha fazla öğe listesini görüntüler. Toplam öğe sayısını görüntülenebilir sayıyı aşarsa, bir kaydırma çubuğunun otomatik olarak eklenir <xref:System.Windows.Forms.ListBox> denetim. Zaman <xref:System.Windows.Forms.ListBox.MultiColumn%2A> özelliği ayarlanmış `true`, liste kutusu öğeleri birden çok sütun görüntüler ve yatay kaydırma çubuğu görüntülenir. Zaman <xref:System.Windows.Forms.ListBox.MultiColumn%2A> özelliği ayarlanmış `false`, liste kutusu öğeleri tek bir sütunda görüntüler ve dikey kaydırma çubuğu görüntülenir. Zaman <xref:System.Windows.Forms.ListBox.ScrollAlwaysVisible%2A> ayarlanır `true`, öğelerin sayısı bağımsız olarak kaydırma çubuğu görüntülenir. <xref:System.Windows.Forms.ListBox.SelectionMode%2A> Özelliği, aynı anda kaç liste öğeleri seçilebilir belirler.  
  
## <a name="ways-to-change-the-listbox-control"></a>ListBox denetimi değiştirme yolları  
 <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> Özelliği, liste kutusunda seçili bir ilk öğesine karşılık gelen bir tamsayı değeri döndürür. Seçili öğeyi değiştirerek program aracılığıyla değiştirebilirsiniz <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> değer kodda; listesinde karşılık gelen öğe Windows formunda vurgulu olarak gösterilir. Öğe seçiliyse, <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> değer -1'dir. Listedeki ilk öğe seçiliyse, <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> değer: 0. Birden çok öğe seçildiğinde, <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> değeri, listedeki ilk görünen seçilen öğeyi yansıtır. <xref:System.Windows.Forms.ListBox.SelectedItem%2A> Özelliği benzer <xref:System.Windows.Forms.ListBox.SelectedIndex%2A>, ancak öğenin kendisini, genellikle bir string değeri döndürür. <xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A> Özelliği yansıtır liste öğelerinin sayısını ve değerini <xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A> özelliktir her zaman bir birden çok büyük olası <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> çünkü değer <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> sıfır tabanlı olduğundan.  
  
 Ekleme veya öğeleri silmek için bir <xref:System.Windows.Forms.ListBox> denetlemek, kullanın <xref:System.Windows.Forms.ListBox.ObjectCollection.Add%2A>, <xref:System.Windows.Forms.ListBox.ObjectCollection.Insert%2A>, <xref:System.Windows.Forms.ListBox.ObjectCollection.Clear%2A> veya <xref:System.Windows.Forms.ListBox.ObjectCollection.Remove%2A> yöntemi. Alternatif olarak, öğeleri listede kullanarak ekleyebileceğiniz <xref:System.Windows.Forms.ListBox.Items%2A> tasarım zamanında özelliği.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ListBox>  
 [Nasıl yapılır: Bir Windows Forms ComboBox, ListBox veya CheckedListBox Denetiminde Öğe Ekleme ve Kaldırma](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)  
 [Nasıl yapılır: Windows Forms ComboBox, ListBox veya CheckedListBox Denetiminin İçeriğini Sıralama](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)  
 [Nasıl yapılır: Windows Forms ComboBox veya ListBox Denetimini Verilere Bağlama](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)  
 [ComboBox Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/combobox-control-overview-windows-forms.md)  
 [CheckedListBox Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/checkedlistbox-control-overview-windows-forms.md)  
 [Seçenekleri Listelemede Kullanılan Windows Forms Denetimleri](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)  
 [Nasıl yapılır: Bir Windows Forms ComboBox, ListBox veya CheckedListBox Denetimi için Arama Tablosu Oluşturma](../../../../docs/framework/winforms/controls/create-a-lookup-table-for-a-wf-combobox-listbox.md)
