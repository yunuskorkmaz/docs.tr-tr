---
title: 'Nasıl yapılır: (Windows Forms) MenuStrip ile MDI pencere listesi oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MDI [Windows Forms], creating window lists
- MenuStrip control [Windows Forms], creating window lists
ms.assetid: 04fb414b-811f-4a83-aab6-b4a24646dec5
ms.openlocfilehash: 00f35fe872fc5702595108646e2605ed419823f8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54585321"
---
# <a name="how-to-create-an-mdi-window-list-with-menustrip-windows-forms"></a><span data-ttu-id="c684c-102">Nasıl yapılır: (Windows Forms) MenuStrip ile MDI pencere listesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="c684c-102">How to: Create an MDI Window List with MenuStrip (Windows Forms)</span></span>
<span data-ttu-id="c684c-103">Çok Belgeli Arabirim (MDI), aynı zaman ve kopyalama sırasında birkaç belge açın ve içeriğini bir belgeden diğerine yapıştırma uygulamalar oluşturmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="c684c-103">Use the multiple-document interface (MDI) to create applications that can open several documents at the same time and copy and paste content from one document to the other.</span></span>  
  
 <span data-ttu-id="c684c-104">Bu yordam, üst öğenin Pencere menüsünden tüm etkin alt formların listesini oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c684c-104">This procedure shows you how to create a list of all the active child forms on the parent's Window menu.</span></span>  
  
### <a name="to-create-an-mdi-window-list-on-a-menustrip"></a><span data-ttu-id="c684c-105">MenuStrip üzerinde bir MDI pencere listesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="c684c-105">To create an MDI Window list on a MenuStrip</span></span>  
  
1.  <span data-ttu-id="c684c-106">Bir form oluşturun ve ayarlayın, <xref:System.Windows.Forms.Form.IsMdiContainer%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="c684c-106">Create a form and set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2.  <span data-ttu-id="c684c-107">Ekleme bir <xref:System.Windows.Forms.MenuStrip> form.</span><span class="sxs-lookup"><span data-stu-id="c684c-107">Add a <xref:System.Windows.Forms.MenuStrip> to the form.</span></span>  
  
3.  <span data-ttu-id="c684c-108">İki üst düzey menü öğeleri ekleme <xref:System.Windows.Forms.MenuStrip> ve bunların <xref:System.Windows.Forms.Control.Text%2A> özelliklerine `&File` ve `&Window`.</span><span class="sxs-lookup"><span data-stu-id="c684c-108">Add two top-level menu items to the <xref:System.Windows.Forms.MenuStrip> and set their <xref:System.Windows.Forms.Control.Text%2A> properties to `&File` and `&Window`.</span></span>  
  
4.  <span data-ttu-id="c684c-109">Bir alt öğe ekleme `&File` menü öğesi ve kümesi kendi <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliğini `&Open`.</span><span class="sxs-lookup"><span data-stu-id="c684c-109">Add a submenu item to the `&File` menu item and set its <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to `&Open`.</span></span>  
  
5.  <span data-ttu-id="c684c-110">Ayarlama <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> özelliği <xref:System.Windows.Forms.MenuStrip> için `&Window` <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="c684c-110">Set the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property of the <xref:System.Windows.Forms.MenuStrip> to the `&Window`<xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
6.  <span data-ttu-id="c684c-111">Projeye form ekleme ve istediğiniz denetim, başka bir gibi <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="c684c-111">Add a form to the project and add the control you want to it, such as another <xref:System.Windows.Forms.MenuStrip>.</span></span>  
  
7.  <span data-ttu-id="c684c-112">İçin bir olay işleyicisi oluşturun <xref:System.Windows.Forms.Control.Click> olayı `&New` <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="c684c-112">Create an event handler for the <xref:System.Windows.Forms.Control.Click> event of the `&New`<xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
8.  <span data-ttu-id="c684c-113">Olay işleyicisinin içerisinde oluşturmak ve yeni örneklerini görüntülemek için aşağıdaki için benzer bir kod ekleme `Form2` MDI alt öğeleri olarak `Form1`.</span><span class="sxs-lookup"><span data-stu-id="c684c-113">Within the event handler, insert code similar to the following to create and display new instances of `Form2` as MDI children of `Form1`.</span></span>  
  
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
  
9. <span data-ttu-id="c684c-114">Kod aşağıdaki gibi yerleştirmek `&New` <xref:System.Windows.Forms.ToolStripMenuItem> olay işleyicisi kaydetmek için.</span><span class="sxs-lookup"><span data-stu-id="c684c-114">Place code like the following in the `&New`<xref:System.Windows.Forms.ToolStripMenuItem> to register the event handler.</span></span>  
  
    ```vb  
    Private Sub newToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles newToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.newToolStripMenuItem.Click += new System.EventHandler(this.newToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c684c-115">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="c684c-115">Compiling the Code</span></span>  
 <span data-ttu-id="c684c-116">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="c684c-116">This example requires:</span></span>  
  
-   <span data-ttu-id="c684c-117">İki <xref:System.Windows.Forms.Form> adlarında `Form1` ve `Form2`.</span><span class="sxs-lookup"><span data-stu-id="c684c-117">Two <xref:System.Windows.Forms.Form> controls named `Form1` and `Form2`.</span></span>  
  
-   <span data-ttu-id="c684c-118">A <xref:System.Windows.Forms.MenuStrip> denetimi `Form1` adlı `menuStrip1`ve <xref:System.Windows.Forms.MenuStrip> denetimi `Form2` adlı `menuStrip2`.</span><span class="sxs-lookup"><span data-stu-id="c684c-118">A <xref:System.Windows.Forms.MenuStrip> control on `Form1` named `menuStrip1`, and a <xref:System.Windows.Forms.MenuStrip> control on `Form2` named `menuStrip2`.</span></span>  
  
-   <span data-ttu-id="c684c-119">Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.</span><span class="sxs-lookup"><span data-stu-id="c684c-119">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c684c-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c684c-120">See also</span></span>
- [<span data-ttu-id="c684c-121">Nasıl yapılır: MDI üst formları oluşturma</span><span class="sxs-lookup"><span data-stu-id="c684c-121">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="c684c-122">Nasıl yapılır: MDI alt formları oluştur</span><span class="sxs-lookup"><span data-stu-id="c684c-122">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="c684c-123">MenuStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="c684c-123">MenuStrip Control</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)
