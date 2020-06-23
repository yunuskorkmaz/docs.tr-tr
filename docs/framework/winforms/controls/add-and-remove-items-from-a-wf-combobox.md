---
title: ComboBox, ListBox veya CheckedListBox denetiminden öğe ekleme ve kaldırma
ms.date: 03/30/2017
description: Veri bağlama olmadan yalnızca Windows Forms ComboBox, ListBox ve CheckedListBox denetimleri ekleme ve kaldırma hakkında bilgi edinin.
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
ms.openlocfilehash: f3701257bbe410bf03c4c21700705e87b581bf2e
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904448"
---
# <a name="how-to-add-and-remove-items-from-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a>Nasıl yapılır: Bir Windows Forms ComboBox, ListBox veya CheckedListBox Denetiminde Öğe Ekleme ve Kaldırma
Öğeler çeşitli yollarla Windows Forms Birleşik giriş kutusu, liste kutusu veya denetlenen liste kutusuna eklenebilir, çünkü bu denetimler çeşitli veri kaynaklarına bağlanabilir. Ancak, bu konuda en basit yöntem gösterilmektedir ve veri bağlama gerekmez. Görüntülenen öğeler genellikle dizelerdir; Ancak, herhangi bir nesne kullanılabilir. Denetimde görüntülenen metin, nesnenin yönteminin döndürdüğü değerdir `ToString` .  
  
### <a name="to-add-items"></a>Öğe eklemek için  
  
1. Sınıfının yöntemini kullanarak dize veya nesneyi listeye ekleyin `Add` `ObjectCollection` . Koleksiyonda, özelliği kullanılarak başvurulur `Items` :  
  
    ```vb  
    ComboBox1.Items.Add("Tokyo")  
    ```  
  
    ```csharp  
    comboBox1.Items.Add("Tokyo");  
    ```  
  
    ```cpp  
    comboBox1->Items->Add("Tokyo");  
    ```  
  
     - veya  
  
2. Listedeki istenen noktada dize veya nesneyi, yöntemiyle birlikte ekleyin `Insert` :  
  
    ```vb  
    CheckedListBox1.Items.Insert(0, "Copenhagen")  
    ```  
  
    ```csharp  
    checkedListBox1.Items.Insert(0, "Copenhagen");  
    ```  
  
    ```cpp  
    checkedListBox1->Items->Insert(0, "Copenhagen");  
    ```  
  
     - veya  
  
3. Koleksiyona tüm diziyi atama `Items` :  
  
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
  
1. `Remove` `RemoveAt` Öğeleri silmek için veya metodunu çağırın.  
  
     `Remove`Kaldırılacak öğeyi belirten bir bağımsız değişkeni vardır.`RemoveAt` Belirtilen dizin numarasına sahip öğeyi kaldırır.  
  
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
  
1. `Clear`Koleksiyondan tüm öğeleri kaldırmak için yöntemini çağırın:  
  
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
