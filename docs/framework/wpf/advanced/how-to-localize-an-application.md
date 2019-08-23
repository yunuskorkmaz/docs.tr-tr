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
ms.openlocfilehash: b3ad3d0c3223d5baf937ca22fd48d46a80979aac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913677"
---
# <a name="how-to-localize-an-application"></a><span data-ttu-id="ac222-102">Nasıl yapılır: Bir Uygulamayı Yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="ac222-102">How to: Localize an Application</span></span>
<span data-ttu-id="ac222-103">Bu öğreticide, LocBaml aracı kullanılarak yerelleştirilmiş bir uygulamanın nasıl oluşturulacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ac222-103">This tutorial explains how to create a localized application by using the LocBaml tool.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ac222-104">LocBaml aracı üretime yönelik olarak hazırlanmayan bir uygulama değildir.</span><span class="sxs-lookup"><span data-stu-id="ac222-104">The LocBaml tool is not a production-ready application.</span></span> <span data-ttu-id="ac222-105">Bu, yerelleştirme API 'Lerinden bazılarını kullanan bir örnek olarak sunulur ve yerelleştirme aracını nasıl yazacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="ac222-105">It is presented as a sample that uses some of the localization APIs and illustrates how you might write a localization tool.</span></span>  
  
<a name="Introduction"></a>   
## <a name="overview"></a><span data-ttu-id="ac222-106">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ac222-106">Overview</span></span>  
 <span data-ttu-id="ac222-107">Bu tartışma, bir uygulamayı yerelleştirme konusunda adım adım bir yaklaşım sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac222-107">This discussion gives you a step-by-step approach to localizing an application.</span></span> <span data-ttu-id="ac222-108">İlk olarak, çevrilecek metnin ayıklanabilmesi için uygulamanızı hazırlayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="ac222-108">First, you will prepare your application so that the text that will be translated can be extracted.</span></span> <span data-ttu-id="ac222-109">Metin çevrildikten sonra, çevrilmiş metni orijinal uygulamanın yeni bir kopyasına birleştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac222-109">After the text is translated, you will merge the translated text into a new copy of the original application.</span></span>  
  
<a name="Requirements"></a>   
## <a name="requirements"></a><span data-ttu-id="ac222-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ac222-110">Requirements</span></span>  
 <span data-ttu-id="ac222-111">Bu tartışma sırasında, komut satırından çalışan bir derleyici olan Microsoft Build Engine (MSBuild) kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="ac222-111">Over the course of this discussion, you will use Microsoft build engine (MSBuild), which is a compiler that runs from the command line.</span></span>  
  
 <span data-ttu-id="ac222-112">Ayrıca, bir proje dosyası kullanmanız istenir.</span><span class="sxs-lookup"><span data-stu-id="ac222-112">Also, you will be instructed to use a project file.</span></span> <span data-ttu-id="ac222-113">MSBuild ve proje dosyalarını kullanma hakkında yönergeler için bkz. [derleme ve dağıtma](../app-development/building-and-deploying-wpf-applications.md).</span><span class="sxs-lookup"><span data-stu-id="ac222-113">For instructions on how to use MSBuild and project files, see [Build and Deploy](../app-development/building-and-deploying-wpf-applications.md).</span></span>  
  
 <span data-ttu-id="ac222-114">Bu tartışmadaki tüm örnekler kültür olarak en-US (Ingilizce-US) kullanır.</span><span class="sxs-lookup"><span data-stu-id="ac222-114">All the examples in this discussion use en-US (English-US) as the culture.</span></span> <span data-ttu-id="ac222-115">Bu, farklı bir dil yüklemeden örneklerin adımlarında çalışabilmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac222-115">This enables you to work through the steps of the examples without installing a different language.</span></span>  
  
<a name="create_sample_app"></a>   
## <a name="create-a-sample-application"></a><span data-ttu-id="ac222-116">Örnek uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="ac222-116">Create a Sample Application</span></span>  
 <span data-ttu-id="ac222-117">Bu adımda, uygulamanızı yerelleştirme için hazırlayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="ac222-117">In this step, you will prepare your application for localization.</span></span> <span data-ttu-id="ac222-118">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Örneklerde, bu tartışmadaki kod örnekleri için kullanılacak bir HelloApp örneği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="ac222-118">In the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] samples, a HelloApp sample is supplied that will be used for the code examples in this discussion.</span></span> <span data-ttu-id="ac222-119">Bu örneği kullanmak isterseniz, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] [LocBaml araç örneğinden](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml)dosyaları indirin.</span><span class="sxs-lookup"><span data-stu-id="ac222-119">If you would like to use this sample, download the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] files from the [LocBaml Tool Sample](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).</span></span>  
  
1. <span data-ttu-id="ac222-120">Uygulamanızı yerelleştirmeye başlamak istediğiniz noktaya geliştirin.</span><span class="sxs-lookup"><span data-stu-id="ac222-120">Develop your application to the point where you want to start localization.</span></span>  
  
2. <span data-ttu-id="ac222-121">MSBuild 'in, bağımsız dil kaynaklarını içermesi için bir ana derleme ve uydu derlemesi (. resources. dll uzantılı bir dosya) oluşturması için proje dosyasında geliştirme dilini belirtin.</span><span class="sxs-lookup"><span data-stu-id="ac222-121">Specify the development language in the project file so that MSBuild generates a main assembly and a satellite assembly (a file with the .resources.dll extension) to contain the neutral language resources.</span></span> <span data-ttu-id="ac222-122">HelloApp örneğindeki proje dosyası HelloApp. csproj ' dır.</span><span class="sxs-lookup"><span data-stu-id="ac222-122">The project file in the HelloApp sample is HelloApp.csproj.</span></span> <span data-ttu-id="ac222-123">Bu dosyada, aşağıdaki şekilde tanımlanan geliştirme dilini bulacaksınız:</span><span class="sxs-lookup"><span data-stu-id="ac222-123">In that file, you will find the development language identified as follows:</span></span>  
  
     `<UICulture>en-US</UICulture>`  
  
3. <span data-ttu-id="ac222-124">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Dosyalarınıza uid 'ler ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ac222-124">Add Uids to your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files.</span></span> <span data-ttu-id="ac222-125">Uid 'ler, dosyalardaki değişiklikleri izlemek ve çevrilmesi gereken öğeleri belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ac222-125">Uids are used to keep track of changes to files and to identify items that must be translated.</span></span> <span data-ttu-id="ac222-126">Dosyalarınıza uid eklemek için, proje dosyanızda **updateuid** komutunu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="ac222-126">To add Uids to your files, run **updateuid** on your project file:</span></span>  
  
     <span data-ttu-id="ac222-127">**MSBuild-t:updateuid HelloApp. csproj**</span><span class="sxs-lookup"><span data-stu-id="ac222-127">**msbuild -t:updateuid helloapp.csproj**</span></span>  
  
     <span data-ttu-id="ac222-128">Eksik veya yinelenen UID 'ler olmadığını doğrulamak için **checkuid**komutunu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="ac222-128">To verify that you have no missing or duplicate Uids, run **checkuid**:</span></span>  
  
     <span data-ttu-id="ac222-129">**MSBuild-t:checkuid HelloApp. csproj**</span><span class="sxs-lookup"><span data-stu-id="ac222-129">**msbuild -t:checkuid helloapp.csproj**</span></span>  
  
     <span data-ttu-id="ac222-130">**Updateuid**çalıştırıldıktan sonra dosyalarınız uid 'leri içermelidir.</span><span class="sxs-lookup"><span data-stu-id="ac222-130">After running **updateuid**, your files should contain Uids.</span></span> <span data-ttu-id="ac222-131">Örneğin, HelloApp 'nin Pane1. xaml dosyasında aşağıdakileri bulmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="ac222-131">For example, in the Pane1.xaml file of HelloApp, you should find the following:</span></span>  
  
     `<StackPanel x:Uid="StackPanel_1">`  
  
     `<TextBlock x:Uid="TextBlock_1">Hello World</TextBlock>`  
  
     `<TextBlock x:Uid="TextBlock_2">Goodbye World</TextBlock>`  
  
     `</StackPanel>`  
  
<a name="create_dll"></a>   
## <a name="create-the-neutral-language-resources-satellite-assembly"></a><span data-ttu-id="ac222-132">Nötr dil kaynakları uydu derlemesini oluşturma</span><span class="sxs-lookup"><span data-stu-id="ac222-132">Create the Neutral Language Resources Satellite Assembly</span></span>  
 <span data-ttu-id="ac222-133">Uygulama, dilden bağımsız bir dil kaynakları uydu derlemesi oluşturmak üzere yapılandırıldıktan sonra, uygulamayı derleyin.</span><span class="sxs-lookup"><span data-stu-id="ac222-133">After the application is configured to generate a neutral language resources satellite assembly, you build the application.</span></span> <span data-ttu-id="ac222-134">Bu, ana uygulama derlemesini ve yerelleştirme için LocBaml 'in gerektirdiği Nötr dil kaynakları uydu derlemesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ac222-134">This generates the main application assembly, as well as the neutral language resources satellite assembly that is required by LocBaml for localization.</span></span> <span data-ttu-id="ac222-135">Uygulamayı derlemek için:</span><span class="sxs-lookup"><span data-stu-id="ac222-135">To build the application:</span></span>  
  
1. <span data-ttu-id="ac222-136">Dinamik bağlantı kitaplığı (DLL) oluşturmak için HelloApp 'yi derleyin:</span><span class="sxs-lookup"><span data-stu-id="ac222-136">Compile HelloApp to create a dynamic-link library (DLL):</span></span>  
  
     <span data-ttu-id="ac222-137">**MSBuild HelloApp. csproj**</span><span class="sxs-lookup"><span data-stu-id="ac222-137">**msbuild helloapp.csproj**</span></span>  
  
2. <span data-ttu-id="ac222-138">Yeni oluşturulan ana uygulama derlemesi HelloApp. exe, şu klasörde oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="ac222-138">The newly created main application assembly, HelloApp.exe, is created in the following folder:</span></span>  
  
     `C:\HelloApp\Bin\Debug\`  
  
3. <span data-ttu-id="ac222-139">Yeni oluşturulan Nötr dil kaynakları uydu derlemesi HelloApp. resources. dll aşağıdaki klasörde oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="ac222-139">The newly created neutral language resources satellite assembly, HelloApp.resources.dll, is created in the following folder:</span></span>  
  
     `C:\HelloApp\Bin\Debug\en-US\`  
  
<a name="build_locbaml"></a>   
## <a name="build-the-locbaml-tool"></a><span data-ttu-id="ac222-140">LocBaml aracını oluşturma</span><span class="sxs-lookup"><span data-stu-id="ac222-140">Build the LocBaml Tool</span></span>  
  
1. <span data-ttu-id="ac222-141">LocBaml oluşturmak için gereken tüm dosyalar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] örneklerde bulunur.</span><span class="sxs-lookup"><span data-stu-id="ac222-141">All the files necessary to build LocBaml are located in the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] samples.</span></span> <span data-ttu-id="ac222-142">C# Dosyaları [LocBaml araç örneğinden](https://go.microsoft.com/fwlink/?LinkID=160016)indirin.</span><span class="sxs-lookup"><span data-stu-id="ac222-142">Download the C# files from the [LocBaml Tool Sample](https://go.microsoft.com/fwlink/?LinkID=160016).</span></span>  
  
2. <span data-ttu-id="ac222-143">Araç oluşturmak için komut satırından proje dosyasını (LocBaml. csproj) çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="ac222-143">From the command line, run the project file (locbaml.csproj) to build the tool:</span></span>  
  
     <span data-ttu-id="ac222-144">**MSBuild LocBaml. csproj**</span><span class="sxs-lookup"><span data-stu-id="ac222-144">**msbuild locbaml.csproj**</span></span>  
  
3. <span data-ttu-id="ac222-145">Yeni oluşturulan yürütülebilir dosyayı (LocBaml. exe) bulmak için Bin\Release dizinine gidin.</span><span class="sxs-lookup"><span data-stu-id="ac222-145">Go to the Bin\Release directory to find the newly created executable file (locbaml.exe).</span></span> <span data-ttu-id="ac222-146">Örnek: C: \LocBaml\Bin\Release\locbaml.exe.</span><span class="sxs-lookup"><span data-stu-id="ac222-146">Example:C:\LocBaml\Bin\Release\locbaml.exe.</span></span>  
  
4. <span data-ttu-id="ac222-147">LocBaml 'i çalıştırdığınızda belirtebileceğiniz seçenekler aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="ac222-147">The options that you can specify when you run LocBaml are as follows:</span></span>  
  
    - <span data-ttu-id="ac222-148">**Parse** veya **-p:** Bir. csv veya. txt dosyası oluşturmak için BAML, kaynaklar veya DLL dosyalarını ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="ac222-148">**parse** or **-p:** Parses Baml, resources, or DLL files to generate a .csv or .txt file.</span></span>  
  
    - <span data-ttu-id="ac222-149">**Oluştur** veya **-g:** Çevrilmiş bir dosya kullanarak yerelleştirilmiş bir ikili dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ac222-149">**generate** or **-g:** Generates a localized binary file by using a translated file.</span></span>  
  
    - <span data-ttu-id="ac222-150">**Out** veya **-o** {*FileDirectory*] **:** Çıkış dosyası adı.</span><span class="sxs-lookup"><span data-stu-id="ac222-150">**out** or **-o** {*filedirectory*] **:** Output file name.</span></span>  
  
    - <span data-ttu-id="ac222-151">**kültür** veya **-Cul** {*kültür*] **:** Çıkış derlemelerinin yerel ayarı.</span><span class="sxs-lookup"><span data-stu-id="ac222-151">**culture** or **-cul** {*culture*] **:** Locale of output assemblies.</span></span>  
  
    - <span data-ttu-id="ac222-152">**çeviri** veya **-Trans** {*Translation. csv*] **:** Çevrilmiş veya yerelleştirilmiş dosya.</span><span class="sxs-lookup"><span data-stu-id="ac222-152">**translation** or **-trans** {*translation.csv*] **:** Translated or localized file.</span></span>  
  
    - <span data-ttu-id="ac222-153">**asmpath** veya **-asmpath:** {*FileDirectory*] **:** Kodunuz özel denetimler içeriyorsa, özel denetim derlemesine asmpath sağlamanız gerekir. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac222-153">**asmpath** or **-asmpath:** {*filedirectory*] **:** If your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] code contains custom controls, you must supply the **asmpath** to the custom control assembly.</span></span>  
  
    - <span data-ttu-id="ac222-154">**nologo** Logo veya telif hakkı bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ac222-154">**nologo:** Displays no logo or copyright information.</span></span>  
  
    - <span data-ttu-id="ac222-155">**seçeneini** Ayrıntılı mod bilgilerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ac222-155">**verbose:** Displays verbose mode information.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="ac222-156">Aracı çalıştırırken seçenekler listesine ihtiyacınız varsa **LocBaml. exe** YAZıN ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="ac222-156">If you need a list of the options when you are running the tool, type     **LocBaml.exe** and press ENTER.</span></span>  
  
<a name="parse_dll"></a>   
## <a name="use-locbaml-to-parse-a-file"></a><span data-ttu-id="ac222-157">Bir dosyayı ayrıştırmak için LocBaml Kullanma</span><span class="sxs-lookup"><span data-stu-id="ac222-157">Use LocBaml to Parse a File</span></span>  
 <span data-ttu-id="ac222-158">LocBaml aracını oluşturduğumuzda, bu uygulamayı, Yerelleştirilecek metin içeriğini ayıklamak için HelloApp. resources. dll ' i ayrıştırmak için kullanmaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="ac222-158">Now that you have created the LocBaml tool, you are ready to use it to parse HelloApp.resources.dll to extract the text content that will be localized.</span></span>  
  
1. <span data-ttu-id="ac222-159">LocBaml. exe ' yi, ana uygulama derlemesinin oluşturulduğu uygulamanızın Bin\Debug klasörüne kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="ac222-159">Copy LocBaml.exe to your application's bin\debug folder, where the main application assembly was created.</span></span>  
  
2. <span data-ttu-id="ac222-160">Uydu derleme dosyasını ayrıştırmak ve çıktıyı bir. csv dosyası olarak depolamak için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="ac222-160">To parse the satellite assembly file and store the output as a .csv file, use the following command:</span></span>  
  
     <span data-ttu-id="ac222-161">**LocBaml. exe/Parse HelloApp. resources. dll/out: Merhaba. csv**</span><span class="sxs-lookup"><span data-stu-id="ac222-161">**LocBaml.exe /parse HelloApp.resources.dll /out:Hello.csv**</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="ac222-162">HelloApp. resources. dll giriş dosyası LocBaml. exe ile aynı dizinde değilse, her iki dosyanın de aynı dizinde olması için dosyalardan birini taşıyın.</span><span class="sxs-lookup"><span data-stu-id="ac222-162">If the input file, HelloApp.resources.dll, is not in the same directory as LocBaml.exe move one of the files so that both files are in the same directory.</span></span>  
  
3. <span data-ttu-id="ac222-163">Dosyaları ayrıştırmak için LocBaml çalıştırdığınızda, çıktı virgüller (. csv dosyaları) veya sekmeler (. txt dosyaları) ile ayrılmış yedi alandan oluşur.</span><span class="sxs-lookup"><span data-stu-id="ac222-163">When you run LocBaml to parse files, the output consists of seven fields delimited by commas (.csv files) or tabs (.txt files).</span></span> <span data-ttu-id="ac222-164">Aşağıda, HelloApp. resources. dll için ayrıştırılmış. csv dosyası gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ac222-164">The following shows the parsed .csv file for the HelloApp.resources.dll:</span></span>

   | |
   |-|
   |<span data-ttu-id="ac222-165">HelloApp. g. en-US. resources: Window1. BAML, Stack1: System. Windows. Controls. StackPanel. $Content, Ignore, FALSE, FALSE,, #Text1; #Text2;</span><span class="sxs-lookup"><span data-stu-id="ac222-165">HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignore,FALSE, FALSE,,#Text1;#Text2;</span></span>|
   |<span data-ttu-id="ac222-166">HelloApp. g. en-US. resources: Window1. BAML, Metin1: System. Windows. Controls. TextBlock. $Content, None, TRUE, TRUE,, Merhaba Dünya</span><span class="sxs-lookup"><span data-stu-id="ac222-166">HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World</span></span>|
   |<span data-ttu-id="ac222-167">HelloApp. g. en-US. resources: Window1. BAML, Metin2: System. Windows. Controls. TextBlock. $Content, None, TRUE, TRUE,, güle dünya</span><span class="sxs-lookup"><span data-stu-id="ac222-167">HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World</span></span>|

   <span data-ttu-id="ac222-168">Yedi alan şunlardır:</span><span class="sxs-lookup"><span data-stu-id="ac222-168">The seven fields are:</span></span>  
  
   1. <span data-ttu-id="ac222-169">**BAML adı**.</span><span class="sxs-lookup"><span data-stu-id="ac222-169">**BAML Name**.</span></span> <span data-ttu-id="ac222-170">Kaynak dil uydu derlemesine göre BAML kaynağının adı.</span><span class="sxs-lookup"><span data-stu-id="ac222-170">The name of the BAML resource with respect to the source language satellite assembly.</span></span>  
  
   2. <span data-ttu-id="ac222-171">**Kaynak anahtarı**.</span><span class="sxs-lookup"><span data-stu-id="ac222-171">**Resource Key**.</span></span> <span data-ttu-id="ac222-172">Yerelleştirilmiş kaynak tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="ac222-172">The localized resource identifier.</span></span>  
  
   3. <span data-ttu-id="ac222-173">**Kategori**.</span><span class="sxs-lookup"><span data-stu-id="ac222-173">**Category**.</span></span> <span data-ttu-id="ac222-174">Değer türü.</span><span class="sxs-lookup"><span data-stu-id="ac222-174">The value type.</span></span> <span data-ttu-id="ac222-175">Bkz. [Yerelleştirme öznitelikleri ve açıklamaları](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="ac222-175">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   4. <span data-ttu-id="ac222-176">**Okunabilirlik**.</span><span class="sxs-lookup"><span data-stu-id="ac222-176">**Readability**.</span></span> <span data-ttu-id="ac222-177">Değerin yerelleştirici tarafından okunup okunamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ac222-177">Whether the value can be read by a localizer.</span></span> <span data-ttu-id="ac222-178">Bkz. [Yerelleştirme öznitelikleri ve açıklamaları](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="ac222-178">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   5. <span data-ttu-id="ac222-179">**Modifibeceri**.</span><span class="sxs-lookup"><span data-stu-id="ac222-179">**Modifiability**.</span></span> <span data-ttu-id="ac222-180">Değerin bir yerelleştirici tarafından değiştirilip değiştirilemediği.</span><span class="sxs-lookup"><span data-stu-id="ac222-180">Whether the value can be modified by a localizer.</span></span> <span data-ttu-id="ac222-181">Bkz. [Yerelleştirme öznitelikleri ve açıklamaları](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="ac222-181">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   6. <span data-ttu-id="ac222-182">**Yorumlar**.</span><span class="sxs-lookup"><span data-stu-id="ac222-182">**Comments**.</span></span> <span data-ttu-id="ac222-183">Değerin nasıl yerelleştirileceğini belirlemede yardımcı olacak değerin ek açıklaması.</span><span class="sxs-lookup"><span data-stu-id="ac222-183">Additional description of the value to help determine how a value is localized.</span></span> <span data-ttu-id="ac222-184">Bkz. [Yerelleştirme öznitelikleri ve açıklamaları](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="ac222-184">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   7. <span data-ttu-id="ac222-185">**Değer**.</span><span class="sxs-lookup"><span data-stu-id="ac222-185">**Value**.</span></span> <span data-ttu-id="ac222-186">İstenen kültüre çevrilecek metin değeri.</span><span class="sxs-lookup"><span data-stu-id="ac222-186">The text value to translate to the desired culture.</span></span>  
  
   <span data-ttu-id="ac222-187">Aşağıdaki tabloda, bu alanların. csv dosyasının ayrılmış değerleriyle nasıl eşlenme gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ac222-187">The following table shows how these fields map to the delimited values of the .csv file:</span></span>  
  
   |<span data-ttu-id="ac222-188">BAML adı</span><span class="sxs-lookup"><span data-stu-id="ac222-188">BAML name</span></span>|<span data-ttu-id="ac222-189">Kaynak anahtarı</span><span class="sxs-lookup"><span data-stu-id="ac222-189">Resource key</span></span>|<span data-ttu-id="ac222-190">Kategori</span><span class="sxs-lookup"><span data-stu-id="ac222-190">Category</span></span>|<span data-ttu-id="ac222-191">Luğunu</span><span class="sxs-lookup"><span data-stu-id="ac222-191">Readability</span></span>|<span data-ttu-id="ac222-192">Modifibilme</span><span class="sxs-lookup"><span data-stu-id="ac222-192">Modifiability</span></span>|<span data-ttu-id="ac222-193">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ac222-193">Comments</span></span>|<span data-ttu-id="ac222-194">Değer</span><span class="sxs-lookup"><span data-stu-id="ac222-194">Value</span></span>|  
   |---------------|------------------|--------------|-----------------|-------------------|--------------|-----------|
   |<span data-ttu-id="ac222-195">HelloApp. g. en-US. resources: Window1. BAML</span><span class="sxs-lookup"><span data-stu-id="ac222-195">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="ac222-196">Stack1: System. Windows. Controls. StackPanel. $Content</span><span class="sxs-lookup"><span data-stu-id="ac222-196">Stack1:System.Windows.Controls.StackPanel.$Content</span></span>|<span data-ttu-id="ac222-197">Yoksayma</span><span class="sxs-lookup"><span data-stu-id="ac222-197">Ignore</span></span>|<span data-ttu-id="ac222-198">YANLÝÞ</span><span class="sxs-lookup"><span data-stu-id="ac222-198">FALSE</span></span>|<span data-ttu-id="ac222-199">YANLÝÞ</span><span class="sxs-lookup"><span data-stu-id="ac222-199">FALSE</span></span>||<span data-ttu-id="ac222-200">#Text1; #Text2</span><span class="sxs-lookup"><span data-stu-id="ac222-200">#Text1;#Text2</span></span>|
   |<span data-ttu-id="ac222-201">HelloApp. g. en-US. resources: Window1. BAML</span><span class="sxs-lookup"><span data-stu-id="ac222-201">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="ac222-202">Metin1: System. Windows. Controls. TextBlock. $Content</span><span class="sxs-lookup"><span data-stu-id="ac222-202">Text1:System.Windows.Controls.TextBlock.$Content</span></span>|<span data-ttu-id="ac222-203">Yok.</span><span class="sxs-lookup"><span data-stu-id="ac222-203">None</span></span>|<span data-ttu-id="ac222-204">TRUE</span><span class="sxs-lookup"><span data-stu-id="ac222-204">TRUE</span></span>|<span data-ttu-id="ac222-205">TRUE</span><span class="sxs-lookup"><span data-stu-id="ac222-205">TRUE</span></span>||<span data-ttu-id="ac222-206">Merhaba Dünya</span><span class="sxs-lookup"><span data-stu-id="ac222-206">Hello World</span></span>|
   |<span data-ttu-id="ac222-207">HelloApp. g. en-US. resources: Window1. BAML</span><span class="sxs-lookup"><span data-stu-id="ac222-207">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="ac222-208">Metin2: System. Windows. Controls. TextBlock. $Content</span><span class="sxs-lookup"><span data-stu-id="ac222-208">Text2:System.Windows.Controls.TextBlock.$Content</span></span>|<span data-ttu-id="ac222-209">Yok.</span><span class="sxs-lookup"><span data-stu-id="ac222-209">None</span></span>|<span data-ttu-id="ac222-210">TRUE</span><span class="sxs-lookup"><span data-stu-id="ac222-210">TRUE</span></span>|<span data-ttu-id="ac222-211">TRUE</span><span class="sxs-lookup"><span data-stu-id="ac222-211">TRUE</span></span>||<span data-ttu-id="ac222-212">Güle dünya</span><span class="sxs-lookup"><span data-stu-id="ac222-212">Goodbye World</span></span>|
  
   <span data-ttu-id="ac222-213">**Comments** alanı için tüm değerlerin değer içermediğini unutmayın; bir alanın değeri yoksa, boştur.</span><span class="sxs-lookup"><span data-stu-id="ac222-213">Notice that all the values for the **Comments** field contain no values; if a field doesn't have a value, it is empty.</span></span> <span data-ttu-id="ac222-214">Ayrıca, ilk satırdaki öğenin okunabilir ve değiştirilebilir olmadığından ve **Kategori** değeri olarak "Yoksay" değerine sahip olduğuna dikkat edin; hepsi değerin yerelleştirilemeyen olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ac222-214">Also notice that the item in the first row is neither readable nor modifiable, and has "Ignore" as its **Category** value, all of which indicates that the value is not localizable.</span></span>  
  
4. <span data-ttu-id="ac222-215">Özellikle büyük dosyalarda, ayrıştırılmış dosyalardaki yerelleştirilebilir öğelerin bulunmasını kolaylaştırmak için öğeleri **kategoriye**, **okunabilirlik**ve **modifime**göre sıralayabilir veya filtreleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac222-215">To facilitate discovery of localizable items in parsed files, particularly in large files, you can sort or filter the items by **Category**, **Readability**, and **Modifiability**.</span></span> <span data-ttu-id="ac222-216">Örneğin, okunamaz ve değiştirilemeyen değerleri filtreleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac222-216">For example, you can filter out unreadable and unmodifiable values.</span></span>  
  
<a name="translate_loc_content"></a>   
## <a name="translate-the-localizable-content"></a><span data-ttu-id="ac222-217">Yerelleştirilebilir Içeriği çevir</span><span class="sxs-lookup"><span data-stu-id="ac222-217">Translate the Localizable Content</span></span>  
 <span data-ttu-id="ac222-218">Ayıklanan içeriği çevirmek için kullanabileceğiniz herhangi bir aracı kullanın.</span><span class="sxs-lookup"><span data-stu-id="ac222-218">Use any tool that you have available to translate the extracted content.</span></span> <span data-ttu-id="ac222-219">Bunu yapmanın iyi bir yolu, kaynakları bir. csv dosyasına yazmak ve bunları içinde [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)]görüntülemeniz, son sütunda (değer) çeviri değişiklikleri yapmak.</span><span class="sxs-lookup"><span data-stu-id="ac222-219">A good way to do this is to write the resources to a .csv file and view them in [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)], making translation changes to the last column (value).</span></span>  
  
<a name="merge_translations"></a>   
## <a name="use-locbaml-to-generate-a-new-resourcesdll-file"></a><span data-ttu-id="ac222-220">Yeni bir. resources. dll dosyası oluşturmak için LocBaml kullanın</span><span class="sxs-lookup"><span data-stu-id="ac222-220">Use LocBaml to Generate a New .resources.dll File</span></span>  
 <span data-ttu-id="ac222-221">LocBaml ile HelloApp. resources. dll ayrıştırılmasından tanımlanan içerik çevrilmiş ve özgün uygulamayla yeniden birleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="ac222-221">The content that was identified by parsing HelloApp.resources.dll with LocBaml has been translated and must be merged back into the original application.</span></span> <span data-ttu-id="ac222-222">Yeni bir. resources. dll dosyası oluşturmak için **Generate** veya **-g** seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ac222-222">Use the **generate** or **-g** option to generate a new .resources.dll file.</span></span>  
  
1. <span data-ttu-id="ac222-223">Yeni bir HelloApp. resources. dll dosyası oluşturmak için aşağıdaki sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ac222-223">Use the following syntax to generate a new HelloApp.resources.dll file.</span></span> <span data-ttu-id="ac222-224">Kültürü en-US (/CUL: en-US) olarak işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="ac222-224">Mark the culture as en-US (/cul:en-US).</span></span>  
  
     <span data-ttu-id="ac222-225">**LocBaml. exe/Generate HelloApp. resources. dll/Trans: Hello. csv/Out: c:\/Cul: en-US**</span><span class="sxs-lookup"><span data-stu-id="ac222-225">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hello.csv /out:c:\ /cul:en-US**</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="ac222-226">Hello. csv giriş dosyası yürütülebilir dosya, LocBaml. exe ile aynı dizinde değilse, her iki dosyanın de aynı dizinde olması için dosyalardan birini taşıyın.</span><span class="sxs-lookup"><span data-stu-id="ac222-226">If the input file, Hello.csv, is not in the same directory as the executable, LocBaml.exe, move one of the files so that both files are in the same directory.</span></span>  
  
2. <span data-ttu-id="ac222-227">C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll dizinindeki eski HelloApp. resources. dll dosyasını yeni oluşturduğunuz HelloApp. resources. dll dosyası ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="ac222-227">Replace the old HelloApp.resources.dll file in the C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll directory with your newly created HelloApp.resources.dll file.</span></span>  
  
3. <span data-ttu-id="ac222-228">"Merhaba Dünya" ve "gücüde Dünya" Artık uygulamanıza çevrilmelidir.</span><span class="sxs-lookup"><span data-stu-id="ac222-228">"Hello World" and "Goodbye World" should now be translated in your application.</span></span>  
  
4. <span data-ttu-id="ac222-229">Farklı bir kültüre çevirmek için, çevirinizin bulunduğu dilin kültürünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="ac222-229">To translate to a different culture, use the culture of the language that you are translating to.</span></span> <span data-ttu-id="ac222-230">Aşağıdaki örnek, Fransızca-Kanada 'ya nasıl çevrileceğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="ac222-230">The following example shows how to translate to French-Canadian:</span></span>  
  
     <span data-ttu-id="ac222-231">**LocBaml. exe/Generate HelloApp. resources. dll/Trans: Hellofr-CA. csv/Out: c:\/Cul: fr-CA**</span><span class="sxs-lookup"><span data-stu-id="ac222-231">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c:\ /cul:fr-CA**</span></span>  
  
5. <span data-ttu-id="ac222-232">Ana uygulama derlemesiyle aynı derlemede, yeni uydu derlemesini barındırmak için kültüre özgü yeni bir klasör oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ac222-232">In the same assembly as the main application assembly, create a new culture-specific folder to house the new satellite assembly.</span></span> <span data-ttu-id="ac222-233">Fransızca-Kanada için klasör fr-CA olur.</span><span class="sxs-lookup"><span data-stu-id="ac222-233">For French-Canadian, the folder would be fr-CA.</span></span>  
  
6. <span data-ttu-id="ac222-234">Oluşturulan uydu derlemesini yeni klasöre kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="ac222-234">Copy the generated satellite assembly to the new folder.</span></span>  
  
7. <span data-ttu-id="ac222-235">Yeni uydu derlemesini test etmek için uygulamanızın çalıştırılacağı kültürü değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ac222-235">To test the new satellite assembly, you need to change the culture under which your application will run.</span></span> <span data-ttu-id="ac222-236">Bunu iki yoldan biriyle yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ac222-236">You can do this in one of two ways:</span></span>  
  
    - <span data-ttu-id="ac222-237">İşletim sisteminizin bölgesel ayarlarını değiştirin ( **Denetim Masası** &#124; **bölge ve dil seçeneklerini** **Başlat** &#124; ).</span><span class="sxs-lookup"><span data-stu-id="ac222-237">Change your operating system's regional settings (**Start** &#124; **Control Panel** &#124; **Regional and Language Options**).</span></span>  
  
    - <span data-ttu-id="ac222-238">Uygulamanızda, App.xaml.cs 'e aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="ac222-238">In your application, add the following code to App.xaml.cs:</span></span>  
  
   [!code-xaml[LocBamlChangeCultureSnippets#LocBamlChangeCultureMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml#locbamlchangeculturemarkup)]
   [!code-csharp[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml.cs#locbamlchangeculturecodebehind)]
   [!code-vb[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/VisualBasic/Application.xaml.vb#locbamlchangeculturecodebehind)]  
  
<a name="Some_Tips_for_Using_LocBaml"></a>   
## <a name="some-tips-for-using-locbaml"></a><span data-ttu-id="ac222-239">LocBaml kullanımı için bazı Ipuçları</span><span class="sxs-lookup"><span data-stu-id="ac222-239">Some Tips for Using LocBaml</span></span>  
  
- <span data-ttu-id="ac222-240">Özel denetimleri tanımlayan tüm bağımlı derlemelerin LocBaml yerel dizinine kopyalanması veya GAC 'ye yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="ac222-240">All dependent assemblies that define custom controls must be copied into the local directory of LocBaml or installed into the GAC.</span></span> <span data-ttu-id="ac222-241">Bu gereklidir çünkü yerelleştirme API 'sinin, ikili XAML (BAML) okurken bağımlı derlemelere erişimi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ac222-241">This is necessary because the localization API must have access to the dependent assemblies when it reads the binary XAML (BAML).</span></span>  
  
- <span data-ttu-id="ac222-242">Ana derleme imzalanmışsa, oluşturulan kaynak DLL 'nin yüklenmesi için de imzalı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ac222-242">If the main assembly is signed, the generated resource DLL must also be signed in order for it to be loaded.</span></span>  
  
- <span data-ttu-id="ac222-243">Yerelleştirilmiş kaynak DLL sürümünün ana derlemeyle eşitlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="ac222-243">The version of the localized resource DLL needs to be synchronized with the main assembly.</span></span>  
  
<a name="Whats_Next"></a>   
## <a name="whats-next"></a><span data-ttu-id="ac222-244">Sıradaki</span><span class="sxs-lookup"><span data-stu-id="ac222-244">What's Next</span></span>  
 <span data-ttu-id="ac222-245">Artık LocBaml aracının nasıl kullanılacağına ilişkin temel bilgiye sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ac222-245">You should now have a basic understanding of how to use the LocBaml tool.</span></span>  <span data-ttu-id="ac222-246">Uid 'leri içeren bir dosya yapabilmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="ac222-246">You should be able to make a file that contains Uids.</span></span> <span data-ttu-id="ac222-247">LocBaml aracını kullanarak, yerelleştirilebilir içeriği ayıklamak için bir dosyayı ayrıştırabilmeniz ve içerik çevrildikten sonra, çevrilmiş içeriği birleştiren bir. resources. dll dosyası oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ac222-247">By using the LocBaml tool, you should be able to parse a file to extract the localizable content, and after the content is translated, you should be able to generate a .resources.dll file that merges the translated content.</span></span> <span data-ttu-id="ac222-248">Bu konu, mümkün olan her ayrıntıyı içermez, ancak artık uygulamalarınızı Yerelleştirmede LocBaml 'i kullanmak için gereken bilgiye sahipsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac222-248">This topic does not include every possible detail, but you now have the knowledge necessary to use LocBaml for localizing your applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac222-249">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac222-249">See also</span></span>

- [<span data-ttu-id="ac222-250">WPF için Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="ac222-250">Globalization for WPF</span></span>](globalization-for-wpf.md)
- [<span data-ttu-id="ac222-251">Otomatik Düzen Kullanımına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ac222-251">Use Automatic Layout Overview</span></span>](use-automatic-layout-overview.md)
