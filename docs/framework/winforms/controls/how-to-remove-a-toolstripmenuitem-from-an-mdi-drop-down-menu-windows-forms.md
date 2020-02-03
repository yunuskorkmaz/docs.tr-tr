---
title: 'Nasıl yapılır: Bir MDI Açılan Menüsünden ToolStripMenuItem kaldırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- menu items [Windows Forms], removing from MDI drop-down menus
- MenuStrip control [Windows Forms], merging
- MenuStrip control [Windows Forms], removing
- MDI [Windows Forms], merging menu items
ms.assetid: bdafe60d-82ee-45bc-97fe-eeefca6e54c1
ms.openlocfilehash: 3198195cf0991734826508aa65818505bf2038c8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735842"
---
# <a name="how-to-remove-a-toolstripmenuitem-from-an-mdi-drop-down-menu-windows-forms"></a>Nasıl yapılır: Bir MDI Açılan Menüsünden ToolStripMenuItem kaldırma (Windows Forms)
Bazı uygulamalarda, bir çoklu belge arabirimi (MDI) alt penceresinin türü MDI ana penceresinden farklı olabilir. Örneğin, MDI parent bir elektronik tablo olabilir ve MDI alt öğesi bir grafik olabilir. Bu durumda, farklı türlerdeki MDI alt pencereleri etkinleştirildiğinden MDI üst öğesinin menüsünün içeriğini MDI alt menüsünün içeriğiyle güncelleştirmek istersiniz.  
  
 Aşağıdaki yordam, MDI parent menüsünün açılan kısmından bir menü öğesini kaldırmak için <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>ve <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> özelliklerini kullanır. MDI alt penceresini kapatmak kaldırılan menü öğelerini MDI parent menüsüne geri yükler.  
  
### <a name="to-remove-a-menustrip-from-an-mdi-drop-down-menu"></a>Bir MDI açılan menüsünden MenuStrip 'i kaldırmak için  
  
1. Bir form oluşturun ve <xref:System.Windows.Forms.Form.IsMdiContainer%2A> özelliğini `true`olarak ayarlayın.  
  
2. `Form1` <xref:System.Windows.Forms.MenuStrip> ekleyin ve <xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> özelliğini `true`olarak ayarlayın.  
  
3. `Form1`<xref:System.Windows.Forms.MenuStrip> en üst düzey menü öğesini ekleyin ve <xref:System.Windows.Forms.Control.Text%2A> özelliğini `&File`olarak ayarlayın.  
  
4. `&File` menü öğesine üç alt menü öğesi ekleyin ve <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliklerini `&Open`, `&Import from`ve `E&xit`olarak ayarlayın.  
  
5. `&Import from` alt menü öğesine iki alt menü öğesi ekleyin ve <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliklerini `&Word` ve `&Excel`olarak ayarlayın.  
  
6. Projeye bir form ekleyin, forma <xref:System.Windows.Forms.MenuStrip> ekleyin ve `Form2`<xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> özelliğini `true`olarak ayarlayın.  
  
7. `Form2`<xref:System.Windows.Forms.MenuStrip> en üst düzey menü öğesini ekleyin ve <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliğini `&File`olarak ayarlayın.  
  
8. `Form2``&File` menüsüne bir `&Import from` alt menü öğesi ekleyin ve `&File` menüsüne bir `&Word` alt menü öğesi ekleyin.  
  
9. Aşağıdaki tabloda gösterildiği gibi `Form2` menü öğelerinin <xref:System.Windows.Forms.MergeAction> ve <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> özelliklerini ayarlayın.  
  
    |Form2 menü öğesi|MergeAction değeri|MergeIndex değeri|  
    |---------------------|-----------------------|----------------------|  
    |Dosya|Yalnızca eşleşme|-1|  
    |İçeri aktarma|Yalnızca eşleşme|-1|  
    |Word|Kaldır|-1|  
  
10. `Form1`, `&Open`<xref:System.Windows.Forms.ToolStripMenuItem><xref:System.Windows.Forms.Control.Click> olayı için bir olay işleyicisi oluşturun.  
  
11. Olay işleyicisi içinde, `Form1`MDI alt öğeleri olarak `Form2` yeni örneklerini oluşturmak ve göstermek için aşağıdaki kod örneğine benzer bir kod ekleyin:  
  
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
    this.openToolStripMenuItem.Click += new _  
    System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- `Form1` ve `Form2`adlı iki <xref:System.Windows.Forms.Form> denetimi.  
  
- `menuStrip1`adlı `Form1` ve `Form2` adlı `menuStrip2`<xref:System.Windows.Forms.MenuStrip> bir denetim <xref:System.Windows.Forms.MenuStrip> denetimi.  
  
- <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: MDI Üst Formları Oluşturma](../advanced/how-to-create-mdi-parent-forms.md)
- [Nasıl yapılır: MDI Alt Formları Oluşturma](../advanced/how-to-create-mdi-child-forms.md)
- [MenuStrip Denetimine Genel Bakış](menustrip-control-overview-windows-forms.md)
