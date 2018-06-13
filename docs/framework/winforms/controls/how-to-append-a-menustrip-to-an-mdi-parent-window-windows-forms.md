---
title: 'Nasıl yapılır: MDI Üst Penceresine MenuStrip Ekleme (Windows Forms)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip control [Windows Forms], merging
- MenuStrip control [Windows Forms], appending
- MDI [Windows Forms], merging menu items
ms.assetid: ab70c936-b452-4653-b417-17be57bb795b
ms.openlocfilehash: 048add340a81856cd30482c52c93c76bbf6181f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529561"
---
# <a name="how-to-append-a-menustrip-to-an-mdi-parent-window-windows-forms"></a>Nasıl yapılır: MDI Üst Penceresine MenuStrip Ekleme (Windows Forms)
Bazı uygulamalarda, birden çok belge arabirimi (MDI) alt pencere türü MDI üst penceresinden farklı olabilir. Örneğin, elektronik tablo MDI olabilir ve MDI alt bir grafik olabilir. Bu durumda, farklı türlerde MDI alt pencereleri etkinleştirilmiş olarak MDI üst öğenin menüsünün içeriğini MDI alt menü içeriğini güncelleştirmek istediğiniz.  
  
 Aşağıdaki yordam kullanır <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, ve <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> MDI alt menüsünü MDI üst menüsüne eklenecek özellikleri. MDI alt pencereyi eklenmiş menüsü MDI üst kaldırır.  
  
 Ayrıca bkz. [Çoklu belge arabirimi (MDI) uygulamaları](http://msdn.microsoft.com/library/xyhh2e7e\(v=vs.110\)).  
  
### <a name="to-append-a-menu-item-to-an-mdi-parent"></a>Menü öğesi için bir MDI eklemek için  
  
1.  Bir form oluşturun ve ayarlayın, <xref:System.Windows.Forms.Form.IsMdiContainer%2A> özelliğine `true`.  
  
2.  Ekleme bir <xref:System.Windows.Forms.MenuStrip> için `Form1` ve <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> özelliği <xref:System.Windows.Forms.MenuStrip> için `true`.  
  
3.  Ayarlama <xref:System.Windows.Forms.ToolStripItem.Visible%2A> özelliği `Form1` <xref:System.Windows.Forms.MenuStrip> için `false`.  
  
4.  Bir üst düzey menü öğesi ekleme `Form1` <xref:System.Windows.Forms.MenuStrip> ve kendi <xref:System.Windows.Forms.Control.Text%2A> özelliğine `&File`.  
  
5.  Bir alt öğe ekleme `&File` menü öğesi ve kümesi kendi <xref:System.Windows.Forms.Form.Text%2A> özelliğine `&Open`.  
  
6.  Projeye form ekleme, ekleme bir <xref:System.Windows.Forms.MenuStrip> form ve kümesi <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> özelliği `Form2` <xref:System.Windows.Forms.MenuStrip> için `true`.  
  
7.  Bir üst düzey menü öğesi ekleme `Form2` <xref:System.Windows.Forms.MenuStrip> ve kendi <xref:System.Windows.Forms.Form.Text%2A> özelliğine `&Special`.  
  
8.  İki alt öğe ekleme `&Special` menü öğesi ve kümesi kendi <xref:System.Windows.Forms.Form.Text%2A> özelliklerine `Command&1` ve `Command&2`sırasıyla.  
  
9. Ayarlama <xref:System.Windows.Forms.MergeAction> özelliği `&Special`, `Command&1`, ve `Command&2` menü öğeleri için <xref:System.Windows.Forms.MergeAction.Append>.  
  
10. İçin bir olay işleyicisi oluşturun <xref:System.Windows.Forms.Control.Click> olayı `&New` <xref:System.Windows.Forms.ToolStripMenuItem>.  
  
11. Olay işleyicisi içinde oluşturmak ve yeni örneklerini görüntülemek için aşağıdaki kod örneğinde benzer bir kod Ekle `Form2` MDI alt öğeleri olarak `Form1`.  
  
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
  
12. Kod aşağıdaki kod örneğinde benzer yerleştirin getirin `&Open` <xref:System.Windows.Forms.ToolStripMenuItem> olay işleyicisi kaydetmek için.  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   İki <xref:System.Windows.Forms.Form> adlı denetimleri `Form1` ve `Form2`.  
  
-   A <xref:System.Windows.Forms.MenuStrip> denetiminin `Form1` adlı `menuStrip1`ve bir <xref:System.Windows.Forms.MenuStrip> denetiminin `Form2` adlı `menuStrip2`.  
  
-   Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.
