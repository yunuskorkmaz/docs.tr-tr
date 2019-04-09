---
title: 'Nasıl yapılır: Bir Windows Forms ComboBox, ListBox veya CheckedListBox Denetiminde Öğe Ekleme ve Kaldırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- combo boxes [Windows Forms], adding items
- list boxes [Windows Forms], removing items
- ComboBox control [Windows Forms], adding and removing items
- ListBox control [Windows Forms], adding and removing items
- list boxes [Windows Forms], adding items
- combo boxes [Windows Forms], removing items
- CheckedListBox control [Windows Forms], adding and removing items
ms.assetid: 7224c8d2-4118-443e-ae1e-d7c17d1e69ee
ms.openlocfilehash: 13f1e18753ad5b49a9cc530cf340579087908b4e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59188890"
---
# <a name="how-to-add-and-remove-items-from-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a>Nasıl yapılır: Bir Windows Forms ComboBox, ListBox veya CheckedListBox Denetiminde Öğe Ekleme ve Kaldırma
Öğeleri bir Windows Forms birleşik giriş kutusu liste kutusu eklenebilir veya çeşitli yollarla, liste kutusunda iade, çünkü bu denetimleri bir çeşitli veri kaynaklarına bağlanabilir. Ancak, bu konuda en basit yöntem gösterir ve hiçbir veri bağlama gerektirir. Görüntülenen öğelerin genellikle dizelerdir; Ancak, herhangi bir nesne kullanılabilir. Denetimde görüntülenen metnin nesne tarafından döndürülen değer olduğu `ToString` yöntemi.  
  
### <a name="to-add-items"></a>Öğe eklemek için  
  
1.  Dize veya nesne kullanılarak listeye eklemek `Add` yöntemi `ObjectCollection` sınıfı. Koleksiyon kullanılarak başvurulur `Items` özelliği:  
  
    ```vb  
    ComboBox1.Items.Add("Tokyo")  
    ```  
  
    ```csharp  
    comboBox1.Items.Add("Tokyo");  
    ```  
  
    ```cpp  
    comboBox1->Items->Add("Tokyo");  
    ```  
  
     - veya -  
  
2.  Dize veya nesne ile bir liste içinde istediğiniz noktaya eklemek `Insert` yöntemi:  
  
    ```vb  
    CheckedListBox1.Items.Insert(0, "Copenhagen")  
    ```  
  
    ```csharp  
    checkedListBox1.Items.Insert(0, "Copenhagen");  
    ```  
  
    ```cpp  
    checkedListBox1->Items->Insert(0, "Copenhagen");  
    ```  
  
     - veya -  
  
3.  Tüm bir diziye atama `Items` koleksiyonu:  
  
    ```vb  
    Dim ItemObject(9) As System.Object  
    Dim i As Integer  
       For i = 0 To 9  
       ItemObject(i) = "Item" & i  
    Next i  
    ListBox1.Items.AddRange(ItemObject)  
    ```  
  
    ```csharp  
    System.Object[] ItemObject = new System.Object[10];  
    for (int i = 0; i <= 9; i++)  
    {  
       ItemObject[i] = "Item" + i;  
    }  
    listBox1.Items.AddRange(ItemObject);  
    ```  
  
    ```cpp  
    Array<System::Object^>^ ItemObject = gcnew Array<System::Object^>(10);  
    for (int i = 0; i <= 9; i++)  
    {  
       ItemObject[i] = String::Concat("Item", i.ToString());  
    }  
    listBox1->Items->AddRange(ItemObject);  
    ```  
  
### <a name="to-remove-an-item"></a>Bir öğeyi kaldırmak için  
  
1.  Çağrı `Remove` veya `RemoveAt` öğelerini silmek için yöntemi.  
  
     `Remove` kaldırılacak öğe belirten bir bağımsız değişken var.`RemoveAt` Belirtilen dizin numaralı öğeyi kaldırır.  
  
    ```vb  
    ' To remove item with index 0:  
    ComboBox1.Items.RemoveAt(0)  
    ' To remove currently selected item:  
    ComboBox1.Items.Remove(ComboBox1.SelectedItem)  
    ' To remove "Tokyo" item:  
    ComboBox1.Items.Remove("Tokyo")  
    ```  
  
    ```csharp  
    // To remove item with index 0:  
    comboBox1.Items.RemoveAt(0);  
    // To remove currently selected item:  
    comboBox1.Items.Remove(comboBox1.SelectedItem);  
    // To remove "Tokyo" item:  
    comboBox1.Items.Remove("Tokyo");  
    ```  
  
    ```cpp  
    // To remove item with index 0:  
    comboBox1->Items->RemoveAt(0);  
    // To remove currently selected item:  
    comboBox1->Items->Remove(comboBox1->SelectedItem);  
    // To remove "Tokyo" item:  
    comboBox1->Items->Remove("Tokyo");  
    ```  
  
### <a name="to-remove-all-items"></a>Tüm öğeleri kaldırmak için  
  
1.  Çağrı `Clear` yöntemi tüm öğeleri koleksiyondan kaldırmak için:  
  
    ```vb  
    ListBox1.Items.Clear()  
    ```  
  
    ```csharp  
    listBox1.Items.Clear();  
    ```  
  
    ```cpp  
    listBox1->Items->Clear();  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms.CheckedListBox>
- [Nasıl yapılır: Windows Forms ComboBox, ListBox veya CheckedListBox Denetiminin İçeriğini Sıralama](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [ListBox Yerine Ne Zaman Windows Forms ComboBox Kullanılır?](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)
- [Seçenekleri Listelemede Kullanılan Windows Forms Denetimleri](windows-forms-controls-used-to-list-options.md)
