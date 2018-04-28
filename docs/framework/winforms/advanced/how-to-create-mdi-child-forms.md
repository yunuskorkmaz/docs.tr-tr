---
title: 'Nasıl yapılır: MDI Alt Formları Oluşturma'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- MDI [Windows Forms], creating forms
- child forms
ms.assetid: 164b69bb-2eca-4339-ada3-0679eb2c6dda
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d28a7390ea3cfbd922f029d963ad3249db399177
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-mdi-child-forms"></a><span data-ttu-id="37001-102">Nasıl yapılır: MDI Alt Formları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="37001-102">How to: Create MDI Child Forms</span></span>
<span data-ttu-id="37001-103">MDI alt formları olan önemli bir öğe [Çoklu belge arabirimi (MDI) uygulamaları](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md), bu formların kullanıcı etkileşimi merkezi olarak.</span><span class="sxs-lookup"><span data-stu-id="37001-103">MDI child forms are an essential element of [Multiple-Document Interface (MDI) Applications](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md), as these forms are the center of user interaction.</span></span>  
  
 <span data-ttu-id="37001-104">Aşağıdaki yordamda görüntüler MDI alt form oluşturacak bir <xref:System.Windows.Forms.RichTextBox> denetim, çoğu sözcük işlemci uygulamalarına benzer.</span><span class="sxs-lookup"><span data-stu-id="37001-104">In the following procedure, you will create MDI child form that displays a <xref:System.Windows.Forms.RichTextBox> control, similar to most word-processing applications.</span></span> <span data-ttu-id="37001-105">Değiştirerek <xref:System.Windows.Forms> başka denetimlerle birlikte denetimini <xref:System.Windows.Forms.DataGridView> denetim veya denetimlerin bir karışımını MDI alt pencereleri oluşturmak etkinleştirir (ve uzantılarının, MDI uygulamaları) farklı sayıda olasılık ile.</span><span class="sxs-lookup"><span data-stu-id="37001-105">Substituting the <xref:System.Windows.Forms> control with other controls, such as the <xref:System.Windows.Forms.DataGridView> control, or a mixture of controls enables you to create MDI child windows (and, by extension, MDI applications) with diverse possibilities.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="37001-106">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="37001-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="37001-107">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="37001-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="37001-108">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="37001-108">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-create-mdi-child-forms"></a><span data-ttu-id="37001-109">MDI alt formları oluşturma</span><span class="sxs-lookup"><span data-stu-id="37001-109">To create MDI child forms</span></span>  
  
1.  <span data-ttu-id="37001-110">Yeni bir Windows Forms projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="37001-110">Create a new Windows Forms project.</span></span> <span data-ttu-id="37001-111">İçinde **özellikleri Windows** formun kendi <xref:System.Windows.Forms.Form.IsMdiContainer%2A> özelliğine `true`ve kendi `WindowsState` özelliğine `Maximized`.</span><span class="sxs-lookup"><span data-stu-id="37001-111">In **the Properties Windows** for the form, set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`, and its `WindowsState` property to `Maximized`.</span></span>  
  
     <span data-ttu-id="37001-112">Bu, formun alt windows için bir MDI kapsayıcı olarak belirler.</span><span class="sxs-lookup"><span data-stu-id="37001-112">This designates the form as an MDI container for child windows.</span></span>  
  
2.  <span data-ttu-id="37001-113">Gelen `Toolbox`, sürükleyin bir <xref:System.Windows.Forms.MenuStrip> forma denetim.</span><span class="sxs-lookup"><span data-stu-id="37001-113">From the `Toolbox`, drag a <xref:System.Windows.Forms.MenuStrip> control to the form.</span></span> <span data-ttu-id="37001-114">Ayarlama, `Text` özelliğine **dosya**.</span><span class="sxs-lookup"><span data-stu-id="37001-114">Set its `Text` property to **File**.</span></span>  
  
3.  <span data-ttu-id="37001-115">Yanındaki üç nokta (...) tıklatın **öğeleri** özelliği ve tıklatın **Ekle** iki alt aracı Şerit menü öğelerini eklemek için.</span><span class="sxs-lookup"><span data-stu-id="37001-115">Click the ellipses (…) next to the **Items** property, and click **Add** to add two child tool strip menu items.</span></span> <span data-ttu-id="37001-116">Ayarlama `Text` özelliği bu öğeler için **yeni** ve **penceresi**.</span><span class="sxs-lookup"><span data-stu-id="37001-116">Set the `Text` property for these items to **New** and **Window**.</span></span>  
  
4.  <span data-ttu-id="37001-117">İçinde **Çözüm Gezgini**, projeye sağ tıklayın, fareyle **Ekle**ve ardından **Yeni Öğe Ekle**.</span><span class="sxs-lookup"><span data-stu-id="37001-117">In **Solution Explorer**, right-click the project, point to **Add**, and then select **Add New Item**.</span></span>  
  
5.  <span data-ttu-id="37001-118">İçinde **Yeni Öğe Ekle** iletişim kutusunda **Windows formu** (Visual Basic veya Visual C# ' ta) veya **Windows Forms uygulaması (.NET)** (içinde [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) gelen **Şablonları** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="37001-118">In the **Add New Item** dialog box, select **Windows Form** (in Visual Basic or in Visual C#) or **Windows Forms Application (.NET)** (in [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) from the **Templates** pane.</span></span> <span data-ttu-id="37001-119">İçinde **adı** kutusunda, formun ad **Form2**.</span><span class="sxs-lookup"><span data-stu-id="37001-119">In the **Name** box, name the form **Form2**.</span></span> <span data-ttu-id="37001-120">Tıklatın **açık** projeye form ekleme düğmesi.</span><span class="sxs-lookup"><span data-stu-id="37001-120">Click the **Open** button to add the form to the project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="37001-121">Bu adımda oluşturduğunuz MDI alt standart Windows formu biçimidir.</span><span class="sxs-lookup"><span data-stu-id="37001-121">The MDI child form you created in this step is a standard Windows Form.</span></span> <span data-ttu-id="37001-122">Bu nedenle, sahip bir <xref:System.Windows.Forms.Form.Opacity%2A> formun saydamlığını denetlemenize olanak sağlayan özelliği.</span><span class="sxs-lookup"><span data-stu-id="37001-122">As such, it has an <xref:System.Windows.Forms.Form.Opacity%2A> property, which enables you to control the transparency of the form.</span></span> <span data-ttu-id="37001-123">Ancak, <xref:System.Windows.Forms.Form.Opacity%2A> özelliği, üst düzey windows için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="37001-123">However, the <xref:System.Windows.Forms.Form.Opacity%2A> property was designed for top-level windows.</span></span> <span data-ttu-id="37001-124">Boyama sorunları ortaya çıktığında MDI alt formları ile kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="37001-124">Do not use it with MDI child forms, as painting problems can occur.</span></span>  
  
     <span data-ttu-id="37001-125">Bu form MDI alt formları için şablonu olacaktır.</span><span class="sxs-lookup"><span data-stu-id="37001-125">This form will be the template for your MDI child forms.</span></span>  
  
     <span data-ttu-id="37001-126">**Windows Form Tasarımcısı** görüntüleme açılır **Form2**.</span><span class="sxs-lookup"><span data-stu-id="37001-126">The **Windows Forms Designer** opens, displaying **Form2**.</span></span>  
  
6.  <span data-ttu-id="37001-127">Gelen **araç**, sürükleyin bir **RichTextBox** forma denetim.</span><span class="sxs-lookup"><span data-stu-id="37001-127">From the **Toolbox**, drag a **RichTextBox** control to the form.</span></span>  
  
7.  <span data-ttu-id="37001-128">İçinde **özellikleri** penceresindeki ayarlayın `Anchor` özelliğine **üst, sol** ve `Dock` özelliğine **doldurun**.</span><span class="sxs-lookup"><span data-stu-id="37001-128">In the **Properties** window, set the `Anchor` property to **Top, Left** and the `Dock` property to **Fill**.</span></span>  
  
     <span data-ttu-id="37001-129">Bu neden <xref:System.Windows.Forms.RichTextBox> bile formu boyutlandırıldığında tamamen MDI alt formunun alanını doldurmak için denetim.</span><span class="sxs-lookup"><span data-stu-id="37001-129">This causes the <xref:System.Windows.Forms.RichTextBox> control to completely fill the area of the MDI child form, even when the form is resized.</span></span>  
  
8.  <span data-ttu-id="37001-130">Çift tıklayarak **yeni** menü öğesi oluşturmak için bir <xref:System.Windows.Forms.Control.Click> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="37001-130">Double click the **New** menu item to create a <xref:System.Windows.Forms.Control.Click> event handler for it.</span></span>  
  
9. <span data-ttu-id="37001-131">Aşağıdaki kullanıcı tıklattığında yeni bir MDI alt form oluşturmak için benzer bir kod ekleme **yeni** menü öğesi.</span><span class="sxs-lookup"><span data-stu-id="37001-131">Insert code similar to the following to create a new MDI child form when the user clicks the **New** menu item.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="37001-132">Aşağıdaki örnekte, olay işleyicisi işleme <xref:System.Windows.Forms.Control.Click> olayı `MenuItem2`.</span><span class="sxs-lookup"><span data-stu-id="37001-132">In the following example, the event handler handles the <xref:System.Windows.Forms.Control.Click> event for `MenuItem2`.</span></span> <span data-ttu-id="37001-133">Unutmayın, uygulama Mimarinizi ayrıntılarını bağlı olarak, **yeni** menü öğesi olmayabilir `MenuItem2`.</span><span class="sxs-lookup"><span data-stu-id="37001-133">Be aware that, depending on the specifics of your application architecture, your **New** menu item may not be `MenuItem2`.</span></span>  
  
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
  
     <span data-ttu-id="37001-134">İçinde [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], aşağıdakileri ekleyin `#include` Form1.h üstündeki yönerge:</span><span class="sxs-lookup"><span data-stu-id="37001-134">In [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], add the following `#include` directive at the top of Form1.h:</span></span>  
  
    ```cpp  
    #include "Form2.h"  
    ```  
  
10. <span data-ttu-id="37001-135">Aşağı açılan listesinde en üstündeki **özellikleri** penceresinde, karşılık gelen menü Şerit seçin **dosya** menü Şerit ve kümesi <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> penceresine özelliği <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="37001-135">In the drop-down list at the top of the **Properties** window, select the menu strip that corresponds to the **File** menu strip and set the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property to the Window <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
     <span data-ttu-id="37001-136">Bu etkinleştirecek **penceresi** etkin alt pencere yanındaki onay işaretiyle açık MDI alt pencereleri listesini korumak için menüsü.</span><span class="sxs-lookup"><span data-stu-id="37001-136">This will enable the **Window** menu to maintain a list of open MDI child windows with a check mark next to the active child window.</span></span>  
  
11. <span data-ttu-id="37001-137">Uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="37001-137">Press F5 to run the application.</span></span> <span data-ttu-id="37001-138">Seçerek **yeni** gelen **dosya** menüsünde hangi tutulan içinde izlemek yeni MDI alt formları oluşturabilirsiniz **penceresi** menü öğesi.</span><span class="sxs-lookup"><span data-stu-id="37001-138">By selecting **New** from the **File** menu, you can create new MDI child forms, which are kept track of in the **Window** menu item.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="37001-139">MDI alt formu olduğunda bir <xref:System.Windows.Forms.MainMenu> bileşeni (yapısıyla, genellikle, menü menü öğeleri) ve onu içeren MDI üst formu içinde açıldığında bir <xref:System.Windows.Forms.MainMenu> bileşeni (ile genellikle bir menü yapısı menü öğelerinin), öğeleri birleştirme otomatik olarak menüsü ayarlamış olmanız durumunda <xref:System.Windows.Forms.MenuItem.MergeType%2A> özelliği (ve isteğe bağlı olarak <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> özelliği).</span><span class="sxs-lookup"><span data-stu-id="37001-139">When an MDI child form has a <xref:System.Windows.Forms.MainMenu> component (with, usually, a menu structure of menu items) and it is opened within an MDI parent form that has a <xref:System.Windows.Forms.MainMenu> component (with, usually, a menu structure of menu items), the menu items will merge automatically if you have set the <xref:System.Windows.Forms.MenuItem.MergeType%2A> property (and optionally, the <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> property).</span></span> <span data-ttu-id="37001-140">Ayarlama <xref:System.Windows.Forms.MenuItem.MergeType%2A> özelliği hem <xref:System.Windows.Forms.MainMenu> bileşenleri ve tüm alt formun menü öğelerinin <xref:System.Windows.Forms.MenuMerge.MergeItems>.</span><span class="sxs-lookup"><span data-stu-id="37001-140">Set the <xref:System.Windows.Forms.MenuItem.MergeType%2A> property of both <xref:System.Windows.Forms.MainMenu> components and all of the menu items of the child form to <xref:System.Windows.Forms.MenuMerge.MergeItems>.</span></span> <span data-ttu-id="37001-141">Ayrıca, olarak <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> özelliği hem menülerden menü öğelerini böylece sıralamada görünür.</span><span class="sxs-lookup"><span data-stu-id="37001-141">Additionally, set the <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> property so that the menu items from both menus appear in the desired order.</span></span> <span data-ttu-id="37001-142">Ayrıca, MDI üst formu kapattığınızda, her MDI alt başlatır forms göz önünde bulundurmanız bir <xref:System.Windows.Forms.Form.Closing> önce olay <xref:System.Windows.Forms.Form.Closing> MDI üst olayı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="37001-142">Moreover, keep in mind that when you close an MDI parent form, each of the MDI child forms raises a <xref:System.Windows.Forms.Form.Closing> event before the <xref:System.Windows.Forms.Form.Closing> event for the MDI parent is raised.</span></span> <span data-ttu-id="37001-143">Bir MDI çocuğun iptal etme <xref:System.Windows.Forms.Form.Closing> olay MDI üst öğenin engellemez <xref:System.Windows.Forms.Form.Closing> gerçekleştirilen; gelen olay ancak <xref:System.ComponentModel.CancelEventArgs> MDI üst öğenin için bağımsız değişken <xref:System.Windows.Forms.Form.Closing> olay şimdi şekilde ayarlanacak `true`.</span><span class="sxs-lookup"><span data-stu-id="37001-143">Canceling an MDI child's <xref:System.Windows.Forms.Form.Closing> event will not prevent the MDI parent's <xref:System.Windows.Forms.Form.Closing> event from being raised; however, the <xref:System.ComponentModel.CancelEventArgs> argument for the MDI parent's <xref:System.Windows.Forms.Form.Closing> event will now be set to `true`.</span></span> <span data-ttu-id="37001-144">MDI ve tüm MDI alt formları ayarlayarak kapatmaya zorlamak <xref:System.ComponentModel.CancelEventArgs> bağımsız değişkeni `false`.</span><span class="sxs-lookup"><span data-stu-id="37001-144">You can force the MDI parent and all MDI child forms to close by setting the <xref:System.ComponentModel.CancelEventArgs> argument to `false`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37001-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="37001-145">See Also</span></span>  
 [<span data-ttu-id="37001-146">Çok Belgeli Arabirim (MDI) Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="37001-146">Multiple-Document Interface (MDI) Applications</span></span>](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)  
 [<span data-ttu-id="37001-147">Nasıl yapılır: MDI Üst Formları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="37001-147">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [<span data-ttu-id="37001-148">Nasıl yapılır: Etkin MDI Alt Öğesini Belirleme</span><span class="sxs-lookup"><span data-stu-id="37001-148">How to: Determine the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)  
 [<span data-ttu-id="37001-149">Nasıl yapılır: Etkin MDI Alt Öğesine Veri Gönderme</span><span class="sxs-lookup"><span data-stu-id="37001-149">How to: Send Data to the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)  
 [<span data-ttu-id="37001-150">Nasıl yapılır: MDI Alt Formlarını Düzenleme</span><span class="sxs-lookup"><span data-stu-id="37001-150">How to: Arrange MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)
