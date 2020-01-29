---
title: Çoklu bölmeli Kullanıcı arabirimi oluşturma
ms.date: 03/30/2017
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
ms.openlocfilehash: 4b168a6d566e20814d4403f90e157d80efe3bf12
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731341"
---
# <a name="how-to-create-a-multipane-user-interface-with-windows-forms"></a><span data-ttu-id="61c92-102">Nasıl yapılır: Windows Forms'ta Çok Bölmeli Kullanıcı Arabirimi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="61c92-102">How to: Create a Multipane User Interface with Windows Forms</span></span>
<span data-ttu-id="61c92-103">Aşağıdaki yordamda, Microsoft Outlook 'ta kullanılan bir **klasör** listesi, **Iletiler** bölmesi ve **Önizleme** bölmesi ile benzer bir çoklu bölmeli Kullanıcı arabirimi oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="61c92-103">In the following procedure, you will create a multipane user interface that is similar to the one used in Microsoft Outlook, with a **Folder** list, a **Messages** pane, and a **Preview** pane.</span></span> <span data-ttu-id="61c92-104">Bu düzenleme, formla birlikte yerleştirme denetimleri aracılığıyla oyda elde edilir.</span><span class="sxs-lookup"><span data-stu-id="61c92-104">This arrangement is achieved chiefly through docking controls with the form.</span></span>  
  
 <span data-ttu-id="61c92-105">Bir denetimi yuvadığınızda, üst kapsayıcının bir denetimin hangi kenarının ' a ekleneceğini belirlersiniz.</span><span class="sxs-lookup"><span data-stu-id="61c92-105">When you dock a control, you determine which edge of the parent container a control is fastened to.</span></span> <span data-ttu-id="61c92-106">Bu nedenle, <xref:System.Windows.Forms.SplitContainer.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Right>olarak ayarlarsanız, denetimin sağ kenarı üst denetiminin sağ kenarına yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="61c92-106">Thus, if you set the <xref:System.Windows.Forms.SplitContainer.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Right>, the right edge of the control will be docked to the right edge of its parent control.</span></span> <span data-ttu-id="61c92-107">Ayrıca, denetimin yerleşik kenarı kapsayıcı denetimiyle eşleşecek şekilde yeniden boyutlandırılır.</span><span class="sxs-lookup"><span data-stu-id="61c92-107">Additionally, the docked edge of the control is resized to match that of its container control.</span></span> <span data-ttu-id="61c92-108"><xref:System.Windows.Forms.SplitContainer.Dock%2A> özelliğinin nasıl çalıştığı hakkında daha fazla bilgi için bkz. [nasıl yapılır: denetimleri yerleştirme Windows Forms](how-to-dock-controls-on-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="61c92-108">For more information about how the <xref:System.Windows.Forms.SplitContainer.Dock%2A> property works, see [How to: Dock Controls on Windows Forms](how-to-dock-controls-on-windows-forms.md).</span></span>  
  
 <span data-ttu-id="61c92-109">Bu yordam, uygulamanın Microsoft Outlook 'U taklit etmek için işlev ekleme üzerine değil, <xref:System.Windows.Forms.SplitContainer> ve formdaki diğer denetimleri düzenleme konusunda odaklanır.</span><span class="sxs-lookup"><span data-stu-id="61c92-109">This procedure focuses on arranging the <xref:System.Windows.Forms.SplitContainer> and the other controls on the form, not on adding functionality to make the application mimic Microsoft Outlook.</span></span>  
  
 <span data-ttu-id="61c92-110">Bu Kullanıcı arabirimini oluşturmak için, tüm denetimleri sol bölmedeki bir <xref:System.Windows.Forms.TreeView> denetimi içeren bir <xref:System.Windows.Forms.SplitContainer> denetimine yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="61c92-110">To create this user interface, you place all the controls within a <xref:System.Windows.Forms.SplitContainer> control, which contains a <xref:System.Windows.Forms.TreeView> control in the left-hand panel.</span></span> <span data-ttu-id="61c92-111"><xref:System.Windows.Forms.SplitContainer> denetiminin sağ paneli, bir <xref:System.Windows.Forms.RichTextBox> denetiminin üzerinde <xref:System.Windows.Forms.ListView> denetimine sahip ikinci bir <xref:System.Windows.Forms.SplitContainer> denetimi içerir.</span><span class="sxs-lookup"><span data-stu-id="61c92-111">The right-hand panel of the <xref:System.Windows.Forms.SplitContainer> control contains a second <xref:System.Windows.Forms.SplitContainer> control with a <xref:System.Windows.Forms.ListView> control above a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="61c92-112">Bu <xref:System.Windows.Forms.SplitContainer> denetimleri, formdaki diğer denetimlerin bağımsız yeniden boyutlandırılmasını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="61c92-112">These <xref:System.Windows.Forms.SplitContainer> controls enable independent resizing of the other controls on the form.</span></span> <span data-ttu-id="61c92-113">Kendi özel kullanıcı arabirimlerini daha fazla yapmak için bu yordamın tekniklerini uyarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="61c92-113">You can adapt the techniques in this procedure to craft custom user interfaces of your own.</span></span>  
  
### <a name="to-create-an-outlook-style-user-interface-programmatically"></a><span data-ttu-id="61c92-114">Programlı olarak Outlook stili bir kullanıcı arabirimi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="61c92-114">To create an Outlook-style user interface programmatically</span></span>  
  
1. <span data-ttu-id="61c92-115">Bir form içinde, Kullanıcı arabiriminizi içeren her denetimi bildirin.</span><span class="sxs-lookup"><span data-stu-id="61c92-115">Within a form, declare each control that comprises your user interface.</span></span> <span data-ttu-id="61c92-116">Bu örnekte, Microsoft Outlook Kullanıcı arabirimini taklit etmek için <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.SplitContainer>ve <xref:System.Windows.Forms.RichTextBox> denetimlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="61c92-116">For this example, use the <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.SplitContainer>, and <xref:System.Windows.Forms.RichTextBox> controls to mimic the Microsoft Outlook user interface.</span></span>  
  
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
  
2. <span data-ttu-id="61c92-117">Kullanıcı arabiriminizi tanımlayan bir yordam oluşturun.</span><span class="sxs-lookup"><span data-stu-id="61c92-117">Create a procedure that defines your user interface.</span></span> <span data-ttu-id="61c92-118">Aşağıdaki kod, formun Microsoft Outlook 'taki Kullanıcı arabirimine benzeyecek şekilde özellikleri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="61c92-118">The following code sets the properties so that the form will resemble the user interface in Microsoft Outlook.</span></span> <span data-ttu-id="61c92-119">Ancak, diğer denetimleri kullanarak veya farklı şekilde yuvalanarak, eşit derecede esnek olan diğer kullanıcı arabirimlerini kolayca oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="61c92-119">However, by using other controls or docking them differently, it is just as easy to create other user interfaces that are equally flexible.</span></span>  
  
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
  
3. <span data-ttu-id="61c92-120">Visual Basic, `New()` yordamında yeni oluşturduğunuz yordama bir çağrı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="61c92-120">In Visual Basic, add a call to the procedure you just created in the `New()` procedure.</span></span> <span data-ttu-id="61c92-121">Görsel C#' te bu kod satırını Form sınıfı için oluşturucuya ekleyin.</span><span class="sxs-lookup"><span data-stu-id="61c92-121">In Visual C#, add this line of code to the constructor for the form class.</span></span>  
  
    ```vb  
    ' Add this to the New procedure.  
    CreateOutlookUI()  
    ```  
  
    ```csharp  
    // Add this to the form class's constructor.  
    createOutlookUI();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="61c92-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="61c92-122">See also</span></span>

- <xref:System.Windows.Forms.SplitContainer>
- [<span data-ttu-id="61c92-123">SplitContainer Denetimi</span><span class="sxs-lookup"><span data-stu-id="61c92-123">SplitContainer Control</span></span>](splitcontainer-control-windows-forms.md)
- [<span data-ttu-id="61c92-124">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms ile Çok Bölmeli bir Kullanıcı Arabirimi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="61c92-124">How to: Create a Multipane User Interface with Windows Forms Using the Designer</span></span>](create-a-multipane-user-interface-with-wf-using-the-designer.md)
