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
ms.locfileid: "33540523"
---
# <a name="how-to-remove-a-toolstripmenuitem-from-an-mdi-drop-down-menu-windows-forms"></a><span data-ttu-id="db0fb-102">Nasıl yapılır: Bir MDI Açılan Menüsünden ToolStripMenuItem kaldırma (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="db0fb-102">How to: Remove a ToolStripMenuItem from an MDI Drop-Down Menu (Windows Forms)</span></span>
<span data-ttu-id="db0fb-103">Bazı uygulamalarda, birden çok belge arabirimi (MDI) alt pencere türü MDI üst penceresinden farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="db0fb-103">In some applications, the kind of a multiple-document interface (MDI) child window can be different from the MDI parent window.</span></span> <span data-ttu-id="db0fb-104">Örneğin, elektronik tablo MDI olabilir ve MDI alt bir grafik olabilir.</span><span class="sxs-lookup"><span data-stu-id="db0fb-104">For example, the MDI parent might be a spreadsheet, and the MDI child might be a chart.</span></span> <span data-ttu-id="db0fb-105">Bu durumda, farklı türlerde MDI alt pencereleri etkinleştirilmiş olarak MDI üst öğenin menüsünün içeriğini MDI alt menü içeriğini güncelleştirmek istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="db0fb-105">In that case, you want to update the contents of the MDI parent's menu with the contents of the MDI child's menu as MDI child windows of different kinds are activated.</span></span>  
  
 <span data-ttu-id="db0fb-106">Aşağıdaki yordam kullanır <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, ve <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> özellikleri menü öğesi MDI üst menü açılan bölümünden kaldırın.</span><span class="sxs-lookup"><span data-stu-id="db0fb-106">The following procedure uses the <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties to remove a menu item from the drop-down part of the MDI parent menu.</span></span> <span data-ttu-id="db0fb-107">MDI alt pencereyi kaldırılan menü öğelerini MDI üst menüsüne geri yükler.</span><span class="sxs-lookup"><span data-stu-id="db0fb-107">Closing the MDI child window restores the removed menu items to the MDI parent menu.</span></span>  
  
### <a name="to-remove-a-menustrip-from-an-mdi-drop-down-menu"></a><span data-ttu-id="db0fb-108">MenuStrip bir MDI açılan menüsünden kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="db0fb-108">To remove a MenuStrip from an MDI drop-down menu</span></span>  
  
1.  <span data-ttu-id="db0fb-109">Bir form oluşturun ve ayarlayın, <xref:System.Windows.Forms.Form.IsMdiContainer%2A> özelliğine `true`.</span><span class="sxs-lookup"><span data-stu-id="db0fb-109">Create a form and set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2.  <span data-ttu-id="db0fb-110">Ekleme bir <xref:System.Windows.Forms.MenuStrip> için `Form1` ve <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> özelliği <xref:System.Windows.Forms.MenuStrip> için `true`.</span><span class="sxs-lookup"><span data-stu-id="db0fb-110">Add a <xref:System.Windows.Forms.MenuStrip> to `Form1` and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the <xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
3.  <span data-ttu-id="db0fb-111">Bir üst düzey menü öğesi ekleme `Form1` <xref:System.Windows.Forms.MenuStrip> ve kendi <xref:System.Windows.Forms.Control.Text%2A> özelliğine `&File`.</span><span class="sxs-lookup"><span data-stu-id="db0fb-111">Add a top-level menu item to the `Form1`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.Control.Text%2A> property to `&File`.</span></span>  
  
4.  <span data-ttu-id="db0fb-112">Üç alt öğeleri Ekle `&File` menü öğesi ve kümesi kendi <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliklerine `&Open`, `&Import from`, ve `E&xit`.</span><span class="sxs-lookup"><span data-stu-id="db0fb-112">Add three submenu items to the `&File` menu item and set their <xref:System.Windows.Forms.ToolStripItem.Text%2A> properties to `&Open`, `&Import from`, and `E&xit`.</span></span>  
  
5.  <span data-ttu-id="db0fb-113">İki alt öğe ekleme `&Import from` alt öğe ve kümesi kendi <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliklerine `&Word` ve `&Excel`.</span><span class="sxs-lookup"><span data-stu-id="db0fb-113">Add two submenu items to the `&Import from` submenu item and set their <xref:System.Windows.Forms.ToolStripItem.Text%2A> properties to `&Word` and `&Excel`.</span></span>  
  
6.  <span data-ttu-id="db0fb-114">Projeye form ekleme, ekleme bir <xref:System.Windows.Forms.MenuStrip> form ve kümesi <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> özelliği `Form2` <xref:System.Windows.Forms.MenuStrip> için `true`.</span><span class="sxs-lookup"><span data-stu-id="db0fb-114">Add a form to the project, add a <xref:System.Windows.Forms.MenuStrip> to the form, and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the `Form2`<xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
7.  <span data-ttu-id="db0fb-115">Bir üst düzey menü öğesi ekleme `Form2` <xref:System.Windows.Forms.MenuStrip> ve kendi <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliğine `&File`.</span><span class="sxs-lookup"><span data-stu-id="db0fb-115">Add a top-level menu item to the `Form2`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to `&File`.</span></span>  
  
8.  <span data-ttu-id="db0fb-116">Ekleme bir `&Import from` alt öğeye `&File` menüsünü `Form2`ve ekleyin bir `&Word` alt öğeye `&File` menüsü.</span><span class="sxs-lookup"><span data-stu-id="db0fb-116">Add an `&Import from` submenu item to the `&File` menu of `Form2`, and add an `&Word` submenu item to the `&File` menu.</span></span>  
  
9. <span data-ttu-id="db0fb-117">Ayarlama <xref:System.Windows.Forms.MergeAction> ve <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> özelliklerini `Form2` menü öğeleri aşağıdaki tabloda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="db0fb-117">Set the <xref:System.Windows.Forms.MergeAction> and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties of the `Form2` menu items as shown in the following table.</span></span>  
  
    |<span data-ttu-id="db0fb-118">Form2 menü öğesi</span><span class="sxs-lookup"><span data-stu-id="db0fb-118">Form2 menu item</span></span>|<span data-ttu-id="db0fb-119">MergeAction değeri</span><span class="sxs-lookup"><span data-stu-id="db0fb-119">MergeAction value</span></span>|<span data-ttu-id="db0fb-120">MergeIndex değeri</span><span class="sxs-lookup"><span data-stu-id="db0fb-120">MergeIndex value</span></span>|  
    |---------------------|-----------------------|----------------------|  
    |<span data-ttu-id="db0fb-121">Dosya</span><span class="sxs-lookup"><span data-stu-id="db0fb-121">File</span></span>|<span data-ttu-id="db0fb-122">MatchOnly</span><span class="sxs-lookup"><span data-stu-id="db0fb-122">MatchOnly</span></span>|<span data-ttu-id="db0fb-123">-1</span><span class="sxs-lookup"><span data-stu-id="db0fb-123">-1</span></span>|  
    |<span data-ttu-id="db0fb-124">İçeri aktarın</span><span class="sxs-lookup"><span data-stu-id="db0fb-124">Import from</span></span>|<span data-ttu-id="db0fb-125">MatchOnly</span><span class="sxs-lookup"><span data-stu-id="db0fb-125">MatchOnly</span></span>|<span data-ttu-id="db0fb-126">-1</span><span class="sxs-lookup"><span data-stu-id="db0fb-126">-1</span></span>|  
    |<span data-ttu-id="db0fb-127">Word</span><span class="sxs-lookup"><span data-stu-id="db0fb-127">Word</span></span>|<span data-ttu-id="db0fb-128">Kaldır</span><span class="sxs-lookup"><span data-stu-id="db0fb-128">Remove</span></span>|<span data-ttu-id="db0fb-129">-1</span><span class="sxs-lookup"><span data-stu-id="db0fb-129">-1</span></span>|  
  
10. <span data-ttu-id="db0fb-130">İçinde `Form1`, bir olay işleyicisi oluşturun <xref:System.Windows.Forms.Control.Click> olayı `&Open` <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="db0fb-130">In `Form1`, create an event handler for the <xref:System.Windows.Forms.Control.Click> event of the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
11. <span data-ttu-id="db0fb-131">Olay işleyicisi içinde oluşturmak ve yeni örneklerini görüntülemek için aşağıdaki kod örneğinde benzer bir kod Ekle `Form2` MDI alt öğeleri olarak `Form1`:</span><span class="sxs-lookup"><span data-stu-id="db0fb-131">Within the event handler, insert code similar to the following code example to create and display new instances of `Form2` as MDI children of `Form1`:</span></span>  
  
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
  
12. <span data-ttu-id="db0fb-132">Kod aşağıdaki kod örneğinde benzer yerleştirin getirin `&Open` <xref:System.Windows.Forms.ToolStripMenuItem> olay işleyicisi kaydetmek için.</span><span class="sxs-lookup"><span data-stu-id="db0fb-132">Place code similar to the following code example in the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> to register the event handler.</span></span>  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new _  
    System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="db0fb-133">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="db0fb-133">Compiling the Code</span></span>  
 <span data-ttu-id="db0fb-134">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="db0fb-134">This example requires:</span></span>  
  
-   <span data-ttu-id="db0fb-135">İki <xref:System.Windows.Forms.Form> adlı denetimleri `Form1` ve `Form2`.</span><span class="sxs-lookup"><span data-stu-id="db0fb-135">Two <xref:System.Windows.Forms.Form> controls named `Form1` and `Form2`.</span></span>  
  
-   <span data-ttu-id="db0fb-136">A <xref:System.Windows.Forms.MenuStrip> denetiminin `Form1` adlı `menuStrip1`ve bir <xref:System.Windows.Forms.MenuStrip> denetiminin `Form2` adlı `menuStrip2`.</span><span class="sxs-lookup"><span data-stu-id="db0fb-136">A <xref:System.Windows.Forms.MenuStrip> control on `Form1` named `menuStrip1`, and a <xref:System.Windows.Forms.MenuStrip> control on `Form2` named `menuStrip2`.</span></span>  
  
-   <span data-ttu-id="db0fb-137">Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.</span><span class="sxs-lookup"><span data-stu-id="db0fb-137">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db0fb-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="db0fb-138">See Also</span></span>  
 [<span data-ttu-id="db0fb-139">Nasıl yapılır: MDI Üst Formları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="db0fb-139">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [<span data-ttu-id="db0fb-140">Nasıl yapılır: MDI Alt Formları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="db0fb-140">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [<span data-ttu-id="db0fb-141">MenuStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="db0fb-141">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
