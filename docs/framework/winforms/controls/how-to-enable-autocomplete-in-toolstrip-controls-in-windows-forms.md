---
title: 'Nasıl yapılır: Windows Forms araç şeridi denetimlerinde otomatik tamamlamayı etkinleştir'
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
ms.openlocfilehash: 301f1b156bbaee5c5f7be95e972ee1ebaa83777f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963609"
---
# <a name="how-to-enable-autocomplete-in-toolstrip-controls-in-windows-forms"></a>Nasıl yapılır: Windows Forms araç şeridi denetimlerinde otomatik tamamlamayı etkinleştir
Aşağıdaki yordam, en son <xref:System.Windows.Forms.ToolStripLabel> ziyaret edilen <xref:System.Windows.Forms.ToolStripComboBox> Web siteleri gibi öğelerin bir listesini göstermek için bir ile birlikte bir birleştirir. Kullanıcı listedeki öğelerden birinin ilk karakteriyle eşleşen bir karakter yazdığında, öğe hemen görüntülenir.  
  
> [!NOTE]
> Otomatik tamamlama, ve `ToolStrip` <xref:System.Windows.Forms.ComboBox> <xref:System.Windows.Forms.TextBox>gibi geleneksel denetimlerle çalıştığı gibi denetimlerle birlikte çalışacaktır.  
  
### <a name="to-enable-autocomplete-in-a-toolstrip-control"></a>ToolStrip denetiminde otomatik tamamlamayı etkinleştirmek için  
  
1. Bir <xref:System.Windows.Forms.ToolStrip> denetim oluşturun ve buna öğe ekleyin.  
  
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
  
2. Listenin, form boyutundan bağımsız olarak her zaman kullanılabilir olması için <xref:System.Windows.Forms.ToolStripItemOverflow.Never> etiketinin ve Birleşik giriş kutusunun özelliğiniolarakayarlayın.<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>  
  
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
  
3. <xref:System.Windows.Forms.ToolStripComboBox> Denetimin Items koleksiyonuna sözcükler ekleyin.  
  
    ```vb  
    ToolStripComboBox1.Items.AddRange(New Object() {"First Item", _  
        "Second Item", "Third Item"})  
    ```  
  
    ```csharp  
    toolStripComboBox1.Items.AddRange(new object[] {"First item", "Second item", "Third item"});  
    ```  
  
4. Birleşik giriş kutusunun <xref:System.Windows.Forms.AutoCompleteMode.Append>özelliğiniolarakayarlayın <xref:System.Windows.Forms.ComboBox.AutoCompleteMode%2A> .  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteMode = _  
        System.Windows.Forms.AutoCompleteMode.Append  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteMode = System.Windows.Forms.AutoCompleteMode.Append;  
    ```  
  
5. Birleşik giriş kutusunun <xref:System.Windows.Forms.AutoCompleteSource.ListItems>özelliğiniolarakayarlayın <xref:System.Windows.Forms.ComboBox.AutoCompleteSource%2A> .  
  
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
