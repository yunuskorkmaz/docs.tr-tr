---
title: 'Nasıl yapılır: Windows Forms ile çok bölmeli kullanıcı arabirimi oluşturma'
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
ms.openlocfilehash: 1f7ba0ab7f0701fe39c3cefb979b9226eeeddffe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54531414"
---
# <a name="how-to-create-a-multipane-user-interface-with-windows-forms"></a><span data-ttu-id="622bb-102">Nasıl yapılır: Windows Forms ile çok bölmeli kullanıcı arabirimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="622bb-102">How to: Create a Multipane User Interface with Windows Forms</span></span>
<span data-ttu-id="622bb-103">Aşağıdaki yordamda, Microsoft Outlook ile kullanılan benzer çok bölmeli kullanıcı arabirimi oluşturacaksınız bir **klasör** listesinde bir **iletileri** bölmesinde ve **Önizleme** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="622bb-103">In the following procedure, you will create a multipane user interface that is similar to the one used in Microsoft Outlook, with a **Folder** list, a **Messages** pane, and a **Preview** pane.</span></span> <span data-ttu-id="622bb-104">Bu düzenleme formu denetimleri yerleştirme temelde aracılığıyla sağlanır.</span><span class="sxs-lookup"><span data-stu-id="622bb-104">This arrangement is achieved chiefly through docking controls with the form.</span></span>  
  
 <span data-ttu-id="622bb-105">Bir denetim noktası, üst kapsayıcı hangi kenarı bir denetim için fastened belirleyin.</span><span class="sxs-lookup"><span data-stu-id="622bb-105">When you dock a control, you determine which edge of the parent container a control is fastened to.</span></span> <span data-ttu-id="622bb-106">Bu nedenle, eğer ayarlarsanız <xref:System.Windows.Forms.SplitContainer.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Right>, denetimin sağ kenarı sağ, üst denetim kenarına yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="622bb-106">Thus, if you set the <xref:System.Windows.Forms.SplitContainer.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Right>, the right edge of the control will be docked to the right edge of its parent control.</span></span> <span data-ttu-id="622bb-107">Buna ek olarak, yerleşik uç denetimin, kapsayıcı denetimdeki eşleşmesi için yeniden boyutlandırılır.</span><span class="sxs-lookup"><span data-stu-id="622bb-107">Additionally, the docked edge of the control is resized to match that of its container control.</span></span> <span data-ttu-id="622bb-108">Nasıl hakkında daha fazla bilgi için <xref:System.Windows.Forms.SplitContainer.Dock%2A> özelliği çalıştığını görmek [nasıl yapılır: Windows Forms'da denetimleri](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="622bb-108">For more information about how the <xref:System.Windows.Forms.SplitContainer.Dock%2A> property works, see [How to: Dock Controls on Windows Forms](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md).</span></span>  
  
 <span data-ttu-id="622bb-109">Bu yordam, düzenleme üzerinde odaklanır <xref:System.Windows.Forms.SplitContainer> ve diğer denetimleri form üzerinde Microsoft Outlook taklit uygulama işlevselliği ekleme değil.</span><span class="sxs-lookup"><span data-stu-id="622bb-109">This procedure focuses on arranging the <xref:System.Windows.Forms.SplitContainer> and the other controls on the form, not on adding functionality to make the application mimic Microsoft Outlook.</span></span>  
  
 <span data-ttu-id="622bb-110">Bu kullanıcı arabirimi oluşturmak için içindeki tüm denetimleri yerleştirin. bir <xref:System.Windows.Forms.SplitContainer> içeren denetim bir <xref:System.Windows.Forms.TreeView> sol panelde bir denetim.</span><span class="sxs-lookup"><span data-stu-id="622bb-110">To create this user interface, you place all the controls within a <xref:System.Windows.Forms.SplitContainer> control, which contains a <xref:System.Windows.Forms.TreeView> control in the left-hand panel.</span></span> <span data-ttu-id="622bb-111">' In sağ bölmeyi <xref:System.Windows.Forms.SplitContainer> denetimi içeren ikinci bir <xref:System.Windows.Forms.SplitContainer> denetimini bir <xref:System.Windows.Forms.ListView> denetim yukarıdaki bir <xref:System.Windows.Forms.RichTextBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="622bb-111">The right-hand panel of the <xref:System.Windows.Forms.SplitContainer> control contains a second <xref:System.Windows.Forms.SplitContainer> control with a <xref:System.Windows.Forms.ListView> control above a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="622bb-112">Bunlar <xref:System.Windows.Forms.SplitContainer> denetimleri, formdaki diğer denetimlerin bağımsız yeniden boyutlandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="622bb-112">These <xref:System.Windows.Forms.SplitContainer> controls enable independent resizing of the other controls on the form.</span></span> <span data-ttu-id="622bb-113">Kendi özel kullanıcı arabirimleri kolaylaştırıyor için bu yordamdaki teknikleri uyarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="622bb-113">You can adapt the techniques in this procedure to craft custom user interfaces of your own.</span></span>  
  
### <a name="to-create-an-outlook-style-user-interface-programmatically"></a><span data-ttu-id="622bb-114">Program aracılığıyla Outlook-stilinde bir kullanıcı arabirimi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="622bb-114">To create an Outlook-style user interface programmatically</span></span>  
  
1.  <span data-ttu-id="622bb-115">Bir form içinde kullanıcı arabirimi oluşturan her denetimi bildirin.</span><span class="sxs-lookup"><span data-stu-id="622bb-115">Within a form, declare each control that comprises your user interface.</span></span> <span data-ttu-id="622bb-116">Bu örneğin <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.SplitContainer>, ve <xref:System.Windows.Forms.RichTextBox> Microsoft Outlook kullanıcı arabirimini taklit edecek şekilde kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="622bb-116">For this example, use the <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.SplitContainer>, and <xref:System.Windows.Forms.RichTextBox> controls to mimic the Microsoft Outlook user interface.</span></span>  
  
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
  
2.  <span data-ttu-id="622bb-117">Kullanıcı arabiriminizi tanımlayan bir yordamı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="622bb-117">Create a procedure that defines your user interface.</span></span> <span data-ttu-id="622bb-118">Aşağıdaki kod, böylece form Microsoft Outlook kullanıcı arabiriminde andıracaktır özelliklerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="622bb-118">The following code sets the properties so that the form will resemble the user interface in Microsoft Outlook.</span></span> <span data-ttu-id="622bb-119">Ancak, diğer denetimleri kullanarak veya farklı yerleştirme, eşit oranda esnek diğer kullanıcı arabirimleri oluşturmak oldukça kolaydır.</span><span class="sxs-lookup"><span data-stu-id="622bb-119">However, by using other controls or docking them differently, it is just as easy to create other user interfaces that are equally flexible.</span></span>  
  
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
  
3.  <span data-ttu-id="622bb-120">Visual Basic'te, yeni oluşturduğunuz yordam bir çağrı ekleyin `New()` yordamı.</span><span class="sxs-lookup"><span data-stu-id="622bb-120">In Visual Basic, add a call to the procedure you just created in the `New()` procedure.</span></span> <span data-ttu-id="622bb-121">Görselde C#, form sınıfın oluşturucusunda Bu kod satırını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="622bb-121">In Visual C#, add this line of code to the constructor for the form class.</span></span>  
  
    ```vb  
    ' Add this to the New procedure.  
    CreateOutlookUI()  
    ```  
  
    ```csharp  
    // Add this to the form class's constructor.  
    createOutlookUI();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="622bb-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="622bb-122">See also</span></span>
- <xref:System.Windows.Forms.SplitContainer>
- [<span data-ttu-id="622bb-123">SplitContainer Denetimi</span><span class="sxs-lookup"><span data-stu-id="622bb-123">SplitContainer Control</span></span>](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)
- [<span data-ttu-id="622bb-124">Nasıl yapılır: Tasarımcı kullanarak Windows Forms ile çok bölmeli kullanıcı arabirimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="622bb-124">How to: Create a Multipane User Interface with Windows Forms Using the Designer</span></span>](../../../../docs/framework/winforms/controls/create-a-multipane-user-interface-with-wf-using-the-designer.md)
