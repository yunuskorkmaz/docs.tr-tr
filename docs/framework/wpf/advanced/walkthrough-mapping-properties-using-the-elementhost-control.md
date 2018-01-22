---
title: "İzlenecek yol: ElementHost Denetimini Kullanarak Özellikleri Eşleme"
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
- ElementHost control [WPF], mapping properties
ms.assetid: bccd6e0d-2272-4924-9107-ff8ed58b88aa
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 030183e77a141036416a3bcb8a4c4018df0a7e65
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-mapping-properties-using-the-elementhost-control"></a><span data-ttu-id="e4827-102">İzlenecek yol: ElementHost Denetimini Kullanarak Özellikleri Eşleme</span><span class="sxs-lookup"><span data-stu-id="e4827-102">Walkthrough: Mapping Properties Using the ElementHost Control</span></span>
<span data-ttu-id="e4827-103">Bu kılavuz size nasıl kullanılacağını gösterir <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> eşlemek için özellik [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] özellikleri barındırılan karşılık gelen özelliklere [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğesi.</span><span class="sxs-lookup"><span data-stu-id="e4827-103">This walkthrough shows you how to use the <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> property to map [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] properties to corresponding properties on a hosted [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element.</span></span>  
  
 <span data-ttu-id="e4827-104">Bu örneklerde gösterilen görevler aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="e4827-104">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="e4827-105">Projeyi oluşturma.</span><span class="sxs-lookup"><span data-stu-id="e4827-105">Creating the project.</span></span>  
  
-   <span data-ttu-id="e4827-106">Yeni bir özellik eşlemesi tanımlama.</span><span class="sxs-lookup"><span data-stu-id="e4827-106">Defining a new property mapping.</span></span>  
  
-   <span data-ttu-id="e4827-107">Varsayılan özellik eşlemesini kaldırma.</span><span class="sxs-lookup"><span data-stu-id="e4827-107">Removing a default property mapping.</span></span>  
  
-   <span data-ttu-id="e4827-108">Varsayılan özellik eşlemesini genişletme.</span><span class="sxs-lookup"><span data-stu-id="e4827-108">Extending a default property mapping.</span></span>  
  
 <span data-ttu-id="e4827-109">Bu örneklerde gösterilen görevlerin tam kod listesi için bkz: [ElementHost denetimi örneğini kullanarak eşleme özellikleri](http://go.microsoft.com/fwlink/?LinkID=160018).</span><span class="sxs-lookup"><span data-stu-id="e4827-109">For a complete code listing of the tasks illustrated in this walkthrough, see [Mapping Properties Using the ElementHost Control Sample](http://go.microsoft.com/fwlink/?LinkID=160018).</span></span>  
  
 <span data-ttu-id="e4827-110">İşiniz bittiğinde, eşleme kuramaz [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] karşılık gelen özellikleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] barındırılan öğe özellikleri.</span><span class="sxs-lookup"><span data-stu-id="e4827-110">When you are finished, you will be able to map [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] properties to corresponding [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties on a hosted element.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e4827-111">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="e4827-111">Prerequisites</span></span>  
 <span data-ttu-id="e4827-112">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="e4827-112">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)]<span data-ttu-id="e4827-113">.</span><span class="sxs-lookup"><span data-stu-id="e4827-113">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="e4827-114">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e4827-114">Creating the Project</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="e4827-115">Proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e4827-115">To create the project</span></span>  
  
1.  <span data-ttu-id="e4827-116">Oluşturma bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] adlı uygulama projesi `PropertyMappingWithElementHost`.</span><span class="sxs-lookup"><span data-stu-id="e4827-116">Create a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] application project named `PropertyMappingWithElementHost`.</span></span> <span data-ttu-id="e4827-117">Daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span><span class="sxs-lookup"><span data-stu-id="e4827-117">For more information, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="e4827-118">Çözüm Gezgini'nde, aşağıdaki başvurular ekleyin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] derlemeler.</span><span class="sxs-lookup"><span data-stu-id="e4827-118">In Solution Explorer, add references to the following [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] assemblies.</span></span>  
  
    -   <span data-ttu-id="e4827-119">PresentationCore</span><span class="sxs-lookup"><span data-stu-id="e4827-119">PresentationCore</span></span>  
  
    -   <span data-ttu-id="e4827-120">PresentationFramework</span><span class="sxs-lookup"><span data-stu-id="e4827-120">PresentationFramework</span></span>  
  
    -   <span data-ttu-id="e4827-121">WindowsBase</span><span class="sxs-lookup"><span data-stu-id="e4827-121">WindowsBase</span></span>  
  
    -   <span data-ttu-id="e4827-122">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="e4827-122">WindowsFormsIntegration</span></span>  
  
3.  <span data-ttu-id="e4827-123">Üstüne aşağıdaki kodu kopyalayın `Form1` kod dosyası.</span><span class="sxs-lookup"><span data-stu-id="e4827-123">Copy the following code into the top of the `Form1` code file.</span></span>  
  
     [!code-csharp[PropertyMappingWithElementHost#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#10)]
     [!code-vb[PropertyMappingWithElementHost#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#10)]  
  
4.  <span data-ttu-id="e4827-124">Açık `Form1` Windows Forms Tasarımcısı'nda.</span><span class="sxs-lookup"><span data-stu-id="e4827-124">Open `Form1` in the Windows Forms Designer.</span></span> <span data-ttu-id="e4827-125">Bir olay işleyicisi eklemek için form çift <xref:System.Windows.Forms.Form.Load> olay.</span><span class="sxs-lookup"><span data-stu-id="e4827-125">Double-click the form to add an event handler for the <xref:System.Windows.Forms.Form.Load> event.</span></span>  
  
5.  <span data-ttu-id="e4827-126">Dönmek için Windows Form Tasarımcısı ve form için bir olay işleyicisi ekleme <xref:System.Windows.Forms.Control.Resize> olay.</span><span class="sxs-lookup"><span data-stu-id="e4827-126">Return to the Windows Forms Designer and add an event handler for the form's <xref:System.Windows.Forms.Control.Resize> event.</span></span> <span data-ttu-id="e4827-127">Daha fazla bilgi için bkz: [nasıl yapılır: olay işleyicileri kullanarak Tasarımcı](http://msdn.microsoft.com/library/8461e9b8-14e8-406f-936e-3726732b23d2).</span><span class="sxs-lookup"><span data-stu-id="e4827-127">For more information, see [How to: Create Event Handlers Using the Designer](http://msdn.microsoft.com/library/8461e9b8-14e8-406f-936e-3726732b23d2).</span></span>  
  
6.  <span data-ttu-id="e4827-128">Bildirme bir <xref:System.Windows.Forms.Integration.ElementHost> alanındaki `Form1` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e4827-128">Declare an <xref:System.Windows.Forms.Integration.ElementHost> field in the `Form1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithElementHost#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#16)]
     [!code-vb[PropertyMappingWithElementHost#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#16)]  
  
## <a name="defining-new-property-mappings"></a><span data-ttu-id="e4827-129">Yeni özellik eşlemesi tanımlama</span><span class="sxs-lookup"><span data-stu-id="e4827-129">Defining New Property Mappings</span></span>  
 <span data-ttu-id="e4827-130"><xref:System.Windows.Forms.Integration.ElementHost> Denetimi birkaç varsayılan özellik eşlemelerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e4827-130">The <xref:System.Windows.Forms.Integration.ElementHost> control provides several default property mappings.</span></span> <span data-ttu-id="e4827-131">Yeni bir özellik eşlemesi çağırarak eklemek <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> yöntemi <xref:System.Windows.Forms.Integration.ElementHost> denetimin <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span><span class="sxs-lookup"><span data-stu-id="e4827-131">You add a new property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.ElementHost> control's <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span></span>  
  
#### <a name="to-define-new-property-mappings"></a><span data-ttu-id="e4827-132">Yeni Özellik eşlemeleri tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="e4827-132">To define new property mappings</span></span>  
  
1.  <span data-ttu-id="e4827-133">Tanımı aşağıdaki kodu kopyalayın `Form1` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e4827-133">Copy the following code into the definition for the `Form1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithElementHost#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#12)]
     [!code-vb[PropertyMappingWithElementHost#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#12)]  
  
     <span data-ttu-id="e4827-134">`AddMarginMapping` Yöntemi ekler için yeni bir eşleme <xref:System.Windows.Forms.Control.Margin%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="e4827-134">The `AddMarginMapping` method adds a new mapping for the <xref:System.Windows.Forms.Control.Margin%2A> property.</span></span>  
  
     <span data-ttu-id="e4827-135">`OnMarginChange` Yöntemi çevirir <xref:System.Windows.Forms.Control.Margin%2A> özelliğine [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement.Margin%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="e4827-135">The `OnMarginChange` method translates the <xref:System.Windows.Forms.Control.Margin%2A> property to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement.Margin%2A> property.</span></span>  
  
2.  <span data-ttu-id="e4827-136">Tanımı aşağıdaki kodu kopyalayın `Form1` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e4827-136">Copy the following code into the definition for the `Form1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithElementHost#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#14)]
     [!code-vb[PropertyMappingWithElementHost#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#14)]  
  
     <span data-ttu-id="e4827-137">`AddRegionMapping` Yöntemi ekler için yeni bir eşleme <xref:System.Windows.Forms.Control.Region%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="e4827-137">The `AddRegionMapping` method adds a new mapping for the <xref:System.Windows.Forms.Control.Region%2A> property.</span></span>  
  
     <span data-ttu-id="e4827-138">`OnRegionChange` Yöntemi çevirir <xref:System.Windows.Forms.Control.Region%2A> özelliğine [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.Clip%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="e4827-138">The `OnRegionChange` method translates the <xref:System.Windows.Forms.Control.Region%2A> property to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.Clip%2A> property.</span></span>  
  
     <span data-ttu-id="e4827-139">`Form1_Resize` Yöntemi işler formun <xref:System.Windows.Forms.Control.Resize> olay ve barındırılan öğeyi sığdıracak şekilde kırpma bölgesini boyutlandırır.</span><span class="sxs-lookup"><span data-stu-id="e4827-139">The `Form1_Resize` method handles the form's <xref:System.Windows.Forms.Control.Resize> event and sizes the clipping region to fit the hosted element.</span></span>  
  
## <a name="removing-a-default-property-mapping"></a><span data-ttu-id="e4827-140">Varsayılan özellik eşlemesini kaldırma</span><span class="sxs-lookup"><span data-stu-id="e4827-140">Removing a Default Property Mapping</span></span>  
 <span data-ttu-id="e4827-141">Varsayılan özellik eşlemesini çağırarak kaldırın <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> yöntemi <xref:System.Windows.Forms.Integration.ElementHost> denetimin <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span><span class="sxs-lookup"><span data-stu-id="e4827-141">Remove a default property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> method on the <xref:System.Windows.Forms.Integration.ElementHost> control's <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span></span>  
  
#### <a name="to-remove-a-default-property-mapping"></a><span data-ttu-id="e4827-142">Varsayılan özellik eşlemesini kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="e4827-142">To remove a default property mapping</span></span>  
  
-   <span data-ttu-id="e4827-143">Tanımı aşağıdaki kodu kopyalayın `Form1` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e4827-143">Copy the following code into the definition for the `Form1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithElementHost#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#13)]
     [!code-vb[PropertyMappingWithElementHost#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#13)]  
  
     <span data-ttu-id="e4827-144">`RemoveCursorMapping` Yöntemi için varsayılan eşlemeyi siler <xref:System.Windows.Forms.Control.Cursor%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="e4827-144">The `RemoveCursorMapping` method deletes the default mapping for the <xref:System.Windows.Forms.Control.Cursor%2A> property.</span></span>  
  
## <a name="extending-a-default-property-mapping"></a><span data-ttu-id="e4827-145">Varsayılan özellik eşlemesini genişletme</span><span class="sxs-lookup"><span data-stu-id="e4827-145">Extending a Default Property Mapping</span></span>  
 <span data-ttu-id="e4827-146">Varsayılan özellik eşleme kullanabilir ve ayrıca kendi eşlemesi ile genişletir.</span><span class="sxs-lookup"><span data-stu-id="e4827-146">You can use a default property mapping and also extend it with your own mapping.</span></span>  
  
#### <a name="to-extend-a-default-property-mapping"></a><span data-ttu-id="e4827-147">Varsayılan özellik eşlemesini genişletmek için</span><span class="sxs-lookup"><span data-stu-id="e4827-147">To extend a default property mapping</span></span>  
  
-   <span data-ttu-id="e4827-148">Tanımı aşağıdaki kodu kopyalayın `Form1` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e4827-148">Copy the following code into the definition for the `Form1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithElementHost#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#15)]
     [!code-vb[PropertyMappingWithElementHost#15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#15)]  
  
     <span data-ttu-id="e4827-149">`ExtendBackColorMapping` Yöntemi, varolan bir özel özellik Çeviricisi ekler <xref:System.Windows.Forms.Control.BackColor%2A> özellik eşlemesi.</span><span class="sxs-lookup"><span data-stu-id="e4827-149">The `ExtendBackColorMapping` method adds a custom property translator to the existing <xref:System.Windows.Forms.Control.BackColor%2A> property mapping.</span></span>  
  
     <span data-ttu-id="e4827-150">`OnBackColorChange` Yöntemi barındırılan denetimin için belirli bir resim atar <xref:System.Windows.Controls.Control.Background%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="e4827-150">The `OnBackColorChange` method assigns a specific image to the hosted control's <xref:System.Windows.Controls.Control.Background%2A> property.</span></span> <span data-ttu-id="e4827-151">`OnBackColorChange` Yöntemi, varsayılan özellik eşleme uygulandıktan sonra çağrılır.</span><span class="sxs-lookup"><span data-stu-id="e4827-151">The `OnBackColorChange` method is called after the default property mapping is applied.</span></span>  
  
## <a name="initializing-your-property-mappings"></a><span data-ttu-id="e4827-152">Özellik eşlemelerinizin başlatılıyor</span><span class="sxs-lookup"><span data-stu-id="e4827-152">Initializing Your Property Mappings</span></span>  
  
#### <a name="to-initialize-your-property-mappings"></a><span data-ttu-id="e4827-153">Özellik eşlemelerinizin başlatmak için</span><span class="sxs-lookup"><span data-stu-id="e4827-153">To initialize your property mappings</span></span>  
  
1.  <span data-ttu-id="e4827-154">Tanımı aşağıdaki kodu kopyalayın `Form1` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e4827-154">Copy the following code into the definition for the `Form1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithElementHost#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#11)]
     [!code-vb[PropertyMappingWithElementHost#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#11)]  
  
     <span data-ttu-id="e4827-155">`Form1_Load` Yöntemi tanıtıcıları <xref:System.Windows.Forms.Form.Load> olay ve aşağıdaki başlatmayı gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="e4827-155">The `Form1_Load` method handles the <xref:System.Windows.Forms.Form.Load> event and performs the following initialization.</span></span>  
  
    -   <span data-ttu-id="e4827-156">Oluşturur bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> öğesi.</span><span class="sxs-lookup"><span data-stu-id="e4827-156">Creates a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> element.</span></span>  
  
    -   <span data-ttu-id="e4827-157">Özellik eşlemelerini ayarlamak için önceki örnekte tanımlanan yöntemleri çağırır.</span><span class="sxs-lookup"><span data-stu-id="e4827-157">Calls the methods you defined earlier in the walkthrough to set up the property mappings.</span></span>  
  
    -   <span data-ttu-id="e4827-158">Eşlenen özelliklere ilk değerleri atar.</span><span class="sxs-lookup"><span data-stu-id="e4827-158">Assigns initial values to the mapped properties.</span></span>  
  
2.  <span data-ttu-id="e4827-159">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e4827-159">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4827-160">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e4827-160">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="e4827-161">Windows Forms ve WPF Özelliğini Eşleme</span><span class="sxs-lookup"><span data-stu-id="e4827-161">Windows Forms and WPF Property Mapping</span></span>](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)  
 [<span data-ttu-id="e4827-162">WPF Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="e4827-162">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="e4827-163">İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma</span><span class="sxs-lookup"><span data-stu-id="e4827-163">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
