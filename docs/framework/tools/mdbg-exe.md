---
title: MDbg.exe (.NET Framework Komut Satırı Hata Ayıklayıcı)
ms.date: 03/30/2017
helpviewer_keywords:
- command-line debugger [.NET Framework]
- MDbg.exe
ms.assetid: 28a3f509-07e2-4dbe-81df-874c5e969cc4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e5320bc6c5105c95d63b1888e1adbc2ecf1bc5fb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59200005"
---
# <a name="mdbgexe-net-framework-command-line-debugger"></a>MDbg.exe (.NET Framework Komut Satırı Hata Ayıklayıcı)
NET Framework Komut Satırı Hata Ayıklayıcısı, araç satıcılarının ve uygulama geliştiricilerin, .NET Framework ortak dil çalışma zamanını hedefleyen programlardaki hataları bulmalarına ve düzeltmelerine yardımcı olur. Bu araç, hata ayıklama hizmetleri sağlamak için çalışma zamanı hata ayıklama API kullanır. MDbg.exe'yi yalnızca yönetilen kodda hata ayıklamak için kullanabilirsiniz; yönetilmeyen kodda hata ayıklama desteği yoktur.  
  
Bu araç, NuGet kullanılabilir. Yükleme bilgileri için bkz. [MDbg 0.1.0](https://www.nuget.org/packages/MDbg/0.1.0). Aracı çalıştırmak için Paket Yöneticisi konsolu kullanın. Paket Yöneticisi Konsolu kullanma hakkında daha fazla bilgi için bkz. [Paket Yöneticisi Konsolu](/nuget/tools/package-manager-console) makalesi.
  
Paket Yöneticisi isteminde aşağıdaki komutu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
MDbg [ProgramName[arguments]] [options]  
```  
  
## <a name="commands"></a>Komutlar  
 Hata ayıklayıcıda olduğunuzda (gösterildiği gibi **mdbg >** istemi), sonraki bölümde açıklanan komutlardan birini yazın:  
  
 **komut** [*bağımsız değişkenleri*]  
  
 MDbg.exe komutları büyük/küçük harfe duyarlıdır.  
  
|Komut|Açıklama|  
|-------------|-----------------|  
|**AP**[**şlem**] [*numarası*]|Hataları ayıklanan başka bir işleme geçer veya kullanılabilir işlemleri yazdırır. Numaralar gerçek işlem kimlikleri (PID) değil, 0-dizinli bir listedir.|  
|**bir**[**kle**] [*PID*]|Bir işleme iliştirir veya kullanılabilir işlemleri yazdırır.|  
|**b**[**reak**] [*ClassName.Method* &#124; *FileName:LineNo*]|Belirtilen yöntemde bir kesme noktası ayarlar. Modüller sırayla taranır.<br /><br /> -   **Kesme** *Lineno* kaynaktaki bir konumda bir kesme noktası ayarlar.<br />-   **Kesme** *~ number* son görüntülenen bir simge üzerinde bir kesme noktası ayarlar **x** komutu.<br />-   **Kesme** *Modülü! ClassName.Method+IlOffset* üzerinde tam olarak belirtilen konumda bir kesme noktası ayarlar.|  
|**Blok**[**; ingobjects &**]|Engelleyici iş parçacıkları olan izleme kilitlerini görüntüler.|  
|**CA**[**eğiştir**] [*exceptionType*]|Hata ayıklayıcının, yalnızca işlenmeyen özel durumları değil, tüm özel durumları kesmesine neden olur.|  
|**cl**[**; earexception &**]|Yürütmenin devam edebilmesi için, geçerli özel durumu işlenmiş olarak işaretler. Özel durumun nedeniyle ilgilenilmediyse, özel durum hızlı bir şekilde yeniden oluşturulabilir.|  
|**conf**[**ig**] [*seçenek değerini*]|Tüm yapılandırılabilir seçenekleri görüntüler ve seçeneklerin isteğe bağlı değerler olmadan nasıl çağrılabileceğini gösterir. Seçeneği belirtilmezse, ayarlar `value` geçerli seçenek olarak. Aşağıdaki seçenekler şu anda kullanılabilir:<br /><br /> -   `extpath` Aranacak uzantılar için yolu ayarlar olduğunda `load` komutu kullanılır.<br />-   `extpath+` uzantıları yüklemek için bir yol ekler.|  
|**del**[**Sil**]|Bir kesme noktasını siler.|  
|**de**[**yır**]|Hata ayıklaması yapılmış bir işlemden ayırır.|  
|**d**[**kendi**] [*çerçeveler*]|Etkin yığın çerçevesini aşağı taşır.|  
|**echo**|Bir iletiyi konsola yankılatır.|  
|**enableNotif**[**ication &**] *typeName* 0&#124;1|Belirtilen tür için özel bildirimleri etkinleştirir (1) veya devre dışı bırakır (0).|  
|**ex**[**it**] [*exitcode*]|MDbg.exe kabuğundan çıkar ve isteğe bağlı olarak işlem çıkış kodunu belirtir.|  
|**fo**[**reach**] [*OtherCommand*]|Bir komutu tüm iş parçacıkları üzerinde uygular. *OtherCommand* işleyen bir iş parçacığında; geçerli bir komuttur **foreach** *OtherCommand* aynı komutu tüm iş parçacıkları üzerinde çalıştırır.|  
|**f**[**unceval**] [`-ad` *Num*] *functionName* [*args...*  ]|Değerlendirilecek işlevin olduğu geçerli etkin iş parçacığı üzerinde İşlev değerlendirmesi gerçekleştirir *functionName*. İşlev adı, ad alanları da dahil olmak üzere tam olarak nitelenmiş olmalıdır.<br /><br /> `-ad` Seçeneği işlevi çözümlemede kullanmak için uygulama etki alanını belirtir. Varsa `-ad` seçeneği belirtilmezse, uygulama etki çözümlemesi için varsayılan olarak, İşlev değerlendirmesi için kullanılan iş parçacığının bulunduğu uygulama etki alanı.<br /><br /> Değerlendirilmekte olan işlev statik değilse, geçirilen ilk parametre olmalıdır bir `this` işaretçi. Tüm uygulama etki alanlarında, işlev değerlendirmesi bağımsız değişkenleri için arama yapılır.<br /><br /> Bir uygulama etki alanından bir değer istemek için değişkenin önüne modül ve uygulama etki alanı adı ön eki; Örneğin, `funceval -ad 0 System.Object.ToString hello.exe#0!MyClass.g_rootRef`. Bu komut işlevi değerlendirir `System.Object.ToString` uygulama etki alanındaki `0`. Çünkü `ToString` yöntemi bir örnek işlevi, birinci parametre olmalıdır bir `this` işaretçi.|  
|**g**[**o**]|Programın bir kesme noktasıyla karşılaşıncaya, programdan çıkılıncaya veya bir olay (örneğin, işlenmemiş bir özel durum) programın durmasına neden oluncaya kadar devam etmesine neden olur.|  
|**h**[**elp**] [*komut*]<br /><br /> -veya-<br /><br /> **?** [*command*]|Tüm komutların açıklamasını veya belirtilen bir komutun ayrıntılı açıklamasını görüntüler.|  
|**ig**[**Yoksay**] [*olay*]|Hata ayıklayıcının yalnızca işlenmemiş özel durumlarda durmasına neden olur.|  
|**int**[**ercept &**] *FrameNumber*|Hata ayıklayıcıyı belirtilen bir çerçeve numarasına geri döndürür.<br /><br /> Hata ayıklayıcı bir özel durumla karşılaşırsa, hata ayıklayıcıyı belirtilen kare numarasına geri döndürmek için bu komutu kullanın. Kullanarak program durumunu değiştirebilir **ayarlamak** komut ve kullanarak devam **Git** komutu.|  
|**k**[**olgu**]|Etkin işlemi durdurur.|  
|**l**[**ist**] [*modules* &#124; *appdomains* &#124; *assemblies*]|Yüklü modülleri, uygulama etki alanlarını veya derlemeleri görüntüler.|  
|**lo**[**ad**] *assemblyName*|Aşağıdaki şekilde bir uzantı yükler: Belirtilen derleme yüklenir ve girişiminin ardından statik yöntemi çalıştırmak için yapılan `LoadExtension` gelen `Microsoft.Tools.Mdbg.Extension.Extension` türü.|  
|**Günlük** [*eventType*]|Günlüğe kaydedilecek olayları ayarlayın veya görüntüleyin.|  
|**ay**[**de**] [*seçeneği açık/kapalı*]|Farklı hata ayıklayıcı seçeneklerini ayarlar. Kullanım `mode` hata ayıklama modlarının ve geçerli ayarlarının listesini almak için hiçbir seçenek olmadan.|  
|**Pzt**[**itorınfo &**] *monitorReference*|Nesne izleme kilidi bilgilerini görüntüler.|  
|**newo**[**bj**] *typeName* [*arguments...* ]|Yeni bir nesne türünün oluşturur *typeName*.|  
|**n**[**ext**]|Kodu çalıştırır ve sonraki satıra geçer (sonraki satır birçok işlev çağrısı içerse bile).|  
|**Opendump** *pathToDumpFile*|Hata ayıklama için belirtilen döküm dosyasını açar.|  
|**o**[**ut**]|Geçerli işlevin sonuna taşır.|  
|**Pa**[**th**] [*pathName*]|İkililerdeki konum kullanılabilir değilse, belirtilen yolda kaynak dosyalarını arar.|  
|**p**[**rint**] [*var*] &#124; [`-d`]|Kapsamdaki tüm değişkenleri yazdırır (**yazdırma**), belirtilen değişkeni yazdırır (**yazdırma** *var*), veya hata ayıklayıcı değişkenleri yazdırır (**yazdırma** `-d`).|  
|**printe**[**zel durum**] [*- r*]|Geçerli iş parçacığındaki son özel durumu yazdırır. Kullanım `–r` geçirilecek (yinelemeli) seçeneğini `InnerException` özelliği zinciriyle hakkında bilgi almak için özel durum nesnesi.|  
|**pro**[**cessenum**]|Etkin işlemleri görüntüler.|  
|**q**[**; uit &**] [*exitcode*]|İsteğe bağlı olarak işlem çıkış kodunu belirterek, MDbg.exe kabuğundan çıkar.|  
|**re**[**sume**] [`*` &#124; [`~`]*threadNumber*]|Geçerli iş parçacığı veya tarafından belirtilen iş parçacığını sürdürür *threadNumber* parametresi.<br /><br /> Varsa *threadNumber* parametre olarak belirtilen `*` veya iş parçacığı numarası ile başlarsa `~`, komut tarafından belirtilen tüm iş parçacıklarına uygulanır *threadNumber*.<br /><br /> Askıya alınmamış bir iş parçacığını sürdürmenin etkisi yoktur.|  
|**r**[**un**] [`-d`(`ebug`) &#124; -`o`(`ptimize`) &#124;`-enc`] [[*path_to_exe*] [*args_to_exe*]]|Geçerli işlemi (varsa) durdurur ve yeni bir işlem başlatır. Yürütülebilir hiçbir bağımsız değişken geçirilmezse, bu komut, daha önce yürütülen programı çalıştırır. `run` komutu. Yürütülebilir bağımsız değişkeni sağlanırsa, belirtilen program isteğe bağlı olarak sağlanan bağımsız değişkenler kullanılarak çalıştırır.<br /><br /> Sınıf yükleme, modül yükleme ve iş parçacığı başlatma olayları yoksayılırsa (varsayılan olarak yoksayıldıkları gibi), program, ana iş parçacığının il yürütülebilir yönergesinde durur.<br /><br /> Aşağıdaki üç bayraktan birini kullanarak, hata ayıklayıcıyı kodu tam zamanında (JIT) derlemeye zorlayabilirsiniz:<br /><br /> -   `-d` *(* `ebug` *)* iyileştirmeleri devre dışı bırakır. Bu, MDbg.exe için varsayılan değerdir.<br />-   `-o` *(* `ptimize` *)* , hata ayıklayıcı dışında desteklemez, ancak hata ayıklama deneyimini de daha zor hale getirir gibi daha fazla çalıştırma için kod zorlar. Bu, hata ayıklayıcının dışında kullanım için varsayılan değerdir.<br />-   `-enc` Düzenle ve devam et özelliğini etkinleştirir, fakat bir performans düşüşüne neden olur.|  
|**Ayarlama** *değişkeni*=*değeri*|Kapsam içi herhangi bir değişkenin değerini değiştirir.<br /><br /> Ayrıca, kendi hata ayıklayıcı değişkenlerinizi de oluşturabilir ve onlara kendi uygulamanızdan başvuru değerleri atayabilirsiniz. Bu değerler, özgün değer kapsam dışında olsa bile, özgün değerin tanıtıcıları gibi davranır. Tüm hata ayıklayıcı değişkenleri ile başlamalıdır `$` (örneğin, `$var`). Aşağıdaki komutla onları hiçbir şey olacak şekilde ayarlayarak bu tanıtıcıları temizleyin:<br /><br /> `set $var=`|  
|**SetIP** [`-il`] *numarası*|Dosyadaki geçerli yönerge işaretçisini (IP) belirtilen konuma ayarlar. Belirtirseniz `-il` seçeneği, sayı, yöntemde uzaklığı bir Microsoft Ara dilini (MSIL) temsil eder. Tersi durumda, sayı, bir kaynak satırı numarasını gösterir.|  
|**sh**[**Göster**] [*satırları*]|Gösterilecek satırların sayısını belirtir.|  
|**s**[**adım**]|Yürütmeyi geçerli satırda sonraki işleve taşır veya geçilecek işlev yoksa sonraki satıra taşır.|  
|**Su**[**harcama**] [\* &#124; [~]*threadNumber*]|Geçerli iş parçacığı veya tarafından belirtilen iş parçacığını askıya *threadNumber* parametresi.  Varsa *threadNumber* olarak belirtilen `*`, komut tüm iş parçacıkları için geçerlidir. İş parçacığı numarası ile başlarsa `~`, komut tarafından belirtilen tüm iş parçacıklarına uygulanır *threadNumber*. Askıya alınan iş parçacığı, işlem ya da yeniden çalıştırdığınızda çalışmasını dışlanır **Git** veya **adım** komutu. İşlemde askıya alınmamış iş parçacığı vardır ve dağıttığınız **Git** komutu, işlem devam etmez. Bu durumda, işleme girmek için CTRL-C tuşlarına basın.|  
|**SY**[**simge**] *commandName* [*gt; commandvalue &*]|Aşağıdaki komutlardan birini belirtir:<br /><br /> -   `symbol path` [`"value"`]-Görüntüler veya geçerli simge yolunu ayarlar.<br />-   `symbol addpath` `"value"` -Geçerli simge yolunuza ekler.<br />-   `symbol reload` [`"module"`]-Tüm simgeleri veya belirtilen modüle ilişkin simgeleri yeniden yükler.<br />-   `symbol list` [`module`]-Tüm modüller veya belirtilen modül için yüklenmiş olan simgeleri gösterir.|  
|**t**[**hread**] [*gt; newThread*] [-*nick Takmaad*`]`|Parametresiz thread komutu, geçerli işlemdeki yönetilen tüm iş parçacıklarını görüntüler. İş parçacıkları genellikle iş parçacığı numaralarıyla tanımlanır; ancak, iş parçacığının atanmış bir takma adı varsa, onun yerine takma ad görüntülenir. Kullanabileceğiniz `-nick` bir iş parçacığına bir takma ad atamak için parametre.<br /><br /> -   **iş parçacığı** `-nick` *threadName* çalışmakta olan iş parçacığına bir takma ad atar.<br /><br /> Takma adlar sayı olamaz. Geçerli iş parçacığına bir takma ad atandıysa, eski takma ad yenisiyle değiştirilir. Yeni takma ad boş bir dize ("") ise, geçerli iş parçacığına ilişkin takma ad silinir ve iş parçacığına yeni takma ad atanmaz.|  
|**u**[**p**]|Etkin yığın çerçevesini yukarı taşır.|  
|**uwgc**[**handle**] [*var*] &#124; [*address*]|Bir tanıtıcıyla izlenen değişkeni yazdırır. Tanıtıcı, ad veya adresle belirtilebilir.|  
|**Ne zaman**|Şu anda etkin görüntüler `when` deyimleri.<br /><br /> **zaman** **Tümünü Sil** &#124; `num` [`num` [`num` ...]]-siler `when` ifade sayı veya tüm belirtilen `when` deyimleri, `all` belirtilir.<br /><br /> **zaman** `stopReason` [`specific_condition`] **yapmak** `cmd` [`cmd` [`cmd` ...]] - *; stopreason &* parametresi aşağıdakilerden biri olabilir:<br /><br /> `StepComplete`, `ProcessExited`, `ThreadCreated`, `BreakpointHit`, `ModuleLoaded`, `ClassLoaded`, `AssemblyLoaded`, `AssemblyUnloaded`, `ControlCTrapped`, `ExceptionThrown`, `UnhandledExceptionThrown`, `AsyncStop`, `AttachComplete`, `UserBreak`, `EvalComplete`, `EvalException`, `RemapOpportunityReached`, `NativeStop`.<br /><br /> *specific_condition* aşağıdakilerden biri olabilir:<br /><br /> -   *sayı* - `ThreadCreated` ve `BreakpointHit`, yalnızca bir iş parçacığı Tanıtıcısı/kesme noktası ile aynı değeri sayı durdurulduklarında eylem tetikler.<br />-[`!`]*adı* - `ModuleLoaded`, `ClassLoaded`, `AssemblyLoaded`, `AssemblyUnloaded`, `ExceptionThrown`, ve `UnhandledExceptionThrown`, yalnızca ad adını eşleştiğinde eylem tetikler  *stopreason &*.<br /><br /> *specific_condition* diğer değerleri için boş olmalıdır *; stopreason &*.|  
|**w**[**burada**] [`-v`] [`-c` *derinliği*] [*ThreadID*]|Yığın çerçevelerle ilgili hata ayıklama bilgilerini görüntüler.<br /><br /> - `-v` Seçeneği her görüntülenen yığın çerçevesi hakkında ayrıntılı bilgi sağlar.<br />-Belirten bir sayı için `depth` görüntülenecek çerçeve sınırlar. Kullanım **tüm** tüm çerçeveleri görüntülemek için komutu. Varsayılan değer 100'dür.<br />-Belirtirseniz *ThreadID* parametresi, yığınla hangi iş parçacığının ilişkilendirilen denetleyebilirsiniz. Varsayılan değer, yalnızca geçerli iş parçacığıdır. Kullanım **tüm** tüm iş parçacıklarını almak için komutu.|  
|**x** [`-c`*numSymbols*] [*Modülü*[`!`*deseni*]]|İle eşleşen işlevleri görüntüler `pattern` bir modül için.<br /><br /> Varsa *numSymbols* belirtilirse, çıkış belirtilen sayıyla sınırlandırılır. Varsa `!` (normal bir ifadeyi gösterir) belirtilmezse için *deseni*, tüm işlevler görüntülenir. Varsa *Modülü* değil tüm yüklü modüller görüntülenir sağlanır. Semboller (*~#*) kullanılarak kesme noktaları ayarlamak için kullanılan **sonu** komutu.|  
  
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
  
 `mdbg>` İstemi, hata ayıklayıcıda olduğunuzu gösterir.  
  
 Hata ayıklayıcıya girdikten sonra, önceki bölümde açıklanan komutları bağımsız değişkenleri kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](../../../docs/framework/tools/index.md)
- [Komut İstemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
