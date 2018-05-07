---
title: 'Nasıl yapılır: Bir MDI Açılan Menüsünden ToolStripMenuItem kaldırma (Windows Forms)'
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
ms.openlocfilehash: 0649e99c682464928aaae68451b2cb29d5675485
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-remove-a-toolstripmenuitem-from-an-mdi-drop-down-menu-windows-forms"></a>Nasıl yapılır: Bir MDI Açılan Menüsünden ToolStripMenuItem kaldırma (Windows Forms)
Bazı uygulamalarda, birden çok belge arabirimi (MDI) alt pencere türü MDI üst penceresinden farklı olabilir. Örneğin, elektronik tablo MDI olabilir ve MDI alt bir grafik olabilir. Bu durumda, farklı türlerde MDI alt pencereleri etkinleştirilmiş olarak MDI üst öğenin menüsünün içeriğini MDI alt menü içeriğini güncelleştirmek istediğiniz.  
  
 Aşağıdaki yordam kullanır <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, ve <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> özellikleri menü öğesi MDI üst menü açılan bölümünden kaldırın. MDI alt pencereyi kaldırılan menü öğelerini MDI üst menüsüne geri yükler.  
  
### <a name="to-remove-a-menustrip-from-an-mdi-drop-down-menu"></a>MenuStrip bir MDI açılan menüsünden kaldırmak için  
  
1.  Bir form oluşturun ve ayarlayın, <xref:System.Windows.Forms.Form.IsMdiContainer%2A> özelliğine `true`.  
  
2.  Ekleme bir <xref:System.Windows.Forms.MenuStrip> için `Form1` ve <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> özelliği <xref:System.Windows.Forms.MenuStrip> için `true`.  
  
3.  Bir üst düzey menü öğesi ekleme `Form1` <xref:System.Windows.Forms.MenuStrip> ve kendi <xref:System.Windows.Forms.Control.Text%2A> özelliğine `&File`.  
  
4.  Üç alt öğeleri Ekle `&File` menü öğesi ve kümesi kendi <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliklerine `&Open`, `&Import from`, ve `E&xit`.  
  
5.  İki alt öğe ekleme `&Import from` alt öğe ve kümesi kendi <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliklerine `&Word` ve `&Excel`.  
  
6.  Projeye form ekleme, ekleme bir <xref:System.Windows.Forms.MenuStrip> form ve kümesi <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> özelliği `Form2` <xref:System.Windows.Forms.MenuStrip> için `true`.  
  
7.  Bir üst düzey menü öğesi ekleme `Form2` <xref:System.Windows.Forms.MenuStrip> ve kendi <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliğine `&File`.  
  
8.  Ekleme bir `&Import from` alt öğeye `&File` menüsünü `Form2`ve ekleyin bir `&Word` alt öğeye `&File` menüsü.  
  
9. Ayarlama <xref:System.Windows.Forms.MergeAction> ve <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> özelliklerini `Form2` menü öğeleri aşağıdaki tabloda gösterildiği gibi.  
  
    |Form2 menü öğesi|MergeAction değeri|MergeIndex değeri|  
    |---------------------|-----------------------|----------------------|  
    |Dosya|MatchOnly|-1|  
    |İçeri aktarın|MatchOnly|-1|  
    |Word|Kaldır|-1|  
  
10. İçinde `Form1`, bir olay işleyicisi oluşturun <xref:System.Windows.Forms.Control.Click> olayı `&Open` <xref:System.Windows.Forms.ToolStripMenuItem>.  
  
11. Olay işleyicisi içinde oluşturmak ve yeni örneklerini görüntülemek için aşağıdaki kod örneğinde benzer bir kod Ekle `Form2` MDI alt öğeleri olarak `Form1`:  
  
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
    this.openToolStripMenuItem.Click += new _  
    System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   İki <xref:System.Windows.Forms.Form> adlı denetimleri `Form1` ve `Form2`.  
  
-   A <xref:System.Windows.Forms.MenuStrip> denetiminin `Form1` adlı `menuStrip1`ve bir <xref:System.Windows.Forms.MenuStrip> denetiminin `Form2` adlı `menuStrip2`.  
  
-   Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: MDI Üst Formları Oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [Nasıl yapılır: MDI Alt Formları Oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [MenuStrip Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
