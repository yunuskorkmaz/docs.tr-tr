---
title: 'İzlenecek yol: Araç Kutusunu Otomatik Olarak Özel Bileşenlerle Doldurma'
ms.date: 03/30/2017
helpviewer_keywords:
- IToolboxService interface
- Toolbox [Windows Forms], populating
- custom components [Windows Forms], adding to Toolbox
ms.assetid: 2fa1e3e8-6b9f-42b2-97c0-2be57444dba4
ms.openlocfilehash: 488d51e748ea17b09e61b982db7abadc34f8e311
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43671897"
---
# <a name="walkthrough-automatically-populating-the-toolbox-with-custom-components"></a><span data-ttu-id="2ed9d-102">İzlenecek yol: Araç Kutusunu Otomatik Olarak Özel Bileşenlerle Doldurma</span><span class="sxs-lookup"><span data-stu-id="2ed9d-102">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>
<span data-ttu-id="2ed9d-103">Bileşenlerinizi açık çözümde bir proje tarafından tanımlanan, bunlar otomatik olarak görünür **araç kutusu**, sizin tarafınızdan gerekli herhangi bir işlem ile.</span><span class="sxs-lookup"><span data-stu-id="2ed9d-103">If your components are defined by a project in the currently open solution, they will automatically appear in the **Toolbox**, with no action required by you.</span></span> <span data-ttu-id="2ed9d-104">El ile de doldurabilirsiniz **araç kutusu** kullanarak kendi özel bileşenlerle [seçin araç kutusu öğeleri iletişim kutusu (Visual Studio)](https://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb), ancak **araç kutusu** alır çözümünüzün içindeki öğelerin aşağıdaki özelliklere sahip çıkışları derleme:</span><span class="sxs-lookup"><span data-stu-id="2ed9d-104">You can also manually populate the **Toolbox** with your custom components by using the [Choose Toolbox Items Dialog Box (Visual Studio)](https://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb), but the **Toolbox** takes account of items in your solution's build outputs with all the following characteristics:</span></span>  
  
-   <span data-ttu-id="2ed9d-105">Implements <xref:System.ComponentModel.IComponent>;</span><span class="sxs-lookup"><span data-stu-id="2ed9d-105">Implements <xref:System.ComponentModel.IComponent>;</span></span>  
  
-   <span data-ttu-id="2ed9d-106">Olmayan <xref:System.ComponentModel.ToolboxItemAttribute> kümesine `false`;</span><span class="sxs-lookup"><span data-stu-id="2ed9d-106">Does not have <xref:System.ComponentModel.ToolboxItemAttribute> set to `false`;</span></span>  
  
-   <span data-ttu-id="2ed9d-107">Olmayan <xref:System.ComponentModel.DesignTimeVisibleAttribute> kümesine `false`.</span><span class="sxs-lookup"><span data-stu-id="2ed9d-107">Does not have <xref:System.ComponentModel.DesignTimeVisibleAttribute> set to `false`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2ed9d-108">**Araç kutusu** , çözümde bir proje tarafından oluşturulmamış öğeleri görüntülenmez için başvuru zincirleri izlemez.</span><span class="sxs-lookup"><span data-stu-id="2ed9d-108">The **Toolbox** does not follow reference chains, so it will not display items that are not built by a project in your solution.</span></span>  
  
 <span data-ttu-id="2ed9d-109">Bu izlenecek yol, nasıl özel bir bileşeni otomatik olarak görünür gösterir **araç kutusu** bileşeni derlendikten sonra.</span><span class="sxs-lookup"><span data-stu-id="2ed9d-109">This walkthrough demonstrates how a custom component automatically appears in the **Toolbox** once the component is built.</span></span> <span data-ttu-id="2ed9d-110">Bu kılavuzda gösterilen görevler aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="2ed9d-110">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="2ed9d-111">Bir Windows Forms projesi oluşturma.</span><span class="sxs-lookup"><span data-stu-id="2ed9d-111">Creating a Windows Forms project.</span></span>  
  
-   <span data-ttu-id="2ed9d-112">Bir özel bileşene oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="2ed9d-112">Creating a custom component.</span></span>  
  
-   <span data-ttu-id="2ed9d-113">Özel bir bileşeninin örneği oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="2ed9d-113">Creating an instance of a custom component.</span></span>  
  
-   <span data-ttu-id="2ed9d-114">Kaldırma ve bir özel bileşene yeniden yükleniyor.</span><span class="sxs-lookup"><span data-stu-id="2ed9d-114">Unloading and reloading a custom component.</span></span>  
  
 <span data-ttu-id="2ed9d-115">İşlemi tamamladığınızda, göreceksiniz **araç kutusu** oluşturmuş olduğunuz bir bileşeni ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="2ed9d-115">When you are finished, you will see that the **Toolbox** is populated with a component that you have created.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2ed9d-116">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="2ed9d-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="2ed9d-117">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="2ed9d-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="2ed9d-118">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="2ed9d-118">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="2ed9d-119">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2ed9d-119">Creating the Project</span></span>  
 <span data-ttu-id="2ed9d-120">İlk adım projeyi oluşturmak ve formu ayarlamak için ' dir.</span><span class="sxs-lookup"><span data-stu-id="2ed9d-120">The first step is to create the project and to set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="2ed9d-121">Proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="2ed9d-121">To create the project</span></span>  
  
1.  <span data-ttu-id="2ed9d-122">Adlı bir Windows tabanlı uygulama projesi oluşturma `ToolboxExample` (**dosya** > **yeni** > **proje**  >  **Visual C#** veya **Visual Basic** > **Klasik Masaüstü** > **Windows Forms uygulamalarındaki**).</span><span class="sxs-lookup"><span data-stu-id="2ed9d-122">Create a Windows-based application project called `ToolboxExample` (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>  
  
2.  <span data-ttu-id="2ed9d-123">Yeni bir bileşen projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2ed9d-123">Add a new component to the project.</span></span> <span data-ttu-id="2ed9d-124">Bu çağrı `DemoComponent`.</span><span class="sxs-lookup"><span data-stu-id="2ed9d-124">Call it `DemoComponent`.</span></span>  
  
     <span data-ttu-id="2ed9d-125">Daha fazla bilgi için [NIB: nasıl yapılır: Yeni proje öğeleri ekleme](https://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce).</span><span class="sxs-lookup"><span data-stu-id="2ed9d-125">For more information, see [NIB:How to: Add New Project Items](https://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce).</span></span>  
  
3.  <span data-ttu-id="2ed9d-126">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2ed9d-126">Build the project.</span></span>  
  
4.  <span data-ttu-id="2ed9d-127">Gelen **Araçları** menüsünde tıklatın **seçenekleri** öğesi.</span><span class="sxs-lookup"><span data-stu-id="2ed9d-127">From the **Tools** menu, click the **Options** item.</span></span> <span data-ttu-id="2ed9d-128">Tıklayın **genel** altında **Windows Form Tasarımcısı** emin olun ve öğe **AutoToolboxPopulate** seçeneği **True**.</span><span class="sxs-lookup"><span data-stu-id="2ed9d-128">Click **General** under the **Windows Forms Designer** item and ensure that the **AutoToolboxPopulate** option is set to **True**.</span></span>  
  
## <a name="creating-an-instance-of-a-custom-component"></a><span data-ttu-id="2ed9d-129">Özel bileşen örneği oluşturma</span><span class="sxs-lookup"><span data-stu-id="2ed9d-129">Creating an Instance of a Custom Component</span></span>  
 <span data-ttu-id="2ed9d-130">Sonraki adım, formda özel bileşen örneği oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="2ed9d-130">The next step is to create an instance of the custom component on the form.</span></span> <span data-ttu-id="2ed9d-131">Çünkü **araç kutusu** otomatik olarak hesapları yeni bileşeni için bu olarak herhangi bir bileşeni veya denetimi oluşturmak oldukça kolaydır.</span><span class="sxs-lookup"><span data-stu-id="2ed9d-131">Because the **Toolbox** automatically accounts for the new component, this is as easy as creating any other component or control.</span></span>  
  
#### <a name="to-create-an-instance-of-a-custom-component"></a><span data-ttu-id="2ed9d-132">Bir özel bileşene bir örneğini oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="2ed9d-132">To create an instance of a custom component</span></span>  
  
1.  <span data-ttu-id="2ed9d-133">Projenin formda açın **Form Tasarımcısı**.</span><span class="sxs-lookup"><span data-stu-id="2ed9d-133">Open the project's form in the **Forms Designer**.</span></span>  
  
2.  <span data-ttu-id="2ed9d-134">İçinde **araç kutusu**, adlı yeni sekmesini **ToolboxExample bileşenleri**.</span><span class="sxs-lookup"><span data-stu-id="2ed9d-134">In the **Toolbox**, click the new tab called **ToolboxExample Components**.</span></span>  
  
     <span data-ttu-id="2ed9d-135">Sekmesine tıklayın, sonra göreceğiniz **DemoComponent**.</span><span class="sxs-lookup"><span data-stu-id="2ed9d-135">Once you click the tab, you will see **DemoComponent**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2ed9d-136">Performans nedenleriyle bileşenleri otomatik olarak doldurulan alanında **araç kutusu** özel bit eşlemler, görüntüleme ve <xref:System.Drawing.ToolboxBitmapAttribute> desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="2ed9d-136">For performance reasons, components in the auto-populated area of the **Toolbox** do not display custom bitmaps, and the <xref:System.Drawing.ToolboxBitmapAttribute> is not supported.</span></span> <span data-ttu-id="2ed9d-137">Özel bir bileşeni için bir simge görüntülemek için **araç kutusu**, kullanın **araç kutusu öğelerini Seç** iletişim kutusu, bileşeni yüklenemiyor.</span><span class="sxs-lookup"><span data-stu-id="2ed9d-137">To display an icon for a custom component in the **Toolbox**, use the **Choose Toolbox Items** dialog box to load your component.</span></span>  
  
3.  <span data-ttu-id="2ed9d-138">Bileşeniniz formunuza sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="2ed9d-138">Drag your component onto your form.</span></span>  
  
     <span data-ttu-id="2ed9d-139">Bileşen örneği oluşturulur ve eklenen **bileşeni Tepsi**.</span><span class="sxs-lookup"><span data-stu-id="2ed9d-139">An instance of the component is created and added to the **Component Tray**.</span></span>  
  
## <a name="unloading-and-reloading-a-custom-component"></a><span data-ttu-id="2ed9d-140">Bir özel bileşene yeniden yükleme ve kaldırma</span><span class="sxs-lookup"><span data-stu-id="2ed9d-140">Unloading and Reloading a Custom Component</span></span>  
 <span data-ttu-id="2ed9d-141">**Araç kutusu** alır hesabı bileşenlerin her proje yüklendi ve bir proje kaldırıldığında, projenin bileşenleri başvurular kaldırır.</span><span class="sxs-lookup"><span data-stu-id="2ed9d-141">The **Toolbox** takes account of the components in each loaded project, and when a project is unloaded, it removes references to the project's components.</span></span>  
  
#### <a name="to-experiment-with-the-effect-on-the-toolbox-of-unloading-and-reloading-components"></a><span data-ttu-id="2ed9d-142">Bileşenleri yeniden yükleme ve kaldırma araç kutusu üzerindeki etkisini denemek için</span><span class="sxs-lookup"><span data-stu-id="2ed9d-142">To experiment with the effect on the Toolbox of unloading and reloading components</span></span>  
  
1.  <span data-ttu-id="2ed9d-143">Çözümden proje Kaldır.</span><span class="sxs-lookup"><span data-stu-id="2ed9d-143">Unload the project from the solution.</span></span>  
  
     <span data-ttu-id="2ed9d-144">Projeleri kaldırma hakkında daha fazla bilgi için bkz. [NIB: nasıl yapılır: kaldırma ve yeniden projeleri](https://msdn.microsoft.com/library/abc0155b-8fcb-4ffc-95b6-698518a7100b).</span><span class="sxs-lookup"><span data-stu-id="2ed9d-144">For more information about unloading projects, see [NIB:How to: Unload and Reload Projects](https://msdn.microsoft.com/library/abc0155b-8fcb-4ffc-95b6-698518a7100b).</span></span> <span data-ttu-id="2ed9d-145">Kaydetmeniz istenirse seçin **Evet**.</span><span class="sxs-lookup"><span data-stu-id="2ed9d-145">If you are prompted to save, choose **Yes**.</span></span>  
  
2.  <span data-ttu-id="2ed9d-146">Yeni bir **Windows uygulama** çözüme bir proje.</span><span class="sxs-lookup"><span data-stu-id="2ed9d-146">Add a new **Windows Application** project to the solution.</span></span> <span data-ttu-id="2ed9d-147">Formda açın **Tasarımcısı**.</span><span class="sxs-lookup"><span data-stu-id="2ed9d-147">Open the form in the **Designer**.</span></span>  
  
     <span data-ttu-id="2ed9d-148">**ToolboxExample bileşenleri** , artık önceki projeyi sekmesinden kaybolur.</span><span class="sxs-lookup"><span data-stu-id="2ed9d-148">The **ToolboxExample Components** tab from the previous project is now gone.</span></span>  
  
3.  <span data-ttu-id="2ed9d-149">Reload `ToolboxExample` proje.</span><span class="sxs-lookup"><span data-stu-id="2ed9d-149">Reload the `ToolboxExample` project.</span></span>  
  
     <span data-ttu-id="2ed9d-150">**ToolboxExample bileşenleri** sekmesinde artık yeniden görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="2ed9d-150">The **ToolboxExample Components** tab now reappears.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="2ed9d-151">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="2ed9d-151">Next Steps</span></span>  
 <span data-ttu-id="2ed9d-152">Bu izlenecek yol gösteren **araç kutusu** projenin bileşenlerinin alır ancak **araç kutusu** ayrıca alır denetimleri hesabıdır.</span><span class="sxs-lookup"><span data-stu-id="2ed9d-152">This walkthrough demonstrates that the **Toolbox** takes account of a project's components, but the **Toolbox** is also takes account of controls.</span></span> <span data-ttu-id="2ed9d-153">İle kendi özel denetimler ekleyerek ve çözümünüze ait denetim projeleri kaldırma denemeler yapın.</span><span class="sxs-lookup"><span data-stu-id="2ed9d-153">Experiment with your own custom controls by adding and removing control projects from your solution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ed9d-154">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2ed9d-154">See Also</span></span>  
 [<span data-ttu-id="2ed9d-155">Genel, Windows Form Tasarımcısı, Seçenekler iletişim kutusu</span><span class="sxs-lookup"><span data-stu-id="2ed9d-155">General, Windows Forms Designer, Options Dialog Box</span></span>](https://msdn.microsoft.com/library/8dd170af-72f0-4212-b04b-034ceee92834)  
 [<span data-ttu-id="2ed9d-156">Nasıl yapılır: araç kutusu sekmeleri düzenleme</span><span class="sxs-lookup"><span data-stu-id="2ed9d-156">How to: Manipulate Toolbox Tabs</span></span>](https://msdn.microsoft.com/library/21285050-cadd-455a-b1f5-a2289a89c4db)  
 [<span data-ttu-id="2ed9d-157">Araç kutusu öğelerini Seç iletişim kutusu (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="2ed9d-157">Choose Toolbox Items Dialog Box (Visual Studio)</span></span>](https://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb)  
 [<span data-ttu-id="2ed9d-158">Windows Forms’a Denetimler Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="2ed9d-158">Putting Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)
