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
# <a name="composition-analysis-tool-mefx"></a>Bileşim Analiz Aracı (Mefx)
Bileşim analiz Aracı (Mefx) kitaplığı (.dll) ve uygulama (.exe) dosyaları Yönetilen Genişletilebilirlik Çerçevesi (MEF) parçalarını içeren bir komut satırı uygulamasıdır. Mefx birincil amacı, geliştiricilerin uygulamaya hantal izleme kodu eklemek için gereksinimi olmadan, MEF uygulamalarında oluşturma hatalarını tanılamak için bir yol sağlamaktır. Ayrıca üçüncü taraf tarafından sağlanan bir kitaplıktan bölümleri yardımcı olması yararlı olabilir. Bu konu, Mefx kullanmayı açıklar ve bir başvuru için kendi sözdizimini sağlar.  
  
<a name="getting_mefx"></a>   
## <a name="getting-mefx"></a>Mefx alma  
 Mefx github'da kullanılabilir [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef/releases/tag/4.0). Yalnızca indirin ve Aracı'nı açın.  
  
<a name="basic_syntax"></a>   
## <a name="basic-syntax"></a>Temel söz dizimi  
 Aşağıdaki biçimde bir komut satırından Mefx çağrılır:  
  
```  
mefx [files and directories] [action] [options]  
```  
  
 İlk bağımsız değişken kümesinin, dosyaları ve analiz için bölümleri yükleneceği dizinlerden belirtin. Bir dosya belirtmek `/file:` anahtarı ve bir dizinle `/directory:` geçin. Aşağıdaki örnekte gösterildiği gibi birden çok dosyayı veya dizinleri belirtebilirsiniz:  
  
```  
mefx /file:MyAddIn.dll /directory:Program\AddIns [action...]  
```  
  
> [!NOTE]
>  Yalnızca bir kez, her .dll veya .exe yüklenmelidir. Bir dosyayı birden çok kez yüklenirse, aracı yanlış bilgi döndürebilir.  
  
 Dosyalar ve dizinler listesinde sonra bir komut ve komutun herhangi bir seçenek belirtmeniz gerekir.  
  
<a name="listing_available_parts"></a>   
## <a name="listing-available-parts"></a>Kullanılabilir bölümleri listeleme  
 Kullanım `/parts` tüm bölümleri listelemek için eylem bildirilen yüklenen dosyaları. Basit bölüm adları listesini sonucudur.  
  
```  
mefx /file:MyAddIn.dll /parts  
MyAddIn.AddIn  
MyAddIn.MemberPart  
```  
  
 Bölümleri hakkında daha fazla bilgi için `/verbose` seçeneği. Bu, daha fazla bilgi için kullanılabilir tüm bölümleri çıkarır. Tek bir bölümü hakkında daha fazla bilgi almak için kullanın `/type` yerine eylem `/parts`.  
  
```  
mefx /file:MyAddIn.dll /type:MyAddIn.AddIn /verbose  
[Part] MyAddIn.MemberPart from: AssemblyCatalog (Assembly=" MyAddIn, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Export] MyAddIn.MemberPart (ContractName=" MyAddIn.MemberPart")  
```  
  
<a name="listing_imports_and_exports"></a>   
## <a name="listing-imports-and-exports"></a>İçeri ve dışarı aktarmalar listeleme  
 `/imports` Ve `/exports` eylemleri listeler içeri aktarılan tüm bölümleri ve tüm dışarı aktarılan bölümleri sırasıyla. Ayrıca belirli bir tür kullanarak dışarı veya içeri aktarın bölümleri listeleyebilirsiniz `/importers` veya `/exporters` eylemler.  
  
```  
mefx /file:MyAddIn.dll /importers:MyAddin.MemberPart  
MyAddin.AddIn  
```  
  
 Ayrıca uygulayabilirsiniz `/verbose` bu eylemler için seçeneği.  
  
<a name="finding_rejected_parts"></a>   
## <a name="finding-rejected-parts"></a>Bulma bölümleri reddetti  
 Mefx MEF bileşim motoru kullanılabilir bölümleri yüklendikten sonra bunları oluşturmak için kullanır. Başarıyla birleştirilemeyen bölümleri denir *reddedilen*. Reddedilen tüm bölümleri listelemek için kullanın `/rejected` eylem.  
  
 Kullanabileceğiniz `/verbose` seçeneğini `/rejected` bölümleri hakkında ayrıntılı bilgi yazdırmak için eylem reddedildi. Aşağıdaki örnekte, `ClassLibrary1` DLL içeren `AddIn` kısım, hangi içeri aktarmalar `MemberPart` ve `ChainOne` bölümleri. `ChainOne` Imports `ChainTwo`, ancak `ChainTwo` yok. Diğer bir deyişle `ChainOne` reddedilir, hangi nedenleri `AddIn` reddedilir.  
  
```  
mefx /file:ClassLibrary1.dll /rejected /verbose  
```  
  
 Önceki komutun tam çıktı aşağıda gösterilmiştir:  
  
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
  
 İlgi çekici bilgiler içerdiği `[Exception]` ve `[Unsuitable]` sonuçları. `[Exception]` Sonucu bir bölümü neden reddedildiği hakkında bilgi sağlar. `[Unsuitable]` Sonuç neden eşleşen başka bir bölümü alma doldurmak için kullanılamadı gösterir; bu durumda, bunlar kendisi bu bölümü olduğundan eksik Imports reddetti.  
  
<a name="analyzing_primary_causes"></a>   
## <a name="analyzing-primary-causes"></a>Birincil çözümleme neden olur.  
 Birkaç bölümden uzun bağımlılık zincirinde bağlıysa, bir bölümü altına ilgili bir sorun reddedilir zincirini neden olabilir. Kök nedenini her zaman açık olmadığından bu sorunların tanılanması zor olabilir. Sorunu çözmek için kullanabileceğiniz `/causes` eylem, hiçbir basamaklı reddetme nedenini bulmaya çalışır.  
  
 Kullanarak `/causes` listesinde yalnızca bilgi için önceki örneğin eylem `ChainOne`, doldurulmamış olan içeri aktarma olan ret kök nedenini `AddIn`. `/causes` Eylem hem normal kullanılabilir ve `/verbose` seçenekleri.  
  
> [!NOTE]
>  Çoğu durumda, Mefx basamaklı hatanın kök nedeni tanılamak mümkün olacaktır. Ancak, burada bölümleri eklendi program aracılığıyla bir kapsayıcıya hiyerarşik kapsayıcılar içeren durumlarda durumları veya özel ilgili olarak `ExportProvider` uygulamaları Mefx gerçekleştiremez nedenini tanılamak. Genel olarak, hataları tanılamak genellikle zor olduğu gibi daha önce açıklandığı gibi durumlarda mümkün olduğunca kaçınılmalıdır.  
  
<a name="white_lists"></a>   
## <a name="white-lists"></a>Beyaz listeleri  
 `/whitelist` Seçeneği reddedilmesi beklenen bölümleri listeleyen bir metin dosyası belirtmenize imkan tanır. Beklenmeyen redleri sonra işaretlenir. Tamamlanmamış bir kitaplığı veya bazı bağımlılıklar eksik olan alt kitaplığı çözümlediğinizde bu yararlı olabilir. `/whitelist` Seçeneği uygulanabilir `/rejected` veya `/causes` eylemler.  
  
 "ClassLibrary1.ChainOne" metni içeren test.txt adlı bir dosyaya göz önünde bulundurun. Çalıştırırsanız `/rejected` eylemiyle `/whitelist` seçeneği önceki örnekten, aşağıdaki çıktıyı üretir:  
  
```  
mefx /file:ClassLibrary1.dll /rejected /whitelist:test.txt  
[Unexpected] ClassLibrary1.AddIn  
ClassLibrary1.ChainOne  
```
