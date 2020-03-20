---
title: MDbg.exe (.NET Framework Komut Satırı Hata Ayıklayıcı)
ms.date: 03/30/2017
helpviewer_keywords:
- command-line debugger [.NET Framework]
- MDbg.exe
ms.assetid: 28a3f509-07e2-4dbe-81df-874c5e969cc4
ms.openlocfilehash: 58502626fed6c9cee52acb673ae34f6024f78b9b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75715762"
---
# <a name="mdbgexe-net-framework-command-line-debugger"></a>MDbg.exe (.NET Framework Komut Satırı Hata Ayıklayıcı)
NET Framework Komut Satırı Hata Ayıklayıcısı, araç satıcılarının ve uygulama geliştiricilerin, .NET Framework ortak dil çalışma zamanını hedefleyen programlardaki hataları bulmalarına ve düzeltmelerine yardımcı olur. Bu araç, hata ayıklama hizmetleri sağlamak için çalışma zamanı hata ayıklama API kullanır. MDbg.exe'yi yalnızca yönetilen kodda hata ayıklamak için kullanabilirsiniz; yönetilmeyen kodda hata ayıklama desteği yoktur.  
  
Bu araç NuGet üzerinden kullanılabilir. Kurulum bilgileri için Bkz. [MDbg 0.1.0](https://www.nuget.org/packages/MDbg/0.1.0). Aracı çalıştırmak için Paket Yöneticisi Konsolu'nu kullanın. Paket Yöneticisi Konsolu'nun nasıl kullanılacağı hakkında daha fazla bilgi için [Paket Yöneticisi Konsolu](/nuget/tools/package-manager-console) makalesine bakın.
  
Paket Yöneticisi isteminde aşağıdakileri yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
MDbg [ProgramName[arguments]] [options]  
```  
  
## <a name="commands"></a>Komutlar  
 Hata ayıklamada olduğunuzda **(mdbg>** isteminde belirtildiği gibi), bir sonraki bölümde açıklanan komutlardan birini yazın:  
  
 **komut** [*argümanlar*]  
  
 MDbg.exe komutları büyük/küçük harfe duyarlıdır.  
  
|Komut|Açıklama|  
|-------------|-----------------|  
|**ap**[**rocess**] [*sayı*]|Hataları ayıklanan başka bir işleme geçer veya kullanılabilir işlemleri yazdırır. Numaralar gerçek işlem kimlikleri (PID) değil, 0-dizinli bir listedir.|  
|**a**[**ttach**] [*pid*]|Bir işleme iliştirir veya kullanılabilir işlemleri yazdırır.|  
|**b**[**reak**] [*ClassName.Method* &#124; *FileName:LineNo ]*|Belirtilen yöntemde bir kesme noktası ayarlar. Modüller sırayla taranır.<br /><br /> -   **FileName'yi** *kırma:LineNo* kaynaktaki bir konumda bir kesme noktası ayarlar.<br />-   **break** *~sayı,* **x** komutuyla son zamanlarda görüntülenen bir sembol üzerinde bir kesme noktası ayarlar.<br />-   **break** *modülü kırmak! ClassName.Method+IlOffset,* tam nitelikli konumda bir kesme noktası ayarlar.|  
|**blok**[**ingObjects**]|Engelleyici iş parçacıkları olan izleme kilitlerini görüntüler.|  
|**ca**[**tch**] [*özel durumYazın*]|Hata ayıklayıcının, yalnızca işlenmeyen özel durumları değil, tüm özel durumları kesmesine neden olur.|  
|**cl**[**earException**]|Yürütmenin devam edebilmesi için, geçerli özel durumu işlenmiş olarak işaretler. Özel durumun nedeniyle ilgilenilmediyse, özel durum hızlı bir şekilde yeniden oluşturulabilir.|  
|**conf**[**ig**] [*opsiyon değeri*]|Tüm yapılandırılabilir seçenekleri görüntüler ve seçeneklerin isteğe bağlı değerler olmadan nasıl çağrılabileceğini gösterir. Seçenek belirtilirse, `value` geçerli seçenek olarak ayarlar. Aşağıdaki seçenekler şu anda kullanılabilir:<br /><br /> -   `extpath``load` komut kullanıldığında uzantıları aramak için yol ayarlar.<br />-   `extpath+`uzantıları yüklemek için bir yol ekler.|  
|**del**[**ete**]|Bir kesme noktasını siler.|  
|**de**[**tach**]|Hata ayıklaması yapılmış bir işlemden ayırır.|  
|**d**[**kendi**] [*çerçeveler*]|Etkin yığın çerçevesini aşağı taşır.|  
|**echo**|Bir iletiyi konsola yankılatır.|  
|**enableNotif**[**ication**] *typeName* 0&#124;1|Belirtilen tür için özel bildirimleri etkinleştirir (1) veya devre dışı bırakır (0).|  
|**ex**[**it**] [*exitcode*]|MDbg.exe kabuğundan çıkar ve isteğe bağlı olarak işlem çıkış kodunu belirtir.|  
|**fo**[**ulaşmak**] [*OtherCommand*]|Bir komutu tüm iş parçacıkları üzerinde uygular. *OtherCommand* tek bir iş parçacığı üzerinde çalışan geçerli bir komutdur; **foreach** *OtherCommand* tüm iş parçacıkları üzerinde aynı komutu gerçekleştirir.|  
|**f**[**unceval**]`-ad` [ *Num*] *functionName* [*args ...* ]|Değerlendirilecek işlevin *functionName*olduğu geçerli etkin iş parçacığı üzerinde bir işlev değerlendirmesi gerçekleştirir. İşlev adı, ad alanları da dahil olmak üzere tam olarak nitelenmiş olmalıdır.<br /><br /> Seçenek, `-ad` işlevi çözmek için kullanılacak uygulama etki alanını belirtir. `-ad` Seçenek belirtilmemişse, çözüm için uygulama etki alanı işlev değerlendirmesi için kullanılan iş parçacığının bulunduğu uygulama etki alanına varsayılan olarak kullanılır.<br /><br /> Değerlendirilmekte olan işlev statik değilse, geçirilen ilk parametre bir `this` işaretçi olmalıdır. Tüm uygulama etki alanlarında, işlev değerlendirmesi bağımsız değişkenleri için arama yapılır.<br /><br /> Bir uygulama etki alanından değer istemek için, değişkeni modül ve uygulama etki alanı adı ile önek; örneğin, `funceval -ad 0 System.Object.ToString hello.exe#0!MyClass.g_rootRef`. Bu komut, uygulama `System.Object.ToString` etki alanında `0`işlevi değerlendirir. `ToString` Yöntem bir örnek işlevi olduğundan, ilk parametre `this` bir işaretçi olmalıdır.|  
|**g**[**o**]|Programın bir kesme noktasıyla karşılaşıncaya, programdan çıkılıncaya veya bir olay (örneğin, işlenmemiş bir özel durum) programın durmasına neden oluncaya kadar devam etmesine neden olur.|  
|**h**[**elp**] [*komut*]<br /><br /> -veya-<br /><br /> **?** [*komut*]|Tüm komutların açıklamasını veya belirtilen bir komutun ayrıntılı açıklamasını görüntüler.|  
|**ig**[**nore**] [*olay*]|Hata ayıklayıcının yalnızca işlenmemiş özel durumlarda durmasına neden olur.|  
|**int**[**ercept**] *FrameNumber*|Hata ayıklayıcıyı belirtilen bir çerçeve numarasına geri döndürür.<br /><br /> Hata ayıklayıcı bir özel durumla karşılaşırsa, hata ayıklayıcıyı belirtilen kare numarasına geri döndürmek için bu komutu kullanın. **Ayarlanan** komutu kullanarak program durumunu değiştirebilir ve **go** komutunu kullanarak devam edebilirsiniz.|  
|**k**[**hasta**]|Etkin işlemi durdurur.|  
|**l**[**ist**] [*modüller* &#124; *appdomains* &#124; *meclisleri*]|Yüklü modülleri, uygulama etki alanlarını veya derlemeleri görüntüler.|  
|**lo**[**reklam**] *assemblyName*|Aşağıdaki şekilde bir uzantı yükler: Belirtilen montaj yüklenir ve daha sonra `LoadExtension` `Microsoft.Tools.Mdbg.Extension.Extension` statik yöntemi türden çalıştırmak için bir girişimyapılır.|  
|**log** [*eventType*]|Günlüğe kaydedilecek olayları ayarlayın veya görüntüleyin.|  
|**mo**[**de**] [*seçeneği aç/kapalı*]|Farklı hata ayıklayıcı seçeneklerini ayarlar. Hata `mode` ayıklama modlarının ve geçerli ayarlarının bir listesini almak için seçenekleri olmadan kullanın.|  
|**mon**[**itorInfo**] *monitorReference*|Nesne izleme kilidi bilgilerini görüntüler.|  
|**newo**[**bj**] *typeName* [*argümanlar...*]|*Tür adı türünde*yeni bir nesne oluşturur.|  
|**n**[**ext**]|Kodu çalıştırır ve sonraki satıra geçer (sonraki satır birçok işlev çağrısı içerse bile).|  
|**Opendump** *yoluToDumpFile*|Hata ayıklama için belirtilen döküm dosyasını açar.|  
|**o**[**ut**]|Geçerli işlevin sonuna taşır.|  
|**pa**[**th**] [*pathName*]|İkililerdeki konum kullanılabilir değilse, belirtilen yolda kaynak dosyalarını arar.|  
|**p**[**rint**] [`-d`*var*] &#124; ] ]|Kapsamdaki tüm değişkenleri yazdırır **(yazdırma),** belirtilen değişkeni **(yazdırma** *var)* yazdırır veya hata ayıklayıcı değişkenlerini **(yazdırma)**`-d`yazdırır.|  
|**printe**[**xception**] [*-r*]|Geçerli iş parçacığındaki son özel durumu yazdırır. Tüm `–r` özel durumlar zinciri hakkında bilgi almak `InnerException` için özel durum nesnesi üzerinde özellik geçiş yapmak için (özyinelemeli) seçeneğini kullanın.|  
|**pro**[**cessenum**]|Etkin işlemleri görüntüler.|  
|**q**[**uit**] [*exitcode*]|İsteğe bağlı olarak işlem çıkış kodunu belirterek, MDbg.exe kabuğundan çıkar.|  
|**re**[**süme**] [`*` &#124; [ ]`~`*iplikNumber*]|Geçerli iş parçacığı veya *threadNumber* parametresi tarafından belirtilen iş parçacığı devam eder.<br /><br /> *ThreadNumber* parametresi olarak `*` belirtilirse veya iş `~`parçacığı numarası ile başlarsa, komut *threadNumber*tarafından belirtilen hariç tüm iş parçacıkları için geçerlidir.<br /><br /> Askıya alınmamış bir iş parçacığını sürdürmenin etkisi yoktur.|  
|**r****un**[ un`-d``ebug`] [`o``ptimize`] `-enc`&#124; – ( ) &#124;] [[*path_to_exe*] [*args_to_exe*]]|Geçerli işlemi (varsa) durdurur ve yeni bir işlem başlatır. Yürütülebilir bağımsız değişken geçirilemezse, bu komut daha önce `run` komutla yürütülen programı çalıştırılır. Yürütülebilir bağımsız değişkeni sağlanırsa, belirtilen program isteğe bağlı olarak sağlanan bağımsız değişkenler kullanılarak çalıştırır.<br /><br /> Sınıf yükleme, modül yükleme ve iş parçacığı başlatma olayları yoksayılırsa (varsayılan olarak yoksayıldıkları gibi), program, ana iş parçacığının il yürütülebilir yönergesinde durur.<br /><br /> Aşağıdaki üç bayraktan birini kullanarak, hata ayıklayıcıyı kodu tam zamanında (JIT) derlemeye zorlayabilirsiniz:<br /><br /> -   `-d`*(* `ebug` *)* optimizasyonları devre dışı kılabilir. Bu, MDbg.exe için varsayılan değerdir.<br />-   `-o`*(* `ptimize` *)* kodu hata ayıklayıcının dışında olduğu gibi daha fazla çalıştırmaya zorlar, ancak hata ayıklama deneyimini de zorlaştırır. Bu, hata ayıklayıcının dışında kullanım için varsayılan değerdir.<br />-   `-enc`Edit ve Continue özelliğini etkinleştirir, ancak bir performans vuruşuna neden olur.|  
|**Set** *variable*Değişken=*değerini* ayarlama|Kapsam içi herhangi bir değişkenin değerini değiştirir.<br /><br /> Ayrıca, kendi hata ayıklayıcı değişkenlerinizi de oluşturabilir ve onlara kendi uygulamanızdan başvuru değerleri atayabilirsiniz. Bu değerler, özgün değer kapsam dışında olsa bile, özgün değerin tanıtıcıları gibi davranır. Tüm hata ayıklama değişkenleri `$` ile başlamalıdır (örneğin, `$var`). Aşağıdaki komutla onları hiçbir şey olacak şekilde ayarlayarak bu tanıtıcıları temizleyin:<br /><br /> `set $var=`|  
|**Setip** `-il`[ ] *sayısı*|Dosyadaki geçerli yönerge işaretçisini (IP) belirtilen konuma ayarlar. `-il` Seçeneği belirtirseniz, sayı yöntemde bir Microsoft ara dili (MSIL) mahsup temsil eder. Tersi durumda, sayı, bir kaynak satırı numarasını gösterir.|  
|**ş**[**ow**] [*satır ]*|Gösterilecek satırların sayısını belirtir.|  
|**s**[**tep**]|Yürütmeyi geçerli satırda sonraki işleve taşır veya geçilecek işlev yoksa sonraki satıra taşır.|  
|**su****spend**[ harcama\* ] [ &#124; [~]*threadNumber*]|Geçerli iş parçacığı veya *threadNumber* parametresi tarafından belirtilen iş parçacığı askıya.  *threadNumber* olarak `*`belirtilirse, komut tüm iş parçacıkları için geçerlidir. İş parçacığı numarası `~`ile başlarsa, komut *threadNumber*tarafından belirtilen hariç tüm iş parçacıkları için geçerlidir. Askıya alınan iş parçacıkları, işlem **git** veya **adım** komutu tarafından çalıştırıldığında çalışmaktan hariç tutulur. İşlemde askıda olmayan iş parçacıkları yoksa ve **git** komutunu verirsen, işlem devam etmez. Bu durumda, işleme girmek için CTRL-C tuşlarına basın.|  
|**sy**[**mbol**] *commandName* [*commandValue*]|Aşağıdaki komutlardan birini belirtir:<br /><br /> -   `symbol path`[`"value"`] - Geçerli sembol yolunu görüntüler veya ayarlar.<br />-   `symbol addpath``"value"` - Geçerli sembol yolunuza ekler.<br />-   `symbol reload`[`"module"`] - Belirtilen modülün tüm sembollerini veya sembollerini yeniden yükler.<br />-   `symbol list`[`module`] - Tüm modüller veya belirtilen modül için şu anda yüklenen sembolleri gösterir.|  
|**t**[**hread**] [*newThread*] [-*nick takma*`]`|Parametresiz thread komutu, geçerli işlemdeki yönetilen tüm iş parçacıklarını görüntüler. İş parçacıkları genellikle iş parçacığı numaralarıyla tanımlanır; ancak, iş parçacığının atanmış bir takma adı varsa, onun yerine takma ad görüntülenir. Bir iş `-nick` parçacığına takma ad atamak için parametreyi kullanabilirsiniz.<br /><br /> -   **threadName,** `-nick` *threadName* şu anda çalışan iş parçacığına bir takma ad atar.<br /><br /> Takma adlar sayı olamaz. Geçerli iş parçacığına bir takma ad atandıysa, eski takma ad yenisiyle değiştirilir. Yeni takma ad boş bir dize ("") ise, geçerli iş parçacığına ilişkin takma ad silinir ve iş parçacığına yeni takma ad atanmaz.|  
|**u**[**p**]|Etkin yığın çerçevesini yukarı taşır.|  
|**uwgc**[**handle**] [*var*] &#124; [*adres*]|Bir tanıtıcıyla izlenen değişkeni yazdırır. Tanıtıcı, ad veya adresle belirtilebilir.|  
|**Tesis**|Şu anda `when` etkin olan deyimleri görüntüler.<br /><br /> **when** tüm &#124; `num` `num` sildiğinde`num` [ [...]] `when` - Numaratarafından belirtilen `when` deyimi `all` veya belirtilirse tüm ifadeleri **siler.**<br /><br /> **ne** `stopReason` `specific_condition`zaman [`cmd` `cmd` ] **do** `cmd` [ [ ...] ] - *StopReason* parametresi aşağıdakilerden biri olabilir:<br /><br /> `StepComplete`, `ProcessExited`, `ThreadCreated`, `BreakpointHit`, `ModuleLoaded`, `ClassLoaded`, `AssemblyLoaded`, `AssemblyUnloaded`, `ControlCTrapped`, `ExceptionThrown`, `UnhandledExceptionThrown`, `AsyncStop`, `AttachComplete`, `UserBreak`, `EvalComplete`, `EvalException`, `RemapOpportunityReached`, `NativeStop`.<br /><br /> *specific_condition* aşağıdakilerden biri olabilir:<br /><br /> -   *sayı* - `ThreadCreated` `BreakpointHit`For ve , yalnızca aynı değere sahip bir iş parçacığı kimliği/kesme noktası numarası tarafından durdurulduğunda eylemi tetikler.<br />-`!`[ ]*adı* `AssemblyLoaded`- `AssemblyUnloaded` `ExceptionThrown`Için `ModuleLoaded` `UnhandledExceptionThrown`, `ClassLoaded`, , , , , ve , sadece adı *stopReason*adı eşleşen eylem tetikler .<br /><br /> *specific_condition* *stopReason*diğer değerler için boş olmalıdır.|  
|**w****here**[ burada`-v`]`-c` [ ] [ *derinlik*] [*threadID*]|Yığın çerçevelerle ilgili hata ayıklama bilgilerini görüntüler.<br /><br /> - `-v` Seçenek, görüntülenen her yığın çerçevesi hakkında ayrıntılı bilgi sağlar.<br />- Kaç çerçevenin `depth` görüntülendiğine ilişkin bir sayı belirtme. Tüm kareleri görüntülemek için **tüm** komutu kullanın. Varsayılan değer 100'dür.<br />- *ThreadID* parametresini belirtirseniz, yığınla ilişkili iş parçacığının hangisi olduğunu denetleyebilirsiniz. Varsayılan değer, yalnızca geçerli iş parçacığıdır. Tüm iş parçacığı almak için **tüm** komutu kullanın.|  
|**x** `-c`[*numSymbols*]`!`[*modül*[*desen*]]|Bir modül `pattern` için eşleşen işlevleri görüntüler.<br /><br /> *numSymbols* belirtilirse, çıktı belirtilen sayıyla sınırlıdır. Desen `!` için (normal bir ifade yi gösteren) belirtilmemişse, tüm işlevler görüntülenir. *pattern* *Modül* sağlanmazsa, yüklenen tüm modüller görüntülenir. Semboller*~#*( ) **kesme** komutunu kullanarak kesme noktalarını ayarlamak için kullanılabilir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Derleyicinizin hata ayıklama simgeleri üretmesine neden olan derleyiciye özel bayraklar kullanarak, hataları ayıklanacak uygulamayı derleyin. Bu bayraklar hakkında daha fazla bilgi için, derleyicinizin belgelerine bakın. En iyi duruma getirilen uygulamalarda hataları ayıklayabilirsiniz, fakat bazı hata ayıklama bilgileri eksik olur. Örneğin, birçok yerel değişken görünür olmaz ve kaynak satırları hatalı olur.  
  
 Başvurunuzu derledikten sonra, aşağıdaki örnekte gösterildiği gibi hata ayıklama oturumu başlatmak için komut istemine **mdbg** yazın.  
  
```console  
C:\Program Files\Microsoft Visual Studio 8\VC>mdbg  
MDbg (Managed debugger) v2.0.50727.42 (RTM.050727-4200) started.  
Copyright (C) Microsoft Corporation. All rights reserved.  
  
For information about commands type "help";  
to exit program type "quit".  
mdbg>  
```  
  
 İstem, `mdbg>` hata ayıklamada olduğunuzu gösterir.  
  
 Hata ayıklayıcıya girdikten sonra, önceki bölümde açıklanan komutları bağımsız değişkenleri kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [Komut İstemleri](developer-command-prompt-for-vs.md)
