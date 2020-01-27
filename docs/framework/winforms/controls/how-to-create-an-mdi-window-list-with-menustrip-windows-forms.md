---
title: 'Nasıl yapılır: MenuStrip ile MDI Pencere Listesi Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MDI [Windows Forms], creating window lists
- MenuStrip control [Windows Forms], creating window lists
ms.assetid: 04fb414b-811f-4a83-aab6-b4a24646dec5
ms.openlocfilehash: f013c3df2ab5783a22fe2c34402dc53a328cafa2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731014"
---
# <a name="how-to-create-an-mdi-window-list-with-menustrip-windows-forms"></a>Nasıl yapılır: MenuStrip (Windows Forms) ile MDI Pencere Listesi Oluşturma
Birden çok belge arabirimi (MDI) kullanarak, aynı anda birden fazla belge açan uygulamalar oluşturun ve içeriği bir belgeden diğerine kopyalayabilir ve yapıştırabilirsiniz.  
  
 Bu yordamda, üst öğenin pencere menüsündeki tüm etkin alt formların listesini nasıl oluşturacağınız gösterilmektedir.  
  
### <a name="to-create-an-mdi-window-list-on-a-menustrip"></a>MenuStrip 'te MDI pencere listesi oluşturmak için  
  
1. Bir form oluşturun ve <xref:System.Windows.Forms.Form.IsMdiContainer%2A> özelliğini `true`olarak ayarlayın.  
  
2. Forma <xref:System.Windows.Forms.MenuStrip> ekleyin.  
  
3. <xref:System.Windows.Forms.MenuStrip> iki üst düzey menü öğesi ekleyin ve <xref:System.Windows.Forms.Control.Text%2A> özelliklerini `&File` ve `&Window`olarak ayarlayın.  
  
4. `&File` menü öğesine bir alt menü öğesi ekleyin ve <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliğini `&Open`olarak ayarlayın.  
  
5. <xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> özelliğini `&Window`<xref:System.Windows.Forms.ToolStripMenuItem>olarak ayarlayın.  
  
6. Projeye bir form ekleyin ve istediğiniz denetimi, başka bir <xref:System.Windows.Forms.MenuStrip>gibi ekleyin.  
  
7. `&New`<xref:System.Windows.Forms.ToolStripMenuItem><xref:System.Windows.Forms.Control.Click> olayı için bir olay işleyicisi oluşturun.  
  
8. Olay işleyicisi içinde, `Form1`MDI alt öğeleri olarak `Form2` yeni örneklerini oluşturmak ve göstermek için aşağıdakine benzer bir kod ekleyin.  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(ByVal sender As _  
    System.Object, ByVal e As System.EventArgs) Handles _  
    openToolStripMenuItem.Click  
        Dim NewMDIChild As New Form2()  
        'Set the parent form of the child window.  
            NewMDIChild.MdiParent = Me  
        'Display the new form.  
            NewMDIChild.Show()  
    End Sub  
    ```  
  
    ```csharp  
    private void newToolStripMenuItem_Click(object sender, EventArgs e)  
    {  
        Form2 newMDIChild = new Form2();  
        // Set the parent form of the child window.  
            newMDIChild.MdiParent = this;  
        // Display the new form.  
            newMDIChild.Show();  
    }  
    ```  
  
9. Olay işleyicisini kaydetmek için `&New`<xref:System.Windows.Forms.ToolStripMenuItem> gibi bir kod girin.  
  
    ```vb  
    Private Sub newToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles newToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.newToolStripMenuItem.Click += new System.EventHandler(this.newToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>Kod Derleme  
 Bu örnek şunları gerektirir:  
  
- `Form1` ve `Form2`adlı iki <xref:System.Windows.Forms.Form> denetimi.  
  
- `menuStrip1`adlı `Form1` ve `Form2` adlı `menuStrip2`<xref:System.Windows.Forms.MenuStrip> bir denetim <xref:System.Windows.Forms.MenuStrip> denetimi.  
  
- <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: MDI Üst Formları Oluşturma](../advanced/how-to-create-mdi-parent-forms.md)
- [Nasıl yapılır: MDI Alt Formları Oluşturma](../advanced/how-to-create-mdi-child-forms.md)
- [MenuStrip Denetimi](menustrip-control-windows-forms.md)
