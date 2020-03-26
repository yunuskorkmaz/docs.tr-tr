---
title: 'İzlenecek yol: Karma Uygulamayı Yerelleştirme'
ms.date: 08/18/2018
helpviewer_keywords:
- localization [WPF interoperability]
- hybrid applications [WPF interoperability]
ms.assetid: fbc0c54e-930a-4c13-8e9c-27b83665010a
ms.openlocfilehash: 69aa5ae145ffe378b7a4547e5a33826965bf7894
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111120"
---
# <a name="walkthrough-localizing-a-hybrid-application"></a><span data-ttu-id="88a45-102">İzlenecek yol: Karma Uygulamayı Yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="88a45-102">Walkthrough: Localizing a Hybrid Application</span></span>

<span data-ttu-id="88a45-103">Bu gözden geçirme, Windows [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Forms tabanlı karma bir uygulamadaki öğeleri nasıl yerelleştirdiğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="88a45-103">This walkthrough shows you how to localize [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elements in a Windows Forms-based hybrid application.</span></span>

<span data-ttu-id="88a45-104">Bu gözden geçirmede gösterilen görevler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="88a45-104">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="88a45-105">Windows Forms ana bilgisayar projesini oluşturma.</span><span class="sxs-lookup"><span data-stu-id="88a45-105">Creating the Windows Forms host project.</span></span>

- <span data-ttu-id="88a45-106">Yerelleştirilebilir içerik ekleme.</span><span class="sxs-lookup"><span data-stu-id="88a45-106">Adding localizable content.</span></span>

- <span data-ttu-id="88a45-107">Yerelleştirmeyi etkinleştirme.</span><span class="sxs-lookup"><span data-stu-id="88a45-107">Enabling localization.</span></span>

- <span data-ttu-id="88a45-108">Kaynak tanımlayıcıları atama.</span><span class="sxs-lookup"><span data-stu-id="88a45-108">Assigning resource identifiers.</span></span>

- <span data-ttu-id="88a45-109">Bir uydu tertibatı üretmek için LocBaml aracını kullanma.</span><span class="sxs-lookup"><span data-stu-id="88a45-109">Using the LocBaml tool to produce a satellite assembly.</span></span>

<span data-ttu-id="88a45-110">Bu gözden geçirme de gösterilen görevlerin tam kod listesi için, [karma uygulama örneğini yerelleştirme](https://go.microsoft.com/fwlink/?LinkID=160015)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="88a45-110">For a complete code listing of the tasks illustrated in this walkthrough, see [Localizing a Hybrid Application Sample](https://go.microsoft.com/fwlink/?LinkID=160015).</span></span>

<span data-ttu-id="88a45-111">Bittiğinde, yerelleştirilmiş bir karma uygulama nız olacaktır.</span><span class="sxs-lookup"><span data-stu-id="88a45-111">When you are finished, you will have a localized hybrid application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="88a45-112">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="88a45-112">Prerequisites</span></span>

<span data-ttu-id="88a45-113">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="88a45-113">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="88a45-114">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="88a45-114">Visual Studio 2017</span></span>

## <a name="creating-the-windows-forms-host-project"></a><span data-ttu-id="88a45-115">Windows Formları Ana Bilgisayar Projesini Oluşturma</span><span class="sxs-lookup"><span data-stu-id="88a45-115">Creating the Windows Forms Host Project</span></span>

<span data-ttu-id="88a45-116">İlk adım, Windows Forms uygulama projesini oluşturmak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve yerelleştireceğiniz içeriğe sahip bir öğe eklemektir.</span><span class="sxs-lookup"><span data-stu-id="88a45-116">The first step is to create the Windows Forms application project and add a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element with content that you will localize.</span></span>

### <a name="to-create-the-host-project"></a><span data-ttu-id="88a45-117">Ana bilgisayar projesini oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="88a45-117">To create the host project</span></span>

1. <span data-ttu-id="88a45-118">Adında `LocalizingWpfInWf`bir **WPF Uygulaması** projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="88a45-118">Create a **WPF App** project named `LocalizingWpfInWf`.</span></span>  <span data-ttu-id="88a45-119">(**Dosya** > **Yeni** > **Proje** > Görsel C **#** veya Visual **Basic** > Klasik**Masaüstü** > **WPF Uygulama**).</span><span class="sxs-lookup"><span data-stu-id="88a45-119">(**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **WPF Application**).</span></span>

2. <span data-ttu-id="88a45-120">Projeye [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> çağrılan `SimpleControl` bir öğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="88a45-120">Add a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.UserControl> element called `SimpleControl` to the project.</span></span>

3. <span data-ttu-id="88a45-121">Forma <xref:System.Windows.Forms.Integration.ElementHost> bir `SimpleControl` öğe yerleştirmek için denetimi kullanın.</span><span class="sxs-lookup"><span data-stu-id="88a45-121">Use the <xref:System.Windows.Forms.Integration.ElementHost> control to place a `SimpleControl` element on the form.</span></span> <span data-ttu-id="88a45-122">Daha fazla bilgi için [Walkthrough: Windows Formlarında 3B WPF Bileşik Denetimi Barındırma'](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md)na bakın.</span><span class="sxs-lookup"><span data-stu-id="88a45-122">For more information, see [Walkthrough: Hosting a 3D WPF Composite Control in Windows Forms](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).</span></span>

## <a name="adding-localizable-content"></a><span data-ttu-id="88a45-123">Yerelleştirilebilir İçerik Ekleme</span><span class="sxs-lookup"><span data-stu-id="88a45-123">Adding Localizable Content</span></span>

<span data-ttu-id="88a45-124">Ardından, bir Windows Forms etiket denetimi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ekler ve öğenin içeriğini yerelleştirilebilir bir dizeye ayarlarsınız.</span><span class="sxs-lookup"><span data-stu-id="88a45-124">Next, you will add a Windows Forms label control and set the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element's content to a localizable string.</span></span>

### <a name="to-add-localizable-content"></a><span data-ttu-id="88a45-125">Yerelleştirilebilir içerik eklemek için</span><span class="sxs-lookup"><span data-stu-id="88a45-125">To add localizable content</span></span>

1. <span data-ttu-id="88a45-126">**Solution**Explorer'da, WPF Designer'da açmak için **SimpleControl.xaml'a** çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="88a45-126">In **Solution Explorer**, double-click **SimpleControl.xaml** to open it in the WPF Designer.</span></span>

2. <span data-ttu-id="88a45-127">Aşağıdaki kodu kullanarak <xref:System.Windows.Controls.Button> denetimin içeriğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="88a45-127">Set the content of the <xref:System.Windows.Controls.Button> control using the following code.</span></span>

     [!code-xaml[LocalizingWpfInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl0.xaml#10)]

3. <span data-ttu-id="88a45-128">**Solution**Explorer'da, Windows Forms Designer'da açmak için **Form1'e** çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="88a45-128">In **Solution Explorer**, double-click **Form1** to open it in the Windows Forms Designer.</span></span>

4. <span data-ttu-id="88a45-129">Forma etiket denetimi eklemek için **Araç Kutusunu** açın ve **Etiket'i** çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="88a45-129">Open the **Toolbox** and double-click **Label** to add a label control to the form.</span></span> <span data-ttu-id="88a45-130"><xref:System.Windows.Forms.Control.Text%2A> Özelliğinin değerini ' `"Hello"`ye ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="88a45-130">Set the value of its <xref:System.Windows.Forms.Control.Text%2A> property to `"Hello"`.</span></span>

5. <span data-ttu-id="88a45-131">Uygulamayı oluşturmak ve çalıştırmak için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="88a45-131">Press **F5** to build and run the application.</span></span>

     <span data-ttu-id="88a45-132">Hem `SimpleControl` öğe hem de etiket denetimi **"Merhaba"** metnini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="88a45-132">Both the `SimpleControl` element and the label control display the text **"Hello"**.</span></span>

## <a name="enabling-localization"></a><span data-ttu-id="88a45-133">Yerelleştirmeyi Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="88a45-133">Enabling Localization</span></span>

<span data-ttu-id="88a45-134">Windows Forms Designer, uydu derlemesinde yerelleştirmeyi etkinleştirmek için ayarlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="88a45-134">The Windows Forms Designer provides settings for enabling localization in a satellite assembly.</span></span>

### <a name="to-enable-localization"></a><span data-ttu-id="88a45-135">Yerelleştirmeyi etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="88a45-135">To enable localization</span></span>

1. <span data-ttu-id="88a45-136">**Solution Explorer'da,** Windows Forms Designer'da açmak için **Form1.cs** çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="88a45-136">In **Solution Explorer**, double-click **Form1.cs** to open it in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="88a45-137">**Özellikler** penceresinde, formun **Yerelleştirilebilir** özelliğinin değerini `true`.</span><span class="sxs-lookup"><span data-stu-id="88a45-137">In the **Properties** window, set the value of the form's **Localizable** property to `true`.</span></span>

3. <span data-ttu-id="88a45-138">**Özellikler** penceresinde, **Dil** özelliğinin değerini **İspanyolca (İspanya)** olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="88a45-138">In the **Properties** window, set the value of the **Language** property to **Spanish (Spain)**.</span></span>

4. <span data-ttu-id="88a45-139">Windows Forms Designer'da etiket denetimini seçin.</span><span class="sxs-lookup"><span data-stu-id="88a45-139">In the Windows Forms Designer, select the label control.</span></span>

5. <span data-ttu-id="88a45-140">**Özellikler** penceresinde, <xref:System.Windows.Forms.Control.Text%2A> özelliğin değerini . `"Hola"`</span><span class="sxs-lookup"><span data-stu-id="88a45-140">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Text%2A> property to `"Hola"`.</span></span>

     <span data-ttu-id="88a45-141">Projeye Form1.es ES.resx adlı yeni bir kaynak dosyası eklendi.</span><span class="sxs-lookup"><span data-stu-id="88a45-141">A new resource file named Form1.es-ES.resx is added to the project.</span></span>

6. <span data-ttu-id="88a45-142">**Çözüm Gezgini'nde,** **Form1.cs** sağ tıklatın ve Kod Düzenleyicisi'nde açmak için **Kodu Görüntüle'yi** tıklatın.</span><span class="sxs-lookup"><span data-stu-id="88a45-142">In **Solution Explorer**, right-click **Form1.cs** and click **View Code** to open it in the Code Editor.</span></span>

7. <span data-ttu-id="88a45-143">Aşağıdaki kodu, `Form1` `InitializeComponent`'' için çağrıdan önce oluşturucuya kopyalayın</span><span class="sxs-lookup"><span data-stu-id="88a45-143">Copy the following code into the `Form1` constructor, preceding the call to `InitializeComponent`.</span></span>

     [!code-csharp[LocalizingWpfInWf#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/Form1.cs#2)]

8. <span data-ttu-id="88a45-144">**Çözüm Gezgini'nde,** **YerelleştirmeWpfInWf'i** sağ tıklatın ve **Project'i Boşalt'ı**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="88a45-144">In **Solution Explorer**, right-click **LocalizingWpfInWf** and click **Unload Project**.</span></span>

     <span data-ttu-id="88a45-145">Proje adı etiketlenir **(kullanılamaz)**.</span><span class="sxs-lookup"><span data-stu-id="88a45-145">The project name is labeled **(unavailable)**.</span></span>

9. <span data-ttu-id="88a45-146">Sağ tıklayın **YerelleştirmeWpfInWf**, ve **Yerelleştirme Edit WpfInWf.csproj**.</span><span class="sxs-lookup"><span data-stu-id="88a45-146">Right-click **LocalizingWpfInWf**, and click **Edit LocalizingWpfInWf.csproj**.</span></span>

     <span data-ttu-id="88a45-147">Proje dosyası Kod Düzenleyicisi'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="88a45-147">The project file opens in the Code Editor.</span></span>

10. <span data-ttu-id="88a45-148">Aşağıdaki satırı proje dosyasındaki ilk `PropertyGroup` satıra kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="88a45-148">Copy the following line into the first `PropertyGroup` in the project file.</span></span>

    ```xml
    <UICulture>en-US</UICulture>
    ```

11. <span data-ttu-id="88a45-149">Proje dosyasını kaydedin ve kapatın.</span><span class="sxs-lookup"><span data-stu-id="88a45-149">Save the project file and close it.</span></span>

12. <span data-ttu-id="88a45-150">**Çözüm Gezgini'nde,** **YerelleştirmeWpfInWf'i** sağ tıklatın ve **Project'i Yeniden Yükle'yi**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="88a45-150">In **Solution Explorer**, right-click **LocalizingWpfInWf** and click **Reload Project**.</span></span>

## <a name="assigning-resource-identifiers"></a><span data-ttu-id="88a45-151">Kaynak Tanımlayıcıları Atama</span><span class="sxs-lookup"><span data-stu-id="88a45-151">Assigning Resource Identifiers</span></span>

<span data-ttu-id="88a45-152">Kaynak tanımlayıcılarını kullanarak yerelleştirilebilir içeriğinizi kaynak derlemeleri ile eşleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="88a45-152">You can map your localizable content to resource assemblies by using resource identifiers.</span></span> <span data-ttu-id="88a45-153">MsBuild.exe `updateuid` uygulaması, seçeneği belirttiğiniz zaman kaynak tanımlayıcılarını otomatik olarak atar.</span><span class="sxs-lookup"><span data-stu-id="88a45-153">The MsBuild.exe application automatically assigns resource identifiers when you specify the `updateuid` option.</span></span>

### <a name="to-assign-resource-identifiers"></a><span data-ttu-id="88a45-154">Kaynak tanımlayıcıları atamak için</span><span class="sxs-lookup"><span data-stu-id="88a45-154">To assign resource identifiers</span></span>

1. <span data-ttu-id="88a45-155">Başlat Menüsünden Visual Studio için Geliştirici Komut Komut Ustem'ini açın.</span><span class="sxs-lookup"><span data-stu-id="88a45-155">From the Start Menu, open the Developer Command Prompt for Visual Studio.</span></span>

2. <span data-ttu-id="88a45-156">Kaynak tanımlayıcılarını yerelleştirilebilir içeriğinize atamak için aşağıdaki komutu kullanın.</span><span class="sxs-lookup"><span data-stu-id="88a45-156">Use the following command to assign resource identifiers to your localizable content.</span></span>

    ```console
    msbuild -t:updateuid LocalizingWpfInWf.csproj
    ```

3. <span data-ttu-id="88a45-157">**Solution**Explorer'da, Code Editor'da açmak için **SimpleControl.xaml'a** çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="88a45-157">In **Solution Explorer**, double-click **SimpleControl.xaml** to open it in the Code Editor.</span></span> <span data-ttu-id="88a45-158">Komutun `msbuild` tüm öğelere `Uid` öznitelik ekladığını göreceksiniz.</span><span class="sxs-lookup"><span data-stu-id="88a45-158">You will see that the `msbuild` command has added the `Uid` attribute to all the elements.</span></span> <span data-ttu-id="88a45-159">Bu, kaynak tanımlayıcılarının atanması yoluyla yerelleştirmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="88a45-159">This facilitates localization through the assignment of resource identifiers.</span></span>

     [!code-xaml[LocalizingWpfInWf#20](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl.xaml#20)]

4. <span data-ttu-id="88a45-160">Çözümü oluşturmak için **F6** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="88a45-160">Press **F6** to build the solution.</span></span>

## <a name="using-locbaml-to-produce-a-satellite-assembly"></a><span data-ttu-id="88a45-161">LocBaml'ı Uydu Montajı Üretmek için kullanma</span><span class="sxs-lookup"><span data-stu-id="88a45-161">Using LocBaml to Produce a Satellite Assembly</span></span>

<span data-ttu-id="88a45-162">Yerelleştirilmiş içeriğiniz yalnızca kaynak uydu *derlemesinde*depolanır.</span><span class="sxs-lookup"><span data-stu-id="88a45-162">Your localized content is stored in a resource-only *satellite assembly*.</span></span> <span data-ttu-id="88a45-163">İçeriğiniz için yerelleştirilmiş bir derleme oluşturmak için LocBaml.exe komut satırı aracını [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kullanın.</span><span class="sxs-lookup"><span data-stu-id="88a45-163">Use the command-line tool LocBaml.exe to produce a localized assembly for your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span>

### <a name="to-produce-a-satellite-assembly"></a><span data-ttu-id="88a45-164">Uydu montajı üretmek için</span><span class="sxs-lookup"><span data-stu-id="88a45-164">To produce a satellite assembly</span></span>

1. <span data-ttu-id="88a45-165">LocBaml.exe'yi projenizin obj\Debug klasörüne kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="88a45-165">Copy LocBaml.exe to your project's obj\Debug folder.</span></span> <span data-ttu-id="88a45-166">Daha fazla bilgi için [bkz.](how-to-localize-an-application.md)</span><span class="sxs-lookup"><span data-stu-id="88a45-166">For more information, see [Localize an Application](how-to-localize-an-application.md).</span></span>

2. <span data-ttu-id="88a45-167">Komut İstemi penceresinde, kaynak dizeleri geçici bir dosyaiçine ayıklamak için aşağıdaki komutu kullanın.</span><span class="sxs-lookup"><span data-stu-id="88a45-167">In the Command Prompt window, use the following command to extract resource strings into a temporary file.</span></span>

    ```console
    LocBaml /parse LocalizingWpfInWf.g.en-US.resources /out:temp.csv
    ```

3. <span data-ttu-id="88a45-168">Visual Studio veya başka bir metin düzenleyicisi ile temp.csv dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="88a45-168">Open the temp.csv file with Visual Studio or another text editor.</span></span> <span data-ttu-id="88a45-169">Dizeyi `"Hello"` İspanyolca çevirisi `"Hola"`ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="88a45-169">Replace the string `"Hello"` with its Spanish translation, `"Hola"`.</span></span>

4. <span data-ttu-id="88a45-170">temp.csv dosyasını kaydedin.</span><span class="sxs-lookup"><span data-stu-id="88a45-170">Save the temp.csv file.</span></span>

5. <span data-ttu-id="88a45-171">Yerelleştirilmiş kaynak dosyasını oluşturmak için aşağıdaki komutu kullanın.</span><span class="sxs-lookup"><span data-stu-id="88a45-171">Use the following command to generate the localized resource file.</span></span>

    ```console
    LocBaml /generate /trans:temp.csv LocalizingWpfInWf.g.en-US.resources /out:. /cul:es-ES
    ```

     <span data-ttu-id="88a45-172">LocalizingWpfInWf.g.es-ES.resources dosyası obj\Debug klasöründe oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="88a45-172">The LocalizingWpfInWf.g.es-ES.resources file is created in the obj\Debug folder.</span></span>

6. <span data-ttu-id="88a45-173">Yerelleştirilmiş uydu derlemesini oluşturmak için aşağıdaki komutu kullanın.</span><span class="sxs-lookup"><span data-stu-id="88a45-173">Use the following command to build the localized satellite assembly.</span></span>

    ```console
    Al.exe /out:LocalizingWpfInWf.resources.dll /culture:es-ES /embed:LocalizingWpfInWf.Form1.es-ES.resources /embed:LocalizingWpfInWf.g.es-ES.resources
    ```

     <span data-ttu-id="88a45-174">LocalizingWpfInWf.resources.dll dosyası obj\Debug klasöründe oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="88a45-174">The LocalizingWpfInWf.resources.dll file is created in the obj\Debug folder.</span></span>

7. <span data-ttu-id="88a45-175">YerelleştirmeWpfInWf.resources.dll dosyasını projenin bin\Debug\es-ES klasörüne kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="88a45-175">Copy the LocalizingWpfInWf.resources.dll file to the project's bin\Debug\es-ES folder.</span></span> <span data-ttu-id="88a45-176">Varolan dosyayı değiştirin.</span><span class="sxs-lookup"><span data-stu-id="88a45-176">Replace the existing file.</span></span>

8. <span data-ttu-id="88a45-177">Projenizin bin\Debug klasöründe bulunan YerelleştirmeWpfInWf.exe'yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="88a45-177">Run LocalizingWpfInWf.exe, which is located in your project's bin\Debug folder.</span></span> <span data-ttu-id="88a45-178">Uygulamayı yeniden yapmayın veya uydu montajı üzerine yazılacaktır.</span><span class="sxs-lookup"><span data-stu-id="88a45-178">Do not rebuild the application or the satellite assembly will be overwritten.</span></span>

     <span data-ttu-id="88a45-179">Uygulama, İngilizce dizeleri yerine yerelleştirilmiş dizeleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="88a45-179">The application shows the localized strings instead of the English strings.</span></span>

## <a name="see-also"></a><span data-ttu-id="88a45-180">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88a45-180">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="88a45-181">Bir Uygulamayı Yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="88a45-181">Localize an Application</span></span>](how-to-localize-an-application.md)
- <span data-ttu-id="88a45-182">[Walkthrough: Windows Formlarını Yerelleştirme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="88a45-182">[Walkthrough: Localizing Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100))</span></span>
- [<span data-ttu-id="88a45-183">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="88a45-183">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
