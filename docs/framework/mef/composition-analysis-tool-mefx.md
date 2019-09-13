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
ms.openlocfilehash: f3777627caec7fc0d383804f71d9b7d3f09756fd
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894124"
---
# <a name="composition-analysis-tool-mefx"></a>Bileşim Analiz Aracı (Mefx)
Bileşim çözümleme aracı (Mefx), kitaplık (. dll) ve Managed Extensibility Framework (MEF) parçaları içeren uygulama (. exe) dosyalarını analiz eden bir komut satırı uygulamasıdır. Mefx 'in birincil amacı, geliştiricilere, uygulamanın kendisi için ek bir izleme kodu ekleme gereksinimi olmadan MEF uygulamalarında bileşim başarısızlıklarını tanılamaya yönelik bir yol sağlamaktır. Üçüncü taraf tarafından sağlanan bir kitaplıktan parçaları anlamanıza yardımcı olmak için de kullanışlı olabilir. Bu konu, Mefx 'in nasıl kullanılacağını açıklar ve söz dizimi için bir başvuru sağlar.  
  
<a name="getting_mefx"></a>   
## <a name="getting-mefx"></a>Mefx alma  
 Mefx, [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef/releases/tag/4.0)'de GitHub 'da kullanılabilir. Aracı indirmeniz ve sıkıştırmayı açmanız yeterlidir.  
  
<a name="basic_syntax"></a>   
## <a name="basic-syntax"></a>Temel söz dizimi  
 Mefx, komut satırından aşağıdaki biçimde çağrılır:  
  
```console
mefx [files and directories] [action] [options]  
```  
  
 İlk bağımsız değişken kümesi, analiz için parçaların yükleneceği dosyaları ve dizinleri belirtir. `/file:` Anahtarına sahip bir dosya ve `/directory:` anahtarı olan bir dizin belirtin. Aşağıdaki örnekte gösterildiği gibi birden çok dosya veya dizin belirtebilirsiniz:  
  
```console  
mefx /file:MyAddIn.dll /directory:Program\AddIns [action...]  
```  
  
> [!NOTE]
> Her. dll veya. exe yalnızca bir kez yüklenmelidir. Bir dosya birden çok kez yüklenirse araç yanlış bilgiler döndürebilir.  
  
 Dosya ve dizinlerin listesinden sonra, bir komut ve bu komut için herhangi bir seçeneği belirtmeniz gerekir.  
  
<a name="listing_available_parts"></a>   
## <a name="listing-available-parts"></a>Kullanılabilir bölümleri listeleme  
 Yüklenen dosyalarda belirtilen tüm parçaları listelemek için eyleminikullanın.`/parts` Sonuç, bölüm adlarının basit bir listesidir.  
  
```console
mefx /file:MyAddIn.dll /parts  
MyAddIn.AddIn  
MyAddIn.MemberPart  
```  
  
 Bölümler hakkında daha fazla bilgi için `/verbose` seçeneğini kullanın. Bu, tüm kullanılabilir parçalar için daha fazla bilgi çıktısını alacak. Tek bir bölüm hakkında daha fazla bilgi edinmek için `/type` `/parts`yerine eylemini kullanın.  
  
```console  
mefx /file:MyAddIn.dll /type:MyAddIn.AddIn /verbose  
[Part] MyAddIn.MemberPart from: AssemblyCatalog (Assembly=" MyAddIn, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Export] MyAddIn.MemberPart (ContractName=" MyAddIn.MemberPart")  
```  
  
<a name="listing_imports_and_exports"></a>   
## <a name="listing-imports-and-exports"></a>Içeri aktarmaları ve dışarı aktarmaları listeleme  
 `/imports` Ve`/exports` eylemleri, tüm içeri aktarılan parçaları ve tüm aktarılmış parçaları sırasıyla listeedecektir. Ayrıca, `/importers` veya `/exporters` eylemlerini kullanarak belirli bir türü içeri veya dışarı aktarma bölümlerini de listeleyebilirsiniz.  
  
```console  
mefx /file:MyAddIn.dll /importers:MyAddin.MemberPart  
MyAddin.AddIn  
```  
  
 Bu eylemlere `/verbose` seçeneği de uygulayabilirsiniz.  
  
<a name="finding_rejected_parts"></a>   
## <a name="finding-rejected-parts"></a>Reddedilen parçaları bulma  
 Mevcut parçalar yüklendikten sonra, Mefx bunları oluşturmak için MEF bileşim altyapısını kullanır. Başarıyla birleştirilemeyen bölümler *reddedildi*olarak adlandırılır. Reddedilen tüm parçaları listelemek için `/rejected` eylemini kullanın.  
  
 Reddedilen bölümlerle ilgili ayrıntılı `/verbose` bilgileri yazdırmak için `/rejected` bu seçeneği kullanın. Aşağıdaki örnekte, `ClassLibrary1` dll `MemberPart` , `AddIn` ve`ChainOne` parçalarını içeri aktaran bölümünü içerir. `ChainOne`İçeri `ChainTwo`aktarmalar, `ChainTwo` ancak yok. Bu, reddedildiği `ChainOne` anlamına gelir ve bu da `AddIn` reddedilmesine neden olur.  
  
```console  
mefx /file:ClassLibrary1.dll /rejected /verbose  
```  
  
 Aşağıda, önceki komutun tüm çıktısı gösterilmektedir:  
  
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
  
 İlginç bilgiler, `[Exception]` ve `[Unsuitable]` sonuçlarında yer alır. `[Exception]` Sonuç olarak bir bölümün reddedilme nedeni hakkında bilgi sağlanır. `[Unsuitable]` Sonuç olarak, başka bir şekilde eşleşen bölümün bir içeri aktarmayı doldurması için kullanılması gerektiğini gösterir; bu durumda, bu bölümün kendisi eksik içeri aktarmalar için reddedildi.  
  
<a name="analyzing_primary_causes"></a>   
## <a name="analyzing-primary-causes"></a>Birincil nedenler çözümleniyor  
 Çok sayıda bölüm uzun bir bağımlılık zincirinde bağlanmışsa, en alta yakın bir bölümü içeren bir sorun, tüm zincirin reddedilmesine neden olabilir. Hatanın asıl nedeni her zaman açık olmadığından, bu sorunların tanılanması zor olabilir. Sorunu gidermek için, herhangi bir geçişli reddetme kök nedenini `/causes` bulmayı deneyen eylemini kullanabilirsiniz.  
  
 Önceki örnekte `ChainOne`eylemin kullanılması yalnızca, doldurulmamış içeri aktarma işleminin `AddIn`reddedilme nedeni olan bilgileri listeme. `/causes` Eylem hem normal hem `/verbose` de seçeneklerde kullanılabilir. `/causes`  
  
> [!NOTE]
> Çoğu durumda, Mefx bir basamaklı hatanın kök nedenini tanılayabilir. Ancak, parçaların bir kapsayıcıya programlı olarak eklendiği durumlarda, hiyerarşik kapsayıcılar içeren durumlar veya özel `ExportProvider` uygulamalar içeren durumlar için Mefx, nedeni tanılayamaz. Genel olarak, daha önce açıklanan durumlar mümkün olduğunda kaçınılması gerekir, çünkü hataların genellikle tanılanması zordur.  
  
<a name="white_lists"></a>   
## <a name="white-lists"></a>Beyaz listeler  
 Seçeneği `/whitelist` , reddedilmesi beklenen bölümleri listeleyen bir metin dosyası belirtmenize olanak sağlar. Ardından, beklenmeyen ret ler işaretlenir. Bu, tamamlanmamış bir kitaplığı veya bazı bağımlılıkları eksik olan bir alt kitaplığı çözümlediğinizde yararlı olabilir. `/whitelist` `/rejected` Seçeneği veya`/causes` eylemlerine uygulanabilir.  
  
 "ClassLibrary1. ChainOne" metnini içeren test. txt adlı bir dosya düşünün. `/rejected` Eylemi`/whitelist` önceki örnekteki seçeneğiyle çalıştırırsanız, aşağıdaki çıktıyı üretir:  
  
```console
mefx /file:ClassLibrary1.dll /rejected /whitelist:test.txt  
[Unexpected] ClassLibrary1.AddIn  
ClassLibrary1.ChainOne  
```
