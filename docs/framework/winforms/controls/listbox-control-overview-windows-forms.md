---
title: ListBox Denetimine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- ListBox
helpviewer_keywords:
- list boxes [Windows Forms], about list boxes
- ListBox control [Windows Forms], about ListBox control
ms.assetid: 37ea226b-6fc8-4c70-936a-c6af4e0cad4c
ms.openlocfilehash: 1abf8bea5c786f2ce326631370fa294ada09a92c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745187"
---
# <a name="listbox-control-overview-windows-forms"></a>ListBox Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ListBox> denetim, kullanıcının bir veya daha fazla öğe seçebileceğiniz bir liste görüntüler. Toplam öğe sayısı görüntülenebilen sayıyı aşarsa, <xref:System.Windows.Forms.ListBox> denetimine bir kaydırma çubuğu otomatik olarak eklenir. <xref:System.Windows.Forms.ListBox.MultiColumn%2A> özelliği `true`olarak ayarlandığında, liste kutusu öğeleri birden çok sütunda görüntüler ve yatay kaydırma çubuğu görüntülenir. <xref:System.Windows.Forms.ListBox.MultiColumn%2A> özelliği `false`olarak ayarlandığında liste kutusu öğeleri tek bir sütunda görüntüler ve dikey kaydırma çubuğu görüntülenir. <xref:System.Windows.Forms.ListBox.ScrollAlwaysVisible%2A> `true`olarak ayarlandığında, öğe sayısından bağımsız olarak kaydırma çubuğu görüntülenir. <xref:System.Windows.Forms.ListBox.SelectionMode%2A> özelliği, her seferinde kaç liste öğesinin seçilebileceğini belirler.  
  
## <a name="ways-to-change-the-listbox-control"></a>ListBox denetimini değiştirme yolları  
 <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> özelliği, liste kutusunda seçili olan ilk öğeye karşılık gelen bir tamsayı değeri döndürür. Kodda <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> değerini değiştirerek, seçilen öğeyi program aracılığıyla değiştirebilirsiniz. listedeki ilgili öğe, Windows formunda vurgulanmış olarak görünür. Hiçbir öğe seçilmezse, <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> değeri-1 ' dir. Listedeki ilk öğe seçiliyse <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> değeri 0 ' dır. Birden çok öğe seçildiğinde, <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> değeri listede ilk görüntülenen seçili öğeyi yansıtır. <xref:System.Windows.Forms.ListBox.SelectedItem%2A> özelliği <xref:System.Windows.Forms.ListBox.SelectedIndex%2A>benzerdir, ancak genellikle bir dize değeri olan öğenin kendisini döndürür. <xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A> özelliği, listedeki öğelerin sayısını yansıtır ve <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> sıfır tabanlı olduğundan, <xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A> özelliğinin değeri her zaman mümkün olan en büyük <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> değerden bir daha büyüktür.  
  
 <xref:System.Windows.Forms.ListBox> denetimine öğe eklemek veya silmek için <xref:System.Windows.Forms.ListBox.ObjectCollection.Add%2A>, <xref:System.Windows.Forms.ListBox.ObjectCollection.Insert%2A>, <xref:System.Windows.Forms.ListBox.ObjectCollection.Clear%2A> veya <xref:System.Windows.Forms.ListBox.ObjectCollection.Remove%2A> yöntemini kullanın. Alternatif olarak, tasarım zamanında <xref:System.Windows.Forms.ListBox.Items%2A> özelliğini kullanarak listeye öğe ekleyebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ListBox>
- [Nasıl yapılır: Bir Windows Forms ComboBox, ListBox veya CheckedListBox Denetiminde Öğe Ekleme ve Kaldırma](add-and-remove-items-from-a-wf-combobox.md)
- [Nasıl yapılır: Windows Forms ComboBox, ListBox veya CheckedListBox Denetiminin İçeriğini Sıralama](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [Nasıl yapılır: Windows Forms ComboBox veya ListBox Denetimini Verilere Bağlama](how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)
- [ComboBox Denetimine Genel Bakış](combobox-control-overview-windows-forms.md)
- [CheckedListBox Denetimine Genel Bakış](checkedlistbox-control-overview-windows-forms.md)
- [Seçenekleri Listelemede Kullanılan Windows Forms Denetimleri](windows-forms-controls-used-to-list-options.md)
- [Nasıl yapılır: Bir Windows Forms ComboBox, ListBox veya CheckedListBox Denetimi için Arama Tablosu Oluşturma](create-a-lookup-table-for-a-wf-combobox-listbox.md)
