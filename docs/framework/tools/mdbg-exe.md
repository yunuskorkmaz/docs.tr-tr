---
title: MDbg.exe (.NET Framework Komut Satırı Hata Ayıklayıcı)
ms.date: 03/30/2017
helpviewer_keywords:
- command-line debugger [.NET Framework]
- MDbg.exe
ms.assetid: 28a3f509-07e2-4dbe-81df-874c5e969cc4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: be32659a270cd7c6b7e3551594934926eabf0d31
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="mdbgexe-net-framework-command-line-debugger"></a>MDbg.exe (.NET Framework Komut Satırı Hata Ayıklayıcı)
NET Framework Komut Satırı Hata Ayıklayıcısı, araç satıcılarının ve uygulama geliştiricilerin, .NET Framework ortak dil çalışma zamanını hedefleyen programlardaki hataları bulmalarına ve düzeltmelerine yardımcı olur. Bu araç, hata ayıklama hizmetleri sağlamak için çalışma zamanı hata ayıklama API kullanır. MDbg.exe'yi yalnızca yönetilen kodda hata ayıklamak için kullanabilirsiniz; yönetilmeyen kodda hata ayıklama desteği yoktur.  
  
 Bu araç, NuGet kullanılabilir. Yükleme bilgileri için bkz: [MDbg 0.1.0](http://www.nuget.org/packages/MDbg/0.1.0). Aracı çalıştırmak için Paket Yöneticisi konsolunu kullanın. Daha fazla bilgi için Paket Yöneticisi Konsolu kullanma hakkında [Paket Yöneticisi konsolu kullanılarak](http://docs.nuget.org/docs/start-here/Using-the-Package-Manager-Console).  
  
 Paket Yöneticisi isteminde aşağıdakileri yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
MDbg [ProgramName[arguments]] [options]  
```  
  
## <a name="commands"></a>Komutlar  
 Hata ayıklayıcıda olduğunda (belirtildiği gibi **mdbg >** istemi), sonraki bölümde açıklanan komutlardan birini yazın:  
  
 **komut** [*bağımsız değişkenleri*]  
  
 MDbg.exe komutları büyük/küçük harfe duyarlıdır.  
  
|Komut|Açıklama|  
|-------------|-----------------|  
|**AP**[**tli**] [*numarası*]|Hataları ayıklanan başka bir işleme geçer veya kullanılabilir işlemleri yazdırır. Numaralar gerçek işlem kimlikleri (PID) değil, 0-dizinli bir listedir.|  
|**bir**[**kle**] [*PID*]|Bir işleme iliştirir veya kullanılabilir işlemleri yazdırır.|  
|**b**[**ikili**] [*ClassName.Method* &#124; *FileName:LineNo*]|Belirtilen yöntemde bir kesme noktası ayarlar. Modüller sırayla taranır.<br /><br /> -   **BREAK** *FileName:LineNo* kaynak konumda bir kesme noktası ayarlar.<br />-   **BREAK** *~ numarası* bir kesme noktası ile son görüntülenen bir simge ayarlar **x** komutu.<br />-   **BREAK** *Modülü! ClassName.Method+IlOffset* bir kesme noktası tam konumuna ayarlar.|  
|**Blok**[**ingObjects**]|Engelleyici iş parçacıkları olan izleme kilitlerini görüntüler.|  
|**CA**[**ürünün**] [*exceptionType*]|Hata ayıklayıcının, yalnızca işlenmeyen özel durumları değil, tüm özel durumları kesmesine neden olur.|  
|**cl**[**earException**]|Yürütmenin devam edebilmesi için, geçerli özel durumu işlenmiş olarak işaretler. Özel durumun nedeniyle ilgilenilmediyse, özel durum hızlı bir şekilde yeniden oluşturulabilir.|  
|**conf**[**ig**] [*seçenek değerini*]|Tüm yapılandırılabilir seçenekleri görüntüler ve seçeneklerin isteğe bağlı değerler olmadan nasıl çağrılabileceğini gösterir. Seçeneği belirtildiyse, ayarlar `value` geçerli seçeneği olarak. Aşağıdaki seçenekler şu anda kullanılabilir:<br /><br /> -   `extpath` uzantıları için aranacak yolunu ayarlar zaman `load` komutu kullanılır.<br />-   `extpath+` Uzantıları yükleme için bir yol ekler.|  
|**del**[**Sil**]|Bir kesme noktasını siler.|  
|**de**[**tach**]|Hata ayıklaması yapılmış bir işlemden ayırır.|  
|**d**[**kendi**] [*çerçeveler*]|Etkin yığın çerçevesini aşağı taşır.|  
|**echo**|Bir iletiyi konsola yankılatır.|  
|**enableNotif**[**ication**] *typeName* 0&#124;1|Belirtilen tür için özel bildirimleri etkinleştirir (1) veya devre dışı bırakır (0).|  
|**Ex**[**,**] [*exitcode*]|MDbg.exe kabuğundan çıkar ve isteğe bağlı olarak işlem çıkış kodunu belirtir.|  
|**FO**[**ulaşmak**] [*OtherCommand*]|Bir komutu tüm iş parçacıkları üzerinde uygular. *OtherCommand* bir iş parçacığında; çalışır geçerli bir komutu **foreach** *OtherCommand* tüm iş parçacıklarının üzerinde aynı komutu gerçekleştirir.|  
|**f**[**unceval**] [`-ad` *Num*] *functionName* [*args...*  ]|Bir işlev değerlendirmesi işlevin değerlendirileceği nerede geçerli etkin iş parçacığı üzerinde gerçekleştirir *functionName*. İşlev adı, ad alanları da dahil olmak üzere tam olarak nitelenmiş olmalıdır.<br /><br /> `-ad` Seçeneği işlevi çözümlemek için uygulama etki alanını belirtir. Varsa `-ad` seçeneği belirtilmezse, çözümleme için uygulama etki alanı işlev değerlendirmesi için kullanılan iş parçacığı bulunduğu uygulama etki alanı için varsayılan olarak belirlenir.<br /><br /> Şu anda değerlendiriliyor işlevi statik değilse, geçirilen ilk parametre olmalıdır bir `this` işaretçi. Tüm uygulama etki alanlarında, işlev değerlendirmesi bağımsız değişkenleri için arama yapılır.<br /><br /> Bir uygulama etki alanından bir değer istemek için değişken modül ve uygulama etki alanı adı ile önek; Örneğin, `funceval -ad 0 System.Object.ToString hello.exe#0!MyClass.g_rootRef`. Bu komut işlevi değerlendirir `System.Object.ToString` uygulama etki alanında `0`. Çünkü `ToString` yöntemi bir örnek işlevi, ilk parametre olmalıdır bir `this` işaretçi.|  
|**g**[**o**]|Programın bir kesme noktasıyla karşılaşıncaya, programdan çıkılıncaya veya bir olay (örneğin, işlenmemiş bir özel durum) programın durmasına neden oluncaya kadar devam etmesine neden olur.|  
|**h**[**ardım**] [*komutu*]<br /><br /> -veya-<br /><br /> **?** [*komutu*]|Tüm komutların açıklamasını veya belirtilen bir komutun ayrıntılı açıklamasını görüntüler.|  
|**ig**[**Yoksay**] [*olay*]|Hata ayıklayıcının yalnızca işlenmemiş özel durumlarda durmasına neden olur.|  
|**int**[**ercept**] *FrameNumber*|Hata ayıklayıcıyı belirtilen bir çerçeve numarasına geri döndürür.<br /><br /> Hata ayıklayıcı bir özel durumla karşılaşırsa, hata ayıklayıcıyı belirtilen kare numarasına geri döndürmek için bu komutu kullanın. Program durumu kullanarak değiştirebilirsiniz **ayarlamak** komut ve kullanarak devam **Git** komutu.|  
|**k**[**hatalı**]|Etkin işlemi durdurur.|  
|**l**[**ist**] [*modülleri* &#124; *appdomains oluşturuyor* &#124; *derlemeleri*]|Yüklü modülleri, uygulama etki alanlarını veya derlemeleri görüntüler.|  
|**aet.aet**[**ad**] *assemblyName*|Aşağıdaki şekilde bir uzantıyı yükler: Belirtilen derleme yüklenir ve ardından statik yöntemi çalıştırmak için girişimde `LoadExtension` gelen `Microsoft.Tools.Mdbg.Extension.Extension` türü.|  
|**Günlük** [*eventType*]|Günlüğe kaydedilecek olayları ayarlayın veya görüntüleyin.|  
|**iletilerin**[**de**] [*seçeneği açık/kapalı*]|Farklı hata ayıklayıcı seçeneklerini ayarlar. Kullanım `mode` hata ayıklama modlarını ve geçerli ayarları listesini almak için hiçbir seçenek.|  
|**MON**[**itorInfo**] *monitorReference*|Nesne izleme kilidi bilgilerini görüntüler.|  
|**newo**[**bj**] *typeName* [*bağımsız değişkenleri...* ]|Yeni bir nesne türü oluşturur *typeName*.|  
|**n**[**ext**]|Kodu çalıştırır ve sonraki satıra geçer (sonraki satır birçok işlev çağrısı içerse bile).|  
|**Opendump** *pathToDumpFile*|Hata ayıklama için belirtilen döküm dosyasını açar.|  
|**o**[**ut**]|Geçerli işlevin sonuna taşır.|  
|**Pa**[**th**] [*pathName*]|İkililerdeki konum kullanılabilir değilse, belirtilen yolda kaynak dosyalarını arar.|  
|**p**[**azdır**] [*var*] &#124; [`-d`]|Kapsamdaki tüm değişkenleri yazdırır (**yazdırma**), belirtilen değişkeni yazdırır (**yazdırma** *var*), ya da hata ayıklayıcı değişkenleri yazdırır (**yazdırma** `-d`).|  
|**printe**[**zel durum**] [*- r*]|Geçerli iş parçacığındaki son özel durumu yazdırır. Kullanım `–r` gezinmesine (yinelemeli) seçeneğini `InnerException` tüm zincir özel durumlar hakkında bilgi almak için özel durum nesnesi özelliği.|  
|**Pro**[**cessenum**]|Etkin işlemleri görüntüler.|  
|**q**[**IK**] [*exitcode*]|İsteğe bağlı olarak işlem çıkış kodunu belirterek, MDbg.exe kabuğundan çıkar.|  
|**RE**[**Et**] [`*` &#124; [`~`]*threadNumber*]|Geçerli iş parçacığının veya tarafından belirtilen iş parçacığı sürdürür *threadNumber* parametresi.<br /><br /> Varsa *threadNumber* parametre olarak belirtilen `*` veya iş parçacığı sayısı ile başlarsa `~`, komut tarafından belirtilen dışındaki tüm iş parçacıklarının uygulanır *threadNumber*.<br /><br /> Askıya alınmamış bir iş parçacığını sürdürmenin etkisi yoktur.|  
|**r**[**kaydını**] [`-d`(`ebug`) &#124; -`o`(`ptimize`) &#124; `-enc`] [[*path_to_exe*] [*bağımsız değişken _to_exe*]]|Geçerli işlemi (varsa) durdurur ve yeni bir işlem başlatır. Yürütülebilir bağımsız değişken aktarılırsa, bu komutu ile daha önce yürütüldü programı çalıştırır `run` komutu. Yürütülebilir bağımsız değişkeni sağlanırsa, belirtilen program isteğe bağlı olarak sağlanan bağımsız değişkenler kullanılarak çalıştırır.<br /><br /> Sınıf yükleme, modül yükleme ve iş parçacığı başlatma olayları yoksayılırsa (varsayılan olarak yoksayıldıkları gibi), program, ana iş parçacığının il yürütülebilir yönergesinde durur.<br /><br /> Aşağıdaki üç bayraktan birini kullanarak, hata ayıklayıcıyı kodu tam zamanında (JIT) derlemeye zorlayabilirsiniz:<br /><br /> -   `-d` *(* `ebug` *)* iyileştirmeleri devre dışı bırakır. Bu, MDbg.exe için varsayılan değerdir.<br />-   `-o` *(* `ptimize` *)* hata ayıklayıcı dışında yapar ancak de hata ayıklama deneyimini zorlaştırır gibi daha fazla çalıştırmak için kod zorlar. Bu, hata ayıklayıcının dışında kullanım için varsayılan değerdir.<br />-   `-enc` Düzenle ve devam et özelliği sağlar, ancak performans isabet doğurur.|  
|**Ayarlama** *değişkeni*=*değeri*|Kapsam içi herhangi bir değişkenin değerini değiştirir.<br /><br /> Ayrıca, kendi hata ayıklayıcı değişkenlerinizi de oluşturabilir ve onlara kendi uygulamanızdan başvuru değerleri atayabilirsiniz. Bu değerler, özgün değer kapsam dışında olsa bile, özgün değerin tanıtıcıları gibi davranır. Tüm hata ayıklayıcı değişkenleri ile başlamalıdır `$` (örneğin, `$var`). Aşağıdaki komutla onları hiçbir şey olacak şekilde ayarlayarak bu tanıtıcıları temizleyin:<br /><br /> `set $var=`|  
|**SetIP** [`-il`] *numarası*|Dosyadaki geçerli yönerge işaretçisini (IP) belirtilen konuma ayarlar. Belirtirseniz `-il` seçeneği, sayı, yönteminde uzaklığı bir Microsoft Ara dili (MSIL) temsil eder. Tersi durumda, sayı, bir kaynak satırı numarasını gösterir.|  
|**paylaş**[**onumu**] [*satırları*]|Gösterilecek satırların sayısını belirtir.|  
|**s**[**adım**]|Yürütmeyi geçerli satırda sonraki işleve taşır veya geçilecek işlev yoksa sonraki satıra taşır.|  
|**Su**[**harcamanız**] [\* &#124; [~]*threadNumber*]|Geçerli iş parçacığının veya tarafından belirtilen iş parçacığı askıya *threadNumber* parametresi.  Varsa *threadNumber* olarak belirtilen `*`, tüm iş parçacıklarının komutu uygular. İş parçacığı sayısı ile başlarsa `~`, komut tarafından belirtilen dışındaki tüm iş parçacıklarının uygulanır *threadNumber*. Askıya alınan iş parçacığı işlemi tarafından çalıştırıldığında çalışmasını dışlanır **Git** veya **adım** komutu. İşlem sırasında askıya olmayan iş parçacığı vardır ve dağıttığınız **Git** komutu, işlem devam etmeyecek. Bu durumda, işleme girmek için CTRL-C tuşlarına basın.|  
|**SY**[**simge**] *commandName* [*commandValue*]|Aşağıdaki komutlardan birini belirtir:<br /><br /> -   `symbol path` [`"``value``"`]-Görüntüler veya geçerli simge yolunu ayarlar.<br />-   `symbol addpath` `"` `value` `"` -Geçerli simgesi yola ekler.<br />-   `symbol reload` [`"``module``"`]-Tüm sembolleri veya belirtilen modül simgelerini yeniden yükler.<br />-   `symbol list` [`module`]-Şu anda yüklü olan tüm modülleri veya belirtilen modül simgelerini gösterir.|  
|**t**[**iş**] [*newThread*] [-*nick takma adı*`]`|Parametresiz thread komutu, geçerli işlemdeki yönetilen tüm iş parçacıklarını görüntüler. İş parçacıkları genellikle iş parçacığı numaralarıyla tanımlanır; ancak, iş parçacığının atanmış bir takma adı varsa, onun yerine takma ad görüntülenir. Kullanabileceğiniz `-nick` iş parçacığı için takma ad atamak için parametre.<br /><br /> -   **iş parçacığı** `-nick` *threadName* şu anda çalışan iş parçacığı için takma ad atar.<br /><br /> Takma adlar sayı olamaz. Geçerli iş parçacığına bir takma ad atandıysa, eski takma ad yenisiyle değiştirilir. Yeni takma ad boş bir dize ("") ise, geçerli iş parçacığına ilişkin takma ad silinir ve iş parçacığına yeni takma ad atanmaz.|  
|**u**[**p**]|Etkin yığın çerçevesini yukarı taşır.|  
|**uwgc**[**işlemek**] [*var*] &#124; [*adresi*]|Bir tanıtıcıyla izlenen değişkeni yazdırır. Tanıtıcı, ad veya adresle belirtilebilir.|  
|**ne zaman**|Şu anda etkin görüntüler `when` deyimleri.<br /><br /> **zaman** **tüm silmek** &#124; `num` [`num` [`num` ...]]-siler `when` sayısını veya tüm ile belirtilen deyim `when` deyimleri varsa `all` belirtildi.<br /><br /> **zaman** `stopReason` [`specific_condition`] **yapmak** `cmd` [`cmd` [`cmd` ...]] - *stopReason* parametresi şunlardan biri olabilir:<br /><br /> `StepComplete`, `ProcessExited`, `ThreadCreated`, `BreakpointHit`, `ModuleLoaded`, `ClassLoaded`, `AssemblyLoaded`, `AssemblyUnloaded`, `ControlCTrapped`, `ExceptionThrown`, `UnhandledExceptionThrown`, `AsyncStop`, `AttachComplete`, `UserBreak`, `EvalComplete`, `EvalException`, `RemapOpportunityReached`, `NativeStop`.<br /><br /> *specific_condition* şunlardan biri olabilir:<br /><br /> -   *sayı* - `ThreadCreated` ve `BreakpointHit`, yalnızca bir iş parçacığı kimliği/kesme noktası ile aynı değeri sayı olarak durduğunda eylemi tetikler.<br />-[`!`]*adı* - `ModuleLoaded`, `ClassLoaded`, `AssemblyLoaded`, `AssemblyUnloaded`, `ExceptionThrown`, ve `UnhandledExceptionThrown`, yalnızca ad adı eşleştiğinde eylemi tetikler  *stopReason*.<br /><br /> *specific_condition* diğer değerleri için boş olmalıdır *stopReason*.|  
|**w**[**burada**] [`-v`] [`-c` *derinliği*] [*ThreadID*]|Yığın çerçevelerle ilgili hata ayıklama bilgilerini görüntüler.<br /><br /> - `-v` Seçeneği her görüntülenen yığın çerçevesi hakkında ayrıntılı bilgi sağlar.<br />-Belirten bir sayı için `depth` kaç kare görüntüleneceğini sınırlar. Kullanım **tüm** tüm çerçevelerini komutu. Varsayılan değer 100'dür.<br />-Belirtirseniz *ThreadID* parametresini, hangi iş parçacığı yığın ile ilişkilendirilen kontrol edebilirsiniz. Varsayılan değer, yalnızca geçerli iş parçacığıdır. Kullanım **tüm** tüm iş parçacıklarının alabilirsiniz.|  
|**x** [`-c`*numSymbols*] [*Modülü*[`!`*düzeni*]]|Eşleşen işlevleri görüntüler `pattern` modülü için.<br /><br /> Varsa *numSymbols* belirtilirse, belirtilen sayıya çıkış sınırlıdır. Varsa `!` (belirten bir normal ifade) belirtilmezse için *düzeni*, tüm işlevleri görüntülenir. Varsa *Modülü* yüklü olan tüm modülleri görüntülenmez sağlanır. Simgeler (*~#*) kullanarak kesme noktaları ayarlamak için kullanılan **sonu** komutu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Derleyicinizin hata ayıklama simgeleri üretmesine neden olan derleyiciye özel bayraklar kullanarak, hataları ayıklanacak uygulamayı derleyin. Bu bayraklar hakkında daha fazla bilgi için, derleyicinizin belgelerine bakın. En iyi duruma getirilen uygulamalarda hataları ayıklayabilirsiniz, fakat bazı hata ayıklama bilgileri eksik olur. Örneğin, birçok yerel değişken görünür olmaz ve kaynak satırları hatalı olur.  
  
 Uygulamanızı derledikten sonra yazın **mdbg** aşağıdaki örnekte gösterildiği gibi bir hata ayıklama oturumu başlatmak için komut isteminde.  
  
```  
C:\Program Files\Microsoft Visual Studio 8\VC>mdbg  
MDbg (Managed debugger) v2.0.50727.42 (RTM.050727-4200) started.  
Copyright (C) Microsoft Corporation. All rights reserved.  
  
For information about commands type "help";  
to exit program type "quit".  
mdbg>  
```  
  
 `mdbg>` İstemi Hata Ayıklayıcısı'ndaki olduğunu gösterir.  
  
 Hata ayıklayıcıya girdikten sonra, önceki bölümde açıklanan komutları bağımsız değişkenleri kullanın.  
  
## <a name="examples"></a>Örnekler  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Araçlar](../../../docs/framework/tools/index.md)  
 [Komut İstemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
