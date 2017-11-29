---
title: "ListBox Denetimine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ListBox
helpviewer_keywords:
- list boxes [Windows Forms], about list boxes
- ListBox control [Windows Forms], about ListBox control
ms.assetid: 37ea226b-6fc8-4c70-936a-c6af4e0cad4c
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6e73d76a2d9b31a87bf5a693b5ffa387d7ab5cef
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="listbox-control-overview-windows-forms"></a>ListBox Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ListBox> denetimi, kullanıcı seçebileceği bir veya daha fazla öğe listesini görüntüler. Toplam öğe sayısını görüntülenebilir sayıyı aşarsa, bir kaydırma çubuğunun otomatik olarak eklenir <xref:System.Windows.Forms.ListBox> denetim. Zaman <xref:System.Windows.Forms.ListBox.MultiColumn%2A> özelliği ayarlanmış `true`, liste kutusu öğeleri birden çok sütun görüntüler ve yatay kaydırma çubuğu görüntülenir. Zaman <xref:System.Windows.Forms.ListBox.MultiColumn%2A> özelliği ayarlanmış `false`, liste kutusu öğeleri tek bir sütunda görüntüler ve dikey kaydırma çubuğu görüntülenir. Zaman <xref:System.Windows.Forms.ListBox.ScrollAlwaysVisible%2A> ayarlanır `true`, öğelerin sayısı bağımsız olarak kaydırma çubuğu görüntülenir. <xref:System.Windows.Forms.ListBox.SelectionMode%2A> Özelliği, aynı anda kaç liste öğeleri seçilebilir belirler.  
  
## <a name="ways-to-change-the-listbox-control"></a>ListBox denetimi değiştirme yolları  
 <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> Özelliği, liste kutusunda seçili bir ilk öğesine karşılık gelen bir tamsayı değeri döndürür. Seçili öğeyi değiştirerek program aracılığıyla değiştirebilirsiniz <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> değer kodda; listesinde karşılık gelen öğe Windows formunda vurgulu olarak gösterilir. Öğe seçiliyse, <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> değer -1'dir. Listedeki ilk öğe seçiliyse, <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> değer: 0. Birden çok öğe seçildiğinde, <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> değeri, listedeki ilk görünen seçilen öğeyi yansıtır. <xref:System.Windows.Forms.ListBox.SelectedItem%2A> Özelliği benzer <xref:System.Windows.Forms.ListBox.SelectedIndex%2A>, ancak öğenin kendisini, genellikle bir string değeri döndürür. <xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A> Özelliği yansıtır liste öğelerinin sayısını ve değerini <xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A> özelliktir her zaman bir birden çok büyük olası <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> çünkü değer <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> sıfır tabanlı olduğundan.  
  
 Ekleme veya öğeleri silmek için bir <xref:System.Windows.Forms.ListBox> denetlemek, kullanın <xref:System.Windows.Forms.ListBox.ObjectCollection.Add%2A>, <xref:System.Windows.Forms.ListBox.ObjectCollection.Insert%2A>, <xref:System.Windows.Forms.ListBox.ObjectCollection.Clear%2A> veya <xref:System.Windows.Forms.ListBox.ObjectCollection.Remove%2A> yöntemi. Alternatif olarak, öğeleri listede kullanarak ekleyebileceğiniz <xref:System.Windows.Forms.ListBox.Items%2A> tasarım zamanında özelliği.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ListBox>  
 [Nasıl yapılır: ekleme ve kaldırma öğeleri bir Windows Forms ComboBox, ListBox veya CheckedListBox denetimi](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)  
 [Nasıl yapılır: bir Windows içeriğini sıralama Forms ComboBox, ListBox veya CheckedListBox denetimi](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)  
 [Nasıl yapılır: Windows Forms ComboBox veya ListBox denetimini verilere bağlama](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)  
 [ComboBox denetimine genel bakış](../../../../docs/framework/winforms/controls/combobox-control-overview-windows-forms.md)  
 [CheckedListBox denetimine genel bakış](../../../../docs/framework/winforms/controls/checkedlistbox-control-overview-windows-forms.md)  
 [Windows Forms denetimleri seçenekleri listelemek için kullanılır](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)  
 [Nasıl yapılır: Windows Forms ComboBox, ListBox veya CheckedListBox denetimi için arama tablosu oluşturma](../../../../docs/framework/winforms/controls/create-a-lookup-table-for-a-wf-combobox-listbox.md)
