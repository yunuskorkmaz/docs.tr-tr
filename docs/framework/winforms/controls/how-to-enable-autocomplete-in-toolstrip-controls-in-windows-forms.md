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
ms.openlocfilehash: 18b17aaea9d2354c03bb43f3fdd8d3779697cf58
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142024"
---
# <a name="how-to-enable-autocomplete-in-toolstrip-controls-in-windows-forms"></a>Nasıl yapılır: Windows Forms'ta ToolStrip Denetimlerinde AutoComplete Seçeneğini Etkinleştirme
Aşağıdaki yordam, yakın <xref:System.Windows.Forms.ToolStripLabel> zamanda <xref:System.Windows.Forms.ToolStripComboBox> ziyaret edilen Web siteleri gibi öğelerin listesini göstermek için bırakılabilen bir ile birleştirir. Kullanıcı, listedeki öğelerden birinin ilk karakteriyle eşleşen bir karakter sınıfa çıkarsa, öğe hemen görüntülenir.  
  
> [!NOTE]
> Otomatik tamamlama `ToolStrip` gibi geleneksel kontroller <xref:System.Windows.Forms.ComboBox> ile çalıştığı gibi aynı <xref:System.Windows.Forms.TextBox>şekilde kontrolleri ile çalışır.  
  
### <a name="to-enable-autocomplete-in-a-toolstrip-control"></a>ToolStrip denetiminde Otomatik Tamamlama'yı etkinleştirmek için  
  
1. Bir <xref:System.Windows.Forms.ToolStrip> denetim oluşturun ve buna öğeler ekleyin.  
  
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
  
2. Etiketin <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> ve açılan kutunun <xref:System.Windows.Forms.ToolStripItemOverflow.Never> özelliğini, formun boyutundan bağımsız olarak listenin her zaman kullanılabilir olması için ayarlayın.  
  
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
  
3. Denetimin Öğeler koleksiyonuna <xref:System.Windows.Forms.ToolStripComboBox> sözcükler ekleyin.  
  
    ```vb  
    ToolStripComboBox1.Items.AddRange(New Object() {"First Item", _  
        "Second Item", "Third Item"})  
    ```  
  
    ```csharp  
    toolStripComboBox1.Items.AddRange(new object[] {"First item", "Second item", "Third item"});  
    ```  
  
4. Açılan <xref:System.Windows.Forms.ComboBox.AutoCompleteMode%2A> kutunun özelliğini <xref:System.Windows.Forms.AutoCompleteMode.Append>.  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteMode = _  
        System.Windows.Forms.AutoCompleteMode.Append  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteMode = System.Windows.Forms.AutoCompleteMode.Append;  
    ```  
  
5. Açılan <xref:System.Windows.Forms.ComboBox.AutoCompleteSource%2A> kutunun özelliğini <xref:System.Windows.Forms.AutoCompleteSource.ListItems>.  
  
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
- [ToolStrip Teknoloiji Özeti](toolstrip-technology-summary.md)
