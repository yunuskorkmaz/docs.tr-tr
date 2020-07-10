---
title: ComboBox ve ListBox
description: Windows Forms ComboBox ve Windows Forms ListBox ' ı kullanma hakkında bilgi edinin ve bir görev için bir veya diğerinin ne zaman uygun olduğunu nasıl söyleyeceğinizi öğrenin.
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
ms.openlocfilehash: ca6ad6bec2dbc30128ea09808af2806687b17a8c
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174425"
---
# <a name="when-to-use-a-windows-forms-combobox-instead-of-a-listbox"></a>ListBox Yerine Ne Zaman Windows Forms ComboBox Kullanılır?
<xref:System.Windows.Forms.ComboBox>Ve <xref:System.Windows.Forms.ListBox> denetimlerinin benzer davranışları vardır ve bazı durumlarda bu şekilde değiştirilebilir. Ancak, bir veya diğeri bir göreve daha uygun olduğunda zamanlar vardır.  
  
 Genellikle, bir açılan kutu, önerilen seçeneklerin bir listesi olduğunda uygundur ve girişi listede olacak şekilde sınırlamak istediğinizde bir liste kutusu uygundur. Bir Birleşik giriş kutusu metin kutusu alanı içeriyorsa, listede bulunmayan seçimler içine yazılabilir. Özel durum, <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> özelliğin olarak ayarlandığı durumdur <xref:System.Windows.Forms.ComboBoxStyle.DropDownList> . Bu durumda, ilk harfini yazarsanız denetim bir öğe seçer.  
  
 Ayrıca, Birleşik giriş kutuları bir formdaki alanı kaydeder. Kullanıcı aşağı oka tıklaana kadar tam liste görüntülenmediği için, bir açılan kutu bir liste kutusunun uygun olmadığı küçük bir alana kolayca uyum sağlayabilir. Bir özel durum, <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> özelliğin olarak ayarlandığı durumdur <xref:System.Windows.Forms.ComboBoxStyle.Simple> : tam liste görüntülenir ve Birleşik giriş kutusu bir liste kutusundan daha fazla yer kaplar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [Nasıl yapılır: Bir Windows Forms ComboBox, ListBox veya CheckedListBox Denetiminde Öğe Ekleme ve Kaldırma](add-and-remove-items-from-a-wf-combobox.md)
- [Nasıl yapılır: Windows Forms ComboBox, ListBox veya CheckedListBox Denetiminin İçeriğini Sıralama](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [Seçenekleri Listelemede Kullanılan Windows Forms Denetimleri](windows-forms-controls-used-to-list-options.md)
