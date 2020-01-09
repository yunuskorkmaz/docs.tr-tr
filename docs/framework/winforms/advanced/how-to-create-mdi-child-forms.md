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
ms.openlocfilehash: b49d43e0e1123921cb3800f0d60193d0ea7b3924
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75338590"
---
# <a name="how-to-create-mdi-child-forms"></a><span data-ttu-id="240d6-102">Nasıl yapılır: MDI alt formları oluşturma</span><span class="sxs-lookup"><span data-stu-id="240d6-102">How to: Create MDI child forms</span></span>

<span data-ttu-id="240d6-103">MDI alt formları, [çok belgeli arabirim (MDI) uygulamalarının](multiple-document-interface-mdi-applications.md)temel bir öğesidir ve bu formlar kullanıcı etkileşiminin ortalarıdır.</span><span class="sxs-lookup"><span data-stu-id="240d6-103">MDI child forms are an essential element of [Multiple-Document Interface (MDI) applications](multiple-document-interface-mdi-applications.md), as these forms are the center of user interaction.</span></span>

<span data-ttu-id="240d6-104">Aşağıdaki yordamda, çoğu sözcük işleme uygulamasına benzer bir <xref:System.Windows.Forms.RichTextBox> denetimi görüntüleyen bir MDI alt formu oluşturmak için Visual Studio 'Yu kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="240d6-104">In the following procedure, you'll use Visual Studio to create an MDI child form that displays a <xref:System.Windows.Forms.RichTextBox> control, similar to most word-processing applications.</span></span> <span data-ttu-id="240d6-105"><xref:System.Windows.Forms> denetimini <xref:System.Windows.Forms.DataGridView> denetimi veya denetimlerin karışımı gibi diğer denetimlerle değiştirerek, farklı olasılıklarla MDI alt pencereleri (ve uzantısı, MDI uygulamaları) oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="240d6-105">By substituting the <xref:System.Windows.Forms> control with other controls, such as the <xref:System.Windows.Forms.DataGridView> control, or a mixture of controls, you can create MDI child windows (and, by extension, MDI applications) with diverse possibilities.</span></span>

## <a name="create-mdi-child-forms"></a><span data-ttu-id="240d6-106">MDI alt formları oluşturma</span><span class="sxs-lookup"><span data-stu-id="240d6-106">Create MDI child forms</span></span>

1. <span data-ttu-id="240d6-107">Visual Studio 'da yeni bir Windows Forms uygulama projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="240d6-107">Create a new Windows Forms application project in Visual Studio.</span></span> <span data-ttu-id="240d6-108">Formun **Özellikler** penceresinde, <xref:System.Windows.Forms.Form.IsMdiContainer%2A> özelliğini `true` ve `WindowsState` özelliğini `Maximized`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="240d6-108">In the **Properties** window for the form, set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true` and its `WindowsState` property to `Maximized`.</span></span>

   <span data-ttu-id="240d6-109">Bu, formu alt Windows için bir MDI kapsayıcısı olarak belirler.</span><span class="sxs-lookup"><span data-stu-id="240d6-109">This designates the form as an MDI container for child windows.</span></span>

2. <span data-ttu-id="240d6-110">`Toolbox`, bir <xref:System.Windows.Forms.MenuStrip> denetimini forma sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="240d6-110">From the `Toolbox`, drag a <xref:System.Windows.Forms.MenuStrip> control to the form.</span></span> <span data-ttu-id="240d6-111">`Text` özelliğini **File**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="240d6-111">Set its `Text` property to **File**.</span></span>

3. <span data-ttu-id="240d6-112">**Items** özelliğinin yanındaki üç nokta (...) işaretine tıklayın ve **Ekle** ' ye tıklayarak iki alt araç şeridi menü öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="240d6-112">Click the ellipsis (…) next to the **Items** property, and click **Add** to add two child tool strip menu items.</span></span> <span data-ttu-id="240d6-113">Bu öğelerin `Text` özelliğini **Yeni** ve **pencere**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="240d6-113">Set the `Text` property for these items to **New** and **Window**.</span></span>

4. <span data-ttu-id="240d6-114">**Çözüm Gezgini**, projeye sağ tıklayın ve ardından > **Yeni öğe** **Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="240d6-114">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

5. <span data-ttu-id="240d6-115">**Yeni öğe Ekle** iletişim kutusunda, **Şablonlar** bölmesinden **Windows form** (Visual Basic veya görsel C#) veya **Windows Forms uygulama (.net)** (görsel C++) seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="240d6-115">In the **Add New Item** dialog box, select **Windows Form** (in Visual Basic or in Visual C#) or **Windows Forms Application (.NET)** (in Visual C++) from the **Templates** pane.</span></span> <span data-ttu-id="240d6-116">**Ad** kutusuna formu **Form2**olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="240d6-116">In the **Name** box, name the form **Form2**.</span></span> <span data-ttu-id="240d6-117">Formu projeye eklemek için **Aç** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="240d6-117">Select **Open** to add the form to the project.</span></span>

    > [!NOTE]
    > <span data-ttu-id="240d6-118">Bu adımda oluşturduğunuz MDI alt formu standart bir Windows formundadır.</span><span class="sxs-lookup"><span data-stu-id="240d6-118">The MDI child form you created in this step is a standard Windows Form.</span></span> <span data-ttu-id="240d6-119">Bu nedenle, formun saydamlığını denetlemenizi sağlayan bir <xref:System.Windows.Forms.Form.Opacity%2A> özelliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="240d6-119">As such, it has an <xref:System.Windows.Forms.Form.Opacity%2A> property, which enables you to control the transparency of the form.</span></span> <span data-ttu-id="240d6-120">Ancak, <xref:System.Windows.Forms.Form.Opacity%2A> özelliği en üst düzey pencereler için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="240d6-120">However, the <xref:System.Windows.Forms.Form.Opacity%2A> property was designed for top-level windows.</span></span> <span data-ttu-id="240d6-121">Boyama sorunları gerçekleşebileceği için bunu MDI alt formları ile kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="240d6-121">Do not use it with MDI child forms, as painting problems can occur.</span></span>

     <span data-ttu-id="240d6-122">Bu form, MDI alt formlarınızın şablonu olacaktır.</span><span class="sxs-lookup"><span data-stu-id="240d6-122">This form will be the template for your MDI child forms.</span></span>

     <span data-ttu-id="240d6-123">**Windows Form Tasarımcısı** açılır, **Form2**görüntülüyor.</span><span class="sxs-lookup"><span data-stu-id="240d6-123">The **Windows Forms Designer** opens, displaying **Form2**.</span></span>

6. <span data-ttu-id="240d6-124">**Araç kutusundan**bir **RichTextBox** denetimini forma sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="240d6-124">From the **Toolbox**, drag a **RichTextBox** control to the form.</span></span>

7. <span data-ttu-id="240d6-125">**Özellikler** penceresinde, `Anchor` özelliğini **üst, sol** ve `Dock` özelliğini **dolduracak**şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="240d6-125">In the **Properties** window, set the `Anchor` property to **Top, Left** and the `Dock` property to **Fill**.</span></span>

   <span data-ttu-id="240d6-126">Bu, form yeniden boyutlandırılırken bile <xref:System.Windows.Forms.RichTextBox> denetiminin MDI alt formunun alanını tamamen doldurmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="240d6-126">This causes the <xref:System.Windows.Forms.RichTextBox> control to completely fill the area of the MDI child form, even when the form is resized.</span></span>

8. <span data-ttu-id="240d6-127">**Yeni** menü öğesine çift tıklayarak onun için <xref:System.Windows.Forms.Control.Click> bir olay işleyicisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="240d6-127">Double click the **New** menu item to create a <xref:System.Windows.Forms.Control.Click> event handler for it.</span></span>

9. <span data-ttu-id="240d6-128">Kullanıcı **Yeni** menü öğesine tıkladığında yenı bir MDI alt formu oluşturmak için aşağıdakine benzer bir kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="240d6-128">Insert code similar to the following to create a new MDI child form when the user clicks the **New** menu item.</span></span>

   > [!NOTE]
   > <span data-ttu-id="240d6-129">Aşağıdaki örnekte, olay işleyicisi `MenuItem2`için <xref:System.Windows.Forms.Control.Click> olayını işler.</span><span class="sxs-lookup"><span data-stu-id="240d6-129">In the following example, the event handler handles the <xref:System.Windows.Forms.Control.Click> event for `MenuItem2`.</span></span> <span data-ttu-id="240d6-130">Uygulama mimarinizin özelliklerine bağlı olarak, **Yeni** menü öğesi `MenuItem2`olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="240d6-130">Be aware that, depending on the specifics of your application architecture, your **New** menu item may not be `MenuItem2`.</span></span>

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

   <span data-ttu-id="240d6-131">İçinde C++, Form1. h ' nin en üstüne aşağıdaki `#include` yönergesini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="240d6-131">In C++, add the following `#include` directive at the top of Form1.h:</span></span>

   ```cpp
   #include "Form2.h"
   ```

10. <span data-ttu-id="240d6-132">**Özellikler** penceresinin üst kısmındaki aşağı açılan listede, **Dosya** menüsü şeridine karşılık gelen menü şeridi ' ni seçin ve <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> özelliğini pencere <xref:System.Windows.Forms.ToolStripMenuItem>olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="240d6-132">In the drop-down list at the top of the **Properties** window, select the menu strip that corresponds to the **File** menu strip and set the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property to the Window <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>

    <span data-ttu-id="240d6-133">Bu, **pencere** menüsünün, etkin alt pencerenin yanındaki bir onay işaretiyle bırlıkte açık MDI alt pencereleri listesini korumasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="240d6-133">This enables the **Window** menu to maintain a list of open MDI child windows with a check mark next to the active child window.</span></span>

11. <span data-ttu-id="240d6-134">Uygulamayı çalıştırmak için **F5**'e basın.</span><span class="sxs-lookup"><span data-stu-id="240d6-134">Press **F5** to run the application.</span></span> <span data-ttu-id="240d6-135">**Dosya** menüsünden **Yeni** ' yi seçerek, **pencere** menü öğesinde izlenen yeni MDI alt formları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="240d6-135">By selecting **New** from the **File** menu, you can create new MDI child forms, which are kept track of in the **Window** menu item.</span></span>

    > [!NOTE]
    > <span data-ttu-id="240d6-136">Bir MDI alt formu <xref:System.Windows.Forms.MainMenu> bileşeni olduğunda (genellikle menü öğelerinin bir menü yapısıyla) ve bir <xref:System.Windows.Forms.MainMenu> bileşeni olan bir MDI parent formu içinde (genellikle menü öğelerinin bir menü yapısıyla) açılırsa, <xref:System.Windows.Forms.MenuItem.MergeType%2A> özelliğini (ve isteğe bağlı olarak, <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> özelliğini) ayarladıysanız menü öğeleri otomatik olarak birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="240d6-136">When an MDI child form has a <xref:System.Windows.Forms.MainMenu> component (with, usually, a menu structure of menu items) and it is opened within an MDI parent form that has a <xref:System.Windows.Forms.MainMenu> component (with, usually, a menu structure of menu items), the menu items will merge automatically if you have set the <xref:System.Windows.Forms.MenuItem.MergeType%2A> property (and optionally, the <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> property).</span></span> <span data-ttu-id="240d6-137">Hem <xref:System.Windows.Forms.MainMenu> bileşenlerinin hem de alt formun tüm menü öğelerinin <xref:System.Windows.Forms.MenuItem.MergeType%2A> özelliğini <xref:System.Windows.Forms.MenuMerge.MergeItems>olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="240d6-137">Set the <xref:System.Windows.Forms.MenuItem.MergeType%2A> property of both <xref:System.Windows.Forms.MainMenu> components and all of the menu items of the child form to <xref:System.Windows.Forms.MenuMerge.MergeItems>.</span></span> <span data-ttu-id="240d6-138">Ayrıca, her iki menüdeki menü öğelerinin istenen sırada görünmesi için <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="240d6-138">Additionally, set the <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> property so that the menu items from both menus appear in the desired order.</span></span> <span data-ttu-id="240d6-139">Üstelik, bir MDI parent formunu kapattığınızda, MDI parent form <xref:System.Windows.Forms.Form.Closing> olayından önce MDI alt formlarının her biri <xref:System.Windows.Forms.Form.Closing> bir olay harekete geçirdiğini aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="240d6-139">Moreover, keep in mind that when you close an MDI parent form, each of the MDI child forms raises a <xref:System.Windows.Forms.Form.Closing> event before the <xref:System.Windows.Forms.Form.Closing> event for the MDI parent is raised.</span></span> <span data-ttu-id="240d6-140">MDI alt öğesinin <xref:System.Windows.Forms.Form.Closing> olayının iptal edilmesi, MDI üstünün <xref:System.Windows.Forms.Form.Closing> olayının oluşmasını engellemez; Ancak, MDI parent <xref:System.Windows.Forms.Form.Closing> olayının <xref:System.ComponentModel.CancelEventArgs> bağımsız değişkeni artık `true`olarak ayarlanacak.</span><span class="sxs-lookup"><span data-stu-id="240d6-140">Canceling an MDI child's <xref:System.Windows.Forms.Form.Closing> event will not prevent the MDI parent's <xref:System.Windows.Forms.Form.Closing> event from being raised; however, the <xref:System.ComponentModel.CancelEventArgs> argument for the MDI parent's <xref:System.Windows.Forms.Form.Closing> event will now be set to `true`.</span></span> <span data-ttu-id="240d6-141"><xref:System.ComponentModel.CancelEventArgs> bağımsız değişkenini `false`olarak ayarlayarak MDI parent ve tüm MDI alt formlarını kapanmaya zorlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="240d6-141">You can force the MDI parent and all MDI child forms to close by setting the <xref:System.ComponentModel.CancelEventArgs> argument to `false`.</span></span>

## <a name="see-also"></a><span data-ttu-id="240d6-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="240d6-142">See also</span></span>

- [<span data-ttu-id="240d6-143">Çok Belgeli Arabirim (MDI) Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="240d6-143">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="240d6-144">Nasıl yapılır: MDI Üst Formları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="240d6-144">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="240d6-145">Nasıl yapılır: Etkin MDI Alt Öğesini Belirleme</span><span class="sxs-lookup"><span data-stu-id="240d6-145">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)
- [<span data-ttu-id="240d6-146">Nasıl yapılır: Etkin MDI Alt Öğesine Veri Gönderme</span><span class="sxs-lookup"><span data-stu-id="240d6-146">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)
- [<span data-ttu-id="240d6-147">Nasıl yapılır: MDI Alt Formlarını Düzenleme</span><span class="sxs-lookup"><span data-stu-id="240d6-147">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)
