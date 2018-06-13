---
title: ListBox Yerine Ne Zaman Windows Forms ComboBox Kullanılır?
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
ms.openlocfilehash: 88b6a6023fbfdd8fa315fcd434357626ea69a9ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537774"
---
# <a name="when-to-use-a-windows-forms-combobox-instead-of-a-listbox"></a>ListBox Yerine Ne Zaman Windows Forms ComboBox Kullanılır?
<xref:System.Windows.Forms.ComboBox> Ve <xref:System.Windows.Forms.ListBox> denetimleri benzer davranışları sahiptir ve bazı durumlarda değiştirilebilir. Bir ya da başka bir görev için daha uygun olduğunda zamanlar vardır.  
  
 Genellikle, önerilen seçenek listesini yoktur ve listede nedir için giriş sınırlama getirmek istediğinizde bir liste kutusu uygun olduğunda bir birleşik giriş kutusu uygundur. Birleşik giriş kutusu bir metin kutusu alanı içerdiğinden, listede olmayan seçimler yazılabilir. Özel durum olduğunda <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> özelliği ayarlanmış <xref:System.Windows.Forms.ComboBoxStyle.DropDownList>. Bu durumda, ilk harfi yazarsanız denetimi bir öğe seçin.  
  
 Ayrıca, birleşik giriş kutuları, bir form üzerinde alanı kaydedin. Aşağı oka kullanıcı kadar tam listesi görüntülenmeyen için birleşik giriş kutusu kolayca bir liste kutusu değil nerelerde küçük bir alanda uygun olamaz. Bir özel durum olduğunda <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> özelliği ayarlanmış <xref:System.Windows.Forms.ComboBoxStyle.Simple>: tam listesi görüntülenir ve birleşik giriş kutusu bir liste kutusu olduğundan daha fazla yer alır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ComboBox>  
 <xref:System.Windows.Forms.ListBox>  
 [Nasıl yapılır: Bir Windows Forms ComboBox, ListBox veya CheckedListBox Denetiminde Öğe Ekleme ve Kaldırma](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)  
 [Nasıl yapılır: Windows Forms ComboBox, ListBox veya CheckedListBox Denetiminin İçeriğini Sıralama](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)  
 [Seçenekleri Listelemede Kullanılan Windows Forms Denetimleri](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
