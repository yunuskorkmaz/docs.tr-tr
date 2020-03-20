---
title: CheckedListBox Denetiminde İşaretlenmiş Öğeleri Belirleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- check boxes [Windows Forms], determining checked state
- CheckedListBox control [Windows Forms], determining checked state
ms.assetid: 178b477d-27c9-489c-8914-44a9623a4d41
ms.openlocfilehash: 5d93a63e9c1c6aae91ecfe83590c59450a565afe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182197"
---
# <a name="how-to-determine-checked-items-in-the-windows-forms-checkedlistbox-control"></a>Nasıl yapılır: Windows Forms CheckedListBox Denetimindeki İşaretli Öğeleri Belirleme
Windows Forms <xref:System.Windows.Forms.CheckedListBox> denetiminde veri sunarken, <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> özellikte depolanan koleksiyonda yineleyebilir veya hangi öğelerin <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> denetlenebileceğini belirlemek için yöntemi kullanarak listeyi karıştırabilirsiniz. Yöntem <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> bağımsız değişkenolarak bir madde dizin numarası alır ve döndürür `true` veya `false`. Tahmin edebileceğinizin aksine, <xref:System.Windows.Forms.ListBox.SelectedItems%2A> ve <xref:System.Windows.Forms.ListBox.SelectedIndices%2A> özellikleri hangi öğelerin denetlenir belirlemez; hangi öğelerin vurgulanalı olduğunu belirlerler.  
  
### <a name="to-determine-checked-items-in-a-checkedlistbox-control"></a>CheckedListBox denetiminde denetlenen öğeleri belirlemek için  
  
1. <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> Koleksiyon sıfır tabanlı olduğundan, 0'dan başlayarak koleksiyon da yineleyin. Bu yöntemin, genel listede değil, denetlenen öğeler listesindeki madde numarasını vereceğini unutmayın. Bu nedenle, listedeki ilk öğe işaretlenmez ve ikinci öğe işaretlenirse, aşağıdaki kod "İşaretlenmiş Madde 1 = MyListItem2" gibi bir metin görüntüler.  
  
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
  
2. <xref:System.Windows.Forms.CheckedListBox.Items%2A> Koleksiyon sıfır tabanlı olduğundan 0'dan başlayarak koleksiyona adım <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> atın ve her öğe için yöntemi arayın. Bu yöntemin size genel listedeki madde numarasını vereceğini, bu nedenle listedeki ilk öğe işaretlenmezse ve ikinci öğe işaretlenirse, "Item 2 = MyListItem2" gibi bir şey görüntülemeyeceğini unutmayın.  
  
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
