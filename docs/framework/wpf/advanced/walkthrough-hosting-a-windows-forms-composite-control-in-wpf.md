---
title: "İzlenecek yol: WPF'de Windows Forms Bileşik Denetimini Barındırma"
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
- hosting Windows Forms control in WPF [WPF]
- composite controls [WPF], hosting in WPF
ms.assetid: 96fcd78d-1c77-4206-8928-3a0579476ef4
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f9fc708d3fff3dfca29f46da8d345aeb243df38c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-hosting-a-windows-forms-composite-control-in-wpf"></a><span data-ttu-id="add16-102">İzlenecek yol: WPF'de Windows Forms Bileşik Denetimini Barındırma</span><span class="sxs-lookup"><span data-stu-id="add16-102">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="add16-103">uygulamaları oluşturmak için zengin bir ortam sağlar.</span><span class="sxs-lookup"><span data-stu-id="add16-103"> provides a rich environment for creating applications.</span></span> <span data-ttu-id="add16-104">Önemli ölçüde yatırımınız varsa [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kodu olabilir en az yeniden daha etkili kodda bazıları, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama yerine baştan yeniden.</span><span class="sxs-lookup"><span data-stu-id="add16-104">However, when you have a substantial investment in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] code, it can be more effective to reuse at least some of that code in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application rather than to rewrite it from scratch.</span></span> <span data-ttu-id="add16-105">Mevcut olduğunda en yaygın senaryodur [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="add16-105">The most common scenario is when you have existing [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] controls.</span></span> <span data-ttu-id="add16-106">Bazı durumlarda, bile bu denetimleri için kaynak koduna erişim sahip olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="add16-106">In some cases, you might not even have access to the source code for these controls.</span></span> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="add16-107">Bu tür denetimlerinde barındırmak için basit bir yordam sağlar bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="add16-107"> provides a straightforward procedure for hosting such controls in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="add16-108">Örneğin, kullanabileceğiniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çoğu barındırırken, programlama için <xref:System.Windows.Forms.DataGridView> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="add16-108">For example, you can use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] for most of your programming while hosting your specialized <xref:System.Windows.Forms.DataGridView> controls.</span></span>  
  
 <span data-ttu-id="add16-109">Bu kılavuzda barındıran aracılığıyla bir uygulama adımları bir [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] veri girişi gerçekleştirmek için bileşik denetim bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="add16-109">This walkthrough steps you through an application that hosts a [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] composite control to perform data entry in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="add16-110">Bileşik Denetim DLL'de paketlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="add16-110">The composite control is packaged in a DLL.</span></span> <span data-ttu-id="add16-111">Bu genel yordam daha karmaşık uygulamalar ve denetimler için genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="add16-111">This general procedure can be extended to more complex applications and controls.</span></span> <span data-ttu-id="add16-112">Bu kılavuzda görünümünü ve işlevini neredeyse aynı olacak şekilde tasarlanmıştır [izlenecek yol: Windows Forms içerisinde WPF bileşik denetimi barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="add16-112">This walkthrough is designed to be nearly identical in appearance and functionality to [Walkthrough: Hosting a WPF Composite Control in Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md).</span></span> <span data-ttu-id="add16-113">Barındırma senaryo tersine çevrildi birincil farktır.</span><span class="sxs-lookup"><span data-stu-id="add16-113">The primary difference is that the hosting scenario is reversed.</span></span>  
  
 <span data-ttu-id="add16-114">İzlenecek yol iki bölüme ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="add16-114">The walkthrough is divided into two sections.</span></span> <span data-ttu-id="add16-115">Uygulamasını ilk bölümü kısaca açıklar [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] bileşik denetim.</span><span class="sxs-lookup"><span data-stu-id="add16-115">The first section briefly describes the implementation of the [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] composite control.</span></span> <span data-ttu-id="add16-116">İkinci bölümü, bileşik denetimi barındırmak nasıl ayrıntılı olarak anlatılmaktadır bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama, denetim olaylarını almasını ve denetimin özelliklerini erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="add16-116">The second section discusses in detail how to host the composite control in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application, receive events from the control, and access some of the control's properties.</span></span>  
  
 <span data-ttu-id="add16-117">Bu örneklerde gösterilen görevler aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="add16-117">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="add16-118">Windows Forms Bileşik Denetim uygulama.</span><span class="sxs-lookup"><span data-stu-id="add16-118">Implementing the Windows Forms composite control.</span></span>  
  
-   <span data-ttu-id="add16-119">WPF konak uygulamanın uygulama.</span><span class="sxs-lookup"><span data-stu-id="add16-119">Implementing the WPF host application.</span></span>  
  
 <span data-ttu-id="add16-120">Bu örneklerde gösterilen görevlerin tam kod listesi için bkz: [bir Windows Forms Bileşik Denetimi WPF örnek barındırma](http://go.microsoft.com/fwlink/?LinkID=159999).</span><span class="sxs-lookup"><span data-stu-id="add16-120">For a complete code listing of the tasks illustrated in this walkthrough, see [Hosting a Windows Forms Composite Control in WPF Sample](http://go.microsoft.com/fwlink/?LinkID=159999).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="add16-121">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="add16-121">Prerequisites</span></span>  
 <span data-ttu-id="add16-122">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="add16-122">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="add16-123">.</span><span class="sxs-lookup"><span data-stu-id="add16-123">.</span></span>  
  
## <a name="implementing-the-windows-forms-composite-control"></a><span data-ttu-id="add16-124">Windows Forms Bileşik denetimi uygulama</span><span class="sxs-lookup"><span data-stu-id="add16-124">Implementing the Windows Forms Composite Control</span></span>  
 <span data-ttu-id="add16-125">[!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] Bu örnekte kullanılan bileşik denetim olan basit veri girişi formu.</span><span class="sxs-lookup"><span data-stu-id="add16-125">The [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] composite control used in this example is a simple data-entry form.</span></span> <span data-ttu-id="add16-126">Bu form kullanıcının adı ve adresini alır ve bu bilgileri ana bilgisayara döndürmek için özel bir olay kullanır.</span><span class="sxs-lookup"><span data-stu-id="add16-126">This form takes the user's name and address and then uses a custom event to return that information to the host.</span></span> <span data-ttu-id="add16-127">Aşağıdaki çizimde işlenen denetimi göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="add16-127">The following illustration shows the rendered control.</span></span>  
  
 <span data-ttu-id="add16-128">![Basit Windows Forms denetimi](../../../../docs/framework/wpf/advanced/media/wfcontrol.gif "WFControl")</span><span class="sxs-lookup"><span data-stu-id="add16-128">![Simple Windows Forms control](../../../../docs/framework/wpf/advanced/media/wfcontrol.gif "WFControl")</span></span>  
<span data-ttu-id="add16-129">Bileşik Windows Forms denetimi</span><span class="sxs-lookup"><span data-stu-id="add16-129">Windows Forms composite control</span></span>  
  
### <a name="creating-the-project"></a><span data-ttu-id="add16-130">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="add16-130">Creating the Project</span></span>  
 <span data-ttu-id="add16-131">Projeyi başlatmak için:</span><span class="sxs-lookup"><span data-stu-id="add16-131">To start the project:</span></span>  
  
1.  <span data-ttu-id="add16-132">Başlatma [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], açarak **yeni proje** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="add16-132">Launch [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], and open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="add16-133">Penceresi kategorisindeki seçmek **Windows Forms Denetim Kitaplığı** şablonu.</span><span class="sxs-lookup"><span data-stu-id="add16-133">In the Window category, select the **Windows Forms Control Library** template.</span></span>  
  
3.  <span data-ttu-id="add16-134">Yeni proje adı `MyControls`.</span><span class="sxs-lookup"><span data-stu-id="add16-134">Name the new project `MyControls`.</span></span>  
  
4.  <span data-ttu-id="add16-135">Konum için uygun şekilde adlandırılmış bir üst düzey klasör gibi belirtin `WpfHostingWindowsFormsControl`.</span><span class="sxs-lookup"><span data-stu-id="add16-135">For the location, specify a conveniently named top-level folder, such as `WpfHostingWindowsFormsControl`.</span></span> <span data-ttu-id="add16-136">Daha sonra bu klasörde konak uygulama sokar.</span><span class="sxs-lookup"><span data-stu-id="add16-136">Later, you will put the host application in this folder.</span></span>  
  
5.  <span data-ttu-id="add16-137">Tıklatın **Tamam** projesi oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="add16-137">Click **OK** to create the project.</span></span> <span data-ttu-id="add16-138">Varsayılan proje adlı tek bir denetim içerir `UserControl1`.</span><span class="sxs-lookup"><span data-stu-id="add16-138">The default project contains a single control named `UserControl1`.</span></span>  
  
6.  <span data-ttu-id="add16-139">Çözüm Gezgini'nde, yeniden adlandırma `UserControl1` için `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="add16-139">In Solution Explorer, rename `UserControl1` to `MyControl1`.</span></span>  
  
 <span data-ttu-id="add16-140">Projeniz aşağıdaki sistem DLL'leri başvurular olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="add16-140">Your project should have references to the following system DLLs.</span></span> <span data-ttu-id="add16-141">Bu DLL'ler birini varsayılan olarak dahil edilmezse, bunları projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="add16-141">If any of these DLLs are not included by default, add them to the project.</span></span>  
  
-   <span data-ttu-id="add16-142">Sistem</span><span class="sxs-lookup"><span data-stu-id="add16-142">System</span></span>  
  
-   <span data-ttu-id="add16-143">System.Data</span><span class="sxs-lookup"><span data-stu-id="add16-143">System.Data</span></span>  
  
-   <span data-ttu-id="add16-144">System.Drawing</span><span class="sxs-lookup"><span data-stu-id="add16-144">System.Drawing</span></span>  
  
-   <span data-ttu-id="add16-145">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="add16-145">System.Windows.Forms</span></span>  
  
-   <span data-ttu-id="add16-146">System.Xml</span><span class="sxs-lookup"><span data-stu-id="add16-146">System.Xml</span></span>  
  
### <a name="adding-controls-to-the-form"></a><span data-ttu-id="add16-147">Forma denetim ekleme</span><span class="sxs-lookup"><span data-stu-id="add16-147">Adding Controls to the Form</span></span>  
 <span data-ttu-id="add16-148">Forma denetim eklemek için:</span><span class="sxs-lookup"><span data-stu-id="add16-148">To add controls to the form:</span></span>  
  
-   <span data-ttu-id="add16-149">Açık `MyControl1` Tasarımcısı'nda.</span><span class="sxs-lookup"><span data-stu-id="add16-149">Open `MyControl1` in the designer.</span></span>  
  
 <span data-ttu-id="add16-150">Beş eklemek <xref:System.Windows.Forms.Label> denetimleri ve karşılık gelen <xref:System.Windows.Forms.TextBox> boyutlandırılmış ve Yukarıdaki çizimde, formdaki oldukları gibi düzenlenmiş denetimleri.</span><span class="sxs-lookup"><span data-stu-id="add16-150">Add five <xref:System.Windows.Forms.Label> controls and their corresponding <xref:System.Windows.Forms.TextBox> controls, sized and arranged as they are in the preceding illustration, on the form.</span></span> <span data-ttu-id="add16-151">Örnekte, <xref:System.Windows.Forms.TextBox> denetimleri adlandırılır:</span><span class="sxs-lookup"><span data-stu-id="add16-151">In the example, the <xref:System.Windows.Forms.TextBox> controls are named:</span></span>  
  
-   `txtName`  
  
-   `txtAddress`  
  
-   `txtCity`  
  
-   `txtState`  
  
-   `txtZip`  
  
 <span data-ttu-id="add16-152">İki eklemek <xref:System.Windows.Forms.Button> etiketli denetimleri **Tamam** ve **iptal**.</span><span class="sxs-lookup"><span data-stu-id="add16-152">Add two <xref:System.Windows.Forms.Button> controls labeled **OK** and **Cancel**.</span></span> <span data-ttu-id="add16-153">Örnekte, düğme adlardır `btnOK` ve `btnCancel`sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="add16-153">In the example, the button names are `btnOK` and `btnCancel`, respectively.</span></span>  
  
### <a name="implementing-the-supporting-code"></a><span data-ttu-id="add16-154">Destek kodunu uygulama</span><span class="sxs-lookup"><span data-stu-id="add16-154">Implementing the Supporting Code</span></span>  
 <span data-ttu-id="add16-155">Formu kod görünümünde açın.</span><span class="sxs-lookup"><span data-stu-id="add16-155">Open the form in code view.</span></span> <span data-ttu-id="add16-156">Denetimin toplanan verileri kendi konağına özel yükselterek döndürür `OnButtonClick` olay.</span><span class="sxs-lookup"><span data-stu-id="add16-156">The control returns the collected data to its host by raising the custom `OnButtonClick` event.</span></span> <span data-ttu-id="add16-157">Verileri olay bağımsız değişken nesnesinde yer alır.</span><span class="sxs-lookup"><span data-stu-id="add16-157">The data is contained in the event argument object.</span></span> <span data-ttu-id="add16-158">Aşağıdaki kod, olay ve temsilci bildirimi gösterir.</span><span class="sxs-lookup"><span data-stu-id="add16-158">The following code shows the event and delegate declaration.</span></span>  
  
 <span data-ttu-id="add16-159">Aşağıdaki kodu ekleyin `MyControl1` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="add16-159">Add the following code to the `MyControl1` class.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#2)]
 [!code-vb[WpfHostingWindowsFormsControl#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#2)]  
  
 <span data-ttu-id="add16-160">`MyControlEventArgs` Sınıfı ana bilgisayara döndürülecek bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="add16-160">The `MyControlEventArgs` class contains the information to be returned to the host.</span></span>  
  
 <span data-ttu-id="add16-161">Aşağıdaki sınıf forma ekleyin.</span><span class="sxs-lookup"><span data-stu-id="add16-161">Add the following class to the form.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#3)]
 [!code-vb[WpfHostingWindowsFormsControl#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#3)]  
  
 <span data-ttu-id="add16-162">Kullanıcı tıkladığında **Tamam** veya **iptal** düğmesini <xref:System.Windows.Forms.Control.Click> olay işleyicileri oluşturma bir `MyControlEventArgs` verileri içeren nesne ve başlatır `OnButtonClick` olay.</span><span class="sxs-lookup"><span data-stu-id="add16-162">When the user clicks the **OK** or **Cancel** button, the <xref:System.Windows.Forms.Control.Click> event handlers create a `MyControlEventArgs` object that contains the data and raises the `OnButtonClick` event.</span></span> <span data-ttu-id="add16-163">İki işleyicinin arasındaki tek fark olay bağımsız değişkeninin olduğu `IsOK` özelliği.</span><span class="sxs-lookup"><span data-stu-id="add16-163">The only difference between the two handlers is the event argument's `IsOK` property.</span></span> <span data-ttu-id="add16-164">Bu özelliği, hangi düğmenin tıklandığını belirleme için ana sağlar.</span><span class="sxs-lookup"><span data-stu-id="add16-164">This property enables the host to determine which button was clicked.</span></span> <span data-ttu-id="add16-165">Ayarlanır `true` için **Tamam** düğmesi ve `false` için **iptal** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="add16-165">It is set to `true` for the **OK** button, and `false` for the **Cancel** button.</span></span> <span data-ttu-id="add16-166">Aşağıdaki kod iki düğmesi işleyicileri gösterir.</span><span class="sxs-lookup"><span data-stu-id="add16-166">The following code shows the two button handlers.</span></span>  
  
 <span data-ttu-id="add16-167">Aşağıdaki kodu ekleyin `MyControl1` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="add16-167">Add the following code to the `MyControl1` class.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#4)]
 [!code-vb[WpfHostingWindowsFormsControl#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#4)]  
  
### <a name="giving-the-assembly-a-strong-name-and-building-the-assembly"></a><span data-ttu-id="add16-168">Derleme güçlü bir ad verip ve bütünleştirilmiş kod oluşturma</span><span class="sxs-lookup"><span data-stu-id="add16-168">Giving the Assembly a Strong Name and Building the Assembly</span></span>  
 <span data-ttu-id="add16-169">Bu derleme tarafından başvurulan bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama, güçlü bir adı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="add16-169">For this assembly to be referenced by a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application, it must have a strong name.</span></span> <span data-ttu-id="add16-170">Güçlü bir ad oluşturmak için Sn.exe ile bir anahtar dosyası oluşturun ve projenize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="add16-170">To create a strong name, create a key file with Sn.exe and add it to your project.</span></span>  
  
1.  <span data-ttu-id="add16-171">Açık bir [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] komut istemi.</span><span class="sxs-lookup"><span data-stu-id="add16-171">Open a [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] command prompt.</span></span> <span data-ttu-id="add16-172">Bunu yapmak için tıklatın **Başlat** menüsüne ve ardından **tüm programlar/Microsoft Visual Studio 2010/Visual Studio Araçları/Visual Studio komut istemi**.</span><span class="sxs-lookup"><span data-stu-id="add16-172">To do so, click the **Start** menu, and then select **All Programs/Microsoft Visual Studio 2010/Visual Studio Tools/Visual Studio Command Prompt**.</span></span> <span data-ttu-id="add16-173">Bir konsol penceresi özelleştirilmiş ortam değişkenleri ile başlatır.</span><span class="sxs-lookup"><span data-stu-id="add16-173">This launches a console window with customized environment variables.</span></span>  
  
2.  <span data-ttu-id="add16-174">Komut isteminde kullanın `cd` proje klasörünüzdeki Git komutu.</span><span class="sxs-lookup"><span data-stu-id="add16-174">At the command prompt, use the `cd` command to go to your project folder.</span></span>  
  
3.  <span data-ttu-id="add16-175">Aşağıdaki komutu çalıştırarak MyControls.snk adlı bir anahtar dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="add16-175">Generate a key file named MyControls.snk by running the following command.</span></span>  
  
    ```  
    Sn.exe -k MyControls.snk  
    ```  
  
4.  <span data-ttu-id="add16-176">Anahtar dosyası projenize eklemek için Çözüm Gezgini'nde proje adına sağ tıklayın ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="add16-176">To include the key file in your project, right-click the project name in Solution Explorer and then click **Properties**.</span></span> <span data-ttu-id="add16-177">Proje Tasarımcısı'nda tıklatın **imzalama** sekmesine **derlemeyi imzalamak** onay kutusunu işaretleyin ve ardından anahtar dosyanızı göz atın.</span><span class="sxs-lookup"><span data-stu-id="add16-177">In the Project Designer, click the **Signing** tab, select the **Sign the assembly** check box and then browse to your key file.</span></span>  
  
5.  <span data-ttu-id="add16-178">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="add16-178">Build the solution.</span></span> <span data-ttu-id="add16-179">Yapı MyControls.dll adlı bir DLL oluşturur.</span><span class="sxs-lookup"><span data-stu-id="add16-179">The build will produce a DLL named MyControls.dll.</span></span>  
  
## <a name="implementing-the-wpf-host-application"></a><span data-ttu-id="add16-180">WPF konak uygulamayı uygulama</span><span class="sxs-lookup"><span data-stu-id="add16-180">Implementing the WPF Host Application</span></span>  
 <span data-ttu-id="add16-181">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Uygulamanız tarafından kullanılan ana bilgisayar <xref:System.Windows.Forms.Integration.WindowsFormsHost> barındırmak için `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="add16-181">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] host application uses the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control to host `MyControl1`.</span></span> <span data-ttu-id="add16-182">Uygulama tanıtıcıları `OnButtonClick` denetimden verileri almak için olay.</span><span class="sxs-lookup"><span data-stu-id="add16-182">The application handles the `OnButtonClick` event to receive the data from the control.</span></span> <span data-ttu-id="add16-183">Denetimin özelliklerinden bazıları değiştirebilmek için seçenek düğmeleri koleksiyonu da sahip [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="add16-183">It also has a collection of option buttons that enable you to change some of the control's properties from the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="add16-184">Aşağıdaki çizimde tamamlanmış uygulamayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="add16-184">The following illustration shows the finished application.</span></span>  
  
 <span data-ttu-id="add16-185">![Bir denetim katıştırılmış bir WPF sayfasında](../../../../docs/framework/wpf/advanced/media/avalonhost.gif "AvalonHost")</span><span class="sxs-lookup"><span data-stu-id="add16-185">![A control embedded in a WPF page](../../../../docs/framework/wpf/advanced/media/avalonhost.gif "AvalonHost")</span></span>  
<span data-ttu-id="add16-186">Tam uygulama denetimi gösteren WPF uygulamasında katıştırılmış</span><span class="sxs-lookup"><span data-stu-id="add16-186">The complete application, showing the control embedded in the WPF application</span></span>  
  
### <a name="creating-the-project"></a><span data-ttu-id="add16-187">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="add16-187">Creating the Project</span></span>  
 <span data-ttu-id="add16-188">Projeyi başlatmak için:</span><span class="sxs-lookup"><span data-stu-id="add16-188">To start the project:</span></span>  
  
1.  <span data-ttu-id="add16-189">Açık [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]seçip **yeni proje**.</span><span class="sxs-lookup"><span data-stu-id="add16-189">Open [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], and select **New Project**.</span></span>  
  
2.  <span data-ttu-id="add16-190">Penceresi kategorisindeki seçmek **WPF uygulaması** şablonu.</span><span class="sxs-lookup"><span data-stu-id="add16-190">In the Window category, select the **WPF Application** template.</span></span>
  
3.  <span data-ttu-id="add16-191">Yeni proje adı `WpfHost`.</span><span class="sxs-lookup"><span data-stu-id="add16-191">Name the new project `WpfHost`.</span></span>  
  
4.  <span data-ttu-id="add16-192">Konum için MyControls projeyi içeren aynı üst düzey klasörü belirtin.</span><span class="sxs-lookup"><span data-stu-id="add16-192">For the location, specify the same top-level folder that contains the MyControls project.</span></span>  
  
5.  <span data-ttu-id="add16-193">Tıklatın **Tamam** projesi oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="add16-193">Click **OK** to create the project.</span></span>  
  
 <span data-ttu-id="add16-194">İçeren DLL başvurular ekleyin gerekir `MyControl1` ve diğer derlemeler.</span><span class="sxs-lookup"><span data-stu-id="add16-194">You also need to add references to the DLL that contains `MyControl1` and other assemblies.</span></span>  
  
1.  <span data-ttu-id="add16-195">Çözüm Gezgini'nde proje adına sağ tıklayıp **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="add16-195">Right-click the project name in Solution Explorer and select **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="add16-196">Tıklatın **Gözat** sekmesini tıklatın ve MyControls.dll içeren klasöre göz atın.</span><span class="sxs-lookup"><span data-stu-id="add16-196">Click the **Browse** tab, and browse to the folder that contains MyControls.dll.</span></span> <span data-ttu-id="add16-197">Bu kılavuz için bu klasör MyControls\bin\Debug'dır.</span><span class="sxs-lookup"><span data-stu-id="add16-197">For this walkthrough, this folder is MyControls\bin\Debug.</span></span>  
  
3.  <span data-ttu-id="add16-198">MyControls.dll seçin ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="add16-198">Select MyControls.dll, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="add16-199">WindowsFormsIntegration.dll adlı WindowsFormsIntegration derlemesine başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="add16-199">Add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>  
  
### <a name="implementing-the-basic-layout"></a><span data-ttu-id="add16-200">Temel düzeni uygulama</span><span class="sxs-lookup"><span data-stu-id="add16-200">Implementing the Basic Layout</span></span>  
 <span data-ttu-id="add16-201">[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] Ana uygulama MainWindow.xaml içinde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="add16-201">The [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] of the host application is implemented in MainWindow.xaml.</span></span> <span data-ttu-id="add16-202">Bu dosyayı içeren [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] düzenini tanımlar ve barındıran biçimlendirmesi [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] denetim.</span><span class="sxs-lookup"><span data-stu-id="add16-202">This file contains [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] markup that defines the layout, and hosts the [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] control.</span></span> <span data-ttu-id="add16-203">Uygulama, üç bölgeye ayrılmıştır:</span><span class="sxs-lookup"><span data-stu-id="add16-203">The application is divided into three regions:</span></span>  
  
-   <span data-ttu-id="add16-204">**Denetim özelliklerini** paneli denetimden çeşitli özelliklerini değiştirmek için kullanabileceğiniz seçenek düğmeleri koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="add16-204">The **Control Properties** panel, which contains a collection of option buttons that you can use to modify various properties of the hosted control.</span></span>  
  
-   <span data-ttu-id="add16-205">**Denetim verileri** birkaç içeren paneli <xref:System.Windows.Controls.TextBlock> verileri görüntülemek öğeleri barındırılan denetiminden döndürdü.</span><span class="sxs-lookup"><span data-stu-id="add16-205">The **Data from Control** panel, which contains several <xref:System.Windows.Controls.TextBlock> elements that display the data returned from the hosted control.</span></span>  
  
-   <span data-ttu-id="add16-206">Barındırılan denetimin kendisi.</span><span class="sxs-lookup"><span data-stu-id="add16-206">The hosted control itself.</span></span>  
  
 <span data-ttu-id="add16-207">Temel düzeni aşağıdaki XAML'de gösterilir.</span><span class="sxs-lookup"><span data-stu-id="add16-207">The basic layout is shown in the following XAML.</span></span> <span data-ttu-id="add16-208">Gerekli biçimlendirme ana bilgisayara `MyControl1` Bu örnekte atlanır, ancak daha sonra açıklanacaktır.</span><span class="sxs-lookup"><span data-stu-id="add16-208">The markup that is needed to host `MyControl1` is omitted from this example, but will be discussed later.</span></span>  
  
 <span data-ttu-id="add16-209">MainWindow.xaml XAML'de aşağıdakiyle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="add16-209">Replace the XAML in MainWindow.xaml with the following.</span></span> <span data-ttu-id="add16-210">Visual Basic kullanıyorsanız, sınıf için değiştirme `x:Class="MainWindow"`.</span><span class="sxs-lookup"><span data-stu-id="add16-210">If you are using Visual Basic, change the class to `x:Class="MainWindow"`.</span></span>  
  
 [!code-xaml[WpfHostingWindowsFormsControl#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#100)]  
  
 <span data-ttu-id="add16-211">İlk <xref:System.Windows.Controls.StackPanel> öğesi içeren birkaç kümesi <xref:System.Windows.Controls.RadioButton> denetimden çeşitli varsayılan özelliklerini değiştirmek etkinleştirmeniz kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="add16-211">The first <xref:System.Windows.Controls.StackPanel> element contains several sets of <xref:System.Windows.Controls.RadioButton> controls that enable you to modify various default properties of the hosted control.</span></span> <span data-ttu-id="add16-212">Tarafından izlenen bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi, hangi ana bilgisayarların `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="add16-212">That is followed by a <xref:System.Windows.Forms.Integration.WindowsFormsHost> element, which hosts `MyControl1`.</span></span> <span data-ttu-id="add16-213">En son <xref:System.Windows.Controls.StackPanel> öğesi içeren birkaç <xref:System.Windows.Controls.TextBlock> barındırılan denetim tarafından döndürülen verileri görüntüleyen öğeleri.</span><span class="sxs-lookup"><span data-stu-id="add16-213">The final <xref:System.Windows.Controls.StackPanel> element contains several <xref:System.Windows.Controls.TextBlock> elements that display the data that is returned by the hosted control.</span></span> <span data-ttu-id="add16-214">Öğeleri sıralama ve <xref:System.Windows.Controls.DockPanel.Dock%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> öznitelik ayarlarını boşluklar veya bozulma olmadan bu denetimden penceresine ekleme.</span><span class="sxs-lookup"><span data-stu-id="add16-214">The ordering of the elements and the <xref:System.Windows.Controls.DockPanel.Dock%2A> and <xref:System.Windows.FrameworkElement.Height%2A> attribute settings embed the hosted control into the window with no gaps or distortion.</span></span>  
  
#### <a name="hosting-the-control"></a><span data-ttu-id="add16-215">Denetimi barındırma</span><span class="sxs-lookup"><span data-stu-id="add16-215">Hosting the Control</span></span>  
 <span data-ttu-id="add16-216">Önceki XAML aşağıdaki düzenlenmiş sürümü için gerekli olan öğeleri odaklanır ana bilgisayara `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="add16-216">The following edited version of the previous XAML focuses on the elements that are needed to host `MyControl1`.</span></span>  
  
 [!code-xaml[WpfHostingWindowsFormsControl#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#101)]  
[!code-xaml[WpfHostingWindowsFormsControl#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#102)]  
  
 <span data-ttu-id="add16-217">`xmlns` Ad alanı eşleme özniteliği için bir başvuru oluşturur `MyControls` barındırılan denetimi içeren ad alanı.</span><span class="sxs-lookup"><span data-stu-id="add16-217">The `xmlns` namespace mapping attribute creates a reference to the `MyControls` namespace that contains the hosted control.</span></span> <span data-ttu-id="add16-218">Bu eşlemeyi temsil eden sağlar `MyControl1` içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] olarak `<mcl:MyControl1>`.</span><span class="sxs-lookup"><span data-stu-id="add16-218">This mapping enables you to represent `MyControl1` in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] as `<mcl:MyControl1>`.</span></span>  
  
 <span data-ttu-id="add16-219">XAML'de iki öğe barındırmayı işler:</span><span class="sxs-lookup"><span data-stu-id="add16-219">Two elements in the XAML handle the hosting:</span></span>  
  
-   <span data-ttu-id="add16-220">`WindowsFormsHost`temsil eden <xref:System.Windows.Forms.Integration.WindowsFormsHost> konağa etkinleştirir öğesi bir [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] denetim bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="add16-220">`WindowsFormsHost` represents the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element that enables you to host a [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] control in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>  
  
-   <span data-ttu-id="add16-221">`mcl:MyControl1`, temsil eden `MyControl1`, eklenen <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğenin alt koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="add16-221">`mcl:MyControl1`, which represents `MyControl1`, is added to the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's child collection.</span></span> <span data-ttu-id="add16-222">Sonuç olarak, bu [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] denetim parçası olarak işlenen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pencere ve iletişim kurabilen uygulama denetiminden.</span><span class="sxs-lookup"><span data-stu-id="add16-222">As a result, this [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] control is rendered as part of the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] window, and you can communicate with the control from the application.</span></span>  
  
### <a name="implementing-the-code-behind-file"></a><span data-ttu-id="add16-223">Arka plan kod dosyası uygulama</span><span class="sxs-lookup"><span data-stu-id="add16-223">Implementing the Code-Behind File</span></span>  
 <span data-ttu-id="add16-224">Arka plan kodu dosyasını MainWindow.xaml.vb veya MainWindow.xaml.cs, işlevselliğini uygulayan yordam kodunu içeren [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] önceki bölümde açıklanan.</span><span class="sxs-lookup"><span data-stu-id="add16-224">The code-behind file, MainWindow.xaml.vb or MainWindow.xaml.cs, contains the procedural code that implements the functionality of the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] discussed in the preceding section.</span></span> <span data-ttu-id="add16-225">Birincil görevler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="add16-225">The primary tasks are:</span></span>  
  
-   <span data-ttu-id="add16-226">Bir olay işleyicisi ekleme `MyControl1`'s `OnButtonClick` olay.</span><span class="sxs-lookup"><span data-stu-id="add16-226">Attaching an event handler to `MyControl1`'s `OnButtonClick` event.</span></span>  
  
-   <span data-ttu-id="add16-227">Çeşitli özelliklerini değiştirme `MyControl1`bağlı olarak seçenek düğmeleri koleksiyonunu nasıl ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="add16-227">Modifying various properties of `MyControl1`, based on how the collection of option buttons are set.</span></span>  
  
-   <span data-ttu-id="add16-228">Verileri görüntüleme denetim tarafından toplanır.</span><span class="sxs-lookup"><span data-stu-id="add16-228">Displaying the data collected by the control.</span></span>  
  
#### <a name="initializing-the-application"></a><span data-ttu-id="add16-229">Uygulama başlatma</span><span class="sxs-lookup"><span data-stu-id="add16-229">Initializing the Application</span></span>  
 <span data-ttu-id="add16-230">Bir pencere için olay işleyicisini başlatma kodu bulunan <xref:System.Windows.FrameworkElement.Loaded> olay ve bir olay işleyicisi denetimin ekler `OnButtonClick` olay.</span><span class="sxs-lookup"><span data-stu-id="add16-230">The initialization code is contained in an event handler for the window's <xref:System.Windows.FrameworkElement.Loaded> event and attaches an event handler to the control's `OnButtonClick` event.</span></span>  
  
 <span data-ttu-id="add16-231">MainWindow.xaml.vb veya MainWindow.xaml.cs, aşağıdaki kodu ekleyin `MainWindow` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="add16-231">In MainWindow.xaml.vb or MainWindow.xaml.cs, add the following code to the `MainWindow` class.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#11)]
 [!code-vb[WpfHostingWindowsFormsControl#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#11)]  
  
 <span data-ttu-id="add16-232">Çünkü [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] önceden eklenen ele alınan `MyControl1` için <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğenin alt öğe koleksiyonunu çevirebilirsiniz <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğenin <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> başvuru almak için `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="add16-232">Because the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] discussed previously added `MyControl1` to the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's child element collection, you can cast the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> to get the reference to `MyControl1`.</span></span> <span data-ttu-id="add16-233">Bir olay işleyicisi eklemek için bu başvuru sonra kullanabileceğiniz `OnButtonClick`.</span><span class="sxs-lookup"><span data-stu-id="add16-233">You can then use that reference to attach an event handler to `OnButtonClick`.</span></span>  
  
 <span data-ttu-id="add16-234">Denetim kendisine başvuru sağlamanın yanı sıra <xref:System.Windows.Forms.Integration.WindowsFormsHost> uygulamadan işleyebileceğiniz denetimin özelliklerini sayısını kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="add16-234">In addition to providing a reference to the control itself, <xref:System.Windows.Forms.Integration.WindowsFormsHost> exposes a number of the control's properties, which you can manipulate from the application.</span></span> <span data-ttu-id="add16-235">Başlangıç kodu özel genel değişkenler uygulama daha sonra kullanmak için bu değerleri atar.</span><span class="sxs-lookup"><span data-stu-id="add16-235">The initialization code assigns those values to private global variables for later use in the application.</span></span>  
  
 <span data-ttu-id="add16-236">Türler kolayca erişebilmeniz `MyControls` DLL, aşağıdakileri ekleyin `Imports` veya `using` dosyanın en üstüne ifadesine.</span><span class="sxs-lookup"><span data-stu-id="add16-236">So that you can easily access the types in the `MyControls` DLL, add the following `Imports` or `using` statement to the top of the file.</span></span>  
  
```vb  
Imports MyControls  
```  
  
```csharp  
using MyControls;  
```  
  
#### <a name="handling-the-onbuttonclick-event"></a><span data-ttu-id="add16-237">OnButtonClick olayını işleme</span><span class="sxs-lookup"><span data-stu-id="add16-237">Handling the OnButtonClick Event</span></span>  
 <span data-ttu-id="add16-238">`MyControl1`başlatır `OnButtonClick` kullanıcı ya da denetim düğmesini tıklattığında olay.</span><span class="sxs-lookup"><span data-stu-id="add16-238">`MyControl1` raises the `OnButtonClick` event when the user clicks either of the control's buttons.</span></span>  
  
 <span data-ttu-id="add16-239">Aşağıdaki kodu ekleyin `MainWindow` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="add16-239">Add the following code to the `MainWindow` class.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#12)]
 [!code-vb[WpfHostingWindowsFormsControl#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#12)]  
  
 <span data-ttu-id="add16-240">Metin kutularındaki veri paketlenmiştir `MyControlEventArgs` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="add16-240">The data in the text boxes is packed into the `MyControlEventArgs` object.</span></span> <span data-ttu-id="add16-241">Kullanıcı tıklarsa **Tamam** düğmesi olay işleyicisi verileri ayıklar ve panelinde görüntüler `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="add16-241">If the user clicks the **OK** button, the event handler extracts the data and displays it in the panel below `MyControl1`.</span></span>  
  
#### <a name="modifying-the-controls-properties"></a><span data-ttu-id="add16-242">Denetimin özelliklerini değiştirme</span><span class="sxs-lookup"><span data-stu-id="add16-242">Modifying the Control’s Properties</span></span>  
 <span data-ttu-id="add16-243"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi birkaç barındırılan denetimin varsayılan özelliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="add16-243">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element exposes several of the hosted control's default properties.</span></span> <span data-ttu-id="add16-244">Sonuç olarak, uygulamanızın stil daha yakından eşleşecek şekilde denetiminin görünümünü değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="add16-244">As a result, you can change the appearance of the control to match the style of your application more closely.</span></span> <span data-ttu-id="add16-245">Sol bölmedeki seçenek düğmeleri kümesi birkaç renk ve yazı tipi özelliklerini değiştirmek kullanıcının etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="add16-245">The sets of option buttons in the left panel enable the user to modify several color and font properties.</span></span> <span data-ttu-id="add16-246">Her düğme için bir işleyici olarak ayarlanmış <xref:System.Windows.Controls.Primitives.ButtonBase.Click> kullanıcının seçenek düğmesi seçimlerini algılayan ve karşılık gelen özelliği denetimde değiştiren olay.</span><span class="sxs-lookup"><span data-stu-id="add16-246">Each set of buttons has a handler for the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, which detects the user's option button selections and changes the corresponding property on the control.</span></span>  
  
 <span data-ttu-id="add16-247">Aşağıdaki kodu ekleyin `MainWindow` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="add16-247">Add the following code to the `MainWindow` class.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#13)]
 [!code-vb[WpfHostingWindowsFormsControl#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#13)]  
  
 <span data-ttu-id="add16-248">Derleme ve uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="add16-248">Build and run the application.</span></span> <span data-ttu-id="add16-249">Windows Forms Bileşik denetiminde biraz metin ekleyin ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="add16-249">Add some text in the Windows Forms composite control and then click **OK**.</span></span> <span data-ttu-id="add16-250">Metin etiketler görünür.</span><span class="sxs-lookup"><span data-stu-id="add16-250">The text appears in the labels.</span></span> <span data-ttu-id="add16-251">Denetim etkisini görmek için farklı radyo düğmelerini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="add16-251">Click the different radio buttons to see the effect on the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="add16-252">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="add16-252">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="add16-253">WPF Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="add16-253">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="add16-254">İzlenecek yol: WPF bir Windows Forms denetimi barındırma</span><span class="sxs-lookup"><span data-stu-id="add16-254">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)  
 [<span data-ttu-id="add16-255">İzlenecek yol: Windows Forms içerisinde WPF bileşik denetimi barındırma</span><span class="sxs-lookup"><span data-stu-id="add16-255">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
