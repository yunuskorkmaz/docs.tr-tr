---
title: Resgen.exe (Kaynak Dosya Oluşturucu)
ms.date: 03/30/2017
helpviewer_keywords:
- resource files, .resources files
- resource files, .resx files
- resx files (resource files)
- .resources files
- files, converting
- Resource File Generator
- .resx files
- Resgen.exe
- resource files, converting
- converting files, Resource File Generator
- binary resources files
- embedding files in runtime binary executable
ms.assetid: 8ef159de-b660-4bec-9213-c3fbc4d1c6f4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c8a619021f8e398c5c3dfc974b9130ecacb44d4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="resgenexe-resource-file-generator"></a>Resgen.exe (Kaynak Dosya Oluşturucu)
Kaynak Dosya Oluşturucu (Resgen.exe), metin (.txt veya .restext) dosyalarını ve XML tabanlı kaynak biçimi (.resx) dosyalarını, bir çalışma zamanı ikili çalıştırılabilir dosyasına katıştırılabilen veya uydu derlemesi haline getirilebilen ortak dil çalışma zamanı ikili (.resources) dosyalarına dönüştürür. (Bkz [kaynak dosyalar oluşturma](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md).)  
  
 Resgen.exe aşağıdaki görevleri gerçekleştiren genel amaçlı bir kaynak dönüştürme programıdır:  
  
-   .txt veya .restext dosyalarını .resources veya .resx dosyalarına dönüştürür. (.restext dosyalarının biçimi .txt dosyalarının biçimiyle aynıdır. Ancak, .restext uzantısı, kaynak tanımları içeren metin dosyalarını daha kolay belirlemenize yardımcı olur.)  
  
-   .resources dosyalarını metin veya .resx dosyalarına dönüştürür.  
  
-   .resx dosyalarını metin veya .resources dosyalarına dönüştürür.  
  
-   Dize kaynaklarını kullanmak için uygun bir .resw dosyasına bir derlemeden ayıklar bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulama.  
  
-   Adlandırılmış kaynakların ve çok erişim sağlayan kesin türü belirtilmiş bir sınıf oluşturur <xref:System.Resources.ResourceManager> örneği.  
  
 Resgen.exe herhangi bir nedenle başarısız olursa, dönüş değeri –1'dir.  
  
 Resgen,exe ile ilgili yardım almak için, hiç seçenek belirtmeden aşağıdaki komutu kullanarak Resgen.exe'ye ilişkin komut sözdizimini ve seçenekleri görüntüleyebilirsiniz:  
  
```  
resgen  
```  
  
 Aynı zamanda `/?` geçin:  
  
```  
resgen /?  
```  
  
 Resgen, ikili .resources dosyaları oluşturmak için exe kullanıyorsanız, ikili dosyaları yürütülebilir derlemelerine katıştırmak için bir dil derleyici kullanabilirsiniz veya kullanabileceğiniz [derleme bağlayıcı (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) uydu derlemeye derlemesi için.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Geliştirici Komut İstemi (veya Windows 7'de Visual Studio Komut İstemi) kullanın. Daha fazla bilgi için bkz: [komut istemlerini](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
resgen  [/define:symbol1[,symbol2,...]] [/useSourcePath] filename.extension  | /compile filename.extension... [outputFilename.extension] [/r:assembly] [/str:lang[,namespace[,class[,file]]] [/publicclass]]   
```  
  
```  
resgen filename.extension [outputDirectory]  
```  
  
#### <a name="parameters"></a>Parametreler  
  
|Parametre veya anahtar|Açıklama|  
|-------------------------|-----------------|  
|`/define:` *symbol1*[, *Simge2*,...]|İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], koşullu derleme göre metin (.txt veya .restext) kaynak dosyalarını destekler. Varsa *simgesi* giriş metin dosyasında bulunan bir simge karşılık gelen bir `#ifdef` yapı, ilişkili dize kaynağını .resources dosyasında bulunur. Giriş metin dosyası içeriyorsa bir `#if !` tarafından tanımlanmamış bir simge deyimiyle `/define` anahtarı, ilişkili dize kaynağını kaynakları dosyasında bulunur.<br /><br /> `/define` metin dışı dosyalarıyla kullandıysanız göz ardı edilir. Simgeler büyük/küçük harfe duyarlıdır.<br /><br /> Bu seçenek hakkında daha fazla bilgi için bkz: [kaynaklara koşullu derleme](#Conditional) bu konuda daha sonra.|  
|`useSourcePath`|Giriş dosyasının geçerli dizininin göreli dosya yollarını çözmek için kullanılacağını belirtir.|  
|`/compile`|Tek bir toplu işlemde birden çok .resources dosyasına dönüştürmek için birden fazla .resx veya metin dosyası belirtmenize olanak sağlar. Bu seçeneği belirtmezseniz, yalnızca bir giriş dosyası bağımsız değişkeni belirtebilirsiniz. Çıkış dosyaları adlı *filename*.resources.<br /><br /> Bu seçenek kullanılamaz `/str:` seçeneği.<br /><br /> Bu seçenek hakkında daha fazla bilgi için bkz: [derleme veya birden çok dosya dönüştürme](#Multiple) bu konuda daha sonra.|  
|`/r:``assembly`|Belirtilen derlemedeki meta verilere başvurur. .resx dosyaları dönüştürülürken kullanılır ve Resgen.exe'nin nesne kaynaklarını serileştirmesine veya serilerinin kaldırılmasına olanak sağlar. Aşağıdakine benzer `/reference:` veya `/r:` C# ve Visual Basic derleyicileri için Seçenekler.|  
|`filename.extension`|Dönüştürülecek giriş dosyasının adını belirtir. Bu tablo önce sunulan ilk, lengthier komut satırı sözdizimi kullanıyorsanız `extension` şunlardan biri olmalıdır:<br /><br /> .txt veya .restext<br /> Bir .resources veya .resx dosyasına dönüştürülecek bir metin dosyası. Metin dosyaları yalnızca dize kaynakları içerebilir. Dosya biçimi hakkında daha fazla bilgi için "Metin dosyaları kaynaklar" bölümüne bakın [oluşturma kaynak dosyaları](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md).<br /><br /> .resx<br /> Bir .resources veya metin (.txt veya .restext) dosyasına dönüştürülecek XML tabanlı bir kaynak dosyası.<br /><br /> .resources<br /> Bir .resx veya bir metin (.txt veya .restext) dosyasına dönüştürülecek ikili bir kaynak dosyası.<br /><br /> Bu tablo önce sunulan ikinci, kısa komut satırı sözdizimi kullanıyorsanız `extension` aşağıdaki olması gerekir:<br /><br /> .exe veya .dll<br /> Dize kaynakları olan geliştirme kullanımda .resw dosyaya ayıklanacak bir .NET Framework derleme (yürütülebilir dosya veya kitaplığa) [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalar.|  
|`outputFilename.extension`|Oluşturulacak kaynak dosyasının adını ve türünü belirtir.<br /><br /> Bir .txt, .restext veya .resx dosyasından bir .resources dosyasına dönüştürme yaparken bu bağımsız değişken isteğe bağlıdır. Belirtmezseniz, `outputFilename`, Resgen.exe .resources uzantısı girdisi ekler `filename` ve dosyayı içeren dizine yazan `filename,extension`.<br /><br /> `outputFilename.extension` .Resources dosyasından dönüştürülürken bağımsız değişkeni zorunludur. Bir .resources dosyasını XML tabanlı bir kaynak dosyasına dönüştürürken, .resx uzantılı bir dosya adı belirtin. Bir .resources dosyasını bir metin dosyasına dönüştürürken, .txt veya .restext uzantılı bir dosya adı belirtin. Bir .resources dosyasını, .resources dosyası yalnızca dize değerleri içerirken bir .txt dosyasına dönüştürmelisiniz.|  
|`outputDirectory`|İçin [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalar, içinde bir .resw dosya, directory dize kaynaklarını içeren belirtir `filename.extension` yazılır. `outputDirectory` önceden var olmalıdır.|  
|`/str:``language[,namespace[,classname[,filename]]]`|Belirtilen programlama dilinde kesin türü belirtilmiş kaynak sınıfı dosyası oluşturur `language` seçeneği. `language` Aşağıdaki değişmez değerleri birini içerebilir:<br /><br /> -İçin C# ' ta: `c#`, `cs`, veya `csharp`.<br />-İçin Visual Basic: `vb` veya `visualbasic`.<br />-İçin VBScript: `vbs` veya `vbscript`.<br />-İçin C++: `c++`, `mc`, veya `cpp`.<br />-İçin JavaScript: `js`, `jscript`, veya `javascript`.<br /><br /> `namespace` Seçeneği belirtir projenin varsayılan ad alanı, `classname` seçeneği oluşturulan sınıfın adını belirtir ve `filename` seçeneği sınıfı dosya adını belirtir.<br /><br /> `/str:` Seçenek sağlar yalnızca bir giriş dosyası ile kullanılamaz `/compile` seçeneği.<br /><br /> Varsa `namespace` belirtildi ancak `classname` sınıf adı çıktı dosya adından türetilmiş değil, (örneğin, alt çizgi için nokta yerine kullanılır). Kesin olarak belirlenmiş kaynaklar sonuç olarak doğru çalışmayabilir. Bunu önlemek için, hem sınıf adı hem de çıkış dosyası adı belirtin.<br /><br /> Bu seçenek hakkında daha fazla bilgi için bkz: [bir kesin türü belirtilmiş kaynak sınıfı oluşturma](#Strong) bu konuda daha sonra.|  
|`/publicClass`|Kesin belirlenmiş bir kaynak sınıfını bir genel sınıf olarak oluşturur. Varsayılan olarak, kaynak sınıftır `internal` C# ve `Friend` Visual Basic'te.<br /><br /> Bu seçenek yoksayılır `/str:` seçeneği kullanılamıyor.|  
  
## <a name="resgenexe-and-resource-file-types"></a>Resgen.exe ve Kaynak Dosya Türleri  
 Resgen.exe'nin kaynakları doğru olarak dönüştürmesi için, metin ve .resx dosyalarının doğru biçime uygun olması gerekir.  
  
### <a name="text-txt-and-restext-files"></a>Metin (.txt ve .restext) Dosyaları  
 Metin (.txt veya .restext) dosyaları yalnızca dize kaynakları içerebilir. Dizelerin çeşitli dillere çevrilmiş olması gereken bir uygulama yazıyorsanız, dize kaynakları yararlıdır. Örneğin, uygun dize kaynağını kullanarak, menü dizelerini kolayca bölgeselleştirebilirsiniz. Resgen.exe, ad/değer çiftlerini içeren metin dosyalarını okur; burada, ad kaynağı tanımlayan bir dizedir ve değer kaynak dizesinin kendisidir.  
  
> [!NOTE]
>  .Txt ve .restext dosya biçimi hakkında daha fazla bilgi için "Metin dosyaları kaynaklar" bölümüne bakın [oluşturma kaynak dosyaları](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md).  
  
 Yalnızca Temel Latince aralığındaki karakterleri (U+007F) içermedikçe, kaynakları içeren bir metin dosyasının UTF-8 veya Unicode (UTF-16) kodlamasıyla kaydedilmesi gerekir. Resgen.exe, ANSI kodlaması kullanılarak kaydedilen bir metin dosyasını işlerken genişletilmiş ANSI karakterlerini kaldırır.  
  
 Resgen.exe, metin dosyasında yinelenen kaynak adlarını denetler. Metin dosyası yinelenen kaynak adları içeriyorsa, Resgen.exe bir uyarı verir ve ikinci değeri yoksayar.  
  
### <a name="resx-files"></a>.resx Dosyaları  
 .resx kaynak dosyası biçimi XML girişlerinden oluşur. Metin dosyalarında olduğu gibi bu XML girdileri içinde dize kaynakları belirtebilirsiniz. .resx dosyalarının metin dosyalarına göre birincil yararlarından birisi, nesneler de belirtebilir veya gömebilir olmanızdır. Bir .resx dosyasını görüntülediğinizde, ikili bilgiler kaynak bildiriminin bir parçası olduğunda, gömülü bir nesnenin (örneğin, bir resim) ikili biçimini görebilirsiniz. Metin dosyalarında olduğu gibi, bir .resx dosyasını bir metin düzenleyicicisiyle (Not Defteri veya Microsoft Word gibi) açabilir ve içeriğini yazabilir, ayrıştırabilir ve değiştirebilirsiniz. Bunun için, XML etiketlerini ve .resx dosyası yapısını iyi bilmenin gerektiğini unutmayın. .Resx dosyası biçimi hakkında daha fazla bilgi için ".resx dosyaları kaynaklarında" bölümüne bakın [oluşturma kaynak dosyaları](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md).  
  
 Katıştırılmış dize olmayan nesneler içeren bir .resources dosyası oluşturmak için nesneleri içeren bir .resx dosyası dönüştürmek için Resgen.exe kullanın veya nesne kaynakları, tarafından sağlanan yöntemleri çağırarak doğrudan kodunuzdan dosyanıza ekleyin <xref:System.Resources.ResourceWriter> sınıf.  
  
 .resx veya .resources dosyanız nesneler içeriyorsa ve onu bir metin dosyasına dönüştürmek için Resgen.exe'yi kullanırsanız, tüm dize kaynakları doğru şekilde dönüştürülür, fakat dize olmayan nesnelerin veri türleri de dize olarak dosyaya yazılır. Gömülü nesneleri dönüştürmede kaybedersiniz ve Resgen.exe, kaynakları alırken bir hata oluştuğunu bildirir.  
  
### <a name="converting-between-resources-file-types"></a>Kaynak Dosya Türleri Arasında Dönüştürme  
 Farklı kaynak dosya türleri arasında dönüştürme yaptığınızda, Resgen.exe, kaynak ve hedef dosya türlerine bağlı olarak dönüştürmeyi gerçekleştiremeyebilir veya belirli kaynaklarla ilgili bilgileri kaybedebilir. Aşağıdaki tablo, bir kaynak dosya türünden diğerine dönüştürürken başarılı olan dönüşümleri türlerini belirtir.  
  
|Dönüştürme kaynağı|Metin dosyasına|.resx dosyasına|.resw dosyasına|.resources dosyasına|  
|------------------|------------------|-------------------|-------------------|------------------------|  
|Metin (.txt veya .restext) dosyası|--|Sorun yok|Desteklenmez|Sorun yok|  
|.resx dosyası|Dosya dize olmayan kaynaklar (dosya bağlantıları dahil) içeriyorsa, dönüştürme başarısız olur.|--|Desteklenmez|Sorun yok|  
|.resources dosyası|Dosya dize olmayan kaynaklar (dosya bağlantıları dahil) içeriyorsa, dönüştürme başarısız olur.|Sorun yok|Desteklenmez|--|  
|.exe veya .dll derlemesi|Desteklenmez|Desteklenmez|Yalnızca dize kaynakları (yol adları dahil) kaynak olarak tanınır.|Desteklenmez|  
  
## <a name="performing-specific-resgenexe-tasks"></a>Belirli Resgen.exe Görevlerini Gerçekleştirme  
 Resgen.exe çeşitli yollarla kullanabilirsiniz: bir ikili dosyasına, kaynak dosya biçimleri arasında dönüştürme yapmak ve saran bir sınıf oluşturmak için bir metin veya XML tabanlı kaynak dosyası derlemek için <xref:System.Resources.ResourceManager> işlevselliği ve kaynaklara erişim sağlar. Bu bölüm, her görevle ilgili ayrıntılı bilgi sağlar:  
  
-   [İkili bir dosyaya kaynakları derleme](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Compiling)  
  
-   [Kaynak dosya türleri arasında dönüştürme](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Convert)  
  
-   [Derleme veya birden çok dosya dönüştürme](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Multiple)  
  
-   [Kaynakları .resw dosyasına dışarı aktarma](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Exporting)  
  
-   [Kaynaklara koşullu derleme](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Conditional)  
  
-   [Kesin türü belirtilmiş kaynak sınıfı oluşturma](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Strong)  
  
<a name="Compiling"></a>   
### <a name="compiling-resources-into-a-binary-file"></a>Kaynakları Bir İkili Dosyaya Derleme  
 Resgen.exe'nin en yaygın kullanımı, metin tabanlı bir kaynak dosyasını (bir .txt veya .restext dosyası) veya XML tabanlı bir kaynak dosyasını (bir .resx dosyası) bir ikili .resources dosyasına derlemektir. Çıktı dosyası sonra ana bütünleştirilmiş kodunda bir dil derleyici tarafından veya bir uydu derlemesi tarafından katıştırılabilen [derleme bağlayıcı (AL.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md).  
  
 Bir kaynak dosyasını derlemek için sözdizimi aşağıdaki gibidir:  
  
```  
resgen inputFilename [outputFilename]   
```  
  
 burada parametreler şunlardır:  
  
 `inputFilename`  
 Uzantı dahil, derlenecek dosyanın adı. Resgen.exe yalnızca uzantısı .txt, .restext veya .resx olan dosyaları derler.  
  
 `outputFilename`  
 Çıktı dosyasının adı. Atlarsanız `outputFilename`, Resgen.exe kök dosya adı ile bir .resources dosyası oluşturur `inputFilename` aynı dizinde `inputFilename`. Varsa `outputFilename` bir dizin yolu içeren dizini mevcut olması gerekir.  
  
 .resources dosyası için tam olarak belirtilen bir ad alanını, ad alanını dosya adında belirterek ve bir nokta ile kök dosya adından ayırarak belirtirsiniz. Örneğin, varsa `outputFilename` olan `MyCompany.Libraries.Strings.resources`, MyCompany.Libraries ad alanıdır.  
  
 Aşağıdaki komut, Resources.txt dosyasındaki ad/değer çiftlerini okur ve Resources.resources adlı bir ikili .resources dosyası yazar. Çıkış dosyası adı açıkça belirtilmediği için, varsayılan olarak giriş dosyası adıyla aynı adı alır.  
  
```  
resgen Resources.txt   
```  
  
 Aşağıdaki komut, Resources.restext dosyasındaki ad/değer çiftlerini okur ve StringResources.resources adlı bir ikili .resources dosyası yazar.  
  
```  
resgen Resources.restext StringResources.resources  
```  
  
 Aşağıdaki komut, Resources.resx adlı XML tabanlı bir giriş dosyasını okur ve Resources.resources adlı bir ikili .resources dosyası yazar.  
  
```  
resgen Resources.resx Resources.resources  
```  
  
<a name="Convert"></a>   
### <a name="converting-between-resource-file-types"></a>Kaynak Dosya Türleri Arasında Dönüştürme  
 Metin tabanlı veya XML tabanlı kaynak dosyalarını ikili .resources dosyalarına derlemeye ek olarak, Resgen.exe desteklenen herhangi bir dosya türünü desteklenen herhangi bir başka dosya türüne dönüştürebilir. Başka bir deyişle, aşağıdaki dönüştürmeleri gerçekleştirebilir:  
  
-   .txt ve .restext dosyalarını .resx dosyalarına.  
  
-   .resx dosyalarını .txt ve .restext dosyalarına.  
  
-   .resources dosyalarını .txt ve .restext dosyalarına.  
  
-   .resources dosyalarını .resx dosyalarına.  
  
 Sözdizimi, bir önceki bölümde gösterilenle aynıdır.  
  
 Ayrıca, bir .NET Framework derlemesindeki gömülü kaynaklar .resw dosya tor için dönüştürmek için Resgen.exe kullanabilirsiniz [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalar.  
  
 Aşağıdaki komut, bir ikili .resources dosyası olan Resources.resources dosyasını okur ve Resources.resx adlı XML tabanlı bir çıkış dosyası yazar.  
  
```  
resgen Resources.resources Resources.resx  
```  
  
 Aşağıdaki komut, StringResources.txt adlı metin tabanlı bir .resources dosyasını okur ve LibraryResources.resx adlı XML tabanlı bir .resources dosyası yazar. Dize dosyalarını eklemek yerine, .resx dosyası dize olmayan kaynakları depolamak için de kullanılabilir.  
  
```  
resgen StringResources.txt LibraryResources.resx  
```  
  
 Aşağıdaki iki komut Resources.resx adlı XML tabanlı bir .resources dosyasını okur ve Resources.txt ve Resources.restext adlı metin dosyaları yazar. .resx dosyasının gömülü nesneler içermesi durumunda, bu nesnelerin metin dosyalarına doğru şekilde dönüştürülmeyeceğini unutmayın.  
  
```  
resgen Resources.resx Resources.txt  
resgen Resources.resx Resources.restext  
```  
  
<a name="Multiple"></a>   
### <a name="compiling-or-converting-multiple-files"></a>Birden Çok Dosyayı Derleme veya Dönüştürme  
 Kullanabileceğiniz `/compile` tek bir işlemde başka bir kaynak dosyaların bir listesini bir biçimden diğerine dönüştürme için anahtar. Sözdizimi şöyledir:  
  
```  
resgen /compile filename.extension [filename.extension...]  
```  
  
 Aşağıdaki komut, StringResources.txt, TableResources.resw ve ImageResources.resw adlı üç dosyayı StringResources.resources, TableResources.resources ve ImageResources.resources adlı ayrı .resources dosyalarına dönüştürür.  
  
```  
resgen /compile StringResources.txt TableResources.resx ImageResources.resx  
```  
  
<a name="Exporting"></a>   
### <a name="exporting-resources-to-a-resw-file"></a>Kaynakları Bir .resw Dosyasına Verme  
 Geliştirme yapıyorsanız bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulama, var olan bir masaüstü uygulaması kaynaklarını kullanmak isteyebilirsiniz. Ancak, iki tür uygulama farklı dosya biçimlerini destekler. Masaüstü uygulamalarında, metin (.txt veya .restext) veya .resx dosyaları içinde kaynaklar ikili .resources dosyalarına derlenir. İçinde [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalar, .resw dosyaları ikili paket kaynak dizini (PRI) dosyalarına derlenir. Resgen.exe bu boşluğunu kaynakları yürütülebilir bir dosya ya da bir uydu derleme ayıklanması ve geliştirirken kullanılabilir olan bir veya daha fazla .resw dosyalara yazma için kullanabileceğiniz bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulama.  
  
> [!IMPORTANT]
>  Visual Studio otomatik olarak taşınabilir kitaplığa kaynakları eklemek için gerekli tüm dönüştürmeler işleyen bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulama. Bir derlemeyi kaynakları için .resw dönüştürmek için dosya biçimi geliştirmek isteyen geliştiriciler için ilgilendirir doğrudan Resgen.exe kullanarak bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulama Visual Studio dışında.  
  
 Bir derlemeden .resw dosyaları oluşturmak için sözdizimi aşağıdaki gibidir:  
  
```  
resgen filename.extension  [outputDirectory]  
```  
  
 burada parametreler şunlardır:  
  
 `filename.extension`  
 Bir .NET Framework derlemesinin (bir yürütülebilir veya .DLL) adı. Dosya hiç kaynak içermiyorsa, Resgen.exe herhangi bir dosya oluşturmaz.  
  
 `outputDirectory`  
 .resw dosyalarının yazılacağı varolan dizin. Varsa `outputDirectory` olan atlandığında .resw dosyaları geçerli dizine yazılır. Resgen.exe, derlemedeki her bir .resources dosyası için bir .resw dosyası oluşturur. .resw dosyasının kök dosya adı, .resources dosyasının kök adı ile aynıdır.  
  
 Aşağıdaki komut, MyApp.exe içinde gömülü her .resources dosyası için Win8Resources dizininde bir .resw dosyası oluşturur:  
  
```  
resgen MyApp.exe Win8Resources  
```  
  
<a name="Conditional"></a>   
### <a name="conditionally-compiling-resources"></a>Kaynakları Koşullu Olarak Derleme  
 İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], Resgen.exe metin (.txt ve .restext) dosyalarında dize kaynaklarının koşullu derleme destekler. Bu, birden çok oluşturma yapılandırmasında tek bir metin tabanlı dosya kullanmanıza olanak tanır.  
  
 Kullandığınız bir .txt veya .restext dosyasında `#ifdef`...`#endif` bir kaynak ikili .resources dosyasında bir simge tanımlanır ve kullanırsanız dahil etmek için yapı `#if !`... `#endif` bir simge tanımlanmazsa, bir kaynak eklemek için yapı. Derleme zamanında sonra simgeleri kullanarak tanımladığınız `/define:` seçeneğinin ardından simgeleri virgülle ayrılmış listesi tarafından. Karşılaştırma ortası duyarlı; tarafından tanımlanan simgeleri durumunun `/define` derlenecek metin dosyalarında simgelerin harf eşleşmelidir.  
  
 Örneğin, UIResources.rext adlı aşağıdaki dosya adlı bir dize kaynağı içerir `AppTitle` , gerçekleştirebileceğiniz olup simgeleri adlı bağlı olarak üç değerden birini `PRODUCTION`, `CONSULT`, veya `RETAIL` tanımlanır.  
  
```  
#ifdef PRODUCTION  
AppTitle=My Software Company Project Manager   
#endif  
#ifdef CONSULT  
AppTitle=My Consulting Company Project Manager  
#endif  
#ifdef RETAIL  
AppTitle=My Retail Store Project Manager  
#endif  
FileMenuName=File  
```  
  
 Dosya daha sonra aşağıdaki komut kullanılarak bir ikili .resources dosyası içine derlenebilir:  
  
```  
resgen /define:CONSULT UIResources.restext  
```  
  
 Bu, iki dize kaynağı içeren bir .resources dosyası oluşturur. Değeri `AppTitle` "My danışmanlık şirket proje yöneticisi" bir kaynaktır.  
  
<a name="Strong"></a>   
### <a name="generating-a-strongly-typed-resource-class"></a>Kesin Olarak Belirlenmiş Bir Kaynak Sınıfı Oluşturma  
 Resgen.exe, bir statik salt okunur özellikler kümesi içeren sınıflar oluşturarak kaynaklara erişimi kapsülleyen, kesin olarak belirlenmiş kaynakları destekler. Bu yöntemleri çağırmak için bir alternatif sağlayan <xref:System.Resources.ResourceManager> doğrudan kaynakları almak için sınıf. Kesin türü belirtilmiş kaynak desteği kullanarak etkinleştirebilirsiniz `/str` işlevselliğini sarmalar Resgen.exe seçeneğinde <xref:System.Resources.Tools.StronglyTypedResourceBuilder> sınıfı. Belirttiğinizde `/str` Resgen.exe çıktısını seçenektir giriş parametresinde başvurulan kaynaklar eşleşen kesin türü belirtilmiş özellikleri içeren bir sınıf. Bu sınıf, işlenen dosyada kullanılabilir olan kaynaklara kesin belirlenmiş salt okunur erişim sağlar.  
  
 Kesin belirlenmiş kaynak oluşturmak için sözdizimi aşağıdaki gibidir:  
  
```  
resgen inputFilename [outputFilename] /str:language[,namespace,[classname[,filename]]] [/publicClass]  
```  
  
 Parametreler ve anahtarlar şunlardır:  
  
 `inputFilename`  
 Kendisi için kesin olarak belirlenmiş bir kaynak sınıfı oluşturulacak kaynak dosyasının dosya adı ve uzantısı. Dosya, metin tabanlı, XML-tabanlı veya ikili .resources dosyası olabilir; uzantısı .txt, .restext, .resw veya .resources olabilir.  
  
 `outputFilename`  
 Çıktı dosyasının adı. Varsa `outputFilename` bir dizin yolu içeren dizini mevcut olması gerekir. Atlarsanız `outputFilename`, Resgen.exe kök dosya adı ile bir .resources dosyası oluşturur `inputFilename` aynı dizinde `inputFilename`.  
  
 `outputFilename` bir metin tabanlı, XML tabanlı veya ikili .resources dosyası olabilir. Varsa dosya uzantısını `outputFilename` öğesinin dosya uzantısı, farklı `inputFilename`, Resgen.exe dosya dönüştürme gerçekleştirir.  
  
 Varsa `inputFilename` .resources dosyasını varsa Resgen.exe kopyalar bir .resources dosyası `outputFilename` de .resources bir dosyadır. Varsa `outputFilename` olan atlandığında Resgen.exe üzerine yazar `inputFilename` aynı .resources dosyası ile.  
  
 *Dil*  
 Kesin olarak belirlenmiş kaynak sınıfı için kaynak kodun üretileceği dil. Olası değerler şunlardır: `cs`, `C#`, ve `csharp` C# kodunu `vb` ve `visualbasic` Visual Basic kodu için `vbs` ve `vbscript` VBScript kodu ve `c++`, `mc`ve `cpp` C++ kodu için.  
  
 *namespace*  
 Kesin olarak belirlenmiş kaynak sınıfını içeren ad alanı. .resources dosyası ve kaynak sınıfı aynı ad alanına sahip olmalıdır. Ad alanında belirtme hakkında daha fazla bilgi için `outputFilename`, bkz: [derleme kaynakları ikili dosyasına](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Compiling). Varsa *ad alanı* olan atlandığında kaynak sınıfı bir ad alanında bulunmuyor.  
  
 *ClassName*  
 kesin belirlenmiş kaynak sınıfının adı. Bu, .resources dosyasının kök adına karşılık gelmelidir. Örneğin, Resgen.exe MyCompany.Libraries.Strings.resources adlı bir .resources dosyası üretirse, belirlenmiş kaynak sınıfının adı Strings olur. Varsa *classname* olan atlanırsa, oluşturulan sınıfın kök adından türetilmiş `outputFilename`. Varsa `outputFilename` olan atlanırsa, oluşturulan sınıfın kök adından türetilmiş `inputFilename`.  
  
 *ClassName* katıştırılmış boşluklar gibi geçersiz karakterler içeremez. Varsa *classname* katıştırılmış boşluklar içeriyor veya *classname* varsayılan olarak oluşturulan *Inputfilename*, ve *Inputfilename* Katıştırılmış boşluklar içeren Resgen.exe tüm geçersiz karakterler alt çizgi (_) ile değiştirir.  
  
 *Dosya adı*  
 Sınıf dosyasının adı.  
  
 `/publicclass`  
 Kesin türü belirtilmiş kaynak sınıfı ortak yapacağı yerine `internal` (C# ' ta) veya `Friend` (Visual Basic'te). Bu, kaynaklara, içine gömüldükleri derlemenin dışından erişmeye olanak tanır.  
  
> [!IMPORTANT]
>  Kesin olarak belirlenmiş bir kaynak sınıfı oluşturduğunuzda, .resources dosyanızın adı üretilen kodun ad alanıyla ve sınıf adıyla eşleşmelidir. Ancak, Resgen.exe uyumsuz bir adı olan bir .resources dosyası üretmek seçenekleri belirtmenize olanak verir. Bu davranışa geçici bir çözüm için, çıktı dosyası oluşturulduktan sonra dosyayı yeniden adlandırın.  
  
 Kesin belirlenmiş kaynak sınıfı aşağıdaki üyelere sahiptir:  
  
-   Kesin belirlenmiş kaynak sınıfı örneğini oluşturmak için kullanılabilecek, parametresiz bir oluşturucu.  
  
-   A `static` (C#) veya `Shared` (Visual Basic) ve salt okunur `ResourceManager` döndürür özelliği <xref:System.Resources.ResourceManager> kesin olarak belirtilmiş kaynak yönetir örneği.  
  
-   Statik `Culture` kaynak alma işlemi için kullanılan kültür ayarlamanıza olanak tanıyan özellik. Varsayılan değeri olduğu `null`, anlamına geçerli UI kültürü kullanılır.  
  
-   Bir `static` (C#) veya `Shared` (Visual Basic) ve .resources dosyasındaki her bir kaynak için salt okunur özellik. Özelliğin adı, kaynağının adıdır.  
  
 Örneğin, aşağıdaki komutu StringResources.resources StringResources.txt adlı bir kaynak dosyasını derler ve adlı bir sınıf oluşturur `StringResources` bir Visual Basic kaynak kodu dosyasının adlı kaynağa erişmek için kullanılan StringResources.vb Yöneticisi.  
  
```  
resgen StringResources.txt /str:vb,,StringResources   
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Araçlar](../../../docs/framework/tools/index.md)  
 [Masaüstü Uygulamalarındaki Kaynaklar](../../../docs/framework/resources/index.md)  
 [Kaynak Dosyaları Oluşturma](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)  
 [Al.exe (Bütünleştirilmiş Kod Bağlayıcı)](../../../docs/framework/tools/al-exe-assembly-linker.md)  
 [Komut İstemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
