---
title: 'Nasıl yapılır: (Windows Forms) MDI üst penceresine MenuStrip ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip control [Windows Forms], merging
- MenuStrip control [Windows Forms], appending
- MDI [Windows Forms], merging menu items
ms.assetid: ab70c936-b452-4653-b417-17be57bb795b
ms.openlocfilehash: a335531b090983de4e2b3daccc9f956930cbad6e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011035"
---
# <a name="how-to-append-a-menustrip-to-an-mdi-parent-window-windows-forms"></a><span data-ttu-id="caa1e-102">Nasıl yapılır: (Windows Forms) MDI üst penceresine MenuStrip ekleme</span><span class="sxs-lookup"><span data-stu-id="caa1e-102">How to: Append a MenuStrip to an MDI Parent Window (Windows Forms)</span></span>
<span data-ttu-id="caa1e-103">Bazı uygulamalarda, bir Çoklu belge arabirimi (MDI) alt penceresi türünü MDI ana penceresinde farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="caa1e-103">In some applications, the kind of a multiple-document interface (MDI) child window can be different from the MDI parent window.</span></span> <span data-ttu-id="caa1e-104">Örneğin, bir elektronik tablo MDI olabilir ve MDI alt bir grafik olabilir.</span><span class="sxs-lookup"><span data-stu-id="caa1e-104">For example, the MDI parent might be a spreadsheet, and the MDI child might be a chart.</span></span> <span data-ttu-id="caa1e-105">Bu durumda, farklı türlerde MDI alt pencereleri etkin olarak MDI üst menü içeriğini MDI alt menü içeriğini güncelleştirmek istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="caa1e-105">In that case, you want to update the contents of the MDI parent's menu with the contents of the MDI child's menu as MDI child windows of different kinds are activated.</span></span>  
  
 <span data-ttu-id="caa1e-106">Aşağıdaki yordam kullanır <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, ve <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> MDI üst menüye MDI alt menüsünü eklenecek özellikleri.</span><span class="sxs-lookup"><span data-stu-id="caa1e-106">The following procedure uses the <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties to append the MDI child menu to the MDI parent menu.</span></span> <span data-ttu-id="caa1e-107">MDI alt penceresini kapatarak eklenmiş menü MDI üst kaldırır.</span><span class="sxs-lookup"><span data-stu-id="caa1e-107">Closing the MDI child window removes the appended menu from the MDI parent.</span></span>  
  
 <span data-ttu-id="caa1e-108">Ayrıca bkz: [Çok Belgeli Arabirim (MDI) uygulamaları](../advanced/multiple-document-interface-mdi-applications.md).</span><span class="sxs-lookup"><span data-stu-id="caa1e-108">Also see [Multiple-Document Interface (MDI) Applications](../advanced/multiple-document-interface-mdi-applications.md).</span></span>  
  
### <a name="to-append-a-menu-item-to-an-mdi-parent"></a><span data-ttu-id="caa1e-109">Bir MDI üst menü öğesi eklemek için</span><span class="sxs-lookup"><span data-stu-id="caa1e-109">To append a menu item to an MDI parent</span></span>  
  
1. <span data-ttu-id="caa1e-110">Bir form oluşturun ve ayarlayın, <xref:System.Windows.Forms.Form.IsMdiContainer%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="caa1e-110">Create a form and set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2. <span data-ttu-id="caa1e-111">Ekleme bir <xref:System.Windows.Forms.MenuStrip> için `Form1` ayarlayıp <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> özelliği <xref:System.Windows.Forms.MenuStrip> için `true`.</span><span class="sxs-lookup"><span data-stu-id="caa1e-111">Add a <xref:System.Windows.Forms.MenuStrip> to `Form1` and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the <xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
3. <span data-ttu-id="caa1e-112">Ayarlama <xref:System.Windows.Forms.ToolStripItem.Visible%2A> özelliği `Form1` <xref:System.Windows.Forms.MenuStrip> için `false`.</span><span class="sxs-lookup"><span data-stu-id="caa1e-112">Set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property of the `Form1`<xref:System.Windows.Forms.MenuStrip> to `false`.</span></span>  
  
4. <span data-ttu-id="caa1e-113">Bir üst düzey menü öğesine eklemek `Form1` <xref:System.Windows.Forms.MenuStrip> ve kendi <xref:System.Windows.Forms.Control.Text%2A> özelliğini `&File`.</span><span class="sxs-lookup"><span data-stu-id="caa1e-113">Add a top-level menu item to the `Form1`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.Control.Text%2A> property to `&File`.</span></span>  
  
5. <span data-ttu-id="caa1e-114">Bir alt öğe ekleme `&File` menü öğesi ve kümesi kendi <xref:System.Windows.Forms.Form.Text%2A> özelliğini `&Open`.</span><span class="sxs-lookup"><span data-stu-id="caa1e-114">Add a submenu item to the `&File` menu item and set its <xref:System.Windows.Forms.Form.Text%2A> property to `&Open`.</span></span>  
  
6. <span data-ttu-id="caa1e-115">Projeye form ekleme, ekleme bir <xref:System.Windows.Forms.MenuStrip> form ve kümesi <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> özelliği `Form2` <xref:System.Windows.Forms.MenuStrip> için `true`.</span><span class="sxs-lookup"><span data-stu-id="caa1e-115">Add a form to the project, add a <xref:System.Windows.Forms.MenuStrip> to the form, and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the `Form2`<xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
7. <span data-ttu-id="caa1e-116">Bir üst düzey menü öğesine eklemek `Form2` <xref:System.Windows.Forms.MenuStrip> ve kendi <xref:System.Windows.Forms.Form.Text%2A> özelliğini `&Special`.</span><span class="sxs-lookup"><span data-stu-id="caa1e-116">Add a top-level menu item to the `Form2`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.Form.Text%2A> property to `&Special`.</span></span>  
  
8. <span data-ttu-id="caa1e-117">İki alt öğe ekleme `&Special` menü öğesi ve kümesi kendi <xref:System.Windows.Forms.Form.Text%2A> özelliklerine `Command&1` ve `Command&2`sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="caa1e-117">Add two submenu items to the `&Special` menu item and set their <xref:System.Windows.Forms.Form.Text%2A> properties to `Command&1` and `Command&2`, respectively.</span></span>  
  
9. <span data-ttu-id="caa1e-118">Ayarlama <xref:System.Windows.Forms.MergeAction> özelliği `&Special`, `Command&1`, ve `Command&2` menü öğeleri için <xref:System.Windows.Forms.MergeAction.Append>.</span><span class="sxs-lookup"><span data-stu-id="caa1e-118">Set the <xref:System.Windows.Forms.MergeAction> property of the `&Special`, `Command&1`, and `Command&2` menu items to <xref:System.Windows.Forms.MergeAction.Append>.</span></span>  
  
10. <span data-ttu-id="caa1e-119">İçin bir olay işleyicisi oluşturun <xref:System.Windows.Forms.Control.Click> olayı `&New` <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="caa1e-119">Create an event handler for the <xref:System.Windows.Forms.Control.Click> event of the `&New`<xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
11. <span data-ttu-id="caa1e-120">Olay işleyicisinin içerisinde kod oluşturmak ve yeni örneklerini görüntülemek için aşağıdaki kod örneği benzer ekleme `Form2` MDI alt öğeleri olarak `Form1`.</span><span class="sxs-lookup"><span data-stu-id="caa1e-120">Within the event handler, insert code similar to the following code example to create and display new instances of `Form2` as MDI children of `Form1`.</span></span>  
  
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
  
12. <span data-ttu-id="caa1e-121">Kod aşağıdaki kod örneğinde benzer yerleştirin getirin `&Open` <xref:System.Windows.Forms.ToolStripMenuItem> olay işleyicisi kaydetmek için.</span><span class="sxs-lookup"><span data-stu-id="caa1e-121">Place code similar to the following code example in the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> to register the event handler.</span></span>  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="caa1e-122">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="caa1e-122">Compiling the Code</span></span>  
 <span data-ttu-id="caa1e-123">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="caa1e-123">This example requires:</span></span>  
  
- <span data-ttu-id="caa1e-124">İki <xref:System.Windows.Forms.Form> adlarında `Form1` ve `Form2`.</span><span class="sxs-lookup"><span data-stu-id="caa1e-124">Two <xref:System.Windows.Forms.Form> controls named `Form1` and `Form2`.</span></span>  
  
- <span data-ttu-id="caa1e-125">A <xref:System.Windows.Forms.MenuStrip> denetimi `Form1` adlı `menuStrip1`ve <xref:System.Windows.Forms.MenuStrip> denetimi `Form2` adlı `menuStrip2`.</span><span class="sxs-lookup"><span data-stu-id="caa1e-125">A <xref:System.Windows.Forms.MenuStrip> control on `Form1` named `menuStrip1`, and a <xref:System.Windows.Forms.MenuStrip> control on `Form2` named `menuStrip2`.</span></span>  
  
- <span data-ttu-id="caa1e-126">Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.</span><span class="sxs-lookup"><span data-stu-id="caa1e-126">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>
