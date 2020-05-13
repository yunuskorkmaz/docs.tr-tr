---
title: Uygulama yerelleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- localization [WPF], applications
- LocBaml tool [WPF]
- applications [WPF], localizing
ms.assetid: 5001227e-9326-48a4-9dcd-ba1b89ee6653
ms.openlocfilehash: dc7d8f4f56b26fffbd883e1e1d6e420026e1f94f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209688"
---
# <a name="how-to-localize-an-application"></a><span data-ttu-id="0960f-102">Nasıl yapılır: bir uygulamayı yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="0960f-102">How to: Localize an application</span></span>

<span data-ttu-id="0960f-103">Bu öğreticide, LocBaml aracı kullanılarak yerelleştirilmiş bir uygulamanın nasıl oluşturulacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0960f-103">This tutorial explains how to create a localized application by using the LocBaml tool.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0960f-104">LocBaml aracı üretime yönelik olarak hazırlanmayan bir uygulama değildir.</span><span class="sxs-lookup"><span data-stu-id="0960f-104">The LocBaml tool is not a production-ready application.</span></span> <span data-ttu-id="0960f-105">Bu, yerelleştirme API 'Lerinden bazılarını kullanan bir örnek olarak sunulur ve yerelleştirme aracını nasıl yazacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="0960f-105">It is presented as a sample that uses some of the localization APIs and illustrates how you might write a localization tool.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="0960f-106">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0960f-106">Overview</span></span>

<span data-ttu-id="0960f-107">Bu makale, bir uygulamayı yerelleştirme konusunda adım adım bir yaklaşım sağlar.</span><span class="sxs-lookup"><span data-stu-id="0960f-107">This article gives you a step-by-step approach to localizing an application.</span></span> <span data-ttu-id="0960f-108">İlk olarak, çevrilecek metnin ayıklanabilmesi için uygulamanızı hazırlarsınız.</span><span class="sxs-lookup"><span data-stu-id="0960f-108">First, you prepare your application so that the text that will be translated can be extracted.</span></span> <span data-ttu-id="0960f-109">Metin çevrildikten sonra, çevrilmiş metni orijinal uygulamanın yeni bir kopyasına birleştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0960f-109">After the text is translated, you merge the translated text into a new copy of the original application.</span></span>
  
## <a name="create-a-sample-application"></a><span data-ttu-id="0960f-110">Örnek uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="0960f-110">Create a sample application</span></span>

<span data-ttu-id="0960f-111">Bu adımda, uygulamanızı yerelleştirme için hazırlarsınız.</span><span class="sxs-lookup"><span data-stu-id="0960f-111">In this step, you prepare your app for localization.</span></span> <span data-ttu-id="0960f-112">Windows Presentation Foundation (WPF) örneklerinde, bu tartışmadaki kod örnekleri için kullanılacak bir HelloApp örneği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="0960f-112">In the Windows Presentation Foundation (WPF) samples, a HelloApp sample is supplied that will be used for the code examples in this discussion.</span></span> <span data-ttu-id="0960f-113">Bu örneği kullanmak isterseniz, [LocBaml araç örneğinden](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml)EXTENSIBLE APPLICATION MARKUP Language (XAML) dosyalarını indirin.</span><span class="sxs-lookup"><span data-stu-id="0960f-113">If you would like to use this sample, download the Extensible Application Markup Language (XAML) files from the [LocBaml Tool Sample](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).</span></span>  
  
1. <span data-ttu-id="0960f-114">Uygulamanızı yerelleştirmeye başlamak istediğiniz noktaya geliştirin.</span><span class="sxs-lookup"><span data-stu-id="0960f-114">Develop your application to the point where you want to start localization.</span></span>  
  
2. <span data-ttu-id="0960f-115">MSBuild 'in, bağımsız dil kaynaklarını içermesi için bir ana derleme ve uydu derlemesi (. resources. dll uzantılı bir dosya) oluşturması için proje dosyasında geliştirme dilini belirtin.</span><span class="sxs-lookup"><span data-stu-id="0960f-115">Specify the development language in the project file so that MSBuild generates a main assembly and a satellite assembly (a file with the .resources.dll extension) to contain the neutral language resources.</span></span> <span data-ttu-id="0960f-116">HelloApp örneğindeki proje dosyası HelloApp. csproj ' dır.</span><span class="sxs-lookup"><span data-stu-id="0960f-116">The project file in the HelloApp sample is HelloApp.csproj.</span></span> <span data-ttu-id="0960f-117">Bu dosyada, aşağıdaki şekilde tanımlanan geliştirme dilini bulacaksınız:</span><span class="sxs-lookup"><span data-stu-id="0960f-117">In that file, you will find the development language identified as follows:</span></span>  
  
   `<UICulture>en-US</UICulture>`  
  
3. <span data-ttu-id="0960f-118">XAML dosyalarınıza uid 'ler ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0960f-118">Add Uids to your XAML files.</span></span> <span data-ttu-id="0960f-119">Uid 'ler, dosyalardaki değişiklikleri izlemek ve çevrilmesi gereken öğeleri belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0960f-119">Uids are used to keep track of changes to files and to identify items that must be translated.</span></span> <span data-ttu-id="0960f-120">Dosyalarınıza uid eklemek için, `updateuid` proje dosyanızda çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="0960f-120">To add Uids to your files, run `updateuid` on your project file:</span></span>  

   `msbuild -t:updateuid helloapp.csproj`

   <span data-ttu-id="0960f-121">Eksik veya yinelenen UID 'ler olmadığını doğrulamak için şunu çalıştırın `checkuid` :</span><span class="sxs-lookup"><span data-stu-id="0960f-121">To verify that you have no missing or duplicate Uids, run `checkuid`:</span></span>  

   `msbuild -t:checkuid helloapp.csproj`

   <span data-ttu-id="0960f-122">Çalıştırıldıktan sonra `updateuid` dosyalarınız uid 'leri içermelidir.</span><span class="sxs-lookup"><span data-stu-id="0960f-122">After running `updateuid`, your files should contain Uids.</span></span> <span data-ttu-id="0960f-123">Örneğin, HelloApp 'nin *Pane1. xaml* dosyasında aşağıdakileri bulmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="0960f-123">For example, in the *Pane1.xaml* file of HelloApp, you should find the following:</span></span>  

   ```xaml
   <StackPanel x:Uid="StackPanel_1">
     <TextBlock x:Uid="TextBlock_1">Hello World</TextBlock>
     <TextBlock x:Uid="TextBlock_2">Goodbye World</TextBlock>
   </StackPanel>
   ```

## <a name="create-the-neutral-language-resources-satellite-assembly"></a><span data-ttu-id="0960f-124">Nötr dil kaynakları uydu derlemesini oluşturma</span><span class="sxs-lookup"><span data-stu-id="0960f-124">Create the neutral-language resources satellite assembly</span></span>

<span data-ttu-id="0960f-125">Uygulama, Nötr dil kaynakları uydu derlemesi oluşturmak üzere yapılandırıldıktan sonra, uygulamayı derleyin.</span><span class="sxs-lookup"><span data-stu-id="0960f-125">After the application is configured to generate a neutral-language resources satellite assembly, you build the application.</span></span> <span data-ttu-id="0960f-126">Bu, yerelleştirme için LocBaml 'in gerektirdiği bağımsız kaynak uydu derlemesini ve ana uygulama derlemesini de oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0960f-126">This generates the main application assembly as well as the neutral-language resources satellite assembly that's required by LocBaml for localization.</span></span>

<span data-ttu-id="0960f-127">Uygulamayı derlemek için:</span><span class="sxs-lookup"><span data-stu-id="0960f-127">To build the application:</span></span>  
  
1. <span data-ttu-id="0960f-128">Dinamik bağlantı kitaplığı (DLL) oluşturmak için HelloApp 'yi derleyin:</span><span class="sxs-lookup"><span data-stu-id="0960f-128">Compile HelloApp to create a dynamic-link library (DLL):</span></span>  
  
   `msbuild helloapp.csproj`
  
2. <span data-ttu-id="0960f-129">Yeni oluşturulan ana uygulama derlemesi HelloApp. exe, şu klasörde oluşturulur: *C:\helloapp\bin\debug*</span><span class="sxs-lookup"><span data-stu-id="0960f-129">The newly created main application assembly, HelloApp.exe, is created in the following folder: *C:\HelloApp\Bin\Debug*</span></span>
  
3. <span data-ttu-id="0960f-130">Yeni oluşturulan Nötr dil kaynakları uydu derlemesi HelloApp. resources. dll şu klasörde oluşturulur: *C:\HelloApp\Bin\Debug\en-US*</span><span class="sxs-lookup"><span data-stu-id="0960f-130">The newly created neutral-language resources satellite assembly, HelloApp.resources.dll, is created in the following folder: *C:\HelloApp\Bin\Debug\en-US*</span></span>
  
## <a name="build-the-locbaml-tool"></a><span data-ttu-id="0960f-131">LocBaml aracını oluşturma</span><span class="sxs-lookup"><span data-stu-id="0960f-131">Build the LocBaml tool</span></span>  
  
1. <span data-ttu-id="0960f-132">LocBaml oluşturmak için gereken tüm dosyalar WPF örneklerinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="0960f-132">All the files necessary to build LocBaml are located in the WPF samples.</span></span> <span data-ttu-id="0960f-133">[LocBaml araç örneğinden](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml)C# dosyalarını indirin.</span><span class="sxs-lookup"><span data-stu-id="0960f-133">Download the C# files from the [LocBaml Tool Sample](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).</span></span>  
  
2. <span data-ttu-id="0960f-134">Araç oluşturmak için komut satırından proje dosyasını (LocBaml. csproj) çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="0960f-134">From the command line, run the project file (locbaml.csproj) to build the tool:</span></span>  

   `msbuild locbaml.csproj`
  
3. <span data-ttu-id="0960f-135">Yeni oluşturulan yürütülebilir dosyayı (LocBaml. exe) bulmak için *Bin\release* dizinine gidin.</span><span class="sxs-lookup"><span data-stu-id="0960f-135">Go to the *Bin\Release* directory to find the newly created executable file (locbaml.exe).</span></span> <span data-ttu-id="0960f-136">Örnek: *C:\LocBaml\Bin\Release\locbaml.exe*</span><span class="sxs-lookup"><span data-stu-id="0960f-136">Example: *C:\LocBaml\Bin\Release\locbaml.exe*</span></span>
  
4. <span data-ttu-id="0960f-137">LocBaml 'i çalıştırdığınızda belirtebileceğiniz seçenekler aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="0960f-137">The options that you can specify when you run LocBaml are as follows.</span></span>

   | <span data-ttu-id="0960f-138">Seçenek</span><span class="sxs-lookup"><span data-stu-id="0960f-138">Option</span></span> | <span data-ttu-id="0960f-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0960f-139">Description</span></span>|
   | - | - |
   | <span data-ttu-id="0960f-140">`parse` veya `-p`</span><span class="sxs-lookup"><span data-stu-id="0960f-140">`parse` or `-p`</span></span> | <span data-ttu-id="0960f-141">Bir. csv veya. txt dosyası oluşturmak için BAML, kaynaklar veya DLL dosyalarını ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="0960f-141">Parses Baml, resources, or DLL files to generate a .csv or .txt file.</span></span> |
   | <span data-ttu-id="0960f-142">`generate` veya `-g`</span><span class="sxs-lookup"><span data-stu-id="0960f-142">`generate` or `-g`</span></span> | <span data-ttu-id="0960f-143">Çevrilmiş bir dosya kullanarak yerelleştirilmiş bir ikili dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0960f-143">Generates a localized binary file by using a translated file.</span></span> |
   | <span data-ttu-id="0960f-144">`out`veya `-o` {*FileDirectory*]</span><span class="sxs-lookup"><span data-stu-id="0960f-144">`out` or `-o` {*filedirectory*]</span></span> | <span data-ttu-id="0960f-145">Çıkış dosyası adı.</span><span class="sxs-lookup"><span data-stu-id="0960f-145">Output file name.</span></span> |
   | <span data-ttu-id="0960f-146">`culture`veya `-cul` {*Culture*]</span><span class="sxs-lookup"><span data-stu-id="0960f-146">`culture` or `-cul` {*culture*]</span></span> | <span data-ttu-id="0960f-147">Çıkış derlemelerinin yerel ayarı.</span><span class="sxs-lookup"><span data-stu-id="0960f-147">Locale of output assemblies.</span></span> |
   | <span data-ttu-id="0960f-148">`translation`veya `-trans` {*Translation. csv*]</span><span class="sxs-lookup"><span data-stu-id="0960f-148">`translation` or `-trans` {*translation.csv*]</span></span> | <span data-ttu-id="0960f-149">Çevrilmiş veya yerelleştirilmiş dosya.</span><span class="sxs-lookup"><span data-stu-id="0960f-149">Translated or localized file.</span></span> |
   | <span data-ttu-id="0960f-150">`asmpath`veya `-asmpath` {*FileDirectory*]</span><span class="sxs-lookup"><span data-stu-id="0960f-150">`asmpath` or `-asmpath` {*filedirectory*]</span></span> | <span data-ttu-id="0960f-151">XAML kodunuz özel denetimler içeriyorsa, öğesini `asmpath` özel denetim derlemesine sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0960f-151">If your XAML code contains custom controls, you must supply the `asmpath` to the custom control assembly.</span></span> |
   | `nologo` | <span data-ttu-id="0960f-152">Logo veya telif hakkı bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0960f-152">Displays no logo or copyright information.</span></span> |
   | `verbose` | <span data-ttu-id="0960f-153">Ayrıntılı mod bilgilerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0960f-153">Displays verbose mode information.</span></span> |
  
   > [!NOTE]
   > <span data-ttu-id="0960f-154">Aracı çalıştırırken seçeneklerin listesine ihtiyacınız varsa girin `LocBaml.exe` ve ardından **ENTER**tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="0960f-154">If you need a list of the options when you are running the tool, enter `LocBaml.exe` and then press **Enter**.</span></span>
  
## <a name="use-locbaml-to-parse-a-file"></a><span data-ttu-id="0960f-155">Bir dosyayı ayrıştırmak için LocBaml Kullanma</span><span class="sxs-lookup"><span data-stu-id="0960f-155">Use LocBaml to parse a file</span></span>

<span data-ttu-id="0960f-156">LocBaml aracını oluşturduğumuzda, bu uygulamayı, Yerelleştirilecek metin içeriğini ayıklamak için HelloApp. resources. dll ' i ayrıştırmak için kullanmaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="0960f-156">Now that you have created the LocBaml tool, you are ready to use it to parse HelloApp.resources.dll to extract the text content that will be localized.</span></span>  
  
1. <span data-ttu-id="0960f-157">LocBaml. exe ' yi, ana uygulama derlemesinin oluşturulduğu uygulamanızın Bin\Debug klasörüne kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="0960f-157">Copy LocBaml.exe to your application's bin\debug folder, where the main application assembly was created.</span></span>  
  
2. <span data-ttu-id="0960f-158">Uydu derleme dosyasını ayrıştırmak ve çıktıyı bir. csv dosyası olarak depolamak için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="0960f-158">To parse the satellite assembly file and store the output as a .csv file, use the following command:</span></span>  
  
   `LocBaml.exe /parse HelloApp.resources.dll /out:Hello.csv`
  
   > [!NOTE]
   > <span data-ttu-id="0960f-159">HelloApp. resources. dll giriş dosyası LocBaml. exe ile aynı dizinde değilse, her iki dosyanın de aynı dizinde olması için dosyalardan birini taşıyın.</span><span class="sxs-lookup"><span data-stu-id="0960f-159">If the input file, HelloApp.resources.dll, is not in the same directory as LocBaml.exe move one of the files so that both files are in the same directory.</span></span>  
  
3. <span data-ttu-id="0960f-160">Dosyaları ayrıştırmak için LocBaml çalıştırdığınızda, çıktı virgüller (. csv dosyaları) veya sekmeler (. txt dosyaları) ile ayrılmış yedi alandan oluşur.</span><span class="sxs-lookup"><span data-stu-id="0960f-160">When you run LocBaml to parse files, the output consists of seven fields delimited by commas (.csv files) or tabs (.txt files).</span></span> <span data-ttu-id="0960f-161">Aşağıda, HelloApp. resources. dll için ayrıştırılmış. csv dosyası gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="0960f-161">The following shows the parsed .csv file for the HelloApp.resources.dll:</span></span>

   | |
   |-|
   |<span data-ttu-id="0960f-162">HelloApp. g. en-US. resources: Window1. BAML, Stack1: System. Windows. Controls. StackPanel. $Content, Ignore, FALSE, FALSE,, #Text1; #Text2;</span><span class="sxs-lookup"><span data-stu-id="0960f-162">HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignore,FALSE, FALSE,,#Text1;#Text2;</span></span>|
   |<span data-ttu-id="0960f-163">HelloApp. g. en-US. resources: Window1. BAML, Metin1: System. Windows. Controls. TextBlock. $Content, None, TRUE, TRUE,, Merhaba Dünya</span><span class="sxs-lookup"><span data-stu-id="0960f-163">HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World</span></span>|
   |<span data-ttu-id="0960f-164">HelloApp. g. en-US. resources: Window1. BAML, Metin2: System. Windows. Controls. TextBlock. $Content, None, TRUE, TRUE,, güle dünya</span><span class="sxs-lookup"><span data-stu-id="0960f-164">HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World</span></span>|

   <span data-ttu-id="0960f-165">Yedi alan şunlardır:</span><span class="sxs-lookup"><span data-stu-id="0960f-165">The seven fields are:</span></span>  
  
   - <span data-ttu-id="0960f-166">**BAML adı**.</span><span class="sxs-lookup"><span data-stu-id="0960f-166">**BAML Name**.</span></span> <span data-ttu-id="0960f-167">Kaynak dil uydu derlemesine göre BAML kaynağının adı.</span><span class="sxs-lookup"><span data-stu-id="0960f-167">The name of the BAML resource with respect to the source language satellite assembly.</span></span>  
  
   - <span data-ttu-id="0960f-168">**Kaynak anahtarı**.</span><span class="sxs-lookup"><span data-stu-id="0960f-168">**Resource Key**.</span></span> <span data-ttu-id="0960f-169">Yerelleştirilmiş kaynak tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="0960f-169">The localized resource identifier.</span></span>  
  
   - <span data-ttu-id="0960f-170">**Kategori**.</span><span class="sxs-lookup"><span data-stu-id="0960f-170">**Category**.</span></span> <span data-ttu-id="0960f-171">Değer türü.</span><span class="sxs-lookup"><span data-stu-id="0960f-171">The value type.</span></span> <span data-ttu-id="0960f-172">Bkz. [Yerelleştirme öznitelikleri ve açıklamaları](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="0960f-172">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   - <span data-ttu-id="0960f-173">**Okunabilirlik**.</span><span class="sxs-lookup"><span data-stu-id="0960f-173">**Readability**.</span></span> <span data-ttu-id="0960f-174">Değerin yerelleştirici tarafından okunup okunamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0960f-174">Whether the value can be read by a localizer.</span></span> <span data-ttu-id="0960f-175">Bkz. [Yerelleştirme öznitelikleri ve açıklamaları](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="0960f-175">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   - <span data-ttu-id="0960f-176">**Modifibeceri**.</span><span class="sxs-lookup"><span data-stu-id="0960f-176">**Modifiability**.</span></span> <span data-ttu-id="0960f-177">Değerin bir yerelleştirici tarafından değiştirilip değiştirilemediği.</span><span class="sxs-lookup"><span data-stu-id="0960f-177">Whether the value can be modified by a localizer.</span></span> <span data-ttu-id="0960f-178">Bkz. [Yerelleştirme öznitelikleri ve açıklamaları](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="0960f-178">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   - <span data-ttu-id="0960f-179">**Yorumlar**.</span><span class="sxs-lookup"><span data-stu-id="0960f-179">**Comments**.</span></span> <span data-ttu-id="0960f-180">Değerin nasıl yerelleştirileceğini belirlemede yardımcı olacak değerin ek açıklaması.</span><span class="sxs-lookup"><span data-stu-id="0960f-180">Additional description of the value to help determine how a value is localized.</span></span> <span data-ttu-id="0960f-181">Bkz. [Yerelleştirme öznitelikleri ve açıklamaları](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="0960f-181">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   - <span data-ttu-id="0960f-182">**Değer**.</span><span class="sxs-lookup"><span data-stu-id="0960f-182">**Value**.</span></span> <span data-ttu-id="0960f-183">İstenen kültüre çevrilecek metin değeri.</span><span class="sxs-lookup"><span data-stu-id="0960f-183">The text value to translate to the desired culture.</span></span>  
  
   <span data-ttu-id="0960f-184">Aşağıdaki tabloda, bu alanların. csv dosyasının ayrılmış değerleriyle nasıl eşlenme gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="0960f-184">The following table shows how these fields map to the delimited values of the .csv file:</span></span>  
  
   |<span data-ttu-id="0960f-185">BAML adı</span><span class="sxs-lookup"><span data-stu-id="0960f-185">BAML name</span></span>|<span data-ttu-id="0960f-186">Kaynak anahtarı</span><span class="sxs-lookup"><span data-stu-id="0960f-186">Resource key</span></span>|<span data-ttu-id="0960f-187">Kategori</span><span class="sxs-lookup"><span data-stu-id="0960f-187">Category</span></span>|<span data-ttu-id="0960f-188">Okunabilirlik</span><span class="sxs-lookup"><span data-stu-id="0960f-188">Readability</span></span>|<span data-ttu-id="0960f-189">Modifibilme</span><span class="sxs-lookup"><span data-stu-id="0960f-189">Modifiability</span></span>|<span data-ttu-id="0960f-190">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0960f-190">Comments</span></span>|<span data-ttu-id="0960f-191">Değer</span><span class="sxs-lookup"><span data-stu-id="0960f-191">Value</span></span>|  
   |---------------|------------------|--------------|-----------------|-------------------|--------------|-----------|
   |<span data-ttu-id="0960f-192">HelloApp. g. en-US. resources: Window1. BAML</span><span class="sxs-lookup"><span data-stu-id="0960f-192">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="0960f-193">Stack1: System. Windows. Controls. StackPanel. $Content</span><span class="sxs-lookup"><span data-stu-id="0960f-193">Stack1:System.Windows.Controls.StackPanel.$Content</span></span>|<span data-ttu-id="0960f-194">Yoksayma</span><span class="sxs-lookup"><span data-stu-id="0960f-194">Ignore</span></span>|<span data-ttu-id="0960f-195">FALSE</span><span class="sxs-lookup"><span data-stu-id="0960f-195">FALSE</span></span>|<span data-ttu-id="0960f-196">FALSE</span><span class="sxs-lookup"><span data-stu-id="0960f-196">FALSE</span></span>||<span data-ttu-id="0960f-197">#Text1; #Text2</span><span class="sxs-lookup"><span data-stu-id="0960f-197">#Text1;#Text2</span></span>|
   |<span data-ttu-id="0960f-198">HelloApp. g. en-US. resources: Window1. BAML</span><span class="sxs-lookup"><span data-stu-id="0960f-198">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="0960f-199">Metin1: System. Windows. Controls. TextBlock. $Content</span><span class="sxs-lookup"><span data-stu-id="0960f-199">Text1:System.Windows.Controls.TextBlock.$Content</span></span>|<span data-ttu-id="0960f-200">Yok</span><span class="sxs-lookup"><span data-stu-id="0960f-200">None</span></span>|<span data-ttu-id="0960f-201">TRUE</span><span class="sxs-lookup"><span data-stu-id="0960f-201">TRUE</span></span>|<span data-ttu-id="0960f-202">TRUE</span><span class="sxs-lookup"><span data-stu-id="0960f-202">TRUE</span></span>||<span data-ttu-id="0960f-203">Hello World</span><span class="sxs-lookup"><span data-stu-id="0960f-203">Hello World</span></span>|
   |<span data-ttu-id="0960f-204">HelloApp. g. en-US. resources: Window1. BAML</span><span class="sxs-lookup"><span data-stu-id="0960f-204">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="0960f-205">Metin2: System. Windows. Controls. TextBlock. $Content</span><span class="sxs-lookup"><span data-stu-id="0960f-205">Text2:System.Windows.Controls.TextBlock.$Content</span></span>|<span data-ttu-id="0960f-206">Yok</span><span class="sxs-lookup"><span data-stu-id="0960f-206">None</span></span>|<span data-ttu-id="0960f-207">TRUE</span><span class="sxs-lookup"><span data-stu-id="0960f-207">TRUE</span></span>|<span data-ttu-id="0960f-208">TRUE</span><span class="sxs-lookup"><span data-stu-id="0960f-208">TRUE</span></span>||<span data-ttu-id="0960f-209">Güle dünya</span><span class="sxs-lookup"><span data-stu-id="0960f-209">Goodbye World</span></span>|
  
   <span data-ttu-id="0960f-210">**Comments** alanı için tüm değerlerin değer içermediğini unutmayın; bir alanın değeri yoksa, boştur.</span><span class="sxs-lookup"><span data-stu-id="0960f-210">Notice that all the values for the **Comments** field contain no values; if a field doesn't have a value, it is empty.</span></span> <span data-ttu-id="0960f-211">Ayrıca, ilk satırdaki öğenin okunabilir ve değiştirilebilir olmadığından ve **Kategori** değeri olarak "Yoksay" değerine sahip olduğuna dikkat edin; hepsi değerin yerelleştirilemeyen olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0960f-211">Also notice that the item in the first row is neither readable nor modifiable, and has "Ignore" as its **Category** value, all of which indicates that the value is not localizable.</span></span>  
  
4. <span data-ttu-id="0960f-212">Özellikle büyük dosyalarda, ayrıştırılmış dosyalardaki yerelleştirilebilir öğelerin bulunmasını kolaylaştırmak için öğeleri **kategoriye**, **okunabilirlik**ve **modifime**göre sıralayabilir veya filtreleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0960f-212">To facilitate discovery of localizable items in parsed files, particularly in large files, you can sort or filter the items by **Category**, **Readability**, and **Modifiability**.</span></span> <span data-ttu-id="0960f-213">Örneğin, okunamaz ve değiştirilemeyen değerleri filtreleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0960f-213">For example, you can filter out unreadable and unmodifiable values.</span></span>  
  
## <a name="translate-the-localizable-content"></a><span data-ttu-id="0960f-214">Yerelleştirilebilir içeriği çevir</span><span class="sxs-lookup"><span data-stu-id="0960f-214">Translate the localizable content</span></span>

<span data-ttu-id="0960f-215">Ayıklanan içeriği çevirmek için kullanabileceğiniz herhangi bir aracı kullanın.</span><span class="sxs-lookup"><span data-stu-id="0960f-215">Use any tool that you have available to translate the extracted content.</span></span> <span data-ttu-id="0960f-216">Bunu yapmanın iyi bir yolu, kaynakları bir. csv dosyasına yazmak ve bunları Microsoft Excel 'de görüntüleyerek, çeviri değişikliklerini son sütuna (değer) yapıyor.</span><span class="sxs-lookup"><span data-stu-id="0960f-216">A good way to do this is to write the resources to a .csv file and view them in Microsoft Excel, making translation changes to the last column (value).</span></span>  
  
## <a name="use-locbaml-to-generate-a-new-resourcesdll-file"></a><span data-ttu-id="0960f-217">Yeni bir. resources. dll dosyası oluşturmak için LocBaml kullanın</span><span class="sxs-lookup"><span data-stu-id="0960f-217">Use LocBaml to generate a new .resources.dll file</span></span>

<span data-ttu-id="0960f-218">LocBaml ile HelloApp. resources. dll ayrıştırılmasından tanımlanan içerik çevrilmiş ve özgün uygulamayla yeniden birleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="0960f-218">The content that was identified by parsing HelloApp.resources.dll with LocBaml has been translated and must be merged back into the original application.</span></span> <span data-ttu-id="0960f-219">`generate` `-g` Yeni bir. resources. dll dosyası oluşturmak için veya seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0960f-219">Use the `generate` or `-g` option to generate a new .resources.dll file.</span></span>  
  
1. <span data-ttu-id="0960f-220">Yeni bir HelloApp. resources. dll dosyası oluşturmak için aşağıdaki sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0960f-220">Use the following syntax to generate a new HelloApp.resources.dll file.</span></span> <span data-ttu-id="0960f-221">Kültürü en-US (/CUL: en-US) olarak işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="0960f-221">Mark the culture as en-US (/cul:en-US).</span></span>  
  
   `LocBaml.exe /generate HelloApp.resources.dll /trans:Hello.csv /out:c:\ /cul:en-US`  

   > [!NOTE]
   > <span data-ttu-id="0960f-222">Hello. csv giriş dosyası yürütülebilir dosya, LocBaml. exe ile aynı dizinde değilse, her iki dosyanın de aynı dizinde olması için dosyalardan birini taşıyın.</span><span class="sxs-lookup"><span data-stu-id="0960f-222">If the input file, Hello.csv, is not in the same directory as the executable, LocBaml.exe, move one of the files so that both files are in the same directory.</span></span>  
  
2. <span data-ttu-id="0960f-223">*C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll* dizinindeki eski *HelloApp. resources. dll* dosyasını yeni oluşturduğunuz *HelloApp. resources. dll* dosyası ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="0960f-223">Replace the old *HelloApp.resources.dll* file in the *C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll* directory with your newly created *HelloApp.resources.dll* file.</span></span>  
  
3. <span data-ttu-id="0960f-224">"Merhaba Dünya" ve "gücüde Dünya" Artık uygulamanıza çevrilmelidir.</span><span class="sxs-lookup"><span data-stu-id="0960f-224">"Hello World" and "Goodbye World" should now be translated in your application.</span></span>  
  
4. <span data-ttu-id="0960f-225">Farklı bir kültüre çevirmek için, çevirinizin bulunduğu dilin kültürünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="0960f-225">To translate to a different culture, use the culture of the language that you are translating to.</span></span> <span data-ttu-id="0960f-226">Aşağıdaki örnek, Fransızca-Kanada 'ya nasıl çevrileceğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="0960f-226">The following example shows how to translate to French-Canadian:</span></span>  
  
   `LocBaml.exe /generate HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c:\ /cul:fr-CA`  
  
5. <span data-ttu-id="0960f-227">Ana uygulama derlemesiyle aynı derlemede, yeni uydu derlemesini barındırmak için kültüre özgü yeni bir klasör oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0960f-227">In the same assembly as the main application assembly, create a new culture-specific folder to house the new satellite assembly.</span></span> <span data-ttu-id="0960f-228">Fransızca-Kanada için klasör fr-CA olur.</span><span class="sxs-lookup"><span data-stu-id="0960f-228">For French-Canadian, the folder would be fr-CA.</span></span>  
  
6. <span data-ttu-id="0960f-229">Oluşturulan uydu derlemesini yeni klasöre kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="0960f-229">Copy the generated satellite assembly to the new folder.</span></span>  
  
7. <span data-ttu-id="0960f-230">Yeni uydu derlemesini test etmek için uygulamanızın çalıştırılacağı kültürü değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0960f-230">To test the new satellite assembly, you need to change the culture under which your application will run.</span></span> <span data-ttu-id="0960f-231">Bunu iki yoldan biriyle yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0960f-231">You can do this in one of two ways:</span></span>  
  
   - <span data-ttu-id="0960f-232">İşletim sisteminizin bölgesel ayarlarını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="0960f-232">Change your operating system's regional settings.</span></span>
  
   - <span data-ttu-id="0960f-233">Uygulamanızda, App.xaml.cs 'e aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0960f-233">In your application, add the following code to App.xaml.cs:</span></span>  
  
     [!code-xaml[LocBamlChangeCultureSnippets#LocBamlChangeCultureMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml#locbamlchangeculturemarkup)]
     [!code-csharp[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml.cs#locbamlchangeculturecodebehind)]
     [!code-vb[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/VisualBasic/Application.xaml.vb#locbamlchangeculturecodebehind)]  
  
## <a name="tips-for-using-locbaml"></a><span data-ttu-id="0960f-234">LocBaml kullanma ipuçları</span><span class="sxs-lookup"><span data-stu-id="0960f-234">Tips for Using LocBaml</span></span>  
  
- <span data-ttu-id="0960f-235">Özel denetimleri tanımlayan tüm bağımlı derlemelerin LocBaml yerel dizinine kopyalanması veya GAC 'ye yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="0960f-235">All dependent assemblies that define custom controls must be copied into the local directory of LocBaml or installed into the GAC.</span></span> <span data-ttu-id="0960f-236">Bu gereklidir çünkü yerelleştirme API 'sinin, ikili XAML (BAML) okurken bağımlı derlemelere erişimi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0960f-236">This is necessary because the localization API must have access to the dependent assemblies when it reads the binary XAML (BAML).</span></span>  
  
- <span data-ttu-id="0960f-237">Ana derleme imzalanmışsa, oluşturulan kaynak DLL 'nin yüklenmesi için de imzalı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0960f-237">If the main assembly is signed, the generated resource DLL must also be signed in order for it to be loaded.</span></span>  
  
- <span data-ttu-id="0960f-238">Yerelleştirilmiş kaynak DLL sürümünün ana derlemeyle eşitlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="0960f-238">The version of the localized resource DLL needs to be synchronized with the main assembly.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0960f-239">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0960f-239">See also</span></span>

- [<span data-ttu-id="0960f-240">WPF için Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="0960f-240">Globalization for WPF</span></span>](globalization-for-wpf.md)
- [<span data-ttu-id="0960f-241">Otomatik Düzen Kullanımına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0960f-241">Use Automatic Layout Overview</span></span>](use-automatic-layout-overview.md)
