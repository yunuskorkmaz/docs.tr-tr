---
title: 'Nasıl yapılır: MDI Üst Penceresine MenuStrip Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip control [Windows Forms], merging
- MenuStrip control [Windows Forms], appending
- MDI [Windows Forms], merging menu items
ms.assetid: ab70c936-b452-4653-b417-17be57bb795b
ms.openlocfilehash: 06e5c9daab8b7eb72024fff27d661c0eb3bf84c6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747161"
---
# <a name="how-to-append-a-menustrip-to-an-mdi-parent-window-windows-forms"></a><span data-ttu-id="d3d77-102">Nasıl yapılır: MDI Üst Penceresine MenuStrip Ekleme (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="d3d77-102">How to: Append a MenuStrip to an MDI Parent Window (Windows Forms)</span></span>
<span data-ttu-id="d3d77-103">Bazı uygulamalarda, bir çoklu belge arabirimi (MDI) alt penceresinin türü MDI ana penceresinden farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="d3d77-103">In some applications, the kind of a multiple-document interface (MDI) child window can be different from the MDI parent window.</span></span> <span data-ttu-id="d3d77-104">Örneğin, MDI parent bir elektronik tablo olabilir ve MDI alt öğesi bir grafik olabilir.</span><span class="sxs-lookup"><span data-stu-id="d3d77-104">For example, the MDI parent might be a spreadsheet, and the MDI child might be a chart.</span></span> <span data-ttu-id="d3d77-105">Bu durumda, farklı türlerdeki MDI alt pencereleri etkinleştirildiğinden MDI üst öğesinin menüsünün içeriğini MDI alt menüsünün içeriğiyle güncelleştirmek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="d3d77-105">In that case, you want to update the contents of the MDI parent's menu with the contents of the MDI child's menu as MDI child windows of different kinds are activated.</span></span>  
  
 <span data-ttu-id="d3d77-106">Aşağıdaki yordam MDI alt menüsünü MDI parent menüsüne eklemek için <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>ve <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> özelliklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d3d77-106">The following procedure uses the <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties to append the MDI child menu to the MDI parent menu.</span></span> <span data-ttu-id="d3d77-107">MDI alt penceresini kapatmak, eklenen menüyü MDI üst öğesinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d3d77-107">Closing the MDI child window removes the appended menu from the MDI parent.</span></span>  
  
 <span data-ttu-id="d3d77-108">Ayrıca bkz. [birden çok belgeli arabirim (MDI) uygulamaları](../advanced/multiple-document-interface-mdi-applications.md).</span><span class="sxs-lookup"><span data-stu-id="d3d77-108">Also see [Multiple-Document Interface (MDI) Applications](../advanced/multiple-document-interface-mdi-applications.md).</span></span>  
  
### <a name="to-append-a-menu-item-to-an-mdi-parent"></a><span data-ttu-id="d3d77-109">Bir MDI üst öğesine bir menü öğesi eklemek için</span><span class="sxs-lookup"><span data-stu-id="d3d77-109">To append a menu item to an MDI parent</span></span>  
  
1. <span data-ttu-id="d3d77-110">Bir form oluşturun ve <xref:System.Windows.Forms.Form.IsMdiContainer%2A> özelliğini `true`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d3d77-110">Create a form and set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2. <span data-ttu-id="d3d77-111">`Form1` <xref:System.Windows.Forms.MenuStrip> ekleyin ve <xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> özelliğini `true`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d3d77-111">Add a <xref:System.Windows.Forms.MenuStrip> to `Form1` and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the <xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
3. <span data-ttu-id="d3d77-112">`Form1`<xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.ToolStripItem.Visible%2A> özelliğini `false`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d3d77-112">Set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property of the `Form1`<xref:System.Windows.Forms.MenuStrip> to `false`.</span></span>  
  
4. <span data-ttu-id="d3d77-113">`Form1`<xref:System.Windows.Forms.MenuStrip> en üst düzey menü öğesini ekleyin ve <xref:System.Windows.Forms.Control.Text%2A> özelliğini `&File`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d3d77-113">Add a top-level menu item to the `Form1`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.Control.Text%2A> property to `&File`.</span></span>  
  
5. <span data-ttu-id="d3d77-114">`&File` menü öğesine bir alt menü öğesi ekleyin ve <xref:System.Windows.Forms.Form.Text%2A> özelliğini `&Open`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d3d77-114">Add a submenu item to the `&File` menu item and set its <xref:System.Windows.Forms.Form.Text%2A> property to `&Open`.</span></span>  
  
6. <span data-ttu-id="d3d77-115">Projeye bir form ekleyin, forma <xref:System.Windows.Forms.MenuStrip> ekleyin ve `Form2`<xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> özelliğini `true`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d3d77-115">Add a form to the project, add a <xref:System.Windows.Forms.MenuStrip> to the form, and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the `Form2`<xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
7. <span data-ttu-id="d3d77-116">`Form2`<xref:System.Windows.Forms.MenuStrip> en üst düzey menü öğesini ekleyin ve <xref:System.Windows.Forms.Form.Text%2A> özelliğini `&Special`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d3d77-116">Add a top-level menu item to the `Form2`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.Form.Text%2A> property to `&Special`.</span></span>  
  
8. <span data-ttu-id="d3d77-117">`&Special` menü öğesine iki alt menü öğesi ekleyin ve <xref:System.Windows.Forms.Form.Text%2A> özelliklerini sırasıyla `Command&1` ve `Command&2`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d3d77-117">Add two submenu items to the `&Special` menu item and set their <xref:System.Windows.Forms.Form.Text%2A> properties to `Command&1` and `Command&2`, respectively.</span></span>  
  
9. <span data-ttu-id="d3d77-118">`&Special`, `Command&1`ve `Command&2` menü öğelerinin <xref:System.Windows.Forms.MergeAction> özelliğini <xref:System.Windows.Forms.MergeAction.Append>olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d3d77-118">Set the <xref:System.Windows.Forms.MergeAction> property of the `&Special`, `Command&1`, and `Command&2` menu items to <xref:System.Windows.Forms.MergeAction.Append>.</span></span>  
  
10. <span data-ttu-id="d3d77-119">`&Open` <xref:System.Windows.Forms.ToolStripMenuItem><xref:System.Windows.Forms.Control.Click> olayı için bir olay işleyicisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d3d77-119">Create an event handler for the <xref:System.Windows.Forms.Control.Click> event of the `&Open` <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
11. <span data-ttu-id="d3d77-120">Olay işleyicisi içinde, `Form1`MDI alt öğeleri olarak `Form2` yeni örneklerini oluşturmak ve göstermek için aşağıdaki kod örneğine benzer bir kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d3d77-120">Within the event handler, insert code similar to the following code example to create and display new instances of `Form2` as MDI children of `Form1`.</span></span>  
  
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
  
12. <span data-ttu-id="d3d77-121">Olay işleyicisini kaydetmek için `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> aşağıdaki kod örneğine benzer bir kod koyun.</span><span class="sxs-lookup"><span data-stu-id="d3d77-121">Place code similar to the following code example in the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> to register the event handler.</span></span>  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d3d77-122">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="d3d77-122">Compiling the Code</span></span>  
 <span data-ttu-id="d3d77-123">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="d3d77-123">This example requires:</span></span>  
  
- <span data-ttu-id="d3d77-124">`Form1` ve `Form2`adlı iki <xref:System.Windows.Forms.Form> denetimi.</span><span class="sxs-lookup"><span data-stu-id="d3d77-124">Two <xref:System.Windows.Forms.Form> controls named `Form1` and `Form2`.</span></span>  
  
- <span data-ttu-id="d3d77-125">`menuStrip1`adlı `Form1` ve `Form2` adlı `menuStrip2`<xref:System.Windows.Forms.MenuStrip> bir denetim <xref:System.Windows.Forms.MenuStrip> denetimi.</span><span class="sxs-lookup"><span data-stu-id="d3d77-125">A <xref:System.Windows.Forms.MenuStrip> control on `Form1` named `menuStrip1`, and a <xref:System.Windows.Forms.MenuStrip> control on `Form2` named `menuStrip2`.</span></span>  
  
- <span data-ttu-id="d3d77-126"><xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="d3d77-126">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>
