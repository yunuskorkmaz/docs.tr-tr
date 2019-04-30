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
ms.openlocfilehash: bd6614c76c63a44a7367ac7c7113c4db260c9a02
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61640449"
---
# <a name="how-to-add-and-remove-items-from-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a><span data-ttu-id="0d260-102">Nasıl yapılır: Bir Windows Forms ComboBox, ListBox veya CheckedListBox Denetiminde Öğe Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="0d260-102">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>
<span data-ttu-id="0d260-103">Öğeleri bir Windows Forms birleşik giriş kutusu liste kutusu eklenebilir veya çeşitli yollarla, liste kutusunda iade, çünkü bu denetimleri bir çeşitli veri kaynaklarına bağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="0d260-103">Items can be added to a Windows Forms combo box, list box, or checked list box in a variety of ways, because these controls can be bound to a variety of data sources.</span></span> <span data-ttu-id="0d260-104">Ancak, bu konuda en basit yöntem gösterir ve hiçbir veri bağlama gerektirir.</span><span class="sxs-lookup"><span data-stu-id="0d260-104">However, this topic demonstrates the simplest method and requires no data binding.</span></span> <span data-ttu-id="0d260-105">Görüntülenen öğelerin genellikle dizelerdir; Ancak, herhangi bir nesne kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0d260-105">The items displayed are usually strings; however, any object can be used.</span></span> <span data-ttu-id="0d260-106">Denetimde görüntülenen metnin nesne tarafından döndürülen değer olduğu `ToString` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0d260-106">The text that is displayed in the control is the value returned by the object's `ToString` method.</span></span>  
  
### <a name="to-add-items"></a><span data-ttu-id="0d260-107">Öğe eklemek için</span><span class="sxs-lookup"><span data-stu-id="0d260-107">To add items</span></span>  
  
1. <span data-ttu-id="0d260-108">Dize veya nesne kullanılarak listeye eklemek `Add` yöntemi `ObjectCollection` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0d260-108">Add the string or object to the list by using the `Add` method of the `ObjectCollection` class.</span></span> <span data-ttu-id="0d260-109">Koleksiyon kullanılarak başvurulur `Items` özelliği:</span><span class="sxs-lookup"><span data-stu-id="0d260-109">The collection is referenced using the `Items` property:</span></span>  
  
    ```vb  
    ComboBox1.Items.Add("Tokyo")  
    ```  
  
    ```csharp  
    comboBox1.Items.Add("Tokyo");  
    ```  
  
    ```cpp  
    comboBox1->Items->Add("Tokyo");  
    ```  
  
     - <span data-ttu-id="0d260-110">veya -</span><span class="sxs-lookup"><span data-stu-id="0d260-110">or -</span></span>  
  
2. <span data-ttu-id="0d260-111">Dize veya nesne ile bir liste içinde istediğiniz noktaya eklemek `Insert` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="0d260-111">Insert the string or object at the desired point in the list with the `Insert` method:</span></span>  
  
    ```vb  
    CheckedListBox1.Items.Insert(0, "Copenhagen")  
    ```  
  
    ```csharp  
    checkedListBox1.Items.Insert(0, "Copenhagen");  
    ```  
  
    ```cpp  
    checkedListBox1->Items->Insert(0, "Copenhagen");  
    ```  
  
     - <span data-ttu-id="0d260-112">veya -</span><span class="sxs-lookup"><span data-stu-id="0d260-112">or -</span></span>  
  
3. <span data-ttu-id="0d260-113">Tüm bir diziye atama `Items` koleksiyonu:</span><span class="sxs-lookup"><span data-stu-id="0d260-113">Assign an entire array to the `Items` collection:</span></span>  
  
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
  
### <a name="to-remove-an-item"></a><span data-ttu-id="0d260-114">Bir öğeyi kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="0d260-114">To remove an item</span></span>  
  
1. <span data-ttu-id="0d260-115">Çağrı `Remove` veya `RemoveAt` öğelerini silmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0d260-115">Call the `Remove` or `RemoveAt` method to delete items.</span></span>  
  
     <span data-ttu-id="0d260-116">`Remove` kaldırılacak öğe belirten bir bağımsız değişken var.`RemoveAt`</span><span class="sxs-lookup"><span data-stu-id="0d260-116">`Remove` has one argument that specifies the item to remove.`RemoveAt`</span></span> <span data-ttu-id="0d260-117">Belirtilen dizin numaralı öğeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="0d260-117">removes the item with the specified index number.</span></span>  
  
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
  
### <a name="to-remove-all-items"></a><span data-ttu-id="0d260-118">Tüm öğeleri kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="0d260-118">To remove all items</span></span>  
  
1. <span data-ttu-id="0d260-119">Çağrı `Clear` yöntemi tüm öğeleri koleksiyondan kaldırmak için:</span><span class="sxs-lookup"><span data-stu-id="0d260-119">Call the `Clear` method to remove all items from the collection:</span></span>  
  
    ```vb  
    ListBox1.Items.Clear()  
    ```  
  
    ```csharp  
    listBox1.Items.Clear();  
    ```  
  
    ```cpp  
    listBox1->Items->Clear();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="0d260-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d260-120">See also</span></span>

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms.CheckedListBox>
- [<span data-ttu-id="0d260-121">Nasıl yapılır: Sıralama içeriği bir Windows Forms ComboBox, ListBox veya CheckedListBox denetimi</span><span class="sxs-lookup"><span data-stu-id="0d260-121">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [<span data-ttu-id="0d260-122">ListBox Yerine Ne Zaman Windows Forms ComboBox Kullanılır?</span><span class="sxs-lookup"><span data-stu-id="0d260-122">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)
- [<span data-ttu-id="0d260-123">Seçenekleri Listelemede Kullanılan Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="0d260-123">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
