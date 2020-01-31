---
title: ComboBox Denetimine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- ComboBox
helpviewer_keywords:
- drop-down lists [Windows Forms], Windows Forms
- ComboBox control [Windows Forms], about ComboBox control
- drop-down lists [Windows Forms], ComboBox control
- combo boxes [Windows Forms], about combo boxes
ms.assetid: a58b393f-a614-45d1-8961-857a024b5acd
ms.openlocfilehash: 9fb270d7787902872a32a87c140316f756bd48aa
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743839"
---
# <a name="combobox-control-overview-windows-forms"></a>ComboBox Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ComboBox> denetimi, verileri açılan bir açılan kutuda göstermek için kullanılır. Varsayılan olarak, <xref:System.Windows.Forms.ComboBox> denetimi iki bölümden oluşur: üstteki bölüm, kullanıcının bir liste öğesi yazarak bir metin kutusudur. İkinci bölüm, kullanıcının seçim bileceği öğelerin bir listesini görüntüleyen bir liste kutusudur. Birleşik giriş kutusunun diğer stilleri hakkında daha fazla bilgi için, bkz. [ListBox yerine Windows Forms ComboBox 'ın ne zaman kullanıldığı](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md).  
  
 <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> özelliği, seçilen liste öğesine karşılık gelen bir tamsayı değeri döndürür. Kodda <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> değerini değiştirerek, seçilen öğeyi program aracılığıyla değiştirebilirsiniz. listedeki ilgili öğe, Birleşik giriş kutusunun metin kutusu bölümünde görünür. Hiçbir öğe seçilmezse, <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> değeri-1 ' dir. Listedeki ilk öğe seçiliyse <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> değeri 0 ' dır. <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> özelliği <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> benzerdir, ancak genellikle bir dize değeri olan öğenin kendisini döndürür. <xref:System.Windows.Forms.ComboBox.ObjectCollection.Count%2A> özelliği, listedeki öğelerin sayısını yansıtır ve <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> sıfır tabanlı olduğundan, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Count%2A> özelliğinin değeri her zaman mümkün olan en büyük <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> değerden bir daha büyüktür.  
  
 <xref:System.Windows.Forms.ComboBox> denetimine öğe eklemek veya silmek için <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A>, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Insert%2A>, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Clear%2A> veya <xref:System.Windows.Forms.ComboBox.ObjectCollection.Remove%2A> yöntemini kullanın. Alternatif olarak, tasarımcıda <xref:System.Windows.Forms.ComboBox.Items%2A> özelliğini kullanarak listeye öğe ekleyebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ComboBox>
- [ListBox Denetimine Genel Bakış](listbox-control-overview-windows-forms.md)
- [ListBox Yerine Ne Zaman Windows Forms ComboBox Kullanılır?](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)
- [Nasıl yapılır: Bir Windows Forms ComboBox, ListBox veya CheckedListBox Denetiminde Öğe Ekleme ve Kaldırma](add-and-remove-items-from-a-wf-combobox.md)
- [Nasıl yapılır: Windows Forms ComboBox, ListBox veya CheckedListBox Denetiminin İçeriğini Sıralama](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [Nasıl yapılır: Bir Windows Forms ComboBox, ListBox veya CheckedListBox Denetiminde Belirli Öğelere Erişme](access-specific-items-in-a-wf-combobox-listbox-or-checkedlistbox.md)
- [Nasıl yapılır: Windows Forms ComboBox veya ListBox Denetimini Verilere Bağlama](how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)
- [Seçenekleri Listelemede Kullanılan Windows Forms Denetimleri](windows-forms-controls-used-to-list-options.md)
- [Nasıl yapılır: Bir Windows Forms ComboBox, ListBox veya CheckedListBox Denetimi için Arama Tablosu Oluşturma](create-a-lookup-table-for-a-wf-combobox-listbox.md)
