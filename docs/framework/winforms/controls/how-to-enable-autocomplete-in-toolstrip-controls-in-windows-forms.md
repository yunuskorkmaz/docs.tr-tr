---
title: 'Nasıl yapılır: ToolStrip Denetiminde AutoComplete Seçeneğini Etkinleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AutoComplete [Windows Forms], examples
- toolbars [Windows Forms], AutoComplete
- examples [Windows Forms], toolbars
- AutoComplete [Windows Forms], enabling in toolbars
- ToolStripComboBox class [Windows Forms], examples
- ToolStrip control [Windows Forms], AutoComplete
ms.assetid: fd66d085-1af1-45d4-930a-cde944da2e16
ms.openlocfilehash: db411023ad624e4c3d60b09bdbd588c85f8e22d1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745510"
---
# <a name="how-to-enable-autocomplete-in-toolstrip-controls-in-windows-forms"></a><span data-ttu-id="59f2c-102">Nasıl yapılır: Windows Forms'ta ToolStrip Denetimlerinde AutoComplete Seçeneğini Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="59f2c-102">How to: Enable AutoComplete in ToolStrip Controls in Windows Forms</span></span>
<span data-ttu-id="59f2c-103">Aşağıdaki yordam, son ziyaret edilen web siteleri gibi öğelerin bir listesini göstermek üzere bırakılmış bir <xref:System.Windows.Forms.ToolStripComboBox> <xref:System.Windows.Forms.ToolStripLabel> birleştirir.</span><span class="sxs-lookup"><span data-stu-id="59f2c-103">The following procedure combines a <xref:System.Windows.Forms.ToolStripLabel> with a <xref:System.Windows.Forms.ToolStripComboBox> that can be dropped down to show a list of items, such as recently visited Web sites.</span></span> <span data-ttu-id="59f2c-104">Kullanıcı listedeki öğelerden birinin ilk karakteriyle eşleşen bir karakter yazdığında, öğe hemen görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="59f2c-104">If the user types a character that matches the first character of one of the items in the list, the item is immediately displayed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="59f2c-105">Otomatik tamamlama, `ToolStrip` denetimleriyle birlikte çalışarak <xref:System.Windows.Forms.ComboBox> ve <xref:System.Windows.Forms.TextBox>gibi geleneksel denetimlerle çalıştığı şekilde çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="59f2c-105">Automatic completion works with `ToolStrip` controls in the same way that it works with traditional controls such as <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.TextBox>.</span></span>  
  
### <a name="to-enable-autocomplete-in-a-toolstrip-control"></a><span data-ttu-id="59f2c-106">ToolStrip denetiminde otomatik tamamlamayı etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="59f2c-106">To enable AutoComplete in a ToolStrip control</span></span>  
  
1. <span data-ttu-id="59f2c-107"><xref:System.Windows.Forms.ToolStrip> bir denetim oluşturun ve buna öğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="59f2c-107">Create a <xref:System.Windows.Forms.ToolStrip> control and add items to it.</span></span>  
  
    ```vb  
    ToolStrip1 = New System.Windows.Forms.ToolStrip  
    ToolStrip1.Items.AddRange(New System.Windows.Forms.ToolStripItem()_  
        {ToolStripLabel1, ToolStripComboBox1})  
    ```  
  
    ```csharp  
    toolStrip1 = new System.Windows.Forms.ToolStrip();  
    toolStrip1.Items.AddRange(new System.Windows.Forms.ToolStripItem[]   
        {toolStripLabel1, toolStripComboBox1});  
    ```  
  
2. <span data-ttu-id="59f2c-108">Listenin, form boyutundan bağımsız olarak her zaman kullanılabilir olması için etiketin ve Birleşik giriş kutusunun <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> özelliğini <xref:System.Windows.Forms.ToolStripItemOverflow.Never> olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="59f2c-108">Set the <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> property of the label and the combo box to <xref:System.Windows.Forms.ToolStripItemOverflow.Never> so that the list is always available regardless of the form's size.</span></span>  
  
    ```vb  
    ToolStripLabel1.Overflow = _  
        System.Windows.Forms.ToolStripItemOverflow.Never  
    ToolStripComboBox1.Overflow = _  
        System.Windows.Forms.ToolStripItemOverflow.Never  
    ```  
  
    ```csharp  
    toolStripLabel1.Overflow = _  
        System.Windows.Forms.ToolStripItemOverflow.Never  
    toolStripComboBox1.Overflow = System.Windows.Forms.ToolStripItemOverflow.Never  
    ```  
  
3. <span data-ttu-id="59f2c-109"><xref:System.Windows.Forms.ToolStripComboBox> denetiminin Items koleksiyonuna sözcükler ekleyin.</span><span class="sxs-lookup"><span data-stu-id="59f2c-109">Add words to the Items collection of the <xref:System.Windows.Forms.ToolStripComboBox> control.</span></span>  
  
    ```vb  
    ToolStripComboBox1.Items.AddRange(New Object() {"First Item", _  
        "Second Item", "Third Item"})  
    ```  
  
    ```csharp  
    toolStripComboBox1.Items.AddRange(new object[] {"First item", "Second item", "Third item"});  
    ```  
  
4. <span data-ttu-id="59f2c-110">Birleşik giriş kutusunun <xref:System.Windows.Forms.ComboBox.AutoCompleteMode%2A> özelliğini <xref:System.Windows.Forms.AutoCompleteMode.Append>olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="59f2c-110">Set the <xref:System.Windows.Forms.ComboBox.AutoCompleteMode%2A> property of the combo box to <xref:System.Windows.Forms.AutoCompleteMode.Append>.</span></span>  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteMode = _  
        System.Windows.Forms.AutoCompleteMode.Append  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteMode = System.Windows.Forms.AutoCompleteMode.Append;  
    ```  
  
5. <span data-ttu-id="59f2c-111">Birleşik giriş kutusunun <xref:System.Windows.Forms.ComboBox.AutoCompleteSource%2A> özelliğini <xref:System.Windows.Forms.AutoCompleteSource.ListItems>olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="59f2c-111">Set the <xref:System.Windows.Forms.ComboBox.AutoCompleteSource%2A> property of the combo box to <xref:System.Windows.Forms.AutoCompleteSource.ListItems>.</span></span>  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteSource = _  
        System.Windows.Forms.AutoCompleteSource.ListItems  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteSource = System.Windows.Forms.AutoCompleteSource.ListItems;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="59f2c-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59f2c-112">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripLabel>
- <xref:System.Windows.Forms.ToolStripComboBox>
- <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteMode%2A>
- <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteSource%2A>
- [<span data-ttu-id="59f2c-113">ToolStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="59f2c-113">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="59f2c-114">ToolStrip Denetim, Mimarisi</span><span class="sxs-lookup"><span data-stu-id="59f2c-114">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="59f2c-115">ToolStrip Teknoloji Özeti</span><span class="sxs-lookup"><span data-stu-id="59f2c-115">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
