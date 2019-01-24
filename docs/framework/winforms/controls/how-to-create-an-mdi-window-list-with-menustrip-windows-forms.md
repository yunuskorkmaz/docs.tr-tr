---
title: 'Nasıl yapılır: (Windows Forms) MenuStrip ile MDI pencere listesi oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MDI [Windows Forms], creating window lists
- MenuStrip control [Windows Forms], creating window lists
ms.assetid: 04fb414b-811f-4a83-aab6-b4a24646dec5
ms.openlocfilehash: 00f35fe872fc5702595108646e2605ed419823f8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54585321"
---
# <a name="how-to-create-an-mdi-window-list-with-menustrip-windows-forms"></a>Nasıl yapılır: (Windows Forms) MenuStrip ile MDI pencere listesi oluşturma
Çok Belgeli Arabirim (MDI), aynı zaman ve kopyalama sırasında birkaç belge açın ve içeriğini bir belgeden diğerine yapıştırma uygulamalar oluşturmak için kullanın.  
  
 Bu yordam, üst öğenin Pencere menüsünden tüm etkin alt formların listesini oluşturulacağını gösterir.  
  
### <a name="to-create-an-mdi-window-list-on-a-menustrip"></a>MenuStrip üzerinde bir MDI pencere listesi oluşturma  
  
1.  Bir form oluşturun ve ayarlayın, <xref:System.Windows.Forms.Form.IsMdiContainer%2A> özelliğini `true`.  
  
2.  Ekleme bir <xref:System.Windows.Forms.MenuStrip> form.  
  
3.  İki üst düzey menü öğeleri ekleme <xref:System.Windows.Forms.MenuStrip> ve bunların <xref:System.Windows.Forms.Control.Text%2A> özelliklerine `&File` ve `&Window`.  
  
4.  Bir alt öğe ekleme `&File` menü öğesi ve kümesi kendi <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliğini `&Open`.  
  
5.  Ayarlama <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> özelliği <xref:System.Windows.Forms.MenuStrip> için `&Window` <xref:System.Windows.Forms.ToolStripMenuItem>.  
  
6.  Projeye form ekleme ve istediğiniz denetim, başka bir gibi <xref:System.Windows.Forms.MenuStrip>.  
  
7.  İçin bir olay işleyicisi oluşturun <xref:System.Windows.Forms.Control.Click> olayı `&New` <xref:System.Windows.Forms.ToolStripMenuItem>.  
  
8.  Olay işleyicisinin içerisinde oluşturmak ve yeni örneklerini görüntülemek için aşağıdaki için benzer bir kod ekleme `Form2` MDI alt öğeleri olarak `Form1`.  
  
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
  
9. Kod aşağıdaki gibi yerleştirmek `&New` <xref:System.Windows.Forms.ToolStripMenuItem> olay işleyicisi kaydetmek için.  
  
    ```vb  
    Private Sub newToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles newToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.newToolStripMenuItem.Click += new System.EventHandler(this.newToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   İki <xref:System.Windows.Forms.Form> adlarında `Form1` ve `Form2`.  
  
-   A <xref:System.Windows.Forms.MenuStrip> denetimi `Form1` adlı `menuStrip1`ve <xref:System.Windows.Forms.MenuStrip> denetimi `Form2` adlı `menuStrip2`.  
  
-   Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: MDI üst formları oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)
- [Nasıl yapılır: MDI alt formları oluştur](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)
- [MenuStrip Denetimi](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)
