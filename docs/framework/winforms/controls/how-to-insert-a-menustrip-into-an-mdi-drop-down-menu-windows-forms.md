---
title: 'Nasıl yapılır: Bir MDI Açılan Menüsüne MenuStrip ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip control [Windows Forms], inserting
- MenuStrip control [Windows Forms], merging
- MDI [Windows Forms], merging menu items
ms.assetid: 0fad444e-26d9-49af-8860-044d9c10d608
ms.openlocfilehash: 6e189dd159c48b5779679d0563fab85e9b848992
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736408"
---
# <a name="how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms"></a>Nasıl yapılır: Bir MDI Açılan Menüsüne MenuStrip ekleme (Windows Forms)
Bazı uygulamalarda, bir çoklu belge arabirimi (MDI) alt penceresinin türü MDI ana penceresinden farklı olabilir. Örneğin, MDI parent bir elektronik tablo olabilir ve MDI alt öğesi bir grafik olabilir. Bu durumda, farklı türlerdeki MDI alt pencereleri etkinleştirildiğinden MDI üst öğesinin menüsünün içeriğini MDI alt menüsünün içeriğiyle güncelleştirmek istersiniz.  
  
 Aşağıdaki yordam, MDI alt menüsünden bir menü öğeleri grubunu MDI üst menüsünün aşağı açılan kısmına eklemek için <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>ve <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> özelliklerini kullanır. MDI alt penceresini kapatmak, ekli menü öğelerini MDI üst öğesinden kaldırır.  
  
### <a name="to-insert-a-menustrip-into-an-mdi-drop-down-menu"></a>Bir MDI açılan menüsüne MenuStrip eklemek için  
  
1. Bir form oluşturun ve <xref:System.Windows.Forms.Form.IsMdiContainer%2A> özelliğini `true`olarak ayarlayın.  
  
2. `Form1` <xref:System.Windows.Forms.MenuStrip> ekleyin ve <xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> özelliğini `true`olarak ayarlayın.  
  
3. `Form1`<xref:System.Windows.Forms.MenuStrip> en üst düzey menü öğesini ekleyin ve <xref:System.Windows.Forms.Control.Text%2A> özelliğini `&File`olarak ayarlayın.  
  
4. `&File` menü öğesine üç alt menü öğesi ekleyin ve <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliklerini `&Open`, `&Import from`ve `E&xit`olarak ayarlayın.  
  
5. `&Import from` alt menü öğesine iki alt menü öğesi ekleyin ve <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliklerini `&Word` ve `&Excel`olarak ayarlayın.  
  
6. Projeye bir form ekleyin, forma <xref:System.Windows.Forms.MenuStrip> ekleyin ve `Form2`<xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> özelliğini `true`olarak ayarlayın.  
  
7. `Form2`<xref:System.Windows.Forms.MenuStrip> en üst düzey menü öğesini ekleyin ve <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliğini `&File`olarak ayarlayın.  
  
8. `Form2` `&File` menüsüne alt menü öğelerini şu sırada ekleyin: bir <xref:System.Windows.Forms.ToolStripSeparator>, `&Save`, `Save and &Close`ve başka bir <xref:System.Windows.Forms.ToolStripSeparator>.  
  
9. Aşağıdaki tabloda gösterildiği gibi `Form2` menü öğelerinin <xref:System.Windows.Forms.MergeAction> ve <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> özelliklerini ayarlayın.  
  
    |Form2 menü öğesi|MergeAction değeri|MergeIndex değeri|  
    |---------------------|-----------------------|----------------------|  
    |Dosya|Yalnızca eşleşme|-1|  
    |Ayırıcı|Ekleme|2|  
    |Kaydet|Ekleme|3|  
    |Kaydet ve Kapat|Ekleme|4|  
    |Ayırıcı|Ekleme|5|  
  
10. `&Open`<xref:System.Windows.Forms.ToolStripMenuItem><xref:System.Windows.Forms.Control.Click> olayı için bir olay işleyicisi oluşturun.  
  
11. Olay işleyicisi içinde, `Form1`MDI alt öğeleri olarak `Form2` yeni örneklerini oluşturmak ve göstermek için aşağıdaki kod örneğine benzer bir kod ekleyin.  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles openToolStripMenuItem.Click  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: MDI Üst Formları Oluşturma](../advanced/how-to-create-mdi-parent-forms.md)
- [Nasıl yapılır: MDI Alt Formları Oluşturma](../advanced/how-to-create-mdi-child-forms.md)
- [MenuStrip Denetimine Genel Bakış](menustrip-control-overview-windows-forms.md)
