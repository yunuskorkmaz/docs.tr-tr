---
title: 'Nasıl yapılır: Bir Uygulamayı Yerelleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- localization [WPF], applications
- LocBaml tool [WPF]
- applications [WPF], localizing
ms.assetid: 5001227e-9326-48a4-9dcd-ba1b89ee6653
ms.openlocfilehash: f2e7e5e8879e89806cfd457a1af80f51b91871cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174218"
---
# <a name="how-to-localize-an-application"></a><span data-ttu-id="758b0-102">Nasıl yapılır: Bir Uygulamayı Yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="758b0-102">How to: Localize an Application</span></span>
<span data-ttu-id="758b0-103">Bu öğretici, LocBaml aracını kullanarak yerelleştirilmiş bir uygulamanın nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="758b0-103">This tutorial explains how to create a localized application by using the LocBaml tool.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="758b0-104">LocBaml aracı üretime hazır bir uygulama değildir.</span><span class="sxs-lookup"><span data-stu-id="758b0-104">The LocBaml tool is not a production-ready application.</span></span> <span data-ttu-id="758b0-105">Bazı yerelleştirme API'lerini kullanan ve bir yerelleştirme aracını nasıl yazabileceğinizi gösteren bir örnek olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="758b0-105">It is presented as a sample that uses some of the localization APIs and illustrates how you might write a localization tool.</span></span>  
  
<a name="Introduction"></a>
## <a name="overview"></a><span data-ttu-id="758b0-106">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="758b0-106">Overview</span></span>  
 <span data-ttu-id="758b0-107">Bu tartışma, bir uygulamayı yerelleştirmek için adım adım bir yaklaşım sağlar.</span><span class="sxs-lookup"><span data-stu-id="758b0-107">This discussion gives you a step-by-step approach to localizing an application.</span></span> <span data-ttu-id="758b0-108">İlk olarak, çeviriyapılacak metnin çıkarılabilmeleri için başvurunuzu hazırlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="758b0-108">First, you will prepare your application so that the text that will be translated can be extracted.</span></span> <span data-ttu-id="758b0-109">Metin çevrildikten sonra, çevrilen metni özgün uygulamanın yeni bir kopyasında birleştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="758b0-109">After the text is translated, you will merge the translated text into a new copy of the original application.</span></span>  
  
<a name="Requirements"></a>
## <a name="requirements"></a><span data-ttu-id="758b0-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="758b0-110">Requirements</span></span>  
 <span data-ttu-id="758b0-111">Bu tartışma boyunca, komut satırından çalışan bir derleyici olan Microsoft build engine 'i (MSBuild) kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="758b0-111">Over the course of this discussion, you will use Microsoft build engine (MSBuild), which is a compiler that runs from the command line.</span></span>  
  
 <span data-ttu-id="758b0-112">Ayrıca, bir proje dosyası kullanmanız için talimat verilecektir.</span><span class="sxs-lookup"><span data-stu-id="758b0-112">Also, you will be instructed to use a project file.</span></span> <span data-ttu-id="758b0-113">MSBuild ve proje dosyalarının nasıl kullanılacağıyla ilgili talimatlar [için](../app-development/building-and-deploying-wpf-applications.md)bkz.</span><span class="sxs-lookup"><span data-stu-id="758b0-113">For instructions on how to use MSBuild and project files, see [Build and Deploy](../app-development/building-and-deploying-wpf-applications.md).</span></span>  
  
 <span data-ttu-id="758b0-114">Bu tartışmadaki tüm örnekler kültür olarak en-US (İngilizce-ABD) kullankullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="758b0-114">All the examples in this discussion use en-US (English-US) as the culture.</span></span> <span data-ttu-id="758b0-115">Bu, farklı bir dil yüklemeden örneklerin adımları üzerinde çalışmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="758b0-115">This enables you to work through the steps of the examples without installing a different language.</span></span>  
  
<a name="create_sample_app"></a>
## <a name="create-a-sample-application"></a><span data-ttu-id="758b0-116">Örnek Uygulama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="758b0-116">Create a Sample Application</span></span>  
 <span data-ttu-id="758b0-117">Bu adımda, yerelleştirme için başvurunuzu hazırlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="758b0-117">In this step, you will prepare your application for localization.</span></span> <span data-ttu-id="758b0-118">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Örneklerde, bu tartışmadaki kod örnekleri için kullanılacak bir HelloApp örneği verilir.</span><span class="sxs-lookup"><span data-stu-id="758b0-118">In the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] samples, a HelloApp sample is supplied that will be used for the code examples in this discussion.</span></span> <span data-ttu-id="758b0-119">Bu örneği kullanmak isterseniz, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] [LocBaml Tool Sample'dan](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml)dosyaları indirin.</span><span class="sxs-lookup"><span data-stu-id="758b0-119">If you would like to use this sample, download the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] files from the [LocBaml Tool Sample](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).</span></span>  
  
1. <span data-ttu-id="758b0-120">Uygulamanızı yerelleştirmeye başlamak istediğiniz noktaya kadar geliştirin.</span><span class="sxs-lookup"><span data-stu-id="758b0-120">Develop your application to the point where you want to start localization.</span></span>  
  
2. <span data-ttu-id="758b0-121">MSBuild'in nötr dil kaynaklarını içerecek şekilde bir ana montaj ve uydu derlemesi (.resources.dll uzantılı bir dosya) oluşturması için proje dosyasındaki geliştirme dilini belirtin.</span><span class="sxs-lookup"><span data-stu-id="758b0-121">Specify the development language in the project file so that MSBuild generates a main assembly and a satellite assembly (a file with the .resources.dll extension) to contain the neutral language resources.</span></span> <span data-ttu-id="758b0-122">HelloApp örneğindeki proje dosyası HelloApp.csproj'dur.</span><span class="sxs-lookup"><span data-stu-id="758b0-122">The project file in the HelloApp sample is HelloApp.csproj.</span></span> <span data-ttu-id="758b0-123">Bu dosyada, aşağıdaki gibi tanımlanan geliştirme dilini bulacaksınız:</span><span class="sxs-lookup"><span data-stu-id="758b0-123">In that file, you will find the development language identified as follows:</span></span>  
  
     `<UICulture>en-US</UICulture>`  
  
3. <span data-ttu-id="758b0-124">Dosyalarınıza [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Uid'leri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="758b0-124">Add Uids to your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files.</span></span> <span data-ttu-id="758b0-125">Uid'ler dosyalardaki değişiklikleri izlemek ve çevrilmesi gereken öğeleri tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="758b0-125">Uids are used to keep track of changes to files and to identify items that must be translated.</span></span> <span data-ttu-id="758b0-126">Dosyalarınıza Uid'ler eklemek için proje dosyanızda **updateuid** çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="758b0-126">To add Uids to your files, run **updateuid** on your project file:</span></span>  
  
     <span data-ttu-id="758b0-127">**msbuild -t:updateuid helloapp.csproj**</span><span class="sxs-lookup"><span data-stu-id="758b0-127">**msbuild -t:updateuid helloapp.csproj**</span></span>  
  
     <span data-ttu-id="758b0-128">Eksik veya yinelenen Uid'niz olmadığını doğrulamak için **checkuid'i**çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="758b0-128">To verify that you have no missing or duplicate Uids, run **checkuid**:</span></span>  
  
     <span data-ttu-id="758b0-129">**msbuild -t:checkuid helloapp.csproj**</span><span class="sxs-lookup"><span data-stu-id="758b0-129">**msbuild -t:checkuid helloapp.csproj**</span></span>  
  
     <span data-ttu-id="758b0-130">**Updateuid**çalıştırdıktan sonra, dosyalarınız Uids içermelidir.</span><span class="sxs-lookup"><span data-stu-id="758b0-130">After running **updateuid**, your files should contain Uids.</span></span> <span data-ttu-id="758b0-131">Örneğin, HelloApp'ın Pane1.xaml dosyasında aşağıdakileri bulmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="758b0-131">For example, in the Pane1.xaml file of HelloApp, you should find the following:</span></span>  
  
     `<StackPanel x:Uid="StackPanel_1">`  
  
     `<TextBlock x:Uid="TextBlock_1">Hello World</TextBlock>`  
  
     `<TextBlock x:Uid="TextBlock_2">Goodbye World</TextBlock>`  
  
     `</StackPanel>`  
  
<a name="create_dll"></a>
## <a name="create-the-neutral-language-resources-satellite-assembly"></a><span data-ttu-id="758b0-132">Tarafsız Dil Kaynakları Uydu Derlemesi Oluştur</span><span class="sxs-lookup"><span data-stu-id="758b0-132">Create the Neutral Language Resources Satellite Assembly</span></span>  
 <span data-ttu-id="758b0-133">Uygulama nötr bir dil kaynakları uydu derlemesi oluşturmak için yapılandırıldıktan sonra, uygulamayı oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="758b0-133">After the application is configured to generate a neutral language resources satellite assembly, you build the application.</span></span> <span data-ttu-id="758b0-134">Bu, ana uygulama derlemesinin yanı sıra LocBaml tarafından yerelleştirme için gerekli olan nötr dil kaynakları uydu derlemesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="758b0-134">This generates the main application assembly, as well as the neutral language resources satellite assembly that is required by LocBaml for localization.</span></span> <span data-ttu-id="758b0-135">Uygulamayı oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="758b0-135">To build the application:</span></span>  
  
1. <span data-ttu-id="758b0-136">Dinamik bağlantı kitaplığı (DLL) oluşturmak için HelloApp'ı derle:</span><span class="sxs-lookup"><span data-stu-id="758b0-136">Compile HelloApp to create a dynamic-link library (DLL):</span></span>  
  
     <span data-ttu-id="758b0-137">**msbuild helloapp.csproj**</span><span class="sxs-lookup"><span data-stu-id="758b0-137">**msbuild helloapp.csproj**</span></span>  
  
2. <span data-ttu-id="758b0-138">Yeni oluşturulan ana uygulama derlemesi HelloApp.exe aşağıdaki klasörde oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="758b0-138">The newly created main application assembly, HelloApp.exe, is created in the following folder:</span></span>  
  
     `C:\HelloApp\Bin\Debug\`  
  
3. <span data-ttu-id="758b0-139">Yeni oluşturulan nötr dil kaynakları uydu derlemesi HelloApp.resources.dll aşağıdaki klasörde oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="758b0-139">The newly created neutral language resources satellite assembly, HelloApp.resources.dll, is created in the following folder:</span></span>  
  
     `C:\HelloApp\Bin\Debug\en-US\`  
  
<a name="build_locbaml"></a>
## <a name="build-the-locbaml-tool"></a><span data-ttu-id="758b0-140">LocBaml Aracı'nı oluşturun</span><span class="sxs-lookup"><span data-stu-id="758b0-140">Build the LocBaml Tool</span></span>  
  
1. <span data-ttu-id="758b0-141">LocBaml oluşturmak için gerekli tüm dosyalar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] örneklerde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="758b0-141">All the files necessary to build LocBaml are located in the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] samples.</span></span> <span data-ttu-id="758b0-142">[LocBaml Tool Sample'dan](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml)C# dosyalarını indirin.</span><span class="sxs-lookup"><span data-stu-id="758b0-142">Download the C# files from the [LocBaml Tool Sample](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).</span></span>  
  
2. <span data-ttu-id="758b0-143">Komut satırından, aracı oluşturmak için proje dosyasını (locbaml.csproj) çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="758b0-143">From the command line, run the project file (locbaml.csproj) to build the tool:</span></span>  
  
     <span data-ttu-id="758b0-144">**msbuild locbaml.csproj**</span><span class="sxs-lookup"><span data-stu-id="758b0-144">**msbuild locbaml.csproj**</span></span>  
  
3. <span data-ttu-id="758b0-145">Yeni oluşturulan yürütülebilir dosyayı (locbaml.exe) bulmak için Bin\Release dizinine gidin.</span><span class="sxs-lookup"><span data-stu-id="758b0-145">Go to the Bin\Release directory to find the newly created executable file (locbaml.exe).</span></span> <span data-ttu-id="758b0-146">Örnek:C:\LocBaml\Bin\Release\locbaml.exe.</span><span class="sxs-lookup"><span data-stu-id="758b0-146">Example:C:\LocBaml\Bin\Release\locbaml.exe.</span></span>  
  
4. <span data-ttu-id="758b0-147">LocBaml çalıştırdığınızda belirtebileceğiniz seçenekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="758b0-147">The options that you can specify when you run LocBaml are as follows:</span></span>  
  
    - <span data-ttu-id="758b0-148">**ayrışma** veya **-p:** Parses Baml, kaynaklar veya DLL dosyaları bir .csv veya .txt dosyası oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="758b0-148">**parse** or **-p:** Parses Baml, resources, or DLL files to generate a .csv or .txt file.</span></span>  
  
    - <span data-ttu-id="758b0-149">**oluşturmak** veya **-g:** Çevrilmiş bir dosya kullanarak yerelleştirilmiş bir ikili dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="758b0-149">**generate** or **-g:** Generates a localized binary file by using a translated file.</span></span>  
  
    - <span data-ttu-id="758b0-150">**out** veya **-o** {*filedirectory*] **:** Çıktı dosyası adı.</span><span class="sxs-lookup"><span data-stu-id="758b0-150">**out** or **-o** {*filedirectory*] **:** Output file name.</span></span>  
  
    - <span data-ttu-id="758b0-151">**kültür** veya **-cul** {*culture*] **:** Çıktı derlemelerinin yerelliği.</span><span class="sxs-lookup"><span data-stu-id="758b0-151">**culture** or **-cul** {*culture*] **:** Locale of output assemblies.</span></span>  
  
    - <span data-ttu-id="758b0-152">**çeviri** veya **-trans** {*translation.csv*] **:** Çevrilmiş veya yerelleştirilmiş dosya.</span><span class="sxs-lookup"><span data-stu-id="758b0-152">**translation** or **-trans** {*translation.csv*] **:** Translated or localized file.</span></span>  
  
    - <span data-ttu-id="758b0-153">**asmpath** veya **-asmpath:** {*filedirectory*] **:** Kodunuz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] özel denetimler içeriyorsa, **asmpath'i** özel denetim derlemesine sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="758b0-153">**asmpath** or **-asmpath:** {*filedirectory*] **:** If your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] code contains custom controls, you must supply the **asmpath** to the custom control assembly.</span></span>  
  
    - <span data-ttu-id="758b0-154">**nologo:** Hiçbir logo veya telif hakkı bilgisi görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="758b0-154">**nologo:** Displays no logo or copyright information.</span></span>  
  
    - <span data-ttu-id="758b0-155">**verbose:** Ayrıntılı mod bilgilerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="758b0-155">**verbose:** Displays verbose mode information.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="758b0-156">Aracı çalıştırırken seçeneklerin bir listesine ihtiyacınız varsa **LocBaml.exe** yazın ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="758b0-156">If you need a list of the options when you are running the tool, type     **LocBaml.exe** and press ENTER.</span></span>  
  
<a name="parse_dll"></a>
## <a name="use-locbaml-to-parse-a-file"></a><span data-ttu-id="758b0-157">Dosyayı Ayrışdırmak için LocBaml'ı kullanma</span><span class="sxs-lookup"><span data-stu-id="758b0-157">Use LocBaml to Parse a File</span></span>  
 <span data-ttu-id="758b0-158">Artık LocBaml aracını oluşturduğunuza göre, yerelleştirilecek metin içeriğini ayıklamak için HelloApp.resources.dll ayrıştırmak için kullanmaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="758b0-158">Now that you have created the LocBaml tool, you are ready to use it to parse HelloApp.resources.dll to extract the text content that will be localized.</span></span>  
  
1. <span data-ttu-id="758b0-159">LocBaml.exe'yi uygulamanızın ana uygulama derlemesinin oluşturulduğu bin\debug klasörüne kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="758b0-159">Copy LocBaml.exe to your application's bin\debug folder, where the main application assembly was created.</span></span>  
  
2. <span data-ttu-id="758b0-160">Uydu montaj dosyasını ayrıştırmak ve çıktıyı .csv dosyası olarak depolamak için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="758b0-160">To parse the satellite assembly file and store the output as a .csv file, use the following command:</span></span>  
  
     <span data-ttu-id="758b0-161">**LocBaml.exe /ayrışdırılan HelloApp.resources.dll /out:Hello.csv**</span><span class="sxs-lookup"><span data-stu-id="758b0-161">**LocBaml.exe /parse HelloApp.resources.dll /out:Hello.csv**</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="758b0-162">Giriş dosyası HelloApp.resources.dll, LocBaml.exe ile aynı dizinde değilse, her iki dosyanın da aynı dizinde olması için dosyalardan birini taşıyın.</span><span class="sxs-lookup"><span data-stu-id="758b0-162">If the input file, HelloApp.resources.dll, is not in the same directory as LocBaml.exe move one of the files so that both files are in the same directory.</span></span>  
  
3. <span data-ttu-id="758b0-163">LocBaml'ı dosyaları ayrıştırmak için çalıştırdığınızda, çıktı virgülle (.csv dosyaları) veya sekmelerle (.txt dosyaları) sınırlandırılmış yedi alandan oluşur.</span><span class="sxs-lookup"><span data-stu-id="758b0-163">When you run LocBaml to parse files, the output consists of seven fields delimited by commas (.csv files) or tabs (.txt files).</span></span> <span data-ttu-id="758b0-164">HelloApp.resources.dll için ayrışmış .csv dosyaaşağıdakileri gösterir:</span><span class="sxs-lookup"><span data-stu-id="758b0-164">The following shows the parsed .csv file for the HelloApp.resources.dll:</span></span>

   | |
   |-|
   |<span data-ttu-id="758b0-165">HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignore,FALSE, FALSE,#Text1;#Text2;</span><span class="sxs-lookup"><span data-stu-id="758b0-165">HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignore,FALSE, FALSE,,#Text1;#Text2;</span></span>|
   |<span data-ttu-id="758b0-166">HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World</span><span class="sxs-lookup"><span data-stu-id="758b0-166">HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World</span></span>|
   |<span data-ttu-id="758b0-167">HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World</span><span class="sxs-lookup"><span data-stu-id="758b0-167">HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World</span></span>|

   <span data-ttu-id="758b0-168">Yedi alan şunlardır:</span><span class="sxs-lookup"><span data-stu-id="758b0-168">The seven fields are:</span></span>  
  
   1. <span data-ttu-id="758b0-169">**BAML Adı**.</span><span class="sxs-lookup"><span data-stu-id="758b0-169">**BAML Name**.</span></span> <span data-ttu-id="758b0-170">Kaynak dil uydu derlemesi ile ilgili BAML kaynağının adı.</span><span class="sxs-lookup"><span data-stu-id="758b0-170">The name of the BAML resource with respect to the source language satellite assembly.</span></span>  
  
   2. <span data-ttu-id="758b0-171">**Kaynak Anahtarı**.</span><span class="sxs-lookup"><span data-stu-id="758b0-171">**Resource Key**.</span></span> <span data-ttu-id="758b0-172">Yerelleştirilmiş kaynak tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="758b0-172">The localized resource identifier.</span></span>  
  
   3. <span data-ttu-id="758b0-173">**Kategori**.</span><span class="sxs-lookup"><span data-stu-id="758b0-173">**Category**.</span></span> <span data-ttu-id="758b0-174">Değer türü.</span><span class="sxs-lookup"><span data-stu-id="758b0-174">The value type.</span></span> <span data-ttu-id="758b0-175">Bkz. [Yerelleştirme Öznitelikleri ve Açıklamaları](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="758b0-175">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   4. <span data-ttu-id="758b0-176">**Okunabilirlik**.</span><span class="sxs-lookup"><span data-stu-id="758b0-176">**Readability**.</span></span> <span data-ttu-id="758b0-177">Değerin bir yerelleştirici tarafından okunup okunamayacağı.</span><span class="sxs-lookup"><span data-stu-id="758b0-177">Whether the value can be read by a localizer.</span></span> <span data-ttu-id="758b0-178">Bkz. [Yerelleştirme Öznitelikleri ve Açıklamaları](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="758b0-178">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   5. <span data-ttu-id="758b0-179">**Değiştirilebilirlik**.</span><span class="sxs-lookup"><span data-stu-id="758b0-179">**Modifiability**.</span></span> <span data-ttu-id="758b0-180">Değerin bir yerelleştirici tarafından değiştirilip değiştirilemeyeceği.</span><span class="sxs-lookup"><span data-stu-id="758b0-180">Whether the value can be modified by a localizer.</span></span> <span data-ttu-id="758b0-181">Bkz. [Yerelleştirme Öznitelikleri ve Açıklamaları](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="758b0-181">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   6. <span data-ttu-id="758b0-182">**Yorumlar**.</span><span class="sxs-lookup"><span data-stu-id="758b0-182">**Comments**.</span></span> <span data-ttu-id="758b0-183">Bir değerin nasıl yerelleştirilmeye yardımcı olacak değerin ek açıklaması.</span><span class="sxs-lookup"><span data-stu-id="758b0-183">Additional description of the value to help determine how a value is localized.</span></span> <span data-ttu-id="758b0-184">Bkz. [Yerelleştirme Öznitelikleri ve Açıklamaları](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="758b0-184">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   7. <span data-ttu-id="758b0-185">**Değer**.</span><span class="sxs-lookup"><span data-stu-id="758b0-185">**Value**.</span></span> <span data-ttu-id="758b0-186">İstenilen kültüre çevirmek için metin değeri.</span><span class="sxs-lookup"><span data-stu-id="758b0-186">The text value to translate to the desired culture.</span></span>  
  
   <span data-ttu-id="758b0-187">Aşağıdaki tablo, bu alanların .csv dosyasının sınırlı değerleriyle nasıl eşleşiş gösterdiğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="758b0-187">The following table shows how these fields map to the delimited values of the .csv file:</span></span>  
  
   |<span data-ttu-id="758b0-188">BAML adı</span><span class="sxs-lookup"><span data-stu-id="758b0-188">BAML name</span></span>|<span data-ttu-id="758b0-189">Kaynak anahtarı</span><span class="sxs-lookup"><span data-stu-id="758b0-189">Resource key</span></span>|<span data-ttu-id="758b0-190">Kategori</span><span class="sxs-lookup"><span data-stu-id="758b0-190">Category</span></span>|<span data-ttu-id="758b0-191">Okunabilirlik</span><span class="sxs-lookup"><span data-stu-id="758b0-191">Readability</span></span>|<span data-ttu-id="758b0-192">Modifiability</span><span class="sxs-lookup"><span data-stu-id="758b0-192">Modifiability</span></span>|<span data-ttu-id="758b0-193">Yorumlar</span><span class="sxs-lookup"><span data-stu-id="758b0-193">Comments</span></span>|<span data-ttu-id="758b0-194">Değer</span><span class="sxs-lookup"><span data-stu-id="758b0-194">Value</span></span>|  
   |---------------|------------------|--------------|-----------------|-------------------|--------------|-----------|
   |<span data-ttu-id="758b0-195">MerhabaApp.g.tr-US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="758b0-195">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="758b0-196">Stack1:System.Windows.Controls.StackPanel.$Content</span><span class="sxs-lookup"><span data-stu-id="758b0-196">Stack1:System.Windows.Controls.StackPanel.$Content</span></span>|<span data-ttu-id="758b0-197">Yoksayma</span><span class="sxs-lookup"><span data-stu-id="758b0-197">Ignore</span></span>|<span data-ttu-id="758b0-198">FALSE</span><span class="sxs-lookup"><span data-stu-id="758b0-198">FALSE</span></span>|<span data-ttu-id="758b0-199">FALSE</span><span class="sxs-lookup"><span data-stu-id="758b0-199">FALSE</span></span>||<span data-ttu-id="758b0-200">#Text1;#Text2</span><span class="sxs-lookup"><span data-stu-id="758b0-200">#Text1;#Text2</span></span>|
   |<span data-ttu-id="758b0-201">MerhabaApp.g.tr-US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="758b0-201">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="758b0-202">Metin1:System.Windows.Controls.TextBlock.$Content</span><span class="sxs-lookup"><span data-stu-id="758b0-202">Text1:System.Windows.Controls.TextBlock.$Content</span></span>|<span data-ttu-id="758b0-203">None</span><span class="sxs-lookup"><span data-stu-id="758b0-203">None</span></span>|<span data-ttu-id="758b0-204">TRUE</span><span class="sxs-lookup"><span data-stu-id="758b0-204">TRUE</span></span>|<span data-ttu-id="758b0-205">TRUE</span><span class="sxs-lookup"><span data-stu-id="758b0-205">TRUE</span></span>||<span data-ttu-id="758b0-206">Hello World</span><span class="sxs-lookup"><span data-stu-id="758b0-206">Hello World</span></span>|
   |<span data-ttu-id="758b0-207">MerhabaApp.g.tr-US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="758b0-207">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="758b0-208">Text2:System.Windows.Controls.TextBlock.$Content</span><span class="sxs-lookup"><span data-stu-id="758b0-208">Text2:System.Windows.Controls.TextBlock.$Content</span></span>|<span data-ttu-id="758b0-209">None</span><span class="sxs-lookup"><span data-stu-id="758b0-209">None</span></span>|<span data-ttu-id="758b0-210">TRUE</span><span class="sxs-lookup"><span data-stu-id="758b0-210">TRUE</span></span>|<span data-ttu-id="758b0-211">TRUE</span><span class="sxs-lookup"><span data-stu-id="758b0-211">TRUE</span></span>||<span data-ttu-id="758b0-212">Güle Güle Dünya</span><span class="sxs-lookup"><span data-stu-id="758b0-212">Goodbye World</span></span>|
  
   <span data-ttu-id="758b0-213">**Yorumlar** alanıiçin tüm değerlerin hiçbir değer içermediğini unutmayın; bir alanın bir değeri yoksa, boştur.</span><span class="sxs-lookup"><span data-stu-id="758b0-213">Notice that all the values for the **Comments** field contain no values; if a field doesn't have a value, it is empty.</span></span> <span data-ttu-id="758b0-214">Ayrıca, ilk satırdaki öğenin ne okunabilir ne de değiştirilebilir olduğunu ve **Kategori** değeri olarak "Yoksay" öğesi olduğunu ve bunların hepsinin değerin yerelleştirilemeyeceğini gösterdiğini de unutmayın.</span><span class="sxs-lookup"><span data-stu-id="758b0-214">Also notice that the item in the first row is neither readable nor modifiable, and has "Ignore" as its **Category** value, all of which indicates that the value is not localizable.</span></span>  
  
4. <span data-ttu-id="758b0-215">Özellikle büyük dosyalarda, ayrıştırılan dosyalarda yerelleştirilebilir öğelerin bulunmasını kolaylaştırmak için, öğeleri **Kategori,** **Okunabilirlik**ve **Değiştirilebilirliğe**göre sıralayabilir veya filtreleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="758b0-215">To facilitate discovery of localizable items in parsed files, particularly in large files, you can sort or filter the items by **Category**, **Readability**, and **Modifiability**.</span></span> <span data-ttu-id="758b0-216">Örneğin, okunamayan ve değiştirilemez değerleri filtreleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="758b0-216">For example, you can filter out unreadable and unmodifiable values.</span></span>  
  
<a name="translate_loc_content"></a>
## <a name="translate-the-localizable-content"></a><span data-ttu-id="758b0-217">Yerelleştirilebilir İçeriği Çevirin</span><span class="sxs-lookup"><span data-stu-id="758b0-217">Translate the Localizable Content</span></span>  
 <span data-ttu-id="758b0-218">Çıkarılan içeriği çevirmek için kullanabileceğiniz herhangi bir aracı kullanın.</span><span class="sxs-lookup"><span data-stu-id="758b0-218">Use any tool that you have available to translate the extracted content.</span></span> <span data-ttu-id="758b0-219">Bunu yapmanın iyi bir yolu, kaynakları bir .csv dosyasına yazmak ve microsoft Excel'de görüntülemek ve son sütunda (değer) çeviri değişiklikleri yapmaktır.</span><span class="sxs-lookup"><span data-stu-id="758b0-219">A good way to do this is to write the resources to a .csv file and view them in Microsoft Excel, making translation changes to the last column (value).</span></span>  
  
<a name="merge_translations"></a>
## <a name="use-locbaml-to-generate-a-new-resourcesdll-file"></a><span data-ttu-id="758b0-220">Yeni bir .resources.dll Dosyası Oluşturmak için LocBaml'ı kullanın</span><span class="sxs-lookup"><span data-stu-id="758b0-220">Use LocBaml to Generate a New .resources.dll File</span></span>  
 <span data-ttu-id="758b0-221">HelloApp.resources.dll'yi LocBaml ile ayrıştarak tanımlanan içerik çevrilmiştir ve orijinal uygulamaya geri verilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="758b0-221">The content that was identified by parsing HelloApp.resources.dll with LocBaml has been translated and must be merged back into the original application.</span></span> <span data-ttu-id="758b0-222">Yeni bir .resources.dll dosyası oluşturmak için **oluşturma** veya **-g** seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="758b0-222">Use the **generate** or **-g** option to generate a new .resources.dll file.</span></span>  
  
1. <span data-ttu-id="758b0-223">Yeni bir HelloApp.resources.dll dosyası oluşturmak için aşağıdaki sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="758b0-223">Use the following syntax to generate a new HelloApp.resources.dll file.</span></span> <span data-ttu-id="758b0-224">Kültürü en-US (/cul:en-US) olarak işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="758b0-224">Mark the culture as en-US (/cul:en-US).</span></span>  
  
     <span data-ttu-id="758b0-225">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hello.csv /out:c:\ /cul:en-US**</span><span class="sxs-lookup"><span data-stu-id="758b0-225">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hello.csv /out:c:\ /cul:en-US**</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="758b0-226">Giriş dosyası Hello.csv, yürütülebilir, LocBaml.exe ile aynı dizinde değilse, her iki dosyanın da aynı dizinde olması için dosyalardan birini taşıyın.</span><span class="sxs-lookup"><span data-stu-id="758b0-226">If the input file, Hello.csv, is not in the same directory as the executable, LocBaml.exe, move one of the files so that both files are in the same directory.</span></span>  
  
2. <span data-ttu-id="758b0-227">C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll dizinini yeni oluşturduğunuz HelloApp.resources.dll dosyanızla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="758b0-227">Replace the old HelloApp.resources.dll file in the C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll directory with your newly created HelloApp.resources.dll file.</span></span>  
  
3. <span data-ttu-id="758b0-228">"Hello World" ve "Goodbye World" artık başvurunuzla çevrilmelidir.</span><span class="sxs-lookup"><span data-stu-id="758b0-228">"Hello World" and "Goodbye World" should now be translated in your application.</span></span>  
  
4. <span data-ttu-id="758b0-229">Farklı bir kültüre çevirmek için, çevirdiğiniz dilin kültürünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="758b0-229">To translate to a different culture, use the culture of the language that you are translating to.</span></span> <span data-ttu-id="758b0-230">Aşağıdaki örnek, Fransızca-Kanadaca nasıl çevrileceklerini gösterir:</span><span class="sxs-lookup"><span data-stu-id="758b0-230">The following example shows how to translate to French-Canadian:</span></span>  
  
     <span data-ttu-id="758b0-231">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c:\ /cul:fr-CA**</span><span class="sxs-lookup"><span data-stu-id="758b0-231">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c:\ /cul:fr-CA**</span></span>  
  
5. <span data-ttu-id="758b0-232">Ana uygulama derlemesi ile aynı derlemede, yeni uydu derlemesini barındırmak için kültüre özel yeni bir klasör oluşturun.</span><span class="sxs-lookup"><span data-stu-id="758b0-232">In the same assembly as the main application assembly, create a new culture-specific folder to house the new satellite assembly.</span></span> <span data-ttu-id="758b0-233">Fransızca-Kanada için, klasör fr-CA olacaktır.</span><span class="sxs-lookup"><span data-stu-id="758b0-233">For French-Canadian, the folder would be fr-CA.</span></span>  
  
6. <span data-ttu-id="758b0-234">Oluşturulan uydu derlemesini yeni klasöre kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="758b0-234">Copy the generated satellite assembly to the new folder.</span></span>  
  
7. <span data-ttu-id="758b0-235">Yeni uydu montajını test etmek için uygulamanızın çalışacağı kültürü değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="758b0-235">To test the new satellite assembly, you need to change the culture under which your application will run.</span></span> <span data-ttu-id="758b0-236">Bunu iki yoldan biriyle yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="758b0-236">You can do this in one of two ways:</span></span>  
  
    - <span data-ttu-id="758b0-237">İşletim sisteminizin bölgesel ayarlarını**değiştirin** **(Bölgesel ve Dil Seçenekleri**&#124; &#124; **Kontrol Paneli** başlatın).</span><span class="sxs-lookup"><span data-stu-id="758b0-237">Change your operating system's regional settings (**Start** &#124; **Control Panel** &#124; **Regional and Language Options**).</span></span>  
  
    - <span data-ttu-id="758b0-238">Uygulamanızda, App.xaml.cs için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="758b0-238">In your application, add the following code to App.xaml.cs:</span></span>  
  
   [!code-xaml[LocBamlChangeCultureSnippets#LocBamlChangeCultureMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml#locbamlchangeculturemarkup)]
   [!code-csharp[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml.cs#locbamlchangeculturecodebehind)]
   [!code-vb[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/VisualBasic/Application.xaml.vb#locbamlchangeculturecodebehind)]  
  
<a name="Some_Tips_for_Using_LocBaml"></a>
## <a name="some-tips-for-using-locbaml"></a><span data-ttu-id="758b0-239">LocBaml kullanmak için bazı ipuçları</span><span class="sxs-lookup"><span data-stu-id="758b0-239">Some Tips for Using LocBaml</span></span>  
  
- <span data-ttu-id="758b0-240">Özel denetimleri tanımlayan tüm bağımlı derlemeler LocBaml'ın yerel dizinine kopyalanmalıdır veya GAC'ye yüklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="758b0-240">All dependent assemblies that define custom controls must be copied into the local directory of LocBaml or installed into the GAC.</span></span> <span data-ttu-id="758b0-241">Bu gereklidir, çünkü yerelleştirme API'si ikili XAML (BAML) okurken bağımlı derlemelere erişebilmeli.</span><span class="sxs-lookup"><span data-stu-id="758b0-241">This is necessary because the localization API must have access to the dependent assemblies when it reads the binary XAML (BAML).</span></span>  
  
- <span data-ttu-id="758b0-242">Ana derleme imzalanırsa, yüklenmesi için oluşturulan kaynak DLL'nin de imzalanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="758b0-242">If the main assembly is signed, the generated resource DLL must also be signed in order for it to be loaded.</span></span>  
  
- <span data-ttu-id="758b0-243">Yerelleştirilmiş kaynak DLL sürümü ana derleme ile eşitlenmiş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="758b0-243">The version of the localized resource DLL needs to be synchronized with the main assembly.</span></span>  
  
<a name="Whats_Next"></a>
## <a name="whats-next"></a><span data-ttu-id="758b0-244">Sırada Ne Var</span><span class="sxs-lookup"><span data-stu-id="758b0-244">What's Next</span></span>  
 <span data-ttu-id="758b0-245">Şimdi LocBaml aracını nasıl kullanacağınız konusunda temel bir anlayışa sahip olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="758b0-245">You should now have a basic understanding of how to use the LocBaml tool.</span></span>  <span data-ttu-id="758b0-246">Uid'ler içeren bir dosya yapmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="758b0-246">You should be able to make a file that contains Uids.</span></span> <span data-ttu-id="758b0-247">LocBaml aracını kullanarak, yerelleştirilebilir içeriği ayıklamak için bir dosyayı ayrıştıramalısınız ve içerik çevrildikten sonra çevrilen içeriği birleştiren bir .resources.dll dosyası oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="758b0-247">By using the LocBaml tool, you should be able to parse a file to extract the localizable content, and after the content is translated, you should be able to generate a .resources.dll file that merges the translated content.</span></span> <span data-ttu-id="758b0-248">Bu konu mümkün olan her ayrıntıyı içermez, ancak artık uygulamalarınızı yerelleştirmek için LocBaml'ı kullanmanız gereken bilgiye sahipsiniz.</span><span class="sxs-lookup"><span data-stu-id="758b0-248">This topic does not include every possible detail, but you now have the knowledge necessary to use LocBaml for localizing your applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="758b0-249">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="758b0-249">See also</span></span>

- [<span data-ttu-id="758b0-250">WPF için Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="758b0-250">Globalization for WPF</span></span>](globalization-for-wpf.md)
- [<span data-ttu-id="758b0-251">Otomatik Düzen Kullanımına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="758b0-251">Use Automatic Layout Overview</span></span>](use-automatic-layout-overview.md)
