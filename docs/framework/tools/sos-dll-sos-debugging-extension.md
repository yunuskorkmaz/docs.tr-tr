---
title: "SOS.dll (SOS Hata Ayıklama Uzantısı)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging extensions
- SOS debugging extensions
- SOS.dll
ms.assetid: 9ac1b522-77ab-4cdc-852a-20fcdc9ae498
caps.latest.revision: "55"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e000d0efbd999d228e10a5df8e6368cbf22c5088
ms.sourcegitcommit: bf8a3ba647252010bdce86dd914ac6c61b5ba89d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/06/2018
---
# <a name="sosdll-sos-debugging-extension"></a>SOS.dll (SOS Hata Ayıklama Uzantısı)
SOS hata ayıklama uzantısı (SOS.dll), Visual Studio ve Windows hata ayıklayıcısı (WinDbg.exe) yönetilen programları iç ortak dil çalışma zamanı (CLR) ortamıyla ilgili bilgileri sağlayarak hata ayıklama yardımcı olur. Bu araç, projenizde yönetilmeyen hata ayıklamanın etkin olmasını gerektirir. SOS.dll, .NET Framework ile birlikte otomatik olarak yüklenir. Visual Studio'da SOS.dll kullanmak için yükleme [Windows Sürücü Seti (WDK)](http://msdn.microsoft.com/windows/hardware/hh852362).  
  
> [!NOTE]
>  Kullanıyorsanız [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], Visual Studio içinde Windows ayıklayıcısında, ancak Visual Studio hata ayıklayıcı komut penceresi SOS.dll desteklenir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
![command] [options]   
```  
  
## <a name="commands"></a>Komutlar  
  
|Komut|Açıklama|  
|-------------|-----------------|  
|**AnalyzeOOM** (**ao**)|Atık toplama yığın için bir ayırma isteğini ortaya çıkan son OOM bilgilerini görüntüler. (Sunucu çöpü toplamada, her bir çöp toplama yığınında varsa OOM görüntüler.)|  
|**BPMD** [**- nofuturemodule**] [\<*modül adı*> \<*yöntem adı*>] [**- MD** <`MethodDesc`>] **-liste** **-temizleyin** \< *kesme numarası bekleyen* >  **- clearall**|Belirtilen modül içinde belirtilen yöntemde bir kesme noktası oluşturur.<br /><br /> Belirtilen modül ve yöntem yüklenmediyse, bu komut, modülün yüklendiğine ve bir kesme noktası oluşturmadan önce tam zamanında (JIT) derlediğine ilişkin bir bildirim bekler.<br /><br /> Kesme noktaları bekleyen listesini kullanarak yönetebileceğiniz **-liste**, **-temizleyin**, ve **- clearall** seçenekleri:<br /><br /> **-Liste** seçeneği tüm bekleyen kesme noktaları listesini oluşturur. Bir bekleyen kesme noktasının sıfır olmayan bir modül kimliği varsa, o kesme noktası o belirli modüldeki bir işleve özeldir. Bekleyen kesme noktasının modül kimliği sıfırsa, o kesme noktası henüz yüklenmeyen modüller için geçerli olur.<br /><br /> Kullanım **-temizleyin** veya **- clearall** bekleyen kesme noktaları listesinden kaldırmak için seçeneği.|  
|**CLRStack** [**-a**] [**-l**] [**-p**] [**-n**]|Yalnızca bir yönetilen kodların bir yığın izlemesini sağlar.<br /><br /> **-P** seçenek Yönetilen işlev bağımsız değişkenleri gösterir.<br /><br /> **-L** seçenek çerçevesinde yerel değişkenleri hakkında bilgi gösterir. Yerel adları için çıktı biçiminde olacak şekilde SOS hata ayıklama uzantısı yerel adları alınamıyor \< *yerel adres* >   **=**  \< *değeri*>.<br /><br /> **-a**(Tümü) seçeneği için bir kısayoludur **-l** ve **-p**birleştirilmiş.<br /><br />  **-n**  Seçeneği, kaynak dosya adlarını ve satır numaralarını görüntülemeyi devre dışı bırakır. Hata ayıklayıcı için SYMOPT_LOAD_LINES seçeneği belirtildiyse, SOS yönetilen her çerçeve için simgelere bakar ve başarılı olursa, ilgili dosya adını ve satır numarasını görüntüler.  **-n**  (Satır numarası yok) parametre, bu davranışı devre dışı bırakmak için belirtilebilir.<br /><br /> SOS Hata Ayıklama Uzantısı, x64 ve IA-64 tabanlı platformlarda geçiş çerçevelerini görüntülemez.|  
|**COMState**|Her iş parçacığı için COM apartman modeli listeler ve `Context` işaretçi, varsa.|  
|**DumpArray** [**-başlangıç** \< *startIndex*>] [**-uzunluk** \< *uzunluğu*>] [**-Ayrıntılar**] [**- nofields**] \< *dizi nesnesi adresi*><br /><br /> veya<br /><br /> **DA** [**-başlangıç** \< *startIndex*>] [**-uzunluk** \< *uzunluğu*>] [**-ayrıntı**] [**- nofields**] *dizi nesnesi adresi*>|Bir dizi nesnesinin öğelerini inceler.<br /><br /> **-Başlangıç** seçeneği öğeleri görüntülemek için başlangıç dizini belirtir.<br /><br /> **-Uzunluk** seçeneği göstermek için kaç tane öğeleri belirtir.<br /><br /> **-Ayrıntılar** seçenek öğesi kullanılarak ayrıntılarını görüntüler **DumpObj** ve **DumpVC** biçimleri.<br /><br /> **- Nofields** seçeneği görüntülemede diziler engeller. Bu seçenek yalnızca olan **-ayrıntı** seçeneği belirtildi.|  
|**DumpAssembly** \< *derleme adresi*>|Bir derlemeyle ilgili bilgileri görüntüler.<br /><br /> **DumpAssembly** komut varsa birden fazla modülü listeler.<br /><br /> Bir derleme adresi kullanarak alabileceğiniz **DumpDomain** komutu.|  
|**DumpClass** \< *EEClass adresi*>|Hakkında daha fazla bilgi görüntüler `EEClass` türü ile ilişkili yapısı.<br /><br /> **DumpClass** komutu statik alan değerlerini görüntüler, ancak statik olmayan alan değerlerini görüntülemez.<br /><br /> Kullanım **DumpMT**, **DumpObj**, **Name2EE**, veya **Token2EE** almak için komut bir `EEClass` adresi yapılandırın.|  
|**DumpDomain** [\<*etki alanı adresi*>]|Her numaralandırır <xref:System.Reflection.Assembly> diğer bir deyişle nesne belirtilen içinde yüklenen <xref:System.AppDomain> nesne adresi.  Hiçbir parametrelerle çağrıldığında **DumpDomain** komutu tüm listeler <xref:System.AppDomain> nesneleri sürecinde.|  
|**DumpHeap** [**-stat**] [**-dizeleri**] [**-kısa**] [**-min** \< *boyutu*>] [**-max** \< *boyutu*>] [**- thinlock**] [**- startAtLowerBound**] [**- mt** \< *MethodTable adresi*>] [**-türü** \< *kısmi tür adı*>] [*Başlat* [*son*]]|Toplanan çöp yığınıyla ilgili bilgileri ve nesnelerle ilgili toplama istatistiklerini görüntüler.<br /><br /> **DumpHeap** komutu atık toplayıcı yığınında aşırı parçalanma algılarsa bir uyarı görüntüler.<br /><br /> **-Stat** seçeneği için istatistiksel türü özeti çıkış kısıtlar.<br /><br /> **-Dizeleri** seçeneği bir istatistik dize değeri Özet çıkış kısıtlar.<br /><br /> **-Kısa** seçeneği her nesne adresine çıkış sınırlar. Bu, otomasyon için komuttan başka bir hata ayıklayıcı komutuna kolayca çıktı yönlendirmenize olanak sağlar.<br /><br /> **-Min** seçeneği olan nesneler yoksayar küçük `size` bayt cinsinden belirtilen parametresi.<br /><br /> **-Max** seçeneği yoksayar daha büyük olan nesneler `size` bayt cinsinden belirtilen parametresi.<br /><br /> **- Thinlock** seçeneği ThinLocks bildirir.  Daha fazla bilgi için bkz: **SyncBlk** komutu.<br /><br /> `-startAtLowerBound` Seçeneği alt sınır sağlanan adres aralığına başlamak için yığın ilerlemesi zorlar. Planlama aşamasında, nesneler taşınmakta olduğundan, yığın genellikle yürünebilir değildir. Bu seçenek zorlar **DumpHeap** belirtilen alt sınırı, kendi ilerlemesi başlamak için. Bu seçeneğin çalışması alt sınır olarak geçerli bir nesne adresi sağlamanız gerekir. Sonraki yöntem tablosunu el ile bulmak için, bozuk bir nesnenin adresindeki belleği görüntüleyebilirsiniz. Çöp toplama şu anda yapılan bir çağrı ise `memcopy`, ayrıca bir parametre olarak sağlanan başlangıç adresi boyutu ekleyerek sonraki nesne adresini bulmak mümkün olabilir.<br /><br /> **- Mt** seçeneği listeler yalnızca belirtilen karşılık nesneleri `MethodTable` yapısı.<br /><br /> **-Türü** seçeneği yalnızca türü adı olan bir eşleşmesinin belirtilen dizenin nesneleri listeler.<br /><br /> `start` Parametresi belirtilen adres listesindeki başlar.<br /><br /> `end` Parametresi belirtilen adresteki listeleme durdurur.|  
|**DumpIL** \< *DynamicMethod yönetilen nesne*> &#124;       \< *DynamicMethodDesc işaretçi*> &#124;        \< *MethodDesc işaretçi*>|Yönetilen bir yöntemle ilişkili Microsoft ara dilini (MSIL) görüntüler.<br /><br /> Dinamik MSIL'in bir derlemeden yüklenen MSIL'den farklı şekilde yayıldığını unutmayın. Dinamik MSIL, meta veri belirteçleri yerine, bir yönetilen nesne dizisindeki nesnelere başvurur.|  
|**DumpLog** [**- addr** \< *addressOfStressLog*>] [<*Filenam*`e`>]|Bir bellek içi yük günlüğünün içeriğini belirtilen dosyaya yazar. Bir ad belirtmezseniz, bu komut geçerli dizinde StressLog.txt adlı bir dosya oluşturur.<br /><br /> Bellek içi yük güvenliği, kilitler veya G/Ç kullanmadan yük hatalarını tanılamanıza yardımcı olur. Stres günlüğünü etkinleştirmek için aşağıdaki kayıt defteri anahtarlarını HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft altında ayarlamak\\. NETFramework:<br /><br /> (DWORD) StressLog = 1<br /><br /> (DWORD) LogFacility = 0xffffffff<br /><br /> (DWORD) StressLogSize = 65536<br /><br /> İsteğe bağlı `-addr` seçeneği stres günlük varsayılan günlük dışında belirtmenize olanak sağlar.|  
|**DumpMD** \< *MethodDesc adresi*>|Hakkında daha fazla bilgi görüntüler bir `MethodDesc` belirtilen adresteki yapısı.<br /><br /> Kullanabileceğiniz **IP2MD** almak için komut `MethodDesc` yapısı yönetilen bir işlev adresinden.|  
|**DumpMT** [**-MD**] \< *MethodTable adresi*>|Belirtilen bir adresteki bir yöntem tablosuyla ilgili bilgileri görüntüler. Belirtme **-MD** seçeneği nesnesiyle tanımlanan tüm yöntemleri listesini görüntüler.<br /><br /> Her bir yönetilen nesne bir yöntem tablosu işaretçisi içerir.|  
|**DumpMethodSig** \< *sigaddr*><*moduleadd*`r`>|Hakkında daha fazla bilgi görüntüler bir `MethodSig` belirtilen adresteki yapısı.|  
|**DumpModule** [**- mt**] \< *modülü adresi*>|Belirtilen adresteki bir modülle ilgili bilgileri görüntüler. **- Mt** seçenek görüntüler modülde tanımlanmış türleri ve modül tarafından başvurulan türleri<br /><br /> Kullanabileceğiniz **DumpDomain** veya **DumpAssembly** bir modülün adresi almak için komutu.|  
|**DumpObj** [**- nofields**] \< *nesne adresi*><br /><br /> veya<br /><br /> **YAPMAK** \< *nesne adresi*>|Belirtilen adresteki bir nesneyle ilgili bilgileri görüntüler. **DumpObj** komut görüntüler alanları `EEClass` yapı bilgileri, yöntemi tablo ve nesnenin boyutu.<br /><br /> Kullanabileceğiniz **DumpStackObjects** nesnenin adresi almak için komutu.<br /><br /> Çalıştırabilirsiniz Not **DumpObj** türünde alanlar komutunu `CLASS` de nesneler olduğundan.<br /><br /> `-` **Nofields** seçeneği engeller görüntülenmesini nesnesinin alanlarını, dize gibi nesneler için kullanışlıdır.|  
|**DumpRuntimeTypes**|Çöp toplayıcı yığınındaki çalışma zamanı türü nesneleri görüntüler ve ilişkili tür adlarını ve yöntem tablolarını listeler.|  
|**DumpStack** [**- EE**] [**-n**] [`top` *yığın* [`bottom` *stac* `k`]]|Bir yığın izleme görüntüler.<br /><br /> **- EE** seçeneği neden **DumpStack** görüntülemek için komut yalnızca yönetilen işlevleri. Kullanım `top` ve `bottom` üzerinde x86 görüntülenen yığın çerçeveleri sınırlamak için parametreleri platformlar.<br /><br />  **-n**  Seçeneği, kaynak dosya adlarını ve satır numaralarını görüntülemeyi devre dışı bırakır. Hata ayıklayıcı için SYMOPT_LOAD_LINES seçeneği belirtildiyse, SOS yönetilen her çerçeve için simgelere bakar ve başarılı olursa, ilgili dosya adını ve satır numarasını görüntüler.  **-n**  (Satır numarası yok) parametre, bu davranışı devre dışı bırakmak için belirtilebilir.<br /><br /> Platformlarda x86 hem x64 **DumpStack** komut ayrıntılı yığın izlemesi oluşturur.<br /><br /> IA-64 tabanlı platformlarda **DumpStack** komutu Hata Ayıklayıcı'nın taklit eder **K** komutu. `top` Ve `bottom` IA-64 tabanlı platformlarda parametreleri yok sayılır.|  
|**DumpSig** \< *sigaddr*> \<*moduleaddr*>|Hakkında daha fazla bilgi görüntüler bir `Sig` belirtilen adresteki yapısı.|  
|**DumpSigElem** \< *sigaddr*> \<*moduleaddr*>|Bir imza nesnesinin tek bir öğesini görüntüler. Çoğu durumda, kullanmanız gereken **DumpSig** imzanın nesneler aramak için. Ancak, bir imza herhangi bir şekilde bozulmuş, kullanabileceğiniz **DumpSigElem** geçerli bölümlerini okunamıyor.|  
|**DumpStackObjects** [**-doğrulayın**] [`top` *yığın* [`bottom` *yığın*]]<br /><br /> veya<br /><br /> **DSO** [**-doğrulayın**] [`top` *yığın* [`bottom` *yığın*]]|Geçerli yığının sınırları içinde bulunan tüm yönetilen nesneleri görüntüler.<br /><br /> **-Doğrulayın** seçeneği doğrular statik olmayan her `CLASS` bir nesne alanı alanı.<br /><br /> Kullanım **DumpStackObject** yığın izleme komutları ile gibi komut **K** komut ve **CLRStack** yerel değişkenlerin değerleri belirlemek için komut ve parametreleri.|  
|**DumpVC** \< *MethodTable adresi*> \<*adresi*>|Belirtilen adresteki bir değer sınıfının alanlarıyla ilgili bilgileri görüntüler.<br /><br /> **MethodTable** parametresi verir **DumpVC** doğru alanları yorumlamak için komutu. Değer sınıfları, ilk alanları olarak bir yöntem tablosuna sahip değildir.|  
|**EEHeap** [**-gc**] [**-yükleyicisi**]|İşlem bellek iç CLR veri yapılarını tarafından tüketilen hakkındaki bilgileri görüntüler.<br /><br /> **-Gc** ve **-yükleyicisi** seçenekleri sınırlamak atık toplayıcı veya yükleyicisi veri yapılarına bu komutun çıktısı.<br /><br /> Çöp toplayıcıya ilişkin bilgiler, yönetilen yığındaki her bir segmentin aralıklarını listeler.  İşaretçinin tarafından verilen bir kesim aralığı içine düşerse, **-gc**, bir nesne işaretçisi işaretçidir.|  
|**EEStack** [**-kısa**] [**- EE**]|Çalıştırır **DumpStack** işlemdeki tüm iş parçacıklarının üzerinde komutu.<br /><br /> **- EE** seçeneği doğrudan geçirilen **DumpStack** komutu. **-Kısa** parametresi sınırlar iş parçacığı şu tür çıkışı:<br /><br /> Kilit almış olan iş parçacıkları.<br /><br /> Çöp toplamaya olanak tanımak için durdurulmuş iş parçacıkları.<br /><br /> Yönetilen kodda bulunan iş parçacıkları.|  
|**EEVersion**|CLR sürümünü görüntüler.|  
|**EHInfo** [\<*MethodDesc adresi*>] [\<*kod adresi*>]|Belirtilen bir yöntemdeki özel durum işleme bloklarını görüntüler.  Bu komut kodu adreslerini ve yan tümcesi blok için uzaklık görüntüler ( `try` blok) ve işleyici engelle ( `catch` blok).|  
|**SSS**|Sık sorulan soruları görüntüler.|  
|**FinalizeQueue** [**-ayrıntı**] &#124; [**- allReady**] [**-kısa**]|Sonlandırma için kaydolan tüm nesneleri görüntüler.<br /><br /> **-Ayrıntı** seçenek görüntüler herhangi hakkında ek bilgi `SyncBlocks` Temizlenen gereken ve tüm `RuntimeCallableWrappers` (RCWs) temizleme bekler. Bu veri yapılarının her ikisi de, çalıştığı zaman sonlandırıcı tarafından ön belleğe kaydedilir.<br /><br /> `-allReady` Seçeneği veya bağımsız olarak mı bunlar şekilde atık toplama tarafından önceden işaretlenmiş sonraki atık toplama tarafından işaretlenecek sonlandırma için hazır olan tüm nesneleri görüntüler. "Sonlandırma için hazır" listesinde olan nesneler, artık köklü olmayan sonlandırılabilir nesnelerdir. Sonlandırılabilir kuyruklarda bulunan tüm nesnelerin hala köklü olduğunu doğruladığından, bu seçenek çok pahalı olabilir.<br /><br /> `-short` Seçeneği her nesne adresine çıkış sınırlar. İle birlikte kullanılırsa **- allReady**, artık kökü için bir sonlandırıcı sahip tüm nesneleri numaralandırır. Bağımsız olarak kullanılırsa, sonlandırılabilir ve "sonlandırmaya hazır" kuyruklardaki tüm nesneleri listeler.|  
|**FindAppDomain** \< *nesne adresi*>|Belirtilen adresteki bir nesnenin uygulama etki alanını belirler.|  
|**FindRoots** **-gen** \< *N*> &#124; **-herhangi bir gen** &#124;\< *nesne adresi*>|Belirtilen oluşturmanın sonraki toplamasında, hata ayıklayıcının hatası ayıklanan öğeyi yarıda kesmesine neden olur. Kesme oluşur oluşmaz, etki sıfırlanır. Sonraki toplamayı kesmek için, komutu tekrar vermeniz gerekir.  *\<Nesne adresi >* formu bu komutun nedeni break sonra kullanılır **-gen** veya **-herhangi bir gen** oluştu. O anda ayıklayıcı sağ için durumda **FindRoots** kökler geçerli nesne için tanımlamak için nesli condemned.|  
|**GCHandles** [**- perdomain**]|İşlemdeki çöp toplayıcı tanıtıcılarıyla ilgili istatistikleri görüntüler.<br /><br /> **- Perdomain** seçeneği istatistiklerini uygulama etki alanına göre düzenler.<br /><br /> Kullanım **GCHandles** bellek sızıntıları atık toplayıcı tanıtıcı sızıntıları tarafından nedeni bulmak için komutu. Örneğin, kesin olarak belirlenmiş bir çöp toplayıcı tanıtıcısı hala onu işaret ettiği için kod büyük bir diziyi tuttuğunda, bir bellek sızıntısı olur ve tanıtıcı onu serbest bırakmadan atılır.|  
|**GCHandleLeaks**|Kesin olarak belirlenmiş ve iliştirilmiş çöp toplayıcı tanıtıcılarına yapılan başvurular için bellekte arama yapar ve sonuçları görüntüler. Bir tanıtıcı bulunursa, **GCHandleLeaks** komut başvurusu adresini görüntüler. Bellekte bir tanıtıcı bulunmazsa, bu komut bir bildirim görüntüler.|  
|**GCInfo** \< *MethodDesc adresi*>\<*kod adresi*>|Kayıt defterlerinin ve yığın konumlarının yönetilen nesneleri ne zaman içerdiğini gösteren verileri görüntüler. Bir çöp toplama olursa, onları yeni nesne işaretçisi değerleriyle güncelleştirebilmesi için, toplayıcı nesnelere yapılan başvuruların konumlarını bilmelidir.|  
|**GCRoot** [**- nostacks**] \< *nesne adresi*>|Belirtilen adresteki bir nesneye yapılan başvurularla (veya köklerle) ilgili bilgi görüntüler.<br /><br /> **GCRoot** komutu tüm yönetilen yığın inceler ve diğer içinde tanıtıcıları için tanıtıcı tablo nesneleri ve yığında işler. Sonra, her bir yığında nesne işaretçileri aranır ve sonlandırıcı kuyruğunda da arama yapılır.<br /><br /> Bu komut, bir yığın kökünün geçerli veya atılmış olduğunu belirlemez. Kullanmak **CLRStack** ve **U** yerel veya bir bağımsız değişken değeri yığını kök hala kullanımda olup olmadığını belirlemek için ait olduğu çerçeve ayrıştırmak için komutları.<br /><br /> **- Nostacks** seçenek atık toplayıcı tanıtıcıları ve freachable nesneleri için arama kısıtlar.|  
|**GCWhere***\<nesne adresi >* |Geçirilen bağımsız değişkenin çöp toplama yığınındaki konumu ve büyüklüğü görüntüler. Bağımsız değişken yönetilen yığında yer aldığında, fakat geçerli bir nesne adresi olmadığında, büyüklük 0 (sıfır) olarak görüntülenir.|  
|**Yardım** [\<*komutu*>] [`faq`]|Parametre belirtilmediğinde kullanılabilir olan tüm komutları görüntüler veya belirli komutla ilgili ayrıntılı yardım bilgilerini görüntüler.<br /><br /> `faq` Parametresi sık sorulan soruların yanıtlarını görüntüler.|  
|**HeapStat** [**- inclUnrooted** &#124; **-IU**]|Her bir yığın için oluşturma büyüklüğünü ve her bir yığındaki her bir oluşturmada bulunan toplam boş alanı görüntüler. Varsa**inclUnrooted** seçeneği belirtildiğinde, rapor artık kökü belirtilmiş atık toplama yığın yönetilen nesneleri hakkında bilgiler içerir.|  
|**HistClear**|Ailesi tarafından kullanılan tüm kaynakları serbest `Hist` komutları.<br /><br /> Genellikle, açıkça çağırın gerekmez `HistClear`, çünkü her `HistInit` önceki kaynakları siler.|  
|**HistInit**|Hatası ayıklanana kaydedilen yük günlüğünden SOS yapılarını başlatır.|  
|**HistObj** *< obj_address >*|Tüm yük günlüğü yeniden yerleştirme kayıtlarını inceler ve bir bağımsız değişken olarak geçirilen adrese yönlendirebilecek çöp toplama yeniden konumlandırmaları zincirini görüntüler.|  
|**HistObjFind***< obj_address >* |Belirtilen adresteki bir nesneye başvuran tüm günlük girişlerini görüntüler.|  
|**HistRoot**  *\<kök >*|Belirtilen kökün tanıtımlarıyla ve yeniden konumlandırılmalarıyla ilişkili bilgileri görüntüler.<br /><br /> Kök değeri, bir nesnenin çöp toplamalar içindeki hareketini izlemek için kullanılabilir.|  
|**IP2MD** \< *kod adresi*>|Görüntüler `MethodDesc` JIT derlenmiş Code belirtilen adresteki yapısı.|  
|`ListNearObj`(`lno`) *< obj_address >*|Belirtilen adresten önceki ve sonraki nesneleri görüntüler. Komut, yönetilen bir nesnenin (geçerli bir yöntem tablosuna dayalı olarak) ve bağımsız değişken adresini izleyen nesnenin geçerli bir başlangıcı gibi görünen çöp toplama yığınında adresi arar.|  
|**MinidumpMode** [**0**] [**1**]|Bir mini döküm kullanırken, güvenli olmayan komutların çalışmasını önler.<br /><br /> Geçirmek **0** bu özelliği devre dışı bırakmak veya **1** bu özelliği etkinleştirmek için. Varsayılan olarak, **MinidumpMode** değeri ayarı **0**.<br /><br /> Mini dökümler oluşturulan ile **.dump /m** komut veya **.dump** komutu CLR özgü verileri sınırlı ve SOS komutları yalnızca bir kısmı düzgün çalışmasına olanak sağlar. Gerekli bellek alanları eşleşmediğinden veya kısmen eşleştiğinden, bazı komutlar beklenmeyen hatalarla başarısız olabilir. Bu seçenek, mini dökümlere karşı güvenli olmayan komutları çalıştırmaktan sizi korur.|  
|**Name2EE** \< *modül adı*> \<*türü veya yöntemi adı*><br /><br /> veya<br /><br /> **Name2EE** \< *modül adı*>**!** \< *türü veya yöntemi adı*>|Görüntüler `MethodTable` yapısı ve `EEClass` belirtilen türe veya belirtilen modül yönteminde yapısı.<br /><br /> Belirtilen modülün işlemde yüklenmesi gerekir.<br /><br /> Uygun türde adını almak için modül kullanarak Gözat [Ildasm.exe (IL ayrıştırıcı)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md). Ayrıca iletebilirsiniz `*` yönetilen modüller name parametresi tüm arama modülü olarak yüklenir. *Modül adı* parametresi de olabilir bir modül için hata ayıklayıcı'nın ad gibi `mscorlib` veya `image00400000`.<br /><br /> Bu komut Windows hata ayıklayıcı sözdizimini destekler <`module`>`!`<`type`>. Tür, tam olarak nitelenmiş olmalıdır.|  
|**ObjSize** [\<*nesne adresi*>] &#124; [**-birleşik**] [**-stat**]|Belirtilen nesnenin boyutunu görüntüler. Herhangi bir parametre belirtmezseniz **ObjSize** komutu yönetilen iş parçacıklarında bulunan tüm nesnelerin boyutunu görüntüler, işlemde tüm atık toplayıcı tanıtıcıları görüntüler ve bu işleyici tarafından işaret herhangi bir nesne boyutunu toplar. **ObjSize** komut boyutu üst yanı sıra tüm alt nesneleri içerir.<br /><br /> **-Birleşik** seçeneği ile birlikte kullanılabilir **-stat** hala olsunlar türleri ayrıntılı görünümünü almak için bağımsız değişken. Kullanarak **! dumpheap-stat** ve **! objsize-toplama - çubuklu**, hangi nesnelerin çeşitli bellek sorunlarını tanılamak ve artık olsunlar belirleyebilirsiniz.|  
|**PrintException** [**-iç içe geçmiş**] [**-satırları**] [\<*özel durum nesnesi adresi*>]<br /><br /> veya<br /><br /> **PE** [**-iç içe geçmiş**] [\<*özel durum nesnesi adresi*>]|Görüntüler ve türetilmiş herhangi bir nesnenin alanları biçimleri <xref:System.Exception> belirtilen adresteki sınıfı. Bir adresi belirtmezseniz **PrintException** komutu, geçerli iş parçacığı üzerinde son durum görüntüler.<br /><br /> **-İç içe geçmiş** seçeneği, iç içe geçmiş özel durum nesneleri hakkındaki ayrıntıları görüntüler.<br /><br /> **-Satırları** seçeneği kullanılabiliyorsa kaynak bilgilerini görüntüler.<br /><br /> Bu komutu biçimlendirmek ve görünümü kullanabilirsiniz `_stackTrace` ikili bir dizi alanı.|  
|**ProcInfo** [**- env**] [**-zaman**] [**-mem**]|İşlem, çekirdek CPU süresi ve bellek kullanımı istatistikleri için ortam değişkenlerini görüntüler.|  
|**RCWCleanupList** \< *RCWCleanupList adresi*>|Belirtilen adreste temizlenmeyi bekleyen çalışma zamanı çağrılabilir sarmalayıcılarının listesini görüntüler.|  
|**SaveModule** \< *temel adresi*> \<*dosya adı*>|Belirtilen adreste belleğe yüklenen bir görüntüyü belirtilen dosyaya yazar.|  
|**SOSFlush**|Bir iç SOS önbelleğini temizler.|  
|**StopOnException** [**-türetilen**] [**-oluşturmak** &#124; **-create2**] \< *özel durum*> \<*sözde kayıt numarası*>|Belirtilen özel durum oluştuğunda hata ayıklayıcının durmasına, fakat diğer özel durumlar oluştuğunda çalışmaya devam etmesine neden olur.<br /><br /> **-Türetilen** seçeneği, belirtilen özel durum ve belirtilen özel durum türetilen her özel durum yakalar.|  
|**SyncBlk** [**-tüm** &#124; \< *syncblk numarası*>]|Belirtilen görüntüler `SyncBlock` yapısı veya tüm `SyncBlock` yapıları.  Tüm bağımsız değişkenleri geçirmezseniz **SyncBlk** komutu görüntüler `SyncBlock` bir iş parçacığı tarafından sahip olunan nesneler karşılık gelen yapısı.<br /><br /> A `SyncBlock` yapısı her nesne için oluşturulan gerekmez ek bilgi için bir kapsayıcıdır. COM birlikte çalışabilirlik verilerini, karma kodları ve güvenli iş parçacığı işlemlerine ilişkin kilitleme bilgilerini tutabilir.|  
|**İş parçacığı havuzu**|Kuyruktaki iş isteklerinin sayısı, derleme bağlantı noktası iş parçacıklarının sayısı ve zamanlayıcıların sayısı dahil, yönetilen iş parçacığı havuzuyla ilgili bilgileri görüntüler.|  
|**Token2EE** \< *modül adı*> \<*belirteci*>|Belirtilen meta veriler belirtilen modülde belirteci kapatır bir `MethodTable` yapısı veya `MethodDesc` yapısı.<br /><br /> Geçirebilirsiniz `*` ne belirtecini yüklenen her yönetilen modülünde eşlendiği bulmak modül adı parametresi için. Bir modül için hata ayıklayıcı'nın ad gibi geçirebilirsiniz `mscorlib` veya `image00400000`.|  
|**İş parçacığı** [**-canlı**] [**-özel**]|İşlemdeki tüm yönetilen iş parçacıklarını görüntüler.<br /><br /> **İş parçacığı** komut görüntüler kestirme kimliği, CLR iş parçacığı kimliği ve işletim sistemi iş parçacığı kimliği hata ayıklayıcı  Ayrıca, **iş parçacığı** komutu, bir iş parçacığı Yürütülüyor uygulama etki alanını gösterir bir etki alanı sütun COM Grup modu görüntüleyen bir APT sütun ve son görüntüleyen bir özel durum sütununa görüntüler iş parçacığında özel durum oluştu.<br /><br /> **-Canlı** seçenek Canlı iş parçacığı ile ilişkili iş parçacıkları görüntüler.<br /><br /> **-Özel** seçenek CLR tarafından oluşturulan tüm özel iş parçacığı görüntüler. Özel iş parçacığı dahil atık toplama iş parçacıkları (eşzamanlı ve sunucu çöp toplama), hata ayıklayıcı yardımcı iş parçacığı, sonlandırıcıyı iş parçacığı <xref:System.AppDomain> iş parçacıkları ve iş parçacığı havuzu Zamanlayıcı iş parçacıkları kaldırın.|  
|**ThreadState \<**  *durumu değeri alanı***>**|Bir iş parçacığının durumunu görüntüler. `value` Parametredir değerini `State` alanındaki **iş parçacığı** rapor çıktı.<br /><br /> Örnek:<br /><br /> `0:003> !Threads     ThreadCount:      2     UnstartedThread:  0     BackgroundThread: 1     PendingThread:    0     DeadThread:       0     Hosted Runtime:   no                                           PreEmptive   GC Alloc           Lock            ID OSID ThreadOBJ    State     GC       Context       Domain   Count APT Exception        0    1  250 0019b068      a020 Disabled 02349668:02349fe8 0015def0     0 MTA        2    2  944 001a6020      b220 Enabled  00000000:00000000 0015def0     0 MTA (Finalizer)     0:003> !ThreadState b220         Legal to Join         Background         CLR Owns         CoInitialized         In Multi Threaded Apartment`|  
|**TraverseHeap** [**- xml**] \< *dosya adı*>|Yığın bilgilerini, CLR profil oluşturucusunun anlayacağı bir biçimde belirtilen dosyaya yazar. **- Xml** seçeneği neden **TraverseHeap** dosyayı XML olarak biçimlendirmek için komutu.<br /><br /> CLR Profil Oluşturucu'dan indirebilirsiniz [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=67325).|  
|**U** [**- gcinfo**] [**- ehinfo**] [**-n**] \< *MethodDesc adresi*> & # 124; \< *Kod adresi*>|Görüntüler yönetilen yönteminin açıklamalı bir ayrıştırılmış ya da belirtilen bir `MethodDesc` yapı işaretçi yöntemi veya yöntem gövdesinin içindeki kod adresi. **U** komutu, meta veri simgesi adlara dönüştürme ek açıklamaları başından tüm yöntemi görüntüler.<br /><br /> **- Gcinfo** seçeneği neden **U** görüntülemek için komut `GCInfo` yöntemi için yapısı.<br /><br /> **- Ehinfo** seçenek yöntemi için özel durum bilgilerini görüntüler. Bu bilgiyle edinebilirsiniz **EHInfo** komutu.<br /><br />  **-n**  Seçeneği, kaynak dosya adlarını ve satır numaralarını görüntülemeyi devre dışı bırakır. Hata ayıklayıcı için SYMOPT_LOAD_LINES seçeneği belirtildiyse, SOS yönetilen her çerçeve için simgelere bakar ve başarılı olursa, ilgili dosya adını ve satır numarasını görüntüler. Belirleyebileceğiniz  **-n**  bu davranışı devre dışı bırakma seçeneği.|  
|**VerifyHeap**|Bozulma işaretleri için çöp toplayıcı yığınını kontrol eder ve bulunan hataları görüntüler.<br /><br /> Yığın bozulmalarına, hatalı oluşturulan platform çağrıları neden olabilir.|  
|**VerifyObj** \< *nesne adresi*>|Bir bağımsız değişken olarak geçirilen nesnede bozulma işaretleri olup olmadığını kontrol eder.|  
|**VMMap**|Sanal adres alanını bir uçtan diğerine dolaşır ve her bir bölgeye uygulanan koruma türünü görüntüler.|  
|**VMStat**|Sanal adres alanının bir özet görünümü, o belleğe (serbest, ayrılmış, adanmış, özel, eşlenmiş, görüntü) uygulanan her bir koruma türüne göre düzenlenmiş olarak sağlar. TOPLAM sütunu, ORTALAMA sütununun sonucunu BLK SAYIMI sütunuyla çarpılmış olarak görüntüler.|  
  
## <a name="remarks"></a>Açıklamalar  
 SOS hata ayıklama uzantısı CLR'nin içinde çalışan kodu hakkında bilgi görüntülemenize olanak tanır. Örneğin, yönetilen yığınla ilgili bilgileri görüntülemek, yığın bozulmalarını aramak, çalışma zamanı tarafından kullanılan iç veri türlerini görüntülemek ve çalışma zamanı içinde çalışan tüm yönetilen kodla ilgili bilgileri görüntülemek için SOS Hata Ayıklama Uzantısı'nı kullanabilirsiniz.  
  
 Visual Studio'da SOS hata ayıklama uzantısını kullanmak için yükleme [Windows Sürücü Seti (WDK)](http://msdn.microsoft.com/windows/hardware/hh852362). Visual Studio tümleşik hata ayıklama ortamında hakkında daha fazla bilgi için bkz: [hata ayıklama ortamları](http://msdn.microsoft.com/library/windows/hardware/hh406268.aspx) Windows geliştirme Merkezi'ndeki.  
  
 SOS hata ayıklama uzantısı kullanılabilir WinDbg.exe hata ayıklayıcı içine yükleyerek kullanabilirsiniz [WDK ve geliştirici araçları Web sitesi](http://go.microsoft.com/fwlink/?LinkId=103787)ve WinDbg.exe içindeki komutları çalıştırma.  
  
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
 Aşağıdaki komut adresinde bir dizinin içeriğini görüntüler `00ad28d0`.  Görüntü ikinci öğeden başlar ve beş öğe boyunca devam eder.  
  
```  
!dumparray -start 2 -length 5 -detail 00ad28d0   
```  
  
 Aşağıdaki komut adresinde bir derlemeyi içeriğini görüntüler `1ca248`.  
  
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
  
 Aşağıdaki komut görüntüler `MethodDesc` adresinde yapısı `902f40`.  
  
```  
!dumpmd 902f40  
```  
  
 Aşağıdaki komut adresinde bir modülü hakkında bilgi görüntüler `1caa50`.  
  
```  
!dumpmodule 1caa50  
```  
  
 Aşağıdaki komut adresinde bir nesne hakkında bilgi görüntüler `a79d40`.  
  
```  
!DumpObj a79d40  
```  
  
 Aşağıdaki komut bir değer sınıfı alanlarının adresinde görüntüler `00a79d9c` adresinde yöntemi tablosunu kullanarak `0090320c`.  
  
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
  
 Aşağıdaki komutu bir nesnenin adresinde uygulama etki alanı belirler `00a79d98`.  
  
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
  
 Aşağıdaki komut adresinde meta veri simgesi hakkında bilgi görüntüler `02000003` modülünde `unittest.exe`.  
  
```  
!token2ee unittest.exe 02000003  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Araçlar](../../../docs/framework/tools/index.md)  
 [Komut İstemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
