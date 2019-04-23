---
title: 'İzlenecek yol: WindowsFormsHost Öğesi Kullanarak Özellikleri Eşleme'
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- WindowsFormsHost element property mapping [WPF]
ms.assetid: 74809167-bf8e-48b7-a2e7-b4ea08bc7d8c
ms.openlocfilehash: edd9d6f698ba27cacb5e9a5eecab43f58d47b8e1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59296530"
---
# <a name="walkthrough-mapping-properties-using-the-windowsformshost-element"></a><span data-ttu-id="c7d28-102">İzlenecek yol: WindowsFormsHost Öğesi Kullanarak Özellikleri Eşleme</span><span class="sxs-lookup"><span data-stu-id="c7d28-102">Walkthrough: Mapping Properties Using the WindowsFormsHost Element</span></span>

<span data-ttu-id="c7d28-103">Bu izlenecek yol size nasıl kullanılacağını gösterir <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> eşlemek için özellik [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] barındırılan karşılık gelen özelliklere özellikleri [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi.</span><span class="sxs-lookup"><span data-stu-id="c7d28-103">This walkthrough shows you how to use the <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> property to map [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties to corresponding properties on a hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>

<span data-ttu-id="c7d28-104">Bu kılavuzda gösterilen görevler aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="c7d28-104">Tasks illustrated in this walkthrough include:</span></span>

-   <span data-ttu-id="c7d28-105">Proje oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="c7d28-105">Creating the project.</span></span>

-   <span data-ttu-id="c7d28-106">Uygulama düzenini tanımlama.</span><span class="sxs-lookup"><span data-stu-id="c7d28-106">Defining the application layout.</span></span>

-   <span data-ttu-id="c7d28-107">Yeni bir özellik eşlemesi tanımlama.</span><span class="sxs-lookup"><span data-stu-id="c7d28-107">Defining a new property mapping.</span></span>

-   <span data-ttu-id="c7d28-108">Varsayılan özellik eşlemesi kaldırılıyor.</span><span class="sxs-lookup"><span data-stu-id="c7d28-108">Removing a default property mapping.</span></span>

-   <span data-ttu-id="c7d28-109">Varsayılan özellik eşlemesi değiştiriliyor.</span><span class="sxs-lookup"><span data-stu-id="c7d28-109">Replacing a default property mapping.</span></span>

-   <span data-ttu-id="c7d28-110">Varsayılan özellik eşlemesi genişletme.</span><span class="sxs-lookup"><span data-stu-id="c7d28-110">Extending a default property mapping.</span></span>

<span data-ttu-id="c7d28-111">Bu izlenecek yolda gösterilen görevler tam kod listesi için bkz. [WindowsFormsHost öğesi örneği kullanarak eşleme özelliklerini](https://go.microsoft.com/fwlink/?LinkID=160019).</span><span class="sxs-lookup"><span data-stu-id="c7d28-111">For a complete code listing of the tasks illustrated in this walkthrough, see [Mapping Properties Using the WindowsFormsHost Element Sample](https://go.microsoft.com/fwlink/?LinkID=160019).</span></span>

<span data-ttu-id="c7d28-112">Bitirdiğiniz zaman, eşlemek mümkün olmayacak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] barındırılan karşılık gelen özelliklere özellikleri [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi.</span><span class="sxs-lookup"><span data-stu-id="c7d28-112">When you are finished, you will be able to map [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties to corresponding properties on a hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c7d28-113">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="c7d28-113">Prerequisites</span></span>

<span data-ttu-id="c7d28-114">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="c7d28-114">You need the following components to complete this walkthrough:</span></span>

-   <span data-ttu-id="c7d28-115">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="c7d28-115">Visual Studio 2017</span></span>

## <a name="create-and-set-up-the-project"></a><span data-ttu-id="c7d28-116">Oluşturma ve projesi kurun</span><span class="sxs-lookup"><span data-stu-id="c7d28-116">Create and set up the project</span></span>

1. <span data-ttu-id="c7d28-117">Oluşturma bir **WPF uygulaması** adlı proje `PropertyMappingWithWfhSample`.</span><span class="sxs-lookup"><span data-stu-id="c7d28-117">Create a **WPF App** project named `PropertyMappingWithWfhSample`.</span></span>

2. <span data-ttu-id="c7d28-118">İçinde **Çözüm Gezgini**, WindowsFormsIntegration.dll adlı WindowsFormsIntegration derlemesine bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c7d28-118">In **Solution Explorer**, add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>

3. <span data-ttu-id="c7d28-119">İçinde **Çözüm Gezgini**, System.Drawing ve System.Windows.Forms öğelerini derlemelere başvurular ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c7d28-119">In **Solution Explorer**, add references to the System.Drawing and System.Windows.Forms assemblies.</span></span>

## <a name="defining-the-application-layout"></a><span data-ttu-id="c7d28-120">Uygulama düzenini tanımlama</span><span class="sxs-lookup"><span data-stu-id="c7d28-120">Defining the Application Layout</span></span>

<span data-ttu-id="c7d28-121">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-Uygulamanız tarafından kullanılan temel <xref:System.Windows.Forms.Integration.WindowsFormsHost> ana öğesine bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi.</span><span class="sxs-lookup"><span data-stu-id="c7d28-121">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application uses the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element to host a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>

### <a name="to-define-the-application-layout"></a><span data-ttu-id="c7d28-122">Uygulama düzenini tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="c7d28-122">To define the application layout</span></span>

1. <span data-ttu-id="c7d28-123">Window1.XAML içinde açın [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c7d28-123">Open Window1.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>

2. <span data-ttu-id="c7d28-124">Varolan kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c7d28-124">Replace the existing code with the following code.</span></span>

     [!code-xaml[PropertyMappingWithWfhSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml#1)]

3. <span data-ttu-id="c7d28-125">Window1.xaml.cs Kod Düzenleyicisi'nde açın.</span><span class="sxs-lookup"><span data-stu-id="c7d28-125">Open Window1.xaml.cs in the Code Editor.</span></span>

4. <span data-ttu-id="c7d28-126">Dosyasının en üstüne aşağıdaki ad alanlarını içeri aktarın.</span><span class="sxs-lookup"><span data-stu-id="c7d28-126">At the top of the file, import the following namespaces.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#20](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#20)]
     [!code-vb[PropertyMappingWithWfhSample#20](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#20)]

## <a name="defining-a-new-property-mapping"></a><span data-ttu-id="c7d28-127">Yeni bir özellik eşlemesi tanımlama</span><span class="sxs-lookup"><span data-stu-id="c7d28-127">Defining a New Property Mapping</span></span>

<span data-ttu-id="c7d28-128"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğe birkaç varsayılan özellik eşlemeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c7d28-128">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element provides several default property mappings.</span></span> <span data-ttu-id="c7d28-129">Çağırarak yeni bir özellik eşlemesi Ekle <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> metodunda <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğenin <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span><span class="sxs-lookup"><span data-stu-id="c7d28-129">You add a new property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>

### <a name="to-define-a-new-property-mapping"></a><span data-ttu-id="c7d28-130">Yeni bir özellik eşlemesi tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="c7d28-130">To define a new property mapping</span></span>

-   <span data-ttu-id="c7d28-131">Tanımı aşağıdaki kodu kopyalayarak `Window1` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c7d28-131">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#14)]
     [!code-vb[PropertyMappingWithWfhSample#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#14)]

     <span data-ttu-id="c7d28-132">`AddClipMapping` Yöntemi ekler için yeni bir eşleme <xref:System.Windows.UIElement.Clip%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="c7d28-132">The `AddClipMapping` method adds a new mapping for the <xref:System.Windows.UIElement.Clip%2A> property.</span></span>

     <span data-ttu-id="c7d28-133">`OnClipChange` Yöntemi çevirir <xref:System.Windows.UIElement.Clip%2A> özelliğini [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Control.Region%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="c7d28-133">The `OnClipChange` method translates the <xref:System.Windows.UIElement.Clip%2A> property to the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.Region%2A> property.</span></span>

     <span data-ttu-id="c7d28-134">`Window1_SizeChanged` Yöntemi işler pencerenin <xref:System.Windows.FrameworkElement.SizeChanged> olay ve uygulama penceresine sığacak şekilde kırpma bölgesini boyutları.</span><span class="sxs-lookup"><span data-stu-id="c7d28-134">The `Window1_SizeChanged` method handles the window's <xref:System.Windows.FrameworkElement.SizeChanged> event and sizes the clipping region to fit the application window.</span></span>

## <a name="removing-a-default-property-mapping"></a><span data-ttu-id="c7d28-135">Varsayılan özellik eşlemesi kaldırılıyor</span><span class="sxs-lookup"><span data-stu-id="c7d28-135">Removing a Default Property Mapping</span></span>

<span data-ttu-id="c7d28-136">Çağırarak varsayılan özellik eşlemesini kaldırma <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> metodunda <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğenin <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span><span class="sxs-lookup"><span data-stu-id="c7d28-136">Remove a default property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>

### <a name="to-remove-a-default-property-mapping"></a><span data-ttu-id="c7d28-137">Varsayılan özellik eşlemesini kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="c7d28-137">To remove a default property mapping</span></span>

-   <span data-ttu-id="c7d28-138">Tanımı aşağıdaki kodu kopyalayarak `Window1` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c7d28-138">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#13](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#13)]
     [!code-vb[PropertyMappingWithWfhSample#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#13)]

     <span data-ttu-id="c7d28-139">`RemoveCursorMapping` Yöntemi için varsayılan eşlemeyi siler <xref:System.Windows.FrameworkElement.Cursor%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="c7d28-139">The `RemoveCursorMapping` method deletes the default mapping for the <xref:System.Windows.FrameworkElement.Cursor%2A> property.</span></span>

## <a name="replacing-a-default-property-mapping"></a><span data-ttu-id="c7d28-140">Varsayılan özellik eşlemesi değiştiriliyor</span><span class="sxs-lookup"><span data-stu-id="c7d28-140">Replacing a Default Property Mapping</span></span>

<span data-ttu-id="c7d28-141">Varsayılan eşleme ve arama kaldırarak bir varsayılan özellik eşlemesini değiştirmek <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> metodunda <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğenin <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span><span class="sxs-lookup"><span data-stu-id="c7d28-141">Replace a default property mapping by removing the default mapping and calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>

### <a name="to-replace-a-default-property-mapping"></a><span data-ttu-id="c7d28-142">Varsayılan özellik eşlemesini değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="c7d28-142">To replace a default property mapping</span></span>

-   <span data-ttu-id="c7d28-143">Tanımı aşağıdaki kodu kopyalayarak `Window1` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c7d28-143">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#12](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#12)]
     [!code-vb[PropertyMappingWithWfhSample#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#12)]

     <span data-ttu-id="c7d28-144">`ReplaceFlowDirectionMapping` Yöntemi için varsayılan eşlemeyi değiştirir <xref:System.Windows.FrameworkElement.FlowDirection%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="c7d28-144">The `ReplaceFlowDirectionMapping` method replaces the default mapping for the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property.</span></span>

     <span data-ttu-id="c7d28-145">`OnFlowDirectionChange` Yöntemi çevirir <xref:System.Windows.FrameworkElement.FlowDirection%2A> özelliğini [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Control.RightToLeft%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="c7d28-145">The `OnFlowDirectionChange` method translates the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property to the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.RightToLeft%2A> property.</span></span>

     <span data-ttu-id="c7d28-146">`cb_CheckedChanged` Yöntemi tanıtıcıları <xref:System.Windows.Forms.CheckBox.CheckedChanged> olayda <xref:System.Windows.Forms.CheckBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="c7d28-146">The `cb_CheckedChanged` method handles the <xref:System.Windows.Forms.CheckBox.CheckedChanged> event on the <xref:System.Windows.Forms.CheckBox> control.</span></span> <span data-ttu-id="c7d28-147">Buna atar <xref:System.Windows.FrameworkElement.FlowDirection%2A> özellik değerini temel alarak <xref:System.Windows.Forms.CheckBox.CheckState%2A> özelliği</span><span class="sxs-lookup"><span data-stu-id="c7d28-147">It assigns the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property based on the value of the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property</span></span>

## <a name="extending-a-default-property-mapping"></a><span data-ttu-id="c7d28-148">Varsayılan özellik eşlemesi genişletme</span><span class="sxs-lookup"><span data-stu-id="c7d28-148">Extending a Default Property Mapping</span></span>

<span data-ttu-id="c7d28-149">Varsayılan özellik eşlemesini ve ayrıca kendi eşleme ile genişletmek kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7d28-149">You can use a default property mapping and also extend it with your own mapping.</span></span>

### <a name="to-extend-a-default-property-mapping"></a><span data-ttu-id="c7d28-150">Varsayılan özellik eşlemesi genişletmek için</span><span class="sxs-lookup"><span data-stu-id="c7d28-150">To extend a default property mapping</span></span>

-   <span data-ttu-id="c7d28-151">Tanımı aşağıdaki kodu kopyalayarak `Window1` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c7d28-151">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#15)]
     [!code-vb[PropertyMappingWithWfhSample#15](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#15)]

     <span data-ttu-id="c7d28-152">`ExtendBackgroundMapping` Yöntemi, varolan bir özel özellik translator ekler <xref:System.Windows.Controls.Control.Background%2A> özellik eşlemesi.</span><span class="sxs-lookup"><span data-stu-id="c7d28-152">The `ExtendBackgroundMapping` method adds a custom property translator to the existing <xref:System.Windows.Controls.Control.Background%2A> property mapping.</span></span>

     <span data-ttu-id="c7d28-153">`OnBackgroundChange` Yöntemi barındırılan denetim için belirli bir görüntünün atar <xref:System.Windows.Forms.Control.BackgroundImage%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="c7d28-153">The `OnBackgroundChange` method assigns a specific image to the hosted control's <xref:System.Windows.Forms.Control.BackgroundImage%2A> property.</span></span> <span data-ttu-id="c7d28-154">`OnBackgroundChange` Yöntemi, varsayılan özellik eşlemesi uygulandıktan sonra çağrılır.</span><span class="sxs-lookup"><span data-stu-id="c7d28-154">The `OnBackgroundChange` method is called after the default property mapping is applied.</span></span>

## <a name="initializing-your-property-mappings"></a><span data-ttu-id="c7d28-155">Özellik eşlemelerinizin başlatılıyor</span><span class="sxs-lookup"><span data-stu-id="c7d28-155">Initializing Your Property Mappings</span></span>

<span data-ttu-id="c7d28-156">Özelliği daha önce açıklandığı gibi yöntemleri çağırarak eşlemelerinizi <xref:System.Windows.FrameworkElement.Loaded> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="c7d28-156">Set up your property mappings by calling the previously described methods in the <xref:System.Windows.FrameworkElement.Loaded> event handler.</span></span>

### <a name="to-initialize-your-property-mappings"></a><span data-ttu-id="c7d28-157">Özellik eşlemelerinizin başlatmak için</span><span class="sxs-lookup"><span data-stu-id="c7d28-157">To initialize your property mappings</span></span>

1. <span data-ttu-id="c7d28-158">Tanımı aşağıdaki kodu kopyalayarak `Window1` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c7d28-158">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#11](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#11)]
     [!code-vb[PropertyMappingWithWfhSample#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#11)]

     <span data-ttu-id="c7d28-159">`WindowLoaded` Yöntemi tanıtıcıları <xref:System.Windows.FrameworkElement.Loaded> olay ve aşağıdaki başlatmaya gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="c7d28-159">The `WindowLoaded` method handles the <xref:System.Windows.FrameworkElement.Loaded> event and performs the following initialization.</span></span>

    -   <span data-ttu-id="c7d28-160">Oluşturur bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.CheckBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="c7d28-160">Creates a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.CheckBox> control.</span></span>

    -   <span data-ttu-id="c7d28-161">Özellik eşlemelerini ayarlamak için daha önce izlenecek içinde tanımlanan yöntemleri çağırır.</span><span class="sxs-lookup"><span data-stu-id="c7d28-161">Calls the methods you defined earlier in the walkthrough to set up the property mappings.</span></span>

    -   <span data-ttu-id="c7d28-162">Eşlenen özelliklere başlangıç değerleri atar.</span><span class="sxs-lookup"><span data-stu-id="c7d28-162">Assigns initial values to the mapped properties.</span></span>

2. <span data-ttu-id="c7d28-163">Tuşuna **F5** oluşturun ve uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c7d28-163">Press **F5** to build and run the application.</span></span> <span data-ttu-id="c7d28-164">Etkisini görmek için bu onay kutusuna tıklayın <xref:System.Windows.FrameworkElement.FlowDirection%2A> eşleme.</span><span class="sxs-lookup"><span data-stu-id="c7d28-164">Click the check box to see the effect of the <xref:System.Windows.FrameworkElement.FlowDirection%2A> mapping.</span></span> <span data-ttu-id="c7d28-165">Düzen onay kutusuna tıklayın, soldan sağa yönünü tersine çevirir.</span><span class="sxs-lookup"><span data-stu-id="c7d28-165">When you click the check box, the layout reverses its left-right orientation.</span></span>

## <a name="see-also"></a><span data-ttu-id="c7d28-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7d28-166">See also</span></span>

- <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="c7d28-167">Windows Forms ve WPF Özelliğini Eşleme</span><span class="sxs-lookup"><span data-stu-id="c7d28-167">Windows Forms and WPF Property Mapping</span></span>](windows-forms-and-wpf-property-mapping.md)
- [<span data-ttu-id="c7d28-168">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="c7d28-168">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="c7d28-169">İzlenecek yol: WPF'de Windows Forms denetimini barındırma</span><span class="sxs-lookup"><span data-stu-id="c7d28-169">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf.md)