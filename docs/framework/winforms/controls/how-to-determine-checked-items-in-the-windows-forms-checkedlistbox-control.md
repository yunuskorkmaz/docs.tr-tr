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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59316576"
---
# <a name="how-to-determine-checked-items-in-the-windows-forms-checkedlistbox-control"></a><span data-ttu-id="9fdea-102">Nasıl yapılır: Windows Forms CheckedListBox Denetimindeki İşaretli Öğeleri Belirleme</span><span class="sxs-lookup"><span data-stu-id="9fdea-102">How to: Determine Checked Items in the Windows Forms CheckedListBox Control</span></span>
<span data-ttu-id="9fdea-103">Bir Windows Forms veri sunarken <xref:System.Windows.Forms.CheckedListBox> denetimi, ya da yineleme depolanan koleksiyonu aracılığıyla <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> özellik ya da liste aracılığıyla adım <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> hangi öğelerin denetlenir belirlemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9fdea-103">When presenting data in a Windows Forms <xref:System.Windows.Forms.CheckedListBox> control, you can either iterate through the collection stored in the <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> property, or step through the list using the <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> method to determine which items are checked.</span></span> <span data-ttu-id="9fdea-104"><xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> Yöntemi ve bağımsız değişkeni olarak bir öğe dizin numarasını alır ve döndürür `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="9fdea-104">The <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> method takes an item index number as its argument and returns `true` or `false`.</span></span> <span data-ttu-id="9fdea-105">Beklediğiniz, aykırı <xref:System.Windows.Forms.ListBox.SelectedItems%2A> ve <xref:System.Windows.Forms.ListBox.SelectedIndices%2A> özelliklerini değil belirleme hangi öğelerin denetlenir; hangi öğelerin vurgulanmış belirlerler.</span><span class="sxs-lookup"><span data-stu-id="9fdea-105">Contrary to what you might expect, the <xref:System.Windows.Forms.ListBox.SelectedItems%2A> and <xref:System.Windows.Forms.ListBox.SelectedIndices%2A> properties do not determine which items are checked; they determine which items are highlighted.</span></span>  
  
### <a name="to-determine-checked-items-in-a-checkedlistbox-control"></a><span data-ttu-id="9fdea-106">CheckedListBox denetimindeki işaretli öğeleri belirleme</span><span class="sxs-lookup"><span data-stu-id="9fdea-106">To determine checked items in a CheckedListBox control</span></span>  
  
1. <span data-ttu-id="9fdea-107">Yinelemek <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> koleksiyon, koleksiyon sıfır tabanlı olduğundan 0'dan başlayan.</span><span class="sxs-lookup"><span data-stu-id="9fdea-107">Iterate through the <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> collection, starting at 0 since the collection is zero-based.</span></span> <span data-ttu-id="9fdea-108">Alınan öğeleri, genel liste bu yöntem listesinde öğe sayısını verir dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="9fdea-108">Note that this method will give you the item number in the list of checked items, not the overall list.</span></span> <span data-ttu-id="9fdea-109">Listedeki ilk öğeye işaretli ve ikinci öğenin kullanıma, aşağıdaki kodu gibi bir metnin görüntülenmesi "işaretlenmiş öğe 1 MyListItem2 =".</span><span class="sxs-lookup"><span data-stu-id="9fdea-109">So if the first item in the list is not checked and the second item is checked, the code below will display text like "Checked Item 1 = MyListItem2".</span></span>  
  
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
  
     - <span data-ttu-id="9fdea-110">veya -</span><span class="sxs-lookup"><span data-stu-id="9fdea-110">or -</span></span>  
  
2. <span data-ttu-id="9fdea-111">Adım adım <xref:System.Windows.Forms.CheckedListBox.Items%2A> koleksiyon, koleksiyon sıfır tabanlı, olduğundan 0'dan başlayan ve çağrı <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> her öğe için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9fdea-111">Step through the <xref:System.Windows.Forms.CheckedListBox.Items%2A> collection, starting at 0 since the collection is zero-based, and call the <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> method for each item.</span></span> <span data-ttu-id="9fdea-112">Not ilk öğesi, liste işaretli için bu yöntem, öğe sayısı genel listesinde, size sunar ve ikinci öğenin seçili olduğunda, aşağıdaki gibi görüntülenir "öğe 2 MyListItem2 =".</span><span class="sxs-lookup"><span data-stu-id="9fdea-112">Note that this method will give you the item number in the overall list, so if the first item in the list is not checked and the second item is checked, it will display something like "Item 2 = MyListItem2".</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9fdea-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9fdea-113">See also</span></span>

- [<span data-ttu-id="9fdea-114">Seçenekleri Listelemede Kullanılan Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="9fdea-114">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
