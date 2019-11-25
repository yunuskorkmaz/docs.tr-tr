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
ms.openlocfilehash: 94d175ec58f35b7e807786c221437d05c605c0bc
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974222"
---
# <a name="walkthrough-mapping-properties-using-the-windowsformshost-element"></a><span data-ttu-id="b162e-102">İzlenecek yol: WindowsFormsHost Öğesi Kullanarak Özellikleri Eşleme</span><span class="sxs-lookup"><span data-stu-id="b162e-102">Walkthrough: Mapping Properties Using the WindowsFormsHost Element</span></span>

<span data-ttu-id="b162e-103">Bu izlenecek yol, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özelliklerini barındırılan bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimindeki ilgili özelliklerle eşlemek için <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> özelliğini nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="b162e-103">This walkthrough shows you how to use the <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> property to map [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties to corresponding properties on a hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>

<span data-ttu-id="b162e-104">Bu izlenecek yolda gösterilen görevler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b162e-104">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="b162e-105">Proje oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="b162e-105">Creating the project.</span></span>

- <span data-ttu-id="b162e-106">Uygulama yerleşimini tanımlama.</span><span class="sxs-lookup"><span data-stu-id="b162e-106">Defining the application layout.</span></span>

- <span data-ttu-id="b162e-107">Yeni özellik eşlemesi tanımlama.</span><span class="sxs-lookup"><span data-stu-id="b162e-107">Defining a new property mapping.</span></span>

- <span data-ttu-id="b162e-108">Varsayılan özellik eşlemesi kaldırılıyor.</span><span class="sxs-lookup"><span data-stu-id="b162e-108">Removing a default property mapping.</span></span>

- <span data-ttu-id="b162e-109">Varsayılan özellik eşlemesini değiştirme.</span><span class="sxs-lookup"><span data-stu-id="b162e-109">Replacing a default property mapping.</span></span>

- <span data-ttu-id="b162e-110">Varsayılan özellik eşlemesini genişletme.</span><span class="sxs-lookup"><span data-stu-id="b162e-110">Extending a default property mapping.</span></span>

<span data-ttu-id="b162e-111">Bu kılavuzda gösterilen görevlerin tüm kod listesi için bkz. [WindowsFormsHost öğesi örneği kullanılarak özellikleri eşleme](https://go.microsoft.com/fwlink/?LinkID=160019).</span><span class="sxs-lookup"><span data-stu-id="b162e-111">For a complete code listing of the tasks illustrated in this walkthrough, see [Mapping Properties Using the WindowsFormsHost Element Sample](https://go.microsoft.com/fwlink/?LinkID=160019).</span></span>

<span data-ttu-id="b162e-112">İşiniz bittiğinde, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özelliklerini barındırılan bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimindeki ilgili özelliklerle eşleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b162e-112">When you are finished, you will be able to map [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties to corresponding properties on a hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b162e-113">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="b162e-113">Prerequisites</span></span>

<span data-ttu-id="b162e-114">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="b162e-114">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="b162e-115">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="b162e-115">Visual Studio 2017</span></span>

## <a name="create-and-set-up-the-project"></a><span data-ttu-id="b162e-116">Projeyi oluşturma ve ayarlama</span><span class="sxs-lookup"><span data-stu-id="b162e-116">Create and set up the project</span></span>

1. <span data-ttu-id="b162e-117">`PropertyMappingWithWfhSample`adlı bir **WPF uygulaması** projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b162e-117">Create a **WPF App** project named `PropertyMappingWithWfhSample`.</span></span>

2. <span data-ttu-id="b162e-118">**Çözüm Gezgini**' de, WindowsFormsIntegration. dll adlı WindowsFormsIntegration derlemesine bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b162e-118">In **Solution Explorer**, add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>

3. <span data-ttu-id="b162e-119">**Çözüm Gezgini**, System. Drawing ve System. Windows. Forms derlemelerine başvuruları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b162e-119">In **Solution Explorer**, add references to the System.Drawing and System.Windows.Forms assemblies.</span></span>

## <a name="defining-the-application-layout"></a><span data-ttu-id="b162e-120">Uygulama yerleşimini tanımlama</span><span class="sxs-lookup"><span data-stu-id="b162e-120">Defining the Application Layout</span></span>

<span data-ttu-id="b162e-121">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]tabanlı uygulama bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimini barındırmak için <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="b162e-121">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application uses the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element to host a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>

### <a name="to-define-the-application-layout"></a><span data-ttu-id="b162e-122">Uygulama yerleşimini tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="b162e-122">To define the application layout</span></span>

1. <span data-ttu-id="b162e-123">WPF Tasarımcısında Window1. xaml ' i açın.</span><span class="sxs-lookup"><span data-stu-id="b162e-123">Open Window1.xaml in the WPF Designer.</span></span>

2. <span data-ttu-id="b162e-124">Mevcut kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b162e-124">Replace the existing code with the following code.</span></span>

     [!code-xaml[PropertyMappingWithWfhSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml#1)]

3. <span data-ttu-id="b162e-125">Kod düzenleyicisinde Window1.xaml.cs öğesini açın.</span><span class="sxs-lookup"><span data-stu-id="b162e-125">Open Window1.xaml.cs in the Code Editor.</span></span>

4. <span data-ttu-id="b162e-126">Dosyanın en üstüne aşağıdaki ad alanlarını içeri aktarın.</span><span class="sxs-lookup"><span data-stu-id="b162e-126">At the top of the file, import the following namespaces.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#20](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#20)]
     [!code-vb[PropertyMappingWithWfhSample#20](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#20)]

## <a name="defining-a-new-property-mapping"></a><span data-ttu-id="b162e-127">Yeni özellik eşlemesi tanımlama</span><span class="sxs-lookup"><span data-stu-id="b162e-127">Defining a New Property Mapping</span></span>

<span data-ttu-id="b162e-128"><xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi, çeşitli varsayılan özellik eşlemeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b162e-128">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element provides several default property mappings.</span></span> <span data-ttu-id="b162e-129"><xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesinin <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A><xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> yöntemini çağırarak yeni bir özellik eşlemesi eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="b162e-129">You add a new property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>

### <a name="to-define-a-new-property-mapping"></a><span data-ttu-id="b162e-130">Yeni bir özellik eşlemesi tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="b162e-130">To define a new property mapping</span></span>

- <span data-ttu-id="b162e-131">Aşağıdaki kodu `Window1` sınıfının tanımına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="b162e-131">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#14)]
     [!code-vb[PropertyMappingWithWfhSample#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#14)]

     <span data-ttu-id="b162e-132">`AddClipMapping` yöntemi <xref:System.Windows.UIElement.Clip%2A> özelliği için yeni bir eşleme ekler.</span><span class="sxs-lookup"><span data-stu-id="b162e-132">The `AddClipMapping` method adds a new mapping for the <xref:System.Windows.UIElement.Clip%2A> property.</span></span>

     <span data-ttu-id="b162e-133">`OnClipChange` yöntemi, <xref:System.Windows.UIElement.Clip%2A> özelliğini [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.Region%2A> özelliğine çevirir.</span><span class="sxs-lookup"><span data-stu-id="b162e-133">The `OnClipChange` method translates the <xref:System.Windows.UIElement.Clip%2A> property to the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.Region%2A> property.</span></span>

     <span data-ttu-id="b162e-134">`Window1_SizeChanged` yöntemi pencerenin <xref:System.Windows.FrameworkElement.SizeChanged> olayını işler ve kırpma bölgesini uygulama penceresine uyacak şekilde boyutlandırır.</span><span class="sxs-lookup"><span data-stu-id="b162e-134">The `Window1_SizeChanged` method handles the window's <xref:System.Windows.FrameworkElement.SizeChanged> event and sizes the clipping region to fit the application window.</span></span>

## <a name="removing-a-default-property-mapping"></a><span data-ttu-id="b162e-135">Varsayılan özellik eşlemesini kaldırma</span><span class="sxs-lookup"><span data-stu-id="b162e-135">Removing a Default Property Mapping</span></span>

<span data-ttu-id="b162e-136"><xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesinin <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A><xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> yöntemini çağırarak varsayılan özellik eşlemesini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="b162e-136">Remove a default property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>

### <a name="to-remove-a-default-property-mapping"></a><span data-ttu-id="b162e-137">Varsayılan özellik eşlemesini kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="b162e-137">To remove a default property mapping</span></span>

- <span data-ttu-id="b162e-138">Aşağıdaki kodu `Window1` sınıfının tanımına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="b162e-138">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#13](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#13)]
     [!code-vb[PropertyMappingWithWfhSample#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#13)]

     <span data-ttu-id="b162e-139">`RemoveCursorMapping` yöntemi <xref:System.Windows.FrameworkElement.Cursor%2A> özelliğinin varsayılan eşlemesini siler.</span><span class="sxs-lookup"><span data-stu-id="b162e-139">The `RemoveCursorMapping` method deletes the default mapping for the <xref:System.Windows.FrameworkElement.Cursor%2A> property.</span></span>

## <a name="replacing-a-default-property-mapping"></a><span data-ttu-id="b162e-140">Varsayılan özellik eşlemesini değiştirme</span><span class="sxs-lookup"><span data-stu-id="b162e-140">Replacing a Default Property Mapping</span></span>

<span data-ttu-id="b162e-141">Varsayılan eşlemeyi kaldırarak ve <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesinin <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A><xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> yöntemi çağırarak varsayılan özellik eşlemesini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b162e-141">Replace a default property mapping by removing the default mapping and calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>

### <a name="to-replace-a-default-property-mapping"></a><span data-ttu-id="b162e-142">Varsayılan bir özellik eşlemesini değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="b162e-142">To replace a default property mapping</span></span>

- <span data-ttu-id="b162e-143">Aşağıdaki kodu `Window1` sınıfının tanımına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="b162e-143">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#12](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#12)]
     [!code-vb[PropertyMappingWithWfhSample#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#12)]

     <span data-ttu-id="b162e-144">`ReplaceFlowDirectionMapping` yöntemi <xref:System.Windows.FrameworkElement.FlowDirection%2A> özelliğinin varsayılan eşlemesinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="b162e-144">The `ReplaceFlowDirectionMapping` method replaces the default mapping for the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property.</span></span>

     <span data-ttu-id="b162e-145">`OnFlowDirectionChange` yöntemi, <xref:System.Windows.FrameworkElement.FlowDirection%2A> özelliğini [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.RightToLeft%2A> özelliğine çevirir.</span><span class="sxs-lookup"><span data-stu-id="b162e-145">The `OnFlowDirectionChange` method translates the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property to the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.RightToLeft%2A> property.</span></span>

     <span data-ttu-id="b162e-146">`cb_CheckedChanged` yöntemi <xref:System.Windows.Forms.CheckBox> denetimindeki <xref:System.Windows.Forms.CheckBox.CheckedChanged> olayını işler.</span><span class="sxs-lookup"><span data-stu-id="b162e-146">The `cb_CheckedChanged` method handles the <xref:System.Windows.Forms.CheckBox.CheckedChanged> event on the <xref:System.Windows.Forms.CheckBox> control.</span></span> <span data-ttu-id="b162e-147"><xref:System.Windows.Forms.CheckBox.CheckState%2A> özelliğinin değerine göre <xref:System.Windows.FrameworkElement.FlowDirection%2A> özelliğini atar</span><span class="sxs-lookup"><span data-stu-id="b162e-147">It assigns the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property based on the value of the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property</span></span>

## <a name="extending-a-default-property-mapping"></a><span data-ttu-id="b162e-148">Varsayılan özellik eşlemesini genişletme</span><span class="sxs-lookup"><span data-stu-id="b162e-148">Extending a Default Property Mapping</span></span>

<span data-ttu-id="b162e-149">Varsayılan bir özellik eşlemesini kullanabilir ve ayrıca kendi eşlemesiyle genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b162e-149">You can use a default property mapping and also extend it with your own mapping.</span></span>

### <a name="to-extend-a-default-property-mapping"></a><span data-ttu-id="b162e-150">Varsayılan bir özellik eşlemesini genişletmek için</span><span class="sxs-lookup"><span data-stu-id="b162e-150">To extend a default property mapping</span></span>

- <span data-ttu-id="b162e-151">Aşağıdaki kodu `Window1` sınıfının tanımına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="b162e-151">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#15)]
     [!code-vb[PropertyMappingWithWfhSample#15](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#15)]

     <span data-ttu-id="b162e-152">`ExtendBackgroundMapping` yöntemi, varolan <xref:System.Windows.Controls.Control.Background%2A> özellik eşlemesine özel bir özellik Çeviricisi ekler.</span><span class="sxs-lookup"><span data-stu-id="b162e-152">The `ExtendBackgroundMapping` method adds a custom property translator to the existing <xref:System.Windows.Controls.Control.Background%2A> property mapping.</span></span>

     <span data-ttu-id="b162e-153">`OnBackgroundChange` yöntemi, barındırılan denetimin <xref:System.Windows.Forms.Control.BackgroundImage%2A> özelliğine belirli bir görüntü atar.</span><span class="sxs-lookup"><span data-stu-id="b162e-153">The `OnBackgroundChange` method assigns a specific image to the hosted control's <xref:System.Windows.Forms.Control.BackgroundImage%2A> property.</span></span> <span data-ttu-id="b162e-154">`OnBackgroundChange` yöntemi, varsayılan özellik eşleme uygulandıktan sonra çağrılır.</span><span class="sxs-lookup"><span data-stu-id="b162e-154">The `OnBackgroundChange` method is called after the default property mapping is applied.</span></span>

## <a name="initializing-your-property-mappings"></a><span data-ttu-id="b162e-155">Özellik Eşlemelerinizi Başlatma</span><span class="sxs-lookup"><span data-stu-id="b162e-155">Initializing Your Property Mappings</span></span>

<span data-ttu-id="b162e-156">Daha önce açıklanan yöntemleri <xref:System.Windows.FrameworkElement.Loaded> olay işleyicisinde çağırarak özellik eşlemelerinizi ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b162e-156">Set up your property mappings by calling the previously described methods in the <xref:System.Windows.FrameworkElement.Loaded> event handler.</span></span>

### <a name="to-initialize-your-property-mappings"></a><span data-ttu-id="b162e-157">Özellik Eşlemelerinizi başlatmak için</span><span class="sxs-lookup"><span data-stu-id="b162e-157">To initialize your property mappings</span></span>

1. <span data-ttu-id="b162e-158">Aşağıdaki kodu `Window1` sınıfının tanımına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="b162e-158">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#11](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#11)]
     [!code-vb[PropertyMappingWithWfhSample#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#11)]

     <span data-ttu-id="b162e-159">`WindowLoaded` yöntemi <xref:System.Windows.FrameworkElement.Loaded> olayını işler ve aşağıdaki başlatmayı gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="b162e-159">The `WindowLoaded` method handles the <xref:System.Windows.FrameworkElement.Loaded> event and performs the following initialization.</span></span>

    - <span data-ttu-id="b162e-160">Bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.CheckBox> denetimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b162e-160">Creates a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.CheckBox> control.</span></span>

    - <span data-ttu-id="b162e-161">Özellik eşlemelerini ayarlamak için izlenecek yolda daha önce tanımladığınız yöntemleri çağırır.</span><span class="sxs-lookup"><span data-stu-id="b162e-161">Calls the methods you defined earlier in the walkthrough to set up the property mappings.</span></span>

    - <span data-ttu-id="b162e-162">Eşlenen özelliklere ilk değerleri atar.</span><span class="sxs-lookup"><span data-stu-id="b162e-162">Assigns initial values to the mapped properties.</span></span>

2. <span data-ttu-id="b162e-163">Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="b162e-163">Press **F5** to build and run the application.</span></span> <span data-ttu-id="b162e-164"><xref:System.Windows.FrameworkElement.FlowDirection%2A> eşlemenin etkisini görmek için onay kutusuna tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b162e-164">Click the check box to see the effect of the <xref:System.Windows.FrameworkElement.FlowDirection%2A> mapping.</span></span> <span data-ttu-id="b162e-165">Onay kutusuna tıkladığınızda, düzen sol sağ yönünü tersine çevirir.</span><span class="sxs-lookup"><span data-stu-id="b162e-165">When you click the check box, the layout reverses its left-right orientation.</span></span>

## <a name="see-also"></a><span data-ttu-id="b162e-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b162e-166">See also</span></span>

- <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="b162e-167">Windows Forms ve WPF Özelliğini Eşleme</span><span class="sxs-lookup"><span data-stu-id="b162e-167">Windows Forms and WPF Property Mapping</span></span>](windows-forms-and-wpf-property-mapping.md)
- [<span data-ttu-id="b162e-168">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="b162e-168">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="b162e-169">İzlenecek yol: WPF'de Windows Forms Denetimini Barındırma</span><span class="sxs-lookup"><span data-stu-id="b162e-169">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
