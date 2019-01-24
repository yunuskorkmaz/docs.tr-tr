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
ms.openlocfilehash: 1c58249df67efe5e782776d4996adef567f71a15
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492215"
---
# <a name="combobox-control-overview-windows-forms"></a>ComboBox Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ComboBox> denetimi bir açılan kutudaki verileri görüntülemek için kullanılır. Varsayılan olarak, <xref:System.Windows.Forms.ComboBox> denetimi iki parça halinde görünür: kullanıcı bir liste öğesi türüne izin veren bir metin kutusu üst parçasıdır. İkinci bir kullanıcı bir seçebileceği öğe listesini görüntüleyen bir liste kutusu bölümüdür. Birleşik giriş kutusu diğer stilleri hakkında daha fazla bilgi için bkz. [ne zaman bir Windows Forms ComboBox INSTEAD of ListBox kullanılacağını](../../../../docs/framework/winforms/controls/when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md).  
  
 <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> Özelliği, seçilen liste öğesine karşılık gelen bir tamsayı değeri döndürür. Seçili öğeyi değiştirerek programlama yoluyla değiştirebilirsiniz <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> değer kodda; listesinde karşılık gelen öğe birleşik giriş kutusundaki metin kutusu bölümünde görünür. Hiçbir öğe seçili değilse <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> değer -1'dir. Listedeki ilk öğe seçili ise, ardından <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> değer: 0. <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> Özelliği benzer <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> , ancak öğenin kendisini, genellikle bir dize değeri döndürür. <xref:System.Windows.Forms.ComboBox.ObjectCollection.Count%2A> Özelliği değerini ve listedeki öğe sayısını yansıtır <xref:System.Windows.Forms.ComboBox.ObjectCollection.Count%2A> özelliği her zaman bir birden çok en büyük olası <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> çünkü değer <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> sıfır tabanlıdır.  
  
 Ekleme veya öğeleri silme bir <xref:System.Windows.Forms.ComboBox> denetlemek, kullanın <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A>, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Insert%2A>, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Clear%2A> veya <xref:System.Windows.Forms.ComboBox.ObjectCollection.Remove%2A> yöntemi. Alternatif olarak, öğeleri listesine kullanarak ekleyebileceğiniz <xref:System.Windows.Forms.ComboBox.Items%2A> özellik Tasarımcısı'nda.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.ComboBox>
- [ListBox Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/listbox-control-overview-windows-forms.md)
- [ListBox Yerine Ne Zaman Windows Forms ComboBox Kullanılır?](../../../../docs/framework/winforms/controls/when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)
- [Nasıl yapılır: Ekleme ve kaldırma öğeleri bir Windows Forms ComboBox, ListBox veya CheckedListBox denetimi](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)
- [Nasıl yapılır: Sıralama içeriği bir Windows Forms ComboBox, ListBox veya CheckedListBox denetimi](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [Nasıl yapılır: Özel erişim öğeleri bir Windows Forms ComboBox, ListBox veya CheckedListBox denetimi](../../../../docs/framework/winforms/controls/access-specific-items-in-a-wf-combobox-listbox-or-checkedlistbox.md)
- [Nasıl yapılır: Bir Windows Forms ComboBox veya ListBox denetimini verilere bağlama](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)
- [Seçenekleri Listelemede Kullanılan Windows Forms Denetimleri](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
- [Nasıl yapılır: ComboBox, ListBox veya CheckedListBox denetiminde bir Windows Forms için arama tablosu oluşturma](../../../../docs/framework/winforms/controls/create-a-lookup-table-for-a-wf-combobox-listbox.md)
