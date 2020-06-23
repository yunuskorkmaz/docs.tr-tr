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
# <a name="how-to-add-and-remove-items-from-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a><span data-ttu-id="b81b7-103">Nasıl yapılır: Bir Windows Forms ComboBox, ListBox veya CheckedListBox Denetiminde Öğe Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="b81b7-103">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>
<span data-ttu-id="b81b7-104">Öğeler çeşitli yollarla Windows Forms Birleşik giriş kutusu, liste kutusu veya denetlenen liste kutusuna eklenebilir, çünkü bu denetimler çeşitli veri kaynaklarına bağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="b81b7-104">Items can be added to a Windows Forms combo box, list box, or checked list box in a variety of ways, because these controls can be bound to a variety of data sources.</span></span> <span data-ttu-id="b81b7-105">Ancak, bu konuda en basit yöntem gösterilmektedir ve veri bağlama gerekmez.</span><span class="sxs-lookup"><span data-stu-id="b81b7-105">However, this topic demonstrates the simplest method and requires no data binding.</span></span> <span data-ttu-id="b81b7-106">Görüntülenen öğeler genellikle dizelerdir; Ancak, herhangi bir nesne kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b81b7-106">The items displayed are usually strings; however, any object can be used.</span></span> <span data-ttu-id="b81b7-107">Denetimde görüntülenen metin, nesnenin yönteminin döndürdüğü değerdir `ToString` .</span><span class="sxs-lookup"><span data-stu-id="b81b7-107">The text that is displayed in the control is the value returned by the object's `ToString` method.</span></span>  
  
### <a name="to-add-items"></a><span data-ttu-id="b81b7-108">Öğe eklemek için</span><span class="sxs-lookup"><span data-stu-id="b81b7-108">To add items</span></span>  
  
1. <span data-ttu-id="b81b7-109">Sınıfının yöntemini kullanarak dize veya nesneyi listeye ekleyin `Add` `ObjectCollection` .</span><span class="sxs-lookup"><span data-stu-id="b81b7-109">Add the string or object to the list by using the `Add` method of the `ObjectCollection` class.</span></span> <span data-ttu-id="b81b7-110">Koleksiyonda, özelliği kullanılarak başvurulur `Items` :</span><span class="sxs-lookup"><span data-stu-id="b81b7-110">The collection is referenced using the `Items` property:</span></span>  
  
    ```vb  
    ComboBox1.Items.Add("Tokyo")  
    ```  
  
    ```csharp  
    comboBox1.Items.Add("Tokyo");  
    ```  
  
    ```cpp  
    comboBox1->Items->Add("Tokyo");  
    ```  
  
     - <span data-ttu-id="b81b7-111">veya</span><span class="sxs-lookup"><span data-stu-id="b81b7-111">or -</span></span>  
  
2. <span data-ttu-id="b81b7-112">Listedeki istenen noktada dize veya nesneyi, yöntemiyle birlikte ekleyin `Insert` :</span><span class="sxs-lookup"><span data-stu-id="b81b7-112">Insert the string or object at the desired point in the list with the `Insert` method:</span></span>  
  
    ```vb  
    CheckedListBox1.Items.Insert(0, "Copenhagen")  
    ```  
  
    ```csharp  
    checkedListBox1.Items.Insert(0, "Copenhagen");  
    ```  
  
    ```cpp  
    checkedListBox1->Items->Insert(0, "Copenhagen");  
    ```  
  
     - <span data-ttu-id="b81b7-113">veya</span><span class="sxs-lookup"><span data-stu-id="b81b7-113">or -</span></span>  
  
3. <span data-ttu-id="b81b7-114">Koleksiyona tüm diziyi atama `Items` :</span><span class="sxs-lookup"><span data-stu-id="b81b7-114">Assign an entire array to the `Items` collection:</span></span>  
  
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
  
### <a name="to-remove-an-item"></a><span data-ttu-id="b81b7-115">Bir öğeyi kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="b81b7-115">To remove an item</span></span>  
  
1. <span data-ttu-id="b81b7-116">`Remove` `RemoveAt` Öğeleri silmek için veya metodunu çağırın.</span><span class="sxs-lookup"><span data-stu-id="b81b7-116">Call the `Remove` or `RemoveAt` method to delete items.</span></span>  
  
     <span data-ttu-id="b81b7-117">`Remove`Kaldırılacak öğeyi belirten bir bağımsız değişkeni vardır.`RemoveAt`</span><span class="sxs-lookup"><span data-stu-id="b81b7-117">`Remove` has one argument that specifies the item to remove.`RemoveAt`</span></span> <span data-ttu-id="b81b7-118">Belirtilen dizin numarasına sahip öğeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="b81b7-118">removes the item with the specified index number.</span></span>  
  
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
  
### <a name="to-remove-all-items"></a><span data-ttu-id="b81b7-119">Tüm öğeleri kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="b81b7-119">To remove all items</span></span>  
  
1. <span data-ttu-id="b81b7-120">`Clear`Koleksiyondan tüm öğeleri kaldırmak için yöntemini çağırın:</span><span class="sxs-lookup"><span data-stu-id="b81b7-120">Call the `Clear` method to remove all items from the collection:</span></span>  
  
    ```vb  
    ListBox1.Items.Clear()  
    ```  
  
    ```csharp  
    listBox1.Items.Clear();  
    ```  
  
    ```cpp  
    listBox1->Items->Clear();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b81b7-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b81b7-121">See also</span></span>

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms.CheckedListBox>
- [<span data-ttu-id="b81b7-122">Nasıl yapılır: Windows Forms ComboBox, ListBox veya CheckedListBox Denetiminin İçeriğini Sıralama</span><span class="sxs-lookup"><span data-stu-id="b81b7-122">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [<span data-ttu-id="b81b7-123">ListBox Yerine Ne Zaman Windows Forms ComboBox Kullanılır?</span><span class="sxs-lookup"><span data-stu-id="b81b7-123">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)
- [<span data-ttu-id="b81b7-124">Seçenekleri Listelemede Kullanılan Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="b81b7-124">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
