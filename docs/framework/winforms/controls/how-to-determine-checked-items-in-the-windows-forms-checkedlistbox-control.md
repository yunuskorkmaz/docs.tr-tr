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
ms.openlocfilehash: 98b4ef7c4ac73e1560bd5c68f22898e46585d082
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531020"
---
# <a name="how-to-determine-checked-items-in-the-windows-forms-checkedlistbox-control"></a>Nasıl yapılır: Windows Forms CheckedListBox Denetimindeki İşaretli Öğeleri Belirleme
Windows Forms'ta veri sunma zaman <xref:System.Windows.Forms.CheckedListBox> denetimi, ya da yinelemek depolanan koleksiyonu aracılığıyla <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> özelliği ya da listesini kullanarak aracılığıyla adım <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> hangi öğelerin denetlenir belirlemek amacıyla yöntemi. <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> Yöntem bağımsız değişkeni olarak bir öğe dizin numarasını alıp döndüren `true` veya `false`. Ne bekleyebilir, aykırı <xref:System.Windows.Forms.ListBox.SelectedItems%2A> ve <xref:System.Windows.Forms.ListBox.SelectedIndices%2A> özellikleri değil belirlemek hangi öğelerin denetlenir; bunlar hangi öğeler vurgulanır belirleyin.  
  
### <a name="to-determine-checked-items-in-a-checkedlistbox-control"></a>CheckedListBox denetimindeki işaretli öğeleri belirleme  
  
1.  Yinelemek <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> koleksiyonu sıfır tabanlı olduğundan 0'den başlayan koleksiyonu. Bu yöntem maddeye işaretli öğeleri, genel listesinde olmayan listesinde erişmenizi sağlayan olduğunu unutmayın. Listedeki ilk öğe onaylanmamış ve ikinci madde işaretli değilse, aşağıdaki kodu gibi metin görüntülemesi için "Checked öğesi 1 MyListItem2 =".  
  
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
       for(int x = 0; x <= checkedListBox1.CheckedItems.Count - 1 ; x++)  
       {  
          s = s + "Checked Item " + (x+1).ToString() + " = " + checkedListBox1.CheckedItems[x].ToString() + "\n";  
       }  
    MessageBox.Show (s);  
    }  
    ```  
  
    ```cpp  
    // Determine if there are any items checked.  
    if(checkedListBox1->CheckedItems->Count != 0)  
    {  
       // If so, loop through all checked items and print results.  
       String ^ s = "";  
       for(int x = 0; x <= checkedListBox1->CheckedItems->Count - 1; x++)  
       {  
          s = String::Concat(s, "Checked Item ", (x+1).ToString(),  
             " = ", checkedListBox1->CheckedItems[x]->ToString(),  
             "\n");  
       }  
       MessageBox::Show(s);  
    }  
    ```  
  
     - veya -  
  
2.  Adım adım <xref:System.Windows.Forms.CheckedListBox.Items%2A> koleksiyon, koleksiyon sıfır tabanlı, olduğundan 0'den başlayan ve çağrı <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> her öğe için bir yöntem. Not ilk öğesi, listenin işaretli şekilde bu yöntem, öğe sayısı genel listesinde verir ve ikinci öğe seçildiğinde, aşağıdakine benzer görüntülenir "2 öğesi MyListItem2 =".  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Seçenekleri Listelemede Kullanılan Windows Forms Denetimleri](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
