---
title: ComboBox ve ListBox
ms.date: 03/30/2017
helpviewer_keywords:
- ListBox control [Windows Forms], adding and removing items
- ListBox control [Windows Forms], vs. ComboBox
- bound controls [Windows Forms], combo boxes
- Windows Forms controls, data binding
- ComboBox control [Windows Forms], compared to ListBox
- combo boxes [Windows Forms], compared to list boxes
- ListBox control [Windows Forms], accessing items
- ListCount property
ms.assetid: 7bcaea58-1cfa-46db-9baf-b75a69d8f9ec
ms.openlocfilehash: 7087760a393bb58d83d899c1741c745fb28585bb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739932"
---
# <a name="when-to-use-a-windows-forms-combobox-instead-of-a-listbox"></a>ListBox Yerine Ne Zaman Windows Forms ComboBox Kullanılır?
<xref:System.Windows.Forms.ComboBox> ve <xref:System.Windows.Forms.ListBox> denetimleri benzer davranışlara sahiptir ve bazı durumlarda bu şekilde değiştirilebilir. Ancak, bir veya diğeri bir göreve daha uygun olduğunda zamanlar vardır.  
  
 Genellikle, bir açılan kutu, önerilen seçeneklerin bir listesi olduğunda uygundur ve girişi listede olacak şekilde sınırlamak istediğinizde bir liste kutusu uygundur. Bir Birleşik giriş kutusu metin kutusu alanı içeriyorsa, listede bulunmayan seçimler içine yazılabilir. Bu, <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> özelliğinin <xref:System.Windows.Forms.ComboBoxStyle.DropDownList>olarak ayarlandığı durumdur. Bu durumda, ilk harfini yazarsanız denetim bir öğe seçer.  
  
 Ayrıca, Birleşik giriş kutuları bir formdaki alanı kaydeder. Kullanıcı aşağı oka tıklaana kadar tam liste görüntülenmediği için, bir açılan kutu bir liste kutusunun uygun olmadığı küçük bir alana kolayca uyum sağlayabilir. Bir özel durum, <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> özelliğinin <xref:System.Windows.Forms.ComboBoxStyle.Simple>olarak ayarlandığı durumdur: tam liste görüntülenir ve Birleşik giriş kutusu bir liste kutusundan daha fazla yer kaplar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [Nasıl yapılır: Bir Windows Forms ComboBox, ListBox veya CheckedListBox Denetiminde Öğe Ekleme ve Kaldırma](add-and-remove-items-from-a-wf-combobox.md)
- [Nasıl yapılır: Windows Forms ComboBox, ListBox veya CheckedListBox Denetiminin İçeriğini Sıralama](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [Seçenekleri Listelemede Kullanılan Windows Forms Denetimleri](windows-forms-controls-used-to-list-options.md)
