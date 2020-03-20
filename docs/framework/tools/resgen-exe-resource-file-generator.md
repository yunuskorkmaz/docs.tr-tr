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
ms.openlocfilehash: cf79e7c76fd54c6cb6b235251a57aba33c28552b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180341"
---
# <a name="resgenexe-resource-file-generator"></a>Resgen.exe (Kaynak Dosya Oluşturucu)
Kaynak Dosya Oluşturucu (Resgen.exe), metin (.txt veya .restext) dosyalarını ve XML tabanlı kaynak biçimi (.resx) dosyalarını, bir çalışma zamanı ikili çalıştırılabilir dosyasına katıştırılabilen veya uydu derlemesi haline getirilebilen ortak dil çalışma zamanı ikili (.resources) dosyalarına dönüştürür. (Bkz. [Kaynak Dosyaları Oluşturma](../resources/creating-resource-files-for-desktop-apps.md).)  
  
 Resgen.exe aşağıdaki görevleri gerçekleştiren genel amaçlı bir kaynak dönüştürme programıdır:  
  
- .txt veya .restext dosyalarını .resources veya .resx dosyalarına dönüştürür. (.restext dosyalarının biçimi .txt dosyalarının biçimiyle aynıdır. Ancak, .restext uzantısı, kaynak tanımları içeren metin dosyalarını daha kolay belirlemenize yardımcı olur.)  
  
- .resources dosyalarını metin veya .resx dosyalarına dönüştürür.  
  
- .resx dosyalarını metin veya .resources dosyalarına dönüştürür.  
  
- Dize kaynaklarını bir derlemeden Windows 8.x Store uygulamasında kullanıma uygun bir .resw dosyasına ayıklar.  
  
- Tek tek adlandırılmış kaynaklara ve <xref:System.Resources.ResourceManager> örneğine erişim sağlayan güçlü bir şekilde yazılan bir sınıf oluşturur.  
  
 Resgen.exe herhangi bir nedenle başarısız olursa, dönüş değeri –1'dir.  
  
 Resgen.exe ile ilgili yardım almak için, Resgen.exe komutu sözdizimini ve seçeneklerini görüntülemek için hiçbir seçenek belirtilmemiş olarak aşağıdaki komutu kullanabilirsiniz:  
  
```console  
resgen  
```  
  
 `/?` Anahtarı da kullanabilirsiniz:  
  
```console  
resgen /?  
```  
  
 İkili .kaynaklar dosyaları oluşturmak için Resgen.exe kullanıyorsanız, ikili dosyaları çalıştırılabilir derlemelere yerleştirmek için bir dil derleyicisi kullanabilir veya bunları uydu derlemelerine derlemek için [Derleme Bağlayıcısı'nı (Al.exe)](al-exe-assembly-linker.md) kullanabilirsiniz.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7). Daha fazla bilgi için [Komut İstemleri'ne](developer-command-prompt-for-vs.md)bakın.  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
resgen  [-define:symbol1[,symbol2,...]] [/useSourcePath] filename.extension  | /compile filename.extension... [outputFilename.extension] [/r:assembly] [/str:lang[,namespace[,class[,file]]] [/publicclass]]
```  
  
```console  
resgen filename.extension [outputDirectory]  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Parametre veya anahtar|Açıklama|  
|-------------------------|-----------------|  
|`/define:`*sembol1*[, *sembol2*,...]|.NET Framework 4.5'ten başlayarak, metin tabanlı (.txt veya .restext) kaynak dosyalarındaki koşullu derlemeyi destekler. *Sembol,* bir yapı içindeki giriş metni dosyasında yer `#ifdef` alan bir simgeye karşılık geliyorsa, ilişkili dize kaynağı .resources dosyasına dahil edilir. Giriş metin `#if !` `/define` dosyasında anahtar tarafından tanımlanmamış bir simgeiçeren bir deyim varsa, ilişkili dize kaynağı kaynaklar dosyasına dahil edilir.<br /><br /> `/define`metin olmayan dosyalarla kullanılırsa yoksayılır. Simgeler büyük/küçük harfe duyarlıdır.<br /><br /> Bu seçenek hakkında daha fazla bilgi için, bu konunun ilerleyen saatlerinde [Kaynakları Koşullu Olarak Derleme'ye](#Conditional) bakın.|  
|`useSourcePath`|Giriş dosyasının geçerli dizininin göreli dosya yollarını çözmek için kullanılacağını belirtir.|  
|`/compile`|Tek bir toplu işlemde birden çok .resources dosyasına dönüştürmek için birden fazla .resx veya metin dosyası belirtmenize olanak sağlar. Bu seçeneği belirtmezseniz, yalnızca bir giriş dosyası bağımsız değişkeni belirtebilirsiniz. Çıktı dosyaları *filename*.resources olarak adlandırılır.<br /><br /> Bu seçenek `/str:` seçeneği ile kullanılamaz.<br /><br /> Bu seçenek hakkında daha fazla bilgi için, daha sonra bu konuda [Birden Çok Dosyayı Derleme veya Dönüştürme](#Multiple) konusuna bakın.|  
|`/r:` `assembly`|Belirtilen derlemedeki meta verilere başvurur. .resx dosyaları dönüştürülürken kullanılır ve Resgen.exe'nin nesne kaynaklarını serileştirmesine veya serilerinin kaldırılmasına olanak sağlar. C# ve `/reference:` Visual `/r:` Basic derleyicileri için veya seçeneklere benzer.|  
|`filename.extension`|Dönüştürülecek giriş dosyasının adını belirtir. Bu tablodan önce sunulan ilk, daha uzun komut satırı `extension` sözdizimini kullanıyorsanız, aşağıdakilerden biri olmalıdır:<br /><br /> .txt veya .restext<br /> Bir .resources veya .resx dosyasına dönüştürülecek bir metin dosyası. Metin dosyaları yalnızca dize kaynakları içerebilir. Dosya biçimi hakkında bilgi için Kaynak [Dosyaları Oluşturma](../resources/creating-resource-files-for-desktop-apps.md)bölümüne bakın .<br /><br /> .resx<br /> Bir .resources veya metin (.txt veya .restext) dosyasına dönüştürülecek XML tabanlı bir kaynak dosyası.<br /><br /> .resources<br /> Bir .resx veya bir metin (.txt veya .restext) dosyasına dönüştürülecek ikili bir kaynak dosyası.<br /><br /> Bu tablodan önce sunulan ikinci, daha kısa komut satırı `extension` sözdizimini kullanıyorsanız, aşağıdakiler olmalıdır:<br /><br /> .exe veya .dll<br /> Windows 8.x Store uygulamalarının geliştirilmesinde kullanılmak üzere dize kaynakları bir .resw dosyasına çıkarılacak olan bir .NET Framework derlemesi (çalıştırılabilir veya kitaplık).|  
|`outputFilename.extension`|Oluşturulacak kaynak dosyasının adını ve türünü belirtir.<br /><br /> Bir .txt, .restext veya .resx dosyasından bir .resources dosyasına dönüştürme yaparken bu bağımsız değişken isteğe bağlıdır. `outputFilename`Belirtmezseniz, Resgen.exe girdiye `filename` bir .resources uzantısı ekler ve dosyayı içeren `filename,extension`dizine yazar.<br /><br /> Bağımsız `outputFilename.extension` değişken, .resources dosyasından dönüştürme yaparken zorunludur. Bir .resources dosyasını XML tabanlı bir kaynak dosyasına dönüştürürken, .resx uzantılı bir dosya adı belirtin. Bir .resources dosyasını bir metin dosyasına dönüştürürken, .txt veya .restext uzantılı bir dosya adı belirtin. Bir .resources dosyasını, .resources dosyası yalnızca dize değerleri içerirken bir .txt dosyasına dönüştürmelisiniz.|  
|`outputDirectory`|Windows 8.x Store uygulamaları için, dize kaynaklarını içeren bir .resw dosyasının `filename.extension` yazılacağı dizini belirtir. `outputDirectory`zaten var olmalıdır.|  
|`/str:` `language[,namespace[,classname[,filename]]]`|`language` Seçenekte belirtilen programlama dilinde güçlü bir şekilde yazılan kaynak sınıfı dosyası oluşturur. `language`aşağıdaki edebiyatlardan birini oluşabilir:<br /><br /> - `c#`C#için: `cs`, `csharp`, veya .<br />- Visual Basic `vb` `visualbasic`için: veya .<br />- VBScript `vbs` için: veya `vbscript`.<br />- `c++`C++için: `mc`, `cpp`, veya .<br />- JavaScript `js`için: , , `jscript`veya `javascript`.<br /><br /> Seçenek `namespace` projenin varsayılan ad alanını belirtir, `classname` seçenek oluşturulan sınıfın adını belirtir ve `filename` seçenek sınıf dosyasının adını belirtir.<br /><br /> Bu `/str:` seçenek yalnızca bir giriş dosyasına izin verir, bu nedenle `/compile` seçenekle kullanılamaz.<br /><br /> Belirtilmiş `namespace` sayılsa da `classname` belirtilmemişse, sınıf adı çıktı dosyası adından türetilir (örneğin, alt çizerler dönemlerin yerine geçer). Kesin olarak belirlenmiş kaynaklar sonuç olarak doğru çalışmayabilir. Bunu önlemek için, hem sınıf adı hem de çıkış dosyası adı belirtin.<br /><br /> Bu seçenek hakkında daha fazla bilgi için, bu konunun ilerleyen saatlerinde [Güçlü Bir Şekilde Yazılan Kaynak Sınıfı Oluşturma](#Strong) konusuna bakın.|  
|`/publicClass`|Kesin belirlenmiş bir kaynak sınıfını bir genel sınıf olarak oluşturur. Varsayılan olarak, kaynak `internal` sınıfı C# `Friend` ve Visual Basic'tedir.<br /><br /> Seçenek kullanılmazsa `/str:` bu seçenek yoksayılır.|  
  
## <a name="resgenexe-and-resource-file-types"></a>Resgen.exe ve Kaynak Dosya Türleri  
 Resgen.exe'nin kaynakları doğru olarak dönüştürmesi için, metin ve .resx dosyalarının doğru biçime uygun olması gerekir.  
  
### <a name="text-txt-and-restext-files"></a>Metin (.txt ve .restext) Dosyaları  
 Metin (.txt veya .restext) dosyaları yalnızca dize kaynakları içerebilir. Dizelerin çeşitli dillere çevrilmiş olması gereken bir uygulama yazıyorsanız, dize kaynakları yararlıdır. Örneğin, uygun dize kaynağını kullanarak, menü dizelerini kolayca bölgeselleştirebilirsiniz. Resgen.exe, ad/değer çiftlerini içeren metin dosyalarını okur; burada, ad kaynağı tanımlayan bir dizedir ve değer kaynak dizesinin kendisidir.  
  
> [!NOTE]
> .txt ve .restext dosyalarının biçimi hakkında bilgi için Kaynak Dosyaları [Oluşturma](../resources/creating-resource-files-for-desktop-apps.md)bölümüne bakın.  
  
 Yalnızca Temel Latince aralığındaki karakterleri (U+007F) içermedikçe, kaynakları içeren bir metin dosyasının UTF-8 veya Unicode (UTF-16) kodlamasıyla kaydedilmesi gerekir. Resgen.exe, ANSI kodlaması kullanılarak kaydedilen bir metin dosyasını işlerken genişletilmiş ANSI karakterlerini kaldırır.  
  
 Resgen.exe, metin dosyasında yinelenen kaynak adlarını denetler. Metin dosyası yinelenen kaynak adları içeriyorsa, Resgen.exe bir uyarı verir ve ikinci değeri yoksayar.  
  
### <a name="resx-files"></a>.resx Dosyaları  
 .resx kaynak dosyası biçimi XML girişlerinden oluşur. Metin dosyalarında olduğu gibi bu XML girdileri içinde dize kaynakları belirtebilirsiniz. .resx dosyalarının metin dosyalarına göre birincil yararlarından birisi, nesneler de belirtebilir veya gömebilir olmanızdır. Bir .resx dosyasını görüntülediğinizde, ikili bilgiler kaynak bildiriminin bir parçası olduğunda, gömülü bir nesnenin (örneğin, bir resim) ikili biçimini görebilirsiniz. Metin dosyalarında olduğu gibi, bir .resx dosyasını bir metin düzenleyicicisiyle (Not Defteri veya Microsoft Word gibi) açabilir ve içeriğini yazabilir, ayrıştırabilir ve değiştirebilirsiniz. Bunun için, XML etiketlerini ve .resx dosyası yapısını iyi bilmenin gerektiğini unutmayın. .resx dosya biçimi hakkında daha fazla bilgi için Kaynak Dosyaları Oluşturma bölümünün [".resx](../resources/creating-resource-files-for-desktop-apps.md)Dosyalarındaki Kaynaklar" bölümüne bakın.  
  
 Katıştırılmış nonstring nesneleri içeren bir .resources dosyası oluşturmak için, nesneleri içeren bir .resx dosyasını dönüştürmek için Resgen.exe'yi kullanmanız veya <xref:System.Resources.ResourceWriter> sınıf tarafından sağlanan yöntemleri çağırarak nesne kaynaklarını doğrudan koddan dosyanıza eklemeniz gerekir.  
  
 .resx veya .resources dosyanız nesneler içeriyorsa ve onu bir metin dosyasına dönüştürmek için Resgen.exe'yi kullanırsanız, tüm dize kaynakları doğru şekilde dönüştürülür, fakat dize olmayan nesnelerin veri türleri de dize olarak dosyaya yazılır. Gömülü nesneleri dönüştürmede kaybedersiniz ve Resgen.exe, kaynakları alırken bir hata oluştuğunu bildirir.  
  
### <a name="converting-between-resources-file-types"></a>Kaynak Dosya Türleri Arasında Dönüştürme  
 Farklı kaynak dosya türleri arasında dönüştürme yaptığınızda, Resgen.exe, kaynak ve hedef dosya türlerine bağlı olarak dönüştürmeyi gerçekleştiremeyebilir veya belirli kaynaklarla ilgili bilgileri kaybedebilir. Aşağıdaki tablo, bir kaynak dosya türünden diğerine dönüştürürken başarılı olan dönüşümleri türlerini belirtir.  
  
|Dönüştürme kaynağı|Metin dosyasına|.resx dosyasına|.resw dosyasına|.resources dosyasına|  
|------------------|------------------|-------------------|-------------------|------------------------|  
|Metin (.txt veya .restext) dosyası|--|Sorun yok|Desteklenmiyor|Sorun yok|  
|.resx dosyası|Dosya dize olmayan kaynaklar (dosya bağlantıları dahil) içeriyorsa, dönüştürme başarısız olur.|--|Desteklenmiyor|Sorun yok|  
|.resources dosyası|Dosya dize olmayan kaynaklar (dosya bağlantıları dahil) içeriyorsa, dönüştürme başarısız olur.|Sorun yok|Desteklenmiyor|--|  
|.exe veya .dll derlemesi|Desteklenmiyor|Desteklenmiyor|Yalnızca dize kaynakları (yol adları dahil) kaynak olarak tanınır.|Desteklenmiyor|  
  
## <a name="performing-specific-resgenexe-tasks"></a>Belirli Resgen.exe Görevlerini Gerçekleştirme  
 Resgen.exe'yi farklı şekillerde kullanabilirsiniz: metin tabanlı veya XML tabanlı bir kaynak dosyasını ikili dosyaya derlemek, kaynak dosyası <xref:System.Resources.ResourceManager> biçimleri arasında dönüştürme yapmak ve işlevselliği saran ve kaynaklara erişim sağlayan bir sınıf oluşturmak. Bu bölüm, her görevle ilgili ayrıntılı bilgi sağlar:  
  
- [Kaynakları Bir İkili Dosyaya Derleme](resgen-exe-resource-file-generator.md#Compiling)  
  
- [Kaynak Dosya Türleri Arasında Dönüştürme](resgen-exe-resource-file-generator.md#Convert)  
  
- [Birden Çok Dosyayı Derleme veya Dönüştürme](resgen-exe-resource-file-generator.md#Multiple)  
  
- [Kaynakları Bir .resw Dosyasına Verme](resgen-exe-resource-file-generator.md#Exporting)  
  
- [Kaynakları Koşullu Olarak Derleme](resgen-exe-resource-file-generator.md#Conditional)  
  
- [Kesin Olarak Belirlenmiş Bir Kaynak Sınıfı Oluşturma](resgen-exe-resource-file-generator.md#Strong)  
  
<a name="Compiling"></a>
### <a name="compiling-resources-into-a-binary-file"></a>Kaynakları Bir İkili Dosyaya Derleme  
 Resgen.exe'nin en yaygın kullanımı, metin tabanlı bir kaynak dosyasını (bir .txt veya .restext dosyası) veya XML tabanlı bir kaynak dosyasını (bir .resx dosyası) bir ikili .resources dosyasına derlemektir. Çıktı dosyası daha sonra bir dil derleyicisi tarafından bir ana derleme veya [Assembly Linker (AL.exe)](al-exe-assembly-linker.md)tarafından uydu derlemek gömülü olabilir.  
  
 Bir kaynak dosyasını derlemek için sözdizimi aşağıdaki gibidir:  
  
```console  
resgen inputFilename [outputFilename]
```  
  
 burada parametreler şunlardır:  
  
 `inputFilename`  
 Uzantı dahil, derlenecek dosyanın adı. Resgen.exe yalnızca uzantısı .txt, .restext veya .resx olan dosyaları derler.  
  
 `outputFilename`  
 Çıktı dosyasının adı. Eğer atlarsanız, `outputFilename`Resgen.exe aynı dizinde kök dosya adı `inputFilename` içeren bir .resources dosyası `inputFilename`oluşturur. Bir `outputFilename` dizin yolu içeriyorsa, dizin var olmalıdır.  
  
 .resources dosyası için tam olarak belirtilen bir ad alanını, ad alanını dosya adında belirterek ve bir nokta ile kök dosya adından ayırarak belirtirsiniz. Örneğin, ad `outputFilename` `MyCompany.Libraries.Strings.resources`alanı MyCompany.Libraries ise.  
  
 Aşağıdaki komut, Resources.txt dosyasındaki ad/değer çiftlerini okur ve Resources.resources adlı bir ikili .resources dosyası yazar. Çıkış dosyası adı açıkça belirtilmediği için, varsayılan olarak giriş dosyası adıyla aynı adı alır.  
  
```console  
resgen Resources.txt
```  
  
 Aşağıdaki komut, Resources.restext dosyasındaki ad/değer çiftlerini okur ve StringResources.resources adlı bir ikili .resources dosyası yazar.  
  
```console  
resgen Resources.restext StringResources.resources  
```  
  
 Aşağıdaki komut, Resources.resx adlı XML tabanlı bir giriş dosyasını okur ve Resources.resources adlı bir ikili .resources dosyası yazar.  
  
```console  
resgen Resources.resx Resources.resources  
```  
  
<a name="Convert"></a>
### <a name="converting-between-resource-file-types"></a>Kaynak Dosya Türleri Arasında Dönüştürme  
 Metin tabanlı veya XML tabanlı kaynak dosyalarını ikili .resources dosyalarına derlemeye ek olarak, Resgen.exe desteklenen herhangi bir dosya türünü desteklenen herhangi bir başka dosya türüne dönüştürebilir. Başka bir deyişle, aşağıdaki dönüştürmeleri gerçekleştirebilir:  
  
- .txt ve .restext dosyalarını .resx dosyalarına.  
  
- .resx dosyalarını .txt ve .restext dosyalarına.  
  
- .resources dosyalarını .txt ve .restext dosyalarına.  
  
- .resources dosyalarını .resx dosyalarına.  
  
 Sözdizimi, bir önceki bölümde gösterilenle aynıdır.  
  
 Ayrıca, .NET Framework derlemesindeki gömülü kaynakları .resw dosyası tor Windows 8.x Store uygulamalarına dönüştürmek için Resgen.exe'yi kullanabilirsiniz.  
  
 Aşağıdaki komut, bir ikili .resources dosyası olan Resources.resources dosyasını okur ve Resources.resx adlı XML tabanlı bir çıkış dosyası yazar.  
  
```console  
resgen Resources.resources Resources.resx  
```  
  
 Aşağıdaki komut, StringResources.txt adlı metin tabanlı bir .resources dosyasını okur ve LibraryResources.resx adlı XML tabanlı bir .resources dosyası yazar. Dize dosyalarını eklemek yerine, .resx dosyası dize olmayan kaynakları depolamak için de kullanılabilir.  
  
```console  
resgen StringResources.txt LibraryResources.resx  
```  
  
 Aşağıdaki iki komut Resources.resx adlı XML tabanlı bir .resources dosyasını okur ve Resources.txt ve Resources.restext adlı metin dosyaları yazar. .resx dosyasının gömülü nesneler içermesi durumunda, bu nesnelerin metin dosyalarına doğru şekilde dönüştürülmeyeceğini unutmayın.  
  
```console  
resgen Resources.resx Resources.txt  
resgen Resources.resx Resources.restext  
```  
  
<a name="Multiple"></a>
### <a name="compiling-or-converting-multiple-files"></a>Birden Çok Dosyayı Derleme veya Dönüştürme  
 Tek bir `/compile` işlemde kaynak dosyaları listesini bir biçimden diğerine dönüştürmek için anahtarı kullanabilirsiniz. Söz dizimi aşağıdaki gibidir:  
  
```console  
resgen /compile filename.extension [filename.extension...]  
```  
  
 Aşağıdaki komut, StringResources.txt, TableResources.resw ve ImageResources.resw adlı üç dosyayı StringResources.resources, TableResources.resources ve ImageResources.resources adlı ayrı .resources dosyalarına dönüştürür.  
  
```console  
resgen /compile StringResources.txt TableResources.resx ImageResources.resx  
```  
  
<a name="Exporting"></a>
### <a name="exporting-resources-to-a-resw-file"></a>Kaynakları Bir .resw Dosyasına Verme  
 Bir Windows 8.x Store uygulaması geliştiriyorsanız, kaynakları varolan bir masaüstü uygulamasından kullanmak isteyebilirsiniz. Ancak, iki tür uygulama farklı dosya biçimlerini destekler. Masaüstü uygulamalarında, metin (.txt veya .restext) veya .resx dosyaları içinde kaynaklar ikili .resources dosyalarına derlenir. Windows 8.x Store uygulamalarında ,resw dosyaları ikili paket kaynak dizini (PRI) dosyalarında derlenir. Bir çalıştırılabilir veya uydu derlemesi kaynakları ayıklayarak ve bunları bir Windows 8.x Store uygulaması geliştirirken kullanılabilecek bir veya daha fazla .resw dosyasına yazarak bu boşluğu kapatmak için Resgen.exe'yi kullanabilirsiniz.  
  
> [!IMPORTANT]
> Visual Studio, taşınabilir kitaplıktaki kaynakları windows 8.x Store uygulamasına birleştirmek için gereken tüm dönüşümleri otomatik olarak işler. Bir derlemedeki kaynakları .resw dosya biçimine dönüştürmek için doğrudan Resgen.exe'yi kullanmak yalnızca Visual Studio dışında bir Windows 8.x Store uygulaması geliştirmek isteyen geliştiricilerin ilgisini çekecektir.  
  
 Bir derlemeden .resw dosyaları oluşturmak için sözdizimi aşağıdaki gibidir:  
  
```console  
resgen filename.extension  [outputDirectory]  
```  
  
 burada parametreler şunlardır:  
  
 `filename.extension`  
 Bir .NET Framework derlemesinin (bir yürütülebilir veya .DLL) adı. Dosya hiç kaynak içermiyorsa, Resgen.exe herhangi bir dosya oluşturmaz.  
  
 `outputDirectory`  
 .resw dosyalarının yazılacağı varolan dizin. `outputDirectory` Atlanırsa, .resw dosyaları geçerli dizine yazılır. Resgen.exe, derlemedeki her bir .resources dosyası için bir .resw dosyası oluşturur. .resw dosyasının kök dosya adı, .resources dosyasının kök adı ile aynıdır.  
  
 Aşağıdaki komut, MyApp.exe içinde gömülü her .resources dosyası için Win8Resources dizininde bir .resw dosyası oluşturur:  
  
```console  
resgen MyApp.exe Win8Resources  
```  
  
<a name="Conditional"></a>
### <a name="conditionally-compiling-resources"></a>Kaynakları Koşullu Olarak Derleme  
 .NET Framework 4.5 ile başlayarak, Resgen.exe metin (.txt ve .restext) dosyalarında dize kaynaklarının koşullu derlemesini destekler. Bu, birden çok oluşturma yapılandırmasında tek bir metin tabanlı dosya kullanmanıza olanak tanır.  
  
 Bir .txt veya .restext dosyasında, `#ifdef`...`#endif` bir sembol tanımlanırsa ikili .kaynaklar dosyasına bir kaynak eklemek `#if !`için yapı ve ... `#endif` bir sembol tanımlanmamışsa bir kaynak eklemek için yapı. Derleme zamanında, virgülle sınırlı semboller `/define:` listesini izleyen seçeneği kullanarak sembolleri tanımlarsınız. Karşılaştırma kasaya duyarlıdır; tarafından `/define` tanımlanan sembollerin durumu, derlenecek metin dosyalarındaki sembollerin durumuyla eşleşmelidir.  
  
 Örneğin, `AppTitle` UIResources.rext adlı aşağıdaki dosya, sembollerin adlandırılmış `PRODUCTION` `CONSULT`veya `RETAIL` tanımlı olup olmadığına bağlı olarak üç değerden birini alabilen bir dize kaynağı içerir.  
  
```text
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
  
```console  
resgen /define:CONSULT UIResources.restext  
```  
  
 Bu, iki dize kaynağı içeren bir .resources dosyası oluşturur. Kaynağın `AppTitle` değeri "Danışmanlık Şirketi Proje Müdürüm"dür.  
  
<a name="Strong"></a>
### <a name="generating-a-strongly-typed-resource-class"></a>Kesin Olarak Belirlenmiş Bir Kaynak Sınıfı Oluşturma  
 Resgen.exe, bir statik salt okunur özellikler kümesi içeren sınıflar oluşturarak kaynaklara erişimi kapsülleyen, kesin olarak belirlenmiş kaynakları destekler. Bu, kaynak almak için sınıfın <xref:System.Resources.ResourceManager> yöntemlerini doğrudan çağırmak için bir alternatif sağlar. Sınıfın işlevselliğini saran `/str` Resgen.exe'deki seçeneği kullanarak güçlü bir şekilde yazılan kaynak desteğini etkinleştirebilirsiniz. <xref:System.Resources.Tools.StronglyTypedResourceBuilder> `/str` Seçeneği belirttiğiniz zaman, Resgen.exe çıktısı, giriş parametresinde başvurulan kaynaklarla eşleşen güçlü bir şekilde yazılmış özellikler içeren bir sınıftır. Bu sınıf, işlenen dosyada kullanılabilir olan kaynaklara kesin belirlenmiş salt okunur erişim sağlar.  
  
 Kesin belirlenmiş kaynak oluşturmak için sözdizimi aşağıdaki gibidir:  
  
```console  
resgen inputFilename [outputFilename] /str:language[,namespace,[classname[,filename]]] [/publicClass]  
```  
  
 Parametreler ve anahtarlar şunlardır:  
  
 `inputFilename`  
 Kendisi için kesin olarak belirlenmiş bir kaynak sınıfı oluşturulacak kaynak dosyasının dosya adı ve uzantısı. Dosya, metin tabanlı, XML-tabanlı veya ikili .resources dosyası olabilir; uzantısı .txt, .restext, .resw veya .resources olabilir.  
  
 `outputFilename`  
 Çıktı dosyasının adı. Bir `outputFilename` dizin yolu içeriyorsa, dizin var olmalıdır. Eğer atlarsanız, `outputFilename`Resgen.exe aynı dizinde kök dosya adı `inputFilename` içeren bir .resources dosyası `inputFilename`oluşturur.  
  
 `outputFilename`metin tabanlı, XML tabanlı veya ikili .kaynaklar dosyası olabilir. Dosya uzantısı dosya `outputFilename` uzantısı `inputFilename`farklıysa, Resgen.exe dosya dönüştürme gerçekleştirir.  
  
 Bir `inputFilename` .resources dosyasıysa, Resgen.exe .resources dosyasını da bir .resources dosyasıysa `outputFilename` kopyalar. `outputFilename` Atlanırsa, Resgen.exe aynı .resources dosyasıyla üzerine yazar. `inputFilename`  
  
 *Dil*  
 Kesin olarak belirlenmiş kaynak sınıfı için kaynak kodun üretileceği dil. `cs`Olası değerler, `C#`C# kodu `csharp` `vb` ve `visualbasic` Visual Basic kodu `vbs` `vbscript` ve VBScript kodu `c++` `mc`ve `cpp` C++ kodu içindir.  
  
 *Namespace*  
 Kesin olarak belirlenmiş kaynak sınıfını içeren ad alanı. .resources dosyası ve kaynak sınıfı aynı ad alanına sahip olmalıdır. Ad alanını belirtme hakkında bilgi `outputFilename`için [bkz.](resgen-exe-resource-file-generator.md#Compiling) *Ad alanı* atlanırsa, kaynak sınıfı bir ad alanında içermez.  
  
 *Classname*  
 kesin belirlenmiş kaynak sınıfının adı. Bu, .resources dosyasının kök adına karşılık gelmelidir. Örneğin, Resgen.exe MyCompany.Libraries.Strings.resources adlı bir .resources dosyası üretirse, belirlenmiş kaynak sınıfının adı Strings olur. *Sınıf adı* atlanırsa, oluşturulan sınıf `outputFilename`. Atlanırsa, `outputFilename` oluşturulan sınıf `inputFilename`.  
  
 *sınıf adı* katıştırılmış alanlar gibi geçersiz karakterler içeremez. Sınıf adı katıştırılmış boşluklar içeriyorsa veya *inputFilename'den*varsayılan *olarak sınıf* *adı* oluşturulacaksa ve *inputFilename* gömülü boşluklar\_içeriyorsa, Resgen.exe tüm geçersiz karakterlerin yerine alt puan ().  
  
 *filename*  
 Sınıf dosyasının adı.  
  
 `/publicclass`  
 (C#' da) veya `internal` `Friend` (Visual Basic) yerine güçlü bir şekilde yazılan kaynak sınıfını herkese açık hale getirir. Bu, kaynaklara, içine gömüldükleri derlemenin dışından erişmeye olanak tanır.  
  
> [!IMPORTANT]
> Kesin olarak belirlenmiş bir kaynak sınıfı oluşturduğunuzda, .resources dosyanızın adı üretilen kodun ad alanıyla ve sınıf adıyla eşleşmelidir. Ancak, Resgen.exe uyumsuz bir adı olan bir .resources dosyası üretmek seçenekleri belirtmenize olanak verir. Bu davranışa geçici bir çözüm için, çıktı dosyası oluşturulduktan sonra dosyayı yeniden adlandırın.  
  
 Kesin belirlenmiş kaynak sınıfı aşağıdaki üyelere sahiptir:  
  
- Güçlü bir şekilde yazılan kaynak sınıfını anında oluşturmak için kullanılabilen parametresiz bir oluşturucu.  
  
- Güçlü `static` bir şekilde `Shared` yazılan kaynağı yöneten <xref:System.Resources.ResourceManager> örneği `ResourceManager` döndüren bir (C#) veya (Visual Basic) ve salt okunur özelliği.  
  
- Kaynak `Culture` alma için kullanılan kültürü ayarlamanızı sağlayan statik bir özellik. Varsayılan olarak, `null`değeri, geçerli UI kültürünün kullanıldığı anlamına gelir.  
  
- .resources dosyasındaki her kaynak için `static` bir (C#) veya `Shared` (Visual Basic) ve salt okunur özellik. Özelliğin adı, kaynağının adıdır.  
  
 Örneğin, aşağıdaki komut StringResources.txt adlı bir kaynak dosyasını StringResources.resources'a `StringResources` derler ve Kaynak Yöneticisi'ne erişmek için kullanılabilecek StringResources.vb adlı Visual Basic kaynak kodu dosyasında bir sınıf oluşturur.  
  
```console  
resgen StringResources.txt /str:vb,,StringResources
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [Masaüstü Uygulamalarında Kaynaklar](../resources/index.md)
- [Kaynak Dosyaları Oluşturma](../resources/creating-resource-files-for-desktop-apps.md)
- [Al.exe (Bütünleştirilmiş Kod Bağlayıcı)](al-exe-assembly-linker.md)
- [Komut İstemleri](developer-command-prompt-for-vs.md)
