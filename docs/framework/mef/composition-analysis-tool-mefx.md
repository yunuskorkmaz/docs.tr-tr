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
# <a name="composition-analysis-tool-mefx"></a>Bileşim Analiz Aracı (Mefx)
Bileşim analiz Aracı (Mefx) kitaplığı (.dll) ve uygulama (.exe) dosyalarını içeren Yönetilen Genişletilebilirlik Çerçevesi (MEF) çözümler bir komut satırı uygulamasıdır. Mefx birincil amacı, geliştiricilerin MEF uygulamalarını sıkıcı izleme kodu uygulamaya eklemek için gereksinimi olmadan de birleşim hataları tanılamak için bir yol sağlamaktır. Ayrıca bir üçüncü taraf tarafından sağlanan bir kitaplıktan bölümleri anlamanıza yardımcı olması yararlı olabilir. Bu konuda Mefx kullanmayı açıklar ve sözdizimi için bir başvuru sağlar.  
  
<a name="getting_mefx"></a>   
## <a name="getting-mefx"></a>Mefx alma  
 Github'da Mefx kullanılabilir [Genişletilebilirlik Çerçevesi ile yönetilen](https://github.com/MicrosoftArchive/mef/releases/tag/4.0). Yalnızca karşıdan yükle ve aracı sıkıştırmasını açın.  
  
<a name="basic_syntax"></a>   
## <a name="basic-syntax"></a>Temel sözdizimi  
 Mefx şu biçimde komut satırından çağrılır:  
  
```  
mefx [files and directories] [action] [options]  
```  
  
 Bağımsız değişkenler ilk kümesi, çözümleme için bölümleri yükleneceği dizinlerden ve dosya belirtin. Bir dosya belirtin `/file:` anahtarı ve bir dizinle `/directory:` geçin. Aşağıdaki örnekte gösterildiği gibi birden fazla dosya veya dizinlerin belirtebilirsiniz:  
  
```  
mefx /file:MyAddIn.dll /directory:Program\AddIns [action...]  
```  
  
> [!NOTE]
>  Her .dll veya .exe yalnızca bir kez yüklenmesi. Bir dosyayı birden çok kez yüklenmişse, aracı yanlış bilgileri döndürebilir.  
  
 Dosyalar ve dizinler listesinde sonra bir komut ve bu komut için herhangi bir seçenek belirtmelisiniz.  
  
<a name="listing_available_parts"></a>   
## <a name="listing-available-parts"></a>Kullanılabilir bölümleri listeleme  
 Kullanım `/parts` tüm bölümleri listelemek için eylemi yüklenen dosyalarda bildirildi. Basit bir bölümü adları listesi sonucudur.  
  
```  
mefx /file:MyAddIn.dll /parts  
MyAddIn.AddIn  
MyAddIn.MemberPart  
```  
  
 Bölümleri hakkında daha fazla bilgi için kullanmak `/verbose` seçeneği. Bu, daha fazla bilgi için tüm kullanılabilir bölümleri çıkarır. Tek bir parça hakkında daha fazla bilgi almak için `/type` yerine eylem `/parts`.  
  
```  
mefx /file:MyAddIn.dll /type:MyAddIn.AddIn /verbose  
[Part] MyAddIn.MemberPart from: AssemblyCatalog (Assembly=" MyAddIn, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Export] MyAddIn.MemberPart (ContractName=" MyAddIn.MemberPart")  
```  
  
<a name="listing_imports_and_exports"></a>   
## <a name="listing-imports-and-exports"></a>İçeri ve dışarı aktarmalar listeleme  
 `/imports` Ve `/exports` eylemleri listeler içe aktarılan tüm bölümleri ve tüm dışarı aktarılan bölümleri sırasıyla. Ayrıca, belirli bir tür kullanarak dışarı veya içeri aktarmanız bölümleri listeleyebilirsiniz `/importers` veya `/exporters` eylemler.  
  
```  
mefx /file:MyAddIn.dll /importers:MyAddin.MemberPart  
MyAddin.AddIn  
```  
  
 Ayrıca uygulayabilirsiniz `/verbose` bu eylemleri seçeneği.  
  
<a name="finding_rejected_parts"></a>   
## <a name="finding-rejected-parts"></a>Bulma bölümleri reddetti  
 Mefx MEF bileşim motoru kullanılabilir bölümleri yüklendikten sonra bunları oluşturmak için kullanır. Başarıyla birleştirilemez bölümleri denir *reddetti*. Tüm reddedilen bölümleri listelemek için kullanın `/rejected` eylem.  
  
 Kullanabileceğiniz `/verbose` seçeneğini `/rejected` hakkında ayrıntılı bilgi yazdırmak için eylem bölümleri reddetti. Aşağıdaki örnekte, `ClassLibrary1` DLL içeren `AddIn` kısım, hangi içeri aktarmalar `MemberPart` ve `ChainOne` bölümleri. `ChainOne` Imports `ChainTwo`, ancak `ChainTwo` yok. Bunun anlamı `ChainOne` reddedilir, hangi nedenler `AddIn` reddedilir.  
  
```  
mefx /file:ClassLibrary1.dll /rejected /verbose  
```  
  
 Önceki komutu tam çıktısını gösterir:  
  
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
  
 İlginç bilgi yer `[Exception]` ve `[Unsuitable]` sonuçları. `[Exception]` Sonuç bir bölümü neden reddedildi hakkında bilgi sağlar. `[Unsuitable]` Sonuç gösterir neden bir eşleşen aksi bölümü alma doldurmak için kullanılamadı; bu durumda, bunlar kendisini bu bölümü olduğundan eksik içeri aktarmalar için reddetti.  
  
<a name="analyzing_primary_causes"></a>   
## <a name="analyzing-primary-causes"></a>Birincil çözümleme neden olur.  
 Birkaç bölümden uzun bağımlılığı bağlıysa altına bir bölümünü içeren bir sorun reddedilir ve tüm zincir neden olabilir. Hatanın kök nedeni her zaman açık olduğundan bu sorunları tanılamak zor olabilir. Sorun yardımcı olmak için kullanabileceğiniz `/causes` herhangi bir geçişli reddetme kök nedenini bulmak için girişimde eylem.  
  
 Kullanarak `/causes` önceki örnekte eylem yalnızca bilgi için liste `ChainOne`, doldurulmamış, içeri aktarma olduğu ret kök nedenini `AddIn`. `/causes` Eylemi hem normal kullanılabilir ve `/verbose` seçenekleri.  
  
> [!NOTE]
>  Çoğu durumda, Mefx basamaklı bir hatanın temel nedeni tanılamanıza mümkün olacaktır. Ancak, burada bölümleri eklendi program aracılığıyla bir kapsayıcıya hiyerarşik kapsayıcıları içeren durumlarda durumları veya özel içeren içinde `ExportProvider` uygulamaları Mefx edemeyecek nedenini tanılamak. Genel olarak, hataları tanılamak genellikle zor olduğu gibi daha önce açıklanan durumlarda mümkün olduğunca kaçınılmalıdır.  
  
<a name="white_lists"></a>   
## <a name="white-lists"></a>Beyaz listeleri  
 `/whitelist` Seçeneği reddedilmesi beklenen bölümleri listeleyen bir metin dosyası belirtmenize olanak sağlar. Beklenmeyen redleri sonra işaretlenir. Bir tamamlanmamış kitaplığı veya bazı bağımlılıklar eksik olan bir alt çözümlediğinizde bu yararlı olabilir. `/whitelist` Seçeneği uygulanabilir `/rejected` veya `/causes` eylemler.  
  
 "ClassLibrary1.ChainOne" metnini içeren sınama.txt adlı bir dosyaya göz önünde bulundurun. Çalıştırırsanız `/rejected` eylemiyle `/whitelist` seçeneği önceki örneği, şu çıkışı üretir:  
  
```  
mefx /file:ClassLibrary1.dll /rejected /whitelist:test.txt  
[Unexpected] ClassLibrary1.AddIn  
ClassLibrary1.ChainOne  
```
