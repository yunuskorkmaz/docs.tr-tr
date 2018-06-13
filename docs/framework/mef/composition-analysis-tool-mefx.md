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
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33392583"
---
# <a name="composition-analysis-tool-mefx"></a><span data-ttu-id="913ea-102">Bileşim Analiz Aracı (Mefx)</span><span class="sxs-lookup"><span data-stu-id="913ea-102">Composition Analysis Tool (Mefx)</span></span>
<span data-ttu-id="913ea-103">Bileşim analiz Aracı (Mefx) kitaplığı (.dll) ve uygulama (.exe) dosyalarını içeren Yönetilen Genişletilebilirlik Çerçevesi (MEF) çözümler bir komut satırı uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="913ea-103">The Composition Analysis Tool (Mefx) is a command-line application that analyzes library (.dll) and application (.exe) files containing Managed Extensibility Framework (MEF) parts.</span></span> <span data-ttu-id="913ea-104">Mefx birincil amacı, geliştiricilerin MEF uygulamalarını sıkıcı izleme kodu uygulamaya eklemek için gereksinimi olmadan de birleşim hataları tanılamak için bir yol sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="913ea-104">The primary purpose of Mefx is to provide developers a way to diagnose composition failures in their MEF applications without the requirement to add cumbersome tracing code to the application itself.</span></span> <span data-ttu-id="913ea-105">Ayrıca bir üçüncü taraf tarafından sağlanan bir kitaplıktan bölümleri anlamanıza yardımcı olması yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="913ea-105">It can also be useful to help understand parts from a library provided by a third party.</span></span> <span data-ttu-id="913ea-106">Bu konuda Mefx kullanmayı açıklar ve sözdizimi için bir başvuru sağlar.</span><span class="sxs-lookup"><span data-stu-id="913ea-106">This topic describes how to use Mefx and provides a reference for its syntax.</span></span>  
  
<a name="getting_mefx"></a>   
## <a name="getting-mefx"></a><span data-ttu-id="913ea-107">Mefx alma</span><span class="sxs-lookup"><span data-stu-id="913ea-107">Getting Mefx</span></span>  
 <span data-ttu-id="913ea-108">Github'da Mefx kullanılabilir [Genişletilebilirlik Çerçevesi ile yönetilen](https://github.com/MicrosoftArchive/mef/releases/tag/4.0).</span><span class="sxs-lookup"><span data-stu-id="913ea-108">Mefx is available on GitHub at [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef/releases/tag/4.0).</span></span> <span data-ttu-id="913ea-109">Yalnızca karşıdan yükle ve aracı sıkıştırmasını açın.</span><span class="sxs-lookup"><span data-stu-id="913ea-109">Simply download and unzip the tool.</span></span>  
  
<a name="basic_syntax"></a>   
## <a name="basic-syntax"></a><span data-ttu-id="913ea-110">Temel sözdizimi</span><span class="sxs-lookup"><span data-stu-id="913ea-110">Basic Syntax</span></span>  
 <span data-ttu-id="913ea-111">Mefx şu biçimde komut satırından çağrılır:</span><span class="sxs-lookup"><span data-stu-id="913ea-111">Mefx is invoked from the command line in the following format:</span></span>  
  
```  
mefx [files and directories] [action] [options]  
```  
  
 <span data-ttu-id="913ea-112">Bağımsız değişkenler ilk kümesi, çözümleme için bölümleri yükleneceği dizinlerden ve dosya belirtin.</span><span class="sxs-lookup"><span data-stu-id="913ea-112">The first set of arguments specify the files and directories from which to load parts for analysis.</span></span> <span data-ttu-id="913ea-113">Bir dosya belirtin `/file:` anahtarı ve bir dizinle `/directory:` geçin.</span><span class="sxs-lookup"><span data-stu-id="913ea-113">Specify a file with the `/file:` switch, and a directory with the `/directory:` switch.</span></span> <span data-ttu-id="913ea-114">Aşağıdaki örnekte gösterildiği gibi birden fazla dosya veya dizinlerin belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="913ea-114">You can specify multiple files or directories, as shown in the following example:</span></span>  
  
```  
mefx /file:MyAddIn.dll /directory:Program\AddIns [action...]  
```  
  
> [!NOTE]
>  <span data-ttu-id="913ea-115">Her .dll veya .exe yalnızca bir kez yüklenmesi.</span><span class="sxs-lookup"><span data-stu-id="913ea-115">Each .dll or .exe should only be loaded one time.</span></span> <span data-ttu-id="913ea-116">Bir dosyayı birden çok kez yüklenmişse, aracı yanlış bilgileri döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="913ea-116">If a file is loaded multiple times, the tool may return incorrect information.</span></span>  
  
 <span data-ttu-id="913ea-117">Dosyalar ve dizinler listesinde sonra bir komut ve bu komut için herhangi bir seçenek belirtmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="913ea-117">After the list of files and directories, you must specify a command, and any options for that command.</span></span>  
  
<a name="listing_available_parts"></a>   
## <a name="listing-available-parts"></a><span data-ttu-id="913ea-118">Kullanılabilir bölümleri listeleme</span><span class="sxs-lookup"><span data-stu-id="913ea-118">Listing Available Parts</span></span>  
 <span data-ttu-id="913ea-119">Kullanım `/parts` tüm bölümleri listelemek için eylemi yüklenen dosyalarda bildirildi.</span><span class="sxs-lookup"><span data-stu-id="913ea-119">Use the `/parts` action to list all the parts declared in the files loaded.</span></span> <span data-ttu-id="913ea-120">Basit bir bölümü adları listesi sonucudur.</span><span class="sxs-lookup"><span data-stu-id="913ea-120">The result is a simple list of part names.</span></span>  
  
```  
mefx /file:MyAddIn.dll /parts  
MyAddIn.AddIn  
MyAddIn.MemberPart  
```  
  
 <span data-ttu-id="913ea-121">Bölümleri hakkında daha fazla bilgi için kullanmak `/verbose` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="913ea-121">For more information about the parts, use the `/verbose` option.</span></span> <span data-ttu-id="913ea-122">Bu, daha fazla bilgi için tüm kullanılabilir bölümleri çıkarır.</span><span class="sxs-lookup"><span data-stu-id="913ea-122">This will output more information for all available parts.</span></span> <span data-ttu-id="913ea-123">Tek bir parça hakkında daha fazla bilgi almak için `/type` yerine eylem `/parts`.</span><span class="sxs-lookup"><span data-stu-id="913ea-123">To get more information about a single part, use the `/type` action instead of `/parts`.</span></span>  
  
```  
mefx /file:MyAddIn.dll /type:MyAddIn.AddIn /verbose  
[Part] MyAddIn.MemberPart from: AssemblyCatalog (Assembly=" MyAddIn, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Export] MyAddIn.MemberPart (ContractName=" MyAddIn.MemberPart")  
```  
  
<a name="listing_imports_and_exports"></a>   
## <a name="listing-imports-and-exports"></a><span data-ttu-id="913ea-124">İçeri ve dışarı aktarmalar listeleme</span><span class="sxs-lookup"><span data-stu-id="913ea-124">Listing Imports and Exports</span></span>  
 <span data-ttu-id="913ea-125">`/imports` Ve `/exports` eylemleri listeler içe aktarılan tüm bölümleri ve tüm dışarı aktarılan bölümleri sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="913ea-125">The `/imports` and `/exports` actions will list all the imported parts and all the exported parts, respectively.</span></span> <span data-ttu-id="913ea-126">Ayrıca, belirli bir tür kullanarak dışarı veya içeri aktarmanız bölümleri listeleyebilirsiniz `/importers` veya `/exporters` eylemler.</span><span class="sxs-lookup"><span data-stu-id="913ea-126">You can also list the parts that import or export a particular type by using the `/importers` or `/exporters` actions.</span></span>  
  
```  
mefx /file:MyAddIn.dll /importers:MyAddin.MemberPart  
MyAddin.AddIn  
```  
  
 <span data-ttu-id="913ea-127">Ayrıca uygulayabilirsiniz `/verbose` bu eylemleri seçeneği.</span><span class="sxs-lookup"><span data-stu-id="913ea-127">You can also apply the `/verbose` option to these actions.</span></span>  
  
<a name="finding_rejected_parts"></a>   
## <a name="finding-rejected-parts"></a><span data-ttu-id="913ea-128">Bulma bölümleri reddetti</span><span class="sxs-lookup"><span data-stu-id="913ea-128">Finding Rejected Parts</span></span>  
 <span data-ttu-id="913ea-129">Mefx MEF bileşim motoru kullanılabilir bölümleri yüklendikten sonra bunları oluşturmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="913ea-129">Once it has loaded the available parts, Mefx uses the MEF composition engine to compose them.</span></span> <span data-ttu-id="913ea-130">Başarıyla birleştirilemez bölümleri denir *reddetti*.</span><span class="sxs-lookup"><span data-stu-id="913ea-130">Parts that cannot be successfully composed are referred to as *rejected*.</span></span> <span data-ttu-id="913ea-131">Tüm reddedilen bölümleri listelemek için kullanın `/rejected` eylem.</span><span class="sxs-lookup"><span data-stu-id="913ea-131">To list all the rejected parts, use the `/rejected` action.</span></span>  
  
 <span data-ttu-id="913ea-132">Kullanabileceğiniz `/verbose` seçeneğini `/rejected` hakkında ayrıntılı bilgi yazdırmak için eylem bölümleri reddetti.</span><span class="sxs-lookup"><span data-stu-id="913ea-132">You can use the `/verbose` option with the `/rejected` action to print detailed information about rejected parts.</span></span> <span data-ttu-id="913ea-133">Aşağıdaki örnekte, `ClassLibrary1` DLL içeren `AddIn` kısım, hangi içeri aktarmalar `MemberPart` ve `ChainOne` bölümleri.</span><span class="sxs-lookup"><span data-stu-id="913ea-133">In the following example, the `ClassLibrary1` DLL contains the `AddIn` part, which imports the `MemberPart` and `ChainOne` parts.</span></span> <span data-ttu-id="913ea-134">`ChainOne` Imports `ChainTwo`, ancak `ChainTwo` yok.</span><span class="sxs-lookup"><span data-stu-id="913ea-134">`ChainOne` imports `ChainTwo`, but `ChainTwo` does not exist.</span></span> <span data-ttu-id="913ea-135">Bunun anlamı `ChainOne` reddedilir, hangi nedenler `AddIn` reddedilir.</span><span class="sxs-lookup"><span data-stu-id="913ea-135">This means that `ChainOne` is rejected, which causes `AddIn` to be rejected.</span></span>  
  
```  
mefx /file:ClassLibrary1.dll /rejected /verbose  
```  
  
 <span data-ttu-id="913ea-136">Önceki komutu tam çıktısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="913ea-136">The following shows the complete output of the previous command:</span></span>  
  
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
  
 <span data-ttu-id="913ea-137">İlginç bilgi yer `[Exception]` ve `[Unsuitable]` sonuçları.</span><span class="sxs-lookup"><span data-stu-id="913ea-137">The interesting information is contained in the `[Exception]` and `[Unsuitable]` results.</span></span> <span data-ttu-id="913ea-138">`[Exception]` Sonuç bir bölümü neden reddedildi hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="913ea-138">The `[Exception]` result provides information about why a part was rejected.</span></span> <span data-ttu-id="913ea-139">`[Unsuitable]` Sonuç gösterir neden bir eşleşen aksi bölümü alma doldurmak için kullanılamadı; bu durumda, bunlar kendisini bu bölümü olduğundan eksik içeri aktarmalar için reddetti.</span><span class="sxs-lookup"><span data-stu-id="913ea-139">The `[Unsuitable]` result indicates why an otherwise-matching part could not be used to fill an import; in this case, because that part was itself rejected for missing imports.</span></span>  
  
<a name="analyzing_primary_causes"></a>   
## <a name="analyzing-primary-causes"></a><span data-ttu-id="913ea-140">Birincil çözümleme neden olur.</span><span class="sxs-lookup"><span data-stu-id="913ea-140">Analyzing Primary Causes</span></span>  
 <span data-ttu-id="913ea-141">Birkaç bölümden uzun bağımlılığı bağlıysa altına bir bölümünü içeren bir sorun reddedilir ve tüm zincir neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="913ea-141">If several parts are linked in a long dependency chain, a problem involving a part near the bottom may cause the entire chain to be rejected.</span></span> <span data-ttu-id="913ea-142">Hatanın kök nedeni her zaman açık olduğundan bu sorunları tanılamak zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="913ea-142">Diagnosing these problems can be difficult because the root cause of the failure is not always obvious.</span></span> <span data-ttu-id="913ea-143">Sorun yardımcı olmak için kullanabileceğiniz `/causes` herhangi bir geçişli reddetme kök nedenini bulmak için girişimde eylem.</span><span class="sxs-lookup"><span data-stu-id="913ea-143">To help with the problem, you can use the `/causes` action, which attempts to find the root cause of any cascading rejection.</span></span>  
  
 <span data-ttu-id="913ea-144">Kullanarak `/causes` önceki örnekte eylem yalnızca bilgi için liste `ChainOne`, doldurulmamış, içeri aktarma olduğu ret kök nedenini `AddIn`.</span><span class="sxs-lookup"><span data-stu-id="913ea-144">Using the `/causes` action on the previous example would list only information for `ChainOne`, whose unfilled import is the root cause of the rejection of `AddIn`.</span></span> <span data-ttu-id="913ea-145">`/causes` Eylemi hem normal kullanılabilir ve `/verbose` seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="913ea-145">The `/causes` action can be used in both normal and `/verbose` options.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="913ea-146">Çoğu durumda, Mefx basamaklı bir hatanın temel nedeni tanılamanıza mümkün olacaktır.</span><span class="sxs-lookup"><span data-stu-id="913ea-146">In most cases, Mefx will be able to diagnose the root cause of a cascading failure.</span></span> <span data-ttu-id="913ea-147">Ancak, burada bölümleri eklendi program aracılığıyla bir kapsayıcıya hiyerarşik kapsayıcıları içeren durumlarda durumları veya özel içeren içinde `ExportProvider` uygulamaları Mefx edemeyecek nedenini tanılamak.</span><span class="sxs-lookup"><span data-stu-id="913ea-147">However, in cases where parts are added programmatically to a container, cases involving hierarchical containers, or cases involving custom `ExportProvider` implementations, Mefx will not be able to diagnose the cause.</span></span> <span data-ttu-id="913ea-148">Genel olarak, hataları tanılamak genellikle zor olduğu gibi daha önce açıklanan durumlarda mümkün olduğunca kaçınılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="913ea-148">In general, the previously described cases should be avoided where possible, as failures are generally difficult to diagnose.</span></span>  
  
<a name="white_lists"></a>   
## <a name="white-lists"></a><span data-ttu-id="913ea-149">Beyaz listeleri</span><span class="sxs-lookup"><span data-stu-id="913ea-149">White Lists</span></span>  
 <span data-ttu-id="913ea-150">`/whitelist` Seçeneği reddedilmesi beklenen bölümleri listeleyen bir metin dosyası belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="913ea-150">The `/whitelist` option enables you to specify a text file that lists parts that are expected to be rejected.</span></span> <span data-ttu-id="913ea-151">Beklenmeyen redleri sonra işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="913ea-151">Unexpected rejections will then be flagged.</span></span> <span data-ttu-id="913ea-152">Bir tamamlanmamış kitaplığı veya bazı bağımlılıklar eksik olan bir alt çözümlediğinizde bu yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="913ea-152">This can be useful when you analyze an incomplete library, or a sub-library that is missing some dependencies.</span></span> <span data-ttu-id="913ea-153">`/whitelist` Seçeneği uygulanabilir `/rejected` veya `/causes` eylemler.</span><span class="sxs-lookup"><span data-stu-id="913ea-153">The `/whitelist` option can be applied to the `/rejected` or `/causes` actions.</span></span>  
  
 <span data-ttu-id="913ea-154">"ClassLibrary1.ChainOne" metnini içeren sınama.txt adlı bir dosyaya göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="913ea-154">Consider a file named test.txt that contains the text "ClassLibrary1.ChainOne".</span></span> <span data-ttu-id="913ea-155">Çalıştırırsanız `/rejected` eylemiyle `/whitelist` seçeneği önceki örneği, şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="913ea-155">If you run the `/rejected` action with the `/whitelist` option on the previous example, it will produce the following output:</span></span>  
  
```  
mefx /file:ClassLibrary1.dll /rejected /whitelist:test.txt  
[Unexpected] ClassLibrary1.AddIn  
ClassLibrary1.ChainOne  
```
