---
title: "İzlenecek yol: Karma Uygulamayı Yerelleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- localization [WPF interoperability]
- hybrid applications [WPF interoperability]
ms.assetid: fbc0c54e-930a-4c13-8e9c-27b83665010a
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9f9bb7588ef1f6962a5cd55196154ac7f666d53b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-localizing-a-hybrid-application"></a><span data-ttu-id="ea146-102">İzlenecek yol: Karma Uygulamayı Yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="ea146-102">Walkthrough: Localizing a Hybrid Application</span></span>
<span data-ttu-id="ea146-103">Bu kılavuz, yerelleştirme gösterilmektedir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğelerinde bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]-karma tabanlı.</span><span class="sxs-lookup"><span data-stu-id="ea146-103">This walkthrough shows you how to localize [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elements in a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]-based hybrid application.</span></span>  
  
 <span data-ttu-id="ea146-104">Bu örneklerde gösterilen görevler aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="ea146-104">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="ea146-105">Oluşturma [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] konak projesi.</span><span class="sxs-lookup"><span data-stu-id="ea146-105">Creating the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] host project.</span></span>  
  
-   <span data-ttu-id="ea146-106">Yerelleştirilebilir İçerik ekleme.</span><span class="sxs-lookup"><span data-stu-id="ea146-106">Adding localizable content.</span></span>  
  
-   <span data-ttu-id="ea146-107">Yerelleştirme etkinleştiriliyor.</span><span class="sxs-lookup"><span data-stu-id="ea146-107">Enabling localization.</span></span>  
  
-   <span data-ttu-id="ea146-108">Kaynak tanımlayıcılar atama.</span><span class="sxs-lookup"><span data-stu-id="ea146-108">Assigning resource identifiers.</span></span>  
  
-   <span data-ttu-id="ea146-109">Uydu derlemesi üretmek için LocBaml aracını kullanma.</span><span class="sxs-lookup"><span data-stu-id="ea146-109">Using the LocBaml tool to produce a satellite assembly.</span></span>  
  
 <span data-ttu-id="ea146-110">Bu örneklerde gösterilen görevlerin tam kod listesi için bkz: [karma uygulama örneği yerelleştirme](http://go.microsoft.com/fwlink/?LinkID=160015).</span><span class="sxs-lookup"><span data-stu-id="ea146-110">For a complete code listing of the tasks illustrated in this walkthrough, see [Localizing a Hybrid Application Sample](http://go.microsoft.com/fwlink/?LinkID=160015).</span></span>  
  
 <span data-ttu-id="ea146-111">İşiniz bittiğinde, yerelleştirilmiş karma uygulamaya sahip olacaksınız.</span><span class="sxs-lookup"><span data-stu-id="ea146-111">When you are finished, you will have a localized hybrid application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ea146-112">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="ea146-112">Prerequisites</span></span>  
 <span data-ttu-id="ea146-113">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="ea146-113">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)]<span data-ttu-id="ea146-114">.</span><span class="sxs-lookup"><span data-stu-id="ea146-114">.</span></span>  
  
## <a name="creating-the-windows-forms-host-project"></a><span data-ttu-id="ea146-115">Windows Forms konak projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="ea146-115">Creating the Windows Forms Host Project</span></span>  
 <span data-ttu-id="ea146-116">İlk adım oluşturmaktır [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] uygulama proje ve ekleme bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğesi yerelleştirme içeriğe sahip.</span><span class="sxs-lookup"><span data-stu-id="ea146-116">The first step is to create the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] application project and add a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element with content that you will localize.</span></span>  
  
#### <a name="to-create-the-host-project"></a><span data-ttu-id="ea146-117">Konak projesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="ea146-117">To create the host project</span></span>  
  
1.  <span data-ttu-id="ea146-118">Adlı bir WPF uygulaması projesi oluşturduğunuzda `LocalizingWpfInWf`.</span><span class="sxs-lookup"><span data-stu-id="ea146-118">Create a WPF Application project named `LocalizingWpfInWf`.</span></span> <span data-ttu-id="ea146-119">Daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span><span class="sxs-lookup"><span data-stu-id="ea146-119">For more information, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="ea146-120">Ekleme bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> adlı öğe `SimpleControl` projeye.</span><span class="sxs-lookup"><span data-stu-id="ea146-120">Add a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.UserControl> element called `SimpleControl` to the project.</span></span>  
  
3.  <span data-ttu-id="ea146-121">Kullanım <xref:System.Windows.Forms.Integration.ElementHost> yerleştirmek için denetim bir `SimpleControl` öğesi form üzerinde.</span><span class="sxs-lookup"><span data-stu-id="ea146-121">Use the <xref:System.Windows.Forms.Integration.ElementHost> control to place a `SimpleControl` element on the form.</span></span> <span data-ttu-id="ea146-122">Daha fazla bilgi için bkz: [izlenecek yol: Windows Forms'ta 3-b WPF bileşik denetim barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="ea146-122">For more information, see [Walkthrough: Hosting a 3-D WPF Composite Control in Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).</span></span>  
  
## <a name="adding-localizable-content"></a><span data-ttu-id="ea146-123">Yerelleştirilebilir İçerik ekleme</span><span class="sxs-lookup"><span data-stu-id="ea146-123">Adding Localizable Content</span></span>  
 <span data-ttu-id="ea146-124">Sonra ekleyeceksiniz bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] etiket denetimini ve ayarlayın [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğenin içeriğini yerelleştirilebilir dize.</span><span class="sxs-lookup"><span data-stu-id="ea146-124">Next, you will add a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] label control and set the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element's content to a localizable string.</span></span>  
  
#### <a name="to-add-localizable-content"></a><span data-ttu-id="ea146-125">Yerelleştirilebilir İçerik eklemek için</span><span class="sxs-lookup"><span data-stu-id="ea146-125">To add localizable content</span></span>  
  
1.  <span data-ttu-id="ea146-126">Çözüm Gezgini'nde çift tıklayarak **SimpleControl.XAML'e** içinde açmak için [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ea146-126">In Solution Explorer, double-click **SimpleControl.xaml** to open it in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
2.  <span data-ttu-id="ea146-127">İçeriğini ayarlayın <xref:System.Windows.Controls.Button> aşağıdaki kodu kullanarak denetim.</span><span class="sxs-lookup"><span data-stu-id="ea146-127">Set the content of the <xref:System.Windows.Controls.Button> control using the following code.</span></span>  
  
     [!code-xaml[LocalizingWpfInWf#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl0.xaml#10)]  
  
3.  <span data-ttu-id="ea146-128">Çözüm Gezgini'nde çift tıklayarak **Form1** Windows Forms Tasarımcısı'nda açmak için.</span><span class="sxs-lookup"><span data-stu-id="ea146-128">In Solution Explorer, double-click **Form1** to open it in the Windows Forms Designer.</span></span>  
  
4.  <span data-ttu-id="ea146-129">Araç kutusunu açın ve çift **etiket** forma etiket denetimi eklemek için.</span><span class="sxs-lookup"><span data-stu-id="ea146-129">Open the Toolbox and double-click **Label** to add a label control to the form.</span></span> <span data-ttu-id="ea146-130">Değerini kendi <xref:System.Windows.Forms.Control.Text%2A> özelliğine `"Hello"`.</span><span class="sxs-lookup"><span data-stu-id="ea146-130">Set the value of its <xref:System.Windows.Forms.Control.Text%2A> property to `"Hello"`.</span></span>  
  
5.  <span data-ttu-id="ea146-131">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="ea146-131">Press F5 to build and run the application.</span></span>  
  
     <span data-ttu-id="ea146-132">Her iki `SimpleControl` öğesini ve etiket denetimi görüntüleme metni **"Merhaba"**.</span><span class="sxs-lookup"><span data-stu-id="ea146-132">Both the `SimpleControl` element and the label control display the text **"Hello"**.</span></span>  
  
## <a name="enabling-localization"></a><span data-ttu-id="ea146-133">Yerelleştirme etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="ea146-133">Enabling Localization</span></span>  
 <span data-ttu-id="ea146-134">Windows Form Tasarımcısı yardımcı derlemede yerelleştirme etkinleştirmek için ayarlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="ea146-134">The Windows Forms Designer provides settings for enabling localization in a satellite assembly.</span></span>  
  
#### <a name="to-enable-localization"></a><span data-ttu-id="ea146-135">Yerelleştirme etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="ea146-135">To enable localization</span></span>  
  
1.  <span data-ttu-id="ea146-136">Çözüm Gezgini'nde çift tıklayarak **Form1.cs** Windows Forms Tasarımcısı'nda açmak için.</span><span class="sxs-lookup"><span data-stu-id="ea146-136">In Solution Explorer, double-click **Form1.cs** to open it in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="ea146-137">Özellikler penceresinde formun değerini **yerelleştirilebilir** özelliğine `true`.</span><span class="sxs-lookup"><span data-stu-id="ea146-137">In the Properties window, set the value of the form's **Localizable** property to `true`.</span></span>  
  
3.  <span data-ttu-id="ea146-138">Özellikler penceresinde değerini **dil** özelliğine **İspanyolca (İspanya)**.</span><span class="sxs-lookup"><span data-stu-id="ea146-138">In the Properties window, set the value of the **Language** property to **Spanish (Spain)**.</span></span>  
  
4.  <span data-ttu-id="ea146-139">Windows Forms Tasarımcısı'nda etiket denetimi seçin.</span><span class="sxs-lookup"><span data-stu-id="ea146-139">In the Windows Forms Designer, select the label control.</span></span>  
  
5.  <span data-ttu-id="ea146-140">Özellikler penceresinde değerini <xref:System.Windows.Forms.Control.Text%2A> özelliğine `"Hola"`.</span><span class="sxs-lookup"><span data-stu-id="ea146-140">In the Properties window, set the value of the <xref:System.Windows.Forms.Control.Text%2A> property to `"Hola"`.</span></span>  
  
     <span data-ttu-id="ea146-141">Form1.es-ES.resx adlı yeni bir kaynak dosyası projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="ea146-141">A new resource file named Form1.es-ES.resx is added to the project.</span></span>  
  
6.  <span data-ttu-id="ea146-142">Çözüm Gezgini'nde sağ **Form1.cs** tıklatıp **görünümü kodu** Kod düzenleyicisinde açın.</span><span class="sxs-lookup"><span data-stu-id="ea146-142">In Solution Explorer, right-click **Form1.cs** and click **View Code** to open it in the Code Editor.</span></span>  
  
7.  <span data-ttu-id="ea146-143">Aşağıdaki kodu kopyalayın `Form1` çağrısının öncesine Oluşturucusu `InitializeComponent`.</span><span class="sxs-lookup"><span data-stu-id="ea146-143">Copy the following code into the `Form1` constructor, preceding the call to `InitializeComponent`.</span></span>  
  
     [!code-csharp[LocalizingWpfInWf#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/Form1.cs#2)]  
  
8.  <span data-ttu-id="ea146-144">Çözüm Gezgini'nde sağ **LocalizingWpfInWf** tıklatıp **projeyi**.</span><span class="sxs-lookup"><span data-stu-id="ea146-144">In Solution Explorer, right-click **LocalizingWpfInWf** and click **Unload Project**.</span></span>  
  
     <span data-ttu-id="ea146-145">Proje adı etiketli **(kullanılamaz)**.</span><span class="sxs-lookup"><span data-stu-id="ea146-145">The project name is labeled **(unavailable)**.</span></span>  
  
9. <span data-ttu-id="ea146-146">Sağ **LocalizingWpfInWf**, tıklatıp **LocalizingWpfInWf.csproj'yi**.</span><span class="sxs-lookup"><span data-stu-id="ea146-146">Right-click **LocalizingWpfInWf**, and click **Edit LocalizingWpfInWf.csproj**.</span></span>  
  
     <span data-ttu-id="ea146-147">Proje dosyası Kod Düzenleyicisi'nde açar.</span><span class="sxs-lookup"><span data-stu-id="ea146-147">The project file opens in the Code Editor.</span></span>  
  
10. <span data-ttu-id="ea146-148">Aşağıdaki satırı ilk kopyalama `PropertyGroup` proje dosyasında.</span><span class="sxs-lookup"><span data-stu-id="ea146-148">Copy the following line into the first `PropertyGroup` in the project file.</span></span>  
  
    ```xml  
    <UICulture>en-US</UICulture>   
    ```  
  
11. <span data-ttu-id="ea146-149">Proje dosyasını kaydedin ve kapatın.</span><span class="sxs-lookup"><span data-stu-id="ea146-149">Save the project file and close it.</span></span>  
  
12. <span data-ttu-id="ea146-150">Çözüm Gezgini'nde sağ **LocalizingWpfInWf** tıklatıp **projeyi yeniden yükle**.</span><span class="sxs-lookup"><span data-stu-id="ea146-150">In Solution Explorer, right-click **LocalizingWpfInWf** and click **Reload Project**.</span></span>  
  
## <a name="assigning-resource-identifiers"></a><span data-ttu-id="ea146-151">Kaynak tanımlayıcılar atama</span><span class="sxs-lookup"><span data-stu-id="ea146-151">Assigning Resource Identifiers</span></span>  
 <span data-ttu-id="ea146-152">Kaynak tanımlayıcılar kullanarak kaynak derlemelerine yerelleştirilebilir içeriğinizi eşleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ea146-152">You can map your localizable content to resource assemblies by using resource identifiers.</span></span> <span data-ttu-id="ea146-153">Belirttiğinizde kaynak tanımlayıcılarını MsBuild.exe uygulaması otomatik olarak atar. `updateuid` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="ea146-153">The MsBuild.exe application automatically assigns resource identifiers when you specify the `updateuid` option.</span></span>  
  
#### <a name="to-assign-resource-identifiers"></a><span data-ttu-id="ea146-154">Kaynak tanımlayıcılar atamak için</span><span class="sxs-lookup"><span data-stu-id="ea146-154">To assign resource identifiers</span></span>  
  
1.  <span data-ttu-id="ea146-155">Başlat menüsünden açmak [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] komut istemi.</span><span class="sxs-lookup"><span data-stu-id="ea146-155">From the Start Menu, open the [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] Command Prompt.</span></span>  
  
2.  <span data-ttu-id="ea146-156">Kaynak tanımlayıcılar yerelleştirilebilir içeriğinize atamak için aşağıdaki komutu kullanın.</span><span class="sxs-lookup"><span data-stu-id="ea146-156">Use the following command to assign resource identifiers to your localizable content.</span></span>  
  
    ```  
    msbuild /t:updateuid LocalizingWpfInWf.csproj  
    ```  
  
3.  <span data-ttu-id="ea146-157">Çözüm Gezgini'nde çift tıklayarak **SimpleControl.XAML'e** Kod düzenleyicisinde açın.</span><span class="sxs-lookup"><span data-stu-id="ea146-157">In Solution Explorer, double-click **SimpleControl.xaml** to open it in the Code Editor.</span></span> <span data-ttu-id="ea146-158">Göreceksiniz `msbuild` komutu ekledi `Uid` özniteliği için tüm öğeleri.</span><span class="sxs-lookup"><span data-stu-id="ea146-158">You will see that the `msbuild` command has added the `Uid` attribute to all the elements.</span></span> <span data-ttu-id="ea146-159">Bu, kaynak tanımlayıcılarının atanması yoluyla yerelleştirme kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="ea146-159">This facilitates localization through the assignment of resource identifiers.</span></span>  
  
     [!code-xaml[LocalizingWpfInWf#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl.xaml#20)]  
  
4.  <span data-ttu-id="ea146-160">Çözümü derlemek için F6 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="ea146-160">Press F6 to build the solution.</span></span>  
  
## <a name="using-locbaml-to-produce-a-satellite-assembly"></a><span data-ttu-id="ea146-161">Uydu derlemesi üretmek için LocBaml Kullanma</span><span class="sxs-lookup"><span data-stu-id="ea146-161">Using LocBaml to Produce a Satellite Assembly</span></span>  
 <span data-ttu-id="ea146-162">Yerelleştirilmiş içeriğiniz bir kaynak yalnızca içinde depolanan *uydu derleme*.</span><span class="sxs-lookup"><span data-stu-id="ea146-162">Your localized content is stored in a resource-only *satellite assembly*.</span></span> <span data-ttu-id="ea146-163">İçin yerelleştirilmiş bir derleme üretmek için komut satırı aracı LocBaml.exe'yi kullanın, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği.</span><span class="sxs-lookup"><span data-stu-id="ea146-163">Use the command-line tool LocBaml.exe to produce a localized assembly for your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span>  
  
#### <a name="to-produce-a-satellite-assembly"></a><span data-ttu-id="ea146-164">Uydu derlemesi üretmek için</span><span class="sxs-lookup"><span data-stu-id="ea146-164">To produce a satellite assembly</span></span>  
  
1.  <span data-ttu-id="ea146-165">LocBaml.exe'yi projenizin obj\Debug klasörüne kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="ea146-165">Copy LocBaml.exe to your project's obj\Debug folder.</span></span> <span data-ttu-id="ea146-166">Daha fazla bilgi için bkz: [uygulama yerelleştirme](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="ea146-166">For more information, see [Localize an Application](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md).</span></span>  
  
2.  <span data-ttu-id="ea146-167">Komut İstemi penceresinde, geçici bir dosyaya kaynak dizeleri ayıklamak için aşağıdaki komutu kullanın.</span><span class="sxs-lookup"><span data-stu-id="ea146-167">In the Command Prompt window, use the following command to extract resource strings into a temporary file.</span></span>  
  
    ```  
    LocBaml /parse LocalizingWpfInWf.g.en-US.resources /out:temp.csv  
    ```  
  
3.  <span data-ttu-id="ea146-168">Temp.csv dosyasını açın [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] veya başka bir metin düzenleyici.</span><span class="sxs-lookup"><span data-stu-id="ea146-168">Open the temp.csv file with [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] or another text editor.</span></span> <span data-ttu-id="ea146-169">Dize Değiştir `"Hello"` kendi İspanyolca çevirisi ile `"Hola"`.</span><span class="sxs-lookup"><span data-stu-id="ea146-169">Replace the string `"Hello"` with its Spanish translation, `"Hola"`.</span></span>  
  
4.  <span data-ttu-id="ea146-170">Temp.csv dosyasını kaydedin.</span><span class="sxs-lookup"><span data-stu-id="ea146-170">Save the temp.csv file.</span></span>  
  
5.  <span data-ttu-id="ea146-171">Yerelleştirilmiş kaynak dosyasını oluşturmak için aşağıdaki komutu kullanın.</span><span class="sxs-lookup"><span data-stu-id="ea146-171">Use the following command to generate the localized resource file.</span></span>  
  
    ```  
    LocBaml /generate /trans:temp.csv LocalizingWpfInWf.g.en-US.resources /out:. /cul:es-ES  
    ```  
  
     <span data-ttu-id="ea146-172">LocalizingWpfInWf.g.es-ES.resources dosyası obj\Debug klasöründe oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ea146-172">The LocalizingWpfInWf.g.es-ES.resources file is created in the obj\Debug folder.</span></span>  
  
6.  <span data-ttu-id="ea146-173">Yerelleştirilmiş uydu derlemesini oluşturmak için aşağıdaki komutu kullanın.</span><span class="sxs-lookup"><span data-stu-id="ea146-173">Use the following command to build the localized satellite assembly.</span></span>  
  
    ```  
    Al.exe /out:LocalizingWpfInWf.resources.dll /culture:es-ES /embed:LocalizingWpfInWf.Form1.es-ES.resources /embed:LocalizingWpfInWf.g.es-ES.resources  
    ```  
  
     <span data-ttu-id="ea146-174">LocalizingWpfInWf.resources.dll dosyası obj\Debug klasöründe oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ea146-174">The LocalizingWpfInWf.resources.dll file is created in the obj\Debug folder.</span></span>  
  
7.  <span data-ttu-id="ea146-175">LocalizingWpfInWf.resources.dll dosyasını projenin bin\Debug\es-ES klasörüne kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="ea146-175">Copy the LocalizingWpfInWf.resources.dll file to the project's bin\Debug\es-ES folder.</span></span> <span data-ttu-id="ea146-176">Varolan dosyayı değiştirmek.</span><span class="sxs-lookup"><span data-stu-id="ea146-176">Replace the existing file.</span></span>  
  
8.  <span data-ttu-id="ea146-177">Projenizin klasörüne içinde bulunan LocalizingWpfInWf.exe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ea146-177">Run LocalizingWpfInWf.exe, which is located in your project's bin\Debug folder.</span></span> <span data-ttu-id="ea146-178">Uygulamayı yeniden değil veya uydu derlemesi üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="ea146-178">Do not rebuild the application or the satellite assembly will be overwritten.</span></span>  
  
     <span data-ttu-id="ea146-179">Uygulama İngilizce dizelerin yerine yerelleştirilmiş dizeleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="ea146-179">The application shows the localized strings instead of the English strings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea146-180">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ea146-180">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="ea146-181">Bir Uygulamayı Yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="ea146-181">Localize an Application</span></span>](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)  
 [<span data-ttu-id="ea146-182">İzlenecek yol: Windows Formları yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="ea146-182">Walkthrough: Localizing Windows Forms</span></span>](http://msdn.microsoft.com/library/9a96220d-a19b-4de0-9f48-01e5d82679e5)  
 [<span data-ttu-id="ea146-183">WPF Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="ea146-183">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)
