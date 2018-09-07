---
title: 'Nasıl yapılır: Bir MDI Açılan Menüsüne MenuStrip ekleme (Windows Forms)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip control [Windows Forms], inserting
- MenuStrip control [Windows Forms], merging
- MDI [Windows Forms], merging menu items
ms.assetid: 0fad444e-26d9-49af-8860-044d9c10d608
ms.openlocfilehash: 64e7e7875a635bcd4fbafb62d3ee7b7018214ee4
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44067480"
---
# <a name="how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms"></a><span data-ttu-id="a84b8-102">Nasıl yapılır: Bir MDI Açılan Menüsüne MenuStrip ekleme (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="a84b8-102">How to: Insert a MenuStrip into an MDI Drop-Down Menu (Windows Forms)</span></span>
<span data-ttu-id="a84b8-103">Bazı uygulamalarda, bir Çoklu belge arabirimi (MDI) alt penceresi türünü MDI ana penceresinde farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="a84b8-103">In some applications, the kind of a multiple-document interface (MDI) child window can be different from the MDI parent window.</span></span> <span data-ttu-id="a84b8-104">Örneğin, bir elektronik tablo MDI olabilir ve MDI alt bir grafik olabilir.</span><span class="sxs-lookup"><span data-stu-id="a84b8-104">For example, the MDI parent might be a spreadsheet, and the MDI child might be a chart.</span></span> <span data-ttu-id="a84b8-105">Bu durumda, farklı türlerde MDI alt pencereleri etkin olarak MDI üst menü içeriğini MDI alt menü içeriğini güncelleştirmek istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="a84b8-105">In that case, you want to update the contents of the MDI parent's menu with the contents of the MDI child's menu as MDI child windows of different kinds are activated.</span></span>  
  
 <span data-ttu-id="a84b8-106">Aşağıdaki yordam kullanır <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, ve <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> özellikleri menü öğelerinin bir grup MDI alt menüsünden MDI üst menünün aşağı açılan bölümüne eklenecek.</span><span class="sxs-lookup"><span data-stu-id="a84b8-106">The following procedure uses the <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties to insert a group of menu items from the MDI child menu into the drop-down part of the MDI parent menu.</span></span> <span data-ttu-id="a84b8-107">MDI alt penceresini kapatarak MDI üst eklenen menü öğeleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="a84b8-107">Closing the MDI child window removes the inserted menu items from the MDI parent.</span></span>  
  
### <a name="to-insert-a-menustrip-into-an-mdi-drop-down-menu"></a><span data-ttu-id="a84b8-108">Bir MDI açılan menüsüne MenuStrip ekleme için</span><span class="sxs-lookup"><span data-stu-id="a84b8-108">To insert a MenuStrip into an MDI drop-down menu</span></span>  
  
1.  <span data-ttu-id="a84b8-109">Bir form oluşturun ve ayarlayın, <xref:System.Windows.Forms.Form.IsMdiContainer%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="a84b8-109">Create a form and set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2.  <span data-ttu-id="a84b8-110">Ekleme bir <xref:System.Windows.Forms.MenuStrip> için `Form1` ayarlayıp <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> özelliği <xref:System.Windows.Forms.MenuStrip> için `true`.</span><span class="sxs-lookup"><span data-stu-id="a84b8-110">Add a <xref:System.Windows.Forms.MenuStrip> to `Form1` and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the <xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
3.  <span data-ttu-id="a84b8-111">Bir üst düzey menü öğesine eklemek `Form1` <xref:System.Windows.Forms.MenuStrip> ve kendi <xref:System.Windows.Forms.Control.Text%2A> özelliğini `&File`.</span><span class="sxs-lookup"><span data-stu-id="a84b8-111">Add a top-level menu item to the `Form1`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.Control.Text%2A> property to `&File`.</span></span>  
  
4.  <span data-ttu-id="a84b8-112">Üç alt öğe ekleme `&File` menü öğesi ve kümesi kendi <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliklerine `&Open`, `&Import from`, ve `E&xit`.</span><span class="sxs-lookup"><span data-stu-id="a84b8-112">Add three submenu items to the `&File` menu item and set their <xref:System.Windows.Forms.ToolStripItem.Text%2A> properties to `&Open`, `&Import from`, and `E&xit`.</span></span>  
  
5.  <span data-ttu-id="a84b8-113">İki alt öğe ekleme `&Import from` alt öğesi ve kümesi kendi <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliklerine `&Word` ve `&Excel`.</span><span class="sxs-lookup"><span data-stu-id="a84b8-113">Add two submenu items to the `&Import from` submenu item and set their <xref:System.Windows.Forms.ToolStripItem.Text%2A> properties to `&Word` and `&Excel`.</span></span>  
  
6.  <span data-ttu-id="a84b8-114">Projeye form ekleme, ekleme bir <xref:System.Windows.Forms.MenuStrip> form ve kümesi <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> özelliği `Form2` <xref:System.Windows.Forms.MenuStrip> için `true`.</span><span class="sxs-lookup"><span data-stu-id="a84b8-114">Add a form to the project, add a <xref:System.Windows.Forms.MenuStrip> to the form, and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the `Form2`<xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
7.  <span data-ttu-id="a84b8-115">Bir üst düzey menü öğesine eklemek `Form2` <xref:System.Windows.Forms.MenuStrip> ve kendi <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliğini `&File`.</span><span class="sxs-lookup"><span data-stu-id="a84b8-115">Add a top-level menu item to the `Form2`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to `&File`.</span></span>  
  
8.  <span data-ttu-id="a84b8-116">Alt öğe ekleme `&File` menüsü `Form2` aşağıdaki sırayla: bir <xref:System.Windows.Forms.ToolStripSeparator>, `&Save`, `Save and &Close`ve başka bir <xref:System.Windows.Forms.ToolStripSeparator>.</span><span class="sxs-lookup"><span data-stu-id="a84b8-116">Add submenu items to the `&File` menu of `Form2` in the following order: a <xref:System.Windows.Forms.ToolStripSeparator>, `&Save`, `Save and &Close`, and another <xref:System.Windows.Forms.ToolStripSeparator>.</span></span>  
  
9. <span data-ttu-id="a84b8-117">Ayarlama <xref:System.Windows.Forms.MergeAction> ve <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> özelliklerini `Form2` menü öğeleri aşağıdaki tabloda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="a84b8-117">Set the <xref:System.Windows.Forms.MergeAction> and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties of the `Form2` menu items as shown in the following table.</span></span>  
  
    |<span data-ttu-id="a84b8-118">Form2 menü öğesi</span><span class="sxs-lookup"><span data-stu-id="a84b8-118">Form2 menu item</span></span>|<span data-ttu-id="a84b8-119">MergeAction değeri</span><span class="sxs-lookup"><span data-stu-id="a84b8-119">MergeAction value</span></span>|<span data-ttu-id="a84b8-120">MergeIndex değeri</span><span class="sxs-lookup"><span data-stu-id="a84b8-120">MergeIndex value</span></span>|  
    |---------------------|-----------------------|----------------------|  
    |<span data-ttu-id="a84b8-121">Dosya</span><span class="sxs-lookup"><span data-stu-id="a84b8-121">File</span></span>|<span data-ttu-id="a84b8-122">MatchOnly</span><span class="sxs-lookup"><span data-stu-id="a84b8-122">MatchOnly</span></span>|<span data-ttu-id="a84b8-123">-1</span><span class="sxs-lookup"><span data-stu-id="a84b8-123">-1</span></span>|  
    |<span data-ttu-id="a84b8-124">Ayırıcı</span><span class="sxs-lookup"><span data-stu-id="a84b8-124">Separator</span></span>|<span data-ttu-id="a84b8-125">Ekleme</span><span class="sxs-lookup"><span data-stu-id="a84b8-125">Insert</span></span>|<span data-ttu-id="a84b8-126">2</span><span class="sxs-lookup"><span data-stu-id="a84b8-126">2</span></span>|  
    |<span data-ttu-id="a84b8-127">Kaydet</span><span class="sxs-lookup"><span data-stu-id="a84b8-127">Save</span></span>|<span data-ttu-id="a84b8-128">Ekleme</span><span class="sxs-lookup"><span data-stu-id="a84b8-128">Insert</span></span>|<span data-ttu-id="a84b8-129">3</span><span class="sxs-lookup"><span data-stu-id="a84b8-129">3</span></span>|  
    |<span data-ttu-id="a84b8-130">Kaydet ve Kapat</span><span class="sxs-lookup"><span data-stu-id="a84b8-130">Save and Close</span></span>|<span data-ttu-id="a84b8-131">Ekleme</span><span class="sxs-lookup"><span data-stu-id="a84b8-131">Insert</span></span>|<span data-ttu-id="a84b8-132">4</span><span class="sxs-lookup"><span data-stu-id="a84b8-132">4</span></span>|  
    |<span data-ttu-id="a84b8-133">Ayırıcı</span><span class="sxs-lookup"><span data-stu-id="a84b8-133">Separator</span></span>|<span data-ttu-id="a84b8-134">Ekleme</span><span class="sxs-lookup"><span data-stu-id="a84b8-134">Insert</span></span>|<span data-ttu-id="a84b8-135">5</span><span class="sxs-lookup"><span data-stu-id="a84b8-135">5</span></span>|  
  
10. <span data-ttu-id="a84b8-136">İçin bir olay işleyicisi oluşturun <xref:System.Windows.Forms.Control.Click> olayı `&Open` <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="a84b8-136">Create an event handler for the <xref:System.Windows.Forms.Control.Click> event of the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
11. <span data-ttu-id="a84b8-137">Olay işleyicisinin içerisinde kod oluşturmak ve yeni örneklerini görüntülemek için aşağıdaki kod örneği benzer ekleme `Form2` MDI alt öğeleri olarak `Form1`.</span><span class="sxs-lookup"><span data-stu-id="a84b8-137">Within the event handler, insert code similar to the following code example to create and display new instances of `Form2` as MDI children of `Form1`.</span></span>  
  
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
  
12. <span data-ttu-id="a84b8-138">Kod aşağıdaki kod örneğinde benzer yerleştirin getirin `&Open` <xref:System.Windows.Forms.ToolStripMenuItem> olay işleyicisi kaydetmek için.</span><span class="sxs-lookup"><span data-stu-id="a84b8-138">Place code similar to the following code example in the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> to register the event handler.</span></span>  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a84b8-139">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="a84b8-139">Compiling the Code</span></span>  
 <span data-ttu-id="a84b8-140">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="a84b8-140">This example requires:</span></span>  
  
-   <span data-ttu-id="a84b8-141">İki <xref:System.Windows.Forms.Form> adlarında `Form1` ve `Form2`.</span><span class="sxs-lookup"><span data-stu-id="a84b8-141">Two <xref:System.Windows.Forms.Form> controls named `Form1` and `Form2`.</span></span>  
  
-   <span data-ttu-id="a84b8-142">A <xref:System.Windows.Forms.MenuStrip> denetimi `Form1` adlı `menuStrip1`ve <xref:System.Windows.Forms.MenuStrip> denetimi `Form2` adlı `menuStrip2`.</span><span class="sxs-lookup"><span data-stu-id="a84b8-142">A <xref:System.Windows.Forms.MenuStrip> control on `Form1` named `menuStrip1`, and a <xref:System.Windows.Forms.MenuStrip> control on `Form2` named `menuStrip2`.</span></span>  
  
-   <span data-ttu-id="a84b8-143">Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.</span><span class="sxs-lookup"><span data-stu-id="a84b8-143">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a84b8-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a84b8-144">See Also</span></span>  
 [<span data-ttu-id="a84b8-145">Nasıl yapılır: MDI Üst Formları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a84b8-145">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [<span data-ttu-id="a84b8-146">Nasıl yapılır: MDI Alt Formları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a84b8-146">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [<span data-ttu-id="a84b8-147">MenuStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a84b8-147">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
