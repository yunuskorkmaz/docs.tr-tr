---
title: 'Nasıl yapılır: (Windows Forms) MDI üst penceresine MenuStrip ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip control [Windows Forms], merging
- MenuStrip control [Windows Forms], appending
- MDI [Windows Forms], merging menu items
ms.assetid: ab70c936-b452-4653-b417-17be57bb795b
ms.openlocfilehash: a335531b090983de4e2b3daccc9f956930cbad6e
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59298948"
---
# <a name="how-to-append-a-menustrip-to-an-mdi-parent-window-windows-forms"></a>Nasıl yapılır: (Windows Forms) MDI üst penceresine MenuStrip ekleme
Bazı uygulamalarda, bir Çoklu belge arabirimi (MDI) alt penceresi türünü MDI ana penceresinde farklı olabilir. Örneğin, bir elektronik tablo MDI olabilir ve MDI alt bir grafik olabilir. Bu durumda, farklı türlerde MDI alt pencereleri etkin olarak MDI üst menü içeriğini MDI alt menü içeriğini güncelleştirmek istediğiniz.  
  
 Aşağıdaki yordam kullanır <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, ve <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> MDI üst menüye MDI alt menüsünü eklenecek özellikleri. MDI alt penceresini kapatarak eklenmiş menü MDI üst kaldırır.  
  
 Ayrıca bkz: [Çok Belgeli Arabirim (MDI) uygulamaları](../advanced/multiple-document-interface-mdi-applications.md).  
  
### <a name="to-append-a-menu-item-to-an-mdi-parent"></a>Bir MDI üst menü öğesi eklemek için  
  
1. Bir form oluşturun ve ayarlayın, <xref:System.Windows.Forms.Form.IsMdiContainer%2A> özelliğini `true`.  
  
2. Ekleme bir <xref:System.Windows.Forms.MenuStrip> için `Form1` ayarlayıp <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> özelliği <xref:System.Windows.Forms.MenuStrip> için `true`.  
  
3. Ayarlama <xref:System.Windows.Forms.ToolStripItem.Visible%2A> özelliği `Form1`<xref:System.Windows.Forms.MenuStrip> için `false`.  
  
4. Bir üst düzey menü öğesine eklemek `Form1`<xref:System.Windows.Forms.MenuStrip> ve kendi <xref:System.Windows.Forms.Control.Text%2A> özelliğini `&File`.  
  
5. Bir alt öğe ekleme `&File` menü öğesi ve kümesi kendi <xref:System.Windows.Forms.Form.Text%2A> özelliğini `&Open`.  
  
6. Projeye form ekleme, ekleme bir <xref:System.Windows.Forms.MenuStrip> form ve kümesi <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> özelliği `Form2`<xref:System.Windows.Forms.MenuStrip> için `true`.  
  
7. Bir üst düzey menü öğesine eklemek `Form2`<xref:System.Windows.Forms.MenuStrip> ve kendi <xref:System.Windows.Forms.Form.Text%2A> özelliğini `&Special`.  
  
8. İki alt öğe ekleme `&Special` menü öğesi ve kümesi kendi <xref:System.Windows.Forms.Form.Text%2A> özelliklerine `Command&1` ve `Command&2`sırasıyla.  
  
9. Ayarlama <xref:System.Windows.Forms.MergeAction> özelliği `&Special`, `Command&1`, ve `Command&2` menü öğeleri için <xref:System.Windows.Forms.MergeAction.Append>.  
  
10. İçin bir olay işleyicisi oluşturun <xref:System.Windows.Forms.Control.Click> olayı `&New`<xref:System.Windows.Forms.ToolStripMenuItem>.  
  
11. Olay işleyicisinin içerisinde kod oluşturmak ve yeni örneklerini görüntülemek için aşağıdaki kod örneği benzer ekleme `Form2` MDI alt öğeleri olarak `Form1`.  
  
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
  
12. Kod aşağıdaki kod örneğinde benzer yerleştirin getirin `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> olay işleyicisi kaydetmek için.  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   İki <xref:System.Windows.Forms.Form> adlarında `Form1` ve `Form2`.  
  
-   A <xref:System.Windows.Forms.MenuStrip> denetimi `Form1` adlı `menuStrip1`ve <xref:System.Windows.Forms.MenuStrip> denetimi `Form2` adlı `menuStrip2`.  
  
-   Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.
