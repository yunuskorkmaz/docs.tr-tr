---
title: "İzlenecek yol: Araç Kutusunu Otomatik Olarak Özel Bileşenlerle Doldurma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IToolboxService interface
- Toolbox [Windows Forms], populating
- custom components [Windows Forms], adding to Toolbox
ms.assetid: 2fa1e3e8-6b9f-42b2-97c0-2be57444dba4
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 691487046e2a34dbf233dc4bc03e20f9ec245da1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-automatically-populating-the-toolbox-with-custom-components"></a><span data-ttu-id="216bd-102">İzlenecek yol: Araç Kutusunu Otomatik Olarak Özel Bileşenlerle Doldurma</span><span class="sxs-lookup"><span data-stu-id="216bd-102">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>
<span data-ttu-id="216bd-103">Bileşenlerinizi açık çözümdeki bir proje ile tanımlanır, bunlar otomatik olarak görünür **araç**, hiçbir eylem yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="216bd-103">If your components are defined by a project in the currently open solution, they will automatically appear in the **Toolbox**, with no action required by you.</span></span> <span data-ttu-id="216bd-104">El ile de doldurabilirsiniz **araç** kullanarak, özel bileşenlerle [seçin araç kutusu öğelerini iletişim kutusu (Visual Studio)](http://msdn.microsoft.com/en-us/bd07835f-18a8-433e-bccc-7141f65263bb), ancak **araç** hesap alır çözümünüzün öğelerinin aşağıdaki özelliklere sahip çıkışları oluşturun:</span><span class="sxs-lookup"><span data-stu-id="216bd-104">You can also manually populate the **Toolbox** with your custom components by using the [Choose Toolbox Items Dialog Box (Visual Studio)](http://msdn.microsoft.com/en-us/bd07835f-18a8-433e-bccc-7141f65263bb), but the **Toolbox** takes account of items in your solution's build outputs with all the following characteristics:</span></span>  
  
-   <span data-ttu-id="216bd-105">Implements <xref:System.ComponentModel.IComponent>;</span><span class="sxs-lookup"><span data-stu-id="216bd-105">Implements <xref:System.ComponentModel.IComponent>;</span></span>  
  
-   <span data-ttu-id="216bd-106">Sahip olmayan <xref:System.ComponentModel.ToolboxItemAttribute> kümesine `false`;</span><span class="sxs-lookup"><span data-stu-id="216bd-106">Does not have <xref:System.ComponentModel.ToolboxItemAttribute> set to `false`;</span></span>  
  
-   <span data-ttu-id="216bd-107">Sahip olmayan <xref:System.ComponentModel.DesignTimeVisibleAttribute> kümesine `false`.</span><span class="sxs-lookup"><span data-stu-id="216bd-107">Does not have <xref:System.ComponentModel.DesignTimeVisibleAttribute> set to `false`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="216bd-108">**Araç** çözümünüzü projede tarafından oluşturulmuş olmayan öğeler görüntülenmez şekilde başvuru zincirleri izlemez.</span><span class="sxs-lookup"><span data-stu-id="216bd-108">The **Toolbox** does not follow reference chains, so it will not display items that are not built by a project in your solution.</span></span>  
  
 <span data-ttu-id="216bd-109">Bu yönergeler, nasıl özel bir bileşen otomatik olarak görünür gösterir **araç** bileşen oluşturulduktan sonra.</span><span class="sxs-lookup"><span data-stu-id="216bd-109">This walkthrough demonstrates how a custom component automatically appears in the **Toolbox** once the component is built.</span></span> <span data-ttu-id="216bd-110">Bu örneklerde gösterilen görevler aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="216bd-110">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="216bd-111">Windows Forms projesi oluşturma.</span><span class="sxs-lookup"><span data-stu-id="216bd-111">Creating a Windows Forms project.</span></span>  
  
-   <span data-ttu-id="216bd-112">Özel bir bileşen oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="216bd-112">Creating a custom component.</span></span>  
  
-   <span data-ttu-id="216bd-113">Özel bir bileşen örneği oluşturma.</span><span class="sxs-lookup"><span data-stu-id="216bd-113">Creating an instance of a custom component.</span></span>  
  
-   <span data-ttu-id="216bd-114">Yüklemeyi kaldırma ve özel bir bileşen yeniden yükleniyor.</span><span class="sxs-lookup"><span data-stu-id="216bd-114">Unloading and reloading a custom component.</span></span>  
  
 <span data-ttu-id="216bd-115">İşiniz bittiğinde, görürsünüz **araç** oluşturduğunuz bir bileşen ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="216bd-115">When you are finished, you will see that the **Toolbox** is populated with a component that you have created.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="216bd-116">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="216bd-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="216bd-117">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="216bd-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="216bd-118">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="216bd-118">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="216bd-119">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="216bd-119">Creating the Project</span></span>  
 <span data-ttu-id="216bd-120">İlk adım, projeyi oluşturmak ve formu ayarlamak için ' dir.</span><span class="sxs-lookup"><span data-stu-id="216bd-120">The first step is to create the project and to set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="216bd-121">Proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="216bd-121">To create the project</span></span>  
  
1.  <span data-ttu-id="216bd-122">Adlı bir Windows tabanlı bir uygulama projesi oluşturun `ToolboxExample`.</span><span class="sxs-lookup"><span data-stu-id="216bd-122">Create a Windows-based application project called `ToolboxExample`.</span></span>  
  
     <span data-ttu-id="216bd-123">Daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).</span><span class="sxs-lookup"><span data-stu-id="216bd-123">For more information, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="216bd-124">Yeni bir bileşen projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="216bd-124">Add a new component to the project.</span></span> <span data-ttu-id="216bd-125">Bu çağrı `DemoComponent`.</span><span class="sxs-lookup"><span data-stu-id="216bd-125">Call it `DemoComponent`.</span></span>  
  
     <span data-ttu-id="216bd-126">Daha fazla bilgi için bkz: [NIB: nasıl yapılır: Yeni proje öğeleri Ekle](http://msdn.microsoft.com/en-us/63d3e16b-de6e-4bb5-a0e3-ecec762201ce).</span><span class="sxs-lookup"><span data-stu-id="216bd-126">For more information, see [NIB:How to: Add New Project Items](http://msdn.microsoft.com/en-us/63d3e16b-de6e-4bb5-a0e3-ecec762201ce).</span></span>  
  
3.  <span data-ttu-id="216bd-127">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="216bd-127">Build the project.</span></span>  
  
4.  <span data-ttu-id="216bd-128">Gelen **Araçları** menüsünde tıklatın **seçenekleri** öğesi.</span><span class="sxs-lookup"><span data-stu-id="216bd-128">From the **Tools** menu, click the **Options** item.</span></span> <span data-ttu-id="216bd-129">Tıklatın **genel** altında **Windows Form Tasarımcısı** öğesi ve emin **AutoToolboxPopulate** seçeneği **True**.</span><span class="sxs-lookup"><span data-stu-id="216bd-129">Click **General** under the **Windows Forms Designer** item and ensure that the **AutoToolboxPopulate** option is set to **True**.</span></span>  
  
## <a name="creating-an-instance-of-a-custom-component"></a><span data-ttu-id="216bd-130">Özel bir bileşen örneği oluşturma</span><span class="sxs-lookup"><span data-stu-id="216bd-130">Creating an Instance of a Custom Component</span></span>  
 <span data-ttu-id="216bd-131">Sonraki adım, formdaki özel bileşen örneği oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="216bd-131">The next step is to create an instance of the custom component on the form.</span></span> <span data-ttu-id="216bd-132">Çünkü **araç** otomatik olarak yeni bileşen hesaplarını, bunun herhangi bir bileşen veya denetim oluşturma olarak kadar kolaydır.</span><span class="sxs-lookup"><span data-stu-id="216bd-132">Because the **Toolbox** automatically accounts for the new component, this is as easy as creating any other component or control.</span></span>  
  
#### <a name="to-create-an-instance-of-a-custom-component"></a><span data-ttu-id="216bd-133">Özel bir bileşen örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="216bd-133">To create an instance of a custom component</span></span>  
  
1.  <span data-ttu-id="216bd-134">Projenin formunda açmak **Forms Tasarımcısı**.</span><span class="sxs-lookup"><span data-stu-id="216bd-134">Open the project's form in the **Forms Designer**.</span></span>  
  
2.  <span data-ttu-id="216bd-135">İçinde **araç**, olarak adlandırılan yeni sekmesini **ToolboxExample bileşenleri**.</span><span class="sxs-lookup"><span data-stu-id="216bd-135">In the **Toolbox**, click the new tab called **ToolboxExample Components**.</span></span>  
  
     <span data-ttu-id="216bd-136">Sekmesine tıkladığınızda göreceğiniz **DemoComponent**.</span><span class="sxs-lookup"><span data-stu-id="216bd-136">Once you click the tab, you will see **DemoComponent**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="216bd-137">Performans nedenleriyle bileşenleri otomatik olarak doldurulmuş alanı **araç** özel bit eşlemler, görüntüleme ve <xref:System.Drawing.ToolboxBitmapAttribute> desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="216bd-137">For performance reasons, components in the auto-populated area of the **Toolbox** do not display custom bitmaps, and the <xref:System.Drawing.ToolboxBitmapAttribute> is not supported.</span></span> <span data-ttu-id="216bd-138">Özel bir bileşen için bir simge görüntülemek için **araç**, kullanın **araç kutusu öğelerini Seç** , bileşeni yüklemek için iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="216bd-138">To display an icon for a custom component in the **Toolbox**, use the **Choose Toolbox Items** dialog box to load your component.</span></span>  
  
3.  <span data-ttu-id="216bd-139">Bileşeniniz formunuza sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="216bd-139">Drag your component onto your form.</span></span>  
  
     <span data-ttu-id="216bd-140">Bileşen örneği oluşturulur ve eklenen **bileşen**.</span><span class="sxs-lookup"><span data-stu-id="216bd-140">An instance of the component is created and added to the **Component Tray**.</span></span>  
  
## <a name="unloading-and-reloading-a-custom-component"></a><span data-ttu-id="216bd-141">Yüklemeyi kaldırma ve özel bir bileşen yeniden yükleniyor</span><span class="sxs-lookup"><span data-stu-id="216bd-141">Unloading and Reloading a Custom Component</span></span>  
 <span data-ttu-id="216bd-142">**Araç** alır hesap her bileşenlerinin yüklü proje ve proje kaldırıldığında, projenin bileşenleri başvuruları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="216bd-142">The **Toolbox** takes account of the components in each loaded project, and when a project is unloaded, it removes references to the project's components.</span></span>  
  
#### <a name="to-experiment-with-the-effect-on-the-toolbox-of-unloading-and-reloading-components"></a><span data-ttu-id="216bd-143">Yüklemeyi kaldırma ve bileşenleri yeniden yükleme araç etkisi deneme</span><span class="sxs-lookup"><span data-stu-id="216bd-143">To experiment with the effect on the Toolbox of unloading and reloading components</span></span>  
  
1.  <span data-ttu-id="216bd-144">Çözüm projeden kaldırın.</span><span class="sxs-lookup"><span data-stu-id="216bd-144">Unload the project from the solution.</span></span>  
  
     <span data-ttu-id="216bd-145">Yüklemeyi kaldırma projeler hakkında daha fazla bilgi için bkz: [NIB: nasıl yapılır: Unload ve yeniden projeleri](http://msdn.microsoft.com/en-us/abc0155b-8fcb-4ffc-95b6-698518a7100b).</span><span class="sxs-lookup"><span data-stu-id="216bd-145">For more information about unloading projects, see [NIB:How to: Unload and Reload Projects](http://msdn.microsoft.com/en-us/abc0155b-8fcb-4ffc-95b6-698518a7100b).</span></span> <span data-ttu-id="216bd-146">Kaydetmek için istenirse, seçin **Evet**.</span><span class="sxs-lookup"><span data-stu-id="216bd-146">If you are prompted to save, choose **Yes**.</span></span>  
  
2.  <span data-ttu-id="216bd-147">Yeni bir ekleme **Windows uygulaması** çözüme proje.</span><span class="sxs-lookup"><span data-stu-id="216bd-147">Add a new **Windows Application** project to the solution.</span></span> <span data-ttu-id="216bd-148">Formunda açmak **Tasarımcısı**.</span><span class="sxs-lookup"><span data-stu-id="216bd-148">Open the form in the **Designer**.</span></span>  
  
     <span data-ttu-id="216bd-149">**ToolboxExample bileşenleri** önceki Proje sekmesinden olduğu artık kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="216bd-149">The **ToolboxExample Components** tab from the previous project is now gone.</span></span>  
  
3.  <span data-ttu-id="216bd-150">Yeniden yükleme `ToolboxExample` projesi.</span><span class="sxs-lookup"><span data-stu-id="216bd-150">Reload the `ToolboxExample` project.</span></span>  
  
     <span data-ttu-id="216bd-151">**ToolboxExample bileşenleri** sekmesinde şimdi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="216bd-151">The **ToolboxExample Components** tab now reappears.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="216bd-152">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="216bd-152">Next Steps</span></span>  
 <span data-ttu-id="216bd-153">Bu anlatımda gösterilir **araç kutusu** hesap bir projenin bileşenlerinin alır ancak **araç** ayrıca alır denetimleri hesabıdır.</span><span class="sxs-lookup"><span data-stu-id="216bd-153">This walkthrough demonstrates that the **Toolbox** takes account of a project's components, but the **Toolbox** is also takes account of controls.</span></span> <span data-ttu-id="216bd-154">Ekleyerek ve denetim projeleri çözümünüzden kaldırılması, kendi özel denetimler ile deneyin.</span><span class="sxs-lookup"><span data-stu-id="216bd-154">Experiment with your own custom controls by adding and removing control projects from your solution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="216bd-155">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="216bd-155">See Also</span></span>  
 [<span data-ttu-id="216bd-156">Genel, Windows Form Tasarımcısı, Seçenekler iletişim kutusu</span><span class="sxs-lookup"><span data-stu-id="216bd-156">General, Windows Forms Designer, Options Dialog Box</span></span>](http://msdn.microsoft.com/en-us/8dd170af-72f0-4212-b04b-034ceee92834)  
 [<span data-ttu-id="216bd-157">Nasıl yapılır: araç kutusu sekmeleri işlemek</span><span class="sxs-lookup"><span data-stu-id="216bd-157">How to: Manipulate Toolbox Tabs</span></span>](http://msdn.microsoft.com/en-us/21285050-cadd-455a-b1f5-a2289a89c4db)  
 [<span data-ttu-id="216bd-158">Araç kutusu öğelerini Seç iletişim kutusu (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="216bd-158">Choose Toolbox Items Dialog Box (Visual Studio)</span></span>](http://msdn.microsoft.com/en-us/bd07835f-18a8-433e-bccc-7141f65263bb)  
 [<span data-ttu-id="216bd-159">Windows formlarına denetimler koyma</span><span class="sxs-lookup"><span data-stu-id="216bd-159">Putting Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)
