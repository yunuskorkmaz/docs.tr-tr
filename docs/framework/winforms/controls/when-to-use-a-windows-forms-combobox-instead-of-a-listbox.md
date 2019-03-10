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
ms.openlocfilehash: 5dc7778f43c01fd28a14489a7b4179dd851568b2
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703003"
---
# <a name="when-to-use-a-windows-forms-combobox-instead-of-a-listbox"></a>ListBox Yerine Ne Zaman Windows Forms ComboBox Kullanılır?
<xref:System.Windows.Forms.ComboBox> Ve <xref:System.Windows.Forms.ListBox> denetimleri benzer davranışlara sahiptir ve bazı durumlarda değiştirilebilir. Bir veya başka bir görev için daha uygun olduğunda zamanlar vardır.  
  
 Genel olarak, önerilen seçenek listesini olduğunda ve listede nedir için giriş sınırlandırmak istediğinizde bir liste kutusunda uygun bir birleşik giriş kutusu uygundur. Listede olmayan seçimler yazılabilir için bir açılan kutunun metin kutusu alanı içerir. Özel durum olduğunda <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> özelliği <xref:System.Windows.Forms.ComboBoxStyle.DropDownList>. Bu durumda, ilk harfinden yazarsanız denetimi bir öğe seçin.  
  
 Ayrıca, birleşik giriş kutuları, form üzerinde alanı kaydedin. Kullanıcı aşağı oka tıklayana kadar tam listesi görüntülenmez için birleşik giriş kutusu liste kutusu değil nerelerde küçük bir alana kolayca uygun olamaz. Bir özel durum olduğunda <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> özelliği <xref:System.Windows.Forms.ComboBoxStyle.Simple>: tam listesi görüntülenir ve birleşik giriş kutusu liste kutusunun olduğu kadar temkinli daha fazla yer alır.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [Nasıl yapılır: Ekleme ve kaldırma öğeleri bir Windows Forms ComboBox, ListBox veya CheckedListBox denetimi](add-and-remove-items-from-a-wf-combobox.md)
- [Nasıl yapılır: Sıralama içeriği bir Windows Forms ComboBox, ListBox veya CheckedListBox denetimi](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [Seçenekleri Listelemede Kullanılan Windows Forms Denetimleri](windows-forms-controls-used-to-list-options.md)
