---
title: 'Nasıl yapılır: MDI Alt Formları Oluşturma'
description: Bir RichTextBox denetimi görüntüleyen birden çok belgeli arabirim (MDI) alt formu oluşturmak için Visual Studio 'Yu nasıl kullanacağınızı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- MDI [Windows Forms], creating forms
- child forms
ms.assetid: 164b69bb-2eca-4339-ada3-0679eb2c6dda
ms.openlocfilehash: 7fe5cde342f0f5ee078f888b7492cd4618bea5c4
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903188"
---
# <a name="how-to-create-mdi-child-forms"></a><span data-ttu-id="8da8c-103">Nasıl yapılır: MDI alt formları oluşturma</span><span class="sxs-lookup"><span data-stu-id="8da8c-103">How to: Create MDI child forms</span></span>

<span data-ttu-id="8da8c-104">MDI alt formları, [çok belgeli arabirim (MDI) uygulamalarının](multiple-document-interface-mdi-applications.md)temel bir öğesidir ve bu formlar kullanıcı etkileşiminin ortalarıdır.</span><span class="sxs-lookup"><span data-stu-id="8da8c-104">MDI child forms are an essential element of [Multiple-Document Interface (MDI) applications](multiple-document-interface-mdi-applications.md), as these forms are the center of user interaction.</span></span>

<span data-ttu-id="8da8c-105">Aşağıdaki yordamda, <xref:System.Windows.Forms.RichTextBox> çoğu sözcük işleme uygulamasına benzer bir denetim görüntüleyen BIR MDI alt formu oluşturmak Için Visual Studio 'yu kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="8da8c-105">In the following procedure, you'll use Visual Studio to create an MDI child form that displays a <xref:System.Windows.Forms.RichTextBox> control, similar to most word-processing applications.</span></span> <span data-ttu-id="8da8c-106">Denetimi veya denetim <xref:System.Windows.Forms> karışımı gibi diğer denetimlerle denetimi değiştirerek <xref:System.Windows.Forms.DataGridView> , farklı olasılıklarla MDI alt pencereleri (ve UZANTıSı, MDI uygulamaları) oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8da8c-106">By substituting the <xref:System.Windows.Forms> control with other controls, such as the <xref:System.Windows.Forms.DataGridView> control, or a mixture of controls, you can create MDI child windows (and, by extension, MDI applications) with diverse possibilities.</span></span>

## <a name="create-mdi-child-forms"></a><span data-ttu-id="8da8c-107">MDI alt formları oluşturma</span><span class="sxs-lookup"><span data-stu-id="8da8c-107">Create MDI child forms</span></span>

1. <span data-ttu-id="8da8c-108">Visual Studio 'da yeni bir Windows Forms uygulama projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8da8c-108">Create a new Windows Forms application project in Visual Studio.</span></span> <span data-ttu-id="8da8c-109">Formun **Özellikler** penceresinde, <xref:System.Windows.Forms.Form.IsMdiContainer%2A> özelliğini `true` ve `WindowsState` özelliğini olarak ayarlayın `Maximized` .</span><span class="sxs-lookup"><span data-stu-id="8da8c-109">In the **Properties** window for the form, set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true` and its `WindowsState` property to `Maximized`.</span></span>

   <span data-ttu-id="8da8c-110">Bu, formu alt Windows için bir MDI kapsayıcısı olarak belirler.</span><span class="sxs-lookup"><span data-stu-id="8da8c-110">This designates the form as an MDI container for child windows.</span></span>

2. <span data-ttu-id="8da8c-111">Öğesinden `Toolbox` bir <xref:System.Windows.Forms.MenuStrip> denetimi forma sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="8da8c-111">From the `Toolbox`, drag a <xref:System.Windows.Forms.MenuStrip> control to the form.</span></span> <span data-ttu-id="8da8c-112">`Text`Özelliğini **File**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8da8c-112">Set its `Text` property to **File**.</span></span>

3. <span data-ttu-id="8da8c-113">**Items** özelliğinin yanındaki üç nokta (...) işaretine tıklayın ve **Ekle** ' ye tıklayarak iki alt araç şeridi menü öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8da8c-113">Click the ellipsis (…) next to the **Items** property, and click **Add** to add two child tool strip menu items.</span></span> <span data-ttu-id="8da8c-114">`Text`Bu öğelerin özelliğini **Yeni** ve **pencere**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8da8c-114">Set the `Text` property for these items to **New** and **Window**.</span></span>

4. <span data-ttu-id="8da8c-115">**Çözüm Gezgini**, projeye sağ tıklayın ve ardından **Add**  >  **Yeni öğe**Ekle ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="8da8c-115">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

5. <span data-ttu-id="8da8c-116">**Yeni öğe Ekle** iletişim kutusunda, **Şablonlar** bölmesinden **Windows formu** (Visual Basic veya Visual C# ' de) veya **Windows Forms uygulama (.net)** (Visual C++) seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="8da8c-116">In the **Add New Item** dialog box, select **Windows Form** (in Visual Basic or in Visual C#) or **Windows Forms Application (.NET)** (in Visual C++) from the **Templates** pane.</span></span> <span data-ttu-id="8da8c-117">**Ad** kutusuna formu **Form2**olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="8da8c-117">In the **Name** box, name the form **Form2**.</span></span> <span data-ttu-id="8da8c-118">Formu projeye eklemek için **Aç** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="8da8c-118">Select **Open** to add the form to the project.</span></span>

    > [!NOTE]
    > <span data-ttu-id="8da8c-119">Bu adımda oluşturduğunuz MDI alt formu standart bir Windows formundadır.</span><span class="sxs-lookup"><span data-stu-id="8da8c-119">The MDI child form you created in this step is a standard Windows Form.</span></span> <span data-ttu-id="8da8c-120">Bu nedenle, <xref:System.Windows.Forms.Form.Opacity%2A> formun saydamlığını denetlemenizi sağlayan bir özelliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="8da8c-120">As such, it has an <xref:System.Windows.Forms.Form.Opacity%2A> property, which enables you to control the transparency of the form.</span></span> <span data-ttu-id="8da8c-121">Ancak, <xref:System.Windows.Forms.Form.Opacity%2A> özelliği üst düzey pencereler için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="8da8c-121">However, the <xref:System.Windows.Forms.Form.Opacity%2A> property was designed for top-level windows.</span></span> <span data-ttu-id="8da8c-122">Boyama sorunları gerçekleşebileceği için bunu MDI alt formları ile kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="8da8c-122">Do not use it with MDI child forms, as painting problems can occur.</span></span>

     <span data-ttu-id="8da8c-123">Bu form, MDI alt formlarınızın şablonu olacaktır.</span><span class="sxs-lookup"><span data-stu-id="8da8c-123">This form will be the template for your MDI child forms.</span></span>

     <span data-ttu-id="8da8c-124">**Windows Form Tasarımcısı** açılır, **Form2**görüntülüyor.</span><span class="sxs-lookup"><span data-stu-id="8da8c-124">The **Windows Forms Designer** opens, displaying **Form2**.</span></span>

6. <span data-ttu-id="8da8c-125">**Araç kutusundan**bir **RichTextBox** denetimini forma sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="8da8c-125">From the **Toolbox**, drag a **RichTextBox** control to the form.</span></span>

7. <span data-ttu-id="8da8c-126">**Özellikler** penceresinde, `Anchor` özelliği **üst, sol** ve `Dock` özelliğini **dolduracak**şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8da8c-126">In the **Properties** window, set the `Anchor` property to **Top, Left** and the `Dock` property to **Fill**.</span></span>

   <span data-ttu-id="8da8c-127">Bu, <xref:System.Windows.Forms.RichTextBox> denetimin, form yeniden boyutlandırılırken bıle MDI alt formunun alanını tamamen doldurmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="8da8c-127">This causes the <xref:System.Windows.Forms.RichTextBox> control to completely fill the area of the MDI child form, even when the form is resized.</span></span>

8. <span data-ttu-id="8da8c-128">**Yeni** menü öğesine çift tıklayarak <xref:System.Windows.Forms.Control.Click> onun için bir olay işleyicisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8da8c-128">Double click the **New** menu item to create a <xref:System.Windows.Forms.Control.Click> event handler for it.</span></span>

9. <span data-ttu-id="8da8c-129">Kullanıcı **Yeni** menü öğesine tıkladığında yenı bir MDI alt formu oluşturmak için aşağıdakine benzer bir kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8da8c-129">Insert code similar to the following to create a new MDI child form when the user clicks the **New** menu item.</span></span>

   > [!NOTE]
   > <span data-ttu-id="8da8c-130">Aşağıdaki örnekte, olay işleyicisi <xref:System.Windows.Forms.Control.Click> olayını işler `MenuItem2` .</span><span class="sxs-lookup"><span data-stu-id="8da8c-130">In the following example, the event handler handles the <xref:System.Windows.Forms.Control.Click> event for `MenuItem2`.</span></span> <span data-ttu-id="8da8c-131">Uygulama mimarinizin özelliklerine bağlı olarak **Yeni** menü öğesi bulunmayabilir `MenuItem2` .</span><span class="sxs-lookup"><span data-stu-id="8da8c-131">Be aware that, depending on the specifics of your application architecture, your **New** menu item may not be `MenuItem2`.</span></span>

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

   <span data-ttu-id="8da8c-132">C++ ' da, `#include` Form1. h ' nin en üstüne aşağıdaki yönergeyi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8da8c-132">In C++, add the following `#include` directive at the top of Form1.h:</span></span>

   ```cpp
   #include "Form2.h"
   ```

10. <span data-ttu-id="8da8c-133">**Özellikler** penceresinin üst kısmındaki aşağı açılan listede, **Dosya** menü şeridine karşılık gelen menü şeridi ' ni seçin ve <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> özelliği pencereye ayarlayın <xref:System.Windows.Forms.ToolStripMenuItem> .</span><span class="sxs-lookup"><span data-stu-id="8da8c-133">In the drop-down list at the top of the **Properties** window, select the menu strip that corresponds to the **File** menu strip and set the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property to the Window <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>

    <span data-ttu-id="8da8c-134">Bu, **pencere** menüsünün, etkin alt pencerenin yanındaki bir onay işaretiyle bırlıkte açık MDI alt pencereleri listesini korumasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="8da8c-134">This enables the **Window** menu to maintain a list of open MDI child windows with a check mark next to the active child window.</span></span>

11. <span data-ttu-id="8da8c-135">Uygulamayı çalıştırmak için **F5**'e basın.</span><span class="sxs-lookup"><span data-stu-id="8da8c-135">Press **F5** to run the application.</span></span> <span data-ttu-id="8da8c-136">**Dosya** menüsünden **Yeni** ' yi seçerek, **pencere** menü öğesinde izlenen yeni MDI alt formları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8da8c-136">By selecting **New** from the **File** menu, you can create new MDI child forms, which are kept track of in the **Window** menu item.</span></span>

    > [!NOTE]
    > <span data-ttu-id="8da8c-137">Bir MDI alt form <xref:System.Windows.Forms.MainMenu> bileşeni olduğunda (genellikle menü öğelerinin bir menü yapısı ile) ve bileşeni olan BIR MDI parent formu içinde ( <xref:System.Windows.Forms.MainMenu> genellikle menü öğelerinin bir menü yapısıyla) açılırsa, <xref:System.Windows.Forms.MenuItem.MergeType%2A> Özelliği (ve isteğe bağlı olarak, özelliğini) ayarladıysanız menü öğeleri otomatik olarak birleştirilir <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> .</span><span class="sxs-lookup"><span data-stu-id="8da8c-137">When an MDI child form has a <xref:System.Windows.Forms.MainMenu> component (with, usually, a menu structure of menu items) and it is opened within an MDI parent form that has a <xref:System.Windows.Forms.MainMenu> component (with, usually, a menu structure of menu items), the menu items will merge automatically if you have set the <xref:System.Windows.Forms.MenuItem.MergeType%2A> property (and optionally, the <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> property).</span></span> <span data-ttu-id="8da8c-138"><xref:System.Windows.Forms.MenuItem.MergeType%2A>Her iki <xref:System.Windows.Forms.MainMenu> bileşenin özelliğini ve alt formun tüm menü öğelerini olarak ayarlayın <xref:System.Windows.Forms.MenuMerge.MergeItems> .</span><span class="sxs-lookup"><span data-stu-id="8da8c-138">Set the <xref:System.Windows.Forms.MenuItem.MergeType%2A> property of both <xref:System.Windows.Forms.MainMenu> components and all of the menu items of the child form to <xref:System.Windows.Forms.MenuMerge.MergeItems>.</span></span> <span data-ttu-id="8da8c-139">Ayrıca, <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> özelliğini her iki menüdeki menü öğelerinin istenen sırada görünmesi için ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8da8c-139">Additionally, set the <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> property so that the menu items from both menus appear in the desired order.</span></span> <span data-ttu-id="8da8c-140">Üstelik, bir MDI parent formunu kapattığınızda, MDI alt formlarının her biri <xref:System.Windows.Forms.Form.Closing> <xref:System.Windows.Forms.Form.Closing> MDI parent olayı oluşturulmadan önce bir olay harekete geçirdiğini aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="8da8c-140">Moreover, keep in mind that when you close an MDI parent form, each of the MDI child forms raises a <xref:System.Windows.Forms.Form.Closing> event before the <xref:System.Windows.Forms.Form.Closing> event for the MDI parent is raised.</span></span> <span data-ttu-id="8da8c-141">MDI alt öğesinin olayının iptal edilmesi <xref:System.Windows.Forms.Form.Closing> MDI üst öğesinin olayının oluşmasını engellemez <xref:System.Windows.Forms.Form.Closing> ; ancak <xref:System.ComponentModel.CancelEventArgs> MDI parent olayının bağımsız değişkeni <xref:System.Windows.Forms.Form.Closing> Şimdi olarak ayarlanır `true` .</span><span class="sxs-lookup"><span data-stu-id="8da8c-141">Canceling an MDI child's <xref:System.Windows.Forms.Form.Closing> event will not prevent the MDI parent's <xref:System.Windows.Forms.Form.Closing> event from being raised; however, the <xref:System.ComponentModel.CancelEventArgs> argument for the MDI parent's <xref:System.Windows.Forms.Form.Closing> event will now be set to `true`.</span></span> <span data-ttu-id="8da8c-142">Bağımsız değişkenini olarak ayarlayarak MDI parent ve tüm MDI alt formlarını kapanmaya zorlayabilirsiniz <xref:System.ComponentModel.CancelEventArgs> `false` .</span><span class="sxs-lookup"><span data-stu-id="8da8c-142">You can force the MDI parent and all MDI child forms to close by setting the <xref:System.ComponentModel.CancelEventArgs> argument to `false`.</span></span>

## <a name="see-also"></a><span data-ttu-id="8da8c-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8da8c-143">See also</span></span>

- [<span data-ttu-id="8da8c-144">Çoklu Belge Arabirimi (MDI) Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="8da8c-144">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="8da8c-145">Nasıl yapılır: MDI Üst Formları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8da8c-145">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="8da8c-146">Nasıl yapılır: Etkin MDI Alt Öğesini Belirleme</span><span class="sxs-lookup"><span data-stu-id="8da8c-146">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)
- [<span data-ttu-id="8da8c-147">Nasıl yapılır: Etkin MDI Alt Öğesine Veri Gönderme</span><span class="sxs-lookup"><span data-stu-id="8da8c-147">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)
- [<span data-ttu-id="8da8c-148">Nasıl yapılır: MDI Alt Formlarını Düzenleme</span><span class="sxs-lookup"><span data-stu-id="8da8c-148">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)
