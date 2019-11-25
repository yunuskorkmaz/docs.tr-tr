---
title: 'İzlenecek yol: Karma Uygulamayı Yerelleştirme'
ms.date: 08/18/2018
helpviewer_keywords:
- localization [WPF interoperability]
- hybrid applications [WPF interoperability]
ms.assetid: fbc0c54e-930a-4c13-8e9c-27b83665010a
ms.openlocfilehash: 281afad0c0de856ca67abc74c65aff0e7afc3e01
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976498"
---
# <a name="walkthrough-localizing-a-hybrid-application"></a><span data-ttu-id="65ed6-102">İzlenecek yol: Karma Uygulamayı Yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="65ed6-102">Walkthrough: Localizing a Hybrid Application</span></span>

<span data-ttu-id="65ed6-103">Bu izlenecek yol, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]tabanlı karma uygulamadaki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğelerinin nasıl yerelleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="65ed6-103">This walkthrough shows you how to localize [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elements in a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]-based hybrid application.</span></span>

<span data-ttu-id="65ed6-104">Bu izlenecek yolda gösterilen görevler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="65ed6-104">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="65ed6-105">[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] konak projesi oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="65ed6-105">Creating the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] host project.</span></span>

- <span data-ttu-id="65ed6-106">Yerelleştirilebilir içerik ekleme.</span><span class="sxs-lookup"><span data-stu-id="65ed6-106">Adding localizable content.</span></span>

- <span data-ttu-id="65ed6-107">Yerelleştirme etkinleştiriliyor.</span><span class="sxs-lookup"><span data-stu-id="65ed6-107">Enabling localization.</span></span>

- <span data-ttu-id="65ed6-108">Kaynak tanımlayıcıları atanıyor.</span><span class="sxs-lookup"><span data-stu-id="65ed6-108">Assigning resource identifiers.</span></span>

- <span data-ttu-id="65ed6-109">Bir uydu derlemesi üretmek için LocBaml aracını kullanma.</span><span class="sxs-lookup"><span data-stu-id="65ed6-109">Using the LocBaml tool to produce a satellite assembly.</span></span>

<span data-ttu-id="65ed6-110">Bu kılavuzda gösterilen görevlerin tüm kod listesi için bkz. [karma uygulama örneğini yerelleştirme](https://go.microsoft.com/fwlink/?LinkID=160015).</span><span class="sxs-lookup"><span data-stu-id="65ed6-110">For a complete code listing of the tasks illustrated in this walkthrough, see [Localizing a Hybrid Application Sample](https://go.microsoft.com/fwlink/?LinkID=160015).</span></span>

<span data-ttu-id="65ed6-111">İşiniz bittiğinde, yerelleştirilmiş bir karma uygulamanız olur.</span><span class="sxs-lookup"><span data-stu-id="65ed6-111">When you are finished, you will have a localized hybrid application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="65ed6-112">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="65ed6-112">Prerequisites</span></span>

<span data-ttu-id="65ed6-113">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="65ed6-113">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="65ed6-114">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="65ed6-114">Visual Studio 2017</span></span>

## <a name="creating-the-windows-forms-host-project"></a><span data-ttu-id="65ed6-115">Windows Forms konak projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="65ed6-115">Creating the Windows Forms Host Project</span></span>

<span data-ttu-id="65ed6-116">İlk adım [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] uygulama projesinin oluşturulması ve Yerelleştirilecek içeriğe sahip bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğesi eklemektir.</span><span class="sxs-lookup"><span data-stu-id="65ed6-116">The first step is to create the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] application project and add a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element with content that you will localize.</span></span>

### <a name="to-create-the-host-project"></a><span data-ttu-id="65ed6-117">Konak projesini oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="65ed6-117">To create the host project</span></span>

1. <span data-ttu-id="65ed6-118">`LocalizingWpfInWf`adlı bir **WPF uygulaması** projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="65ed6-118">Create a **WPF App** project named `LocalizingWpfInWf`.</span></span>  <span data-ttu-id="65ed6-119">(**Dosya** > **Yeni** > **projesi** > **görsel C#**  veya **Visual Basic** > **Klasik Masaüstü** > **WPF uygulaması**).</span><span class="sxs-lookup"><span data-stu-id="65ed6-119">(**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **WPF Application**).</span></span>

2. <span data-ttu-id="65ed6-120">Projeye `SimpleControl` adlı bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.UserControl> öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="65ed6-120">Add a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.UserControl> element called `SimpleControl` to the project.</span></span>

3. <span data-ttu-id="65ed6-121">Forma bir `SimpleControl` öğesi yerleştirmek için <xref:System.Windows.Forms.Integration.ElementHost> denetimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="65ed6-121">Use the <xref:System.Windows.Forms.Integration.ElementHost> control to place a `SimpleControl` element on the form.</span></span> <span data-ttu-id="65ed6-122">Daha fazla bilgi için bkz. [Izlenecek yol: 3-b WPF bileşik denetimini barındırma Windows Forms](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="65ed6-122">For more information, see [Walkthrough: Hosting a 3-D WPF Composite Control in Windows Forms](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).</span></span>

## <a name="adding-localizable-content"></a><span data-ttu-id="65ed6-123">Yerelleştirilebilir Içerik ekleme</span><span class="sxs-lookup"><span data-stu-id="65ed6-123">Adding Localizable Content</span></span>

<span data-ttu-id="65ed6-124">Sonra, bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Label denetimi ekleyeceksiniz ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğesinin içeriğini yerelleştirilebilir bir dizeye ayarlayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="65ed6-124">Next, you will add a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] label control and set the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element's content to a localizable string.</span></span>

### <a name="to-add-localizable-content"></a><span data-ttu-id="65ed6-125">Yerelleştirilebilir İçerik eklemek için</span><span class="sxs-lookup"><span data-stu-id="65ed6-125">To add localizable content</span></span>

1. <span data-ttu-id="65ed6-126">**Çözüm Gezgini**, WPF Tasarımcısında açmak Için **SimpleControl. xaml** ' ye çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="65ed6-126">In **Solution Explorer**, double-click **SimpleControl.xaml** to open it in the WPF Designer.</span></span>

2. <span data-ttu-id="65ed6-127">Aşağıdaki kodu kullanarak <xref:System.Windows.Controls.Button> denetiminin içeriğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="65ed6-127">Set the content of the <xref:System.Windows.Controls.Button> control using the following code.</span></span>

     [!code-xaml[LocalizingWpfInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl0.xaml#10)]

3. <span data-ttu-id="65ed6-128">**Çözüm Gezgini**, Windows Form Tasarımcısı açmak için **Form1** ' e çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="65ed6-128">In **Solution Explorer**, double-click **Form1** to open it in the Windows Forms Designer.</span></span>

4. <span data-ttu-id="65ed6-129">Forma bir etiket denetimi eklemek için **araç kutusunu** açın ve **etiket** ' e çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="65ed6-129">Open the **Toolbox** and double-click **Label** to add a label control to the form.</span></span> <span data-ttu-id="65ed6-130"><xref:System.Windows.Forms.Control.Text%2A> özelliğinin değerini `"Hello"`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="65ed6-130">Set the value of its <xref:System.Windows.Forms.Control.Text%2A> property to `"Hello"`.</span></span>

5. <span data-ttu-id="65ed6-131">Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="65ed6-131">Press **F5** to build and run the application.</span></span>

     <span data-ttu-id="65ed6-132">Hem `SimpleControl` öğesi hem de Label denetimi **"Hello"** metnini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="65ed6-132">Both the `SimpleControl` element and the label control display the text **"Hello"**.</span></span>

## <a name="enabling-localization"></a><span data-ttu-id="65ed6-133">Yerelleştirme etkinleştiriliyor</span><span class="sxs-lookup"><span data-stu-id="65ed6-133">Enabling Localization</span></span>

<span data-ttu-id="65ed6-134">Windows Form Tasarımcısı bir uydu derlemesinde yerelleştirmeyi etkinleştirmeye yönelik ayarları sağlar.</span><span class="sxs-lookup"><span data-stu-id="65ed6-134">The Windows Forms Designer provides settings for enabling localization in a satellite assembly.</span></span>

### <a name="to-enable-localization"></a><span data-ttu-id="65ed6-135">Yerelleştirmeyi etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="65ed6-135">To enable localization</span></span>

1. <span data-ttu-id="65ed6-136">**Çözüm Gezgini**' de, **Form1.cs** ' ye çift tıklayarak Windows Form Tasarımcısı açın.</span><span class="sxs-lookup"><span data-stu-id="65ed6-136">In **Solution Explorer**, double-click **Form1.cs** to open it in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="65ed6-137">**Özellikler** penceresinde, formun **yerelleştirilebilir** özelliğinin değerini `true`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="65ed6-137">In the **Properties** window, set the value of the form's **Localizable** property to `true`.</span></span>

3. <span data-ttu-id="65ed6-138">**Özellikler** penceresinde, **Language** özelliğinin değerini **İspanyolca (İspanya)** olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="65ed6-138">In the **Properties** window, set the value of the **Language** property to **Spanish (Spain)**.</span></span>

4. <span data-ttu-id="65ed6-139">Windows Form Tasarımcısı etiket denetimini seçin.</span><span class="sxs-lookup"><span data-stu-id="65ed6-139">In the Windows Forms Designer, select the label control.</span></span>

5. <span data-ttu-id="65ed6-140">**Özellikler** penceresinde <xref:System.Windows.Forms.Control.Text%2A> özelliğinin değerini `"Hola"`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="65ed6-140">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Text%2A> property to `"Hola"`.</span></span>

     <span data-ttu-id="65ed6-141">Projeye Form1.es-ES. resx adlı yeni bir kaynak dosyası eklenir.</span><span class="sxs-lookup"><span data-stu-id="65ed6-141">A new resource file named Form1.es-ES.resx is added to the project.</span></span>

6. <span data-ttu-id="65ed6-142">**Çözüm Gezgini**' de, **Form1.cs** öğesine sağ tıklayın ve kodu **görüntüle** ' ye tıklayarak kodu düzenleyici 'de açın.</span><span class="sxs-lookup"><span data-stu-id="65ed6-142">In **Solution Explorer**, right-click **Form1.cs** and click **View Code** to open it in the Code Editor.</span></span>

7. <span data-ttu-id="65ed6-143">Aşağıdaki kodu, `InitializeComponent`çağrısından önce `Form1` oluşturucusuna kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="65ed6-143">Copy the following code into the `Form1` constructor, preceding the call to `InitializeComponent`.</span></span>

     [!code-csharp[LocalizingWpfInWf#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/Form1.cs#2)]

8. <span data-ttu-id="65ed6-144">**Çözüm Gezgini**, **localizingwpfinwf** öğesine sağ tıklayın ve **Projeyi Kaldır**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="65ed6-144">In **Solution Explorer**, right-click **LocalizingWpfInWf** and click **Unload Project**.</span></span>

     <span data-ttu-id="65ed6-145">Proje adı etiketlendi **(kullanılamıyor)** .</span><span class="sxs-lookup"><span data-stu-id="65ed6-145">The project name is labeled **(unavailable)**.</span></span>

9. <span data-ttu-id="65ed6-146">**Localizingwpfinwf**öğesine sağ tıklayın ve **localizingwpfinwf. csproj öğesini Düzenle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="65ed6-146">Right-click **LocalizingWpfInWf**, and click **Edit LocalizingWpfInWf.csproj**.</span></span>

     <span data-ttu-id="65ed6-147">Proje dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="65ed6-147">The project file opens in the Code Editor.</span></span>

10. <span data-ttu-id="65ed6-148">Aşağıdaki satırı proje dosyasındaki ilk `PropertyGroup` kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="65ed6-148">Copy the following line into the first `PropertyGroup` in the project file.</span></span>

    ```xml
    <UICulture>en-US</UICulture>
    ```

11. <span data-ttu-id="65ed6-149">Proje dosyasını kaydedin ve kapatın.</span><span class="sxs-lookup"><span data-stu-id="65ed6-149">Save the project file and close it.</span></span>

12. <span data-ttu-id="65ed6-150">**Çözüm Gezgini**, **localizingwpfinwf** öğesine sağ tıklayın ve **projeyi yeniden yükle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="65ed6-150">In **Solution Explorer**, right-click **LocalizingWpfInWf** and click **Reload Project**.</span></span>

## <a name="assigning-resource-identifiers"></a><span data-ttu-id="65ed6-151">Kaynak tanımlayıcıları atama</span><span class="sxs-lookup"><span data-stu-id="65ed6-151">Assigning Resource Identifiers</span></span>

<span data-ttu-id="65ed6-152">Kaynak tanımlayıcılarını kullanarak, yerelleştirilebilir içeriğinizi kaynak Derlemeleriyle eşleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65ed6-152">You can map your localizable content to resource assemblies by using resource identifiers.</span></span> <span data-ttu-id="65ed6-153">MsBuild. exe uygulaması, `updateuid` seçeneğini belirttiğinizde kaynak tanımlayıcılarını otomatik olarak atar.</span><span class="sxs-lookup"><span data-stu-id="65ed6-153">The MsBuild.exe application automatically assigns resource identifiers when you specify the `updateuid` option.</span></span>

### <a name="to-assign-resource-identifiers"></a><span data-ttu-id="65ed6-154">Kaynak tanımlayıcılarını atamak için</span><span class="sxs-lookup"><span data-stu-id="65ed6-154">To assign resource identifiers</span></span>

1. <span data-ttu-id="65ed6-155">Başlat menüsünde, Visual Studio için Geliştirici Komut İstemi açın.</span><span class="sxs-lookup"><span data-stu-id="65ed6-155">From the Start Menu, open the Developer Command Prompt for Visual Studio.</span></span>

2. <span data-ttu-id="65ed6-156">Kaynak tanımlayıcılarını yerelleştirilebilir içeriğinize atamak için aşağıdaki komutu kullanın.</span><span class="sxs-lookup"><span data-stu-id="65ed6-156">Use the following command to assign resource identifiers to your localizable content.</span></span>

    ```console
    msbuild -t:updateuid LocalizingWpfInWf.csproj
    ```

3. <span data-ttu-id="65ed6-157">**Çözüm Gezgini**, kod düzenleyicisinde açmak Için **SimpleControl. xaml** ' ye çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="65ed6-157">In **Solution Explorer**, double-click **SimpleControl.xaml** to open it in the Code Editor.</span></span> <span data-ttu-id="65ed6-158">`msbuild` komutun tüm öğelere `Uid` özniteliğini eklediğini göreceksiniz.</span><span class="sxs-lookup"><span data-stu-id="65ed6-158">You will see that the `msbuild` command has added the `Uid` attribute to all the elements.</span></span> <span data-ttu-id="65ed6-159">Bu, kaynak tanımlayıcılarının atanması yoluyla yerelleştirmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="65ed6-159">This facilitates localization through the assignment of resource identifiers.</span></span>

     [!code-xaml[LocalizingWpfInWf#20](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl.xaml#20)]

4. <span data-ttu-id="65ed6-160">Çözümü derlemek için **F6** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="65ed6-160">Press **F6** to build the solution.</span></span>

## <a name="using-locbaml-to-produce-a-satellite-assembly"></a><span data-ttu-id="65ed6-161">Bir uydu derlemesi oluşturmak için LocBaml Kullanma</span><span class="sxs-lookup"><span data-stu-id="65ed6-161">Using LocBaml to Produce a Satellite Assembly</span></span>

<span data-ttu-id="65ed6-162">Yerelleştirilmiş içeriğiniz yalnızca kaynak bir *uydu derlemesinde*depolanır.</span><span class="sxs-lookup"><span data-stu-id="65ed6-162">Your localized content is stored in a resource-only *satellite assembly*.</span></span> <span data-ttu-id="65ed6-163">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğiniz için yerelleştirilmiş bir derleme oluşturmak üzere LocBaml. exe komut satırı aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="65ed6-163">Use the command-line tool LocBaml.exe to produce a localized assembly for your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span>

### <a name="to-produce-a-satellite-assembly"></a><span data-ttu-id="65ed6-164">Uydu derlemesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="65ed6-164">To produce a satellite assembly</span></span>

1. <span data-ttu-id="65ed6-165">LocBaml. exe ' yi projenizin obj\Debug klasörüne kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="65ed6-165">Copy LocBaml.exe to your project's obj\Debug folder.</span></span> <span data-ttu-id="65ed6-166">Daha fazla bilgi için bkz. [uygulamayı yerelleştirin](how-to-localize-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="65ed6-166">For more information, see [Localize an Application](how-to-localize-an-application.md).</span></span>

2. <span data-ttu-id="65ed6-167">Komut Istemi penceresinde, kaynak dizelerini geçici bir dosyaya ayıklamak için aşağıdaki komutu kullanın.</span><span class="sxs-lookup"><span data-stu-id="65ed6-167">In the Command Prompt window, use the following command to extract resource strings into a temporary file.</span></span>

    ```console
    LocBaml /parse LocalizingWpfInWf.g.en-US.resources /out:temp.csv
    ```

3. <span data-ttu-id="65ed6-168">Geçici. csv dosyasını Visual Studio veya başka bir metin düzenleyici ile açın.</span><span class="sxs-lookup"><span data-stu-id="65ed6-168">Open the temp.csv file with Visual Studio or another text editor.</span></span> <span data-ttu-id="65ed6-169">Dize `"Hello"`, Ispanyolca çevirisi, `"Hola"`ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="65ed6-169">Replace the string `"Hello"` with its Spanish translation, `"Hola"`.</span></span>

4. <span data-ttu-id="65ed6-170">Temp. csv dosyasını kaydedin.</span><span class="sxs-lookup"><span data-stu-id="65ed6-170">Save the temp.csv file.</span></span>

5. <span data-ttu-id="65ed6-171">Yerelleştirilmiş kaynak dosyasını oluşturmak için aşağıdaki komutu kullanın.</span><span class="sxs-lookup"><span data-stu-id="65ed6-171">Use the following command to generate the localized resource file.</span></span>

    ```console
    LocBaml /generate /trans:temp.csv LocalizingWpfInWf.g.en-US.resources /out:. /cul:es-ES
    ```

     <span data-ttu-id="65ed6-172">LocalizingWpfInWf.g.es-ES. resources dosyası obj\Debug klasöründe oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="65ed6-172">The LocalizingWpfInWf.g.es-ES.resources file is created in the obj\Debug folder.</span></span>

6. <span data-ttu-id="65ed6-173">Yerelleştirilmiş uydu derlemesini derlemek için aşağıdaki komutu kullanın.</span><span class="sxs-lookup"><span data-stu-id="65ed6-173">Use the following command to build the localized satellite assembly.</span></span>

    ```console
    Al.exe /out:LocalizingWpfInWf.resources.dll /culture:es-ES /embed:LocalizingWpfInWf.Form1.es-ES.resources /embed:LocalizingWpfInWf.g.es-ES.resources
    ```

     <span data-ttu-id="65ed6-174">LocalizingWpfInWf. resources. dll dosyası obj\Debug klasöründe oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="65ed6-174">The LocalizingWpfInWf.resources.dll file is created in the obj\Debug folder.</span></span>

7. <span data-ttu-id="65ed6-175">LocalizingWpfInWf. resources. dll dosyasını projenin bin\Debug\es-ES klasörüne kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="65ed6-175">Copy the LocalizingWpfInWf.resources.dll file to the project's bin\Debug\es-ES folder.</span></span> <span data-ttu-id="65ed6-176">Varolan dosyayı değiştirin.</span><span class="sxs-lookup"><span data-stu-id="65ed6-176">Replace the existing file.</span></span>

8. <span data-ttu-id="65ed6-177">Projenizin bin\Debug klasöründe bulunan LocalizingWpfInWf. exe ' yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="65ed6-177">Run LocalizingWpfInWf.exe, which is located in your project's bin\Debug folder.</span></span> <span data-ttu-id="65ed6-178">Uygulamayı yeniden oluşturma veya uydu derlemesinin üzerine yazılacak.</span><span class="sxs-lookup"><span data-stu-id="65ed6-178">Do not rebuild the application or the satellite assembly will be overwritten.</span></span>

     <span data-ttu-id="65ed6-179">Uygulama, Ingilizce dizeler yerine yerelleştirilmiş dizeleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="65ed6-179">The application shows the localized strings instead of the English strings.</span></span>

## <a name="see-also"></a><span data-ttu-id="65ed6-180">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65ed6-180">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="65ed6-181">Bir Uygulamayı Yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="65ed6-181">Localize an Application</span></span>](how-to-localize-an-application.md)
- <span data-ttu-id="65ed6-182">[İzlenecek yol: Windows Forms yerelleştirme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="65ed6-182">[Walkthrough: Localizing Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100))</span></span>
- [<span data-ttu-id="65ed6-183">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="65ed6-183">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
