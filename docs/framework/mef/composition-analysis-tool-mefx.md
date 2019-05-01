---
title: Bileşim Analiz Aracı (Mefx)
ms.date: 03/30/2017
helpviewer_keywords:
- Composition Analysis Tool [MEF]
- MEF, Composition Analysis Tool
- Mefx [MEF], Composition Analysis Tool
ms.assetid: c48a7f93-83bb-4a06-aea0-d8e7bd1502ad
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6851ac334d439f2e5c0f6056f5226e3faa1503d5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61872345"
---
# <a name="composition-analysis-tool-mefx"></a><span data-ttu-id="47919-102">Bileşim Analiz Aracı (Mefx)</span><span class="sxs-lookup"><span data-stu-id="47919-102">Composition Analysis Tool (Mefx)</span></span>
<span data-ttu-id="47919-103">Bileşim analiz Aracı (Mefx) kitaplığı (.dll) ve uygulama (.exe) dosyaları Yönetilen Genişletilebilirlik Çerçevesi (MEF) parçalarını içeren bir komut satırı uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="47919-103">The Composition Analysis Tool (Mefx) is a command-line application that analyzes library (.dll) and application (.exe) files containing Managed Extensibility Framework (MEF) parts.</span></span> <span data-ttu-id="47919-104">Mefx birincil amacı, geliştiricilerin uygulamaya hantal izleme kodu eklemek için gereksinimi olmadan, MEF uygulamalarında oluşturma hatalarını tanılamak için bir yol sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="47919-104">The primary purpose of Mefx is to provide developers a way to diagnose composition failures in their MEF applications without the requirement to add cumbersome tracing code to the application itself.</span></span> <span data-ttu-id="47919-105">Ayrıca üçüncü taraf tarafından sağlanan bir kitaplıktan bölümleri yardımcı olması yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="47919-105">It can also be useful to help understand parts from a library provided by a third party.</span></span> <span data-ttu-id="47919-106">Bu konu, Mefx kullanmayı açıklar ve bir başvuru için kendi sözdizimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="47919-106">This topic describes how to use Mefx and provides a reference for its syntax.</span></span>  
  
<a name="getting_mefx"></a>   
## <a name="getting-mefx"></a><span data-ttu-id="47919-107">Mefx alma</span><span class="sxs-lookup"><span data-stu-id="47919-107">Getting Mefx</span></span>  
 <span data-ttu-id="47919-108">Mefx github'da kullanılabilir [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef/releases/tag/4.0).</span><span class="sxs-lookup"><span data-stu-id="47919-108">Mefx is available on GitHub at [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef/releases/tag/4.0).</span></span> <span data-ttu-id="47919-109">Yalnızca indirin ve Aracı'nı açın.</span><span class="sxs-lookup"><span data-stu-id="47919-109">Simply download and unzip the tool.</span></span>  
  
<a name="basic_syntax"></a>   
## <a name="basic-syntax"></a><span data-ttu-id="47919-110">Temel söz dizimi</span><span class="sxs-lookup"><span data-stu-id="47919-110">Basic Syntax</span></span>  
 <span data-ttu-id="47919-111">Aşağıdaki biçimde bir komut satırından Mefx çağrılır:</span><span class="sxs-lookup"><span data-stu-id="47919-111">Mefx is invoked from the command line in the following format:</span></span>  
  
```  
mefx [files and directories] [action] [options]  
```  
  
 <span data-ttu-id="47919-112">İlk bağımsız değişken kümesinin, dosyaları ve analiz için bölümleri yükleneceği dizinlerden belirtin.</span><span class="sxs-lookup"><span data-stu-id="47919-112">The first set of arguments specify the files and directories from which to load parts for analysis.</span></span> <span data-ttu-id="47919-113">Bir dosya belirtmek `/file:` anahtarı ve bir dizinle `/directory:` geçin.</span><span class="sxs-lookup"><span data-stu-id="47919-113">Specify a file with the `/file:` switch, and a directory with the `/directory:` switch.</span></span> <span data-ttu-id="47919-114">Aşağıdaki örnekte gösterildiği gibi birden çok dosyayı veya dizinleri belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="47919-114">You can specify multiple files or directories, as shown in the following example:</span></span>  
  
```  
mefx /file:MyAddIn.dll /directory:Program\AddIns [action...]  
```  
  
> [!NOTE]
>  <span data-ttu-id="47919-115">Yalnızca bir kez, her .dll veya .exe yüklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="47919-115">Each .dll or .exe should only be loaded one time.</span></span> <span data-ttu-id="47919-116">Bir dosyayı birden çok kez yüklenirse, aracı yanlış bilgi döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="47919-116">If a file is loaded multiple times, the tool may return incorrect information.</span></span>  
  
 <span data-ttu-id="47919-117">Dosyalar ve dizinler listesinde sonra bir komut ve komutun herhangi bir seçenek belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="47919-117">After the list of files and directories, you must specify a command, and any options for that command.</span></span>  
  
<a name="listing_available_parts"></a>   
## <a name="listing-available-parts"></a><span data-ttu-id="47919-118">Kullanılabilir bölümleri listeleme</span><span class="sxs-lookup"><span data-stu-id="47919-118">Listing Available Parts</span></span>  
 <span data-ttu-id="47919-119">Kullanım `/parts` tüm bölümleri listelemek için eylem bildirilen yüklenen dosyaları.</span><span class="sxs-lookup"><span data-stu-id="47919-119">Use the `/parts` action to list all the parts declared in the files loaded.</span></span> <span data-ttu-id="47919-120">Basit bölüm adları listesini sonucudur.</span><span class="sxs-lookup"><span data-stu-id="47919-120">The result is a simple list of part names.</span></span>  
  
```  
mefx /file:MyAddIn.dll /parts  
MyAddIn.AddIn  
MyAddIn.MemberPart  
```  
  
 <span data-ttu-id="47919-121">Bölümleri hakkında daha fazla bilgi için `/verbose` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="47919-121">For more information about the parts, use the `/verbose` option.</span></span> <span data-ttu-id="47919-122">Bu, daha fazla bilgi için kullanılabilir tüm bölümleri çıkarır.</span><span class="sxs-lookup"><span data-stu-id="47919-122">This will output more information for all available parts.</span></span> <span data-ttu-id="47919-123">Tek bir bölümü hakkında daha fazla bilgi almak için kullanın `/type` yerine eylem `/parts`.</span><span class="sxs-lookup"><span data-stu-id="47919-123">To get more information about a single part, use the `/type` action instead of `/parts`.</span></span>  
  
```  
mefx /file:MyAddIn.dll /type:MyAddIn.AddIn /verbose  
[Part] MyAddIn.MemberPart from: AssemblyCatalog (Assembly=" MyAddIn, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Export] MyAddIn.MemberPart (ContractName=" MyAddIn.MemberPart")  
```  
  
<a name="listing_imports_and_exports"></a>   
## <a name="listing-imports-and-exports"></a><span data-ttu-id="47919-124">İçeri ve dışarı aktarmalar listeleme</span><span class="sxs-lookup"><span data-stu-id="47919-124">Listing Imports and Exports</span></span>  
 <span data-ttu-id="47919-125">`/imports` Ve `/exports` eylemleri listeler içeri aktarılan tüm bölümleri ve tüm dışarı aktarılan bölümleri sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="47919-125">The `/imports` and `/exports` actions will list all the imported parts and all the exported parts, respectively.</span></span> <span data-ttu-id="47919-126">Ayrıca belirli bir tür kullanarak dışarı veya içeri aktarın bölümleri listeleyebilirsiniz `/importers` veya `/exporters` eylemler.</span><span class="sxs-lookup"><span data-stu-id="47919-126">You can also list the parts that import or export a particular type by using the `/importers` or `/exporters` actions.</span></span>  
  
```  
mefx /file:MyAddIn.dll /importers:MyAddin.MemberPart  
MyAddin.AddIn  
```  
  
 <span data-ttu-id="47919-127">Ayrıca uygulayabilirsiniz `/verbose` bu eylemler için seçeneği.</span><span class="sxs-lookup"><span data-stu-id="47919-127">You can also apply the `/verbose` option to these actions.</span></span>  
  
<a name="finding_rejected_parts"></a>   
## <a name="finding-rejected-parts"></a><span data-ttu-id="47919-128">Bulma bölümleri reddetti</span><span class="sxs-lookup"><span data-stu-id="47919-128">Finding Rejected Parts</span></span>  
 <span data-ttu-id="47919-129">Mefx MEF bileşim motoru kullanılabilir bölümleri yüklendikten sonra bunları oluşturmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="47919-129">Once it has loaded the available parts, Mefx uses the MEF composition engine to compose them.</span></span> <span data-ttu-id="47919-130">Başarıyla birleştirilemeyen bölümleri denir *reddedilen*.</span><span class="sxs-lookup"><span data-stu-id="47919-130">Parts that cannot be successfully composed are referred to as *rejected*.</span></span> <span data-ttu-id="47919-131">Reddedilen tüm bölümleri listelemek için kullanın `/rejected` eylem.</span><span class="sxs-lookup"><span data-stu-id="47919-131">To list all the rejected parts, use the `/rejected` action.</span></span>  
  
 <span data-ttu-id="47919-132">Kullanabileceğiniz `/verbose` seçeneğini `/rejected` bölümleri hakkında ayrıntılı bilgi yazdırmak için eylem reddedildi.</span><span class="sxs-lookup"><span data-stu-id="47919-132">You can use the `/verbose` option with the `/rejected` action to print detailed information about rejected parts.</span></span> <span data-ttu-id="47919-133">Aşağıdaki örnekte, `ClassLibrary1` DLL içeren `AddIn` kısım, hangi içeri aktarmalar `MemberPart` ve `ChainOne` bölümleri.</span><span class="sxs-lookup"><span data-stu-id="47919-133">In the following example, the `ClassLibrary1` DLL contains the `AddIn` part, which imports the `MemberPart` and `ChainOne` parts.</span></span> <span data-ttu-id="47919-134">`ChainOne` Imports `ChainTwo`, ancak `ChainTwo` yok.</span><span class="sxs-lookup"><span data-stu-id="47919-134">`ChainOne` imports `ChainTwo`, but `ChainTwo` does not exist.</span></span> <span data-ttu-id="47919-135">Diğer bir deyişle `ChainOne` reddedilir, hangi nedenleri `AddIn` reddedilir.</span><span class="sxs-lookup"><span data-stu-id="47919-135">This means that `ChainOne` is rejected, which causes `AddIn` to be rejected.</span></span>  
  
```  
mefx /file:ClassLibrary1.dll /rejected /verbose  
```  
  
 <span data-ttu-id="47919-136">Önceki komutun tam çıktı aşağıda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="47919-136">The following shows the complete output of the previous command:</span></span>  
  
```  
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
  
 <span data-ttu-id="47919-137">İlgi çekici bilgiler içerdiği `[Exception]` ve `[Unsuitable]` sonuçları.</span><span class="sxs-lookup"><span data-stu-id="47919-137">The interesting information is contained in the `[Exception]` and `[Unsuitable]` results.</span></span> <span data-ttu-id="47919-138">`[Exception]` Sonucu bir bölümü neden reddedildiği hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="47919-138">The `[Exception]` result provides information about why a part was rejected.</span></span> <span data-ttu-id="47919-139">`[Unsuitable]` Sonuç neden eşleşen başka bir bölümü alma doldurmak için kullanılamadı gösterir; bu durumda, bunlar kendisi bu bölümü olduğundan eksik Imports reddetti.</span><span class="sxs-lookup"><span data-stu-id="47919-139">The `[Unsuitable]` result indicates why an otherwise-matching part could not be used to fill an import; in this case, because that part was itself rejected for missing imports.</span></span>  
  
<a name="analyzing_primary_causes"></a>   
## <a name="analyzing-primary-causes"></a><span data-ttu-id="47919-140">Birincil çözümleme neden olur.</span><span class="sxs-lookup"><span data-stu-id="47919-140">Analyzing Primary Causes</span></span>  
 <span data-ttu-id="47919-141">Birkaç bölümden uzun bağımlılık zincirinde bağlıysa, bir bölümü altına ilgili bir sorun reddedilir zincirini neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="47919-141">If several parts are linked in a long dependency chain, a problem involving a part near the bottom may cause the entire chain to be rejected.</span></span> <span data-ttu-id="47919-142">Kök nedenini her zaman açık olmadığından bu sorunların tanılanması zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="47919-142">Diagnosing these problems can be difficult because the root cause of the failure is not always obvious.</span></span> <span data-ttu-id="47919-143">Sorunu çözmek için kullanabileceğiniz `/causes` eylem, hiçbir basamaklı reddetme nedenini bulmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="47919-143">To help with the problem, you can use the `/causes` action, which attempts to find the root cause of any cascading rejection.</span></span>  
  
 <span data-ttu-id="47919-144">Kullanarak `/causes` listesinde yalnızca bilgi için önceki örneğin eylem `ChainOne`, doldurulmamış olan içeri aktarma olan ret kök nedenini `AddIn`.</span><span class="sxs-lookup"><span data-stu-id="47919-144">Using the `/causes` action on the previous example would list only information for `ChainOne`, whose unfilled import is the root cause of the rejection of `AddIn`.</span></span> <span data-ttu-id="47919-145">`/causes` Eylem hem normal kullanılabilir ve `/verbose` seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="47919-145">The `/causes` action can be used in both normal and `/verbose` options.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="47919-146">Çoğu durumda, Mefx basamaklı hatanın kök nedeni tanılamak mümkün olacaktır.</span><span class="sxs-lookup"><span data-stu-id="47919-146">In most cases, Mefx will be able to diagnose the root cause of a cascading failure.</span></span> <span data-ttu-id="47919-147">Ancak, burada bölümleri eklendi program aracılığıyla bir kapsayıcıya hiyerarşik kapsayıcılar içeren durumlarda durumları veya özel ilgili olarak `ExportProvider` uygulamaları Mefx gerçekleştiremez nedenini tanılamak.</span><span class="sxs-lookup"><span data-stu-id="47919-147">However, in cases where parts are added programmatically to a container, cases involving hierarchical containers, or cases involving custom `ExportProvider` implementations, Mefx will not be able to diagnose the cause.</span></span> <span data-ttu-id="47919-148">Genel olarak, hataları tanılamak genellikle zor olduğu gibi daha önce açıklandığı gibi durumlarda mümkün olduğunca kaçınılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="47919-148">In general, the previously described cases should be avoided where possible, as failures are generally difficult to diagnose.</span></span>  
  
<a name="white_lists"></a>   
## <a name="white-lists"></a><span data-ttu-id="47919-149">Beyaz listeleri</span><span class="sxs-lookup"><span data-stu-id="47919-149">White Lists</span></span>  
 <span data-ttu-id="47919-150">`/whitelist` Seçeneği reddedilmesi beklenen bölümleri listeleyen bir metin dosyası belirtmenize imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="47919-150">The `/whitelist` option enables you to specify a text file that lists parts that are expected to be rejected.</span></span> <span data-ttu-id="47919-151">Beklenmeyen redleri sonra işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="47919-151">Unexpected rejections will then be flagged.</span></span> <span data-ttu-id="47919-152">Tamamlanmamış bir kitaplığı veya bazı bağımlılıklar eksik olan alt kitaplığı çözümlediğinizde bu yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="47919-152">This can be useful when you analyze an incomplete library, or a sub-library that is missing some dependencies.</span></span> <span data-ttu-id="47919-153">`/whitelist` Seçeneği uygulanabilir `/rejected` veya `/causes` eylemler.</span><span class="sxs-lookup"><span data-stu-id="47919-153">The `/whitelist` option can be applied to the `/rejected` or `/causes` actions.</span></span>  
  
 <span data-ttu-id="47919-154">"ClassLibrary1.ChainOne" metni içeren test.txt adlı bir dosyaya göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="47919-154">Consider a file named test.txt that contains the text "ClassLibrary1.ChainOne".</span></span> <span data-ttu-id="47919-155">Çalıştırırsanız `/rejected` eylemiyle `/whitelist` seçeneği önceki örnekten, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="47919-155">If you run the `/rejected` action with the `/whitelist` option on the previous example, it will produce the following output:</span></span>  
  
```  
mefx /file:ClassLibrary1.dll /rejected /whitelist:test.txt  
[Unexpected] ClassLibrary1.AddIn  
ClassLibrary1.ChainOne  
```
