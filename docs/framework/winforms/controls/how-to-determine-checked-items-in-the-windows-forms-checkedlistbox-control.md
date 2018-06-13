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
# <a name="how-to-determine-checked-items-in-the-windows-forms-checkedlistbox-control"></a><span data-ttu-id="23053-102">Nasıl yapılır: Windows Forms CheckedListBox Denetimindeki İşaretli Öğeleri Belirleme</span><span class="sxs-lookup"><span data-stu-id="23053-102">How to: Determine Checked Items in the Windows Forms CheckedListBox Control</span></span>
<span data-ttu-id="23053-103">Windows Forms'ta veri sunma zaman <xref:System.Windows.Forms.CheckedListBox> denetimi, ya da yinelemek depolanan koleksiyonu aracılığıyla <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> özelliği ya da listesini kullanarak aracılığıyla adım <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> hangi öğelerin denetlenir belirlemek amacıyla yöntemi.</span><span class="sxs-lookup"><span data-stu-id="23053-103">When presenting data in a Windows Forms <xref:System.Windows.Forms.CheckedListBox> control, you can either iterate through the collection stored in the <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> property, or step through the list using the <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> method to determine which items are checked.</span></span> <span data-ttu-id="23053-104"><xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> Yöntem bağımsız değişkeni olarak bir öğe dizin numarasını alıp döndüren `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="23053-104">The <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> method takes an item index number as its argument and returns `true` or `false`.</span></span> <span data-ttu-id="23053-105">Ne bekleyebilir, aykırı <xref:System.Windows.Forms.ListBox.SelectedItems%2A> ve <xref:System.Windows.Forms.ListBox.SelectedIndices%2A> özellikleri değil belirlemek hangi öğelerin denetlenir; bunlar hangi öğeler vurgulanır belirleyin.</span><span class="sxs-lookup"><span data-stu-id="23053-105">Contrary to what you might expect, the <xref:System.Windows.Forms.ListBox.SelectedItems%2A> and <xref:System.Windows.Forms.ListBox.SelectedIndices%2A> properties do not determine which items are checked; they determine which items are highlighted.</span></span>  
  
### <a name="to-determine-checked-items-in-a-checkedlistbox-control"></a><span data-ttu-id="23053-106">CheckedListBox denetimindeki işaretli öğeleri belirleme</span><span class="sxs-lookup"><span data-stu-id="23053-106">To determine checked items in a CheckedListBox control</span></span>  
  
1.  <span data-ttu-id="23053-107">Yinelemek <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> koleksiyonu sıfır tabanlı olduğundan 0'den başlayan koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="23053-107">Iterate through the <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> collection, starting at 0 since the collection is zero-based.</span></span> <span data-ttu-id="23053-108">Bu yöntem maddeye işaretli öğeleri, genel listesinde olmayan listesinde erişmenizi sağlayan olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="23053-108">Note that this method will give you the item number in the list of checked items, not the overall list.</span></span> <span data-ttu-id="23053-109">Listedeki ilk öğe onaylanmamış ve ikinci madde işaretli değilse, aşağıdaki kodu gibi metin görüntülemesi için "Checked öğesi 1 MyListItem2 =".</span><span class="sxs-lookup"><span data-stu-id="23053-109">So if the first item in the list is not checked and the second item is checked, the code below will display text like "Checked Item 1 = MyListItem2".</span></span>  
  
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
  
     - <span data-ttu-id="23053-110">veya -</span><span class="sxs-lookup"><span data-stu-id="23053-110">or -</span></span>  
  
2.  <span data-ttu-id="23053-111">Adım adım <xref:System.Windows.Forms.CheckedListBox.Items%2A> koleksiyon, koleksiyon sıfır tabanlı, olduğundan 0'den başlayan ve çağrı <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> her öğe için bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="23053-111">Step through the <xref:System.Windows.Forms.CheckedListBox.Items%2A> collection, starting at 0 since the collection is zero-based, and call the <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> method for each item.</span></span> <span data-ttu-id="23053-112">Not ilk öğesi, listenin işaretli şekilde bu yöntem, öğe sayısı genel listesinde verir ve ikinci öğe seçildiğinde, aşağıdakine benzer görüntülenir "2 öğesi MyListItem2 =".</span><span class="sxs-lookup"><span data-stu-id="23053-112">Note that this method will give you the item number in the overall list, so if the first item in the list is not checked and the second item is checked, it will display something like "Item 2 = MyListItem2".</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="23053-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="23053-113">See Also</span></span>  
 [<span data-ttu-id="23053-114">Seçenekleri Listelemede Kullanılan Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="23053-114">Windows Forms Controls Used to List Options</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
