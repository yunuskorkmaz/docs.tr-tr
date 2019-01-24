---
title: 'Nasıl yapılır: Özel erişim öğeleri bir Windows Forms ComboBox, ListBox veya CheckedListBox denetimi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ComboBox control [Windows Forms], accessing items
- ListBox control [Windows Forms], returning item information
- list boxes [Windows Forms], accessing items
- ListBox control [Windows Forms], accessing items
- combo boxes [Windows Forms], accessing items
- CheckedListBox control [Windows Forms], accessing items
ms.assetid: 1216742f-bcf9-4ff8-8a62-d7c9053c2b96
ms.openlocfilehash: b6478c24550f9f32ea75899521f7aa610ef12955
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54656706"
---
# <a name="how-to-access-specific-items-in-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a>Nasıl yapılır: Özel erişim öğeleri bir Windows Forms ComboBox, ListBox veya CheckedListBox denetimi
Bir Windows Forms birleşik giriş kutusu, liste kutusu ya da işaretli liste kutusu belirli öğeleri erişme önemli bir görevdir. Bir listenin herhangi bir konuma nedir programlı bir şekilde belirlemenizi sağlar.  
  
### <a name="to-access-a-specific-item"></a>Belirli bir öğeye erişmek için  
  
1.  Sorgu `Items` belirli öğenin dizinini kullanarak koleksiyon:  
  
    ```vb  
    Private Function GetItemText(i As Integer) As String  
       ' Return the text of the item using the index:  
       Return ComboBox1.Items(i).ToString  
    End Function  
    ```  
  
    ```csharp  
    private string GetItemText(int i)  
    {  
       // Return the text of the item using the index:  
       return (comboBox1.Items[i].ToString());  
    }  
    ```  
  
    ```cpp  
    private:  
       String^ GetItemText(int i)  
       {  
          // Return the text of the item using the index:  
          return (comboBox1->Items->Item[i]->ToString());  
       }  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms.CheckedListBox>
- [Seçenekleri Listelemede Kullanılan Windows Forms Denetimleri](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
