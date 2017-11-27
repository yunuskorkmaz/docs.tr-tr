---
title: "Nasıl yapılır: Windows Forms'ta Çok Bölmeli Kullanıcı Arabirimi Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SplitContainer control [Windows Forms], examples
- ListView control [Windows Forms], examples
- RichTextBox control [Windows Forms], examples
- Panel control [Windows Forms], examples
- TreeView control [Windows Forms], examples
- Splitter control [Windows Forms], examples
ms.assetid: e79f6bcc-3740-4d1e-b46a-c5594d9b7327
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6db621912e76d24b05c8dcdca7f1d3f4e62c2838
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-multipane-user-interface-with-windows-forms"></a>Nasıl yapılır: Windows Forms'ta Çok Bölmeli Kullanıcı Arabirimi Oluşturma
Aşağıdaki yordamda, Microsoft Outlook ile kullanılan benzer çok bölmeli kullanıcı arabirimi oluşturacak bir **klasörü** listesinde, bir **iletileri** bölmesinde ve **Önizleme** bölmesi. Bu düzenlemenin, formun denetimleriyle chiefly yerleştirme aracılığıyla elde edilir.  
  
 Bir denetim noktası olduğunda, bir denetim üst kapsayıcı hangi kenarı fastened belirler. Bu nedenle, ayarlarsanız <xref:System.Windows.Forms.SplitContainer.Dock%2A> özelliğine <xref:System.Windows.Forms.DockStyle.Right>, denetimin sağ kenarı sağ, üst denetim kenarına yerleştirilir. Ayrıca, kapsayıcı denetiminin eşleşen denetim yerleşik kenarı boyutlandırılır. Ne hakkında daha fazla bilgi için <xref:System.Windows.Forms.SplitContainer.Dock%2A> özelliği çalıştığını görmek [nasıl yapılır: Windows formlarında denetimleri yerleştirme](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md).  
  
 Bu yordam, düzenleme üzerinde odaklanır <xref:System.Windows.Forms.SplitContainer> ve diğer denetimleri form üzerinde Microsoft Outlook taklit uygulama yapmayı işlevselliği ekleme değil.  
  
 Bu kullanıcı arabirimi oluşturmak için içindeki tüm denetimler yerleştirin bir <xref:System.Windows.Forms.SplitContainer> içeren denetim bir <xref:System.Windows.Forms.TreeView> sol panelinde denetim. Sağ taraftaki panelinin <xref:System.Windows.Forms.SplitContainer> denetimi içeren ikinci bir <xref:System.Windows.Forms.SplitContainer> ile denetleyen bir <xref:System.Windows.Forms.ListView> yukarıdaki denetimi bir <xref:System.Windows.Forms.RichTextBox> denetim. Bunlar <xref:System.Windows.Forms.SplitContainer> denetimlerini etkinleştir diğer denetimleri form üzerinde bağımsız yeniden boyutlandırma. Kendi craft özel kullanıcı arabirimleri için bu yordamdaki teknikleri uyarlayabilirsiniz.  
  
### <a name="to-create-an-outlook-style-user-interface-programmatically"></a>Program aracılığıyla Outlook stilinde bir kullanıcı arabirimi oluşturmak için  
  
1.  Bir form içinde Kullanıcı Arabiriminizin oluşur her denetimi bildirin. Bu örneğin <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.SplitContainer>, ve <xref:System.Windows.Forms.RichTextBox> Microsoft Outlook kullanıcı arabirimi taklit etmek için kontrol eder.  
  
    ```vb  
    Private WithEvents treeView1 As System.Windows.Forms.TreeView  
    Private WithEvents listView1 As System.Windows.Forms.ListView  
    Private WithEvents richTextBox1 As System.Windows.Forms.RichTextBox  
    Private WithEvents splitContainer1 As _  
        System.Windows.Forms.SplitContainer  
    Private WithEvents splitContainer2 As _  
        System.Windows.Forms.SplitContainer  
    ```  
  
    ```csharp  
    private System.Windows.Forms.TreeView treeView1;  
    private System.Windows.Forms.ListView listView1;  
    private System.Windows.Forms.RichTextBox richTextBox1;  
    private System.Windows.Forms. SplitContainer splitContainer2;  
    private System.Windows.Forms. SplitContainer splitContainer1;  
    ```  
  
2.  Kullanıcı Arabiriminizin tanımlayan bir yordam oluşturun. Aşağıdaki kod özelliklerini ayarlar, böylece form Microsoft Outlook kullanıcı arabiriminde benzeyecektir. Ancak, diğer denetimleri kullanarak veya farklı yerleştirme eşit esnek diğer kullanıcı arabirimleri oluşturmak yalnızca kadar kolaydır.  
  
    ```vb  
    Public Sub CreateOutlookUI()  
        ' Create an instance of each control being used.  
        Me.components = New System.ComponentModel.Container()  
        Me.treeView1 = New System.Windows.Forms.TreeView()  
        Me.listView1 = New System.Windows.Forms.ListView()  
        Me.richTextBox1 = New System.Windows.Forms.RichTextBox()  
        Me.splitContainer1 = New System.Windows.Forms.SplitContainer()  
        Me.splitContainer2= New System.Windows.Forms. SplitContainer()  
  
        ' Should you develop this into a working application,  
        ' use the AddHandler method to hook up event procedures here.  
  
        ' Set properties of TreeView control.  
        ' Use the With statement to avoid repetitive code.  
        With Me.treeView1  
            .Dock = System.Windows.Forms.DockStyle.Fill  
            .TabIndex = 0  
            .Nodes.Add("treeView")  
        End With  
  
    ' Set properties of ListView control.  
       With Me.listView1  
          .Dock = System.Windows.Forms.DockStyle.Top  
          .TabIndex = 2  
          .Items.Add("listView")  
       End With  
  
    ' Set properties of RichTextBox control.  
       With Me.richTextBox1  
          .Dock = System.Windows.Forms.DockStyle.Fill  
          .TabIndex = 3  
          .Text = "richTextBox1"  
       End With  
  
        ' Set properties of the first SplitContainer control.  
        With Me.splitContainer1  
            .Dock = System.Windows.Forms.DockStyle.Fill  
            .TabIndex = 1  
            .SplitterWidth = 4  
            .SplitterDistance = 150  
            .Orientation = Orientation.Horizontal  
            .Panel1.Controls.Add(Me.listView1)  
            .Panel2.Controls.Add(Me.richTextBox1)  
    End With  
  
        ' Set properties of the second SplitContainer control.  
        With Me.splitContainer2  
            .Dock = System.Windows.Forms.DockStyle.Fill  
            .TabIndex = 4  
            .SplitterWidth = 4  
            .SplitterDistance = 100  
            .Panel1.Controls.Add(Me.treeView1)  
            .Panel2.Controls.Add(Me.SplitContainer1)  
    End With  
  
    ' Add the main SplitContainer control to the form.  
        Me.Controls.Add(Me.splitContainer2)  
        Me.Text = "Intricate UI Example"  
    End Sub  
    ```  
  
    ```csharp  
    public void createOutlookUI()  
    {  
        // Create an instance of each control being used.  
        treeView1 = new System.Windows.Forms.TreeView();  
        listView1 = new System.Windows.Forms.ListView();  
        richTextBox1 = new System.Windows.Forms.RichTextBox();  
        splitContainer2 = new System.Windows.Forms.SplitContainer();  
        splitContainer1 = new System.Windows.Forms.SplitContainer();  
  
        // Insert code here to hook up event methods.  
  
        // Set properties of TreeView control.  
        treeView1.Dock = System.Windows.Forms.DockStyle.Fill;  
        treeView1.TabIndex = 0;  
        treeView1.Nodes.Add("treeView");  
  
        // Set properties of ListView control.  
        listView1.Dock = System.Windows.Forms.DockStyle.Top;  
        listView1.TabIndex = 2;  
        listView1.Items.Add("listView");  
  
        // Set properties of RichTextBox control.  
        richTextBox1.Dock = System.Windows.Forms.DockStyle.Fill;  
        richTextBox1.TabIndex = 3;  
        richTextBox1.Text = "richTextBox1";  
  
        // Set properties of first SplitContainer control.  
        splitContainer1.Dock = System.Windows.Forms.DockStyle.Fill;  
        splitContainer2.TabIndex = 1;  
        splitContainer2.SplitterWidth = 4;  
        splitContainer2.SplitterDistance = 150;  
        splitContainer2.Orientation = Orientation.Horizontal;  
        splitContainer2.Panel1.Controls.Add(this.listView1);  
        splitContainer2.Panel1.Controls.Add(this.richTextBox1);  
  
        // Set properties of second SplitContainer control.  
        splitContainer2.Dock = System.Windows.Forms.DockStyle.Fill;  
        splitContainer2.TabIndex = 4;  
        splitContainer2.SplitterWidth = 4;  
        splitContainer2.SplitterDistance = 100;  
        splitContainer2.Panel1.Controls.Add(this.treeView1);  
        splitContainer2.Panel1.Controls.Add(this.splitContainer1);  
  
        // Add the main SplitContainer control to the form.  
        this.Controls.Add(this.splitContainer2);  
        this.Text = "Intricate UI Example";  
    }  
    ```  
  
3.  İçinde [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], yeni oluşturduğunuz yordamı bir çağrı ekleyin `New()` yordamı. İçinde [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], form sınıfı oluşturucusu Bu kod satırını ekleyin.  
  
    ```vb  
    ' Add this to the New procedure.  
    CreateOutlookUI()  
    ```  
  
    ```csharp  
    // Add this to the form class's constructor.  
    createOutlookUI();  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.SplitContainer>  
 [SplitContainer denetimi](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)  
 [Nasıl yapılır: Tasarımcı kullanarak Windows formları ile çok bölmeli kullanıcı arabirimi oluşturma](../../../../docs/framework/winforms/controls/create-a-multipane-user-interface-with-wf-using-the-designer.md)
