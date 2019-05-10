---
title: 'Nasıl yapılır: MDI Alt Formları Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- MDI [Windows Forms], creating forms
- child forms
ms.assetid: 164b69bb-2eca-4339-ada3-0679eb2c6dda
ms.openlocfilehash: fbc92c03da69dd452f35e5b4e00cd4a9ca17e252
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211177"
---
# <a name="how-to-create-mdi-child-forms"></a><span data-ttu-id="e6f4a-102">Nasıl yapılır: MDI alt formları oluştur</span><span class="sxs-lookup"><span data-stu-id="e6f4a-102">How to: Create MDI child forms</span></span>

<span data-ttu-id="e6f4a-103">MDI alt formlarını olan önemli bir öğesidir [Çok Belgeli Arabirim (MDI) uygulamaları](multiple-document-interface-mdi-applications.md), bu formları kullanıcı etkileşimi merkezi olarak.</span><span class="sxs-lookup"><span data-stu-id="e6f4a-103">MDI child forms are an essential element of [Multiple-Document Interface (MDI) Applications](multiple-document-interface-mdi-applications.md), as these forms are the center of user interaction.</span></span>

<span data-ttu-id="e6f4a-104">Aşağıdaki yordamda görüntüleyen bir MDI alt formunu oluşturmak için Visual Studio kullanacaksınız bir <xref:System.Windows.Forms.RichTextBox> denetimi en sözcük uygulamalarına benzer.</span><span class="sxs-lookup"><span data-stu-id="e6f4a-104">In the following procedure, you'll use Visual Studio to create an MDI child form that displays a <xref:System.Windows.Forms.RichTextBox> control, similar to most word-processing applications.</span></span> <span data-ttu-id="e6f4a-105">Değiştirerek <xref:System.Windows.Forms> diğer denetimlerle denetimini <xref:System.Windows.Forms.DataGridView> denetim veya denetimlerin bir karışımını sağlar, MDI alt pencereleri oluşturmak (ve uzantısı, MDI uygulamaları) ile çeşitli olanaklar.</span><span class="sxs-lookup"><span data-stu-id="e6f4a-105">Substituting the <xref:System.Windows.Forms> control with other controls, such as the <xref:System.Windows.Forms.DataGridView> control, or a mixture of controls enables you to create MDI child windows (and, by extension, MDI applications) with diverse possibilities.</span></span>

## <a name="create-mdi-child-forms"></a><span data-ttu-id="e6f4a-106">MDI alt formları oluştur</span><span class="sxs-lookup"><span data-stu-id="e6f4a-106">Create MDI child forms</span></span>

1. <span data-ttu-id="e6f4a-107">Yeni bir Windows Forms projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e6f4a-107">Create a new Windows Forms project.</span></span> <span data-ttu-id="e6f4a-108">İçinde **özellikleri Windows** formun kendi <xref:System.Windows.Forms.Form.IsMdiContainer%2A> özelliğini `true`ve onun `WindowsState` özelliğini `Maximized`.</span><span class="sxs-lookup"><span data-stu-id="e6f4a-108">In **the Properties Windows** for the form, set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`, and its `WindowsState` property to `Maximized`.</span></span>

   <span data-ttu-id="e6f4a-109">Bu, form alt pencereler için bir MDI kapsayıcısı olarak belirler.</span><span class="sxs-lookup"><span data-stu-id="e6f4a-109">This designates the form as an MDI container for child windows.</span></span>

2. <span data-ttu-id="e6f4a-110">Gelen `Toolbox`, sürükleyin bir <xref:System.Windows.Forms.MenuStrip> forma.</span><span class="sxs-lookup"><span data-stu-id="e6f4a-110">From the `Toolbox`, drag a <xref:System.Windows.Forms.MenuStrip> control to the form.</span></span> <span data-ttu-id="e6f4a-111">Ayarlama, `Text` özelliğini **dosya**.</span><span class="sxs-lookup"><span data-stu-id="e6f4a-111">Set its `Text` property to **File**.</span></span>

3. <span data-ttu-id="e6f4a-112">Yanındaki üç nokta (...) tıklayın **öğeleri** özelliği seçeneğine tıklayıp **Ekle** iki alt araç şeridi menü öğesi eklemek için.</span><span class="sxs-lookup"><span data-stu-id="e6f4a-112">Click the ellipses (…) next to the **Items** property, and click **Add** to add two child tool strip menu items.</span></span> <span data-ttu-id="e6f4a-113">Ayarlama `Text` özelliği için bu öğeler için **yeni** ve **penceresi**.</span><span class="sxs-lookup"><span data-stu-id="e6f4a-113">Set the `Text` property for these items to **New** and **Window**.</span></span>

4. <span data-ttu-id="e6f4a-114">İçinde **Çözüm Gezgini**, projeye sağ tıklayın, fareyle **Ekle**ve ardından **Yeni Öğe Ekle**.</span><span class="sxs-lookup"><span data-stu-id="e6f4a-114">In **Solution Explorer**, right-click the project, point to **Add**, and then select **Add New Item**.</span></span>

5. <span data-ttu-id="e6f4a-115">İçinde **Yeni Öğe Ekle** iletişim kutusunda **Windows Form** (Visual Basic veya Visual C#) veya **Windows Forms uygulaması (.NET)** (içinde [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) gelen **Şablonları** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="e6f4a-115">In the **Add New Item** dialog box, select **Windows Form** (in Visual Basic or in Visual C#) or **Windows Forms Application (.NET)** (in [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) from the **Templates** pane.</span></span> <span data-ttu-id="e6f4a-116">İçinde **adı** kutusunda, formun adı **Form2**.</span><span class="sxs-lookup"><span data-stu-id="e6f4a-116">In the **Name** box, name the form **Form2**.</span></span> <span data-ttu-id="e6f4a-117">Tıklayın **açık** projeye form ekleme düğmesi.</span><span class="sxs-lookup"><span data-stu-id="e6f4a-117">Click the **Open** button to add the form to the project.</span></span>

    > [!NOTE]
    > <span data-ttu-id="e6f4a-118">Bu adımda oluşturduğunuz MDI alt formu, bir standart Windows biçimidir.</span><span class="sxs-lookup"><span data-stu-id="e6f4a-118">The MDI child form you created in this step is a standard Windows Form.</span></span> <span data-ttu-id="e6f4a-119">Bu nedenle, sahip bir <xref:System.Windows.Forms.Form.Opacity%2A> form saydamlığını denetlemenize olanak sağlayan özellik.</span><span class="sxs-lookup"><span data-stu-id="e6f4a-119">As such, it has an <xref:System.Windows.Forms.Form.Opacity%2A> property, which enables you to control the transparency of the form.</span></span> <span data-ttu-id="e6f4a-120">Ancak, <xref:System.Windows.Forms.Form.Opacity%2A> özelliği, üst düzey pencerelere için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e6f4a-120">However, the <xref:System.Windows.Forms.Form.Opacity%2A> property was designed for top-level windows.</span></span> <span data-ttu-id="e6f4a-121">Boyama sorunlar oluşabilir gibi MDI alt formlarını ile kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="e6f4a-121">Do not use it with MDI child forms, as painting problems can occur.</span></span>

     <span data-ttu-id="e6f4a-122">Bu form, MDI alt formlarını şablonu olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e6f4a-122">This form will be the template for your MDI child forms.</span></span>

     <span data-ttu-id="e6f4a-123">**Windows Form Tasarımcısı** görüntüleme açıldığında **Form2**.</span><span class="sxs-lookup"><span data-stu-id="e6f4a-123">The **Windows Forms Designer** opens, displaying **Form2**.</span></span>

6. <span data-ttu-id="e6f4a-124">Gelen **araç kutusu**, sürükleyin bir **RichTextBox** forma.</span><span class="sxs-lookup"><span data-stu-id="e6f4a-124">From the **Toolbox**, drag a **RichTextBox** control to the form.</span></span>

7. <span data-ttu-id="e6f4a-125">İçinde **özellikleri** penceresinde `Anchor` özelliğini **üst, sol** ve `Dock` özelliğini **dolgu**.</span><span class="sxs-lookup"><span data-stu-id="e6f4a-125">In the **Properties** window, set the `Anchor` property to **Top, Left** and the `Dock` property to **Fill**.</span></span>

   <span data-ttu-id="e6f4a-126">Bu neden <xref:System.Windows.Forms.RichTextBox> bile formu yeniden boyutlandırıldığında alanı MDI alt formunun tamamen doldurmak için denetimi.</span><span class="sxs-lookup"><span data-stu-id="e6f4a-126">This causes the <xref:System.Windows.Forms.RichTextBox> control to completely fill the area of the MDI child form, even when the form is resized.</span></span>

8. <span data-ttu-id="e6f4a-127">Çift tıklayarak **yeni** oluşturmak için menü öğesi bir <xref:System.Windows.Forms.Control.Click> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="e6f4a-127">Double click the **New** menu item to create a <xref:System.Windows.Forms.Control.Click> event handler for it.</span></span>

9. <span data-ttu-id="e6f4a-128">Kullanıcı tıkladığında, yeni bir MDI alt formu oluşturmak için aşağıdaki için benzer bir kod ekleme **yeni** menü öğesi.</span><span class="sxs-lookup"><span data-stu-id="e6f4a-128">Insert code similar to the following to create a new MDI child form when the user clicks the **New** menu item.</span></span>

   > [!NOTE]
   > <span data-ttu-id="e6f4a-129">Aşağıdaki örnekte olay işleyicisi işler <xref:System.Windows.Forms.Control.Click> olayı `MenuItem2`.</span><span class="sxs-lookup"><span data-stu-id="e6f4a-129">In the following example, the event handler handles the <xref:System.Windows.Forms.Control.Click> event for `MenuItem2`.</span></span> <span data-ttu-id="e6f4a-130">Unutmayın uygulama mimarinizin ayrıntılarına bağlı olarak, uygulamanızın **yeni** menü öğesi olabilir `MenuItem2`.</span><span class="sxs-lookup"><span data-stu-id="e6f4a-130">Be aware that, depending on the specifics of your application architecture, your **New** menu item may not be `MenuItem2`.</span></span>

    ```vb
    Protected Sub MDIChildNew_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MenuItem2.Click
       Dim NewMDIChild As New Form2()
       'Set the Parent Form of the Child window.
       NewMDIChild.MdiParent = Me
       'Display the new form.
       NewMDIChild.Show()
    End Sub
    ```

    ```csharp
    protected void MDIChildNew_Click(object sender, System.EventArgs e){
       Form2 newMDIChild = new Form2();
       // Set the Parent Form of the Child window.
       newMDIChild.MdiParent = this;
       // Display the new form.
       newMDIChild.Show();
    }
    ```

    ```cpp
    private:
       void menuItem2_Click(System::Object ^ sender,
          System::EventArgs ^ e)
       {
          Form2^ newMDIChild = gcnew Form2();
          // Set the Parent Form of the Child window.
          newMDIChild->MdiParent = this;
          // Display the new form.
          newMDIChild->Show();
       }
    ```

   <span data-ttu-id="e6f4a-131">İçinde C++, aşağıdaki `#include` Form1.h üst kısmındaki yönergesi:</span><span class="sxs-lookup"><span data-stu-id="e6f4a-131">In C++, add the following `#include` directive at the top of Form1.h:</span></span>

   ```cpp
   #include "Form2.h"
   ```

10. <span data-ttu-id="e6f4a-132">En üstündeki açılan listesinde **özellikleri** penceresinde karşılık gelen menü Şerit seçin **dosya** Şerit menüsü ve kümesi <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> özellik penceresine <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="e6f4a-132">In the drop-down list at the top of the **Properties** window, select the menu strip that corresponds to the **File** menu strip and set the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property to the Window <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>

    <span data-ttu-id="e6f4a-133">Bu olanak tanıyacak **penceresi** etkin alt pencerenin yanında bir onay işareti ile açık MDI alt pencereleri listesini korumak için menü.</span><span class="sxs-lookup"><span data-stu-id="e6f4a-133">This will enable the **Window** menu to maintain a list of open MDI child windows with a check mark next to the active child window.</span></span>

11. <span data-ttu-id="e6f4a-134">Tuşuna **F5** uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e6f4a-134">Press **F5** to run the application.</span></span> <span data-ttu-id="e6f4a-135">Seçerek **yeni** gelen **dosya** menüsünde, hangi tutulan içinde izlemek yeni MDI alt formlarını oluşturabilirsiniz **penceresi** menü öğesi.</span><span class="sxs-lookup"><span data-stu-id="e6f4a-135">By selecting **New** from the **File** menu, you can create new MDI child forms, which are kept track of in the **Window** menu item.</span></span>

    > [!NOTE]
    > <span data-ttu-id="e6f4a-136">MDI alt formu olduğunda bir <xref:System.Windows.Forms.MainMenu> (sahip, genellikle bir menüsü yapısı menü öğelerinin) bileşen ve onu içeren MDI üst formu içinde açılır bir <xref:System.Windows.Forms.MainMenu> (sahip, genellikle bir menüsü yapısı menü öğelerinin) bileşen, menü öğeleri otomatik olarak birleştirilir ayarladıysanız <xref:System.Windows.Forms.MenuItem.MergeType%2A> özelliği (ve isteğe bağlı olarak <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> özelliği).</span><span class="sxs-lookup"><span data-stu-id="e6f4a-136">When an MDI child form has a <xref:System.Windows.Forms.MainMenu> component (with, usually, a menu structure of menu items) and it is opened within an MDI parent form that has a <xref:System.Windows.Forms.MainMenu> component (with, usually, a menu structure of menu items), the menu items will merge automatically if you have set the <xref:System.Windows.Forms.MenuItem.MergeType%2A> property (and optionally, the <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> property).</span></span> <span data-ttu-id="e6f4a-137">Ayarlama <xref:System.Windows.Forms.MenuItem.MergeType%2A> her iki özellik <xref:System.Windows.Forms.MainMenu> bileşenlerini ve tüm alt formun menü öğelerinin <xref:System.Windows.Forms.MenuMerge.MergeItems>.</span><span class="sxs-lookup"><span data-stu-id="e6f4a-137">Set the <xref:System.Windows.Forms.MenuItem.MergeType%2A> property of both <xref:System.Windows.Forms.MainMenu> components and all of the menu items of the child form to <xref:System.Windows.Forms.MenuMerge.MergeItems>.</span></span> <span data-ttu-id="e6f4a-138">Ayrıca, olarak <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> özelliği hem menülerden menü öğelerini böylece istenen sırada görünür.</span><span class="sxs-lookup"><span data-stu-id="e6f4a-138">Additionally, set the <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> property so that the menu items from both menus appear in the desired order.</span></span> <span data-ttu-id="e6f4a-139">Ayrıca, MDI üst formu kapatın, her bir MDI alt harekete geçirirse forms akılda tutulması bir <xref:System.Windows.Forms.Form.Closing> olayından önce <xref:System.Windows.Forms.Form.Closing> MDI üst olayı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e6f4a-139">Moreover, keep in mind that when you close an MDI parent form, each of the MDI child forms raises a <xref:System.Windows.Forms.Form.Closing> event before the <xref:System.Windows.Forms.Form.Closing> event for the MDI parent is raised.</span></span> <span data-ttu-id="e6f4a-140">Bir MDI çocuk iptal <xref:System.Windows.Forms.Form.Closing> olay MDI üst öğenin engellemez <xref:System.Windows.Forms.Form.Closing> gerçekleştirilen; gelen olay ancak <xref:System.ComponentModel.CancelEventArgs> MDI üst öğenin için bağımsız değişken <xref:System.Windows.Forms.Form.Closing> olay artık ayarlanır `true`.</span><span class="sxs-lookup"><span data-stu-id="e6f4a-140">Canceling an MDI child's <xref:System.Windows.Forms.Form.Closing> event will not prevent the MDI parent's <xref:System.Windows.Forms.Form.Closing> event from being raised; however, the <xref:System.ComponentModel.CancelEventArgs> argument for the MDI parent's <xref:System.Windows.Forms.Form.Closing> event will now be set to `true`.</span></span> <span data-ttu-id="e6f4a-141">MDI ve tüm MDI alt formlarını ayarlayarak kapanmaya zorlayabilir <xref:System.ComponentModel.CancelEventArgs> bağımsız değişkeni `false`.</span><span class="sxs-lookup"><span data-stu-id="e6f4a-141">You can force the MDI parent and all MDI child forms to close by setting the <xref:System.ComponentModel.CancelEventArgs> argument to `false`.</span></span>

## <a name="see-also"></a><span data-ttu-id="e6f4a-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6f4a-142">See also</span></span>

- [<span data-ttu-id="e6f4a-143">Çok Belgeli Arabirim (MDI) Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="e6f4a-143">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="e6f4a-144">Nasıl yapılır: MDI üst formları oluşturma</span><span class="sxs-lookup"><span data-stu-id="e6f4a-144">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="e6f4a-145">Nasıl yapılır: Etkin MDI alt öğesini belirleme</span><span class="sxs-lookup"><span data-stu-id="e6f4a-145">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)
- [<span data-ttu-id="e6f4a-146">Nasıl yapılır: Etkin MDI alt öğesine veri gönderme</span><span class="sxs-lookup"><span data-stu-id="e6f4a-146">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)
- [<span data-ttu-id="e6f4a-147">Nasıl yapılır: MDI alt formlarını düzenleme</span><span class="sxs-lookup"><span data-stu-id="e6f4a-147">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)
