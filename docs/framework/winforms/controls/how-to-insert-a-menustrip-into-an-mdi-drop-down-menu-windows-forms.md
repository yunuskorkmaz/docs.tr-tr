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
# <a name="how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms"></a><span data-ttu-id="b06f3-102">Nasıl yapılır: Bir MDI Açılan Menüsüne MenuStrip ekleme (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="b06f3-102">How to: Insert a MenuStrip into an MDI Drop-Down Menu (Windows Forms)</span></span>
<span data-ttu-id="b06f3-103">Bazı uygulamalarda, bir çoklu belge arabirimi (MDI) alt penceresinin türü MDI ana penceresinden farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="b06f3-103">In some applications, the kind of a multiple-document interface (MDI) child window can be different from the MDI parent window.</span></span> <span data-ttu-id="b06f3-104">Örneğin, MDI parent bir elektronik tablo olabilir ve MDI alt öğesi bir grafik olabilir.</span><span class="sxs-lookup"><span data-stu-id="b06f3-104">For example, the MDI parent might be a spreadsheet, and the MDI child might be a chart.</span></span> <span data-ttu-id="b06f3-105">Bu durumda, farklı türlerdeki MDI alt pencereleri etkinleştirildiğinden MDI üst öğesinin menüsünün içeriğini MDI alt menüsünün içeriğiyle güncelleştirmek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="b06f3-105">In that case, you want to update the contents of the MDI parent's menu with the contents of the MDI child's menu as MDI child windows of different kinds are activated.</span></span>  
  
 <span data-ttu-id="b06f3-106">Aşağıdaki yordam, MDI alt menüsünden bir menü öğeleri grubunu MDI üst menüsünün aşağı açılan kısmına eklemek için <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>ve <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> özelliklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="b06f3-106">The following procedure uses the <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties to insert a group of menu items from the MDI child menu into the drop-down part of the MDI parent menu.</span></span> <span data-ttu-id="b06f3-107">MDI alt penceresini kapatmak, ekli menü öğelerini MDI üst öğesinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="b06f3-107">Closing the MDI child window removes the inserted menu items from the MDI parent.</span></span>  
  
### <a name="to-insert-a-menustrip-into-an-mdi-drop-down-menu"></a><span data-ttu-id="b06f3-108">Bir MDI açılan menüsüne MenuStrip eklemek için</span><span class="sxs-lookup"><span data-stu-id="b06f3-108">To insert a MenuStrip into an MDI drop-down menu</span></span>  
  
1. <span data-ttu-id="b06f3-109">Bir form oluşturun ve <xref:System.Windows.Forms.Form.IsMdiContainer%2A> özelliğini `true`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b06f3-109">Create a form and set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2. <span data-ttu-id="b06f3-110">`Form1` <xref:System.Windows.Forms.MenuStrip> ekleyin ve <xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> özelliğini `true`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b06f3-110">Add a <xref:System.Windows.Forms.MenuStrip> to `Form1` and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the <xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
3. <span data-ttu-id="b06f3-111">`Form1`<xref:System.Windows.Forms.MenuStrip> en üst düzey menü öğesini ekleyin ve <xref:System.Windows.Forms.Control.Text%2A> özelliğini `&File`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b06f3-111">Add a top-level menu item to the `Form1`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.Control.Text%2A> property to `&File`.</span></span>  
  
4. <span data-ttu-id="b06f3-112">`&File` menü öğesine üç alt menü öğesi ekleyin ve <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliklerini `&Open`, `&Import from`ve `E&xit`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b06f3-112">Add three submenu items to the `&File` menu item and set their <xref:System.Windows.Forms.ToolStripItem.Text%2A> properties to `&Open`, `&Import from`, and `E&xit`.</span></span>  
  
5. <span data-ttu-id="b06f3-113">`&Import from` alt menü öğesine iki alt menü öğesi ekleyin ve <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliklerini `&Word` ve `&Excel`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b06f3-113">Add two submenu items to the `&Import from` submenu item and set their <xref:System.Windows.Forms.ToolStripItem.Text%2A> properties to `&Word` and `&Excel`.</span></span>  
  
6. <span data-ttu-id="b06f3-114">Projeye bir form ekleyin, forma <xref:System.Windows.Forms.MenuStrip> ekleyin ve `Form2`<xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> özelliğini `true`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b06f3-114">Add a form to the project, add a <xref:System.Windows.Forms.MenuStrip> to the form, and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the `Form2`<xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
7. <span data-ttu-id="b06f3-115">`Form2`<xref:System.Windows.Forms.MenuStrip> en üst düzey menü öğesini ekleyin ve <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliğini `&File`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b06f3-115">Add a top-level menu item to the `Form2`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to `&File`.</span></span>  
  
8. <span data-ttu-id="b06f3-116">`Form2` `&File` menüsüne alt menü öğelerini şu sırada ekleyin: bir <xref:System.Windows.Forms.ToolStripSeparator>, `&Save`, `Save and &Close`ve başka bir <xref:System.Windows.Forms.ToolStripSeparator>.</span><span class="sxs-lookup"><span data-stu-id="b06f3-116">Add submenu items to the `&File` menu of `Form2` in the following order: a <xref:System.Windows.Forms.ToolStripSeparator>, `&Save`, `Save and &Close`, and another <xref:System.Windows.Forms.ToolStripSeparator>.</span></span>  
  
9. <span data-ttu-id="b06f3-117">Aşağıdaki tabloda gösterildiği gibi `Form2` menü öğelerinin <xref:System.Windows.Forms.MergeAction> ve <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b06f3-117">Set the <xref:System.Windows.Forms.MergeAction> and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties of the `Form2` menu items as shown in the following table.</span></span>  
  
    |<span data-ttu-id="b06f3-118">Form2 menü öğesi</span><span class="sxs-lookup"><span data-stu-id="b06f3-118">Form2 menu item</span></span>|<span data-ttu-id="b06f3-119">MergeAction değeri</span><span class="sxs-lookup"><span data-stu-id="b06f3-119">MergeAction value</span></span>|<span data-ttu-id="b06f3-120">MergeIndex değeri</span><span class="sxs-lookup"><span data-stu-id="b06f3-120">MergeIndex value</span></span>|  
    |---------------------|-----------------------|----------------------|  
    |<span data-ttu-id="b06f3-121">Dosya</span><span class="sxs-lookup"><span data-stu-id="b06f3-121">File</span></span>|<span data-ttu-id="b06f3-122">Yalnızca eşleşme</span><span class="sxs-lookup"><span data-stu-id="b06f3-122">MatchOnly</span></span>|<span data-ttu-id="b06f3-123">-1</span><span class="sxs-lookup"><span data-stu-id="b06f3-123">-1</span></span>|  
    |<span data-ttu-id="b06f3-124">Ayırıcı</span><span class="sxs-lookup"><span data-stu-id="b06f3-124">Separator</span></span>|<span data-ttu-id="b06f3-125">Ekleme</span><span class="sxs-lookup"><span data-stu-id="b06f3-125">Insert</span></span>|<span data-ttu-id="b06f3-126">2</span><span class="sxs-lookup"><span data-stu-id="b06f3-126">2</span></span>|  
    |<span data-ttu-id="b06f3-127">Kaydet</span><span class="sxs-lookup"><span data-stu-id="b06f3-127">Save</span></span>|<span data-ttu-id="b06f3-128">Ekleme</span><span class="sxs-lookup"><span data-stu-id="b06f3-128">Insert</span></span>|<span data-ttu-id="b06f3-129">3</span><span class="sxs-lookup"><span data-stu-id="b06f3-129">3</span></span>|  
    |<span data-ttu-id="b06f3-130">Kaydet ve Kapat</span><span class="sxs-lookup"><span data-stu-id="b06f3-130">Save and Close</span></span>|<span data-ttu-id="b06f3-131">Ekleme</span><span class="sxs-lookup"><span data-stu-id="b06f3-131">Insert</span></span>|<span data-ttu-id="b06f3-132">4</span><span class="sxs-lookup"><span data-stu-id="b06f3-132">4</span></span>|  
    |<span data-ttu-id="b06f3-133">Ayırıcı</span><span class="sxs-lookup"><span data-stu-id="b06f3-133">Separator</span></span>|<span data-ttu-id="b06f3-134">Ekleme</span><span class="sxs-lookup"><span data-stu-id="b06f3-134">Insert</span></span>|<span data-ttu-id="b06f3-135">5</span><span class="sxs-lookup"><span data-stu-id="b06f3-135">5</span></span>|  
  
10. <span data-ttu-id="b06f3-136">`&Open`<xref:System.Windows.Forms.ToolStripMenuItem><xref:System.Windows.Forms.Control.Click> olayı için bir olay işleyicisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b06f3-136">Create an event handler for the <xref:System.Windows.Forms.Control.Click> event of the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
11. <span data-ttu-id="b06f3-137">Olay işleyicisi içinde, `Form1`MDI alt öğeleri olarak `Form2` yeni örneklerini oluşturmak ve göstermek için aşağıdaki kod örneğine benzer bir kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b06f3-137">Within the event handler, insert code similar to the following code example to create and display new instances of `Form2` as MDI children of `Form1`.</span></span>  
  
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
  
12. <span data-ttu-id="b06f3-138">Olay işleyicisini kaydetmek için `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> aşağıdaki kod örneğine benzer bir kod koyun.</span><span class="sxs-lookup"><span data-stu-id="b06f3-138">Place code similar to the following code example in the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> to register the event handler.</span></span>  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b06f3-139">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="b06f3-139">Compiling the Code</span></span>  
 <span data-ttu-id="b06f3-140">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="b06f3-140">This example requires:</span></span>  
  
- <span data-ttu-id="b06f3-141">`Form1` ve `Form2`adlı iki <xref:System.Windows.Forms.Form> denetimi.</span><span class="sxs-lookup"><span data-stu-id="b06f3-141">Two <xref:System.Windows.Forms.Form> controls named `Form1` and `Form2`.</span></span>  
  
- <span data-ttu-id="b06f3-142">`menuStrip1`adlı `Form1` ve `Form2` adlı `menuStrip2`<xref:System.Windows.Forms.MenuStrip> bir denetim <xref:System.Windows.Forms.MenuStrip> denetimi.</span><span class="sxs-lookup"><span data-stu-id="b06f3-142">A <xref:System.Windows.Forms.MenuStrip> control on `Form1` named `menuStrip1`, and a <xref:System.Windows.Forms.MenuStrip> control on `Form2` named `menuStrip2`.</span></span>  
  
- <span data-ttu-id="b06f3-143"><xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="b06f3-143">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b06f3-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b06f3-144">See also</span></span>

- [<span data-ttu-id="b06f3-145">Nasıl yapılır: MDI Üst Formları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b06f3-145">How to: Create MDI Parent Forms</span></span>](../advanced/how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="b06f3-146">Nasıl yapılır: MDI Alt Formları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b06f3-146">How to: Create MDI Child Forms</span></span>](../advanced/how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="b06f3-147">MenuStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b06f3-147">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
