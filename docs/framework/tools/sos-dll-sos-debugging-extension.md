---
title: SOS.dll (SOS Hata Ayıklama Uzantısı)
ms.date: 03/30/2017
helpviewer_keywords:
- debugging extensions
- SOS debugging extensions
- SOS.dll
ms.assetid: 9ac1b522-77ab-4cdc-852a-20fcdc9ae498
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7f5981a157377d633fb270ff079d2860ce880f6b
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46001096"
---
# <a name="sosdll-sos-debugging-extension"></a>SOS.dll (SOS Hata Ayıklama Uzantısı)
SOS hata ayıklama uzantısı (SOS.dll) iç ortak dil çalışma zamanı (CLR) ortamıyla ilgili bilgi sağlayarak Visual Studio ve Windows hata ayıklayıcısındaki (WinDbg.exe) yönetilen programlarda hata ayıklamanıza yardımcı olur. Bu araç, projenizde yönetilmeyen hata ayıklamanın etkin olmasını gerektirir. SOS.dll, .NET Framework ile birlikte otomatik olarak yüklenir. SOS.dll, Visual Studio'da kullanmak için yükleyin [Windows Sürücü Seti'nin (WDK)](https://msdn.microsoft.com/windows/hardware/hh852362).  
  
> [!NOTE]
>  Kullanıyorsanız [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], SOS.dll, Visual Studio içinde Windows hata ayıklayıcısı, ancak Visual Studio hata ayıklayıcının komut penceresinde desteklenir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
![command] [options]   
```  
  
## <a name="commands"></a>Komutlar  
  
|Komut|Açıklama|  
|-------------|-----------------|  
|**AnalyzeOOM** (**ao**)|Atık toplama yığın için bir ayırma isteğini ortaya çıkan son OOM bilgilerini görüntüler. (Sunucu çöpü toplamada, her bir çöp toplama yığınında varsa OOM görüntüler.)|  
|**BPMD** [**- nofuturemodule**] [\<*modül adı*> \<*yöntem adı*>] [**- md**   < `MethodDesc`>] **-liste** **-clear** \< *bekleyen kesme noktası numarası* >  **- clearall**|Belirtilen modül içinde belirtilen yöntemde bir kesme noktası oluşturur.<br /><br /> Belirtilen modül ve yöntem yüklenmediyse, bu komut, modülün yüklendiğine ve bir kesme noktası oluşturmadan önce tam zamanında (JIT) derlediğine ilişkin bir bildirim bekler.<br /><br /> Bekleyen kesme noktaları listesini kullanarak yönetebileceğiniz **-liste**, **-clear**, ve **- clearall** seçenekleri:<br /><br /> **-Liste** seçeneği tüm bekleyen kesme noktalarının bir listesini oluşturur. Bir bekleyen kesme noktasının sıfır olmayan bir modül kimliği varsa, o kesme noktası o belirli modüldeki bir işleve özeldir. Bekleyen kesme noktasının modül kimliği sıfırsa, o kesme noktası henüz yüklenmeyen modüller için geçerli olur.<br /><br /> Kullanım **-clear** veya **- clearall** bekleyen kesme noktalarını listeden kaldırmak için seçeneği.|  
|**CLRStack** [**-a**] [**-l**] [**-p**] [**- n**]|Yalnızca bir yönetilen kodların bir yığın izlemesini sağlar.<br /><br /> **-P** seçeneği yönetilen işleve bağımsız değişkenleri gösterir.<br /><br /> **-L** seçeneği bir çerçeve yerel değişkenlerle ilgili bilgileri gösterir. Yerel adlara ilişkin çıkış biçimi, bu nedenle SOS hata ayıklama uzantısı yerel adları alamadığından \< *yerel adres* >  **=** \< *değer*>.<br /><br /> **-A**(Tümü) seçeneği için bir kısayoldur **-l** ve **-p** birleştirilmiş.<br /><br /> **-N** seçeneği, kaynak dosya adları ve satır numaralarının görüntüsünü devre dışı bırakır. Hata ayıklayıcı için SYMOPT_LOAD_LINES seçeneği belirtildiyse, SOS yönetilen her çerçeve için simgelere bakar ve başarılı olursa, ilgili dosya adını ve satır numarasını görüntüler. **- N** (satır numarası yok) parametresi, bu davranışı devre dışı bırakmak için belirtilebilir.<br /><br /> SOS Hata Ayıklama Uzantısı, x64 ve IA-64 tabanlı platformlarda geçiş çerçevelerini görüntülemez.|  
|**COMState**|Her iş parçacığı için COM grubu modelini listeler ve `Context` varsa işaretçisi.|  
|**DumpArray** [**-başlangıç** \< *startIndex*>] [**-uzunluk** \<*uzunluğu*>] [**-Ayrıntılar**] [**- nofields**] \<*dizi nesnesi adresi*><br /><br /> veya<br /><br /> **DA** [**-başlangıç** \< *startIndex*>] [**-uzunluğu** \< *uzunluğu*>] [**-ayrıntı**] [**- nofields**] *dizi nesnesi adresi*>|Bir dizi nesnesinin öğelerini inceler.<br /><br /> **-Başlangıç** seçeneği, öğelerin görüntüleneceği başlangıç dizinini belirtir.<br /><br /> **-Uzunluğu** seçeneği kaç öğenin gösterileceğini belirtir.<br /><br /> **-Ayrıntılar** seçeneği kullanarak öğe ayrıntılarını görüntüler **DumpObj** ve **DumpVC** biçimleri.<br /><br /> **- Nofields** seçeneği, dizilerin görüntülenmesini önler. Bu seçenek yalnızca, **-ayrıntı** seçeneği belirtildi.|  
|**DumpAssembly** \< *derleme adresi*>|Bir derlemeyle ilgili bilgileri görüntüler.<br /><br /> **DumpAssembly** komutu, varsa birden çok modülü listeler.<br /><br /> Kullanarak bir derleme adresi alabilirsiniz **DumpDomain** komutu.|  
|**DumpClass** \< *EEClass adresi*>|İlgili bilgileri görüntüler `EEClass` yapısı türü ile ilişkili.<br /><br /> **DumpClass** komutu statik alan değerlerini görüntüler, fakat statik olmayan alan değerlerini görüntülemez.<br /><br /> Kullanım **Eeclass**, **DumpObj**, **Name2EE**, veya **name2ee** almak için komutu bir `EEClass` yapı adresi.|  
|**DumpDomain** [\<*etki alanı adresi*>]|Her numaralandırır <xref:System.Reflection.Assembly> diğer bir deyişle nesne belirtilen içinde yüklenen <xref:System.AppDomain> nesnesi adresi.  Hiçbir parametre olmadan çağrıldığında **DumpDomain** komut tüm listeler <xref:System.AppDomain> bir işlemde nesneleri.|  
|**DumpHeap** [**-stat**] [**-dizeleri**] [**-kısa**] [**-min** \< *boyutu*>] [**-max** \< *boyutu*>] [**- thinlock**] [**- startAtLowerBound**] [**- mt** \< *MethodTable adresi*>] [**-türü** \< *kısmi tür adı*>] [*Başlat* [*son*]]|Toplanan çöp yığınıyla ilgili bilgileri ve nesnelerle ilgili toplama istatistiklerini görüntüler.<br /><br /> **DumpHeap** komut, çöp toplayıcı yığınında aşırı parçalanma algılarsa bir uyarı görüntüler.<br /><br /> **-Stat** seçeneği, istatistiksel tür özetine çıkışı kısıtlar.<br /><br /> **-Dizeleri** seçeneği, bir istatistiksel dize değeri özetine çıkışı kısıtlar.<br /><br /> **-Kısa** seçeneği yalnızca her bir nesnenin adresine çıkışı sınırlandırır. Bu, otomasyon için komuttan başka bir hata ayıklayıcı komutuna kolayca çıktı yönlendirmenize olanak sağlar.<br /><br /> **-Min** seçeneği nesneleri yoksayar küçüktür `size` bayt cinsinden belirtilen parametresi.<br /><br /> **-Max** seçeneği büyük nesneleri yoksayar `size` bayt cinsinden belirtilen parametresi.<br /><br /> **- Thinlock** seçeneği thinlocks.  Daha fazla bilgi için **SyncBlk** komutu.<br /><br /> `-startAtLowerBound` Seçeneği yığın yürüyüşünü sağlanan bir adres aralığının alt sınırı başlayan zorlar. Planlama aşamasında, nesneler taşınmakta olduğundan, yığın genellikle yürünebilir değildir. Bu seçenek zorlar **DumpHeap** yürüyüşüne belirtilen alt sınırda başlamaya. Bu seçeneğin çalışması alt sınır olarak geçerli bir nesne adresi sağlamanız gerekir. Sonraki yöntem tablosunu el ile bulmak için, bozuk bir nesnenin adresindeki belleği görüntüleyebilirsiniz. Çöp toplama şu anda bir çağrıda ise `memcopy`, ayrıca boyutu bir parametre olarak sağlanan başlangıç adresine ekleyerek sonraki nesnenin adresini bulmak mümkün olabilir.<br /><br /> **- Mt** seçeneği belirtilen karşılık gelen nesneleri listeler `MethodTable` yapısı.<br /><br /> **-Türü** seçeneği yalnızca, tür adları belirtilen dizenin bir alt dize eşleşmesinin olan nesneleri listeler.<br /><br /> `start` Parametresi, listeleme yapmaya belirtilen adresten başlar.<br /><br /> `end` Parametresi belirtilen adreste listelemeyi durdurur.|  
|**DumpIL** \< *DynamicMethod yönetilen nesne*> &#124; \< *DynamicMethodDesc işaretçi*> &#124; \<  *MethodDesc işaretçi*>|Yönetilen bir yöntemle ilişkili Microsoft ara dilini (MSIL) görüntüler.<br /><br /> Dinamik MSIL'in bir derlemeden yüklenen MSIL'den farklı şekilde yayıldığını unutmayın. Dinamik MSIL, meta veri belirteçleri yerine, bir yönetilen nesne dizisindeki nesnelere başvurur.|  
|**DumpLog** [**- addr** \< *addressOfStressLog*>] [<*Filenam*`e`>]|Bir bellek içi yük günlüğünün içeriğini belirtilen dosyaya yazar. Bir ad belirtmezseniz, bu komut geçerli dizinde StressLog.txt adlı bir dosya oluşturur.<br /><br /> Bellek içi yük güvenliği, kilitler veya G/Ç kullanmadan yük hatalarını tanılamanıza yardımcı olur. Yük günlüğünü etkinleştirmek üzere HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft altında aşağıdaki kayıt defteri anahtarlarını ayarlamak\\. NETFramework:<br /><br /> (DWORD) StressLog = 1<br /><br /> (DWORD) LogFacility = 0xffffffff<br /><br /> (DWORD) StressLogSize = 65536<br /><br /> İsteğe bağlı `-addr` seçeneği varsayılan günlük başka bir yük günlüğü belirtmenize olanak sağlar.|  
|**DumpMD** \< *MethodDesc adresi*>|İlgili bilgileri görüntüler bir `MethodDesc` belirtilen adreste yapısı.<br /><br /> Kullanabileceğiniz **IP2MD** almak için komut `MethodDesc` yapı adresi yönetilen bir işlevden.|  
|**Eeclass** [**-MD**] \< *MethodTable adresi*>|Belirtilen bir adresteki bir yöntem tablosuyla ilgili bilgileri görüntüler. Belirtme **-MD** seçeneği nesneyle birlikte tanımlanan tüm yöntemlerin listesini görüntüler.<br /><br /> Her bir yönetilen nesne bir yöntem tablosu işaretçisi içerir.|  
|**DumpMethodSig** \< *sigaddr*><*moduleadd*`r`>|İlgili bilgileri görüntüler bir `MethodSig` belirtilen adreste yapısı.|  
|**DumpModule** [**- mt**] \< *modülü adresi*>|Belirtilen adresteki bir modülle ilgili bilgileri görüntüler. **- Mt** seçeneği bir modülde tanımlanan türleri ve modül tarafından başvurulan türleri görüntüler<br /><br /> Kullanabileceğiniz **DumpDomain** veya **DumpAssembly** bir modülün adresini almak için komutu.|  
|**DumpObj** [**- nofields**] \< *nesnesi adresi*><br /><br /> veya<br /><br /> **YAPMAK** \<*nesne adresi*>|Belirtilen adresteki bir nesneyle ilgili bilgileri görüntüler. **DumpObj** komutu alanları görüntüler `EEClass` yapı bilgilerini, yöntem tablosunu ve nesnenin boyutu.<br /><br /> Kullanabileceğiniz **DumpStackObjects** bir nesnenin adresini almak için komutu.<br /><br /> Çalıştırabileceğiniz Not **DumpObj** türünde alanlar üzerinde komutunu `CLASS` onlarda nesne olduğu için.<br /><br /> `-` **Nofields** seçeneği alanları nesnenin görüntülenmesini önler, dize gibi nesneler için kullanışlıdır.|  
|**DumpRuntimeTypes**|Çöp toplayıcı yığınındaki çalışma zamanı türü nesneleri görüntüler ve ilişkili tür adlarını ve yöntem tablolarını listeler.|  
|**DumpStack** [**- EE**] [**- n**] [`top` *yığın* [`bottom` *Yığ*`k`]]|Bir yığın izleme görüntüler.<br /><br /> **- EE** seçeneğini neden **DumpStack** komutunun yalnızca yönetilen işlevleri. Kullanım `top` ve `bottom` x86 üzerinde görüntülenen yığın karelerini sınırlamak için parametreleri platformlar.<br /><br /> **-N** seçeneği, kaynak dosya adları ve satır numaralarının görüntüsünü devre dışı bırakır. Hata ayıklayıcı için SYMOPT_LOAD_LINES seçeneği belirtildiyse, SOS yönetilen her çerçeve için simgelere bakar ve başarılı olursa, ilgili dosya adını ve satır numarasını görüntüler. **- N** (satır numarası yok) parametresi, bu davranışı devre dışı bırakmak için belirtilebilir.<br /><br /> X86 ve x64 platformlarında **DumpStack** komutu bir ayrıntılı yığın izleme oluşturur.<br /><br /> IA-64 tabanlı platformlarda **DumpStack** komutunu taklit eder, hata ayıklayıcı'nın **K** komutu. `top` Ve `bottom` parametreleri IA-64 tabanlı platformlarda yoksayılır.|  
|**DumpSig** \< *sigaddr*> \<*moduleaddr*>|İlgili bilgileri görüntüler bir `Sig` belirtilen adreste yapısı.|  
|**DumpSigElem** \< *sigaddr*> \<*moduleaddr*>|Bir imza nesnesinin tek bir öğesini görüntüler. Çoğu durumda, kullanmanız gereken **DumpSig** bireysel imza nesnelerine aramak için. Ancak, bir imza bir şekilde bozulduysa, kullanabileceğiniz **DumpSigElem** geçerli bölümlerini okumak için.|  
|**DumpStackObjects** [**-doğrulayın**] [`top` *yığın* [`bottom` *yığın*]]<br /><br /> veya<br /><br /> **DSO** [**-doğrulayın**] [`top` *yığın* [`bottom` *yığın*]]|Geçerli yığının sınırları içinde bulunan tüm yönetilen nesneleri görüntüler.<br /><br /> **-Doğrulayın** seçeneği statik olmayan her doğrulama `CLASS` , bir nesne alanının alan.<br /><br /> Kullanım **k** gibi yığın izleme komutlarıyla birlikte komut **K** komut ve **CLRStack** yerel değişkenlerin değerleri belirlemek için komut ve Parametreler.|  
|**DumpVC** \< *MethodTable adresi*> \<*adresi*>|Belirtilen adresteki bir değer sınıfının alanlarıyla ilgili bilgileri görüntüler.<br /><br /> **MethodTable** parametresi verir **DumpVC** alanları doğru olarak yorumlamasına komutu. Değer sınıfları, ilk alanları olarak bir yöntem tablosuna sahip değildir.|  
|**EEHeap** [**-gc**] [**-loader**]|İç CLR veri yapıları tarafından tüketilen işlem belleğiyle ilgili bilgileri görüntüler.<br /><br /> **-Gc** ve **-loader** seçenekleri, bu komutun çöp Toplayıcıya veya yükleyici veri yapılarına çıkışını sınırlandırır.<br /><br /> Çöp toplayıcıya ilişkin bilgiler, yönetilen yığındaki her bir segmentin aralıklarını listeler.  İşaretçi tarafından verilen bir segment aralığı içinde kalırsa **-gc**, işaretçi bir nesne işaretçisidir.|  
|**EEStack** [**-kısa**] [**- EE**]|Çalıştırmaları **DumpStack** komutunu işlemdeki tüm iş parçacıkları.<br /><br /> **- EE** seçeneği doğrudan geçirilen **DumpStack** komutu. **-Kısa** parametresi çıkışı aşağıdaki türden iş parçacıklarıyla sınırlandırır:<br /><br /> Kilit almış olan iş parçacıkları.<br /><br /> Çöp toplamaya olanak tanımak için durdurulmuş iş parçacıkları.<br /><br /> Yönetilen kodda bulunan iş parçacıkları.|  
|**EEVersion**|CLR sürümünü görüntüler.|  
|**EHInfo** [\<*MethodDesc adresi*>] [\<*kod adresi*>]|Belirtilen bir yöntemdeki özel durum işleme bloklarını görüntüler.  Bu komut, kod adreslerini ve ofsetleri yan tümce bloğu için gösterir ( `try` bloğu) ve işleyici bloğu ( `catch` blok).|  
|**SSS**|Sık sorulan soruları görüntüler.|  
|**FinalizeQueue** [**-ayrıntı**] &#124; [**- allReady**] [**-kısa**]|Sonlandırma için kaydolan tüm nesneleri görüntüler.<br /><br /> **-Ayrıntı** seçeneği görüntüler hakkında ek bilgi `SyncBlocks` temizlenmesi gereken ve tüm `RuntimeCallableWrappers` (RCW) syncblocks. Bu veri yapılarının her ikisi de, çalıştığı zaman sonlandırıcı tarafından ön belleğe kaydedilir.<br /><br /> `-allReady` Seçeneği olup, bu nedenle çöp toplama zaten işaretlenmiş veya sonraki çöp toplamadan işaretlenecek bakılmaksızın, sonlandırma için hazır olan tüm nesneleri görüntüler. "Sonlandırma için hazır" listesinde olan nesneler, artık köklü olmayan sonlandırılabilir nesnelerdir. Sonlandırılabilir kuyruklarda bulunan tüm nesnelerin hala köklü olduğunu doğruladığından, bu seçenek çok pahalı olabilir.<br /><br /> `-short` Seçeneği her nesnenin adresine çıkışı sınırlandırır. İle birlikte kullanıldığında **- allReady**, artık köklü olmayan bir Sonlandırıcısı olan tüm nesneleri numaralandırır. Bağımsız olarak kullanılırsa, sonlandırılabilir ve "sonlandırmaya hazır" kuyruklardaki tüm nesneleri listeler.|  
|**FindAppDomain** \< *nesnesi adresi*>|Belirtilen adresteki bir nesnenin uygulama etki alanını belirler.|  
|**FindRoots** **-gen** \< *N*> &#124; **-gen any** &#124; \< *nesnesi adresi*>|Belirtilen oluşturmanın sonraki toplamasında, hata ayıklayıcının hatası ayıklanan öğeyi yarıda kesmesine neden olur. Kesme oluşur oluşmaz, etki sıfırlanır. Sonraki toplamayı kesmek için, komutu tekrar vermeniz gerekir. *\<Nesnesi adresi >* bu komutun formu tarafından neden olunan sonra kullanılır **-gen** veya **-gen any** oluştu. O anda hata ayıklanan için doğru durumda olduğundan. **FindRoots** geçerli nesneler için köklerin tanımlamak için oluşturmalardan.|  
|**GCHandles** [**- perdomain**]|İşlemdeki çöp toplayıcı tanıtıcılarıyla ilgili istatistikleri görüntüler.<br /><br /> **- Perdomain** seçeneği, istatistikleri uygulama etki alanına göre düzenler.<br /><br /> Kullanım **GCHandles** çöp toplayıcı tanıtıcı sızıntılarının neden olduğu bellek sızıntılarını bulmak için komutu. Örneğin, kesin olarak belirlenmiş bir çöp toplayıcı tanıtıcısı hala onu işaret ettiği için kod büyük bir diziyi tuttuğunda, bir bellek sızıntısı olur ve tanıtıcı onu serbest bırakmadan atılır.|  
|**GCHandleLeaks**|Kesin olarak belirlenmiş ve iliştirilmiş çöp toplayıcı tanıtıcılarına yapılan başvurular için bellekte arama yapar ve sonuçları görüntüler. Bir tanıtıcı bulunursa **GCHandleLeaks** komutu başvurunun adresini görüntüler. Bellekte bir tanıtıcı bulunmazsa, bu komut bir bildirim görüntüler.|  
|**Gcınfo** \< *MethodDesc adresi*>\<*kod adresi*>|Kayıt defterlerinin ve yığın konumlarının yönetilen nesneleri ne zaman içerdiğini gösteren verileri görüntüler. Bir çöp toplama olursa, onları yeni nesne işaretçisi değerleriyle güncelleştirebilmesi için, toplayıcı nesnelere yapılan başvuruların konumlarını bilmelidir.|  
|**GCRoot** [**- nostacks**] \< *nesnesi adresi*>|Belirtilen adresteki bir nesneye yapılan başvurularla (veya köklerle) ilgili bilgi görüntüler.<br /><br /> **GCRoot** komut inceler yönetilen yığını ve tanıtıcı tablosunu diğer tanıtıcılar için nesneleri ve yığındaki tanıtıcılar. Sonra, her bir yığında nesne işaretçileri aranır ve sonlandırıcı kuyruğunda da arama yapılır.<br /><br /> Bu komut, bir yığın kökünün geçerli veya atılmış olduğunu belirlemez. Kullanma **CLRStack** ve **U** yerel veya bağımsız değişken değeri yığın kökünün hala kullanılıp kullanılmadığını belirlemek için ait olduğu çerçeveyi ayrıştırmak için komutları.<br /><br /> **- Nostacks** seçeneği, aramayı çöp toplayıcı tanıtıcılarıyla ve aranabilir nesnelerle kısıtlar kısıtlar.|  
|**GCWhere***\<nesnesi adresi >*|Geçirilen bağımsız değişkenin çöp toplama yığınındaki konumu ve büyüklüğü görüntüler. Bağımsız değişken yönetilen yığında yer aldığında, fakat geçerli bir nesne adresi olmadığında, büyüklük 0 (sıfır) olarak görüntülenir.|  
|**Yardım** [\<*komut*>] [`faq`]|Parametre belirtilmediğinde kullanılabilir olan tüm komutları görüntüler veya belirli komutla ilgili ayrıntılı yardım bilgilerini görüntüler.<br /><br /> `faq` Parametresi sık sorulan soruların yanıtlarını görüntüler.|  
|**HeapStat** [**- inclUnrooted** &#124; **-IU**]|Her bir yığın için oluşturma büyüklüğünü ve her bir yığındaki her bir oluşturmada bulunan toplam boş alanı görüntüler. Varsa**inclUnrooted** seçeneği belirtilmemişse, rapor artık kökü olmayan çöp toplama yığınındaki yönetilen nesnelerle ilgili bilgiler içerir.|  
|**Histınit**|Ailesi tarafından kullanılan tüm kaynakları serbest bırakır `Hist` komutları.<br /><br /> Genellikle, açıkça çağırmanız gerekmez `HistClear`, çünkü her `HistInit` önceki kaynakları temizlediğinden.|  
|**Histclear**|Hatası ayıklanana kaydedilen yük günlüğünden SOS yapılarını başlatır.|  
|**HistObj** *< obj_address >*|Tüm yük günlüğü yeniden yerleştirme kayıtlarını inceler ve bir bağımsız değişken olarak geçirilen adrese yönlendirebilecek çöp toplama yeniden konumlandırmaları zincirini görüntüler.|  
|**HistObjFind***< obj_address >* |Belirtilen adresteki bir nesneye başvuran tüm günlük girişlerini görüntüler.|  
|**HistRoot**  *\<kök >*|Belirtilen kökün tanıtımlarıyla ve yeniden konumlandırılmalarıyla ilişkili bilgileri görüntüler.<br /><br /> Kök değeri, bir nesnenin çöp toplamalar içindeki hareketini izlemek için kullanılabilir.|  
|**IP2MD** \< *kod adresi*>|Görüntüler `MethodDesc` JIT derlemeli kod içinde belirtilen adreste yapısı.|  
|`ListNearObj` (`lno`) *< obj_address >*|Belirtilen adresten önceki ve sonraki nesneleri görüntüler. Komut, yönetilen bir nesnenin (geçerli bir yöntem tablosuna dayalı olarak) ve bağımsız değişken adresini izleyen nesnenin geçerli bir başlangıcı gibi görünen çöp toplama yığınında adresi arar.|  
|**MinidumpMode** [**0**] [**1**]|Bir mini döküm kullanırken, güvenli olmayan komutların çalışmasını önler.<br /><br /> Geçirmek **0** bu özelliği devre dışı bırakmak veya **1** bu özelliği etkinleştirmek için. Varsayılan olarak, **MinidumpMode** değeri ayarı **0**.<br /><br /> Oluşturulan Mini dökümler **.dump /m** komutu veya **.dump** komut CLR özel sınırlı veriler içerir ve SOS komutlarının yalnızca bir kısmı düzgün çalıştırmanıza olanak tanır. Gerekli bellek alanları eşleşmediğinden veya kısmen eşleştiğinden, bazı komutlar beklenmeyen hatalarla başarısız olabilir. Bu seçenek, mini dökümlere karşı güvenli olmayan komutları çalıştırmaktan sizi korur.|  
|**Name2EE** \< *modül adı*> \<*tür veya yöntem adı*><br /><br /> veya<br /><br /> **Name2EE** \< *modül adı*>**!** \< *tür veya yöntem adı*>|Görüntüler `MethodTable` yapısı ve `EEClass` belirtilen tür veya yöntemin belirtilen modüldeki yapısı.<br /><br /> Belirtilen modülün işlemde yüklenmesi gerekir.<br /><br /> Uygun tür adını almak için kullanarak modüle gözatın [Ildasm.exe (IL ayrıştırıcı)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md). De geçirebilirsiniz `*` modül olarak tüm arama için ad yüklü yönetilen modülleri. *Modül adı* parametresi ayrıca olabilir bir modül için hata ayıklayıcı'nın adı gibi `mscorlib` veya `image00400000`.<br /><br /> Bu komut Windows hata ayıklayıcı sözdizimini destekler <`module`>`!`<`type`>. Tür, tam olarak nitelenmiş olmalıdır.|  
|**ObjSize** [\<*nesnesi adresi*>] &#124; [**-toplama**] [**-stat**]|Belirtilen nesnenin boyutunu görüntüler. Herhangi bir parametre belirtmezseniz, **ObjSize** komutu yönetilen iş parçacıklarında bulunan tüm nesnelerin boyutunu görüntüler, işlemdeki tüm çöp toplayıcı tanıtıcılarını görüntüler ve bu tanıtıcıların işaret ettiği tüm nesnelerin boyutunu toplar. **ObjSize** komut üst ek olarak tüm alt nesnelerin büyüklüğünü içerir.<br /><br /> **-Toplama** seçeneği ile birlikte kullanılabilir **-stat** bağımsız değişkeni, hala köklü olan türlerin ayrıntılı bir görünüm elde edin. Kullanarak **! dumpheap-stat** ve **! objsize-toplama - stat**, hangi nesnelerin artık köklü olmayan ve çeşitli bellek sorunlarını tanılamak belirleyebilirsiniz.|  
|**PrintException** [**-iç içe geçmiş**] [**-satırları**] [\<*özel durum nesnesi adresi*>]<br /><br /> veya<br /><br /> **PE** [**-iç içe geçmiş**] [\<*özel durum nesnesi adresi*>]|Görüntüler ve türetilen herhangi bir nesnenin alanlarını biçimleri <xref:System.Exception> belirtilen adreste sınıfı. Bir Adres belirtmezseniz **PrintException** komutu, geçerli iş parçacığında oluşturulan en son özel durumu görüntüler.<br /><br /> **-İç içe geçmiş** seçeneği iç içe geçmiş özel durum nesneleri hakkındaki ayrıntıları görüntüler.<br /><br /> **-Satırları** seçeneği varsa kaynak bilgilerini görüntüler.<br /><br /> Bu komut biçimlendirmek ve görüntülemek için kullanabileceğiniz `_stackTrace` bir ikili dizi olan alan.|  
|**ProcInfo** [**- env**] [**-zaman**] [**-bellek**]|İşlem, çekirdek CPU süresi ve bellek kullanımı istatistikleri için ortam değişkenlerini görüntüler.|  
|**RCWCleanupList** \< *RCWCleanupList adresi*>|Belirtilen adreste temizlenmeyi bekleyen çalışma zamanı çağrılabilir sarmalayıcılarının listesini görüntüler.|  
|**SaveModule** \< *temel adres*> \<*dosya adı*>|Belirtilen adreste belleğe yüklenen bir görüntüyü belirtilen dosyaya yazar.|  
|**SOSFlush**|Bir iç SOS önbelleğini temizler.|  
|**StopOnException** [**-türetilmiş**] [**-oluşturma** &#124; **-create2**] \< *özel durum* >  \< *Sözde kayıt numarası*>|Belirtilen özel durum oluştuğunda hata ayıklayıcının durmasına, fakat diğer özel durumlar oluştuğunda çalışmaya devam etmesine neden olur.<br /><br /> **-Türetilmiş** seçeneği belirtilen özel durum ve belirtilen özel durumdan türetilen her bir özel durumu yakalar.|  
|**SyncBlk** [**-tüm** &#124; \< *syncblk numarası*>]|Belirtilen görüntüler `SyncBlock` yapısını veya tüm `SyncBlock` yapıları.  Herhangi bir bağımsız değişken geçirmezseniz **SyncBlk** komutunu görüntüler `SyncBlock` bir iş parçacığının sahip olduğu nesnelere karşılık gelen yapısı.<br /><br /> A `SyncBlock` yapısı her nesne için oluşturulması gerekmeyen fazladan bilgiler için bir kapsayıcıdır. COM birlikte çalışabilirlik verilerini, karma kodları ve güvenli iş parçacığı işlemlerine ilişkin kilitleme bilgilerini tutabilir.|  
|**İş parçacığı havuzu**|Kuyruktaki iş isteklerinin sayısı, derleme bağlantı noktası iş parçacıklarının sayısı ve zamanlayıcıların sayısı dahil, yönetilen iş parçacığı havuzuyla ilgili bilgileri görüntüler.|  
|**Name2ee** \< *modül adı*> \<*belirteci*>|Belirtilen meta veri içinde belirtilen modüldeki belirteci kapatır bir `MethodTable` yapısı veya `MethodDesc` yapısı.<br /><br /> Geçirebilirsiniz `*` ne o belirteç tüm yüklü yönetilen modülde eşlendiği bulmak modül adı parametresi için. Bir modül için hata ayıklayıcı'nın adı gibi geçirebilirsiniz `mscorlib` veya `image00400000`.|  
|**İş parçacığı** [**-canlı**] [**-özel**]|İşlemdeki tüm yönetilen iş parçacıklarını görüntüler.<br /><br /> **İş parçacıkları** komut hata ayıklayıcı hızlı yazma Kimliğini, CLR iş parçacığı Kimliğini ve işletim sistemi iş parçacığı kimliğini görüntüler  Ayrıca, **iş parçacıkları** komut bir iş parçacığının yürütülmekte uygulama etki alanını gösteren bir etki alanı sütununu, COM grubu modunu görüntüleyen bir APT sütununu ve son görüntüleyen bir özel durum sütununu görüntüler özel durum iş parçacığında oluşturuldu.<br /><br /> **-Canlı** seçeneği bir canlı iş parçacığıyla ilişkili iş parçacıklarını görüntüler.<br /><br /> **-Özel** seçeneği CLR tarafından oluşturulan tüm özel iş parçacıklarını görüntüler. Özel iş parçacıkları, çöp toplama iş parçacıklarını (eşzamanlı ve sunucu çöp toplamada), hata ayıklayıcı yardımcı iş, sonlandırıcı iş parçacıklarını dahil <xref:System.AppDomain> iş parçacıkları ve iş parçacığı havuzu Zamanlayıcı iş parçacıklarını kaldırın.|  
|**ThreadState \<**  *durum değeri alanı* **>**|Bir iş parçacığının durumunu görüntüler. `value` Parametredir değerini `State` alanındaki **iş parçacıkları** rapor çıkışında.<br /><br /> Örnek:<br /><br /> `0:003> !Threads     ThreadCount:      2     UnstartedThread:  0     BackgroundThread: 1     PendingThread:    0     DeadThread:       0     Hosted Runtime:   no                                           PreEmptive   GC Alloc           Lock            ID OSID ThreadOBJ    State     GC       Context       Domain   Count APT Exception        0    1  250 0019b068      a020 Disabled 02349668:02349fe8 0015def0     0 MTA        2    2  944 001a6020      b220 Enabled  00000000:00000000 0015def0     0 MTA (Finalizer)     0:003> !ThreadState b220         Legal to Join         Background         CLR Owns         CoInitialized         In Multi Threaded Apartment`|  
|**TraverseHeap** [**- xml**] \< *dosya adı*>|Yığın bilgilerini, CLR profil oluşturucusunun anlayacağı bir biçimde belirtilen dosyaya yazar. **- Xml** seçeneğini neden **TraverseHeap** dosyayı XML olarak biçimlendirmek için komutu.<br /><br /> CLR Profiler'nden indirebileceğiniz [Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkID=67325).|  
|**U** [**- gcinfo**] [**- ehinfo**] [**- n**] \< *MethodDesc adresi*> &#124; \< *Kod adresi*>|Görüntüler bir yönetilen yöntemin ek açıklamalı bir ayrıştırmasını ya da belirtilen bir `MethodDesc` yöntemi veya yöntem gövdesi içindeki bir kod adresiyle yapısı işaretçisi. **U** komut, meta veri belirteçlerini adlara dönüştüren ek açıklamalar ile baştan sona tüm yöntemi görüntüler.<br /><br /> **- Gcinfo** seçeneğini neden **U** görüntülemek için komut `GCInfo` yapısı için yöntemi.<br /><br /> **- Ehinfo** seçeneği yöntemi özel durum bilgilerini görüntüler. Bu bilgileri de edinebilirsiniz **EHInfo** komutu.<br /><br /> **-N** seçeneği, kaynak dosya adları ve satır numaralarının görüntüsünü devre dışı bırakır. Hata ayıklayıcı için SYMOPT_LOAD_LINES seçeneği belirtildiyse, SOS yönetilen her çerçeve için simgelere bakar ve başarılı olursa, ilgili dosya adını ve satır numarasını görüntüler. Belirtebileceğiniz **- n** bu davranışı devre dışı bırakma seçeneği.|  
|**VerifyHeap**|Bozulma işaretleri için çöp toplayıcı yığınını kontrol eder ve bulunan hataları görüntüler.<br /><br /> Yığın bozulmalarına, hatalı oluşturulan platform çağrıları neden olabilir.|  
|**VerifyObj** \< *nesnesi adresi*>|Bir bağımsız değişken olarak geçirilen nesnede bozulma işaretleri olup olmadığını kontrol eder.|  
|**VMMap**|Sanal adres alanını bir uçtan diğerine dolaşır ve her bir bölgeye uygulanan koruma türünü görüntüler.|  
|**VMStat**|Sanal adres alanının bir özet görünümü, o belleğe (serbest, ayrılmış, adanmış, özel, eşlenmiş, görüntü) uygulanan her bir koruma türüne göre düzenlenmiş olarak sağlar. TOPLAM sütunu, ORTALAMA sütununun sonucunu BLK SAYIMI sütunuyla çarpılmış olarak görüntüler.|  
  
## <a name="remarks"></a>Açıklamalar  
 SOS hata ayıklama uzantısı CLR içinde çalışan kodu bilgilerini görüntülemenize olanak tanır. Örneğin, yönetilen yığınla ilgili bilgileri görüntülemek, yığın bozulmalarını aramak, çalışma zamanı tarafından kullanılan iç veri türlerini görüntülemek ve çalışma zamanı içinde çalışan tüm yönetilen kodla ilgili bilgileri görüntülemek için SOS Hata Ayıklama Uzantısı'nı kullanabilirsiniz.  
  
 SOS hata ayıklama uzantısı Visual Studio'da kullanmak için yükleyin [Windows Sürücü Seti'nin (WDK)](https://msdn.microsoft.com/windows/hardware/hh852362). Visual Studio tümleşik hata ayıklama ortamında hakkında daha fazla bilgi için bkz. [hata ayıklama ortamları](https://msdn.microsoft.com/library/windows/hardware/hh406268.aspx) Windows geliştirme Merkezi'nde.  
  
 SOS hata ayıklama uzantısı edinebileceğiniz WinDbg.exe ayıklayıcısına yükleyerek kullanabilirsiniz [WDK ve geliştirici araçları Web sitesi](https://go.microsoft.com/fwlink/?LinkId=103787)ve WinDbg.exe içindeki komutları.  
  
 SOS Hata Ayıklama Uzantısı'nı WinDbg.exe hata ayıklayıcısına yüklemek için, aşağıdaki komutu araçta çalıştırın:  
  
```  
.loadby sos clr  
```  
  
 WinDbg.exe ve Visual Studio, kullanımda olan Mscorwks.dll'ye karşılık gelen SOS.dll'nin bir sürümünü kullanır. .NET Framework'ün 1.1 ve 2.0 sürümlerinde, SOS.dll, Mscorwks.dll ile aynı dizine yüklenir. Varsayılan olarak, Mscorwks.dll'nin geçerli sürümüyle eşleşen SOS.dll sürümünü kullanmanız gerekir.  
  
 Başka bir bilgisayarda oluşturulan bir döküm dosyasını kullanmak için, yüklemeyle birlikte gelen Mscorwks.dll dosyasının simge yolunuzda olduğundan emin olun ve ilgili SOS.dll sürümünü yükleyin.  
  
 SOS.dll'nin özel bir sürümünü yüklemek için, aşağıdaki komutu Windows Hata Ayıklayıcı'ya yazın:  
  
```  
.load <full path to sos.dll>  
```  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki komut, adresindeki bir dizinin içeriğini görüntüler `00ad28d0`.  Görüntü ikinci öğeden başlar ve beş öğe boyunca devam eder.  
  
```  
!dumparray -start 2 -length 5 -detail 00ad28d0   
```  
  
 Aşağıdaki komut, adresindeki bir derlemenin içeriğini görüntüler `1ca248`.  
  
```  
!dumpassembly 1ca248  
```  
  
 Aşağıdaki komut, çöp toplayıcı yığınıyla ilgili bilgileri görüntüler.  
  
```  
!dumpheap  
```  
  
 Aşağıdaki komut, bellek içi yük günlüğünün içeriğini, geçerli dizindeki StressLog.txt adlı bir dosyaya (varsayılan) yazar.  
  
```  
!DumpLog  
```  
  
 Aşağıdaki komut görüntüler `MethodDesc` yapısı adresten `902f40`.  
  
```  
!dumpmd 902f40  
```  
  
 Aşağıdaki komut, adresindeki bir modülle ilgili bilgileri görüntüler `1caa50`.  
  
```  
!dumpmodule 1caa50  
```  
  
 Aşağıdaki komut, adresindeki bir nesneyle ilgili bilgileri görüntüler `a79d40`.  
  
```  
!DumpObj a79d40  
```  
  
 Aşağıdaki komut bir değer sınıfının alanlarını görüntüler `00a79d9c` adresindeki yöntem tablosunu kullanarak `0090320c`.  
  
```  
!DumpVC 0090320c 00a79d9c  
```  
  
 Aşağıdaki komut, çöp toplayıcı tarafından kullanılan işlem belleğini görüntüler.  
  
```  
!eeheap -gc  
```  
  
 Aşağıdaki komut, sonlandırma için zamanlanan tüm nesneleri görüntüler.  
  
```  
!finalizequeue  
```  
  
 Aşağıdaki komutu adresteki bir nesneye uygulama etki alanını belirler `00a79d98`.  
  
```  
!findappdomain 00a79d98  
```  
  
 Aşağıdaki komut, geçerli işlemdeki tüm çöp toplayıcı tanıtıcılarını görüntüler.  
  
```  
!gcinfo 5b68dbb8   
```  
  
 Aşağıdaki komut görüntüler `MethodTable` ve `EEClass` için yapıları `Main` sınıfında yöntemi `MainClass` modülünde `unittest.exe`.  
  
```  
!name2ee unittest.exe MainClass.Main  
```  
  
 Aşağıdaki komut, adresindeki meta veri belirteciyle ilgili bilgileri görüntüler `02000003` modülünde `unittest.exe`.  
  
```  
!token2ee unittest.exe 02000003  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Araçlar](../../../docs/framework/tools/index.md)  
 [Komut İstemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
