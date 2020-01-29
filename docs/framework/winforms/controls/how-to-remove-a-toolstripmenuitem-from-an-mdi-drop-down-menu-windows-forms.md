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
# <a name="how-to-remove-a-toolstripmenuitem-from-an-mdi-drop-down-menu-windows-forms"></a><span data-ttu-id="e1011-102">Nasıl yapılır: Bir MDI Açılan Menüsünden ToolStripMenuItem kaldırma (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="e1011-102">How to: Remove a ToolStripMenuItem from an MDI Drop-Down Menu (Windows Forms)</span></span>
<span data-ttu-id="e1011-103">Bazı uygulamalarda, bir çoklu belge arabirimi (MDI) alt penceresinin türü MDI ana penceresinden farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="e1011-103">In some applications, the kind of a multiple-document interface (MDI) child window can be different from the MDI parent window.</span></span> <span data-ttu-id="e1011-104">Örneğin, MDI parent bir elektronik tablo olabilir ve MDI alt öğesi bir grafik olabilir.</span><span class="sxs-lookup"><span data-stu-id="e1011-104">For example, the MDI parent might be a spreadsheet, and the MDI child might be a chart.</span></span> <span data-ttu-id="e1011-105">Bu durumda, farklı türlerdeki MDI alt pencereleri etkinleştirildiğinden MDI üst öğesinin menüsünün içeriğini MDI alt menüsünün içeriğiyle güncelleştirmek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="e1011-105">In that case, you want to update the contents of the MDI parent's menu with the contents of the MDI child's menu as MDI child windows of different kinds are activated.</span></span>  
  
 <span data-ttu-id="e1011-106">Aşağıdaki yordam, MDI parent menüsünün açılan kısmından bir menü öğesini kaldırmak için <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>ve <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> özelliklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e1011-106">The following procedure uses the <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties to remove a menu item from the drop-down part of the MDI parent menu.</span></span> <span data-ttu-id="e1011-107">MDI alt penceresini kapatmak kaldırılan menü öğelerini MDI parent menüsüne geri yükler.</span><span class="sxs-lookup"><span data-stu-id="e1011-107">Closing the MDI child window restores the removed menu items to the MDI parent menu.</span></span>  
  
### <a name="to-remove-a-menustrip-from-an-mdi-drop-down-menu"></a><span data-ttu-id="e1011-108">Bir MDI açılan menüsünden MenuStrip 'i kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="e1011-108">To remove a MenuStrip from an MDI drop-down menu</span></span>  
  
1. <span data-ttu-id="e1011-109">Bir form oluşturun ve <xref:System.Windows.Forms.Form.IsMdiContainer%2A> özelliğini `true`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e1011-109">Create a form and set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2. <span data-ttu-id="e1011-110">`Form1` <xref:System.Windows.Forms.MenuStrip> ekleyin ve <xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> özelliğini `true`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e1011-110">Add a <xref:System.Windows.Forms.MenuStrip> to `Form1` and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the <xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
3. <span data-ttu-id="e1011-111">`Form1`<xref:System.Windows.Forms.MenuStrip> en üst düzey menü öğesini ekleyin ve <xref:System.Windows.Forms.Control.Text%2A> özelliğini `&File`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e1011-111">Add a top-level menu item to the `Form1`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.Control.Text%2A> property to `&File`.</span></span>  
  
4. <span data-ttu-id="e1011-112">`&File` menü öğesine üç alt menü öğesi ekleyin ve <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliklerini `&Open`, `&Import from`ve `E&xit`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e1011-112">Add three submenu items to the `&File` menu item and set their <xref:System.Windows.Forms.ToolStripItem.Text%2A> properties to `&Open`, `&Import from`, and `E&xit`.</span></span>  
  
5. <span data-ttu-id="e1011-113">`&Import from` alt menü öğesine iki alt menü öğesi ekleyin ve <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliklerini `&Word` ve `&Excel`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e1011-113">Add two submenu items to the `&Import from` submenu item and set their <xref:System.Windows.Forms.ToolStripItem.Text%2A> properties to `&Word` and `&Excel`.</span></span>  
  
6. <span data-ttu-id="e1011-114">Projeye bir form ekleyin, forma <xref:System.Windows.Forms.MenuStrip> ekleyin ve `Form2`<xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> özelliğini `true`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e1011-114">Add a form to the project, add a <xref:System.Windows.Forms.MenuStrip> to the form, and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the `Form2`<xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
7. <span data-ttu-id="e1011-115">`Form2`<xref:System.Windows.Forms.MenuStrip> en üst düzey menü öğesini ekleyin ve <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliğini `&File`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e1011-115">Add a top-level menu item to the `Form2`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to `&File`.</span></span>  
  
8. <span data-ttu-id="e1011-116">`Form2``&File` menüsüne bir `&Import from` alt menü öğesi ekleyin ve `&File` menüsüne bir `&Word` alt menü öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e1011-116">Add an `&Import from` submenu item to the `&File` menu of `Form2`, and add an `&Word` submenu item to the `&File` menu.</span></span>  
  
9. <span data-ttu-id="e1011-117">Aşağıdaki tabloda gösterildiği gibi `Form2` menü öğelerinin <xref:System.Windows.Forms.MergeAction> ve <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e1011-117">Set the <xref:System.Windows.Forms.MergeAction> and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties of the `Form2` menu items as shown in the following table.</span></span>  
  
    |<span data-ttu-id="e1011-118">Form2 menü öğesi</span><span class="sxs-lookup"><span data-stu-id="e1011-118">Form2 menu item</span></span>|<span data-ttu-id="e1011-119">MergeAction değeri</span><span class="sxs-lookup"><span data-stu-id="e1011-119">MergeAction value</span></span>|<span data-ttu-id="e1011-120">MergeIndex değeri</span><span class="sxs-lookup"><span data-stu-id="e1011-120">MergeIndex value</span></span>|  
    |---------------------|-----------------------|----------------------|  
    |<span data-ttu-id="e1011-121">Dosya</span><span class="sxs-lookup"><span data-stu-id="e1011-121">File</span></span>|<span data-ttu-id="e1011-122">Yalnızca eşleşme</span><span class="sxs-lookup"><span data-stu-id="e1011-122">MatchOnly</span></span>|<span data-ttu-id="e1011-123">-1</span><span class="sxs-lookup"><span data-stu-id="e1011-123">-1</span></span>|  
    |<span data-ttu-id="e1011-124">İçeri aktarma</span><span class="sxs-lookup"><span data-stu-id="e1011-124">Import from</span></span>|<span data-ttu-id="e1011-125">Yalnızca eşleşme</span><span class="sxs-lookup"><span data-stu-id="e1011-125">MatchOnly</span></span>|<span data-ttu-id="e1011-126">-1</span><span class="sxs-lookup"><span data-stu-id="e1011-126">-1</span></span>|  
    |<span data-ttu-id="e1011-127">Word</span><span class="sxs-lookup"><span data-stu-id="e1011-127">Word</span></span>|<span data-ttu-id="e1011-128">Kaldır</span><span class="sxs-lookup"><span data-stu-id="e1011-128">Remove</span></span>|<span data-ttu-id="e1011-129">-1</span><span class="sxs-lookup"><span data-stu-id="e1011-129">-1</span></span>|  
  
10. <span data-ttu-id="e1011-130">`Form1`, `&Open`<xref:System.Windows.Forms.ToolStripMenuItem><xref:System.Windows.Forms.Control.Click> olayı için bir olay işleyicisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e1011-130">In `Form1`, create an event handler for the <xref:System.Windows.Forms.Control.Click> event of the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
11. <span data-ttu-id="e1011-131">Olay işleyicisi içinde, `Form1`MDI alt öğeleri olarak `Form2` yeni örneklerini oluşturmak ve göstermek için aşağıdaki kod örneğine benzer bir kod ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e1011-131">Within the event handler, insert code similar to the following code example to create and display new instances of `Form2` as MDI children of `Form1`:</span></span>  
  
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
  
12. <span data-ttu-id="e1011-132">Olay işleyicisini kaydetmek için `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> aşağıdaki kod örneğine benzer bir kod koyun.</span><span class="sxs-lookup"><span data-stu-id="e1011-132">Place code similar to the following code example in the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> to register the event handler.</span></span>  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new _  
    System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e1011-133">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="e1011-133">Compiling the Code</span></span>  
 <span data-ttu-id="e1011-134">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="e1011-134">This example requires:</span></span>  
  
- <span data-ttu-id="e1011-135">`Form1` ve `Form2`adlı iki <xref:System.Windows.Forms.Form> denetimi.</span><span class="sxs-lookup"><span data-stu-id="e1011-135">Two <xref:System.Windows.Forms.Form> controls named `Form1` and `Form2`.</span></span>  
  
- <span data-ttu-id="e1011-136">`menuStrip1`adlı `Form1` ve `Form2` adlı `menuStrip2`<xref:System.Windows.Forms.MenuStrip> bir denetim <xref:System.Windows.Forms.MenuStrip> denetimi.</span><span class="sxs-lookup"><span data-stu-id="e1011-136">A <xref:System.Windows.Forms.MenuStrip> control on `Form1` named `menuStrip1`, and a <xref:System.Windows.Forms.MenuStrip> control on `Form2` named `menuStrip2`.</span></span>  
  
- <span data-ttu-id="e1011-137"><xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="e1011-137">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1011-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1011-138">See also</span></span>

- [<span data-ttu-id="e1011-139">Nasıl yapılır: MDI Üst Formları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e1011-139">How to: Create MDI Parent Forms</span></span>](../advanced/how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="e1011-140">Nasıl yapılır: MDI Alt Formları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e1011-140">How to: Create MDI Child Forms</span></span>](../advanced/how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="e1011-141">MenuStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e1011-141">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
