---
title: CheckedListBox denetimindeki Işaretli öğeleri belirleme
description: CheckedItems özelliğinde depolanan koleksiyonda yineleme yaparak Windows Forms CheckedListBox denetimindeki işaretli öğeleri belirlemeyi öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- check boxes [Windows Forms], determining checked state
- CheckedListBox control [Windows Forms], determining checked state
ms.assetid: 178b477d-27c9-489c-8914-44a9623a4d41
ms.openlocfilehash: fd8845ef83da7406ff4f1468506a23e3f4d386a0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618356"
---
# <a name="how-to-determine-checked-items-in-the-windows-forms-checkedlistbox-control"></a>Nasıl yapılır: Windows Forms CheckedListBox Denetimindeki İşaretli Öğeleri Belirleme
Verileri bir Windows Forms <xref:System.Windows.Forms.CheckedListBox> denetiminde sunarken, özellikte depolanan koleksiyonda yineleyebilirsiniz <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> ya da <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> hangi öğelerin denetleneceğini belirleyen yöntemi kullanarak listede ilerleyebilir. <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A>Yöntemi bağımsız değişkeni olarak bir öğe dizin numarası alır ve veya döndürür `true` `false` . Beklediğiniz öğelerin aksine, <xref:System.Windows.Forms.ListBox.SelectedItems%2A> ve <xref:System.Windows.Forms.ListBox.SelectedIndices%2A> özellikleri hangi öğelerin denetleneceğini tespit etmez; hangi öğelerin vurgulandığı belirlenir.  
  
### <a name="to-determine-checked-items-in-a-checkedlistbox-control"></a>CheckedListBox denetimindeki işaretli öğeleri belirleme  
  
1. <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A>Koleksiyon sıfır tabanlı olduğundan, toplama işlemi 0 ' dan başlayarak yineleyin. Bu yöntemin, genel liste değil, denetlenen öğeler listesindeki öğe numarasını sunyacağını unutmayın. Bu nedenle, listedeki ilk öğe denetlenmez ve ikinci öğe işaretliyse, aşağıdaki kod "Checked Item 1 = MyListItem2" gibi metni görüntüler.  
  
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
  
     - veya  
  
2. Koleksiyon <xref:System.Windows.Forms.CheckedListBox.Items%2A> sıfır tabanlı olduğundan koleksiyonda ilerleyin ve <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> her öğe için yöntemi çağırın. Bu yöntemin genel listedeki öğe numarasını sunyacağını unutmayın. bu nedenle, listedeki ilk öğe denetlenmez ve ikinci öğe denetlendiğinde, "öğe 2 = MyListItem2" gibi bir şey görüntülenir.  
  
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
