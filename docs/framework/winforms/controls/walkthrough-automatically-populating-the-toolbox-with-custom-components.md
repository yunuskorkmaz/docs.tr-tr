---
title: 'İzlenecek yol: Araç Kutusunu Otomatik Olarak Özel Bileşenlerle Doldurma'
ms.date: 03/30/2017
helpviewer_keywords:
- IToolboxService interface
- Toolbox [Windows Forms], populating
- custom components [Windows Forms], adding to Toolbox
ms.assetid: 2fa1e3e8-6b9f-42b2-97c0-2be57444dba4
ms.openlocfilehash: 876de650f9c182c0f82a02d1c5b356faa4f7f118
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211155"
---
# <a name="walkthrough-automatically-populating-the-toolbox-with-custom-components"></a><span data-ttu-id="ecebf-102">İzlenecek yol: Araç Kutusunu Otomatik Olarak Özel Bileşenlerle Doldurma</span><span class="sxs-lookup"><span data-stu-id="ecebf-102">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>

<span data-ttu-id="ecebf-103">Bileşenlerinizi açık çözümde bir proje tarafından tanımlanan, bunlar otomatik olarak görünür **araç kutusu**, sizin tarafınızdan gerekli herhangi bir işlem ile.</span><span class="sxs-lookup"><span data-stu-id="ecebf-103">If your components are defined by a project in the currently open solution, they will automatically appear in the **Toolbox**, with no action required by you.</span></span> <span data-ttu-id="ecebf-104">El ile de doldurabilirsiniz **araç kutusu** kullanarak kendi özel bileşenlerle [seçin araç kutusu öğeleri iletişim kutusu (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100)), ancak **araç kutusu** alır çözümünüzün içindeki öğelerin aşağıdaki özelliklere sahip çıkışları derleme:</span><span class="sxs-lookup"><span data-stu-id="ecebf-104">You can also manually populate the **Toolbox** with your custom components by using the [Choose Toolbox Items Dialog Box (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100)), but the **Toolbox** takes account of items in your solution's build outputs with all the following characteristics:</span></span>

- <span data-ttu-id="ecebf-105">Implements <xref:System.ComponentModel.IComponent>;</span><span class="sxs-lookup"><span data-stu-id="ecebf-105">Implements <xref:System.ComponentModel.IComponent>;</span></span>

- <span data-ttu-id="ecebf-106">Olmayan <xref:System.ComponentModel.ToolboxItemAttribute> kümesine `false`;</span><span class="sxs-lookup"><span data-stu-id="ecebf-106">Does not have <xref:System.ComponentModel.ToolboxItemAttribute> set to `false`;</span></span>

- <span data-ttu-id="ecebf-107">Olmayan <xref:System.ComponentModel.DesignTimeVisibleAttribute> kümesine `false`.</span><span class="sxs-lookup"><span data-stu-id="ecebf-107">Does not have <xref:System.ComponentModel.DesignTimeVisibleAttribute> set to `false`.</span></span>

> [!NOTE]
> <span data-ttu-id="ecebf-108">**Araç kutusu** , çözümde bir proje tarafından oluşturulmamış öğeleri görüntülenmeyecek için başvuru zincirleri izlemez.</span><span class="sxs-lookup"><span data-stu-id="ecebf-108">The **Toolbox** does not follow reference chains, so it won't display items that are not built by a project in your solution.</span></span>

<span data-ttu-id="ecebf-109">Bu izlenecek yol, nasıl özel bir bileşeni otomatik olarak görünür gösterir **araç kutusu** bileşeni derlendikten sonra.</span><span class="sxs-lookup"><span data-stu-id="ecebf-109">This walkthrough demonstrates how a custom component automatically appears in the **Toolbox** once the component is built.</span></span> <span data-ttu-id="ecebf-110">Bu kılavuzda gösterilen görevler aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="ecebf-110">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="ecebf-111">Bir Windows Forms projesi oluşturma.</span><span class="sxs-lookup"><span data-stu-id="ecebf-111">Creating a Windows Forms project.</span></span>

- <span data-ttu-id="ecebf-112">Bir özel bileşene oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="ecebf-112">Creating a custom component.</span></span>

- <span data-ttu-id="ecebf-113">Özel bir bileşeninin örneği oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="ecebf-113">Creating an instance of a custom component.</span></span>

- <span data-ttu-id="ecebf-114">Kaldırma ve bir özel bileşene yeniden yükleniyor.</span><span class="sxs-lookup"><span data-stu-id="ecebf-114">Unloading and reloading a custom component.</span></span>

<span data-ttu-id="ecebf-115">İşlemi tamamladığınızda, göreceksiniz **araç kutusu** oluşturmuş olduğunuz bir bileşeni ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="ecebf-115">When you are finished, you will see that the **Toolbox** is populated with a component that you have created.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="ecebf-116">Projeyi oluşturma</span><span class="sxs-lookup"><span data-stu-id="ecebf-116">Create the project</span></span>

1. <span data-ttu-id="ecebf-117">Visual Studio'da adlı bir Windows tabanlı uygulama projesi oluşturma `ToolboxExample` (**dosya** > **yeni** > **proje**  >  **Visual C#**  veya **Visual Basic** > **Klasik Masaüstü** > **Windows Forms Uygulama**).</span><span class="sxs-lookup"><span data-stu-id="ecebf-117">In Visual Studio, create a Windows-based application project called `ToolboxExample` (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="ecebf-118">Yeni bir bileşen projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ecebf-118">Add a new component to the project.</span></span> <span data-ttu-id="ecebf-119">Bu çağrı `DemoComponent`.</span><span class="sxs-lookup"><span data-stu-id="ecebf-119">Call it `DemoComponent`.</span></span>

     <span data-ttu-id="ecebf-120">Daha fazla bilgi için [nasıl yapılır: Yeni proje öğeleri ekleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="ecebf-120">For more information, see [How to: Add New Project Items](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100)).</span></span>

3. <span data-ttu-id="ecebf-121">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ecebf-121">Build the project.</span></span>

4. <span data-ttu-id="ecebf-122">Gelen **Araçları** menüsünde tıklatın **seçenekleri** öğesi.</span><span class="sxs-lookup"><span data-stu-id="ecebf-122">From the **Tools** menu, click the **Options** item.</span></span> <span data-ttu-id="ecebf-123">Tıklayın **genel** altında **Windows Form Tasarımcısı** emin olun ve öğe **AutoToolboxPopulate** seçeneği **True**.</span><span class="sxs-lookup"><span data-stu-id="ecebf-123">Click **General** under the **Windows Forms Designer** item and ensure that the **AutoToolboxPopulate** option is set to **True**.</span></span>

## <a name="create-an-instance-of-a-custom-component"></a><span data-ttu-id="ecebf-124">Özel bileşen örneği oluşturma</span><span class="sxs-lookup"><span data-stu-id="ecebf-124">Create an instance of a custom component</span></span>

<span data-ttu-id="ecebf-125">Sonraki adım, formda özel bileşen örneği oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="ecebf-125">The next step is to create an instance of the custom component on the form.</span></span> <span data-ttu-id="ecebf-126">Çünkü **araç kutusu** otomatik olarak hesapları yeni bileşeni için bu olarak herhangi bir bileşeni veya denetimi oluşturmak oldukça kolaydır.</span><span class="sxs-lookup"><span data-stu-id="ecebf-126">Because the **Toolbox** automatically accounts for the new component, this is as easy as creating any other component or control.</span></span>

1. <span data-ttu-id="ecebf-127">Projenin formda açın **Form Tasarımcısı**.</span><span class="sxs-lookup"><span data-stu-id="ecebf-127">Open the project's form in the **Forms Designer**.</span></span>

2. <span data-ttu-id="ecebf-128">İçinde **araç kutusu**, adlı yeni sekmesini **ToolboxExample bileşenleri**.</span><span class="sxs-lookup"><span data-stu-id="ecebf-128">In the **Toolbox**, click the new tab called **ToolboxExample Components**.</span></span>

     <span data-ttu-id="ecebf-129">Sekmesine tıklayın, sonra göreceğiniz **DemoComponent**.</span><span class="sxs-lookup"><span data-stu-id="ecebf-129">Once you click the tab, you will see **DemoComponent**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ecebf-130">Performans nedenleriyle bileşenleri otomatik olarak doldurulan alanında **araç kutusu** özel bit eşlemler, görüntüleme ve <xref:System.Drawing.ToolboxBitmapAttribute> desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="ecebf-130">For performance reasons, components in the auto-populated area of the **Toolbox** do not display custom bitmaps, and the <xref:System.Drawing.ToolboxBitmapAttribute> is not supported.</span></span> <span data-ttu-id="ecebf-131">Özel bir bileşeni için bir simge görüntülemek için **araç kutusu**, kullanın **araç kutusu öğelerini Seç** iletişim kutusu, bileşeni yüklenemiyor.</span><span class="sxs-lookup"><span data-stu-id="ecebf-131">To display an icon for a custom component in the **Toolbox**, use the **Choose Toolbox Items** dialog box to load your component.</span></span>

3. <span data-ttu-id="ecebf-132">Bileşeniniz formunuza sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="ecebf-132">Drag your component onto your form.</span></span>

     <span data-ttu-id="ecebf-133">Bileşen örneği oluşturulur ve eklenen **bileşeni Tepsi**.</span><span class="sxs-lookup"><span data-stu-id="ecebf-133">An instance of the component is created and added to the **Component Tray**.</span></span>

## <a name="unload-and-reload-a-custom-component"></a><span data-ttu-id="ecebf-134">Kaldırma ve bir özel bileşene yeniden yükleyin</span><span class="sxs-lookup"><span data-stu-id="ecebf-134">Unload and reload a custom component</span></span>

<span data-ttu-id="ecebf-135">**Araç kutusu** alır hesabı bileşenlerin her proje yüklendi ve bir proje kaldırıldığında, projenin bileşenleri başvurular kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ecebf-135">The **Toolbox** takes account of the components in each loaded project, and when a project is unloaded, it removes references to the project's components.</span></span>

1. <span data-ttu-id="ecebf-136">Çözümden proje Kaldır.</span><span class="sxs-lookup"><span data-stu-id="ecebf-136">Unload the project from the solution.</span></span>

     <span data-ttu-id="ecebf-137">Projeleri kaldırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Projeleri yeniden yükleyin ve kaldırma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/tt479x1t(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="ecebf-137">For more information about unloading projects, see [How to: Unload and Reload Projects](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/tt479x1t(v=vs.100)).</span></span> <span data-ttu-id="ecebf-138">Kaydetmeniz istenirse seçin **Evet**.</span><span class="sxs-lookup"><span data-stu-id="ecebf-138">If you are prompted to save, choose **Yes**.</span></span>

2. <span data-ttu-id="ecebf-139">Yeni bir **Windows uygulama** çözüme bir proje.</span><span class="sxs-lookup"><span data-stu-id="ecebf-139">Add a new **Windows Application** project to the solution.</span></span> <span data-ttu-id="ecebf-140">Formda açın **Tasarımcısı**.</span><span class="sxs-lookup"><span data-stu-id="ecebf-140">Open the form in the **Designer**.</span></span>

     <span data-ttu-id="ecebf-141">**ToolboxExample bileşenleri** , artık önceki projeyi sekmesinden kaybolur.</span><span class="sxs-lookup"><span data-stu-id="ecebf-141">The **ToolboxExample Components** tab from the previous project is now gone.</span></span>

3. <span data-ttu-id="ecebf-142">Reload `ToolboxExample` proje.</span><span class="sxs-lookup"><span data-stu-id="ecebf-142">Reload the `ToolboxExample` project.</span></span>

     <span data-ttu-id="ecebf-143">**ToolboxExample bileşenleri** sekmesinde artık yeniden görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ecebf-143">The **ToolboxExample Components** tab now reappears.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ecebf-144">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="ecebf-144">Next steps</span></span>

<span data-ttu-id="ecebf-145">Bu izlenecek yol gösteren **araç kutusu** projenin bileşenlerinin alır ancak **araç kutusu** ayrıca alır denetimleri hesabıdır.</span><span class="sxs-lookup"><span data-stu-id="ecebf-145">This walkthrough demonstrates that the **Toolbox** takes account of a project's components, but the **Toolbox** is also takes account of controls.</span></span> <span data-ttu-id="ecebf-146">İle kendi özel denetimler ekleyerek ve çözümünüze ait denetim projeleri kaldırma denemeler yapın.</span><span class="sxs-lookup"><span data-stu-id="ecebf-146">Experiment with your own custom controls by adding and removing control projects from your solution.</span></span>

## <a name="see-also"></a><span data-ttu-id="ecebf-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ecebf-147">See also</span></span>

- <span data-ttu-id="ecebf-148">[Genel, Windows Form Tasarımcısı, Seçenekler iletişim kutusu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/5aazxs78(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ecebf-148">[General, Windows Forms Designer, Options Dialog Box](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/5aazxs78(v=vs.100))</span></span>
- <span data-ttu-id="ecebf-149">[Nasıl yapılır: Araç kutusu sekmeleri düzenleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/66kwe227(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ecebf-149">[How to: Manipulate Toolbox Tabs](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/66kwe227(v=vs.100))</span></span>
- <span data-ttu-id="ecebf-150">[Araç kutusu öğelerini Seç iletişim kutusu (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ecebf-150">[Choose Toolbox Items Dialog Box (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100))</span></span>
- [<span data-ttu-id="ecebf-151">Windows Forms’a Denetimler Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="ecebf-151">Putting Controls on Windows Forms</span></span>](putting-controls-on-windows-forms.md)
