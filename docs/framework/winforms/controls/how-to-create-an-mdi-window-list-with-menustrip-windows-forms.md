---
title: 'Nasıl yapılır: MenuStrip ile MDI Pencere Listesi Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MDI [Windows Forms], creating window lists
- MenuStrip control [Windows Forms], creating window lists
ms.assetid: 04fb414b-811f-4a83-aab6-b4a24646dec5
ms.openlocfilehash: f013c3df2ab5783a22fe2c34402dc53a328cafa2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731014"
---
# <a name="how-to-create-an-mdi-window-list-with-menustrip-windows-forms"></a><span data-ttu-id="cce1d-102">Nasıl yapılır: MenuStrip (Windows Forms) ile MDI Pencere Listesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="cce1d-102">How to: Create an MDI Window List with MenuStrip (Windows Forms)</span></span>
<span data-ttu-id="cce1d-103">Birden çok belge arabirimi (MDI) kullanarak, aynı anda birden fazla belge açan uygulamalar oluşturun ve içeriği bir belgeden diğerine kopyalayabilir ve yapıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cce1d-103">Use the multiple-document interface (MDI) to create applications that can open several documents at the same time and copy and paste content from one document to the other.</span></span>  
  
 <span data-ttu-id="cce1d-104">Bu yordamda, üst öğenin pencere menüsündeki tüm etkin alt formların listesini nasıl oluşturacağınız gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="cce1d-104">This procedure shows you how to create a list of all the active child forms on the parent's Window menu.</span></span>  
  
### <a name="to-create-an-mdi-window-list-on-a-menustrip"></a><span data-ttu-id="cce1d-105">MenuStrip 'te MDI pencere listesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="cce1d-105">To create an MDI Window list on a MenuStrip</span></span>  
  
1. <span data-ttu-id="cce1d-106">Bir form oluşturun ve <xref:System.Windows.Forms.Form.IsMdiContainer%2A> özelliğini `true`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="cce1d-106">Create a form and set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2. <span data-ttu-id="cce1d-107">Forma <xref:System.Windows.Forms.MenuStrip> ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cce1d-107">Add a <xref:System.Windows.Forms.MenuStrip> to the form.</span></span>  
  
3. <span data-ttu-id="cce1d-108"><xref:System.Windows.Forms.MenuStrip> iki üst düzey menü öğesi ekleyin ve <xref:System.Windows.Forms.Control.Text%2A> özelliklerini `&File` ve `&Window`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="cce1d-108">Add two top-level menu items to the <xref:System.Windows.Forms.MenuStrip> and set their <xref:System.Windows.Forms.Control.Text%2A> properties to `&File` and `&Window`.</span></span>  
  
4. <span data-ttu-id="cce1d-109">`&File` menü öğesine bir alt menü öğesi ekleyin ve <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliğini `&Open`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="cce1d-109">Add a submenu item to the `&File` menu item and set its <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to `&Open`.</span></span>  
  
5. <span data-ttu-id="cce1d-110"><xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> özelliğini `&Window`<xref:System.Windows.Forms.ToolStripMenuItem>olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="cce1d-110">Set the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property of the <xref:System.Windows.Forms.MenuStrip> to the `&Window`<xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
6. <span data-ttu-id="cce1d-111">Projeye bir form ekleyin ve istediğiniz denetimi, başka bir <xref:System.Windows.Forms.MenuStrip>gibi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cce1d-111">Add a form to the project and add the control you want to it, such as another <xref:System.Windows.Forms.MenuStrip>.</span></span>  
  
7. <span data-ttu-id="cce1d-112">`&New`<xref:System.Windows.Forms.ToolStripMenuItem><xref:System.Windows.Forms.Control.Click> olayı için bir olay işleyicisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cce1d-112">Create an event handler for the <xref:System.Windows.Forms.Control.Click> event of the `&New`<xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
8. <span data-ttu-id="cce1d-113">Olay işleyicisi içinde, `Form1`MDI alt öğeleri olarak `Form2` yeni örneklerini oluşturmak ve göstermek için aşağıdakine benzer bir kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cce1d-113">Within the event handler, insert code similar to the following to create and display new instances of `Form2` as MDI children of `Form1`.</span></span>  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(ByVal sender As _  
    System.Object, ByVal e As System.EventArgs) Handles _  
    openToolStripMenuItem.Click  
        Dim NewMDIChild As New Form2()  
        'Set the parent form of the child window.  
            NewMDIChild.MdiParent = Me  
        'Display the new form.  
            NewMDIChild.Show()  
    End Sub  
    ```  
  
    ```csharp  
    private void newToolStripMenuItem_Click(object sender, EventArgs e)  
    {  
        Form2 newMDIChild = new Form2();  
        // Set the parent form of the child window.  
            newMDIChild.MdiParent = this;  
        // Display the new form.  
            newMDIChild.Show();  
    }  
    ```  
  
9. <span data-ttu-id="cce1d-114">Olay işleyicisini kaydetmek için `&New`<xref:System.Windows.Forms.ToolStripMenuItem> gibi bir kod girin.</span><span class="sxs-lookup"><span data-stu-id="cce1d-114">Place code like the following in the `&New`<xref:System.Windows.Forms.ToolStripMenuItem> to register the event handler.</span></span>  
  
    ```vb  
    Private Sub newToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles newToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.newToolStripMenuItem.Click += new System.EventHandler(this.newToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cce1d-115">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="cce1d-115">Compiling the Code</span></span>  
 <span data-ttu-id="cce1d-116">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="cce1d-116">This example requires:</span></span>  
  
- <span data-ttu-id="cce1d-117">`Form1` ve `Form2`adlı iki <xref:System.Windows.Forms.Form> denetimi.</span><span class="sxs-lookup"><span data-stu-id="cce1d-117">Two <xref:System.Windows.Forms.Form> controls named `Form1` and `Form2`.</span></span>  
  
- <span data-ttu-id="cce1d-118">`menuStrip1`adlı `Form1` ve `Form2` adlı `menuStrip2`<xref:System.Windows.Forms.MenuStrip> bir denetim <xref:System.Windows.Forms.MenuStrip> denetimi.</span><span class="sxs-lookup"><span data-stu-id="cce1d-118">A <xref:System.Windows.Forms.MenuStrip> control on `Form1` named `menuStrip1`, and a <xref:System.Windows.Forms.MenuStrip> control on `Form2` named `menuStrip2`.</span></span>  
  
- <span data-ttu-id="cce1d-119"><xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="cce1d-119">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cce1d-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cce1d-120">See also</span></span>

- [<span data-ttu-id="cce1d-121">Nasıl yapılır: MDI Üst Formları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="cce1d-121">How to: Create MDI Parent Forms</span></span>](../advanced/how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="cce1d-122">Nasıl yapılır: MDI Alt Formları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="cce1d-122">How to: Create MDI Child Forms</span></span>](../advanced/how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="cce1d-123">MenuStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="cce1d-123">MenuStrip Control</span></span>](menustrip-control-windows-forms.md)
