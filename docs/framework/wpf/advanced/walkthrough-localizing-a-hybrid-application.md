---
title: 'İzlenecek yol: Karma uygulamayı yerelleştirme'
ms.date: 08/18/2018
helpviewer_keywords:
- localization [WPF interoperability]
- hybrid applications [WPF interoperability]
ms.assetid: fbc0c54e-930a-4c13-8e9c-27b83665010a
ms.openlocfilehash: b2f771f124cee6ad52ea841006a6749408540048
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56746078"
---
# <a name="walkthrough-localizing-a-hybrid-application"></a><span data-ttu-id="41286-102">İzlenecek yol: Karma uygulamayı yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="41286-102">Walkthrough: Localizing a Hybrid Application</span></span>

<span data-ttu-id="41286-103">Bu izlenecek yol size nasıl yerelleştirileceği konusunda gösterir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğelerinde bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]-karma tabanlı.</span><span class="sxs-lookup"><span data-stu-id="41286-103">This walkthrough shows you how to localize [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elements in a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]-based hybrid application.</span></span>

<span data-ttu-id="41286-104">Bu kılavuzda gösterilen görevler aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="41286-104">Tasks illustrated in this walkthrough include:</span></span>

-   <span data-ttu-id="41286-105">Oluşturma [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] konak projesi.</span><span class="sxs-lookup"><span data-stu-id="41286-105">Creating the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] host project.</span></span>

-   <span data-ttu-id="41286-106">Yerelleştirilebilir İçerik ekleme.</span><span class="sxs-lookup"><span data-stu-id="41286-106">Adding localizable content.</span></span>

-   <span data-ttu-id="41286-107">Yerelleştirme etkinleştiriliyor.</span><span class="sxs-lookup"><span data-stu-id="41286-107">Enabling localization.</span></span>

-   <span data-ttu-id="41286-108">Kaynak Tanımlayıcıları atanıyor.</span><span class="sxs-lookup"><span data-stu-id="41286-108">Assigning resource identifiers.</span></span>

-   <span data-ttu-id="41286-109">LocBaml aracı, bir uydu derlemesi üretmek için kullanma.</span><span class="sxs-lookup"><span data-stu-id="41286-109">Using the LocBaml tool to produce a satellite assembly.</span></span>

<span data-ttu-id="41286-110">Bu izlenecek yolda gösterilen görevler tam kod listesi için bkz. [görevlerin yerelleştirme](https://go.microsoft.com/fwlink/?LinkID=160015).</span><span class="sxs-lookup"><span data-stu-id="41286-110">For a complete code listing of the tasks illustrated in this walkthrough, see [Localizing a Hybrid Application Sample](https://go.microsoft.com/fwlink/?LinkID=160015).</span></span>

<span data-ttu-id="41286-111">İşlemi tamamladığınızda, yerelleştirilmiş karma uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="41286-111">When you are finished, you will have a localized hybrid application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="41286-112">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="41286-112">Prerequisites</span></span>

<span data-ttu-id="41286-113">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="41286-113">You need the following components to complete this walkthrough:</span></span>

-   <span data-ttu-id="41286-114">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="41286-114">Visual Studio 2017</span></span>

## <a name="creating-the-windows-forms-host-project"></a><span data-ttu-id="41286-115">Windows Forms konak projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="41286-115">Creating the Windows Forms Host Project</span></span>

<span data-ttu-id="41286-116">İlk adım oluşturmaktır [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] uygulama ekleyin ve proje bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğesi, yerelleştirme içeriğe sahip.</span><span class="sxs-lookup"><span data-stu-id="41286-116">The first step is to create the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] application project and add a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element with content that you will localize.</span></span>

### <a name="to-create-the-host-project"></a><span data-ttu-id="41286-117">Konak projeyi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="41286-117">To create the host project</span></span>

1.  <span data-ttu-id="41286-118">Oluşturma bir **WPF uygulaması** adlı proje `LocalizingWpfInWf`.</span><span class="sxs-lookup"><span data-stu-id="41286-118">Create a **WPF App** project named `LocalizingWpfInWf`.</span></span>  <span data-ttu-id="41286-119">(**Dosya** > **yeni** > **proje** > **Visual C#** veya **Visual Basic**   >  **Klasik Masaüstü** > **WPF uygulaması**).</span><span class="sxs-lookup"><span data-stu-id="41286-119">(**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **WPF Application**).</span></span>

2.  <span data-ttu-id="41286-120">Ekleme bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> adlı öğesi `SimpleControl` projeye.</span><span class="sxs-lookup"><span data-stu-id="41286-120">Add a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.UserControl> element called `SimpleControl` to the project.</span></span>

3.  <span data-ttu-id="41286-121">Kullanım <xref:System.Windows.Forms.Integration.ElementHost> yerleştirmek için denetimi bir `SimpleControl` formdaki öğesi.</span><span class="sxs-lookup"><span data-stu-id="41286-121">Use the <xref:System.Windows.Forms.Integration.ElementHost> control to place a `SimpleControl` element on the form.</span></span> <span data-ttu-id="41286-122">Daha fazla bilgi için [izlenecek yol: Bir 3B WPF bileşik denetimini Windows Forms içinde barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="41286-122">For more information, see [Walkthrough: Hosting a 3-D WPF Composite Control in Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).</span></span>

## <a name="adding-localizable-content"></a><span data-ttu-id="41286-123">Yerelleştirilebilir İçerik ekleme</span><span class="sxs-lookup"><span data-stu-id="41286-123">Adding Localizable Content</span></span>

<span data-ttu-id="41286-124">Sonra ekleyeceksiniz bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ayarlayın ve etiket denetimini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yerelleştirilebilir dize öğesinin içeriği.</span><span class="sxs-lookup"><span data-stu-id="41286-124">Next, you will add a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] label control and set the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element's content to a localizable string.</span></span>

### <a name="to-add-localizable-content"></a><span data-ttu-id="41286-125">Yerelleştirilebilir İçerik eklemek için</span><span class="sxs-lookup"><span data-stu-id="41286-125">To add localizable content</span></span>

1.  <span data-ttu-id="41286-126">İçinde **Çözüm Gezgini**, çift **SimpleControl.XAML'e** açılır [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="41286-126">In **Solution Explorer**, double-click **SimpleControl.xaml** to open it in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>

2.  <span data-ttu-id="41286-127">İçeriğini ayarlama <xref:System.Windows.Controls.Button> aşağıdaki kodu kullanarak denetimi.</span><span class="sxs-lookup"><span data-stu-id="41286-127">Set the content of the <xref:System.Windows.Controls.Button> control using the following code.</span></span>

     [!code-xaml[LocalizingWpfInWf#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl0.xaml#10)]

3.  <span data-ttu-id="41286-128">İçinde **Çözüm Gezgini**, çift **Form1** Windows Form Tasarımcısı'nda açın.</span><span class="sxs-lookup"><span data-stu-id="41286-128">In **Solution Explorer**, double-click **Form1** to open it in the Windows Forms Designer.</span></span>

4.  <span data-ttu-id="41286-129">Açık **araç kutusu** ve çift **etiket** forma bir etiket denetiminizi ekleyecek.</span><span class="sxs-lookup"><span data-stu-id="41286-129">Open the **Toolbox** and double-click **Label** to add a label control to the form.</span></span> <span data-ttu-id="41286-130">Değerini kendi <xref:System.Windows.Forms.Control.Text%2A> özelliğini `"Hello"`.</span><span class="sxs-lookup"><span data-stu-id="41286-130">Set the value of its <xref:System.Windows.Forms.Control.Text%2A> property to `"Hello"`.</span></span>

5.  <span data-ttu-id="41286-131">Tuşuna **F5** oluşturun ve uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="41286-131">Press **F5** to build and run the application.</span></span>

     <span data-ttu-id="41286-132">Her iki `SimpleControl` öğesini ve etiket denetimi görüntüleme metni **"Hello"**.</span><span class="sxs-lookup"><span data-stu-id="41286-132">Both the `SimpleControl` element and the label control display the text **"Hello"**.</span></span>

## <a name="enabling-localization"></a><span data-ttu-id="41286-133">Yerelleştirme etkinleştiriliyor</span><span class="sxs-lookup"><span data-stu-id="41286-133">Enabling Localization</span></span>

<span data-ttu-id="41286-134">Windows Form Tasarımcısı, bir uydu derlemeye yerelleştirme etkinleştirmek için ayarlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="41286-134">The Windows Forms Designer provides settings for enabling localization in a satellite assembly.</span></span>

### <a name="to-enable-localization"></a><span data-ttu-id="41286-135">Yerelleştirme etkinleştirilemedi</span><span class="sxs-lookup"><span data-stu-id="41286-135">To enable localization</span></span>

1.  <span data-ttu-id="41286-136">İçinde **Çözüm Gezgini**, çift **Form1.cs** Windows Form Tasarımcısı'nda açın.</span><span class="sxs-lookup"><span data-stu-id="41286-136">In **Solution Explorer**, double-click **Form1.cs** to open it in the Windows Forms Designer.</span></span>

2.  <span data-ttu-id="41286-137">İçinde **özellikleri** penceresinde, formun ayarlayın **yerelleştirilebilir** özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="41286-137">In the **Properties** window, set the value of the form's **Localizable** property to `true`.</span></span>

3.  <span data-ttu-id="41286-138">İçinde **özellikleri** penceresinde değerini ayarlayın **dil** özelliğini **İspanyolca (İspanya)**.</span><span class="sxs-lookup"><span data-stu-id="41286-138">In the **Properties** window, set the value of the **Language** property to **Spanish (Spain)**.</span></span>

4.  <span data-ttu-id="41286-139">Windows Form Tasarımcısı'nda, etiket denetimini seçin.</span><span class="sxs-lookup"><span data-stu-id="41286-139">In the Windows Forms Designer, select the label control.</span></span>

5.  <span data-ttu-id="41286-140">İçinde **özellikleri** penceresinde değerini ayarlayın <xref:System.Windows.Forms.Control.Text%2A> özelliğini `"Hola"`.</span><span class="sxs-lookup"><span data-stu-id="41286-140">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Text%2A> property to `"Hola"`.</span></span>

     <span data-ttu-id="41286-141">Form1.es ES.resx adlı yeni bir kaynak dosya projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="41286-141">A new resource file named Form1.es-ES.resx is added to the project.</span></span>

6.  <span data-ttu-id="41286-142">İçinde **Çözüm Gezgini**, sağ **Form1.cs** tıklatıp **kodu görüntüle** Kod Düzenleyicisi'nde açın.</span><span class="sxs-lookup"><span data-stu-id="41286-142">In **Solution Explorer**, right-click **Form1.cs** and click **View Code** to open it in the Code Editor.</span></span>

7.  <span data-ttu-id="41286-143">Aşağıdaki kodu kopyalayın `Form1` Oluşturucusu çağrısının öncesine `InitializeComponent`.</span><span class="sxs-lookup"><span data-stu-id="41286-143">Copy the following code into the `Form1` constructor, preceding the call to `InitializeComponent`.</span></span>

     [!code-csharp[LocalizingWpfInWf#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/Form1.cs#2)]

8.  <span data-ttu-id="41286-144">İçinde **Çözüm Gezgini**, sağ **LocalizingWpfInWf** tıklatıp **projeyi**.</span><span class="sxs-lookup"><span data-stu-id="41286-144">In **Solution Explorer**, right-click **LocalizingWpfInWf** and click **Unload Project**.</span></span>

     <span data-ttu-id="41286-145">Proje adı etiketli **(kullanılamıyor)**.</span><span class="sxs-lookup"><span data-stu-id="41286-145">The project name is labeled **(unavailable)**.</span></span>

9. <span data-ttu-id="41286-146">Sağ **LocalizingWpfInWf**, tıklatıp **LocalizingWpfInWf.csproj'yi**.</span><span class="sxs-lookup"><span data-stu-id="41286-146">Right-click **LocalizingWpfInWf**, and click **Edit LocalizingWpfInWf.csproj**.</span></span>

     <span data-ttu-id="41286-147">Proje dosyası Kod Düzenleyicisi'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="41286-147">The project file opens in the Code Editor.</span></span>

10. <span data-ttu-id="41286-148">Aşağıdaki satırı ilk kopyalamak `PropertyGroup` proje dosyasındaki.</span><span class="sxs-lookup"><span data-stu-id="41286-148">Copy the following line into the first `PropertyGroup` in the project file.</span></span>

    ```xml
    <UICulture>en-US</UICulture>
    ```

11. <span data-ttu-id="41286-149">Proje dosyasını kaydedin ve kapatın.</span><span class="sxs-lookup"><span data-stu-id="41286-149">Save the project file and close it.</span></span>

12. <span data-ttu-id="41286-150">İçinde **Çözüm Gezgini**, sağ **LocalizingWpfInWf** tıklatıp **projeyi**.</span><span class="sxs-lookup"><span data-stu-id="41286-150">In **Solution Explorer**, right-click **LocalizingWpfInWf** and click **Reload Project**.</span></span>

## <a name="assigning-resource-identifiers"></a><span data-ttu-id="41286-151">Kaynak Tanımlayıcıları atama</span><span class="sxs-lookup"><span data-stu-id="41286-151">Assigning Resource Identifiers</span></span>

<span data-ttu-id="41286-152">Yerelleştirilebilir İçerik kaynak tanımlayıcılarını kullanarak, kaynak derlemelerine eşleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41286-152">You can map your localizable content to resource assemblies by using resource identifiers.</span></span> <span data-ttu-id="41286-153">Belirttiğiniz zaman MsBuild.exe uygulaması kaynak tanımlayıcılarını otomatik olarak atar. `updateuid` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="41286-153">The MsBuild.exe application automatically assigns resource identifiers when you specify the `updateuid` option.</span></span>

### <a name="to-assign-resource-identifiers"></a><span data-ttu-id="41286-154">Kaynak Tanımlayıcıları atamak için</span><span class="sxs-lookup"><span data-stu-id="41286-154">To assign resource identifiers</span></span>

1.  <span data-ttu-id="41286-155">Başlat menüsünde Visual Studio için geliştirici komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="41286-155">From the Start Menu, open the Developer Command Prompt for Visual Studio.</span></span>

2.  <span data-ttu-id="41286-156">Yerelleştirilebilir İçerik için kaynak tanımlayıcılarını atamak için aşağıdaki komutu kullanın.</span><span class="sxs-lookup"><span data-stu-id="41286-156">Use the following command to assign resource identifiers to your localizable content.</span></span>

    ```
    msbuild -t:updateuid LocalizingWpfInWf.csproj
    ```

3.  <span data-ttu-id="41286-157">İçinde **Çözüm Gezgini**, çift **SimpleControl.XAML'e** Kod Düzenleyicisi'nde açın.</span><span class="sxs-lookup"><span data-stu-id="41286-157">In **Solution Explorer**, double-click **SimpleControl.xaml** to open it in the Code Editor.</span></span> <span data-ttu-id="41286-158">Göreceksiniz `msbuild` komut ekledi `Uid` özniteliği için tüm öğeleri.</span><span class="sxs-lookup"><span data-stu-id="41286-158">You will see that the `msbuild` command has added the `Uid` attribute to all the elements.</span></span> <span data-ttu-id="41286-159">Bu kaynak tanımlayıcıları atanması yoluyla yerelleştirme kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="41286-159">This facilitates localization through the assignment of resource identifiers.</span></span>

     [!code-xaml[LocalizingWpfInWf#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl.xaml#20)]

4.  <span data-ttu-id="41286-160">Tuşuna **F6** çözümü derlemek için.</span><span class="sxs-lookup"><span data-stu-id="41286-160">Press **F6** to build the solution.</span></span>

## <a name="using-locbaml-to-produce-a-satellite-assembly"></a><span data-ttu-id="41286-161">LocBaml bir uydu derlemesi üretmek için kullanma</span><span class="sxs-lookup"><span data-stu-id="41286-161">Using LocBaml to Produce a Satellite Assembly</span></span>

<span data-ttu-id="41286-162">Bir kaynak yalnızca içinde yerelleştirilmiş içeriği depolanan *uydu derleme*.</span><span class="sxs-lookup"><span data-stu-id="41286-162">Your localized content is stored in a resource-only *satellite assembly*.</span></span> <span data-ttu-id="41286-163">Komut satırı aracı LocBaml.exe'yi için yerelleştirilmiş bir derleme oluşturmak için kullanın, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği.</span><span class="sxs-lookup"><span data-stu-id="41286-163">Use the command-line tool LocBaml.exe to produce a localized assembly for your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span>

### <a name="to-produce-a-satellite-assembly"></a><span data-ttu-id="41286-164">Uydu derlemesi üretmek için</span><span class="sxs-lookup"><span data-stu-id="41286-164">To produce a satellite assembly</span></span>

1.  <span data-ttu-id="41286-165">LocBaml.exe projenizin obj\Debug klasörüne kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="41286-165">Copy LocBaml.exe to your project's obj\Debug folder.</span></span> <span data-ttu-id="41286-166">Daha fazla bilgi için [bir uygulamayı yerelleştirme](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="41286-166">For more information, see [Localize an Application](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md).</span></span>

2.  <span data-ttu-id="41286-167">Komut İstemi penceresinde, kaynak dizeleri geçici bir dosyaya ayıklamak için aşağıdaki komutu kullanın.</span><span class="sxs-lookup"><span data-stu-id="41286-167">In the Command Prompt window, use the following command to extract resource strings into a temporary file.</span></span>

    ```
    LocBaml /parse LocalizingWpfInWf.g.en-US.resources /out:temp.csv
    ```

3.  <span data-ttu-id="41286-168">Temp.csv dosyasını Visual Studio veya başka bir metin düzenleyici ile açın.</span><span class="sxs-lookup"><span data-stu-id="41286-168">Open the temp.csv file with Visual Studio or another text editor.</span></span> <span data-ttu-id="41286-169">Dize değiştirin `"Hello"` İspanyolca çevirisini ile `"Hola"`.</span><span class="sxs-lookup"><span data-stu-id="41286-169">Replace the string `"Hello"` with its Spanish translation, `"Hola"`.</span></span>

4.  <span data-ttu-id="41286-170">Temp.csv dosyasını kaydedin.</span><span class="sxs-lookup"><span data-stu-id="41286-170">Save the temp.csv file.</span></span>

5.  <span data-ttu-id="41286-171">Yerelleştirilmiş kaynak dosyası oluşturmak için aşağıdaki komutu kullanın.</span><span class="sxs-lookup"><span data-stu-id="41286-171">Use the following command to generate the localized resource file.</span></span>

    ```
    LocBaml /generate /trans:temp.csv LocalizingWpfInWf.g.en-US.resources /out:. /cul:es-ES
    ```

     <span data-ttu-id="41286-172">LocalizingWpfInWf.g.es ES.resources dosya obj\Debug klasöründe oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="41286-172">The LocalizingWpfInWf.g.es-ES.resources file is created in the obj\Debug folder.</span></span>

6.  <span data-ttu-id="41286-173">Yerelleştirilmiş bir uydu derlemesi oluşturmak için aşağıdaki komutu kullanın.</span><span class="sxs-lookup"><span data-stu-id="41286-173">Use the following command to build the localized satellite assembly.</span></span>

    ```
    Al.exe /out:LocalizingWpfInWf.resources.dll /culture:es-ES /embed:LocalizingWpfInWf.Form1.es-ES.resources /embed:LocalizingWpfInWf.g.es-ES.resources
    ```

     <span data-ttu-id="41286-174">LocalizingWpfInWf.resources.dll dosyasını obj\Debug klasöründe oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="41286-174">The LocalizingWpfInWf.resources.dll file is created in the obj\Debug folder.</span></span>

7.  <span data-ttu-id="41286-175">LocalizingWpfInWf.resources.dll dosya projenin bin\Debug\es ES klasörüne kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="41286-175">Copy the LocalizingWpfInWf.resources.dll file to the project's bin\Debug\es-ES folder.</span></span> <span data-ttu-id="41286-176">Var olan dosyayı değiştirin.</span><span class="sxs-lookup"><span data-stu-id="41286-176">Replace the existing file.</span></span>

8.  <span data-ttu-id="41286-177">Projenizin bin\Debug klasöründe bulunan LocalizingWpfInWf.exe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="41286-177">Run LocalizingWpfInWf.exe, which is located in your project's bin\Debug folder.</span></span> <span data-ttu-id="41286-178">Uygulamayı yeniden değil veya uydu derlemesi üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="41286-178">Do not rebuild the application or the satellite assembly will be overwritten.</span></span>

     <span data-ttu-id="41286-179">Uygulama yerelleştirilmiş dizeleri İngilizce dizeler yerine gösterir.</span><span class="sxs-lookup"><span data-stu-id="41286-179">The application shows the localized strings instead of the English strings.</span></span>

## <a name="see-also"></a><span data-ttu-id="41286-180">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41286-180">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="41286-181">Bir Uygulamayı Yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="41286-181">Localize an Application</span></span>](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)
- <span data-ttu-id="41286-182">[İzlenecek yol: Windows formlarını yerelleştirme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="41286-182">[Walkthrough: Localizing Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100))</span></span>
- [<span data-ttu-id="41286-183">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="41286-183">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
