---
title: 'İzlenecek yol: ElementHost Denetimini Kullanarak Özellikleri Eşleme'
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- ElementHost control [WPF], mapping properties
ms.assetid: bccd6e0d-2272-4924-9107-ff8ed58b88aa
ms.openlocfilehash: 7ff4ff607ab70b55cda1e2c4736ff773d4907a22
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794111"
---
# <a name="walkthrough-mapping-properties-using-the-elementhost-control"></a><span data-ttu-id="54f82-102">İzlenecek yol: ElementHost Denetimini Kullanarak Özellikleri Eşleme</span><span class="sxs-lookup"><span data-stu-id="54f82-102">Walkthrough: Mapping Properties Using the ElementHost Control</span></span>

<span data-ttu-id="54f82-103">Bu izlenecek yol, Windows Forms özelliklerini barındırılan bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğesinde karşılık gelen özelliklerle eşlemek için <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> özelliğini nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="54f82-103">This walkthrough shows you how to use the <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> property to map Windows Forms properties to corresponding properties on a hosted [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element.</span></span>

<span data-ttu-id="54f82-104">Bu izlenecek yolda gösterilen görevler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="54f82-104">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="54f82-105">Proje oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="54f82-105">Creating the project.</span></span>

- <span data-ttu-id="54f82-106">Yeni özellik eşlemesi tanımlama.</span><span class="sxs-lookup"><span data-stu-id="54f82-106">Defining a new property mapping.</span></span>

- <span data-ttu-id="54f82-107">Varsayılan özellik eşlemesi kaldırılıyor.</span><span class="sxs-lookup"><span data-stu-id="54f82-107">Removing a default property mapping.</span></span>

- <span data-ttu-id="54f82-108">Varsayılan özellik eşlemesini genişletme.</span><span class="sxs-lookup"><span data-stu-id="54f82-108">Extending a default property mapping.</span></span>

<span data-ttu-id="54f82-109">Bu kılavuzda gösterilen görevlerin tüm kod listesi için bkz. [ElementHost denetim örneğini kullanarak özellikleri eşleme](https://go.microsoft.com/fwlink/?LinkID=160018).</span><span class="sxs-lookup"><span data-stu-id="54f82-109">For a complete code listing of the tasks illustrated in this walkthrough, see [Mapping Properties Using the ElementHost Control Sample](https://go.microsoft.com/fwlink/?LinkID=160018).</span></span>

<span data-ttu-id="54f82-110">İşiniz bittiğinde, Windows Forms özelliklerini barındırılan bir öğede karşılık gelen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellikleriyle eşleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="54f82-110">When you are finished, you will be able to map Windows Forms properties to corresponding [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties on a hosted element.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="54f82-111">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="54f82-111">Prerequisites</span></span>

<span data-ttu-id="54f82-112">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="54f82-112">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="54f82-113">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="54f82-113">Visual Studio 2017</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="54f82-114">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="54f82-114">Creating the Project</span></span>

### <a name="to-create-the-project"></a><span data-ttu-id="54f82-115">Proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="54f82-115">To create the project</span></span>

1. <span data-ttu-id="54f82-116">`PropertyMappingWithElementHost`adlı **Windows Forms bir uygulama** projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="54f82-116">Create a **Windows Forms App** project named `PropertyMappingWithElementHost`.</span></span>

2. <span data-ttu-id="54f82-117">**Çözüm Gezgini**, aşağıdaki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] derlemelerine başvuruları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="54f82-117">In **Solution Explorer**, add references to the following [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] assemblies.</span></span>

    - <span data-ttu-id="54f82-118">PresentationCore</span><span class="sxs-lookup"><span data-stu-id="54f82-118">PresentationCore</span></span>

    - <span data-ttu-id="54f82-119">PresentationFramework</span><span class="sxs-lookup"><span data-stu-id="54f82-119">PresentationFramework</span></span>

    - <span data-ttu-id="54f82-120">WindowsBase</span><span class="sxs-lookup"><span data-stu-id="54f82-120">WindowsBase</span></span>

    - <span data-ttu-id="54f82-121">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="54f82-121">WindowsFormsIntegration</span></span>

3. <span data-ttu-id="54f82-122">Aşağıdaki kodu `Form1` kod dosyasının en üstüne kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="54f82-122">Copy the following code into the top of the `Form1` code file.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#10](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#10)]
     [!code-vb[PropertyMappingWithElementHost#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#10)]

4. <span data-ttu-id="54f82-123">Windows Form Tasarımcısı `Form1` açın.</span><span class="sxs-lookup"><span data-stu-id="54f82-123">Open `Form1` in the Windows Forms Designer.</span></span> <span data-ttu-id="54f82-124"><xref:System.Windows.Forms.Form.Load> olayına bir olay işleyicisi eklemek için forma çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="54f82-124">Double-click the form to add an event handler for the <xref:System.Windows.Forms.Form.Load> event.</span></span>

5. <span data-ttu-id="54f82-125">Windows Form Tasarımcısı dönüp formun <xref:System.Windows.Forms.Control.Resize> olayı için bir olay işleyicisi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="54f82-125">Return to the Windows Forms Designer and add an event handler for the form's <xref:System.Windows.Forms.Control.Resize> event.</span></span> <span data-ttu-id="54f82-126">Daha fazla bilgi için bkz. [nasıl yapılır: tasarımcı kullanarak olay Işleyicileri oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="54f82-126">For more information, see [How to: Create Event Handlers Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)).</span></span>

6. <span data-ttu-id="54f82-127">`Form1` sınıfında bir <xref:System.Windows.Forms.Integration.ElementHost> alanı bildirin.</span><span class="sxs-lookup"><span data-stu-id="54f82-127">Declare an <xref:System.Windows.Forms.Integration.ElementHost> field in the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#16](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#16)]
     [!code-vb[PropertyMappingWithElementHost#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#16)]

## <a name="defining-new-property-mappings"></a><span data-ttu-id="54f82-128">Yeni özellik eşlemelerini tanımlama</span><span class="sxs-lookup"><span data-stu-id="54f82-128">Defining New Property Mappings</span></span>

<span data-ttu-id="54f82-129"><xref:System.Windows.Forms.Integration.ElementHost> denetimi, çeşitli varsayılan özellik eşlemeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="54f82-129">The <xref:System.Windows.Forms.Integration.ElementHost> control provides several default property mappings.</span></span> <span data-ttu-id="54f82-130"><xref:System.Windows.Forms.Integration.ElementHost> denetiminin <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A><xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> yöntemini çağırarak yeni bir özellik eşlemesi eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="54f82-130">You add a new property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.ElementHost> control's <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span></span>

### <a name="to-define-new-property-mappings"></a><span data-ttu-id="54f82-131">Yeni özellik eşlemelerini tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="54f82-131">To define new property mappings</span></span>

1. <span data-ttu-id="54f82-132">Aşağıdaki kodu `Form1` sınıfının tanımına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="54f82-132">Copy the following code into the definition for the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#12](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#12)]
     [!code-vb[PropertyMappingWithElementHost#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#12)]

     <span data-ttu-id="54f82-133">`AddMarginMapping` yöntemi <xref:System.Windows.Forms.Control.Margin%2A> özelliği için yeni bir eşleme ekler.</span><span class="sxs-lookup"><span data-stu-id="54f82-133">The `AddMarginMapping` method adds a new mapping for the <xref:System.Windows.Forms.Control.Margin%2A> property.</span></span>

     <span data-ttu-id="54f82-134">`OnMarginChange` yöntemi, <xref:System.Windows.Forms.Control.Margin%2A> özelliğini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement.Margin%2A> özelliğine çevirir.</span><span class="sxs-lookup"><span data-stu-id="54f82-134">The `OnMarginChange` method translates the <xref:System.Windows.Forms.Control.Margin%2A> property to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement.Margin%2A> property.</span></span>

2. <span data-ttu-id="54f82-135">Aşağıdaki kodu `Form1` sınıfının tanımına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="54f82-135">Copy the following code into the definition for the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#14](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#14)]
     [!code-vb[PropertyMappingWithElementHost#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#14)]

     <span data-ttu-id="54f82-136">`AddRegionMapping` yöntemi <xref:System.Windows.Forms.Control.Region%2A> özelliği için yeni bir eşleme ekler.</span><span class="sxs-lookup"><span data-stu-id="54f82-136">The `AddRegionMapping` method adds a new mapping for the <xref:System.Windows.Forms.Control.Region%2A> property.</span></span>

     <span data-ttu-id="54f82-137">`OnRegionChange` yöntemi, <xref:System.Windows.Forms.Control.Region%2A> özelliğini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.Clip%2A> özelliğine çevirir.</span><span class="sxs-lookup"><span data-stu-id="54f82-137">The `OnRegionChange` method translates the <xref:System.Windows.Forms.Control.Region%2A> property to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.Clip%2A> property.</span></span>

     <span data-ttu-id="54f82-138">`Form1_Resize` yöntemi, formun <xref:System.Windows.Forms.Control.Resize> olayını işler ve kırpma bölgesini barındırılan öğeye uyacak şekilde boyutlandırır.</span><span class="sxs-lookup"><span data-stu-id="54f82-138">The `Form1_Resize` method handles the form's <xref:System.Windows.Forms.Control.Resize> event and sizes the clipping region to fit the hosted element.</span></span>

## <a name="removing-a-default-property-mapping"></a><span data-ttu-id="54f82-139">Varsayılan özellik eşlemesini kaldırma</span><span class="sxs-lookup"><span data-stu-id="54f82-139">Removing a Default Property Mapping</span></span>

<span data-ttu-id="54f82-140"><xref:System.Windows.Forms.Integration.ElementHost> denetiminin <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A><xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> yöntemini çağırarak varsayılan özellik eşlemesini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="54f82-140">Remove a default property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> method on the <xref:System.Windows.Forms.Integration.ElementHost> control's <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span></span>

### <a name="to-remove-a-default-property-mapping"></a><span data-ttu-id="54f82-141">Varsayılan özellik eşlemesini kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="54f82-141">To remove a default property mapping</span></span>

- <span data-ttu-id="54f82-142">Aşağıdaki kodu `Form1` sınıfının tanımına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="54f82-142">Copy the following code into the definition for the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#13](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#13)]
     [!code-vb[PropertyMappingWithElementHost#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#13)]

     <span data-ttu-id="54f82-143">`RemoveCursorMapping` yöntemi <xref:System.Windows.Forms.Control.Cursor%2A> özelliğinin varsayılan eşlemesini siler.</span><span class="sxs-lookup"><span data-stu-id="54f82-143">The `RemoveCursorMapping` method deletes the default mapping for the <xref:System.Windows.Forms.Control.Cursor%2A> property.</span></span>

## <a name="extending-a-default-property-mapping"></a><span data-ttu-id="54f82-144">Varsayılan özellik eşlemesini genişletme</span><span class="sxs-lookup"><span data-stu-id="54f82-144">Extending a Default Property Mapping</span></span>

<span data-ttu-id="54f82-145">Varsayılan bir özellik eşlemesini kullanabilir ve ayrıca kendi eşlemesiyle genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="54f82-145">You can use a default property mapping and also extend it with your own mapping.</span></span>

### <a name="to-extend-a-default-property-mapping"></a><span data-ttu-id="54f82-146">Varsayılan bir özellik eşlemesini genişletmek için</span><span class="sxs-lookup"><span data-stu-id="54f82-146">To extend a default property mapping</span></span>

- <span data-ttu-id="54f82-147">Aşağıdaki kodu `Form1` sınıfının tanımına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="54f82-147">Copy the following code into the definition for the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#15](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#15)]
     [!code-vb[PropertyMappingWithElementHost#15](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#15)]

     <span data-ttu-id="54f82-148">`ExtendBackColorMapping` yöntemi, varolan <xref:System.Windows.Forms.Control.BackColor%2A> özellik eşlemesine özel bir özellik Çeviricisi ekler.</span><span class="sxs-lookup"><span data-stu-id="54f82-148">The `ExtendBackColorMapping` method adds a custom property translator to the existing <xref:System.Windows.Forms.Control.BackColor%2A> property mapping.</span></span>

     <span data-ttu-id="54f82-149">`OnBackColorChange` yöntemi, barındırılan denetimin <xref:System.Windows.Controls.Control.Background%2A> özelliğine belirli bir görüntü atar.</span><span class="sxs-lookup"><span data-stu-id="54f82-149">The `OnBackColorChange` method assigns a specific image to the hosted control's <xref:System.Windows.Controls.Control.Background%2A> property.</span></span> <span data-ttu-id="54f82-150">`OnBackColorChange` yöntemi, varsayılan özellik eşleme uygulandıktan sonra çağrılır.</span><span class="sxs-lookup"><span data-stu-id="54f82-150">The `OnBackColorChange` method is called after the default property mapping is applied.</span></span>

## <a name="initialize-your-property-mappings"></a><span data-ttu-id="54f82-151">Özellik Eşlemelerinizi başlatın</span><span class="sxs-lookup"><span data-stu-id="54f82-151">Initialize your property mappings</span></span>

1. <span data-ttu-id="54f82-152">Aşağıdaki kodu `Form1` sınıfının tanımına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="54f82-152">Copy the following code into the definition for the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#11](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#11)]
     [!code-vb[PropertyMappingWithElementHost#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#11)]

     <span data-ttu-id="54f82-153">`Form1_Load` yöntemi <xref:System.Windows.Forms.Form.Load> olayını işler ve aşağıdaki başlatmayı gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="54f82-153">The `Form1_Load` method handles the <xref:System.Windows.Forms.Form.Load> event and performs the following initialization.</span></span>

    - <span data-ttu-id="54f82-154">Bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> öğesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="54f82-154">Creates a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> element.</span></span>

    - <span data-ttu-id="54f82-155">Özellik eşlemelerini ayarlamak için izlenecek yolda daha önce tanımladığınız yöntemleri çağırır.</span><span class="sxs-lookup"><span data-stu-id="54f82-155">Calls the methods you defined earlier in the walkthrough to set up the property mappings.</span></span>

    - <span data-ttu-id="54f82-156">Eşlenen özelliklere ilk değerleri atar.</span><span class="sxs-lookup"><span data-stu-id="54f82-156">Assigns initial values to the mapped properties.</span></span>

2. <span data-ttu-id="54f82-157">Uygulamayı derlemek ve çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="54f82-157">Press F5 to build and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="54f82-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54f82-158">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="54f82-159">Windows Forms ve WPF Özelliğini Eşleme</span><span class="sxs-lookup"><span data-stu-id="54f82-159">Windows Forms and WPF Property Mapping</span></span>](windows-forms-and-wpf-property-mapping.md)
- [<span data-ttu-id="54f82-160">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="54f82-160">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="54f82-161">İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma</span><span class="sxs-lookup"><span data-stu-id="54f82-161">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
