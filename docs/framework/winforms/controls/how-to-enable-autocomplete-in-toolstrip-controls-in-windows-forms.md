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
# <a name="how-to-enable-autocomplete-in-toolstrip-controls-in-windows-forms"></a>Nasıl yapılır: Windows Forms'ta ToolStrip Denetimlerinde AutoComplete Seçeneğini Etkinleştirme
Aşağıdaki yordam, son ziyaret edilen web siteleri gibi öğelerin bir listesini göstermek üzere bırakılmış bir <xref:System.Windows.Forms.ToolStripComboBox> <xref:System.Windows.Forms.ToolStripLabel> birleştirir. Kullanıcı listedeki öğelerden birinin ilk karakteriyle eşleşen bir karakter yazdığında, öğe hemen görüntülenir.  
  
> [!NOTE]
> Otomatik tamamlama, `ToolStrip` denetimleriyle birlikte çalışarak <xref:System.Windows.Forms.ComboBox> ve <xref:System.Windows.Forms.TextBox>gibi geleneksel denetimlerle çalıştığı şekilde çalışacaktır.  
  
### <a name="to-enable-autocomplete-in-a-toolstrip-control"></a>ToolStrip denetiminde otomatik tamamlamayı etkinleştirmek için  
  
1. <xref:System.Windows.Forms.ToolStrip> bir denetim oluşturun ve buna öğe ekleyin.  
  
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
  
2. Listenin, form boyutundan bağımsız olarak her zaman kullanılabilir olması için etiketin ve Birleşik giriş kutusunun <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> özelliğini <xref:System.Windows.Forms.ToolStripItemOverflow.Never> olarak ayarlayın.  
  
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
  
3. <xref:System.Windows.Forms.ToolStripComboBox> denetiminin Items koleksiyonuna sözcükler ekleyin.  
  
    ```vb  
    ToolStripComboBox1.Items.AddRange(New Object() {"First Item", _  
        "Second Item", "Third Item"})  
    ```  
  
    ```csharp  
    toolStripComboBox1.Items.AddRange(new object[] {"First item", "Second item", "Third item"});  
    ```  
  
4. Birleşik giriş kutusunun <xref:System.Windows.Forms.ComboBox.AutoCompleteMode%2A> özelliğini <xref:System.Windows.Forms.AutoCompleteMode.Append>olarak ayarlayın.  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteMode = _  
        System.Windows.Forms.AutoCompleteMode.Append  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteMode = System.Windows.Forms.AutoCompleteMode.Append;  
    ```  
  
5. Birleşik giriş kutusunun <xref:System.Windows.Forms.ComboBox.AutoCompleteSource%2A> özelliğini <xref:System.Windows.Forms.AutoCompleteSource.ListItems>olarak ayarlayın.  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteSource = _  
        System.Windows.Forms.AutoCompleteSource.ListItems  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteSource = System.Windows.Forms.AutoCompleteSource.ListItems;  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripLabel>
- <xref:System.Windows.Forms.ToolStripComboBox>
- <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteMode%2A>
- <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteSource%2A>
- [ToolStrip Denetimine Genel Bakış](toolstrip-control-overview-windows-forms.md)
- [ToolStrip Denetim, Mimarisi](toolstrip-control-architecture.md)
- [ToolStrip Teknoloji Özeti](toolstrip-technology-summary.md)
