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
# <a name="composition-analysis-tool-mefx"></a>Bileşim Analiz Aracı (Mefx)
Kompozisyon Çözümleme Aracı (Mefx), Yönetilen Genişletilebilirlik Çerçevesi (MEF) parçalarını içeren kitaplık (.dll) ve uygulama (.exe) dosyalarını analiz eden bir komut satırı uygulamasıdır. Mefx'in birincil amacı, geliştiricilere MEF uygulamalarındaki kompozisyon hatalarını uygulamanın kendisine hantal izleme kodu ekleme gereksinimi olmadan tanılamaları için bir yol sağlamaktır. Ayrıca, üçüncü bir taraf tarafından sağlanan bir kitaplıktan parçaları anlamasına yardımcı olmak da yararlı olabilir. Bu konu, Mefx'in nasıl kullanılacağını açıklar ve sözdizimi için bir başvuru sağlar.  
  
<a name="getting_mefx"></a>
## <a name="getting-mefx"></a>Mefx Başlarken  
 Mefx GitHub'da [Yönetilen Genişletilebilirlik Çerçevesi'nde](https://github.com/MicrosoftArchive/mef/releases/tag/4.0)mevcuttur. Sadece indirin ve aracı unzip.  
  
<a name="basic_syntax"></a>
## <a name="basic-syntax"></a>Temel Sözdizimi  
 Mefx komut satırından aşağıdaki biçimde çağrılır:  
  
```console
mefx [files and directories] [action] [options]  
```  
  
 İlk bağımsız değişken kümesi, çözümleme için parçaların yüklendiği dosyaları ve dizinleri belirtir. Anahtarlı `/file:` bir dosya ve anahtarlı bir `/directory:` dizin belirtin. Aşağıdaki örnekte gösterildiği gibi birden çok dosya veya dizin belirtebilirsiniz:  
  
```console  
mefx /file:MyAddIn.dll /directory:Program\AddIns [action...]  
```  
  
> [!NOTE]
> Her .dll veya .exe yalnızca bir kez yüklenmelidir. Bir dosya birden çok kez yüklenirse, araç yanlış bilgileri döndürebilir.  
  
 Dosya ve dizinler listesinden sonra, bir komut ve bu komut için herhangi bir seçenek belirtmeniz gerekir.  
  
<a name="listing_available_parts"></a>
## <a name="listing-available-parts"></a>Kullanılabilir Parçaları Listeleme  
 Yüklenen `/parts` dosyalarda bildirilen tüm parçaları listelemek için eylemi kullanın. Sonuç, parça adlarının basit bir listesidir.  
  
```console
mefx /file:MyAddIn.dll /parts  
MyAddIn.AddIn  
MyAddIn.MemberPart  
```  
  
 Parçalar hakkında daha fazla bilgi `/verbose` için seçeneği kullanın. Bu, kullanılabilir tüm parçalar için daha fazla bilgi elde eder. Tek bir bölüm hakkında daha fazla `/type` bilgi `/parts`almak için eylemi ' yerine kullanın.  
  
```console  
mefx /file:MyAddIn.dll /type:MyAddIn.AddIn /verbose  
[Part] MyAddIn.MemberPart from: AssemblyCatalog (Assembly=" MyAddIn, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Export] MyAddIn.MemberPart (ContractName=" MyAddIn.MemberPart")  
```  
  
<a name="listing_imports_and_exports"></a>
## <a name="listing-imports-and-exports"></a>İthalat ve İhracatı Listeleme  
 Ve `/imports` `/exports` eylemler, sırasıyla tüm içe aktarılan parçaları ve tüm dışa aktarılan parçaları listeler. Ayrıca, belirli bir türü veya `/importers` `/exporters` eylemleri kullanarak içe aktaran veya dışa aktaran parçaları da listeleyebilirsiniz.  
  
```console  
mefx /file:MyAddIn.dll /importers:MyAddin.MemberPart  
MyAddin.AddIn  
```  
  
 Bu eylemler ekimi `/verbose` de uygulayabilirsiniz.  
  
<a name="finding_rejected_parts"></a>
## <a name="finding-rejected-parts"></a>Reddedilen Parçaları Bulma  
 Kullanılabilir parçaları yükledikten sonra, Mefx bunları oluşturmak için MEF kompozisyon motorini kullanır. Başarıyla oluşturulamayan parçalar *reddedildi*olarak adlandırılır. Reddedilen tüm parçaları listelemek `/rejected` için eylemi kullanın.  
  
 Reddedilen parçalar `/verbose` hakkında ayrıntılı `/rejected` bilgi yazdırmak için eylem seçeneğini kullanabilirsiniz. Aşağıdaki örnekte, `ClassLibrary1` DLL ve `AddIn` `ChainOne` parçaları içe `MemberPart` aktaran bölümü içerir. `ChainOne`içe, `ChainTwo` `ChainTwo` ancak yok. Bu, `ChainOne` reddedilmesine neden `AddIn` olan anlamına gelir.  
  
```console  
mefx /file:ClassLibrary1.dll /rejected /verbose  
```  
  
 Aşağıdaki önceki komutun tam çıktısını gösterir:  
  
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
  
 İlginç bilgiler `[Exception]` ve `[Unsuitable]` sonuçlar yer almaktadır. Sonuç, `[Exception]` bir parçanın neden reddedildiği hakkında bilgi sağlar. Sonuç, `[Unsuitable]` başka bir şekilde eşleşen bir parçanın neden bir alma işlemi doldurmak için kullanılamayacağını gösterir; bu durumda, çünkü bu bölüm kendisi eksik ithalat için reddedildi.  
  
<a name="analyzing_primary_causes"></a>
## <a name="analyzing-primary-causes"></a>Birincil Nedenleri Çözümleme  
 Birkaç parça uzun bir bağımlılık zincirine bağlıysa, alta yakın bir parçayı içeren bir sorun tüm zincirin reddedilmesine neden olabilir. Başarısızlığın temel nedeni her zaman açık olmadığından, bu sorunları tanılamak zor olabilir. Soruna yardımcı olmak için, `/causes` basamaklı reddin temel nedenini bulmaya çalışan eylemi kullanabilirsiniz.  
  
 Önceki `/causes` örnekte eylemi kullanarak yalnızca doldurulmamış alma reddinin temel nedeni olan `ChainOne` `AddIn`bilgileri listeler. Eylem `/causes` hem normal hem `/verbose` de seçeneklerde kullanılabilir.  
  
> [!NOTE]
> Çoğu durumda, Mefx basamaklı bir hatanın kök nedenini tanılamak mümkün olacaktır. Ancak, parçaların bir kapsayıcıya programlı olarak eklendiği durumlarda, hiyerarşik `ExportProvider` kapsayıcılar içeren durumlarda veya özel uygulamaları içeren durumlarda, Mefx nedenini tanılamak mümkün olmayacaktır. Genel olarak, hataların tanısı genellikle zor olduğundan, daha önce açıklanan durumlarda mümkün olduğunca kaçınılmalıdır.  
  
<a name="white_lists"></a>
## <a name="white-lists"></a>Beyaz Listeler  
 Bu `/whitelist` seçenek, reddedilmesi beklenen bölümleri listeleyen bir metin dosyası belirtmenizi sağlar. Beklenmeyen reddetmeler daha sonra işaretlenir. Bu, eksik bir kitaplığı veya bazı bağımlılıkları eksik olan bir alt kitaplığı çözümlediğinizde yararlı olabilir. Bu `/whitelist` seçenek eylemlere `/rejected` veya `/causes` eylemlere uygulanabilir.  
  
 "ClassLibrary1.ChainOne" metnini içeren test.txt adlı bir dosya düşünün. `/rejected` Eylemi önceki örnekte `/whitelist` seçenekle çalıştırırsanız, aşağıdaki çıktıyı üretecektir:  
  
```console
mefx /file:ClassLibrary1.dll /rejected /whitelist:test.txt  
[Unexpected] ClassLibrary1.AddIn  
ClassLibrary1.ChainOne  
```
