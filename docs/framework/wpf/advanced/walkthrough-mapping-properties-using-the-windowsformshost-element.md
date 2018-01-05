---
title: "İzlenecek yol: WindowsFormsHost Öğesi Kullanarak Özellikleri Eşleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- WindowsFormsHost element property mapping [WPF]
ms.assetid: 74809167-bf8e-48b7-a2e7-b4ea08bc7d8c
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 612d4a78f2f18824e5859604dc40e66b99e68586
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-mapping-properties-using-the-windowsformshost-element"></a><span data-ttu-id="bb990-102">İzlenecek yol: WindowsFormsHost Öğesi Kullanarak Özellikleri Eşleme</span><span class="sxs-lookup"><span data-stu-id="bb990-102">Walkthrough: Mapping Properties Using the WindowsFormsHost Element</span></span>
<span data-ttu-id="bb990-103">Bu kılavuz size nasıl kullanılacağını gösterir <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> eşlemek için özellik [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellikleri barındırılan karşılık gelen özelliklere [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetim.</span><span class="sxs-lookup"><span data-stu-id="bb990-103">This walkthrough shows you how to use the <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> property to map [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties to corresponding properties on a hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>  
  
 <span data-ttu-id="bb990-104">Bu örneklerde gösterilen görevler aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="bb990-104">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="bb990-105">Projeyi oluşturma.</span><span class="sxs-lookup"><span data-stu-id="bb990-105">Creating the project.</span></span>  
  
-   <span data-ttu-id="bb990-106">Uygulama düzenini tanımlama.</span><span class="sxs-lookup"><span data-stu-id="bb990-106">Defining the application layout.</span></span>  
  
-   <span data-ttu-id="bb990-107">Yeni bir özellik eşlemesi tanımlama.</span><span class="sxs-lookup"><span data-stu-id="bb990-107">Defining a new property mapping.</span></span>  
  
-   <span data-ttu-id="bb990-108">Varsayılan özellik eşlemesini kaldırma.</span><span class="sxs-lookup"><span data-stu-id="bb990-108">Removing a default property mapping.</span></span>  
  
-   <span data-ttu-id="bb990-109">Varsayılan özellik eşlemesini değiştirme.</span><span class="sxs-lookup"><span data-stu-id="bb990-109">Replacing a default property mapping.</span></span>  
  
-   <span data-ttu-id="bb990-110">Varsayılan özellik eşlemesini genişletme.</span><span class="sxs-lookup"><span data-stu-id="bb990-110">Extending a default property mapping.</span></span>  
  
 <span data-ttu-id="bb990-111">Bu örneklerde gösterilen görevlerin tam kod listesi için bkz: [WindowsFormsHost Öğesi örneğini kullanarak eşleme özellikleri](http://go.microsoft.com/fwlink/?LinkID=160019).</span><span class="sxs-lookup"><span data-stu-id="bb990-111">For a complete code listing of the tasks illustrated in this walkthrough, see [Mapping Properties Using the WindowsFormsHost Element Sample](http://go.microsoft.com/fwlink/?LinkID=160019).</span></span>  
  
 <span data-ttu-id="bb990-112">İşiniz bittiğinde, eşleme kuramaz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellikleri barındırılan karşılık gelen özelliklere [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetim.</span><span class="sxs-lookup"><span data-stu-id="bb990-112">When you are finished, you will be able to map [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties to corresponding properties on a hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="bb990-113">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="bb990-113">Prerequisites</span></span>  
 <span data-ttu-id="bb990-114">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="bb990-114">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)]<span data-ttu-id="bb990-115">.</span><span class="sxs-lookup"><span data-stu-id="bb990-115">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="bb990-116">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="bb990-116">Creating the Project</span></span>  
  
#### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="bb990-117">Oluşturun ve projeyi ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="bb990-117">To create and set up the project</span></span>  
  
1.  <span data-ttu-id="bb990-118">Adlı bir WPF uygulaması projesi oluşturduğunuzda `PropertyMappingWithWfhSample`.</span><span class="sxs-lookup"><span data-stu-id="bb990-118">Create a WPF Application project named `PropertyMappingWithWfhSample`.</span></span>  
  
2.  <span data-ttu-id="bb990-119">Çözüm Gezgininde WindowsFormsIntegration.dll adlı WindowsFormsIntegration derlemesine başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bb990-119">In Solution Explorer, add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>  
  
3.  <span data-ttu-id="bb990-120">Çözüm Gezgini'nde System.Drawing ve System.Windows.Forms derlemelerine başvurular ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bb990-120">In Solution Explorer, add references to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="defining-the-application-layout"></a><span data-ttu-id="bb990-121">Uygulama düzenini tanımlama</span><span class="sxs-lookup"><span data-stu-id="bb990-121">Defining the Application Layout</span></span>  
 <span data-ttu-id="bb990-122">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-Uygulamanız tarafından kullanılan temel <xref:System.Windows.Forms.Integration.WindowsFormsHost> konak öğesine bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetim.</span><span class="sxs-lookup"><span data-stu-id="bb990-122">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application uses the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element to host a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>  
  
#### <a name="to-define-the-application-layout"></a><span data-ttu-id="bb990-123">Uygulama düzeni tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="bb990-123">To define the application layout</span></span>  
  
1.  <span data-ttu-id="bb990-124">Window1.XAML içinde açmak [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bb990-124">Open Window1.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
2.  <span data-ttu-id="bb990-125">Var olan kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="bb990-125">Replace the existing code with the following code.</span></span>  
  
     [!code-xaml[PropertyMappingWithWfhSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml#1)]  
  
3.  <span data-ttu-id="bb990-126">Window1.xaml.cs'i Kod düzenleyicisinde açın.</span><span class="sxs-lookup"><span data-stu-id="bb990-126">Open Window1.xaml.cs in the Code Editor.</span></span>  
  
4.  <span data-ttu-id="bb990-127">Dosyanın üst kısmında, şu ad alanlarından içe aktarın.</span><span class="sxs-lookup"><span data-stu-id="bb990-127">At the top of the file, import the following namespaces.</span></span>  
  
     [!code-csharp[PropertyMappingWithWfhSample#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#20)]
     [!code-vb[PropertyMappingWithWfhSample#20](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#20)]  
  
## <a name="defining-a-new-property-mapping"></a><span data-ttu-id="bb990-128">Yeni bir özellik eşlemesi tanımlama</span><span class="sxs-lookup"><span data-stu-id="bb990-128">Defining a New Property Mapping</span></span>  
 <span data-ttu-id="bb990-129"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi birkaç varsayılan özellik eşlemelerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="bb990-129">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element provides several default property mappings.</span></span> <span data-ttu-id="bb990-130">Yeni bir özellik eşlemesi çağırarak eklemek <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> yöntemi <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğenin <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span><span class="sxs-lookup"><span data-stu-id="bb990-130">You add a new property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>  
  
#### <a name="to-define-a-new-property-mapping"></a><span data-ttu-id="bb990-131">Yeni bir özellik eşlemesi tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="bb990-131">To define a new property mapping</span></span>  
  
-   <span data-ttu-id="bb990-132">Tanımı aşağıdaki kodu kopyalayın `Window1` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="bb990-132">Copy the following code into the definition for the `Window1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithWfhSample#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#14)]
     [!code-vb[PropertyMappingWithWfhSample#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#14)]  
  
     <span data-ttu-id="bb990-133">`AddClipMapping` Yöntemi ekler için yeni bir eşleme <xref:System.Windows.UIElement.Clip%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="bb990-133">The `AddClipMapping` method adds a new mapping for the <xref:System.Windows.UIElement.Clip%2A> property.</span></span>  
  
     <span data-ttu-id="bb990-134">`OnClipChange` Yöntemi çevirir <xref:System.Windows.UIElement.Clip%2A> özelliğine [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Control.Region%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="bb990-134">The `OnClipChange` method translates the <xref:System.Windows.UIElement.Clip%2A> property to the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.Region%2A> property.</span></span>  
  
     <span data-ttu-id="bb990-135">`Window1_SizeChanged` Yöntemi işler pencerenin <xref:System.Windows.FrameworkElement.SizeChanged> olay ve kırpma bölgesinin uygulama penceresine sığacak şekilde boyutlandırır.</span><span class="sxs-lookup"><span data-stu-id="bb990-135">The `Window1_SizeChanged` method handles the window's <xref:System.Windows.FrameworkElement.SizeChanged> event and sizes the clipping region to fit the application window.</span></span>  
  
## <a name="removing-a-default-property-mapping"></a><span data-ttu-id="bb990-136">Varsayılan özellik eşlemesini kaldırma</span><span class="sxs-lookup"><span data-stu-id="bb990-136">Removing a Default Property Mapping</span></span>  
 <span data-ttu-id="bb990-137">Varsayılan özellik eşlemesini çağırarak kaldırın <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> yöntemi <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğenin <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span><span class="sxs-lookup"><span data-stu-id="bb990-137">Remove a default property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>  
  
#### <a name="to-remove-a-default-property-mapping"></a><span data-ttu-id="bb990-138">Varsayılan özellik eşlemesini kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="bb990-138">To remove a default property mapping</span></span>  
  
-   <span data-ttu-id="bb990-139">Tanımı aşağıdaki kodu kopyalayın `Window1` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="bb990-139">Copy the following code into the definition for the `Window1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithWfhSample#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#13)]
     [!code-vb[PropertyMappingWithWfhSample#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#13)]  
  
     <span data-ttu-id="bb990-140">`RemoveCursorMapping` Yöntemi için varsayılan eşlemeyi siler <xref:System.Windows.FrameworkElement.Cursor%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="bb990-140">The `RemoveCursorMapping` method deletes the default mapping for the <xref:System.Windows.FrameworkElement.Cursor%2A> property.</span></span>  
  
## <a name="replacing-a-default-property-mapping"></a><span data-ttu-id="bb990-141">Varsayılan özellik eşlemesini değiştirme</span><span class="sxs-lookup"><span data-stu-id="bb990-141">Replacing a Default Property Mapping</span></span>  
 <span data-ttu-id="bb990-142">Varsayılan eşleme ve arama kaldırarak varsayılan özellik eşlemesini değiştirmek <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> yöntemi <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğenin <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span><span class="sxs-lookup"><span data-stu-id="bb990-142">Replace a default property mapping by removing the default mapping and calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>  
  
#### <a name="to-replace-a-default-property-mapping"></a><span data-ttu-id="bb990-143">Varsayılan özellik eşlemesini değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="bb990-143">To replace a default property mapping</span></span>  
  
-   <span data-ttu-id="bb990-144">Tanımı aşağıdaki kodu kopyalayın `Window1` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="bb990-144">Copy the following code into the definition for the `Window1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithWfhSample#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#12)]
     [!code-vb[PropertyMappingWithWfhSample#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#12)]  
  
     <span data-ttu-id="bb990-145">`ReplaceFlowDirectionMapping` Yöntemi için varsayılan eşlemeyi değiştirir <xref:System.Windows.FrameworkElement.FlowDirection%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="bb990-145">The `ReplaceFlowDirectionMapping` method replaces the default mapping for the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property.</span></span>  
  
     <span data-ttu-id="bb990-146">`OnFlowDirectionChange` Yöntemi çevirir <xref:System.Windows.FrameworkElement.FlowDirection%2A> özelliğine [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Control.RightToLeft%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="bb990-146">The `OnFlowDirectionChange` method translates the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property to the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.RightToLeft%2A> property.</span></span>  
  
     <span data-ttu-id="bb990-147">`cb_CheckedChanged` Yöntemi tanıtıcıları <xref:System.Windows.Forms.CheckBox.CheckedChanged> olayda <xref:System.Windows.Forms.CheckBox> denetim.</span><span class="sxs-lookup"><span data-stu-id="bb990-147">The `cb_CheckedChanged` method handles the <xref:System.Windows.Forms.CheckBox.CheckedChanged> event on the <xref:System.Windows.Forms.CheckBox> control.</span></span> <span data-ttu-id="bb990-148">Atar <xref:System.Windows.FrameworkElement.FlowDirection%2A> özellik değeri temel alarak <xref:System.Windows.Forms.CheckBox.CheckState%2A> özelliği</span><span class="sxs-lookup"><span data-stu-id="bb990-148">It assigns the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property based on the value of the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property</span></span>  
  
## <a name="extending-a-default-property-mapping"></a><span data-ttu-id="bb990-149">Varsayılan özellik eşlemesini genişletme</span><span class="sxs-lookup"><span data-stu-id="bb990-149">Extending a Default Property Mapping</span></span>  
 <span data-ttu-id="bb990-150">Varsayılan özellik eşleme kullanabilir ve ayrıca kendi eşlemesi ile genişletir.</span><span class="sxs-lookup"><span data-stu-id="bb990-150">You can use a default property mapping and also extend it with your own mapping.</span></span>  
  
#### <a name="to-extend-a-default-property-mapping"></a><span data-ttu-id="bb990-151">Varsayılan özellik eşlemesini genişletmek için</span><span class="sxs-lookup"><span data-stu-id="bb990-151">To extend a default property mapping</span></span>  
  
-   <span data-ttu-id="bb990-152">Tanımı aşağıdaki kodu kopyalayın `Window1` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="bb990-152">Copy the following code into the definition for the `Window1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithWfhSample#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#15)]
     [!code-vb[PropertyMappingWithWfhSample#15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#15)]  
  
     <span data-ttu-id="bb990-153">`ExtendBackgroundMapping` Yöntemi, varolan bir özel özellik Çeviricisi ekler <xref:System.Windows.Controls.Control.Background%2A> özellik eşlemesi.</span><span class="sxs-lookup"><span data-stu-id="bb990-153">The `ExtendBackgroundMapping` method adds a custom property translator to the existing <xref:System.Windows.Controls.Control.Background%2A> property mapping.</span></span>  
  
     <span data-ttu-id="bb990-154">`OnBackgroundChange` Yöntemi barındırılan denetimin için belirli bir resim atar <xref:System.Windows.Forms.Control.BackgroundImage%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="bb990-154">The `OnBackgroundChange` method assigns a specific image to the hosted control's <xref:System.Windows.Forms.Control.BackgroundImage%2A> property.</span></span> <span data-ttu-id="bb990-155">`OnBackgroundChange` Yöntemi, varsayılan özellik eşleme uygulandıktan sonra çağrılır.</span><span class="sxs-lookup"><span data-stu-id="bb990-155">The `OnBackgroundChange` method is called after the default property mapping is applied.</span></span>  
  
## <a name="initializing-your-property-mappings"></a><span data-ttu-id="bb990-156">Özellik eşlemelerinizin başlatılıyor</span><span class="sxs-lookup"><span data-stu-id="bb990-156">Initializing Your Property Mappings</span></span>  
 <span data-ttu-id="bb990-157">Daha önce açıklanan yöntemleri çağırarak, özellik eşlemelerini ayarlamak <xref:System.Windows.FrameworkElement.Loaded> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="bb990-157">Set up your property mappings by calling the previously described methods in the <xref:System.Windows.FrameworkElement.Loaded> event handler.</span></span>  
  
#### <a name="to-initialize-your-property-mappings"></a><span data-ttu-id="bb990-158">Özellik eşlemelerinizin başlatmak için</span><span class="sxs-lookup"><span data-stu-id="bb990-158">To initialize your property mappings</span></span>  
  
1.  <span data-ttu-id="bb990-159">Tanımı aşağıdaki kodu kopyalayın `Window1` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="bb990-159">Copy the following code into the definition for the `Window1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithWfhSample#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#11)]
     [!code-vb[PropertyMappingWithWfhSample#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#11)]  
  
     <span data-ttu-id="bb990-160">`WindowLoaded` Yöntemi tanıtıcıları <xref:System.Windows.FrameworkElement.Loaded> olay ve aşağıdaki başlatmayı gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="bb990-160">The `WindowLoaded` method handles the <xref:System.Windows.FrameworkElement.Loaded> event and performs the following initialization.</span></span>  
  
    -   <span data-ttu-id="bb990-161">Oluşturur bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.CheckBox> denetim.</span><span class="sxs-lookup"><span data-stu-id="bb990-161">Creates a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.CheckBox> control.</span></span>  
  
    -   <span data-ttu-id="bb990-162">Özellik eşlemelerini ayarlamak için önceki örnekte tanımlanan yöntemleri çağırır.</span><span class="sxs-lookup"><span data-stu-id="bb990-162">Calls the methods you defined earlier in the walkthrough to set up the property mappings.</span></span>  
  
    -   <span data-ttu-id="bb990-163">Eşlenen özelliklere ilk değerleri atar.</span><span class="sxs-lookup"><span data-stu-id="bb990-163">Assigns initial values to the mapped properties.</span></span>  
  
2.  <span data-ttu-id="bb990-164">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="bb990-164">Press F5 to build and run the application.</span></span> <span data-ttu-id="bb990-165">Etkisini görmek için bu onay kutusuna tıklayın <xref:System.Windows.FrameworkElement.FlowDirection%2A> eşleme.</span><span class="sxs-lookup"><span data-stu-id="bb990-165">Click the check box to see the effect of the <xref:System.Windows.FrameworkElement.FlowDirection%2A> mapping.</span></span> <span data-ttu-id="bb990-166">Onay kutusunu işaretlediğinizde düzenini soldan sağa yönünü tersine çevirir.</span><span class="sxs-lookup"><span data-stu-id="bb990-166">When you click the check box, the layout reverses its left-right orientation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb990-167">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bb990-167">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="bb990-168">Windows Forms ve WPF Özelliğini Eşleme</span><span class="sxs-lookup"><span data-stu-id="bb990-168">Windows Forms and WPF Property Mapping</span></span>](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)  
 [<span data-ttu-id="bb990-169">WPF Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="bb990-169">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="bb990-170">İzlenecek yol: WPF'de Windows Forms Denetimini Barındırma</span><span class="sxs-lookup"><span data-stu-id="bb990-170">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)
