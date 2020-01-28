---
title: ComboBox, ListBox veya CheckedListBox denetiminden öğe ekleme ve kaldırma
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
ms.openlocfilehash: 3a83d98af42386b566b4af7bc11ff383dea8fd6b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746297"
---
# <a name="how-to-add-and-remove-items-from-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a><span data-ttu-id="8b81e-102">Nasıl yapılır: Bir Windows Forms ComboBox, ListBox veya CheckedListBox Denetiminde Öğe Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="8b81e-102">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>
<span data-ttu-id="8b81e-103">Öğeler çeşitli yollarla Windows Forms Birleşik giriş kutusu, liste kutusu veya denetlenen liste kutusuna eklenebilir, çünkü bu denetimler çeşitli veri kaynaklarına bağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="8b81e-103">Items can be added to a Windows Forms combo box, list box, or checked list box in a variety of ways, because these controls can be bound to a variety of data sources.</span></span> <span data-ttu-id="8b81e-104">Ancak, bu konuda en basit yöntem gösterilmektedir ve veri bağlama gerekmez.</span><span class="sxs-lookup"><span data-stu-id="8b81e-104">However, this topic demonstrates the simplest method and requires no data binding.</span></span> <span data-ttu-id="8b81e-105">Görüntülenen öğeler genellikle dizelerdir; Ancak, herhangi bir nesne kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8b81e-105">The items displayed are usually strings; however, any object can be used.</span></span> <span data-ttu-id="8b81e-106">Denetimde görüntülenen metin, nesnenin `ToString` yöntemi tarafından döndürülen değerdir.</span><span class="sxs-lookup"><span data-stu-id="8b81e-106">The text that is displayed in the control is the value returned by the object's `ToString` method.</span></span>  
  
### <a name="to-add-items"></a><span data-ttu-id="8b81e-107">Öğe eklemek için</span><span class="sxs-lookup"><span data-stu-id="8b81e-107">To add items</span></span>  
  
1. <span data-ttu-id="8b81e-108">`ObjectCollection` sınıfının `Add` yöntemini kullanarak dize veya nesneyi listeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8b81e-108">Add the string or object to the list by using the `Add` method of the `ObjectCollection` class.</span></span> <span data-ttu-id="8b81e-109">Koleksiyona `Items` özelliği kullanılarak başvurulur:</span><span class="sxs-lookup"><span data-stu-id="8b81e-109">The collection is referenced using the `Items` property:</span></span>  
  
    ```vb  
    ComboBox1.Items.Add("Tokyo")  
    ```  
  
    ```csharp  
    comboBox1.Items.Add("Tokyo");  
    ```  
  
    ```cpp  
    comboBox1->Items->Add("Tokyo");  
    ```  
  
     - <span data-ttu-id="8b81e-110">veya -</span><span class="sxs-lookup"><span data-stu-id="8b81e-110">or -</span></span>  
  
2. <span data-ttu-id="8b81e-111">`Insert` yöntemi ile listedeki istenen noktada dize veya nesne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8b81e-111">Insert the string or object at the desired point in the list with the `Insert` method:</span></span>  
  
    ```vb  
    CheckedListBox1.Items.Insert(0, "Copenhagen")  
    ```  
  
    ```csharp  
    checkedListBox1.Items.Insert(0, "Copenhagen");  
    ```  
  
    ```cpp  
    checkedListBox1->Items->Insert(0, "Copenhagen");  
    ```  
  
     - <span data-ttu-id="8b81e-112">veya -</span><span class="sxs-lookup"><span data-stu-id="8b81e-112">or -</span></span>  
  
3. <span data-ttu-id="8b81e-113">Tüm diziyi `Items` koleksiyonuna ata:</span><span class="sxs-lookup"><span data-stu-id="8b81e-113">Assign an entire array to the `Items` collection:</span></span>  
  
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
  
### <a name="to-remove-an-item"></a><span data-ttu-id="8b81e-114">Bir öğeyi kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="8b81e-114">To remove an item</span></span>  
  
1. <span data-ttu-id="8b81e-115">Öğeleri silmek için `Remove` veya `RemoveAt` metodunu çağırın.</span><span class="sxs-lookup"><span data-stu-id="8b81e-115">Call the `Remove` or `RemoveAt` method to delete items.</span></span>  
  
     <span data-ttu-id="8b81e-116">`Remove` Kaldırılacak öğeyi belirten bir bağımsız değişken içeriyor.`RemoveAt`</span><span class="sxs-lookup"><span data-stu-id="8b81e-116">`Remove` has one argument that specifies the item to remove.`RemoveAt`</span></span> <span data-ttu-id="8b81e-117">Belirtilen dizin numarasına sahip öğeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="8b81e-117">removes the item with the specified index number.</span></span>  
  
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
  
### <a name="to-remove-all-items"></a><span data-ttu-id="8b81e-118">Tüm öğeleri kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="8b81e-118">To remove all items</span></span>  
  
1. <span data-ttu-id="8b81e-119">Koleksiyondaki tüm öğeleri kaldırmak için `Clear` yöntemini çağırın:</span><span class="sxs-lookup"><span data-stu-id="8b81e-119">Call the `Clear` method to remove all items from the collection:</span></span>  
  
    ```vb  
    ListBox1.Items.Clear()  
    ```  
  
    ```csharp  
    listBox1.Items.Clear();  
    ```  
  
    ```cpp  
    listBox1->Items->Clear();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8b81e-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b81e-120">See also</span></span>

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms.CheckedListBox>
- [<span data-ttu-id="8b81e-121">Nasıl yapılır: Windows Forms ComboBox, ListBox veya CheckedListBox Denetiminin İçeriğini Sıralama</span><span class="sxs-lookup"><span data-stu-id="8b81e-121">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [<span data-ttu-id="8b81e-122">ListBox Yerine Ne Zaman Windows Forms ComboBox Kullanılır?</span><span class="sxs-lookup"><span data-stu-id="8b81e-122">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)
- [<span data-ttu-id="8b81e-123">Seçenekleri Listelemede Kullanılan Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="8b81e-123">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
