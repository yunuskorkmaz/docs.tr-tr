---
title: MDbg.exe (.NET Framework Komut Satırı Hata Ayıklayıcı)
description: Araç satıcılarının ve uygulama geliştiricilerinin CLR 'yi hedefleyen programlardaki hataları bulmasına ve düzeltmesine yardımcı olan, .NET için komut satırı hata ayıklayıcı MDbg.exe anlayın.
ms.date: 03/30/2017
helpviewer_keywords:
- command-line debugger [.NET Framework]
- MDbg.exe
ms.assetid: 28a3f509-07e2-4dbe-81df-874c5e969cc4
ms.openlocfilehash: 6118e20293f6076d080402b4e6ce52bd0e86e5cd
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104653952"
---
# <a name="mdbgexe-net-framework-command-line-debugger"></a>MDbg.exe (.NET Framework Komut Satırı Hata Ayıklayıcı)

NET Framework Komut Satırı Hata Ayıklayıcısı, araç satıcılarının ve uygulama geliştiricilerin, .NET Framework ortak dil çalışma zamanını hedefleyen programlardaki hataları bulmalarına ve düzeltmelerine yardımcı olur. Bu araç, hata ayıklama hizmetleri sağlamak için çalışma zamanı hata ayıklama API kullanır. MDbg.exe'yi yalnızca yönetilen kodda hata ayıklamak için kullanabilirsiniz; yönetilmeyen kodda hata ayıklama desteği yoktur.  
  
Bu araç NuGet aracılığıyla kullanılabilir. Yükleme bilgileri için bkz. [MDbg 0.1.0](https://www.nuget.org/packages/MDbg/0.1.0). Aracı çalıştırmak için Paket Yöneticisi konsolunu kullanın. Paket Yöneticisi konsolunun kullanımı hakkında daha fazla bilgi için bkz. [Paket Yöneticisi konsol](/nuget/tools/package-manager-console) makalesi.
  
Paket Yöneticisi isteminde aşağıdakileri yazın:  
  
## <a name="syntax"></a>Syntax  
  
```console  
MDbg [ProgramName[arguments]] [options]  
```  
  
## <a name="commands"></a>Komutlar  

 Hata ayıklayıcısında ( **MDbg>** isteminde gösterildiği gibi), sonraki bölümde açıklanan komutlardan birini yazın:  
  
 **komut** [*bağımsız değişkenler*]  
  
 MDbg.exe komutları büyük/küçük harfe duyarlıdır.  
  
|Komut|Açıklama|  
|-------------|-----------------|  
|**AP**[**neticisi**] [*sayı*]|Hataları ayıklanan başka bir işleme geçer veya kullanılabilir işlemleri yazdırır. Numaralar gerçek işlem kimlikleri (PID) değil, 0-dizinli bir listedir.|  
|**a**[**kle**] [*pid*]|Bir işleme iliştirir veya kullanılabilir işlemleri yazdırır.|  
|**b**[**reak**] [*ClassName. Method* &#124; *filename: LineNo*]|Belirtilen yöntemde bir kesme noktası ayarlar. Modüller sırayla taranır.<br /><br /> -   **kesme** *dosya adı: LineNo* , kaynaktaki bir konumda bir kesme noktası ayarlar.<br />-   **Break** *~ sayı* **x** komutuyla yakın zamanda görünen bir simgenin üzerine bir kesme noktası ayarlar.<br />-   modülün **sonu** *! ClassName. Method + ılkayması* tam konumda bir kesme noktası ayarlar.|  
|**Block**[**ınobjects**]|Engelleyici iş parçacıkları olan izleme kilitlerini görüntüler.|  
|**CA**[**eğiştir**] [*ExceptionType*]|Hata ayıklayıcının, yalnızca işlenmeyen özel durumları değil, tüm özel durumları kesmesine neden olur.|  
|**CL**[**earexception**]|Yürütmenin devam edebilmesi için, geçerli özel durumu işlenmiş olarak işaretler. Özel durumun nedeniyle ilgilenilmediyse, özel durum hızlı bir şekilde yeniden oluşturulabilir.|  
|**conf**[**IG**] [*seçenek değeri*]|Tüm yapılandırılabilir seçenekleri görüntüler ve seçeneklerin isteğe bağlı değerler olmadan nasıl çağrılabileceğini gösterir. Seçenek belirtilmişse, `value` Geçerli seçenek olarak ayarlar. Aşağıdaki seçenekler şu anda kullanılabilir:<br /><br /> -   `extpath` komut kullanıldığında uzantıları aramak için yolu ayarlar `load` .<br />-   `extpath+` uzantıları yüklemek için bir yol ekler.|  
|**del**[**si**]|Bir kesme noktasını siler.|  
|**de**[**yır**]|Hata ayıklaması yapılmış bir işlemden ayırır.|  
|**d**[**sahip**] [*çerçeveler*]|Etkin yığın çerçevesini aşağı taşır.|  
|**girdilerinizi**|Bir iletiyi konsola yankılatır.|  
|**Enableuyr**[**,**] *TypeName* 0&#124;1|Belirtilen tür için özel bildirimleri etkinleştirir (1) veya devre dışı bırakır (0).|  
|**ex**[**It**] [*ExitCode*]|MDbg.exe kabuğundan çıkar ve isteğe bağlı olarak işlem çıkış kodunu belirtir.|  
|**fo**[**Reach**] [*diğerkomut*]|Bir komutu tüm iş parçacıkları üzerinde uygular. *OtherCommand* , bir iş parçacığında çalışan geçerli bir komuttur; **ForEach** *diğerkomutu* tüm iş parçacıkları üzerinde aynı komutu gerçekleştirir.|  
|**f**[**unceval**] [ `-ad` *num*] *fonksiyonadı* [*args...* ]|Değerlendirilecek işlevin *fonksiyonadı* olduğu geçerli etkin iş parçacığında bir işlev değerlendirmesi gerçekleştirir. İşlev adı, ad alanları da dahil olmak üzere tam olarak nitelenmiş olmalıdır.<br /><br /> `-ad`Seçeneği, işlevi çözümlemek için kullanılacak uygulama etki alanını belirtir. `-ad`Seçenek belirtilmemişse, çözüm için uygulama etki alanı, işlev değerlendirmesi için kullanılan iş parçacığının bulunduğu uygulama etki alanına varsayılan olarak ayarlanır.<br /><br /> Değerlendirilen işlev statik değilse, geçirilen ilk parametre bir `this` işaretçi olmalıdır. Tüm uygulama etki alanlarında, işlev değerlendirmesi bağımsız değişkenleri için arama yapılır.<br /><br /> Bir uygulama etki alanından bir değer istemek için, değişkeni modüle ve uygulama etki alanı adına önek olarak ekleyin; Örneğin, `funceval -ad 0 System.Object.ToString hello.exe#0!MyClass.g_rootRef` . Bu komut, `System.Object.ToString` uygulama etki alanındaki işlevini değerlendirir `0` . `ToString`Yöntem bir örnek işlevi olduğundan, ilk parametre bir `this` işaretçi olmalıdır.|  
|**g**[**o**]|Programın bir kesme noktasıyla karşılaşıncaya, programdan çıkılıncaya veya bir olay (örneğin, işlenmemiş bir özel durum) programın durmasına neden oluncaya kadar devam etmesine neden olur.|  
|**h**[**ELP**] [*komut*]<br /><br /> -veya-<br /><br /> **?** [*komut*]|Tüm komutların açıklamasını veya belirtilen bir komutun ayrıntılı açıklamasını görüntüler.|  
|**IG**[**ksay**] [*olay*]|Hata ayıklayıcının yalnızca işlenmemiş özel durumlarda durmasına neden olur.|  
|**int**[**ercept**] *framenumarası*|Hata ayıklayıcıyı belirtilen bir çerçeve numarasına geri döndürür.<br /><br /> Hata ayıklayıcı bir özel durumla karşılaşırsa, hata ayıklayıcıyı belirtilen kare numarasına geri döndürmek için bu komutu kullanın. **Ayarla** komutunu kullanarak program durumunu değiştirebilir ve **Go** komutunu kullanarak devam edebilirsiniz.|  
|**k**[**ill**]|Etkin işlemi durdurur.|  
|**l**[**ist**] [*modüller* &#124; *AppDomain* &#124; *derlemeleri*]|Yüklü modülleri, uygulama etki alanlarını veya derlemeleri görüntüler.|  
|**Lo**[**ad**] *AssemblyName*|Aşağıdaki şekilde bir uzantı yükler: belirtilen derleme yüklenir ve statik yöntemi türden çalıştırmak için bir deneme yapılır `LoadExtension` `Microsoft.Tools.Mdbg.Extension.Extension` .|  
|**günlük** [*EventType*]|Günlüğe kaydedilecek olayları ayarlayın veya görüntüleyin.|  
|**Mo**[**de**] [*seçenek açık/kapalı*]|Farklı hata ayıklayıcı seçeneklerini ayarlar. `mode`Hata ayıklama modlarının ve geçerli ayarlarının bir listesini almak için hiçbir seçenek olmadan kullanın.|  
|**Mon**[**ıtorınfo**] *monitorreference*|Nesne izleme kilidi bilgilerini görüntüler.|  
|**newo**[**BJ**] *TypeName* [*bağımsız değişkenler...*]|*TypeName* türünde yeni bir nesne oluşturur.|  
|**n**[**EXT**]|Kodu çalıştırır ve sonraki satıra geçer (sonraki satır birçok işlev çağrısı içerse bile).|  
|**Opendump** *pathtodumpfile*|Hata ayıklama için belirtilen döküm dosyasını açar.|  
|**o**[**UT**]|Geçerli işlevin sonuna taşır.|  
|**PA**[**TH**] [*yol adı*]|İkililerdeki konum kullanılabilir değilse, belirtilen yolda kaynak dosyalarını arar.|  
|**p**[**rint**] [*var*] &#124; [ `-d` ]|Kapsam (**Yazdır**) içindeki tüm değişkenleri yazdırır, belirtilen değişkeni (**Yazdır** *var*) yazdırır veya hata ayıklayıcı değişkenlerini yazdırır (**Yazdır** `-d` ).|  
|**Printe**[**durum**] [*-r*]|Geçerli iş parçacığındaki son özel durumu yazdırır. Özel `–r` `InnerException` durumların tüm zinciri hakkında bilgi almak için özel durum nesnesindeki özelliği çapraz geçiş yapmak için (özyinelemeli) seçeneğini kullanın.|  
|**Pro**[**cessenum**]|Etkin işlemleri görüntüler.|  
|**q**[**uit**] [*ExitCode*]|İsteğe bağlı olarak işlem çıkış kodunu belirterek, MDbg.exe kabuğundan çıkar.|  
|**yeniden**[**sume**] [ `*` &#124; [ `~` ]*threadNumber*]|Geçerli iş parçacığını veya *threadNumber* parametresiyle belirtilen iş parçacığını sürdürür.<br /><br /> *ThreadNumber* parametresi olarak belirtilmişse `*` veya iş parçacığı numarası ile başlıyorsa, bu komut, `~` *threadNumber* tarafından belirtilen bir hariç tüm iş parçacıkları için geçerlidir.<br /><br /> Askıya alınmamış bir iş parçacığını sürdürmenin etkisi yoktur.|  
|**r**[**un**] [ `-d` ( `ebug` ) &#124;- `o` ( `ptimize` ) &#124;`-enc` ] [[*path_to_exe*] [*args_to_exe*]]|Geçerli işlemi (varsa) durdurur ve yeni bir işlem başlatır. Yürütülebilir bir bağımsız değişken geçirilmemişse, bu komut daha önce komutuyla yürütülen programı çalıştırır `run` . Yürütülebilir bağımsız değişkeni sağlanırsa, belirtilen program isteğe bağlı olarak sağlanan bağımsız değişkenler kullanılarak çalıştırır.<br /><br /> Sınıf yükleme, modül yükleme ve iş parçacığı başlatma olayları yoksayılırsa (varsayılan olarak yoksayıldıkları gibi), program, ana iş parçacığının il yürütülebilir yönergesinde durur.<br /><br /> Aşağıdaki üç bayraktan birini kullanarak, hata ayıklayıcıyı kodu tam zamanında (JIT) derlemeye zorlayabilirsiniz:<br /><br /> -   `-d`*(* `ebug` *)* iyileştirmeleri devre dışı bırakır. Bu, MDbg.exe için varsayılan değerdir.<br />-   `-o`*(* `ptimize` *)* kodu hata ayıklayıcının dışında bir şekilde çalışacak şekilde zorlar, ancak aynı zamanda hata ayıklama deneyimini daha zor hale getirir. Bu, hata ayıklayıcının dışında kullanım için varsayılan değerdir.<br />-   `-enc` Düzenle ve devam et özelliğini sunar, ancak bir performans isabetini doğurur.|  
| *Değişken* = *değeri* ayarla|Kapsam içi herhangi bir değişkenin değerini değiştirir.<br /><br /> Ayrıca, kendi hata ayıklayıcı değişkenlerinizi de oluşturabilir ve onlara kendi uygulamanızdan başvuru değerleri atayabilirsiniz. Bu değerler, özgün değer kapsam dışında olsa bile, özgün değerin tanıtıcıları gibi davranır. Tüm hata ayıklayıcı değişkenlerinin ile başlaması gerekir `$` (örneğin, `$var` ). Aşağıdaki komutla onları hiçbir şey olacak şekilde ayarlayarak bu tanıtıcıları temizleyin:<br /><br /> `set $var=`|  
|**SetIP** [ `-il` ] *numarası*|Dosyadaki geçerli yönerge işaretçisini (IP) belirtilen konuma ayarlar. `-il`Seçeneğini belirtirseniz, sayı yöntemdeki bir Microsoft ara dili (MSIL) sapmasını temsil eder. Tersi durumda, sayı, bir kaynak satırı numarasını gösterir.|  
|**sh**[**ow**] [*Satırlar*]|Gösterilecek satırların sayısını belirtir.|  
|**s**[**adım**]|Yürütmeyi geçerli satırda sonraki işleve taşır veya geçilecek işlev yoksa sonraki satıra taşır.|  
|**su**[**harcama**] [ \* &#124; [~]*threadNumber*]|Geçerli iş parçacığını veya *threadNumber* parametresiyle belirtilen iş parçacığını askıya alır.  *ThreadNumber* olarak belirtilirse `*` , komut tüm iş parçacıkları için geçerli olur. İş parçacığı numarası ile başlıyorsa `~` , bu komut, *threadNumber* tarafından belirtilen biri hariç tüm iş parçacıkları için geçerlidir. İşlem, **Git** veya **adımla** komutu tarafından çalıştırıldığında, askıya alınan iş parçacıkları çalışmaya dahil edilmez. İşlemde askıya alınmamış bir iş parçacığı yoksa ve **Go** komutunu verirseniz, işlem devam etmez. Bu durumda, işleme girmek için CTRL-C tuşlarına basın.|  
|**Sy**[**mbol**] *CommandName* [*commandvalue*]|Aşağıdaki komutlardan birini belirtir:<br /><br /> -   `symbol path` [ `"value"` ]-Geçerli simge yolunu görüntüler veya ayarlar.<br />-   `symbol addpath``"value"`-Geçerli simge yolunuza ekler.<br />-   `symbol reload` [ `"module"` ]-Belirtilen modül için tüm sembolleri veya sembolleri yeniden yükler.<br />-   `symbol list` [ `module` ]-Şu anda yüklü olan sembolleri tüm modüller veya belirtilen modül için gösterir.|  
|**t**[**hread**] [*newThread*] [-*ick takma adı*`]`|Parametresiz thread komutu, geçerli işlemdeki yönetilen tüm iş parçacıklarını görüntüler. İş parçacıkları genellikle iş parçacığı numaralarıyla tanımlanır; ancak, iş parçacığının atanmış bir takma adı varsa, onun yerine takma ad görüntülenir. `-nick`Bir iş parçacığına bir takma ad atamak için parametresini kullanabilirsiniz.<br /><br /> -   **iş parçacığı** `-nick` *threadName* , çalışmakta olan iş parçacığına bir takma ad atar.<br /><br /> Takma adlar sayı olamaz. Geçerli iş parçacığına bir takma ad atandıysa, eski takma ad yenisiyle değiştirilir. Yeni takma ad boş bir dize ("") ise, geçerli iş parçacığına ilişkin takma ad silinir ve iş parçacığına yeni takma ad atanmaz.|  
|**u**[**p**]|Etkin yığın çerçevesini yukarı taşır.|  
|**uıwgc**[**tanıtıcı**] [*var*] &#124; [*Adres*]|Bir tanıtıcıyla izlenen değişkeni yazdırır. Tanıtıcı, ad veya adresle belirtilebilir.|  
|**oluşturulurken**|Şu anda etkin olan `when` deyimleri görüntüler.<br /><br />  **Tüm** &#124; ([ `num` `num` [ `num` ...]]) silindiğinde- `when` sayı tarafından belirtilen deyimi veya belirtilmişse tüm deyimleri siler `when` `all` .<br /><br /> **ne zaman** `stopReason` [ `specific_condition` ] **Do** `cmd` [ `cmd` [ `cmd` ...]]- *StopReason* parametresi aşağıdakilerden biri olabilir:<br /><br /> `StepComplete`, `ProcessExited`, `ThreadCreated`, `BreakpointHit`, `ModuleLoaded`, `ClassLoaded`, `AssemblyLoaded`, `AssemblyUnloaded`, `ControlCTrapped`, `ExceptionThrown`, `UnhandledExceptionThrown`, `AsyncStop`, `AttachComplete`, `UserBreak`, `EvalComplete`, `EvalException`, `RemapOpportunityReached`, `NativeStop`.<br /><br /> *specific_condition* aşağıdakilerden biri olabilir:<br /><br /> -    ve için sayı `ThreadCreated` `BreakpointHit` , yalnızca aynı değere sahıp bir iş parçacığı kimliği/kesme noktası numarası tarafından durdurulduğunda tetiklenir.<br />-[ `!` ]*ad* -,,,, `ModuleLoaded` `ClassLoaded` ve için `AssemblyLoaded` `AssemblyUnloaded` `ExceptionThrown` `UnhandledExceptionThrown` , yalnızca ad *stopReason* adıyla eşleştiğinde eylem tetikler.<br /><br /> *stopReason*'in diğer değerleri için *specific_condition* boş olmalıdır.|  
|**w**[**buraya**] [ `-v` ] [ `-c` *derinlik*] [*ThreadID*]|Yığın çerçevelerle ilgili hata ayıklama bilgilerini görüntüler.<br /><br /> - `-v` Seçeneği, her bir görünen yığın çerçevesi hakkında ayrıntılı bilgi sağlar.<br />-Bir sayı belirtildiğinde `depth` , kaç kare görüntülendiğini sınırlayabilirsiniz. Tüm kareleri göstermek için **All** komutunu kullanın. Varsayılan değer 100'dür.<br />- *ThreadID* parametresini belirtirseniz, yığınla hangi iş parçacığının ilişkilendirildiğini kontrol edebilirsiniz. Varsayılan değer, yalnızca geçerli iş parçacığıdır. Tüm iş parçacıklarını almak için **All** komutunu kullanın.|  
|**x** [ `-c` *numSymbols*] [*Modül*[ `!` *model*]]|Bir modül için ile eşleşen işlevleri görüntüler `pattern` .<br /><br /> *NumSymbols* belirtilmişse, çıkış belirtilen sayıyla sınırlıdır. Eğer `!` (normal bir ifadeyi gösterir), *model* için belirtilmemişse, tüm işlevler görüntülenir. *Modül* sağlanmazsa, yüklenen tüm modüller görüntülenir. Symbols ( *~#* ), **Break** komutu kullanılarak kesme noktaları ayarlamak için kullanılabilir.|  
  
## <a name="remarks"></a>Açıklamalar  

 Derleyicinizin hata ayıklama simgeleri üretmesine neden olan derleyiciye özel bayraklar kullanarak, hataları ayıklanacak uygulamayı derleyin. Bu bayraklar hakkında daha fazla bilgi için, derleyicinizin belgelerine bakın. En iyi duruma getirilen uygulamalarda hataları ayıklayabilirsiniz, fakat bazı hata ayıklama bilgileri eksik olur. Örneğin, birçok yerel değişken görünür olmaz ve kaynak satırları hatalı olur.  
  
 Uygulamanızı derledikten sonra, aşağıdaki örnekte gösterildiği gibi bir hata ayıklama oturumu başlatmak için komut istemine **MDbg** yazın.  
  
```console  
C:\Program Files\Microsoft Visual Studio 8\VC>mdbg  
MDbg (Managed debugger) v2.0.50727.42 (RTM.050727-4200) started.  
Copyright (C) Microsoft Corporation. All rights reserved.  
  
For information about commands type "help";  
to exit program type "quit".  
mdbg>  
```  
  
 `mdbg>`İstem, hata ayıklayıcıda olduğunu gösterir.  
  
 Hata ayıklayıcıya girdikten sonra, önceki bölümde açıklanan komutları bağımsız değişkenleri kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
