---
title: Resgen.exe (Kaynak Dosya Oluşturucu)
description: Kaynak dosya Oluşturucu Resgen.exe kullanın. Metin (. txt,. restext) ve XML kaynak biçimi (. resx) dosyalarını, eklenebilir CLR Runtime ikilileriyle (. resources) dönüştürün.
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
ms.openlocfilehash: f51ee6c8537abafc82017f3cc29d734e939a254f
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517236"
---
# <a name="resgenexe-resource-file-generator"></a>Resgen.exe (Kaynak Dosya Oluşturucu)
Kaynak Dosya Oluşturucu (Resgen.exe), metin (.txt veya .restext) dosyalarını ve XML tabanlı kaynak biçimi (.resx) dosyalarını, bir çalışma zamanı ikili çalıştırılabilir dosyasına katıştırılabilen veya uydu derlemesi haline getirilebilen ortak dil çalışma zamanı ikili (.resources) dosyalarına dönüştürür. (Bkz. [kaynak dosyalarını oluşturma](../resources/creating-resource-files-for-desktop-apps.md).)  
  
 Resgen.exe aşağıdaki görevleri gerçekleştiren genel amaçlı bir kaynak dönüştürme programıdır:  
  
- .txt veya .restext dosyalarını .resources veya .resx dosyalarına dönüştürür. (.restext dosyalarının biçimi .txt dosyalarının biçimiyle aynıdır. Ancak, .restext uzantısı, kaynak tanımları içeren metin dosyalarını daha kolay belirlemenize yardımcı olur.)  
  
- .resources dosyalarını metin veya .resx dosyalarına dönüştürür.  
  
- .resx dosyalarını metin veya .resources dosyalarına dönüştürür.  
  
- Bir derlemeden dize kaynaklarını bir Windows 8. x mağaza uygulamasında kullanılmak üzere uygun bir. resw dosyasına ayıklar.  
  
- Tek bir adlandırılmış kaynağa ve örneğe erişim sağlayan, türü kesin belirlenmiş bir sınıf oluşturur <xref:System.Resources.ResourceManager> .  
  
 Resgen.exe herhangi bir nedenle başarısız olursa, dönüş değeri –1'dir.  
  
 Resgen.exe hakkında yardım almak için, komut sözdizimini ve Resgen.exe seçeneklerini göstermek üzere hiçbir seçenek belirtilmeyen aşağıdaki komutu kullanabilirsiniz:  
  
```console  
resgen  
```  
  
 Anahtarı da kullanabilirsiniz `/?` :  
  
```console  
resgen /?  
```  
  
 İkili. resources dosyaları oluşturmak için Resgen.exe kullanırsanız, ikili dosyaları yürütülebilir derlemelere eklemek için bir dil derleyicisi kullanabilir veya [derleme Bağlayıcısı (Al.exe)](al-exe-assembly-linker.md) kullanarak bunları uydu derlemelerine derleyebilirsiniz.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın. Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md).  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
resgen  [-define:symbol1[,symbol2,...]] [/useSourcePath] filename.extension  | /compile filename.extension... [outputFilename.extension] [/r:assembly] [/str:lang[,namespace[,class[,file]]] [/publicclass]]
```  
  
```console  
resgen filename.extension [outputDirectory]  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Parametre veya anahtar|Açıklama|  
|-------------------------|-----------------|  
|`/define:`*symbol1*[, *symbol2*,...]|4,5 .NET Framework başlayarak, metin tabanlı (. txt veya. restext) kaynak dosyalarında koşullu derlemeyi destekler. *Sembol* , bir yapı içindeki giriş metin dosyasında içerilen bir simgeye karşılık geliyorsa `#ifdef` , ilişkili dize kaynağı. resources dosyasına dahil edilir. Giriş metin dosyası, `#if !` anahtar tarafından tanımlanmayan bir sembol içeren bir ifade içeriyorsa `/define` , ilişkili dize kaynağı kaynaklar dosyasına dahil edilir.<br /><br /> `/define`metin olmayan dosyalarla kullanılırsa yok sayılır. Simgeler büyük/küçük harfe duyarlıdır.<br /><br /> Bu seçenek hakkında daha fazla bilgi için, bu konunun ilerleyen kısımlarında [kaynakları koşullu olarak derleme](#Conditional) bölümüne bakın.|  
|`useSourcePath`|Giriş dosyasının geçerli dizininin göreli dosya yollarını çözmek için kullanılacağını belirtir.|  
|`/compile`|Tek bir toplu işlemde birden çok .resources dosyasına dönüştürmek için birden fazla .resx veya metin dosyası belirtmenize olanak sağlar. Bu seçeneği belirtmezseniz, yalnızca bir giriş dosyası bağımsız değişkeni belirtebilirsiniz. Çıktı dosyaları *dosya adı*. resources olarak adlandırılır.<br /><br /> Bu seçenek, seçeneğiyle birlikte kullanılamaz `/str:` .<br /><br /> Bu seçenek hakkında daha fazla bilgi için, bu konunun ilerleyen kısımlarında [birden çok dosya derleme veya dönüştürme](#Multiple) bölümüne bakın.|  
|`/r:` `assembly`|Belirtilen derlemedeki meta verilere başvurur. .resx dosyaları dönüştürülürken kullanılır ve Resgen.exe'nin nesne kaynaklarını serileştirmesine veya serilerinin kaldırılmasına olanak sağlar. `/reference:` `/r:` C# ve Visual Basic derleyicileri için veya seçeneklerine benzerdir.|  
|`filename.extension`|Dönüştürülecek giriş dosyasının adını belirtir. Bu tablodan önce sunulan birinci, tablodan komut satırı söz dizimini kullanıyorsanız, aşağıdakilerden `extension` biri olmalıdır:<br /><br /> .txt veya .restext<br /> Bir .resources veya .resx dosyasına dönüştürülecek bir metin dosyası. Metin dosyaları yalnızca dize kaynakları içerebilir. Dosya biçimi hakkında daha fazla bilgi için, [kaynak dosyaları oluşturma](../resources/creating-resource-files-for-desktop-apps.md)konusunun "metin dosyalarındaki kaynaklar" bölümüne bakın.<br /><br /> .resx<br /> Bir .resources veya metin (.txt veya .restext) dosyasına dönüştürülecek XML tabanlı bir kaynak dosyası.<br /><br /> .resources<br /> Bir .resx veya bir metin (.txt veya .restext) dosyasına dönüştürülecek ikili bir kaynak dosyası.<br /><br /> İkincisini kullanıyorsanız, bu tablodan önce sunulan daha kısa komut satırı sözdizimi `extension` aşağıdaki olmalıdır:<br /><br /> .exe veya .dll<br /> Windows 8. x Mağazası uygulamaları geliştirmek için kullanmak üzere dize kaynakları bir. resw dosyasına Ayıklanacak bir .NET Framework derlemesi (yürütülebilir veya kitaplık).|  
|`outputFilename.extension`|Oluşturulacak kaynak dosyasının adını ve türünü belirtir.<br /><br /> Bir .txt, .restext veya .resx dosyasından bir .resources dosyasına dönüştürme yaparken bu bağımsız değişken isteğe bağlıdır. Belirtmezseniz `outputFilename` , Resgen.exe girişe bir. resources uzantısı ekler `filename` ve dosyayı içeren dizine yazar `filename,extension` .<br /><br /> `outputFilename.extension`Bir. resources dosyasından dönüştürürken bağımsız değişken zorunludur. Bir .resources dosyasını XML tabanlı bir kaynak dosyasına dönüştürürken, .resx uzantılı bir dosya adı belirtin. Bir .resources dosyasını bir metin dosyasına dönüştürürken, .txt veya .restext uzantılı bir dosya adı belirtin. Bir .resources dosyasını, .resources dosyası yalnızca dize değerleri içerirken bir .txt dosyasına dönüştürmelisiniz.|  
|`outputDirectory`|Windows 8. x Mağazası uygulamaları için, içinde dize kaynaklarını içeren bir. resw dosyasının yazılacağı dizini belirtir `filename.extension` . `outputDirectory`zaten var olmalıdır.|  
|`/str:` `language[,namespace[,classname[,filename]]]`|Seçeneğinde belirtilen programlama dilinde kesin olarak belirlenmiş bir kaynak sınıfı dosyası oluşturur `language` . `language`Aşağıdaki değişmez değerlerden birini içerebilir:<br /><br /> -C# için: `c#` , `cs` , veya `csharp` .<br />-Visual Basic için: `vb` veya `visualbasic` .<br />-VBScript için: `vbs` veya `vbscript` .<br />-C++ için: `c++` , `mc` , veya `cpp` .<br />-JavaScript için: `js` , `jscript` , veya `javascript` .<br /><br /> `namespace`Seçeneği, projenin varsayılan ad alanını belirtir, `classname` seçeneği oluşturulan sınıfın adını belirtir ve `filename` seçenek sınıf dosyasının adını belirtir.<br /><br /> `/str:`Seçenek yalnızca bir giriş dosyasına izin veriyor, bu nedenle `/compile` seçeneğiyle kullanılamaz.<br /><br /> `namespace`Belirtilirse, ancak yoksa `classname` , sınıf adı çıkış dosyası adından türetilir (örneğin, alt çizgiler dönemler için değiştirilir). Kesin olarak belirlenmiş kaynaklar sonuç olarak doğru çalışmayabilir. Bunu önlemek için, hem sınıf adı hem de çıkış dosyası adı belirtin.<br /><br /> Bu seçenek hakkında daha fazla bilgi için, bu konunun ilerleyen kısımlarında türü [kesin belirlenmiş kaynak sınıfı oluşturma](#Strong) bölümüne bakın.|  
|`/publicClass`|Kesin belirlenmiş bir kaynak sınıfını bir genel sınıf olarak oluşturur. Varsayılan olarak, kaynak sınıfı `internal` C# ve `Friend` Visual Basic.<br /><br /> Seçenek kullanılmazsa bu seçenek yoksayılır `/str:` .|  
  
## <a name="resgenexe-and-resource-file-types"></a>Resgen.exe ve Kaynak Dosya Türleri  
 Resgen.exe'nin kaynakları doğru olarak dönüştürmesi için, metin ve .resx dosyalarının doğru biçime uygun olması gerekir.  
  
### <a name="text-txt-and-restext-files"></a>Metin (.txt ve .restext) Dosyaları  
 Metin (.txt veya .restext) dosyaları yalnızca dize kaynakları içerebilir. Dizelerin çeşitli dillere çevrilmiş olması gereken bir uygulama yazıyorsanız, dize kaynakları yararlıdır. Örneğin, uygun dize kaynağını kullanarak, menü dizelerini kolayca bölgeselleştirebilirsiniz. Resgen.exe, ad/değer çiftlerini içeren metin dosyalarını okur; burada, ad kaynağı tanımlayan bir dizedir ve değer kaynak dizesinin kendisidir.  
  
> [!NOTE]
> . Txt ve. restext dosyalarının biçimi hakkında daha fazla bilgi için [kaynak dosyaları oluşturma](../resources/creating-resource-files-for-desktop-apps.md)konusunun "metin dosyalarındaki kaynaklar" bölümüne bakın.  
  
 Yalnızca Temel Latince aralığındaki karakterleri (U+007F) içermedikçe, kaynakları içeren bir metin dosyasının UTF-8 veya Unicode (UTF-16) kodlamasıyla kaydedilmesi gerekir. Resgen.exe, ANSI kodlaması kullanılarak kaydedilen bir metin dosyasını işlerken genişletilmiş ANSI karakterlerini kaldırır.  
  
 Resgen.exe, metin dosyasında yinelenen kaynak adlarını denetler. Metin dosyası yinelenen kaynak adları içeriyorsa, Resgen.exe bir uyarı verir ve ikinci değeri yoksayar.  
  
### <a name="resx-files"></a>.resx Dosyaları  
 .resx kaynak dosyası biçimi XML girişlerinden oluşur. Metin dosyalarında olduğu gibi bu XML girdileri içinde dize kaynakları belirtebilirsiniz. .resx dosyalarının metin dosyalarına göre birincil yararlarından birisi, nesneler de belirtebilir veya gömebilir olmanızdır. Bir .resx dosyasını görüntülediğinizde, ikili bilgiler kaynak bildiriminin bir parçası olduğunda, gömülü bir nesnenin (örneğin, bir resim) ikili biçimini görebilirsiniz. Metin dosyalarında olduğu gibi, bir .resx dosyasını bir metin düzenleyicicisiyle (Not Defteri veya Microsoft Word gibi) açabilir ve içeriğini yazabilir, ayrıştırabilir ve değiştirebilirsiniz. Bunun için, XML etiketlerini ve .resx dosyası yapısını iyi bilmenin gerektiğini unutmayın. . Resx dosya biçimi hakkında daha fazla bilgi için bkz. [kaynak dosyaları oluşturma](../resources/creating-resource-files-for-desktop-apps.md)konusunun ". resx dosyalarındaki kaynaklar" bölümü.  
  
 Gömülü dize olmayan nesneler içeren bir. resources dosyası oluşturmak için, nesne içeren bir. resx dosyasını dönüştürmek veya sınıf tarafından sunulan yöntemleri çağırarak doğrudan koddan dosyanıza nesne kaynakları eklemek için Resgen.exe kullanmanız gerekir <xref:System.Resources.ResourceWriter> .  
  
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
 Resgen.exe farklı yollarla kullanabilirsiniz: metin tabanlı veya XML tabanlı bir kaynak dosyasını ikili bir dosyaya derlemek, kaynak dosya biçimlerini arasında dönüştürmek ve işlevselliği sarmalayan <xref:System.Resources.ResourceManager> ve kaynaklara erişim sağlayan bir sınıf oluşturmak için. Bu bölüm, her görevle ilgili ayrıntılı bilgi sağlar:  
  
- [Kaynakları Bir İkili Dosyaya Derleme](resgen-exe-resource-file-generator.md#Compiling)  
  
- [Kaynak Dosya Türleri Arasında Dönüştürme](resgen-exe-resource-file-generator.md#Convert)  
  
- [Birden Çok Dosyayı Derleme veya Dönüştürme](resgen-exe-resource-file-generator.md#Multiple)  
  
- [Kaynakları Bir .resw Dosyasına Verme](resgen-exe-resource-file-generator.md#Exporting)  
  
- [Kaynakları Koşullu Olarak Derleme](resgen-exe-resource-file-generator.md#Conditional)  
  
- [Kesin Olarak Belirlenmiş Bir Kaynak Sınıfı Oluşturma](resgen-exe-resource-file-generator.md#Strong)  
  
<a name="Compiling"></a>
### <a name="compiling-resources-into-a-binary-file"></a>Kaynakları Bir İkili Dosyaya Derleme  
 Resgen.exe'nin en yaygın kullanımı, metin tabanlı bir kaynak dosyasını (bir .txt veya .restext dosyası) veya XML tabanlı bir kaynak dosyasını (bir .resx dosyası) bir ikili .resources dosyasına derlemektir. Çıktı dosyası daha sonra bir dil derleyicisi tarafından bir ana derlemeye veya [derleme Bağlayıcısı (AL.exe)](al-exe-assembly-linker.md)tarafından bir uydu derlemesine eklenebilir.  
  
 Bir kaynak dosyasını derlemek için sözdizimi aşağıdaki gibidir:  
  
```console  
resgen inputFilename [outputFilename]
```  
  
 burada parametreler şunlardır:  
  
 `inputFilename`  
 Uzantı dahil, derlenecek dosyanın adı. Resgen.exe yalnızca uzantısı .txt, .restext veya .resx olan dosyaları derler.  
  
 `outputFilename`  
 Çıktı dosyasının adı. Atlanırsa `outputFilename` , Resgen.exe aynı dizinde kök dosya adı olan bir. resources dosyası oluşturur `inputFilename` `inputFilename` . `outputFilename`Bir dizin yolu içeriyorsa, dizin var olmalıdır.  
  
 .resources dosyası için tam olarak belirtilen bir ad alanını, ad alanını dosya adında belirterek ve bir nokta ile kök dosya adından ayırarak belirtirsiniz. Örneğin, ise, `outputFilename` `MyCompany.Libraries.Strings.resources` ad alanı MyCompany. Libraries olur.  
  
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
  
 Ayrıca, bir .NET Framework derlemesindeki katıştırılmış kaynakları, Windows 8. x Mağazası uygulamalarına bir. resw dosyasına dönüştürmek için Resgen.exe kullanabilirsiniz.  
  
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
 Tek bir işlemde bir `/compile` kaynak dosyaları listesini bir biçimden diğerine dönüştürmek için anahtarını kullanabilirsiniz. Söz dizimi aşağıdaki gibidir:  
  
```console  
resgen /compile filename.extension [filename.extension...]  
```  
  
 Aşağıdaki komut, StringResources.txt, TableResources.resw ve ImageResources.resw adlı üç dosyayı StringResources.resources, TableResources.resources ve ImageResources.resources adlı ayrı .resources dosyalarına dönüştürür.  
  
```console  
resgen /compile StringResources.txt TableResources.resx ImageResources.resx  
```  
  
<a name="Exporting"></a>
### <a name="exporting-resources-to-a-resw-file"></a>Kaynakları Bir .resw Dosyasına Verme  
 Bir Windows 8. x Mağazası uygulaması geliştiriyorsanız, mevcut bir masaüstü uygulamasındaki kaynakları kullanmak isteyebilirsiniz. Ancak, iki tür uygulama farklı dosya biçimlerini destekler. Masaüstü uygulamalarında, metin (.txt veya .restext) veya .resx dosyaları içinde kaynaklar ikili .resources dosyalarına derlenir. Windows 8. x Mağazası uygulamaları,. resw dosyaları ikili paket kaynak dizini (PRı) dosyalarına derlenir. Bir yürütülebilir veya uydu derlemesinden kaynakları çıkararak ve bunları bir Windows 8. x Mağazası uygulaması geliştirirken kullanılabilecek bir veya daha fazla. resw dosyasına yazarak bu boşluğu bağlamak için Resgen.exe kullanabilirsiniz.  
  
> [!IMPORTANT]
> Visual Studio, taşınabilir bir kitaplıktaki kaynakları bir Windows 8. x mağaza uygulamasına eklemek için gereken tüm dönüştürmeleri otomatik olarak işler. Bir derlemedeki kaynakları. resw dosya biçimine dönüştürmek için Resgen.exe doğrudan kullanmak, yalnızca Visual Studio dışında bir Windows 8. x Mağazası uygulaması geliştirmek isteyen geliştiriciler için geçerlidir.  
  
 Bir derlemeden .resw dosyaları oluşturmak için sözdizimi aşağıdaki gibidir:  
  
```console  
resgen filename.extension  [outputDirectory]  
```  
  
 burada parametreler şunlardır:  
  
 `filename.extension`  
 Bir .NET Framework derlemesinin (bir yürütülebilir veya .DLL) adı. Dosya hiç kaynak içermiyorsa, Resgen.exe herhangi bir dosya oluşturmaz.  
  
 `outputDirectory`  
 .resw dosyalarının yazılacağı varolan dizin. `outputDirectory`Atlanırsa,. resw dosyaları geçerli dizine yazılır. Resgen.exe, derlemedeki her bir .resources dosyası için bir .resw dosyası oluşturur. .resw dosyasının kök dosya adı, .resources dosyasının kök adı ile aynıdır.  
  
 Aşağıdaki komut, MyApp.exe içinde gömülü her .resources dosyası için Win8Resources dizininde bir .resw dosyası oluşturur:  
  
```console  
resgen MyApp.exe Win8Resources  
```  
  
<a name="Conditional"></a>
### <a name="conditionally-compiling-resources"></a>Kaynakları Koşullu Olarak Derleme  
 Resgen.exe .NET Framework 4,5 ' den başlayarak, metin (. txt ve. restext) dosyalarındaki dize kaynaklarının koşullu derlemesini destekler. Bu, birden çok oluşturma yapılandırmasında tek bir metin tabanlı dosya kullanmanıza olanak tanır.  
  
 Bir. txt veya. restext dosyasında,... `#ifdef``#endif` bir sembol tanımlandıysa ve bir `#if !` `#endif` sembol tanımlanmamışsa bir kaynağı dahil etmek için... yapısını kullanarak, bir kaynağı ikili. resources dosyasına dahil etmek için oluşturun. Derleme zamanında, ardından seçeneğini kullanarak, ardından `/define:` virgülle ayrılmış semboller listesi olan sembolleri tanımlayın. Karşılaştırma hassastır; tarafından tanımlanan simgelerin durumu, `/define` derlenmiş metin dosyalarındaki semboller durumuyla eşleşmelidir.  
  
 Örneğin, UIResources. Rext adlı aşağıdaki dosya `AppTitle` ,, veya adında simgelerin tanımlanmış olmasına bağlı olarak üç değerden birini alan adlı bir dize kaynağı içerir `PRODUCTION` `CONSULT` `RETAIL` .  
  
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
  
 Bu, iki dize kaynağı içeren bir .resources dosyası oluşturur. `AppTitle`Kaynağın değeri "danışmanlık şirketi Proje Yöneticisi" dir.  
  
<a name="Strong"></a>
### <a name="generating-a-strongly-typed-resource-class"></a>Kesin Olarak Belirlenmiş Bir Kaynak Sınıfı Oluşturma  
 Resgen.exe, bir statik salt okunur özellikler kümesi içeren sınıflar oluşturarak kaynaklara erişimi kapsülleyen, kesin olarak belirlenmiş kaynakları destekler. Bu, <xref:System.Resources.ResourceManager> kaynakları almak için doğrudan sınıfın yöntemlerini çağırmaya bir alternatif sağlar. `/str`Sınıfının işlevselliğini sarmalayan Resgen.exe seçeneğini kullanarak türü kesin belirlenmiş kaynak desteğini etkinleştirebilirsiniz <xref:System.Resources.Tools.StronglyTypedResourceBuilder> . `/str`Seçeneğini belirttiğinizde Resgen.exe çıkışı, giriş parametresinde başvurulan kaynaklarla eşleşen kesin türü belirtilmiş özellikler içeren bir sınıftır. Bu sınıf, işlenen dosyada kullanılabilir olan kaynaklara kesin belirlenmiş salt okunur erişim sağlar.  
  
 Kesin belirlenmiş kaynak oluşturmak için sözdizimi aşağıdaki gibidir:  
  
```console  
resgen inputFilename [outputFilename] /str:language[,namespace,[classname[,filename]]] [/publicClass]  
```  
  
 Parametreler ve anahtarlar şunlardır:  
  
 `inputFilename`  
 Kendisi için kesin olarak belirlenmiş bir kaynak sınıfı oluşturulacak kaynak dosyasının dosya adı ve uzantısı. Dosya, metin tabanlı, XML-tabanlı veya ikili .resources dosyası olabilir; uzantısı .txt, .restext, .resw veya .resources olabilir.  
  
 `outputFilename`  
 Çıktı dosyasının adı. `outputFilename`Bir dizin yolu içeriyorsa, dizin var olmalıdır. Atlanırsa `outputFilename` , Resgen.exe aynı dizinde kök dosya adı olan bir. resources dosyası oluşturur `inputFilename` `inputFilename` .  
  
 `outputFilename`metin tabanlı, XML tabanlı veya ikili. resources dosyası olabilir. Dosya Uzantısı `outputFilename` ' ın dosya uzantısından farklıysa `inputFilename` , Resgen.exe dosya dönüştürmeyi gerçekleştirir.  
  
 `inputFilename`Bir. resources dosyası ise, Resgen.exe. resources dosyasını `outputFilename` da bir. resources dosyası ise kopyalar. `outputFilename`Atlanırsa, Resgen.exe `inputFilename` özdeş bir. resources dosyası ile üzerine yazılır.  
  
 *dildir*  
 Türü kesin belirlenmiş kaynak sınıfı için kaynak kodunun oluşturulacağı dil. Olası değerler `cs` ,, `C#` ve `csharp` C# kodu için, `vb` `visualbasic` Visual Basic kodu ve VBScript kodu için `vbs` ve `vbscript` `c++` , `mc` ve `cpp` C++ kodu için.  
  
 *uzayına*  
 Kesin olarak belirlenmiş kaynak sınıfını içeren ad alanı. .resources dosyası ve kaynak sınıfı aynı ad alanına sahip olmalıdır. İçinde ad alanını belirtme hakkında bilgi için `outputFilename` bkz. [kaynakları bir Ikili dosyada derleme](resgen-exe-resource-file-generator.md#Compiling). *Ad alanı* atlanırsa, kaynak sınıfı bir ad alanında yer alır.  
  
 *sınıf*  
 kesin belirlenmiş kaynak sınıfının adı. Bu, .resources dosyasının kök adına karşılık gelmelidir. Örneğin, Resgen.exe MyCompany.Libraries.Strings.resources adlı bir .resources dosyası üretirse, belirlenmiş kaynak sınıfının adı Strings olur. *ClassName* atlanırsa, oluşturulan sınıf öğesinin kök adından türetilir `outputFilename` . `outputFilename`Atlanırsa, oluşturulan sınıf öğesinin kök adından türetilir `inputFilename` .  
  
 *ClassName* gömülü boşluklar gibi geçersiz karakterler içeremez. *ClassName* gömülü alanlar içeriyorsa veya varsayılan olarak *inputFilename* *öğesinden oluşturulursa,* *ınputfilename* gömülü boşluklar içeriyorsa Resgen.exe tüm geçersiz karakterleri alt çizgi () ile değiştirir \_ .  
  
 *filename*  
 Sınıf dosyasının adı.  
  
 `/publicclass`  
 Kesin türü belirtilmiş kaynak sınıfını `internal` (C# ' de) veya `Friend` (Visual Basic) olarak ortak hale getirir. Bu, kaynaklara, içine gömüldükleri derlemenin dışından erişmeye olanak tanır.  
  
> [!IMPORTANT]
> Kesin olarak belirlenmiş bir kaynak sınıfı oluşturduğunuzda, .resources dosyanızın adı üretilen kodun ad alanıyla ve sınıf adıyla eşleşmelidir. Ancak, Resgen.exe uyumsuz bir adı olan bir .resources dosyası üretmek seçenekleri belirtmenize olanak verir. Bu davranışa geçici bir çözüm için, çıktı dosyası oluşturulduktan sonra dosyayı yeniden adlandırın.  
  
 Kesin belirlenmiş kaynak sınıfı aşağıdaki üyelere sahiptir:  
  
- Türü kesin belirlenmiş kaynak sınıfının örneğini oluşturmak için kullanılabilen parametresiz Oluşturucu.  
  
- `static` `Shared` `ResourceManager` <xref:System.Resources.ResourceManager> Kesin olarak belirlenmiş kaynağı yöneten örneği döndüren bir (C#) veya (Visual Basic) ve salt okunurdur özelliği.  
  
- `Culture`Kaynak alımı için kullanılan kültürü ayarlamanıza olanak tanıyan statik bir özellik. Varsayılan olarak, değeri, `null` GEÇERLI UI kültürünün kullanıldığı anlamına gelir.  
  
- `static` `Shared` . Resources dosyasındaki her kaynak için bir (C#) veya (Visual Basic) ve salt okunurdur özelliği. Özelliğin adı, kaynağının adıdır.  
  
 Örneğin, aşağıdaki komut, StringResources.txt adlı bir kaynak dosyasını StringResources. resources içine derler ve `StringResources` Kaynak Yöneticisi erişmek için kullanılabilecek StringResources. vb adlı Visual Basic kaynak kodu dosyasında adlı bir sınıf oluşturur.  
  
```console  
resgen StringResources.txt /str:vb,,StringResources
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [Masaüstü uygulamalarındaki kaynaklar](../resources/index.md)
- [Kaynak Dosyaları Oluşturma](../resources/creating-resource-files-for-desktop-apps.md)
- [Al.exe (bütünleştirilmiş kod bağlayıcı)](al-exe-assembly-linker.md)
- [Komut Istemleri](developer-command-prompt-for-vs.md)
