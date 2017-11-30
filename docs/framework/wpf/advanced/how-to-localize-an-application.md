---
title: "Nasıl yapılır: Bir Uygulamayı Yerelleştirme"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- localization [WPF], applications
- LocBaml tool [WPF]
- applications [WPF], localizing
ms.assetid: 5001227e-9326-48a4-9dcd-ba1b89ee6653
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: df52c44ca72108ffc984bed169daae654c01aa87
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-localize-an-application"></a><span data-ttu-id="db762-102">Nasıl yapılır: Bir Uygulamayı Yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="db762-102">How to: Localize an Application</span></span>
<span data-ttu-id="db762-103">Bu öğretici LocBaml aracını kullanarak yerelleştirilmiş bir uygulama oluşturma açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="db762-103">This tutorial explains how to create a localized application by using the LocBaml tool.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="db762-104">LocBaml aracı üretime hazır bir uygulama değil.</span><span class="sxs-lookup"><span data-stu-id="db762-104">The LocBaml tool is not a production-ready application.</span></span> <span data-ttu-id="db762-105">Bazı yerelleştirme API'lerini kullanan ve bir yerelleştirme aracını nasıl yazabilir gösterilmektedir bir örnek olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="db762-105">It is presented as a sample that uses some of the localization APIs and illustrates how you might write a localization tool.</span></span>  
  
<a name="Introduction"></a>   
## <a name="overview"></a><span data-ttu-id="db762-106">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="db762-106">Overview</span></span>  
 <span data-ttu-id="db762-107">Bu tartışma uygulama yerelleştirme için adım adım bir yaklaşım sağlar.</span><span class="sxs-lookup"><span data-stu-id="db762-107">This discussion gives you a step-by-step approach to localizing an application.</span></span> <span data-ttu-id="db762-108">İlk olarak, böylece çevrilir metin ayıklanabilir uygulamanızı hazırlayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="db762-108">First, you will prepare your application so that the text that will be translated can be extracted.</span></span> <span data-ttu-id="db762-109">Metin çevrilen sonra özgün uygulamayı yeni bir kopyasını çevrilmiş metni birleştirir.</span><span class="sxs-lookup"><span data-stu-id="db762-109">After the text is translated, you will merge the translated text into a new copy of the original application.</span></span>  
  
<a name="Requirements"></a>   
## <a name="requirements"></a><span data-ttu-id="db762-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="db762-110">Requirements</span></span>  
 <span data-ttu-id="db762-111">Bu tartışma süresince kullanacağınız [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)], komut satırından çalışan bir derleyici olduğu.</span><span class="sxs-lookup"><span data-stu-id="db762-111">Over the course of this discussion, you will use [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)], which is a compiler that runs from the command line.</span></span>  
  
 <span data-ttu-id="db762-112">Ayrıca, proje dosyasını kullanmanız istenecek.</span><span class="sxs-lookup"><span data-stu-id="db762-112">Also, you will be instructed to use a project file.</span></span> <span data-ttu-id="db762-113">Nasıl kullanılacağı hakkında yönergeler için [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] ve proje dosyalarını bkz [oluşturma ve dağıtma](../../../../docs/framework/wpf/app-development/building-and-deploying-wpf-applications.md).</span><span class="sxs-lookup"><span data-stu-id="db762-113">For instructions on how to use [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] and project files, see [Build and Deploy](../../../../docs/framework/wpf/app-development/building-and-deploying-wpf-applications.md).</span></span>  
  
 <span data-ttu-id="db762-114">Bu konudaki tüm örnekler kültür olarak en-US (İngilizce-ABD) kullanın.</span><span class="sxs-lookup"><span data-stu-id="db762-114">All the examples in this discussion use en-US (English-US) as the culture.</span></span> <span data-ttu-id="db762-115">Bu, farklı bir dil yüklemeden örneklerin adımlarını çalışmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="db762-115">This enables you to work through the steps of the examples without installing a different language.</span></span>  
  
<a name="create_sample_app"></a>   
## <a name="create-a-sample-application"></a><span data-ttu-id="db762-116">Örnek bir uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="db762-116">Create a Sample Application</span></span>  
 <span data-ttu-id="db762-117">Bu adımda, uygulamanızı yerelleştirme için hazırlarsınız.</span><span class="sxs-lookup"><span data-stu-id="db762-117">In this step, you will prepare your application for localization.</span></span> <span data-ttu-id="db762-118">İçinde [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] örnekleri, bu konudaki kod örnekleri için kullanılacak bir HelloApp örnek sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="db762-118">In the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] samples, a HelloApp sample is supplied that will be used for the code examples in this discussion.</span></span> <span data-ttu-id="db762-119">Bu örneği kullanmak istiyorsanız, indirme [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosyaları buradan [LocBaml aracı örneği](http://go.microsoft.com/fwlink/?LinkID=160016).</span><span class="sxs-lookup"><span data-stu-id="db762-119">If you would like to use this sample, download the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] files from the [LocBaml Tool Sample](http://go.microsoft.com/fwlink/?LinkID=160016).</span></span>  
  
1.  <span data-ttu-id="db762-120">Yerelleştirme başlatmak istediğiniz noktasına uygulamanızı geliştirin.</span><span class="sxs-lookup"><span data-stu-id="db762-120">Develop your application to the point where you want to start localization.</span></span>  
  
2.  <span data-ttu-id="db762-121">Proje dosyasında geliştirme dilini belirtin böylece [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] ana derleme ve uydu derlemesini oluşturur (bir dosyayla. resources.dll uzantısı) dilden bağımsız kaynakları içerecek şekilde.</span><span class="sxs-lookup"><span data-stu-id="db762-121">Specify the development language in the project file so that [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] generates a main assembly and a satellite assembly (a file with the .resources.dll extension) to contain the neutral language resources.</span></span> <span data-ttu-id="db762-122">HelloApp örnek proje dosyasında HelloApp.csproj'dur.</span><span class="sxs-lookup"><span data-stu-id="db762-122">The project file in the HelloApp sample is HelloApp.csproj.</span></span> <span data-ttu-id="db762-123">Bu dosyada, aşağıdaki gibi tanımlanan geliştirme dilini bulabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="db762-123">In that file, you will find the development language identified as follows:</span></span>  
  
     `<UICulture>en-US</UICulture>`  
  
3.  <span data-ttu-id="db762-124">Uıd'leri için ekleme, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyaları.</span><span class="sxs-lookup"><span data-stu-id="db762-124">Add Uids to your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files.</span></span> <span data-ttu-id="db762-125">Uıd'leri dosyalardaki değişiklikler izlemek ve çevrilmelidir öğeleri tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="db762-125">Uids are used to keep track of changes to files and to identify items that must be translated.</span></span> <span data-ttu-id="db762-126">Uıd'leri dosyalarınıza eklemek için çalıştırın **updateuid** proje dosyanızda:</span><span class="sxs-lookup"><span data-stu-id="db762-126">To add Uids to your files, run **updateuid** on your project file:</span></span>  
  
     <span data-ttu-id="db762-127">**MSBuild /t:updateuid helloapp.csproj**</span><span class="sxs-lookup"><span data-stu-id="db762-127">**msbuild /t:updateuid helloapp.csproj**</span></span>  
  
     <span data-ttu-id="db762-128">Eksik veya Uıd'leri yinelenen doğrulamak için çalıştırın **checkuid**:</span><span class="sxs-lookup"><span data-stu-id="db762-128">To verify that you have no missing or duplicate Uids, run **checkuid**:</span></span>  
  
     <span data-ttu-id="db762-129">**MSBuild /t:checkuid helloapp.csproj**</span><span class="sxs-lookup"><span data-stu-id="db762-129">**msbuild /t:checkuid helloapp.csproj**</span></span>  
  
     <span data-ttu-id="db762-130">Çalıştırdıktan sonra **updateuid**, dosyalarınızı Uıd'leri içermelidir.</span><span class="sxs-lookup"><span data-stu-id="db762-130">After running **updateuid**, your files should contain Uids.</span></span> <span data-ttu-id="db762-131">Örneğin, Pane1.xaml dosyasında, aşağıdaki bulduğunuz:</span><span class="sxs-lookup"><span data-stu-id="db762-131">For example, in the Pane1.xaml file of HelloApp, you should find the following:</span></span>  
  
     `<StackPanel x:Uid="StackPanel_1">`  
  
     `<TextBlock x:Uid="TextBlock_1">Hello World</TextBlock>`  
  
     `<TextBlock x:Uid="TextBlock_2">Goodbye World</TextBlock>`  
  
     `</StackPanel>`  
  
<a name="create_dll"></a>   
## <a name="create-the-neutral-language-resources-satellite-assembly"></a><span data-ttu-id="db762-132">Dilden kaynakların uydu derlemesini oluşturun</span><span class="sxs-lookup"><span data-stu-id="db762-132">Create the Neutral Language Resources Satellite Assembly</span></span>  
 <span data-ttu-id="db762-133">Uygulama, bir dilden bağımsız kaynakların uydu derlemesini oluşturmak için yapılandırıldıktan sonra uygulamayı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="db762-133">After the application is configured to generate a neutral language resources satellite assembly, you build the application.</span></span> <span data-ttu-id="db762-134">Bu, yerelleştirme için LocBaml tarafından gereken dilden kaynakları uydu derlemesini yanı sıra ana uygulama derlemesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="db762-134">This generates the main application assembly, as well as the neutral language resources satellite assembly that is required by LocBaml for localization.</span></span> <span data-ttu-id="db762-135">Uygulamayı yapılandırmak için:</span><span class="sxs-lookup"><span data-stu-id="db762-135">To build the application:</span></span>  
  
1.  <span data-ttu-id="db762-136">Oluşturmak için HelloApp derleyin bir [!INCLUDE[TLA#tla_dll](../../../../includes/tlasharptla-dll-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="db762-136">Compile HelloApp to create a [!INCLUDE[TLA#tla_dll](../../../../includes/tlasharptla-dll-md.md)]:</span></span>  
  
     <span data-ttu-id="db762-137">**MSBuild helloapp.csproj**</span><span class="sxs-lookup"><span data-stu-id="db762-137">**msbuild helloapp.csproj**</span></span>  
  
2.  <span data-ttu-id="db762-138">Yeni oluşturulan ana uygulama bütünleştirilmiş kodu HelloApp.exe aşağıdaki klasörde oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="db762-138">The newly created main application assembly, HelloApp.exe, is created in the following folder:</span></span>  
  
     `C:\HelloApp\Bin\Debug\`  
  
3.  <span data-ttu-id="db762-139">Yeni oluşturulan dilden kaynakları uydu derlemesini HelloApp.resources.dll aşağıdaki klasörde oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="db762-139">The newly created neutral language resources satellite assembly, HelloApp.resources.dll, is created in the following folder:</span></span>  
  
     `C:\HelloApp\Bin\Debug\en-US\`  
  
<a name="build_locbaml"></a>   
## <a name="build-the-locbaml-tool"></a><span data-ttu-id="db762-140">LocBaml aracını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="db762-140">Build the LocBaml Tool</span></span>  
  
1.  <span data-ttu-id="db762-141">LocBaml'i yapılandırmak için gerekli tüm dosyalar bulunur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="db762-141">All the files necessary to build LocBaml are located in the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] samples.</span></span> <span data-ttu-id="db762-142">Karşıdan [!INCLUDE[TLA#tla_lhcshrp](../../../../includes/tlasharptla-lhcshrp-md.md)] dosyaları buradan [LocBaml aracı örneği](http://go.microsoft.com/fwlink/?LinkID=160016).</span><span class="sxs-lookup"><span data-stu-id="db762-142">Download the [!INCLUDE[TLA#tla_lhcshrp](../../../../includes/tlasharptla-lhcshrp-md.md)] files from the [LocBaml Tool Sample](http://go.microsoft.com/fwlink/?LinkID=160016).</span></span>  
  
2.  <span data-ttu-id="db762-143">Komut satırından aracı yapılandırmak için proje dosyası (locbaml.csproj) çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="db762-143">From the command line, run the project file (locbaml.csproj) to build the tool:</span></span>  
  
     <span data-ttu-id="db762-144">**MSBuild locbaml.csproj**</span><span class="sxs-lookup"><span data-stu-id="db762-144">**msbuild locbaml.csproj**</span></span>  
  
3.  <span data-ttu-id="db762-145">Yeni oluşturulan yürütülebilir dosya (locbaml.exe) bulmak için Bin\Release dizinine gidin.</span><span class="sxs-lookup"><span data-stu-id="db762-145">Go to the Bin\Release directory to find the newly created executable file (locbaml.exe).</span></span> <span data-ttu-id="db762-146">Example:C:\LocBaml\Bin\Release\locbaml.exe.</span><span class="sxs-lookup"><span data-stu-id="db762-146">Example:C:\LocBaml\Bin\Release\locbaml.exe.</span></span>  
  
4.  <span data-ttu-id="db762-147">LocBaml'i çalıştırdığınızda belirtebilirsiniz seçenekleri aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="db762-147">The options that you can specify when you run LocBaml are as follows:</span></span>  
  
    -   <span data-ttu-id="db762-148">**Ayrıştırma** veya **-p:** ayrıştırır Baml, kaynaklar veya [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] .csv veya .txt dosyası oluşturmak için dosyaları.</span><span class="sxs-lookup"><span data-stu-id="db762-148">**parse** or **-p:** Parses Baml, resources, or [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] files to generate a .csv or .txt file.</span></span>  
  
    -   <span data-ttu-id="db762-149">**Oluştur** veya **-g:** çevrilmiş dosyayı kullanarak yerelleştirilmiş bir ikili dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="db762-149">**generate** or **-g:** Generates a localized binary file by using a translated file.</span></span>  
  
    -   <span data-ttu-id="db762-150">**out** veya **-o** {*filedirectory*] **:** çıktı dosyası adı.</span><span class="sxs-lookup"><span data-stu-id="db762-150">**out** or **-o** {*filedirectory*] **:** Output file name.</span></span>  
  
    -   <span data-ttu-id="db762-151">**kültür** veya **- cul** {*kültür*] **:** çıkış derlemelerinin yerel ayarı.</span><span class="sxs-lookup"><span data-stu-id="db762-151">**culture** or **-cul** {*culture*] **:** Locale of output assemblies.</span></span>  
  
    -   <span data-ttu-id="db762-152">**Çeviri** veya **- hareketi** {*translation.csv*] **:** çevrilmiş ya da yerelleştirilmiş dosya.</span><span class="sxs-lookup"><span data-stu-id="db762-152">**translation** or **-trans** {*translation.csv*] **:** Translated or localized file.</span></span>  
  
    -   <span data-ttu-id="db762-153">**asmpath** veya **- asmpath:** {*filedirectory*] **:** varsa, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kodu özel denetimleri içeriyorsa, sağlamanız gerekir  **asmpath** özel denetim derleme.</span><span class="sxs-lookup"><span data-stu-id="db762-153">**asmpath** or **-asmpath:** {*filedirectory*] **:** If your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] code contains custom controls, you must supply the **asmpath** to the custom control assembly.</span></span>  
  
    -   <span data-ttu-id="db762-154">**nologo:** hiçbir logo veya telif hakkı bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="db762-154">**nologo:** Displays no logo or copyright information.</span></span>  
  
    -   <span data-ttu-id="db762-155">**ayrıntılı:** ayrıntılı mod bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="db762-155">**verbose:** Displays verbose mode information.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="db762-156">Aracı çalıştırırken seçeneklerin bir listesini gerekiyorsa, yazın **LocBaml.exe'yi** ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="db762-156">If you need a list of the options when you are running the tool, type     **LocBaml.exe** and press ENTER.</span></span>  
  
<a name="parse_dll"></a>   
## <a name="use-locbaml-to-parse-a-file"></a><span data-ttu-id="db762-157">Bir dosyayı ayrıştırmak için LocBaml Kullanma</span><span class="sxs-lookup"><span data-stu-id="db762-157">Use LocBaml to Parse a File</span></span>  
 <span data-ttu-id="db762-158">LocBaml aracını oluşturduğunuza göre bunu yerelleştirilmiş olabilir metin içeriği ayıklamak için HelloApp.resources.dll ayrıştırmak için kullanılacak hazır olursunuz.</span><span class="sxs-lookup"><span data-stu-id="db762-158">Now that you have created the LocBaml tool, you are ready to use it to parse HelloApp.resources.dll to extract the text content that will be localized.</span></span>  
  
1.  <span data-ttu-id="db762-159">LocBaml.exe'yi ana uygulama derlemesini oluşturulduğu uygulamanızın klasörüne, kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="db762-159">Copy LocBaml.exe to your application's bin\debug folder, where the main application assembly was created.</span></span>  
  
2.  <span data-ttu-id="db762-160">Uydu derleme dosyasını ayrıştırabilir ve çıktıyı bir .csv dosyası olarak depolamak için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="db762-160">To parse the satellite assembly file and store the output as a .csv file, use the following command:</span></span>  
  
     <span data-ttu-id="db762-161">**LocBaml.exe'yi /parse HelloApp.resources.dll /out:Hello.csv**</span><span class="sxs-lookup"><span data-stu-id="db762-161">**LocBaml.exe /parse HelloApp.resources.dll /out:Hello.csv**</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="db762-162">HelloApp.resources.dll giriş dosyası içinde değilse LocBaml.exe'yi aynı dizine taşıyın dosyalarından birini dosyalarının her ikisinin de aynı dizinde; böylece.</span><span class="sxs-lookup"><span data-stu-id="db762-162">If the input file, HelloApp.resources.dll, is not in the same directory as LocBaml.exe move one of the files so that both files are in the same directory.</span></span>  
  
3.  <span data-ttu-id="db762-163">Dosyaları ayrıştırmak için LocBaml'i çalıştırdığınızda, çıktı virgüller (.csv dosyaları) veya sekmeler (.txt dosyaları) tarafından ayrılmış yedi alandan oluşur.</span><span class="sxs-lookup"><span data-stu-id="db762-163">When you run LocBaml to parse files, the output consists of seven fields delimited by commas (.csv files) or tabs (.txt files).</span></span> <span data-ttu-id="db762-164">Aşağıdaki, HelloApp.resources.dll için ayrıştırılmış .csv dosyasını gösterir:</span><span class="sxs-lookup"><span data-stu-id="db762-164">The following shows the parsed .csv file for the HelloApp.resources.dll:</span></span>

   | |
   |-|
   |<span data-ttu-id="db762-165">HelloApp.g.en US.resources:window1.baml, Stack1:System.Windows.Controls.StackPanel. $Content, Yoksay yanlış, yanlış,, # Metin1; # Metin2;</span><span class="sxs-lookup"><span data-stu-id="db762-165">HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignore,FALSE, FALSE,,#Text1;#Text2;</span></span>|
   |<span data-ttu-id="db762-166">HelloApp.g.en US.resources:window1.baml, Text1:System.Windows.Controls.TextBlock. hiçbiri, $Content TRUE, TRUE,, Merhaba Dünya</span><span class="sxs-lookup"><span data-stu-id="db762-166">HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World</span></span>|
   |<span data-ttu-id="db762-167">HelloApp.g.en US.resources:window1.baml, Text2:System.Windows.Controls.TextBlock. hiçbiri, $Content TRUE, TRUE,, Goodbye World</span><span class="sxs-lookup"><span data-stu-id="db762-167">HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World</span></span>|

   <span data-ttu-id="db762-168">Yedi alanlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="db762-168">The seven fields are:</span></span>  
  
   1.  <span data-ttu-id="db762-169">**BAML adı**.</span><span class="sxs-lookup"><span data-stu-id="db762-169">**BAML Name**.</span></span> <span data-ttu-id="db762-170">Kaynak dili uydu derlemesine göre BAML kaynağının adı.</span><span class="sxs-lookup"><span data-stu-id="db762-170">The name of the BAML resource with respect to the source language satellite assembly.</span></span>  
  
   2.  <span data-ttu-id="db762-171">**Kaynak anahtarı**.</span><span class="sxs-lookup"><span data-stu-id="db762-171">**Resource Key**.</span></span> <span data-ttu-id="db762-172">Yerelleştirilmiş kaynak tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="db762-172">The localized resource identifier.</span></span>  
  
   3.  <span data-ttu-id="db762-173">**Kategori**.</span><span class="sxs-lookup"><span data-stu-id="db762-173">**Category**.</span></span> <span data-ttu-id="db762-174">Değer türü.</span><span class="sxs-lookup"><span data-stu-id="db762-174">The value type.</span></span> <span data-ttu-id="db762-175">Bkz: [Yerelleştirme öznitelikleri ve Yorumlar](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="db762-175">See [Localization Attributes and Comments](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).</span></span>  
  
   4.  <span data-ttu-id="db762-176">**Okunabilirlik**.</span><span class="sxs-lookup"><span data-stu-id="db762-176">**Readability**.</span></span> <span data-ttu-id="db762-177">Olup değeri yerelleştirici tarafından okunabilir.</span><span class="sxs-lookup"><span data-stu-id="db762-177">Whether the value can be read by a localizer.</span></span> <span data-ttu-id="db762-178">Bkz: [Yerelleştirme öznitelikleri ve Yorumlar](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="db762-178">See [Localization Attributes and Comments](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).</span></span>  
  
   5.  <span data-ttu-id="db762-179">**Modifiability'e göre**.</span><span class="sxs-lookup"><span data-stu-id="db762-179">**Modifiability**.</span></span> <span data-ttu-id="db762-180">Olup değeri yerelleştirici tarafından değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="db762-180">Whether the value can be modified by a localizer.</span></span> <span data-ttu-id="db762-181">Bkz: [Yerelleştirme öznitelikleri ve Yorumlar](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="db762-181">See [Localization Attributes and Comments](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).</span></span>  
  
   6.  <span data-ttu-id="db762-182">**Açıklamaları**.</span><span class="sxs-lookup"><span data-stu-id="db762-182">**Comments**.</span></span> <span data-ttu-id="db762-183">Ek açıklama değeri nasıl yerelleştirilmiş belirlemeye yardımcı olmak için değeri.</span><span class="sxs-lookup"><span data-stu-id="db762-183">Additional description of the value to help determine how a value is localized.</span></span> <span data-ttu-id="db762-184">Bkz: [Yerelleştirme öznitelikleri ve Yorumlar](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="db762-184">See [Localization Attributes and Comments](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).</span></span>  
  
   7.  <span data-ttu-id="db762-185">**Değer**.</span><span class="sxs-lookup"><span data-stu-id="db762-185">**Value**.</span></span> <span data-ttu-id="db762-186">İstenen kültüre çevirmek için metin değeri.</span><span class="sxs-lookup"><span data-stu-id="db762-186">The text value to translate to the desired culture.</span></span>  
  
   <span data-ttu-id="db762-187">Aşağıdaki tabloda, bu alanların .csv dosyasının ayrılmış değerlere nasıl karşıladığı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="db762-187">The following table shows how these fields map to the delimited values of the .csv file:</span></span>  
  
   |<span data-ttu-id="db762-188">BAML adı</span><span class="sxs-lookup"><span data-stu-id="db762-188">BAML name</span></span>|<span data-ttu-id="db762-189">Kaynak anahtarı</span><span class="sxs-lookup"><span data-stu-id="db762-189">Resource key</span></span>|<span data-ttu-id="db762-190">Kategori</span><span class="sxs-lookup"><span data-stu-id="db762-190">Category</span></span>|<span data-ttu-id="db762-191">Okunabilirlik</span><span class="sxs-lookup"><span data-stu-id="db762-191">Readability</span></span>|<span data-ttu-id="db762-192">Modifiability'e göre</span><span class="sxs-lookup"><span data-stu-id="db762-192">Modifiability</span></span>|<span data-ttu-id="db762-193">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="db762-193">Comments</span></span>|<span data-ttu-id="db762-194">Değer</span><span class="sxs-lookup"><span data-stu-id="db762-194">Value</span></span>|  
   |---------------|------------------|--------------|-----------------|-------------------|--------------|-----------|
   |<span data-ttu-id="db762-195">HelloApp.g.en US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="db762-195">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="db762-196">Stack1:System.Windows.Controls.StackPanel.$Content</span><span class="sxs-lookup"><span data-stu-id="db762-196">Stack1:System.Windows.Controls.StackPanel.$Content</span></span>|<span data-ttu-id="db762-197">Yoksay</span><span class="sxs-lookup"><span data-stu-id="db762-197">Ignore</span></span>|<span data-ttu-id="db762-198">FALSE</span><span class="sxs-lookup"><span data-stu-id="db762-198">FALSE</span></span>|<span data-ttu-id="db762-199">FALSE</span><span class="sxs-lookup"><span data-stu-id="db762-199">FALSE</span></span>||<span data-ttu-id="db762-200"># Metin1; # Metin2</span><span class="sxs-lookup"><span data-stu-id="db762-200">#Text1;#Text2</span></span>|
   |<span data-ttu-id="db762-201">HelloApp.g.en US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="db762-201">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="db762-202">Text1:System.Windows.Controls.TextBlock.$Content</span><span class="sxs-lookup"><span data-stu-id="db762-202">Text1:System.Windows.Controls.TextBlock.$Content</span></span>|<span data-ttu-id="db762-203">Yok.</span><span class="sxs-lookup"><span data-stu-id="db762-203">None</span></span>|<span data-ttu-id="db762-204">TRUE</span><span class="sxs-lookup"><span data-stu-id="db762-204">TRUE</span></span>|<span data-ttu-id="db762-205">TRUE</span><span class="sxs-lookup"><span data-stu-id="db762-205">TRUE</span></span>||<span data-ttu-id="db762-206">Merhaba Dünya</span><span class="sxs-lookup"><span data-stu-id="db762-206">Hello World</span></span>|
   |<span data-ttu-id="db762-207">HelloApp.g.en US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="db762-207">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="db762-208">Text2:System.Windows.Controls.TextBlock.$Content</span><span class="sxs-lookup"><span data-stu-id="db762-208">Text2:System.Windows.Controls.TextBlock.$Content</span></span>|<span data-ttu-id="db762-209">Yok.</span><span class="sxs-lookup"><span data-stu-id="db762-209">None</span></span>|<span data-ttu-id="db762-210">TRUE</span><span class="sxs-lookup"><span data-stu-id="db762-210">TRUE</span></span>|<span data-ttu-id="db762-211">TRUE</span><span class="sxs-lookup"><span data-stu-id="db762-211">TRUE</span></span>||<span data-ttu-id="db762-212">Güle güle World</span><span class="sxs-lookup"><span data-stu-id="db762-212">Goodbye World</span></span>|
  
   <span data-ttu-id="db762-213">Dikkat tüm değerleri **açıklamaları** alan hiçbir değer içeriyor; bir alan bir değer yoksa, boş.</span><span class="sxs-lookup"><span data-stu-id="db762-213">Notice that all the values for the **Comments** field contain no values; if a field doesn't have a value, it is empty.</span></span> <span data-ttu-id="db762-214">Ayrıca ilk satırda öğesi ne okunabilir ne de değiştirilebilir ve "Yoksay" sahip olarak dikkat edin, **kategori** değeri, her biri gösteren değer yerelleştirilebilir değil.</span><span class="sxs-lookup"><span data-stu-id="db762-214">Also notice that the item in the first row is neither readable nor modifiable, and has "Ignore" as its **Category** value, all of which indicates that the value is not localizable.</span></span>  
  
4.  <span data-ttu-id="db762-215">Ayrıştırılmış dosyalarında, özellikle de büyük dosyalarda yerelleştirilebilir öğelerin bulma kolaylaştırmak için listeyi sıralayın veya öğeleri göre filtrele **kategori**, **okunabilirlik**, ve **Modifiability'egöre**.</span><span class="sxs-lookup"><span data-stu-id="db762-215">To facilitate discovery of localizable items in parsed files, particularly in large files, you can sort or filter the items by **Category**, **Readability**, and **Modifiability**.</span></span> <span data-ttu-id="db762-216">Örneğin, okunamaz ve değiştirilemeyen değerlere filtre uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db762-216">For example, you can filter out unreadable and unmodifiable values.</span></span>  
  
<a name="translate_loc_content"></a>   
## <a name="translate-the-localizable-content"></a><span data-ttu-id="db762-217">Yerelleştirilebilir İçerik Çevir</span><span class="sxs-lookup"><span data-stu-id="db762-217">Translate the Localizable Content</span></span>  
 <span data-ttu-id="db762-218">Ayıklanan içeriği çevirmek kullanılabilir olan herhangi bir aracı kullanın.</span><span class="sxs-lookup"><span data-stu-id="db762-218">Use any tool that you have available to translate the extracted content.</span></span> <span data-ttu-id="db762-219">Bunu yapmak için en iyi yolu kaynakları .csv dosya ve görüntülemeye yazmaktır [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)], çeviri yapma değişikliklerini son sütun (değer).</span><span class="sxs-lookup"><span data-stu-id="db762-219">A good way to do this is to write the resources to a .csv file and view them in [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)], making translation changes to the last column (value).</span></span>  
  
<a name="merge_translations"></a>   
## <a name="use-locbaml-to-generate-a-new-resourcesdll-file"></a><span data-ttu-id="db762-220">Yeni bir oluşturmak için LocBaml kullanın. resources.dll dosyası</span><span class="sxs-lookup"><span data-stu-id="db762-220">Use LocBaml to Generate a New .resources.dll File</span></span>  
 <span data-ttu-id="db762-221">LocBaml ile HelloApp.resources.DLL'i tarafından tanımlanan içerik çevrilmiştir ve özgün uygulamasına birleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="db762-221">The content that was identified by parsing HelloApp.resources.dll with LocBaml has been translated and must be merged back into the original application.</span></span> <span data-ttu-id="db762-222">Kullanım **oluşturmak** veya **-g** yeni oluşturmak için seçeneği. resources.dll dosyası.</span><span class="sxs-lookup"><span data-stu-id="db762-222">Use the **generate** or **-g** option to generate a new .resources.dll file.</span></span>  
  
1.  <span data-ttu-id="db762-223">Yeni bir HelloApp.resources.dll dosyası oluşturmak için aşağıdaki sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="db762-223">Use the following syntax to generate a new HelloApp.resources.dll file.</span></span> <span data-ttu-id="db762-224">Kültür en-US olarak işaretle (/ cul: en-US).</span><span class="sxs-lookup"><span data-stu-id="db762-224">Mark the culture as en-US (/cul:en-US).</span></span>  
  
     <span data-ttu-id="db762-225">**LocBaml.exe'yi / HelloApp.resources.dll /trans:Hello.csv /out:c oluştur: \ /cul:en-ABD**</span><span class="sxs-lookup"><span data-stu-id="db762-225">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hello.csv /out:c:\ /cul:en-US**</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="db762-226">Giriş dosyası, Hello.csv çalıştırılabilir LocBaml.exe ile aynı dizinde değilse, böylece her iki dosya aynı dizinde dosyalarından birini taşıyın.</span><span class="sxs-lookup"><span data-stu-id="db762-226">If the input file, Hello.csv, is not in the same directory as the executable, LocBaml.exe, move one of the files so that both files are in the same directory.</span></span>  
  
2.  <span data-ttu-id="db762-227">Eski HelloApp.resources.dll dosyasını C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll dizininde, yeni oluşturulan HelloApp.resources.dll dosyası ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="db762-227">Replace the old HelloApp.resources.dll file in the C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll directory with your newly created HelloApp.resources.dll file.</span></span>  
  
3.  <span data-ttu-id="db762-228">"Hello World" ve "Goodbye World" şimdi uygulamanızda çevrilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="db762-228">"Hello World" and "Goodbye World" should now be translated in your application.</span></span>  
  
4.  <span data-ttu-id="db762-229">Farklı bir kültür çevirmek için çevireceğiniz dil kültürünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="db762-229">To translate to a different culture, use the culture of the language that you are translating to.</span></span> <span data-ttu-id="db762-230">Aşağıdaki örnek, Canadian'a Çevir gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="db762-230">The following example shows how to translate to French-Canadian:</span></span>  
  
     <span data-ttu-id="db762-231">**LocBaml.exe'yi / HelloApp.resources.dll /trans:Hellofr Oluştur-CA.csv /out:c: \ /cul:fr-CA**</span><span class="sxs-lookup"><span data-stu-id="db762-231">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c:\ /cul:fr-CA**</span></span>  
  
5.  <span data-ttu-id="db762-232">Ana uygulama derlemeyle aynı bütünleştirilmiş kodda yeni bir uydu derleme barındırmak için yeni bir kültüre özgü klasör oluşturun.</span><span class="sxs-lookup"><span data-stu-id="db762-232">In the same assembly as the main application assembly, create a new culture-specific folder to house the new satellite assembly.</span></span> <span data-ttu-id="db762-233">French-Canadian için klasör fr-CA olacaktır.</span><span class="sxs-lookup"><span data-stu-id="db762-233">For French-Canadian, the folder would be fr-CA.</span></span>  
  
6.  <span data-ttu-id="db762-234">Oluşturulan uydu derlemesini yeni klasöre kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="db762-234">Copy the generated satellite assembly to the new folder.</span></span>  
  
7.  <span data-ttu-id="db762-235">Yeni bir uydu derleme sınamak için uygulamanızın çalıştırılacağı kültür değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="db762-235">To test the new satellite assembly, you need to change the culture under which your application will run.</span></span> <span data-ttu-id="db762-236">Bunu iki yoldan biriyle yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="db762-236">You can do this in one of two ways:</span></span>  
  
    -   <span data-ttu-id="db762-237">İşletim sisteminizin bölgesel ayarları değiştirin (**Başlat** &#124; **Denetim Masası** &#124; **Bölge ve Dil Seçenekleri**).</span><span class="sxs-lookup"><span data-stu-id="db762-237">Change your operating system's regional settings (**Start** &#124; **Control Panel** &#124; **Regional and Language Options**).</span></span>  
  
    -   <span data-ttu-id="db762-238">Uygulamanızda App.xaml.cs için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="db762-238">In your application, add the following code to App.xaml.cs:</span></span>  
  
   [!code-xaml[LocBamlChangeCultureSnippets#LocBamlChangeCultureMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml#locbamlchangeculturemarkup)]
   [!code-csharp[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml.cs#locbamlchangeculturecodebehind)]
   [!code-vb[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/VisualBasic/Application.xaml.vb#locbamlchangeculturecodebehind)]  
  
<a name="Some_Tips_for_Using_LocBaml"></a>   
## <a name="some-tips-for-using-locbaml"></a><span data-ttu-id="db762-239">LocBaml kullanımına yönelik bazı ipuçları</span><span class="sxs-lookup"><span data-stu-id="db762-239">Some Tips for Using LocBaml</span></span>  
  
-   <span data-ttu-id="db762-240">Özel denetimleri tanımlayan tüm bağımlı derlemeleri LocBaml yerel dizine kopyaladığınız veya GAC içine yüklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="db762-240">All dependent assemblies that define custom controls must be copied into the local directory of LocBaml or installed into the GAC.</span></span> <span data-ttu-id="db762-241">Okuduğunda API yerelleştirme bağımlı derlemelere erişimi olması gerektiği için bu gereklidir [!INCLUDE[TLA#tla_baml](../../../../includes/tlasharptla-baml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="db762-241">This is necessary because the localization API must have access to the dependent assemblies when it reads the [!INCLUDE[TLA#tla_baml](../../../../includes/tlasharptla-baml-md.md)].</span></span>  
  
-   <span data-ttu-id="db762-242">Ana derleme kaydolduysanız sırayla yüklü olması için oluşturulan kaynak DLL de imzalanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="db762-242">If the main assembly is signed, the generated resource DLL must also be signed in order for it to be loaded.</span></span>  
  
-   <span data-ttu-id="db762-243">Yerelleştirilmiş kaynak sürümü DLL ana bütünleştirilmiş kod ile eşitlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="db762-243">The version of the localized resource DLL needs to be synchronized with the main assembly.</span></span>  
  
<a name="Whats_Next"></a>   
## <a name="whats-next"></a><span data-ttu-id="db762-244">Sırada ne var?</span><span class="sxs-lookup"><span data-stu-id="db762-244">What's Next</span></span>  
 <span data-ttu-id="db762-245">Şimdi LocBaml aracının nasıl kullanılacağını ilgili temel bilgilere sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="db762-245">You should now have a basic understanding of how to use the LocBaml tool.</span></span>  <span data-ttu-id="db762-246">Uıd'leri içeren bir dosyayı olun olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="db762-246">You should be able to make a file that contains Uids.</span></span> <span data-ttu-id="db762-247">LocBaml aracını kullanarak, yerelleştirilebilir içerik ayıklamak için dosyayı ayrıştırabiliyor olmalıdır ve içeriği çevrilen sonra oluşturabilir olmalıdır bir. çevrilmiş içeriği birleştiren resources.dll dosyası.</span><span class="sxs-lookup"><span data-stu-id="db762-247">By using the LocBaml tool, you should be able to parse a file to extract the localizable content, and after the content is translated, you should be able to generate a .resources.dll file that merges the translated content.</span></span> <span data-ttu-id="db762-248">Bu konu, olası her ayrıntıyı içermez, ancak şu anda uygulamalarınızı yerelleştirme için LocBaml kullanmak için gerekli bilgiye sahipsiniz.</span><span class="sxs-lookup"><span data-stu-id="db762-248">This topic does not include every possible detail, but you now have the knowledge necessary to use LocBaml for localizing your applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db762-249">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="db762-249">See Also</span></span>  
 [<span data-ttu-id="db762-250">WPF için genelleştirme</span><span class="sxs-lookup"><span data-stu-id="db762-250">Globalization for WPF</span></span>](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md)  
 [<span data-ttu-id="db762-251">Otomatik Düzen Kullanım genel bakış</span><span class="sxs-lookup"><span data-stu-id="db762-251">Use Automatic Layout Overview</span></span>](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)
