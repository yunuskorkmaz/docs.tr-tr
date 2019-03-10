---
title: ListBox Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ListBox
helpviewer_keywords:
- list boxes [Windows Forms], about list boxes
- ListBox control [Windows Forms], about ListBox control
ms.assetid: 37ea226b-6fc8-4c70-936a-c6af4e0cad4c
ms.openlocfilehash: 2bba90f704458e1c724328feccaaf6f04b98ecb4
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723991"
---
# <a name="listbox-control-overview-windows-forms"></a>ListBox Denetimine Genel Bakış (Windows Forms)
Bir Windows Forms <xref:System.Windows.Forms.ListBox> denetimi, kullanıcı bir veya daha fazla öğe seçebilir listesini görüntüler. Toplam öğe sayısı, görüntülenebilen sayıyı aşarsa, bir kaydırma çubuğuna otomatik olarak eklenir <xref:System.Windows.Forms.ListBox> denetimi. Zaman <xref:System.Windows.Forms.ListBox.MultiColumn%2A> özelliği `true`, liste kutusunda birden çok sütunda öğeleri görüntüler ve yatay kaydırma çubuğu görünür. Zaman <xref:System.Windows.Forms.ListBox.MultiColumn%2A> özelliği `false`, liste kutusu öğeleri tek bir sütunda görüntüler ve dikey kaydırma çubuğu görünür. Zaman <xref:System.Windows.Forms.ListBox.ScrollAlwaysVisible%2A> ayarlanır `true`, öğe sayısı ne olursa olsun kaydırma çubuğu görünür. <xref:System.Windows.Forms.ListBox.SelectionMode%2A> Özelliği, aynı anda kaç liste öğelerini seçilebilir belirler.  
  
## <a name="ways-to-change-the-listbox-control"></a>ListBox denetimi değiştirme yolları  
 <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> Özelliği liste kutusunda seçili ilk öğenin karşılık gelen bir tamsayı değeri döndürür. Seçili öğeyi değiştirerek programlama yoluyla değiştirebilirsiniz <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> değer kodda; listesinde karşılık gelen öğe Windows Form üzerinde vurgulu olarak görünür. Hiçbir öğe seçili değilse <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> değer -1'dir. Listedeki ilk öğe seçili değilse <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> değer: 0. Birden çok öğe seçildiğinde, <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> değeri, listedeki ilk görünen seçili öğeyi yansıtır. <xref:System.Windows.Forms.ListBox.SelectedItem%2A> Özelliği benzer <xref:System.Windows.Forms.ListBox.SelectedIndex%2A>, ancak öğenin kendisini, genellikle bir dize değeri döndürür. <xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A> Özelliği değerini ve listedeki öğe sayısını yansıtır <xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A> özelliği her zaman bir birden çok en büyük olası <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> çünkü değer <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> sıfır tabanlıdır.  
  
 Ekleme veya öğeleri silme bir <xref:System.Windows.Forms.ListBox> denetlemek, kullanın <xref:System.Windows.Forms.ListBox.ObjectCollection.Add%2A>, <xref:System.Windows.Forms.ListBox.ObjectCollection.Insert%2A>, <xref:System.Windows.Forms.ListBox.ObjectCollection.Clear%2A> veya <xref:System.Windows.Forms.ListBox.ObjectCollection.Remove%2A> yöntemi. Alternatif olarak, öğeleri listesine kullanarak ekleyebileceğiniz <xref:System.Windows.Forms.ListBox.Items%2A> özellik tasarım zamanında.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.ListBox>
- [Nasıl yapılır: Ekleme ve kaldırma öğeleri bir Windows Forms ComboBox, ListBox veya CheckedListBox denetimi](add-and-remove-items-from-a-wf-combobox.md)
- [Nasıl yapılır: Sıralama içeriği bir Windows Forms ComboBox, ListBox veya CheckedListBox denetimi](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [Nasıl yapılır: Bir Windows Forms ComboBox veya ListBox denetimini verilere bağlama](how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)
- [ComboBox Denetimine Genel Bakış](combobox-control-overview-windows-forms.md)
- [CheckedListBox Denetimine Genel Bakış](checkedlistbox-control-overview-windows-forms.md)
- [Seçenekleri Listelemede Kullanılan Windows Forms Denetimleri](windows-forms-controls-used-to-list-options.md)
- [Nasıl yapılır: ComboBox, ListBox veya CheckedListBox denetiminde bir Windows Forms için arama tablosu oluşturma](create-a-lookup-table-for-a-wf-combobox-listbox.md)
