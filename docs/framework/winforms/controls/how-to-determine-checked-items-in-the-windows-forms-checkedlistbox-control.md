---
title: 'Nasıl yapılır: Windows Forms CheckedListBox Denetimindeki İşaretli Öğeleri Belirleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- check boxes [Windows Forms], determining checked state
- CheckedListBox control [Windows Forms], determining checked state
ms.assetid: 178b477d-27c9-489c-8914-44a9623a4d41
ms.openlocfilehash: 10793053934dce0bb83113004a79f1c265f5f267
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59316576"
---
# <a name="how-to-determine-checked-items-in-the-windows-forms-checkedlistbox-control"></a>Nasıl yapılır: Windows Forms CheckedListBox Denetimindeki İşaretli Öğeleri Belirleme
Bir Windows Forms veri sunarken <xref:System.Windows.Forms.CheckedListBox> denetimi, ya da yineleme depolanan koleksiyonu aracılığıyla <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> özellik ya da liste aracılığıyla adım <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> hangi öğelerin denetlenir belirlemek için yöntemi. <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> Yöntemi ve bağımsız değişkeni olarak bir öğe dizin numarasını alır ve döndürür `true` veya `false`. Beklediğiniz, aykırı <xref:System.Windows.Forms.ListBox.SelectedItems%2A> ve <xref:System.Windows.Forms.ListBox.SelectedIndices%2A> özelliklerini değil belirleme hangi öğelerin denetlenir; hangi öğelerin vurgulanmış belirlerler.  
  
### <a name="to-determine-checked-items-in-a-checkedlistbox-control"></a>CheckedListBox denetimindeki işaretli öğeleri belirleme  
  
1. Yinelemek <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> koleksiyon, koleksiyon sıfır tabanlı olduğundan 0'dan başlayan. Alınan öğeleri, genel liste bu yöntem listesinde öğe sayısını verir dikkat edin. Listedeki ilk öğeye işaretli ve ikinci öğenin kullanıma, aşağıdaki kodu gibi bir metnin görüntülenmesi "işaretlenmiş öğe 1 MyListItem2 =".  
  
    ```vb  
    ' Determine if there are any items checked.  
    If CheckedListBox1.CheckedItems.Count <> 0 Then  
       ' If so, loop through all checked items and print results.  
       Dim x As Integer  
       Dim s As String = ""  
       For x = 0 To CheckedListBox1.CheckedItems.Count - 1  
          s = s & "Checked Item " & (x + 1).ToString & " = " & CheckedListBox1.CheckedItems(x).ToString & ControlChars.CrLf  
       Next x  
       MessageBox.Show(s)  
    End If  
    ```  
  
    ```csharp  
    // Determine if there are any items checked.  
    if(checkedListBox1.CheckedItems.Count != 0)  
    {  
       // If so, loop through all checked items and print results.  
       string s = "";  
       for(int x = 0; x < checkedListBox1.CheckedItems.Count ; x++)  
       {  
          s = s + "Checked Item " + (x+1).ToString() + " = " + checkedListBox1.CheckedItems[x].ToString() + "\n";  
       }  
       MessageBox.Show(s);  
    }  
    ```  
  
    ```cpp  
    // Determine if there are any items checked.  
    if(checkedListBox1->CheckedItems->Count != 0)  
    {  
       // If so, loop through all checked items and print results.  
       String ^ s = "";  
       for(int x = 0; x < checkedListBox1->CheckedItems->Count; x++)  
       {  
          s = String::Concat(s, "Checked Item ", (x+1).ToString(),  
             " = ", checkedListBox1->CheckedItems[x]->ToString(),  
             "\n");  
       }  
       MessageBox::Show(s);  
    }  
    ```  
  
     - veya -  
  
2. Adım adım <xref:System.Windows.Forms.CheckedListBox.Items%2A> koleksiyon, koleksiyon sıfır tabanlı, olduğundan 0'dan başlayan ve çağrı <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> her öğe için yöntemi. Not ilk öğesi, liste işaretli için bu yöntem, öğe sayısı genel listesinde, size sunar ve ikinci öğenin seçili olduğunda, aşağıdaki gibi görüntülenir "öğe 2 MyListItem2 =".  
  
    ```vb  
    Dim i As Integer  
    Dim s As String  
    s = "Checked Items:" & ControlChars.CrLf  
    For i = 0 To (CheckedListBox1.Items.Count - 1)  
       If CheckedListBox1.GetItemChecked(i) = True Then  
          s = s & "Item " & (i + 1).ToString & " = " & CheckedListBox1.Items(i).ToString & ControlChars.CrLf  
       End If  
    Next  
    MessageBox.Show(s)  
    ```  
  
    ```csharp  
    int i;  
    string s;   
    s = "Checked items:\n" ;  
    for (i = 0; i <= (checkedListBox1.Items.Count-1); i++)  
    {  
       if (checkedListBox1.GetItemChecked(i))  
       {  
          s = s + "Item " + (i+1).ToString() + " = " + checkedListBox1.Items[i].ToString() + "\n";  
       }  
    }  
    MessageBox.Show (s);  
    ```  
  
    ```cpp  
    int i;  
    String ^ s;   
    s = "Checked items:\n" ;  
    for (i = 0; i <= (checkedListBox1->Items->Count-1); i++)  
    {  
       if (checkedListBox1->GetItemChecked(i))  
       {  
          s = String::Concat(s, "Item ", (i+1).ToString(), " = ",  
             checkedListBox1->Item[i]->ToString(), "\n");  
       }  
    }  
    MessageBox::Show(s);  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Seçenekleri Listelemede Kullanılan Windows Forms Denetimleri](windows-forms-controls-used-to-list-options.md)
