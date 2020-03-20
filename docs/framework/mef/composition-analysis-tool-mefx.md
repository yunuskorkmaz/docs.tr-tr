---
title: Bileşim Analiz Aracı (Mefx)
ms.date: 03/30/2017
helpviewer_keywords:
- Composition Analysis Tool [MEF]
- MEF, Composition Analysis Tool
- Mefx [MEF], Composition Analysis Tool
ms.assetid: c48a7f93-83bb-4a06-aea0-d8e7bd1502ad
ms.openlocfilehash: 7d0acf16ace5aad60b32b7139a58a258fb080ee0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181295"
---
# <a name="composition-analysis-tool-mefx"></a><span data-ttu-id="7d3b8-102">Bileşim Analiz Aracı (Mefx)</span><span class="sxs-lookup"><span data-stu-id="7d3b8-102">Composition Analysis Tool (Mefx)</span></span>
<span data-ttu-id="7d3b8-103">Kompozisyon Çözümleme Aracı (Mefx), Yönetilen Genişletilebilirlik Çerçevesi (MEF) parçalarını içeren kitaplık (.dll) ve uygulama (.exe) dosyalarını analiz eden bir komut satırı uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="7d3b8-103">The Composition Analysis Tool (Mefx) is a command-line application that analyzes library (.dll) and application (.exe) files containing Managed Extensibility Framework (MEF) parts.</span></span> <span data-ttu-id="7d3b8-104">Mefx'in birincil amacı, geliştiricilere MEF uygulamalarındaki kompozisyon hatalarını uygulamanın kendisine hantal izleme kodu ekleme gereksinimi olmadan tanılamaları için bir yol sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="7d3b8-104">The primary purpose of Mefx is to provide developers a way to diagnose composition failures in their MEF applications without the requirement to add cumbersome tracing code to the application itself.</span></span> <span data-ttu-id="7d3b8-105">Ayrıca, üçüncü bir taraf tarafından sağlanan bir kitaplıktan parçaları anlamasına yardımcı olmak da yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="7d3b8-105">It can also be useful to help understand parts from a library provided by a third party.</span></span> <span data-ttu-id="7d3b8-106">Bu konu, Mefx'in nasıl kullanılacağını açıklar ve sözdizimi için bir başvuru sağlar.</span><span class="sxs-lookup"><span data-stu-id="7d3b8-106">This topic describes how to use Mefx and provides a reference for its syntax.</span></span>  
  
<a name="getting_mefx"></a>
## <a name="getting-mefx"></a><span data-ttu-id="7d3b8-107">Mefx Başlarken</span><span class="sxs-lookup"><span data-stu-id="7d3b8-107">Getting Mefx</span></span>  
 <span data-ttu-id="7d3b8-108">Mefx GitHub'da [Yönetilen Genişletilebilirlik Çerçevesi'nde](https://github.com/MicrosoftArchive/mef/releases/tag/4.0)mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="7d3b8-108">Mefx is available on GitHub at [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef/releases/tag/4.0).</span></span> <span data-ttu-id="7d3b8-109">Sadece indirin ve aracı unzip.</span><span class="sxs-lookup"><span data-stu-id="7d3b8-109">Simply download and unzip the tool.</span></span>  
  
<a name="basic_syntax"></a>
## <a name="basic-syntax"></a><span data-ttu-id="7d3b8-110">Temel Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7d3b8-110">Basic Syntax</span></span>  
 <span data-ttu-id="7d3b8-111">Mefx komut satırından aşağıdaki biçimde çağrılır:</span><span class="sxs-lookup"><span data-stu-id="7d3b8-111">Mefx is invoked from the command line in the following format:</span></span>  
  
```console
mefx [files and directories] [action] [options]  
```  
  
 <span data-ttu-id="7d3b8-112">İlk bağımsız değişken kümesi, çözümleme için parçaların yüklendiği dosyaları ve dizinleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="7d3b8-112">The first set of arguments specify the files and directories from which to load parts for analysis.</span></span> <span data-ttu-id="7d3b8-113">Anahtarlı `/file:` bir dosya ve anahtarlı bir `/directory:` dizin belirtin.</span><span class="sxs-lookup"><span data-stu-id="7d3b8-113">Specify a file with the `/file:` switch, and a directory with the `/directory:` switch.</span></span> <span data-ttu-id="7d3b8-114">Aşağıdaki örnekte gösterildiği gibi birden çok dosya veya dizin belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7d3b8-114">You can specify multiple files or directories, as shown in the following example:</span></span>  
  
```console  
mefx /file:MyAddIn.dll /directory:Program\AddIns [action...]  
```  
  
> [!NOTE]
> <span data-ttu-id="7d3b8-115">Her .dll veya .exe yalnızca bir kez yüklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="7d3b8-115">Each .dll or .exe should only be loaded one time.</span></span> <span data-ttu-id="7d3b8-116">Bir dosya birden çok kez yüklenirse, araç yanlış bilgileri döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="7d3b8-116">If a file is loaded multiple times, the tool may return incorrect information.</span></span>  
  
 <span data-ttu-id="7d3b8-117">Dosya ve dizinler listesinden sonra, bir komut ve bu komut için herhangi bir seçenek belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7d3b8-117">After the list of files and directories, you must specify a command, and any options for that command.</span></span>  
  
<a name="listing_available_parts"></a>
## <a name="listing-available-parts"></a><span data-ttu-id="7d3b8-118">Kullanılabilir Parçaları Listeleme</span><span class="sxs-lookup"><span data-stu-id="7d3b8-118">Listing Available Parts</span></span>  
 <span data-ttu-id="7d3b8-119">Yüklenen `/parts` dosyalarda bildirilen tüm parçaları listelemek için eylemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="7d3b8-119">Use the `/parts` action to list all the parts declared in the files loaded.</span></span> <span data-ttu-id="7d3b8-120">Sonuç, parça adlarının basit bir listesidir.</span><span class="sxs-lookup"><span data-stu-id="7d3b8-120">The result is a simple list of part names.</span></span>  
  
```console
mefx /file:MyAddIn.dll /parts  
MyAddIn.AddIn  
MyAddIn.MemberPart  
```  
  
 <span data-ttu-id="7d3b8-121">Parçalar hakkında daha fazla bilgi `/verbose` için seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="7d3b8-121">For more information about the parts, use the `/verbose` option.</span></span> <span data-ttu-id="7d3b8-122">Bu, kullanılabilir tüm parçalar için daha fazla bilgi elde eder.</span><span class="sxs-lookup"><span data-stu-id="7d3b8-122">This will output more information for all available parts.</span></span> <span data-ttu-id="7d3b8-123">Tek bir bölüm hakkında daha fazla `/type` bilgi `/parts`almak için eylemi ' yerine kullanın.</span><span class="sxs-lookup"><span data-stu-id="7d3b8-123">To get more information about a single part, use the `/type` action instead of `/parts`.</span></span>  
  
```console  
mefx /file:MyAddIn.dll /type:MyAddIn.AddIn /verbose  
[Part] MyAddIn.MemberPart from: AssemblyCatalog (Assembly=" MyAddIn, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Export] MyAddIn.MemberPart (ContractName=" MyAddIn.MemberPart")  
```  
  
<a name="listing_imports_and_exports"></a>
## <a name="listing-imports-and-exports"></a><span data-ttu-id="7d3b8-124">İthalat ve İhracatı Listeleme</span><span class="sxs-lookup"><span data-stu-id="7d3b8-124">Listing Imports and Exports</span></span>  
 <span data-ttu-id="7d3b8-125">Ve `/imports` `/exports` eylemler, sırasıyla tüm içe aktarılan parçaları ve tüm dışa aktarılan parçaları listeler.</span><span class="sxs-lookup"><span data-stu-id="7d3b8-125">The `/imports` and `/exports` actions will list all the imported parts and all the exported parts, respectively.</span></span> <span data-ttu-id="7d3b8-126">Ayrıca, belirli bir türü veya `/importers` `/exporters` eylemleri kullanarak içe aktaran veya dışa aktaran parçaları da listeleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d3b8-126">You can also list the parts that import or export a particular type by using the `/importers` or `/exporters` actions.</span></span>  
  
```console  
mefx /file:MyAddIn.dll /importers:MyAddin.MemberPart  
MyAddin.AddIn  
```  
  
 <span data-ttu-id="7d3b8-127">Bu eylemler ekimi `/verbose` de uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d3b8-127">You can also apply the `/verbose` option to these actions.</span></span>  
  
<a name="finding_rejected_parts"></a>
## <a name="finding-rejected-parts"></a><span data-ttu-id="7d3b8-128">Reddedilen Parçaları Bulma</span><span class="sxs-lookup"><span data-stu-id="7d3b8-128">Finding Rejected Parts</span></span>  
 <span data-ttu-id="7d3b8-129">Kullanılabilir parçaları yükledikten sonra, Mefx bunları oluşturmak için MEF kompozisyon motorini kullanır.</span><span class="sxs-lookup"><span data-stu-id="7d3b8-129">Once it has loaded the available parts, Mefx uses the MEF composition engine to compose them.</span></span> <span data-ttu-id="7d3b8-130">Başarıyla oluşturulamayan parçalar *reddedildi*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="7d3b8-130">Parts that cannot be successfully composed are referred to as *rejected*.</span></span> <span data-ttu-id="7d3b8-131">Reddedilen tüm parçaları listelemek `/rejected` için eylemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="7d3b8-131">To list all the rejected parts, use the `/rejected` action.</span></span>  
  
 <span data-ttu-id="7d3b8-132">Reddedilen parçalar `/verbose` hakkında ayrıntılı `/rejected` bilgi yazdırmak için eylem seçeneğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d3b8-132">You can use the `/verbose` option with the `/rejected` action to print detailed information about rejected parts.</span></span> <span data-ttu-id="7d3b8-133">Aşağıdaki örnekte, `ClassLibrary1` DLL ve `AddIn` `ChainOne` parçaları içe `MemberPart` aktaran bölümü içerir.</span><span class="sxs-lookup"><span data-stu-id="7d3b8-133">In the following example, the `ClassLibrary1` DLL contains the `AddIn` part, which imports the `MemberPart` and `ChainOne` parts.</span></span> <span data-ttu-id="7d3b8-134">`ChainOne`içe, `ChainTwo` `ChainTwo` ancak yok.</span><span class="sxs-lookup"><span data-stu-id="7d3b8-134">`ChainOne` imports `ChainTwo`, but `ChainTwo` does not exist.</span></span> <span data-ttu-id="7d3b8-135">Bu, `ChainOne` reddedilmesine neden `AddIn` olan anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="7d3b8-135">This means that `ChainOne` is rejected, which causes `AddIn` to be rejected.</span></span>  
  
```console  
mefx /file:ClassLibrary1.dll /rejected /verbose  
```  
  
 <span data-ttu-id="7d3b8-136">Aşağıdaki önceki komutun tam çıktısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="7d3b8-136">The following shows the complete output of the previous command:</span></span>  
  
```output
[Part] ClassLibrary1.AddIn from: AssemblyCatalog (Assembly="ClassLibrary1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Export] ClassLibrary1.AddIn (ContractName="ClassLibrary1.AddIn")  
  [Import] ClassLibrary1.AddIn.memberPart (ContractName="ClassLibrary1.MemberPart")  
    [SatisfiedBy] ClassLibrary1.MemberPart (ContractName="ClassLibrary1.MemberPart") from: ClassLibrary1.MemberPart from: AssemblyCatalog (Assembly="ClassLibrar  
y1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Import] ClassLibrary1.AddIn.chain (ContractName="ClassLibrary1.ChainOne")  
    [Exception] System.ComponentModel.Composition.ImportCardinalityMismatchException: No valid exports were found that match the constraint '((exportDefinition.ContractName == "ClassLibrary1.ChainOne") AndAlso (exportDefinition.Metadata.ContainsKey("ExportTypeIdentity") AndAlso "ClassLibrary1.ChainOne".Equals(exportDefinition.Metadata.get_Item("ExportTypeIdentity"))))', invalid exports may have been rejected.  
   at System.ComponentModel.Composition.Hosting.ExportProvider.GetExports(ImportDefinition definition, AtomicComposition atomicComposition)  
   at Microsoft.ComponentModel.Composition.Diagnostics.CompositionInfo.AnalyzeImportDefinition(ExportProvider host, IEnumerable`1 availableParts, ImportDefinition id)  
    [Unsuitable] ClassLibrary1.ChainOne (ContractName="ClassLibrary1.ChainOne")  
from: ClassLibrary1.ChainOne from: AssemblyCatalog (Assembly="ClassLibrary1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
      [Because] PartDefinitionIsRejected, The part providing the export is rejected because of other issues.  
  
[Part] ClassLibrary1.ChainOne from: AssemblyCatalog (Assembly="ClassLibrary1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Primary Rejection]  
  [Export] ClassLibrary1.ChainOne (ContractName="ClassLibrary1.ChainOne")  
  [Import] ClassLibrary1.ChainOne.chain (ContractName="ClassLibrary1.ChainTwo")  
    [Exception] System.ComponentModel.Composition.ImportCardinalityMismatchException: No valid exports were found that match the constraint '((exportDefinition.ContractName == "ClassLibrary1.ChainTwo") AndAlso (exportDefinition.Metadata.ContainsKey("ExportTypeIdentity") AndAlso "ClassLibrary1.ChainTwo".Equals(exportDefinition.Metadata.get_Item("ExportTypeIdentity"))))', invalid exports may have been rejected.  
   at System.ComponentModel.Composition.Hosting.ExportProvider.GetExports(ImportDefinition definition, AtomicComposition atomicComposition)  
   at Microsoft.ComponentModel.Composition.Diagnostics.CompositionInfo.AnalyzeImportDefinition(ExportProvider host, IEnumerable`1 availableParts, ImportDefinition id)  
```  
  
 <span data-ttu-id="7d3b8-137">İlginç bilgiler `[Exception]` ve `[Unsuitable]` sonuçlar yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="7d3b8-137">The interesting information is contained in the `[Exception]` and `[Unsuitable]` results.</span></span> <span data-ttu-id="7d3b8-138">Sonuç, `[Exception]` bir parçanın neden reddedildiği hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="7d3b8-138">The `[Exception]` result provides information about why a part was rejected.</span></span> <span data-ttu-id="7d3b8-139">Sonuç, `[Unsuitable]` başka bir şekilde eşleşen bir parçanın neden bir alma işlemi doldurmak için kullanılamayacağını gösterir; bu durumda, çünkü bu bölüm kendisi eksik ithalat için reddedildi.</span><span class="sxs-lookup"><span data-stu-id="7d3b8-139">The `[Unsuitable]` result indicates why an otherwise-matching part could not be used to fill an import; in this case, because that part was itself rejected for missing imports.</span></span>  
  
<a name="analyzing_primary_causes"></a>
## <a name="analyzing-primary-causes"></a><span data-ttu-id="7d3b8-140">Birincil Nedenleri Çözümleme</span><span class="sxs-lookup"><span data-stu-id="7d3b8-140">Analyzing Primary Causes</span></span>  
 <span data-ttu-id="7d3b8-141">Birkaç parça uzun bir bağımlılık zincirine bağlıysa, alta yakın bir parçayı içeren bir sorun tüm zincirin reddedilmesine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="7d3b8-141">If several parts are linked in a long dependency chain, a problem involving a part near the bottom may cause the entire chain to be rejected.</span></span> <span data-ttu-id="7d3b8-142">Başarısızlığın temel nedeni her zaman açık olmadığından, bu sorunları tanılamak zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="7d3b8-142">Diagnosing these problems can be difficult because the root cause of the failure is not always obvious.</span></span> <span data-ttu-id="7d3b8-143">Soruna yardımcı olmak için, `/causes` basamaklı reddin temel nedenini bulmaya çalışan eylemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d3b8-143">To help with the problem, you can use the `/causes` action, which attempts to find the root cause of any cascading rejection.</span></span>  
  
 <span data-ttu-id="7d3b8-144">Önceki `/causes` örnekte eylemi kullanarak yalnızca doldurulmamış alma reddinin temel nedeni olan `ChainOne` `AddIn`bilgileri listeler.</span><span class="sxs-lookup"><span data-stu-id="7d3b8-144">Using the `/causes` action on the previous example would list only information for `ChainOne`, whose unfilled import is the root cause of the rejection of `AddIn`.</span></span> <span data-ttu-id="7d3b8-145">Eylem `/causes` hem normal hem `/verbose` de seçeneklerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7d3b8-145">The `/causes` action can be used in both normal and `/verbose` options.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7d3b8-146">Çoğu durumda, Mefx basamaklı bir hatanın kök nedenini tanılamak mümkün olacaktır.</span><span class="sxs-lookup"><span data-stu-id="7d3b8-146">In most cases, Mefx will be able to diagnose the root cause of a cascading failure.</span></span> <span data-ttu-id="7d3b8-147">Ancak, parçaların bir kapsayıcıya programlı olarak eklendiği durumlarda, hiyerarşik `ExportProvider` kapsayıcılar içeren durumlarda veya özel uygulamaları içeren durumlarda, Mefx nedenini tanılamak mümkün olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="7d3b8-147">However, in cases where parts are added programmatically to a container, cases involving hierarchical containers, or cases involving custom `ExportProvider` implementations, Mefx will not be able to diagnose the cause.</span></span> <span data-ttu-id="7d3b8-148">Genel olarak, hataların tanısı genellikle zor olduğundan, daha önce açıklanan durumlarda mümkün olduğunca kaçınılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7d3b8-148">In general, the previously described cases should be avoided where possible, as failures are generally difficult to diagnose.</span></span>  
  
<a name="white_lists"></a>
## <a name="white-lists"></a><span data-ttu-id="7d3b8-149">Beyaz Listeler</span><span class="sxs-lookup"><span data-stu-id="7d3b8-149">White Lists</span></span>  
 <span data-ttu-id="7d3b8-150">Bu `/whitelist` seçenek, reddedilmesi beklenen bölümleri listeleyen bir metin dosyası belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="7d3b8-150">The `/whitelist` option enables you to specify a text file that lists parts that are expected to be rejected.</span></span> <span data-ttu-id="7d3b8-151">Beklenmeyen reddetmeler daha sonra işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="7d3b8-151">Unexpected rejections will then be flagged.</span></span> <span data-ttu-id="7d3b8-152">Bu, eksik bir kitaplığı veya bazı bağımlılıkları eksik olan bir alt kitaplığı çözümlediğinizde yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="7d3b8-152">This can be useful when you analyze an incomplete library, or a sub-library that is missing some dependencies.</span></span> <span data-ttu-id="7d3b8-153">Bu `/whitelist` seçenek eylemlere `/rejected` veya `/causes` eylemlere uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="7d3b8-153">The `/whitelist` option can be applied to the `/rejected` or `/causes` actions.</span></span>  
  
 <span data-ttu-id="7d3b8-154">"ClassLibrary1.ChainOne" metnini içeren test.txt adlı bir dosya düşünün.</span><span class="sxs-lookup"><span data-stu-id="7d3b8-154">Consider a file named test.txt that contains the text "ClassLibrary1.ChainOne".</span></span> <span data-ttu-id="7d3b8-155">`/rejected` Eylemi önceki örnekte `/whitelist` seçenekle çalıştırırsanız, aşağıdaki çıktıyı üretecektir:</span><span class="sxs-lookup"><span data-stu-id="7d3b8-155">If you run the `/rejected` action with the `/whitelist` option on the previous example, it will produce the following output:</span></span>  
  
```console
mefx /file:ClassLibrary1.dll /rejected /whitelist:test.txt  
[Unexpected] ClassLibrary1.AddIn  
ClassLibrary1.ChainOne  
```
