---
title: 'Nasıl yapılır: MDI Üst Penceresine MenuStrip Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip control [Windows Forms], merging
- MenuStrip control [Windows Forms], appending
- MDI [Windows Forms], merging menu items
ms.assetid: ab70c936-b452-4653-b417-17be57bb795b
ms.openlocfilehash: 06e5c9daab8b7eb72024fff27d661c0eb3bf84c6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747161"
---
# <a name="how-to-append-a-menustrip-to-an-mdi-parent-window-windows-forms"></a>Nasıl yapılır: MDI Üst Penceresine MenuStrip Ekleme (Windows Forms)
Bazı uygulamalarda, bir çoklu belge arabirimi (MDI) alt penceresinin türü MDI ana penceresinden farklı olabilir. Örneğin, MDI parent bir elektronik tablo olabilir ve MDI alt öğesi bir grafik olabilir. Bu durumda, farklı türlerdeki MDI alt pencereleri etkinleştirildiğinden MDI üst öğesinin menüsünün içeriğini MDI alt menüsünün içeriğiyle güncelleştirmek istersiniz.  
  
 Aşağıdaki yordam MDI alt menüsünü MDI parent menüsüne eklemek için <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>ve <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> özelliklerini kullanır. MDI alt penceresini kapatmak, eklenen menüyü MDI üst öğesinden kaldırır.  
  
 Ayrıca bkz. [birden çok belgeli arabirim (MDI) uygulamaları](../advanced/multiple-document-interface-mdi-applications.md).  
  
### <a name="to-append-a-menu-item-to-an-mdi-parent"></a>Bir MDI üst öğesine bir menü öğesi eklemek için  
  
1. Bir form oluşturun ve <xref:System.Windows.Forms.Form.IsMdiContainer%2A> özelliğini `true`olarak ayarlayın.  
  
2. `Form1` <xref:System.Windows.Forms.MenuStrip> ekleyin ve <xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> özelliğini `true`olarak ayarlayın.  
  
3. `Form1`<xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.ToolStripItem.Visible%2A> özelliğini `false`olarak ayarlayın.  
  
4. `Form1`<xref:System.Windows.Forms.MenuStrip> en üst düzey menü öğesini ekleyin ve <xref:System.Windows.Forms.Control.Text%2A> özelliğini `&File`olarak ayarlayın.  
  
5. `&File` menü öğesine bir alt menü öğesi ekleyin ve <xref:System.Windows.Forms.Form.Text%2A> özelliğini `&Open`olarak ayarlayın.  
  
6. Projeye bir form ekleyin, forma <xref:System.Windows.Forms.MenuStrip> ekleyin ve `Form2`<xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> özelliğini `true`olarak ayarlayın.  
  
7. `Form2`<xref:System.Windows.Forms.MenuStrip> en üst düzey menü öğesini ekleyin ve <xref:System.Windows.Forms.Form.Text%2A> özelliğini `&Special`olarak ayarlayın.  
  
8. `&Special` menü öğesine iki alt menü öğesi ekleyin ve <xref:System.Windows.Forms.Form.Text%2A> özelliklerini sırasıyla `Command&1` ve `Command&2`olarak ayarlayın.  
  
9. `&Special`, `Command&1`ve `Command&2` menü öğelerinin <xref:System.Windows.Forms.MergeAction> özelliğini <xref:System.Windows.Forms.MergeAction.Append>olarak ayarlayın.  
  
10. `&Open` <xref:System.Windows.Forms.ToolStripMenuItem><xref:System.Windows.Forms.Control.Click> olayı için bir olay işleyicisi oluşturun.  
  
11. Olay işleyicisi içinde, `Form1`MDI alt öğeleri olarak `Form2` yeni örneklerini oluşturmak ve göstermek için aşağıdaki kod örneğine benzer bir kod ekleyin.  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles openToolStripMenuItem.Click  
        Dim NewMDIChild As New Form2()  
        'Set the parent form of the child window.  
        NewMDIChild.MdiParent = Me  
        'Display the new form.  
        NewMDIChild.Show()  
    End Sub  
    ```  
  
    ```csharp  
    private void openToolStripMenuItem_Click(object sender, EventArgs e)  
    {  
        Form2 newMDIChild = new Form2();  
        // Set the parent form of the child window.  
        newMDIChild.MdiParent = this;  
        // Display the new form.  
        newMDIChild.Show();  
    }  
    ```  
  
12. Olay işleyicisini kaydetmek için `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> aşağıdaki kod örneğine benzer bir kod koyun.  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>Kod Derleme  
 Bu örnek şunları gerektirir:  
  
- `Form1` ve `Form2`adlı iki <xref:System.Windows.Forms.Form> denetimi.  
  
- `menuStrip1`adlı `Form1` ve `Form2` adlı `menuStrip2`<xref:System.Windows.Forms.MenuStrip> bir denetim <xref:System.Windows.Forms.MenuStrip> denetimi.  
  
- <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemelerine başvurular.
