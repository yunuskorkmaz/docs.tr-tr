---
title: ComboBox Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ComboBox
helpviewer_keywords:
- drop-down lists [Windows Forms], Windows Forms
- ComboBox control [Windows Forms], about ComboBox control
- drop-down lists [Windows Forms], ComboBox control
- combo boxes [Windows Forms], about combo boxes
ms.assetid: a58b393f-a614-45d1-8961-857a024b5acd
ms.openlocfilehash: c8cd0430e9abaed0ee58e971edf6a9c871da37c5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="combobox-control-overview-windows-forms"></a>ComboBox Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ComboBox> denetimi açılan kutuya verileri görüntülemek için kullanılır. Varsayılan olarak, <xref:System.Windows.Forms.ComboBox> denetimi iki parça halinde görüntülenir: bir liste öğesi türü kullanıcı sağlayan bir metin kutusu üst parçasıdır. İkinci bölümü, kullanıcı bir seçebileceği öğe listesini görüntüleyen bir liste kutusudur. Birleşik giriş kutusu diğer stilleri hakkında daha fazla bilgi için bkz: [ne zaman bir Windows Forms ComboBox INSTEAD of ListBox kullanılacağı](../../../../docs/framework/winforms/controls/when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md).  
  
 <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> Özelliği seçilen liste öğesine karşılık gelen bir tamsayı değeri döndürür. Seçili öğeyi değiştirerek program aracılığıyla değiştirebilirsiniz <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> değer kodda; listesinde karşılık gelen öğe birleşik giriş kutusu metin kutusu bölümünde görüntülenir. Öğe seçiliyse, <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> değer -1'dir. Listedeki ilk öğe seçiliyse, sonra <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> değer: 0. <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> Özelliği benzer <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> , ancak öğenin kendisini, genellikle bir string değeri döndürür. <xref:System.Windows.Forms.ComboBox.ObjectCollection.Count%2A> Özelliği yansıtır liste öğelerinin sayısını ve değerini <xref:System.Windows.Forms.ComboBox.ObjectCollection.Count%2A> özelliktir her zaman bir birden çok büyük olası <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> çünkü değer <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> sıfır tabanlı olduğundan.  
  
 Ekleme veya öğeleri silmek için bir <xref:System.Windows.Forms.ComboBox> denetlemek, kullanın <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A>, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Insert%2A>, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Clear%2A> veya <xref:System.Windows.Forms.ComboBox.ObjectCollection.Remove%2A> yöntemi. Alternatif olarak, öğeleri listede kullanarak ekleyebileceğiniz <xref:System.Windows.Forms.ComboBox.Items%2A> Tasarımcısı'nda özelliği.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ComboBox>  
 [ListBox Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/listbox-control-overview-windows-forms.md)  
 [ListBox Yerine Ne Zaman Windows Forms ComboBox Kullanılır?](../../../../docs/framework/winforms/controls/when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)  
 [Nasıl yapılır: Bir Windows Forms ComboBox, ListBox veya CheckedListBox Denetiminde Öğe Ekleme ve Kaldırma](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)  
 [Nasıl yapılır: Windows Forms ComboBox, ListBox veya CheckedListBox Denetiminin İçeriğini Sıralama](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)  
 [Nasıl yapılır: Bir Windows Forms ComboBox, ListBox veya CheckedListBox Denetiminde Belirli Öğelere Erişme](../../../../docs/framework/winforms/controls/access-specific-items-in-a-wf-combobox-listbox-or-checkedlistbox.md)  
 [Nasıl yapılır: Windows Forms ComboBox veya ListBox Denetimini Verilere Bağlama](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)  
 [Seçenekleri Listelemede Kullanılan Windows Forms Denetimleri](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)  
 [Nasıl yapılır: Bir Windows Forms ComboBox, ListBox veya CheckedListBox Denetimi için Arama Tablosu Oluşturma](../../../../docs/framework/winforms/controls/create-a-lookup-table-for-a-wf-combobox-listbox.md)
