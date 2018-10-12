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
ms.openlocfilehash: 4f4f73ec60283e1ddf0fee0beaa76bdb68124698
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49122785"
---
# <a name="resgenexe-resource-file-generator"></a>Resgen.exe (Kaynak Dosya Oluşturucu)
Kaynak Dosya Oluşturucu (Resgen.exe), metin (.txt veya .restext) dosyalarını ve XML tabanlı kaynak biçimi (.resx) dosyalarını, bir çalışma zamanı ikili çalıştırılabilir dosyasına katıştırılabilen veya uydu derlemesi haline getirilebilen ortak dil çalışma zamanı ikili (.resources) dosyalarına dönüştürür. (Bkz [kaynak dosyaları oluşturma](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md).)  
  
 Resgen.exe aşağıdaki görevleri gerçekleştiren genel amaçlı bir kaynak dönüştürme programıdır:  
  
-   .txt veya .restext dosyalarını .resources veya .resx dosyalarına dönüştürür. (.restext dosyalarının biçimi .txt dosyalarının biçimiyle aynıdır. Ancak, .restext uzantısı, kaynak tanımları içeren metin dosyalarını daha kolay belirlemenize yardımcı olur.)  
  
-   .resources dosyalarını metin veya .resx dosyalarına dönüştürür.  
  
-   .resx dosyalarını metin veya .resources dosyalarına dönüştürür.  
  
-   Dize kaynaklarını bir derlemeden kullanıma uygun bir .resw dosyasına ayıklar bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulama.  
  
-   Tek tek adlandırılmış kaynaklara ve çok erişim sağlayan kesin belirlenmiş bir sınıf oluşturur <xref:System.Resources.ResourceManager> örneği.  
  
 Resgen.exe herhangi bir nedenle başarısız olursa, dönüş değeri –1'dir.  
  
 Resgen,exe ile ilgili yardım almak için, hiç seçenek belirtmeden aşağıdaki komutu kullanarak Resgen.exe'ye ilişkin komut sözdizimini ve seçenekleri görüntüleyebilirsiniz:  
  
```  
resgen  
```  
  
 Ayrıca `/?` geçin:  
  
```  
resgen /?  
```  
  
 Resgen, exe ikili .resources dosyaları üretmek için kullanıyorsanız, ikili dosyaları yürütülebilir derlemelere gömmek için bir dil derleyicisi kullanabilirsiniz veya kullanabileceğiniz [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) onları uydu derlemeler içinde derlemek için.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Geliştirici Komut İstemi (veya Windows 7'de Visual Studio Komut İstemi) kullanın. Daha fazla bilgi için [komut istemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
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
|`/define:` *symbol1*[, *symbol2*,...]|İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], metin tabanlı (.txt veya .restext) kaynak dosyalarında koşullu derlemeyi destekler. Varsa *sembol* içinde giriş metin dosyasına eklenen bir simgeye karşılık gelen bir `#ifdef` yapısı, ilişkili dize kaynağı .resources dosyasına eklenir. Giriş metin dosyası içeriyorsa bir `#if !` ile tanımlanmamış bir sembol deyimiyle `/define` anahtarı, ilişkili dize kaynağı .Resources dosyasına eklenir.<br /><br /> `/define` metin olmayan dosyalarla kullanılırsa, göz ardı edilir. Simgeler büyük/küçük harfe duyarlıdır.<br /><br /> Bu seçenek hakkında daha fazla bilgi için bkz. [kaynakları koşullu olarak derleme](#Conditional) bu konuda.|  
|`useSourcePath`|Giriş dosyasının geçerli dizininin göreli dosya yollarını çözmek için kullanılacağını belirtir.|  
|`/compile`|Tek bir toplu işlemde birden çok .resources dosyasına dönüştürmek için birden fazla .resx veya metin dosyası belirtmenize olanak sağlar. Bu seçeneği belirtmezseniz, yalnızca bir giriş dosyası bağımsız değişkeni belirtebilirsiniz. Çıkış dosyaları *filename*.resources.<br /><br /> Bu seçenek kullanılamaz `/str:` seçeneği.<br /><br /> Bu seçenek hakkında daha fazla bilgi için bkz. [derleme veya dönüştürme birden çok dosya](#Multiple) bu konuda.|  
|`/r:``assembly`|Belirtilen derlemedeki meta verilere başvurur. .resx dosyaları dönüştürülürken kullanılır ve Resgen.exe'nin nesne kaynaklarını serileştirmesine veya serilerinin kaldırılmasına olanak sağlar. Benzer `/reference:` veya `/r:` C# ve Visual Basic derleyicileri için Seçenekler.|  
|`filename.extension`|Dönüştürülecek giriş dosyasının adını belirtir. Bu tablodan önce sunulan ilk ve daha uzun komut satırı sözdizimini kullanıyorsanız, `extension` aşağıdakilerden biri olmalıdır:<br /><br /> .txt veya .restext<br /> Bir .resources veya .resx dosyasına dönüştürülecek bir metin dosyası. Metin dosyaları yalnızca dize kaynakları içerebilir. Dosya biçimi hakkında daha fazla bilgi için bkz: "Metin dosyalarındaki kaynaklar" bölümünü [Creating Resource Files](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md).<br /><br /> .resx<br /> Bir .resources veya metin (.txt veya .restext) dosyasına dönüştürülecek XML tabanlı bir kaynak dosyası.<br /><br /> .resources<br /> Bir .resx veya bir metin (.txt veya .restext) dosyasına dönüştürülecek ikili bir kaynak dosyası.<br /><br /> Bu tablodan önce sunulan ikinci ve daha kısa komut satırı sözdizimini kullanıyorsanız, `extension` aşağıdakilerden biri olmalıdır:<br /><br /> .exe veya .dll<br /> Dize kaynakları olan geliştirme kullanmak için bir .resw dosyasına ayıklanacak bir .NET Framework derlemesi (yürütülebilir veya kitaplık) [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalar.|  
|`outputFilename.extension`|Oluşturulacak kaynak dosyasının adını ve türünü belirtir.<br /><br /> Bir .txt, .restext veya .resx dosyasından bir .resources dosyasına dönüştürme yaparken bu bağımsız değişken isteğe bağlıdır. Siz belirtmezseniz `outputFilename`, Resgen.exe giriş .resources uzantısını ekler `filename` ve dosyayı içeren dizine yazar `filename,extension`.<br /><br /> `outputFilename.extension` Bir .resources dosyasından dönüştürme yaparken bağımsız değişkeni zorunludur. Bir .resources dosyasını XML tabanlı bir kaynak dosyasına dönüştürürken, .resx uzantılı bir dosya adı belirtin. Bir .resources dosyasını bir metin dosyasına dönüştürürken, .txt veya .restext uzantılı bir dosya adı belirtin. Bir .resources dosyasını, .resources dosyası yalnızca dize değerleri içerirken bir .txt dosyasına dönüştürmelisiniz.|  
|`outputDirectory`|İçin [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamaları içinde bir .resw dosyasının dizini içindeki dize kaynaklarını içeren belirtir `filename.extension` yazılır. `outputDirectory` önceden var olmalıdır.|  
|`/str:``language[,namespace[,classname[,filename]]]`|Belirtilen programlama dilinde, kesin olarak belirlenmiş kaynak sınıfı dosyası oluşturur `language` seçeneği. `language` Aşağıdaki değişmez değerlerden birini içerebilir:<br /><br /> -C# için: `c#`, `cs`, veya `csharp`.<br />-Visual Basic için: `vb` veya `visualbasic`.<br />-İçin VBScript: `vbs` veya `vbscript`.<br />-İçin C++: `c++`, `mc`, veya `cpp`.<br />-İçin JavaScript: `js`, `jscript`, veya `javascript`.<br /><br /> `namespace` Seçeneği projenin varsayılan ad alanını belirtir `classname` seçeneği üretilen sınıfın adını belirtir ve `filename` seçeneği sınıf dosyasının adını belirtir.<br /><br /> `/str:` Seçenek sayesinde yalnızca bir giriş dosyası ile kullanılamaz `/compile` seçeneği.<br /><br /> Varsa `namespace` belirtildi ancak `classname` sınıf adı çıkış dosyası adından türetilir değil, (örneğin, alt çizgiler noktaların yerini alır). Kesin olarak belirlenmiş kaynaklar sonuç olarak doğru çalışmayabilir. Bunu önlemek için, hem sınıf adı hem de çıkış dosyası adı belirtin.<br /><br /> Bu seçenek hakkında daha fazla bilgi için bkz. [bir türü kesin belirlenmiş kaynak sınıfı oluşturma](#Strong) bu konuda.|  
|`/publicClass`|Kesin belirlenmiş bir kaynak sınıfını bir genel sınıf olarak oluşturur. Varsayılan olarak, kaynak sınıfı, `internal` C# ve `Friend` Visual Basic'te.<br /><br /> Bu seçenek yoksayılır `/str:` seçeneği kullanılamıyor.|  
  
## <a name="resgenexe-and-resource-file-types"></a>Resgen.exe ve Kaynak Dosya Türleri  
 Resgen.exe'nin kaynakları doğru olarak dönüştürmesi için, metin ve .resx dosyalarının doğru biçime uygun olması gerekir.  
  
### <a name="text-txt-and-restext-files"></a>Metin (.txt ve .restext) Dosyaları  
 Metin (.txt veya .restext) dosyaları yalnızca dize kaynakları içerebilir. Dizelerin çeşitli dillere çevrilmiş olması gereken bir uygulama yazıyorsanız, dize kaynakları yararlıdır. Örneğin, uygun dize kaynağını kullanarak, menü dizelerini kolayca bölgeselleştirebilirsiniz. Resgen.exe, ad/değer çiftlerini içeren metin dosyalarını okur; burada, ad kaynağı tanımlayan bir dizedir ve değer kaynak dizesinin kendisidir.  
  
> [!NOTE]
>  .Txt ve .restext dosyalarının biçimi hakkında daha fazla bilgi için bkz: "Metin dosyalarındaki kaynaklar" bölümünü [Creating Resource Files](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md).  
  
 Yalnızca Temel Latince aralığındaki karakterleri (U+007F) içermedikçe, kaynakları içeren bir metin dosyasının UTF-8 veya Unicode (UTF-16) kodlamasıyla kaydedilmesi gerekir. Resgen.exe, ANSI kodlaması kullanılarak kaydedilen bir metin dosyasını işlerken genişletilmiş ANSI karakterlerini kaldırır.  
  
 Resgen.exe, metin dosyasında yinelenen kaynak adlarını denetler. Metin dosyası yinelenen kaynak adları içeriyorsa, Resgen.exe bir uyarı verir ve ikinci değeri yoksayar.  
  
### <a name="resx-files"></a>.resx Dosyaları  
 .resx kaynak dosyası biçimi XML girişlerinden oluşur. Metin dosyalarında olduğu gibi bu XML girdileri içinde dize kaynakları belirtebilirsiniz. .resx dosyalarının metin dosyalarına göre birincil yararlarından birisi, nesneler de belirtebilir veya gömebilir olmanızdır. Bir .resx dosyasını görüntülediğinizde, ikili bilgiler kaynak bildiriminin bir parçası olduğunda, gömülü bir nesnenin (örneğin, bir resim) ikili biçimini görebilirsiniz. Metin dosyalarında olduğu gibi, bir .resx dosyasını bir metin düzenleyicicisiyle (Not Defteri veya Microsoft Word gibi) açabilir ve içeriğini yazabilir, ayrıştırabilir ve değiştirebilirsiniz. Bunun için, XML etiketlerini ve .resx dosyası yapısını iyi bilmenin gerektiğini unutmayın. .Resx dosya biçimi hakkında daha fazla bilgi için bkz: ".resx dosyalarındaki kaynaklar" bölümünü [Creating Resource Files](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md).  
  
 Gömülü dize olmayan nesneler içeren bir .resources dosyası oluşturmak için gereken nesneleri içeren bir .resx dosyasını dönüştürmek için Resgen.exe kullanın ya da nesne kaynakları, tarafından sağlanan yöntemleri çağırarak doğrudan koddan dosyanıza ekleyin <xref:System.Resources.ResourceWriter> sınıf.  
  
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
 Resgen.exe'yi çeşitli yollarla kullanabilirsiniz: bir ikili dosyaya dönüştürmek, kaynak dosya biçimleri arasında dönüştürmek için ve sarmalayan bir sınıf oluşturmak için bir metin veya XML tabanlı kaynak dosyasını derlemek için <xref:System.Resources.ResourceManager> işlevselliği ve kaynaklara erişim sağlar. Bu bölüm, her görevle ilgili ayrıntılı bilgi sağlar:  
  
-   [Kaynakları bir ikili dosyaya derleme](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Compiling)  
  
-   [Kaynak dosya türleri arasında dönüştürme](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Convert)  
  
-   [Derleme veya birden çok dosyayı dönüştürme](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Multiple)  
  
-   [Kaynakları bir .resw dosyasına verme](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Exporting)  
  
-   [Kaynakları koşullu olarak derleme](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Conditional)  
  
-   [Türü kesin belirlenmiş kaynak sınıfı oluşturma](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Strong)  
  
<a name="Compiling"></a>   
### <a name="compiling-resources-into-a-binary-file"></a>Kaynakları Bir İkili Dosyaya Derleme  
 Resgen.exe'nin en yaygın kullanımı, metin tabanlı bir kaynak dosyasını (bir .txt veya .restext dosyası) veya XML tabanlı bir kaynak dosyasını (bir .resx dosyası) bir ikili .resources dosyasına derlemektir. Çıktı dosyası daha sonra bir ana derlemeye bir dil derleyicisi tarafından veya bir uydu derlemesi tarafından eklenebilir [Assembly Linker (AL.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md).  
  
 Bir kaynak dosyasını derlemek için sözdizimi aşağıdaki gibidir:  
  
```  
resgen inputFilename [outputFilename]   
```  
  
 burada parametreler şunlardır:  
  
 `inputFilename`  
 Uzantı dahil, derlenecek dosyanın adı. Resgen.exe yalnızca uzantısı .txt, .restext veya .resx olan dosyaları derler.  
  
 `outputFilename`  
 Çıktı dosyasının adı. Atlarsanız `outputFilename`, Resgen.exe, kök dosya adı ile bir .resources dosyası oluşturur `inputFilename` aynı dizinde `inputFilename`. Varsa `outputFilename` bir dizin yolu içeriyorsa dizin varolmalıdır.  
  
 .resources dosyası için tam olarak belirtilen bir ad alanını, ad alanını dosya adında belirterek ve bir nokta ile kök dosya adından ayırarak belirtirsiniz. Örneğin, varsa `outputFilename` olduğu `MyCompany.Libraries.Strings.resources`, ad alanı MyCompany.Libraries olur.  
  
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
  
 Ayrıca, bir .NET Framework derlemesindeki gömülü kaynakları bir .resw dosyası dönüştürmek için Resgen.exe'yi kullanabilirsiniz [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalar.  
  
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
 Kullanabileceğiniz `/compile` kaynak dosyaların listesini diğerine tek bir işlemde bir biçimden diğerine dönüştürmek için anahtar. Sözdizimi şöyledir:  
  
```  
resgen /compile filename.extension [filename.extension...]  
```  
  
 Aşağıdaki komut, StringResources.txt, TableResources.resw ve ImageResources.resw adlı üç dosyayı StringResources.resources, TableResources.resources ve ImageResources.resources adlı ayrı .resources dosyalarına dönüştürür.  
  
```  
resgen /compile StringResources.txt TableResources.resx ImageResources.resx  
```  
  
<a name="Exporting"></a>   
### <a name="exporting-resources-to-a-resw-file"></a>Kaynakları Bir .resw Dosyasına Verme  
 Geliştiriyorsanız bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulama, var olan bir masaüstü uygulamasından kaynakları kullanmak isteyebilirsiniz. Ancak, iki tür uygulama farklı dosya biçimlerini destekler. Masaüstü uygulamalarında, metin (.txt veya .restext) veya .resx dosyaları içinde kaynaklar ikili .resources dosyalarına derlenir. İçinde [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalarında, .resw dosyaları ikili paket kaynak dizini (PRI) dosyalarına derlenir. Resgen.exe bir yürütülebilir dosya veya bir uydu derleme kaynakları ayıklayarak ve bunları geliştirirken kullanılabilir olan bir veya daha fazla .resw dosyaları yazma bu boşluğu kapatmak için kullanabileceğiniz bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulama.  
  
> [!IMPORTANT]
>  Visual Studio taşınabilir bir kitaplıktaki kaynakları dahil etmek için gereken tüm dönüştürmeleri otomatik olarak işleyen bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulama. Resgen.exe, bir derleme içindeki kaynakları .resw dönüştürmek için dosya biçimi geliştirmek isteyen geliştiricileri ilgilendirir doğrudan kullanarak bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulama Visual Studio dışında.  
  
 Bir derlemeden .resw dosyaları oluşturmak için sözdizimi aşağıdaki gibidir:  
  
```  
resgen filename.extension  [outputDirectory]  
```  
  
 burada parametreler şunlardır:  
  
 `filename.extension`  
 Bir .NET Framework derlemesinin (bir yürütülebilir veya .DLL) adı. Dosya hiç kaynak içermiyorsa, Resgen.exe herhangi bir dosya oluşturmaz.  
  
 `outputDirectory`  
 .resw dosyalarının yazılacağı varolan dizin. Varsa `outputDirectory` olan atlanırsa, .resw dosyaları geçerli dizine yazılır. Resgen.exe, derlemedeki her bir .resources dosyası için bir .resw dosyası oluşturur. .resw dosyasının kök dosya adı, .resources dosyasının kök adı ile aynıdır.  
  
 Aşağıdaki komut, MyApp.exe içinde gömülü her .resources dosyası için Win8Resources dizininde bir .resw dosyası oluşturur:  
  
```  
resgen MyApp.exe Win8Resources  
```  
  
<a name="Conditional"></a>   
### <a name="conditionally-compiling-resources"></a>Kaynakları Koşullu Olarak Derleme  
 İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], Resgen.exe, metin (.txt ve .restext) dosyalarında dize kaynaklarının koşullu derlenmesini destekler. Bu, birden çok oluşturma yapılandırmasında tek bir metin tabanlı dosya kullanmanıza olanak tanır.  
  
 Bir .txt veya .restext dosyasında, kullandığınız `#ifdef`...`#endif` bir simge tanımlanmadıysa ve kullanırsanız, ikili .resources dosyasına bir kaynak eklemek için `#if !`... `#endif` bir simge tanımlanmazsa bir kaynak eklemek için. Derleme zamanında, ardından kullanarak simgeler tanımlarsınız `/define:` seçeneğinin ardından simgeler virgülle ayrılmış bir listesi. Karşılaştırma büyük/küçük harfleri duyarlıdır; tarafından tanımlanan simgelerin `/define` derlenecek metin dosyalarındaki simgelerin eşleşmelidir.  
  
 Örneğin, Uıresources.rext adlı aşağıdaki dosya adında bir dize kaynağı içerir `AppTitle` olup sembolleri adlı bağlı olarak üç değerden birini alabilir `PRODUCTION`, `CONSULT`, veya `RETAIL` tanımlanır.  
  
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
  
 Bu, iki dize kaynağı içeren bir .resources dosyası oluşturur. Değerini `AppTitle` "My danışmanlık proje yöneticisi" bir kaynaktır.  
  
<a name="Strong"></a>   
### <a name="generating-a-strongly-typed-resource-class"></a>Kesin Olarak Belirlenmiş Bir Kaynak Sınıfı Oluşturma  
 Resgen.exe, bir statik salt okunur özellikler kümesi içeren sınıflar oluşturarak kaynaklara erişimi kapsülleyen, kesin olarak belirlenmiş kaynakları destekler. Bu yöntemlerini çağırmak için bir alternatif sağlayan <xref:System.Resources.ResourceManager> doğrudan kaynakları almak için sınıf. Kullanarak türü kesin olarak belirlenmiş kaynak desteğini etkinleştirebilirsiniz `/str` işlevini sarmalayan Resgen.exe, seçeneğinde <xref:System.Resources.Tools.StronglyTypedResourceBuilder> sınıfı. Belirttiğinizde `/str` seçeneği, Resgen.exe'nin çıktısı giriş parametresinde başvurulan kaynaklarla eşleşen kesin olarak belirlenmiş özellikler içeren bir sınıf. Bu sınıf, işlenen dosyada kullanılabilir olan kaynaklara kesin belirlenmiş salt okunur erişim sağlar.  
  
 Kesin belirlenmiş kaynak oluşturmak için sözdizimi aşağıdaki gibidir:  
  
```  
resgen inputFilename [outputFilename] /str:language[,namespace,[classname[,filename]]] [/publicClass]  
```  
  
 Parametreler ve anahtarlar şunlardır:  
  
 `inputFilename`  
 Kendisi için kesin olarak belirlenmiş bir kaynak sınıfı oluşturulacak kaynak dosyasının dosya adı ve uzantısı. Dosya, metin tabanlı, XML-tabanlı veya ikili .resources dosyası olabilir; uzantısı .txt, .restext, .resw veya .resources olabilir.  
  
 `outputFilename`  
 Çıktı dosyasının adı. Varsa `outputFilename` bir dizin yolu içeriyorsa dizin varolmalıdır. Atlarsanız `outputFilename`, Resgen.exe, kök dosya adı ile bir .resources dosyası oluşturur `inputFilename` aynı dizinde `inputFilename`.  
  
 `outputFilename` bir metin tabanlı, XML-tabanlı veya ikili .resources dosyası olabilir. Dosya uzantısını `outputFilename` öğesinin dosya uzantısı farklı `inputFilename`, Resgen.exe Dosya dönüştürmeyi gerçekleştirir.  
  
 Varsa `inputFilename` Resgen.exe Kopyaları .resources dosyasını bir .resources dosyası olması `outputFilename` da bir .resources dosyası olması. Varsa `outputFilename` olan atlanırsa, Resgen.exe üzerine yazar `inputFilename` özdeş bir .resources dosyasını ile.  
  
 *Dil*  
 Kesin olarak belirlenmiş kaynak sınıfı için kaynak kodun üretileceği dil. Olası değerler `cs`, `C#`, ve `csharp` C# kodunu `vb` ve `visualbasic` Visual Basic kodu için `vbs` ve `vbscript` VBScript kodu için ve `c++`, `mc`ve `cpp` C++ kodu için.  
  
 *namespace*  
 Kesin olarak belirlenmiş kaynak sınıfını içeren ad alanı. .resources dosyası ve kaynak sınıfı aynı ad alanına sahip olmalıdır. Ad alanını belirtmekle ilgili bilgi için `outputFilename`, bkz: [kaynakları bir ikili dosyaya derleme](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Compiling). Varsa *ad alanı* olan atlanırsa, kaynak sınıfı bir ad alanında bulunmuyor.  
  
 *ClassName*  
 kesin belirlenmiş kaynak sınıfının adı. Bu, .resources dosyasının kök adına karşılık gelmelidir. Örneğin, Resgen.exe MyCompany.Libraries.Strings.resources adlı bir .resources dosyası üretirse, belirlenmiş kaynak sınıfının adı Strings olur. Varsa *classname* olan atlanırsa, üretilen sınıf kök adından türetilir `outputFilename`. Varsa `outputFilename` olan atlanırsa, üretilen sınıf kök adından türetilir `inputFilename`.  
  
 *ClassName* gömülü boşluklar gibi geçersiz karakterler içeremez. Varsa *classname* gömülü boşluklar içeriyorsa veya *classname* varsayılan olarak oluşturulan *Inputfilename*, ve *Inputfilename* gömülü boşluklar içeriyorsa Resgen.exe tüm geçersiz karakterleri bir alt çizgiyle (_) değiştirir.  
  
 *Dosya adı*  
 Sınıf dosyasının adı.  
  
 `/publicclass`  
 Türü kesin belirlenmiş kaynak sınıfı genel yapar yerine `internal` (C# ' de) veya `Friend` (Visual Basic'te). Bu, kaynaklara, içine gömüldükleri derlemenin dışından erişmeye olanak tanır.  
  
> [!IMPORTANT]
>  Kesin olarak belirlenmiş bir kaynak sınıfı oluşturduğunuzda, .resources dosyanızın adı üretilen kodun ad alanıyla ve sınıf adıyla eşleşmelidir. Ancak, Resgen.exe uyumsuz bir adı olan bir .resources dosyası üretmek seçenekleri belirtmenize olanak verir. Bu davranışa geçici bir çözüm için, çıktı dosyası oluşturulduktan sonra dosyayı yeniden adlandırın.  
  
 Kesin belirlenmiş kaynak sınıfı aşağıdaki üyelere sahiptir:  
  
-   Kesin belirlenmiş kaynak sınıfı örneğini oluşturmak için kullanılabilecek, parametresiz bir oluşturucu.  
  
-   A `static` (C#) veya `Shared` (Visual Basic) ve salt okunur `ResourceManager` döndüren özellik <xref:System.Resources.ResourceManager> kesin olarak belirlenmiş kaynağı yöneten bir örneği.  
  
-   Statik `Culture` kaynak almak için kullanılan kültürü ayarlamanıza olanak tanıyan özellik. Varsayılan olarak, kendi değerdir `null`, geçerli UI kültürünün kullanıldığı anlamına gelir.  
  
-   Bir `static` (C#) veya `Shared` (Visual Basic) ve salt okunur özelliği .resources dosyasındaki her bir kaynak. Özelliğin adı, kaynağının adıdır.  
  
 Örneğin, aşağıdaki komut StringResources.resources StringResources.txt adlı bir kaynak dosyasını derler ve adlı bir sınıf oluşturur `StringResources` içinde bir Visual Basic kaynak kod dosyası kaynağa erişmek için kullanılabilecek StringResources.vb adlı Yöneticisi.  
  
```  
resgen StringResources.txt /str:vb,,StringResources   
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Araçlar](../../../docs/framework/tools/index.md)  
 [Masaüstü Uygulamalarındaki Kaynaklar](../../../docs/framework/resources/index.md)  
 [Kaynak Dosyaları Oluşturma](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)  
 [Al.exe (Bütünleştirilmiş Kod Bağlayıcı)](../../../docs/framework/tools/al-exe-assembly-linker.md)  
 [Komut İstemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
