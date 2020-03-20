---
title: SOS.dll (SOS Hata Ayıklama Uzantısı)
ms.date: 03/30/2017
helpviewer_keywords:
- debugging extensions
- SOS debugging extensions
- SOS.dll
ms.assetid: 9ac1b522-77ab-4cdc-852a-20fcdc9ae498
ms.openlocfilehash: 4c3a7f2798791f0c8a6b752f06bc2937fc970d40
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75715725"
---
# <a name="sosdll-sos-debugging-extension"></a>SOS.dll (SOS hata ayıklama uzantısı)

SOS Hata Ayıklama Uzantısı (SOS.dll), iç Ortak Dil Çalışma Süresi (CLR) ortamı hakkında bilgi sağlayarak Visual Studio'da ve Windows hata ayıklayıcısında (WinDbg.exe) yönetilen programları hata ayıklamanıza yardımcı olur. Bu araç, projenizde yönetilmeyen hata ayıklamanın etkin olmasını gerektirir. SOS.dll, .NET Framework ile birlikte otomatik olarak yüklenir. Visual Studio'da SOS.dll kullanmak için [Windows Sürücü Kiti'ni (WDK)](/windows-hardware/drivers/download-the-wdk)yükleyin.

## <a name="syntax"></a>Sözdizimi

```console
![command] [options]
```

## <a name="commands"></a>Komutlar

|Komut|Açıklama|
|-------------|-----------------|
|**AnalyzeOOM** (**ao**)|Çöp toplama yığınına ayırma isteğinde oluşan bellek dışında son bilgileri (OOM) görüntüler. (Sunucu çöpü toplamada, her bir çöp toplama yığınında varsa OOM görüntüler.)|
|**BPMD** [**-nofuturemodule**] [\<modül*adı*> \<*yöntem adı*>] [**-md**  < `MethodDesc`>] **-liste** **-bekleyen** \< *kesme noktası numarası*> **-clearall**|Belirtilen modül içinde belirtilen yöntemde bir kesme noktası oluşturur.<br /><br /> Belirtilen modül ve yöntem yüklenmediyse, bu komut, modülün yüklendiğine ve bir kesme noktası oluşturmadan önce tam zamanında (JIT) derlediğine ilişkin bir bildirim bekler.<br /><br /> Bekleyen kesme noktalarılistesini **-liste**, **-temizve** **-tüm** seçenekleri kullanarak yönetebilirsiniz:<br /><br /> **-liste** seçeneği, bekleyen tüm kesme noktalarının bir listesini oluşturur. Bir bekleyen kesme noktasının sıfır olmayan bir modül kimliği varsa, o kesme noktası o belirli modüldeki bir işleve özeldir. Bekleyen kesme noktasının modül kimliği sıfırsa, o kesme noktası henüz yüklenmeyen modüller için geçerli olur.<br /><br /> Bekleyen kesme noktalarını listeden kaldırmak için **-açık** veya **temiztüm** seçeneğini kullanın.|
|**CLRStack** [**-a**] [**-l**] [**-p**] [**-n**]|Yalnızca bir yönetilen kodların bir yığın izlemesini sağlar.<br /><br /> **-p** seçeneği, yönetilen işlevin bağımsız değişkenlerini gösterir.<br /><br /> **-l** seçeneği, bir çerçevedeki yerel değişkenler hakkındaki bilgileri gösterir. SOS Hata Ayıklama Uzantısı yerel adları alamadığından, yerel adların çıktısı \< *yerel adres* >  **=** \< *değeri*> biçimindedir.<br /><br /> **-a**(tümü) seçeneği **-l** ve **-p** kombine için bir kısayoldur.<br /><br /> **-n** seçeneği kaynak dosya adlarının ve satır numaralarının görüntülenmesini devre dışı kılabilir. Hata ayıklayıcı için SYMOPT_LOAD_LINES seçeneği belirtildiyse, SOS yönetilen her çerçeve için simgelere bakar ve başarılı olursa, ilgili dosya adını ve satır numarasını görüntüler. **-n** (Satır numarası yok) parametresi bu davranışı devre dışı bırakılabilir.<br /><br /> SOS Hata Ayıklama Uzantısı, x64 ve IA-64 tabanlı platformlarda geçiş çerçevelerini görüntülemez.|
|**KOMİlİ**|Varsa, her iş parçacığı ve `Context` işaretçi için COM daire modelini listeler.|
|**DumpArray** [ \< *-startIndex* **-start**>] [**-uzunluk** \< *uzunluğu*>] [ \<**-ayrıntılar**] [**-nofields**] dizi nesne *adresi*><br /><br /> -veya-<br /><br /> **DA** [ \< *-startIndex*>] [**-start** **-uzunluk** \< *uzunluğu*>] [**-detay**] [**-nofields**] *dizi nesne adresi*>|Bir dizi nesnesinin öğelerini inceler.<br /><br /> **-başlat** seçeneği, öğeleri görüntülemek için başlangıç dizinini belirtir.<br /><br /> **-uzunluk** seçeneği, gösterilen kaç öğe belirtir.<br /><br /> **-ayrıntılar** **seçeneği, DumpObj** ve **DumpVC** biçimlerini kullanarak öğenin ayrıntılarını görüntüler.<br /><br /> **-nofields** seçeneği dizilerin görüntülenmesini engeller. Bu seçenek yalnızca **-ayrıntı** seçeneği belirtildiğinde kullanılabilir.|
|**DumpAssembly** \< *montaj adresi*>|Bir derlemeyle ilgili bilgileri görüntüler.<br /><br /> **DumpAssembly** komutu varsa birden çok modülü listeler.<br /><br /> **DumpDomain** komutunu kullanarak bir montaj adresi alabilirsiniz.|
|**DumpClass** \< *EEClass adresi*>|Bir türle `EEClass` ilişkili yapı yla ilgili bilgileri görüntüler.<br /><br /> **DumpClass** komutu statik alan değerlerini görüntüler, ancak statik olmayan alan değerlerini göstermez.<br /><br /> `EEClass` Bir yapı adresi almak için **DumpMT,** **DumpObj,** **Name2EE**veya **Token2EE** komutunu kullanın.|
|**DumpDomain** \<[*etki alanı adresi*>]|Belirtilen <xref:System.AppDomain> nesne adresi <xref:System.Reflection.Assembly> içinde yüklenen her nesneyi oyalar.  Parametreleri olmadan çağrıldığında, **DumpDomain** komutu bir işlemdeki tüm <xref:System.AppDomain> nesneleri listeler.|
|**DumpHeap** [**-stat**] [**-strings**] [**-kısa**] [**-min** \< *boyutu*>] [**-max** \< *boyutu*>] [**-thinlock**] [**-startAtLowerBound**] [**-mt** \< *MethodTable adres*>] [**-yazın** \<kısmi tür *adı*>][*başlat* ]*end*|Toplanan çöp yığınıyla ilgili bilgileri ve nesnelerle ilgili toplama istatistiklerini görüntüler.<br /><br /> **DumpHeap** komutu, çöp toplayıcı yığınında aşırı parçalanma algılarsa bir uyarı görüntüler.<br /><br /> **-stat** seçeneği çıktıyı istatistiksel tür özetiyle sınırlandırıyor.<br /><br /> **-strings** seçeneği çıktıyı istatistiksel dize değer özetiyle sınırlandırıyor.<br /><br /> **-kısa** seçenek çıkışı yalnızca her nesnenin adresiyle sınırlar. Bu, otomasyon için komuttan başka bir hata ayıklayıcı komutuna kolayca çıktı yönlendirmenize olanak sağlar.<br /><br /> **-min** seçeneği, baytcinsinden belirtilen `size` parametreden daha az olan nesneleri yoksa.<br /><br /> **-max** seçeneği, baytcinsinden belirtilen `size` parametreden daha büyük nesneleri yokslar.<br /><br /> **-thinlock** seçeneği ThinLocks bildirir.  Daha fazla bilgi için **Eşitleme** komutuna bakın.<br /><br /> Seçenek, `-startAtLowerBound` yığın yürüyüşünü verilen adres aralığının alt ucundan başlamaya zorlar. Planlama aşamasında, nesneler taşınmakta olduğundan, yığın genellikle yürünebilir değildir. Bu seçenek **DumpHeap'ı** belirtilen alt sınırda yürümeye zorlar. Bu seçeneğin çalışması alt sınır olarak geçerli bir nesne adresi sağlamanız gerekir. Sonraki yöntem tablosunu el ile bulmak için, bozuk bir nesnenin adresindeki belleği görüntüleyebilirsiniz. Çöp toplama şu anda bir `memcopy`çağrı da, bir parametre olarak verilen başlangıç adresine boyutu ekleyerek bir sonraki nesnenin adresini bulmak mümkün olabilir.<br /><br /> **-mt** seçeneği yalnızca belirtilen `MethodTable` yapıya karşılık gelen nesneleri listeler.<br /><br /> **-türü** seçeneği yalnızca tür adı belirtilen dize bir substring eşleme olan nesneleri listeler.<br /><br /> `start` Parametre belirtilen adresten liste başlar.<br /><br /> `end` Parametre belirtilen adreste listeyi durdurur.|
|**DumpIL** \< *Yönetilen DynamicMethod nesne*> &#124;  \< *DynamicMethodDesc işaretçisi*> &#124;  \< *MethodDesc işaretçisi*>|Yönetilen bir yöntemle ilişkili Microsoft ara dilini (MSIL) görüntüler.<br /><br /> Dinamik MSIL'in bir derlemeden yüklenen MSIL'den farklı şekilde yayıldığını unutmayın. Dinamik MSIL, meta veri belirteçleri yerine, bir yönetilen nesne dizisindeki nesnelere başvurur.|
|**DumpLog** [**-addr** \< *adresiOfStressLog*>] [<*Filenam* `e`>]|Bir bellek içi yük günlüğünün içeriğini belirtilen dosyaya yazar. Bir ad belirtmezseniz, bu komut geçerli dizinde StressLog.txt adlı bir dosya oluşturur.<br /><br /> Bellek içi yük güvenliği, kilitler veya G/Ç kullanmadan yük hatalarını tanılamanıza yardımcı olur. Stres günlüğü etkinleştirmek için aşağıdaki kayıt defteri anahtarlarını\\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft altında ayarlayın. Netframework:<br /><br /> (DWORD) StressLog = 1<br /><br /> (DWORD) LogFacility = 0xffffffff<br /><br /> (DWORD) StressLogSize = 65536<br /><br /> İsteğe `-addr` bağlı seçenek, varsayılan günlük dışında bir stres günlüğü belirtmenize olanak tanır.|
|**DumpMD** \< *MethodDesc adresi*>|Belirtilen adreste `MethodDesc` bir yapı yla ilgili bilgileri görüntüler.<br /><br /> Yapı adresini yönetilen bir işlevden `MethodDesc` almak için **IP2MD** komutunu kullanabilirsiniz.|
|**DumpMT** [**-MD**] \< *MethodTable adresi*>|Belirtilen bir adresteki bir yöntem tablosuyla ilgili bilgileri görüntüler. **-MD** seçeneğini belirtmek, nesneyle tanımlanan tüm yöntemlerin listesini görüntüler.<br /><br /> Her bir yönetilen nesne bir yöntem tablosu işaretçisi içerir.|
|**DumpMethodSig** \< *sigaddr*> <*moduleadd*`r`>|Belirtilen adreste `MethodSig` bir yapı yla ilgili bilgileri görüntüler.|
|**DumpModule** [**-mt**] \< *Modül adresi*>|Belirtilen adresteki bir modülle ilgili bilgileri görüntüler. **-mt** seçeneği, bir modülde tanımlanan türleri ve modül tarafından başvurulan türleri görüntüler<br /><br /> Bir modülün adresini almak için **DumpDomain** veya **DumpAssembly** komutunu kullanabilirsiniz.|
|**DumpObj** [**-nofields**] \< *nesne adresi*><br /><br /> -veya-<br /><br /> **DO** \< *nesne adresi*>|Belirtilen adresteki bir nesneyle ilgili bilgileri görüntüler. **DumpObj** komutu alanları, `EEClass` yapı bilgilerini, yöntem tablosunu ve nesnenin boyutunu görüntüler.<br /><br /> Bir nesnenin adresini almak için **DumpStackObjects** komutunu kullanabilirsiniz.<br /><br /> Onlar da nesneler olduğu için tür `CLASS` alanlarında **DumpObj** komutunu çalıştırabilirsiniz unutmayın.<br /><br /> `-` **Nofields** seçeneği görüntülenen nesnenin alanları engeller, String gibi nesneler için yararlıdır.|
|**DumpRuntimeTypes**|Çöp toplayıcı yığınındaki çalışma zamanı türü nesneleri görüntüler ve ilişkili tür adlarını ve yöntem tablolarını listeler.|
|**DumpStack** [**-EE**] [`top` **-n**] [ *yığın* `bottom` [ *stac*`k`]]|Bir yığın izleme görüntüler.<br /><br /> **-EE** **seçeneği, DumpStack** komutunun yalnızca yönetilen işlevleri görüntülemesine neden olur. X86 platformlarında görüntülenen yığın çerçevelerini sınırlamak için parametreleri `top` ve `bottom` parametreleri kullanın.<br /><br /> **-n** seçeneği kaynak dosya adlarının ve satır numaralarının görüntülenmesini devre dışı kılabilir. Hata ayıklayıcı için SYMOPT_LOAD_LINES seçeneği belirtildiyse, SOS yönetilen her çerçeve için simgelere bakar ve başarılı olursa, ilgili dosya adını ve satır numarasını görüntüler. **-n** (Satır numarası yok) parametresi bu davranışı devre dışı bırakılabilir.<br /><br /> X86 ve x64 platformlarında, **DumpStack** komutu ayrıntılı bir yığın izleme oluşturur.<br /><br /> IA-64 tabanlı **platformlarda, DumpStack** komutu hata ayıklamanın **K** komutunu taklit eder. Ve `top` `bottom` parametreler IA-64 tabanlı platformlarda yoksayılır.|
|**DumpSig** \< *sigaddr*> \<*moduleaddr*>|Belirtilen adreste `Sig` bir yapı yla ilgili bilgileri görüntüler.|
|**DumpSigElem** \< *sigaddr*> \<*moduleaddr*>|Bir imza nesnesinin tek bir öğesini görüntüler. Çoğu durumda, tek tek imza nesnelerine bakmak için **DumpSig'i** kullanmanız gerekir. Ancak, bir imza bir şekilde bozulmuşsa, geçerli bölümlerini okumak için **DumpSigElem'i** kullanabilirsiniz.|
|**DumpStackObjects** [**-verify**`top` ]`bottom` [ *yığın* [ *yığın*]]<br /><br /> -veya-<br /><br /> **DSO** [**-verify**`top` ]`bottom` [ *yığın* [ *yığın*]]|Geçerli yığının sınırları içinde bulunan tüm yönetilen nesneleri görüntüler.<br /><br /> **-doğrula** seçeneği, nesne alanının statik `CLASS` olmayan her alanını doğrular.<br /><br /> Yerel değişkenlerin ve parametrelerin değerlerini belirlemek için **K** komutu ve **CLRStack** komutu gibi yığın izleme komutları ile **DumpStackObject** komutunu kullanın.|
|**DumpVC** \< *MethodTable adres*> \<*adresi*>|Belirtilen adresteki bir değer sınıfının alanlarıyla ilgili bilgileri görüntüler.<br /><br /> **MethodTable** parametresi, **DumpVC** komutunun alanları doğru yorumlamasına olanak tanır. Değer sınıfları, ilk alanları olarak bir yöntem tablosuna sahip değildir.|
|**EEHeap** [**-gc**] [**-Yükleyici**]|Dahili CLR veri yapıları tarafından tüketilen işlem belleği hakkındaki bilgileri görüntüler.<br /><br /> **-gc** ve **-yükleyici** seçenekleri, bu komutun çıktısını çöp toplayıcı veya yükleyici veri yapıları ile sınırlar.<br /><br /> Çöp toplayıcıya ilişkin bilgiler, yönetilen yığındaki her bir segmentin aralıklarını listeler.  İşaretçi **-gc**tarafından verilen bir segment aralığına düşerse, işaretçi bir nesne işaretçisidir.|
|**EEStack** [**-kısa**] [**-EE**]|İşlemdeki tüm iş parçacıklarıüzerinde **DumpStack** komutunu çalıştırın.<br /><br /> **-EE** seçeneği doğrudan **DumpStack** komutuna geçirilir. **-kısa** parametre çıktıyı aşağıdaki iş parçacığı türleri ile sınırlar:<br /><br /> Kilit almış olan iş parçacıkları.<br /><br /> Çöp toplamaya olanak tanımak için durdurulmuş iş parçacıkları.<br /><br /> Yönetilen kodda bulunan iş parçacıkları.|
|**EEVersion**|CLR sürümünü görüntüler.|
|**EHInfo** \<[*MethodDesc* adresi\<>] [*Kod adresi*>]|Belirtilen bir yöntemdeki özel durum işleme bloklarını görüntüler.  Bu komut, yan tümce bloğu `try` (blok) ve işleyici bloğu `catch` (blok) için kod adreslerini ve uzaklıkları görüntüler.|
|**SSS**|Sık sorulan soruları görüntüler.|
|**FinalizeQueue** [**-detay**] &#124; [**-allReady**] [**-kısa**]|Sonlandırma için kaydolan tüm nesneleri görüntüler.<br /><br /> **-ayrıntı** seçeneği, temizlenmesi gereken `SyncBlocks` ler ve temizlemeyi bekleyen `RuntimeCallableWrappers` herhangi bir (RCW) hakkında ek bilgi görüntüler. Bu veri yapılarının her ikisi de, çalıştığı zaman sonlandırıcı tarafından ön belleğe kaydedilir.<br /><br /> Seçenek, `-allReady` çöp toplama tarafından zaten bu şekilde işaretlenmiş olup olmadıklarına veya bir sonraki çöp toplama tarafından işaretlenip işaretlenmediğine bakılmaksızın sonlandırmaya hazır olan tüm nesneleri görüntüler. "Sonlandırma için hazır" listesinde olan nesneler, artık köklü olmayan sonlandırılabilir nesnelerdir. Sonlandırılabilir kuyruklarda bulunan tüm nesnelerin hala köklü olduğunu doğruladığından, bu seçenek çok pahalı olabilir.<br /><br /> Seçenek, `-short` çıktıyı her nesnenin adresiyle sınırlar. **-allReady**ile birlikte kullanılırsa, artık köklü olmayan bir sonlandırıcıya sahip tüm nesneleri günceller. Bağımsız olarak kullanılırsa, sonlandırılabilir ve "sonlandırmaya hazır" kuyruklardaki tüm nesneleri listeler.|
|**FindAppDomain** \< *Nesne adresi*>|Belirtilen adresteki bir nesnenin uygulama etki alanını belirler.|
|**FindRoots** **-gen** \< *N*> &#124; \< **-gen herhangi bir** &#124;nesne *adresi*>|Belirtilen oluşturmanın sonraki toplamasında, hata ayıklayıcının hatası ayıklanan öğeyi yarıda kesmesine neden olur. Kesme oluşur oluşmaz, etki sıfırlanır. Sonraki toplamayı kesmek için, komutu tekrar vermeniz gerekir. Bu komutun * \<nesne adresi>* formu, meydana gelen -gen veya **-gen'in** neden olduğu aradan sonra kullanılır. **-gen any** O zaman, hata ayıklama **FindRoots** için geçerli mahkum nesillerden nesnelerin köklerini tanımlamak için doğru durumdadır.|
|**GCHandles** [**-perdomain**]|İşlemdeki çöp toplayıcı tanıtıcılarıyla ilgili istatistikleri görüntüler.<br /><br /> **-perdomain** seçeneği uygulama etki alanına göre istatistikleri düzenler.<br /><br /> Çöp toplayıcı tutamacı sızıntılarının neden olduğu bellek sızıntılarını bulmak için **GCHandles** komutunu kullanın. Örneğin, kesin olarak belirlenmiş bir çöp toplayıcı tanıtıcısı hala onu işaret ettiği için kod büyük bir diziyi tuttuğunda, bir bellek sızıntısı olur ve tanıtıcı onu serbest bırakmadan atılır.|
|**GCHandleLeaks**|Kesin olarak belirlenmiş ve iliştirilmiş çöp toplayıcı tanıtıcılarına yapılan başvurular için bellekte arama yapar ve sonuçları görüntüler. Bir tanıtıcı bulunursa, **GCHandleLeaks** komutu başvurunun adresini görüntüler. Bellekte bir tanıtıcı bulunmazsa, bu komut bir bildirim görüntüler.|
|**GCInfo** \< *MethodDesc adres*>\<*Kodu adresi*>|Kayıt defterlerinin ve yığın konumlarının yönetilen nesneleri ne zaman içerdiğini gösteren verileri görüntüler. Bir çöp toplama olursa, onları yeni nesne işaretçisi değerleriyle güncelleştirebilmesi için, toplayıcı nesnelere yapılan başvuruların konumlarını bilmelidir.|
|**GCRoot** [**-nostacks**] \< *Nesne adresi*>|Belirtilen adresteki bir nesneye yapılan başvurularla (veya köklerle) ilgili bilgi görüntüler.<br /><br /> **GCRoot** komutu, yönetilen yığının tamamını ve yığındaki diğer nesneler ve tutamaçların tutamaçları için tutamaç tablosunu inceler. Sonra, her bir yığında nesne işaretçileri aranır ve sonlandırıcı kuyruğunda da arama yapılır.<br /><br /> Bu komut, bir yığın kökünün geçerli veya atılmış olduğunu belirlemez. Yığın kökün hala kullanımda olup olmadığını belirlemek için yerel veya bağımsız değişken değerinin ait olduğu çerçeveyi sökmek için **CLRStack** ve **U** komutlarını kullanın.<br /><br /> **-nostacks** seçeneği, aramayı çöp toplayıcı tutamaçları ve ulaşılabilir nesnelerle sınırlandırıyor.|
|**GCWhere**  *\<nesne adresi>*|Geçirilen bağımsız değişkenin çöp toplama yığınındaki konumu ve büyüklüğü görüntüler. Bağımsız değişken yönetilen yığında yer aldığında, fakat geçerli bir nesne adresi olmadığında, büyüklük 0 (sıfır) olarak görüntülenir.|
|**yardım** \<[>`faq`*komutu]* [ ]|Parametre belirtilmediğinde kullanılabilir olan tüm komutları görüntüler veya belirli komutla ilgili ayrıntılı yardım bilgilerini görüntüler.<br /><br /> Parametre, `faq` sık sorulan soruların yanıtlarını görüntüler.|
|**HeapStat** [**-inclRooted** &#124; **-iu**]|Her bir yığın için oluşturma büyüklüğünü ve her bir yığındaki her bir oluşturmada bulunan toplam boş alanı görüntüler. -**InclRooted** seçeneği belirtilirse, rapor artık köklü olmayan çöp toplama yığınından yönetilen nesneler hakkında bilgi içerir.|
|**HistClear**|`Hist` Komut ailesi tarafından kullanılan kaynakları serbest bırakır.<br /><br /> Genellikle, her biri `HistClear` `HistInit` önceki kaynakları temizlediği için açıkça aramanız gerekmez.|
|**HistInit**|Hatası ayıklanana kaydedilen yük günlüğünden SOS yapılarını başlatır.|
|**HistObj** * \<obj_address>*|Tüm yük günlüğü yeniden yerleştirme kayıtlarını inceler ve bir bağımsız değişken olarak geçirilen adrese yönlendirebilecek çöp toplama yeniden konumlandırmaları zincirini görüntüler.|
|**HistObjFind**  *\<obj_address>*|Belirtilen adresteki bir nesneye başvuran tüm günlük girişlerini görüntüler.|
|**HistRoot** * \<kök>*|Belirtilen kökün tanıtımlarıyla ve yeniden konumlandırılmalarıyla ilişkili bilgileri görüntüler.<br /><br /> Kök değeri, bir nesnenin çöp toplamalar içindeki hareketini izlemek için kullanılabilir.|
|**IP2MD** \< *Kod adresi*>|`MethodDesc` JIT tarafından derlenmiş kodda yapıyı belirtilen adreste görüntüler.|
|`ListNearObj`(`lno` * \<* ) obj_address>|Belirtilen adresten önceki ve sonraki nesneleri görüntüler. Komut, yönetilen bir nesnenin (geçerli bir yöntem tablosuna dayalı olarak) ve bağımsız değişken adresini izleyen nesnenin geçerli bir başlangıcı gibi görünen çöp toplama yığınında adresi arar.|
|**MinidumpMode** [**0**] [**1**]|Bir mini döküm kullanırken, güvenli olmayan komutların çalışmasını önler.<br /><br /> Bu özelliği devre dışı katlamak için **0'ı** veya bu özelliği etkinleştirmek için **1'i** geçirin. Varsayılan olarak, **MinidumpMode** değeri **0**olarak ayarlanır.<br /><br /> **.dump /m** komutu veya **.dump** komutu ile oluşturulan minidumps clr özgül veri sınırlı ve doğru SOS komutları yalnızca bir alt kümesi çalıştırmak için izin verir. Gerekli bellek alanları eşleşmediğinden veya kısmen eşleştiğinden, bazı komutlar beklenmeyen hatalarla başarısız olabilir. Bu seçenek, mini dökümlere karşı güvenli olmayan komutları çalıştırmaktan sizi korur.|
|**Name2EE** \< *modül adı*> \<*türü veya yöntem adı*><br /><br /> -veya-<br /><br /> **Name2EE** \< *modül adı*>**!** \< *türü veya yöntem adı*>|Belirtilen `MethodTable` modülde `EEClass` belirtilen tür veya yöntemin yapısını ve yapısını görüntüler.<br /><br /> Belirtilen modülün işlemde yüklenmesi gerekir.<br /><br /> Uygun tür adını almak için [Ildasm.exe (IL Desassembler)](ildasm-exe-il-disassembler.md)kullanarak modüle göz atın. Ayrıca, yüklenen `*` tüm yönetilen modülleri aramak için modül adı parametresi olarak da geçebilirsiniz. *Modül adı* parametresi, hata ayıklayıcının adı olabilir, örneğin `mscorlib` `image00400000`.<br /><br /> Bu komut, <`module` > `!` < `type`> Windows hata ayıklama sözdizimini destekler. Tür, tam olarak nitelenmiş olmalıdır.|
|**ObjSize** \<[*Nesne adresi*>] &#124; [**-toplam**] [**-stat**]|Belirtilen nesnenin boyutunu görüntüler. Herhangi bir parametre belirtmezseniz, **ObjSize** komutu yönetilen iş parçacıklarında bulunan tüm nesnelerin boyutunu görüntüler, işlemdeki tüm çöp toplayıcı tutamaçlarını görüntüler ve bu tutamaçların işaret ettiği nesnelerin boyutunu bir araya alır. **ObjSize** komutu, üst öğeye ek olarak tüm alt nesnelerin boyutunu içerir.<br /><br /> **-toplam** seçeneği, hala köklü türlerin ayrıntılı bir görünümünü elde etmek için **-stat** bağımsız değişkeni ile birlikte kullanılabilir. **!dumpheap -stat** ve **!objsize -aggregate -stat**kullanarak, hangi nesnelerin artık köklü olmadığını belirleyebilir ve çeşitli bellek sorunlarını tanılayabilirsiniz.|
|**PrintException** [**-iç içe ]**\<[**-satırlar**] [ Özel Durum nesne*adresi*>]<br /><br /> -veya-<br /><br /> **PE** [**-iç**\<içe ] [*Özel durum nesne adresi*>]|Belirtilen adreste sınıftan türetilen <xref:System.Exception> herhangi bir nesnenin alanlarını görüntüler ve biçimlendirin. Bir adres belirtmezseniz, **PrintException** komutu geçerli iş parçacığına atılan son özel durumu görüntüler.<br /><br /> İç **içe geçme** seçeneği, iç içe olan özel durum nesneleri yle ilgili ayrıntıları görüntüler.<br /><br /> **-lines** seçeneği varsa kaynak bilgileri görüntüler.<br /><br /> İkili bir dizi olan `_stackTrace` alanı biçimlendirmek ve görüntülemek için bu komutu kullanabilirsiniz.|
|**ProcInfo** [**-env**] [**-zaman**] [**-mem**]|İşlem, çekirdek CPU süresi ve bellek kullanımı istatistikleri için ortam değişkenlerini görüntüler.|
|**RCWCleanupList** \< *RCWCleanupList adresi*>|Belirtilen adreste temizlenmeyi bekleyen çalışma zamanı çağrılabilir sarmalayıcılarının listesini görüntüler.|
|**SaveModule** \< *Temel adresi*> \<*Dosya Adı*>|Belirtilen adreste belleğe yüklenen bir görüntüyü belirtilen dosyaya yazar.|
|**SOSFlush**|Bir iç SOS önbelleğini temizler.|
|**StopOnException** [**-türetilmiş**] [ \<**-create** &#124; **-create2**] *Özel Durum*> \<*Pseudo-register numarası*>|Belirtilen özel durum oluştuğunda hata ayıklayıcının durmasına, fakat diğer özel durumlar oluştuğunda çalışmaya devam etmesine neden olur.<br /><br /> **Türetilen** seçenek, belirtilen özel durumu ve belirtilen özel durumdan türeyen her özel durumu yakalar.|
|**SyncBlk** [**-tüm** &#124; \< *>]*|Belirtilen `SyncBlock` yapıyı veya `SyncBlock` tüm yapıları görüntüler.  Herhangi bir bağımsız değişkeni geçemezseniz, **Eşitleme Blk** komutu bir iş parçacığının sahip olduğu nesnelere karşılık gelen `SyncBlock` yapıyı görüntüler.<br /><br /> Yapı, `SyncBlock` her nesne için oluşturulması gerekmeyen ek bilgi için bir kapsayıcıdır. COM birlikte çalışabilirlik verilerini, karma kodları ve güvenli iş parçacığı işlemlerine ilişkin kilitleme bilgilerini tutabilir.|
|**Threadpool**|Kuyruktaki iş isteklerinin sayısı, derleme bağlantı noktası iş parçacıklarının sayısı ve zamanlayıcıların sayısı dahil, yönetilen iş parçacığı havuzuyla ilgili bilgileri görüntüler.|
|**Token2EE** \< *modül adı*> \<*belirteci*>|Belirtilen modülde belirtilen meta veri belirteci `MethodTable` `MethodDesc` bir yapı veya yapı ya da döner.<br /><br /> Modül adı `*` parametresini geçerken, bu belirteç eşlemlerin her yüklenen yönetilen modülde ne anlama geldiğini bulabilirsiniz. Hata ayıklayıcının adını da bir modül için geçirebilirsiniz. `mscorlib` `image00400000`|
|**Konuları** [**-live**] [**-özel**]|İşlemdeki tüm yönetilen iş parçacıklarını görüntüler.<br /><br /> **Threads** komutu hata ayıklayıcı steno kimliği, CLR iş parçacığı kimliği ve işletim sistemi iş parçacığı kimliğini görüntüler.  Ayrıca, **İş Parçacıkları** komutu, iş parçacığının yürütüldettiği uygulama etki alanını, COM apartman modunu görüntüleyen bir APT sütununu ve iş parçacığına atılan son özel durumu görüntüleyen bir Özel Durum sütununu gösteren bir Etki Alanı sütunu görüntüler.<br /><br /> **-live** seçeneği, canlı iş parçacığıyla ilişkili iş parçacıklarını görüntüler.<br /><br /> **-özel** seçenek CLR tarafından oluşturulan tüm özel konuları görüntüler. Özel iş parçacıkları çöp toplama iş parçacığı (eşzamanlı ve sunucu çöp toplama), hata ayıklayıcı <xref:System.AppDomain> yardımcı iş parçacıkları, sonlandırıcı iş parçacıkları, boşaltma iş parçacıkları ve iş parçacığı havuzu zamanlayıcı iş parçacığı içerir.|
|**ThreadState \< ** *State değer alanı***>**|Bir iş parçacığının durumunu görüntüler. Parametre, **İş Parçacıkları** `State` rapor çıktısındaki alanın değeridir. `value`<br /><br /> Örnek:<br /><br /> `0:003> !Threads     ThreadCount:      2     UnstartedThread:  0     BackgroundThread: 1     PendingThread:    0     DeadThread:       0     Hosted Runtime:   no                                           PreEmptive   GC Alloc           Lock            ID OSID ThreadOBJ    State     GC       Context       Domain   Count APT Exception        0    1  250 0019b068      a020 Disabled 02349668:02349fe8 0015def0     0 MTA        2    2  944 001a6020      b220 Enabled  00000000:00000000 0015def0     0 MTA (Finalizer)     0:003> !ThreadState b220         Legal to Join         Background         CLR Owns         CoInitialized         In Multi Threaded Apartment`|
|**TraverseHeap** [**-xml**] \< *dosya adı*>|Yığın bilgilerini, CLR profil oluşturucusunun anlayacağı bir biçimde belirtilen dosyaya yazar. **-xml** **seçeneği, TraverseHeap** komutunun dosyayı XML olarak biçimlendirmesine neden olur.<br /><br /> CLR Profiler'ı Microsoft [Download Center'dan](https://go.microsoft.com/fwlink/?LinkID=67325)indirebilirsiniz.|
|**U** [**-gcinfo**] [**-ehinfo**] [**-n**] \< *MethodDesc adresi*> &#124; \<Kod *adresi*>|Yöntem için bir `MethodDesc` yapı işaretçisi veya yöntem gövdesi içindeki bir kod adresi tarafından belirtilen yönetilen yöntemin açıklamalı bir şekilde disassemblyini görüntüler. **U** komutu, meta veri belirteçlerini adlara dönüştüren ek açıklamalarla tüm yöntemi baştan sona görüntüler.<br /><br /> **-gcinfo** seçeneği, **Yöntemin** yapısını `GCInfo` görüntülemek için U komutuna neden olur.<br /><br /> **-ehinfo** seçeneği yöntem için özel durum bilgilerini görüntüler. Bu bilgileri **EHInfo** komutu yla da edinebilirsiniz.<br /><br /> **-n** seçeneği kaynak dosya adlarının ve satır numaralarının görüntülenmesini devre dışı kılabilir. Hata ayıklayıcı için SYMOPT_LOAD_LINES seçeneği belirtildiyse, SOS yönetilen her çerçeve için simgelere bakar ve başarılı olursa, ilgili dosya adını ve satır numarasını görüntüler. Bu davranışı devre dışı kalmak için **-n** seçeneğini belirtebilirsiniz.|
|**DoğrulamaHeap**|Bozulma işaretleri için çöp toplayıcı yığınını kontrol eder ve bulunan hataları görüntüler.<br /><br /> Yığın bozulmalarına, hatalı oluşturulan platform çağrıları neden olabilir.|
|**VerifyObj** \< *nesne adresi*>|Bir bağımsız değişken olarak geçirilen nesnede bozulma işaretleri olup olmadığını kontrol eder.|
|**VMMap**|Sanal adres alanını bir uçtan diğerine dolaşır ve her bir bölgeye uygulanan koruma türünü görüntüler.|
|**VMStat**|Sanal adres alanının bir özet görünümü, o belleğe (serbest, ayrılmış, adanmış, özel, eşlenmiş, görüntü) uygulanan her bir koruma türüne göre düzenlenmiş olarak sağlar. TOPLAM sütunu, ORTALAMA sütununun sonucunu BLK SAYIMI sütunuyla çarpılmış olarak görüntüler.|

## <a name="remarks"></a>Açıklamalar

SOS Hata Ayıklama Uzantısı, CLR içinde çalışan kod hakkındaki bilgileri görüntülemenizi sağlar. Örneğin, yönetilen yığınla ilgili bilgileri görüntülemek, yığın bozulmalarını aramak, çalışma zamanı tarafından kullanılan iç veri türlerini görüntülemek ve çalışma zamanı içinde çalışan tüm yönetilen kodla ilgili bilgileri görüntülemek için SOS Hata Ayıklama Uzantısı'nı kullanabilirsiniz.

Visual Studio'daki SOS Hata Ayıklama Uzantısı'nı kullanmak için [Windows Sürücü Kiti'ni (WDK)](/windows-hardware/drivers/download-the-wdk)yükleyin. Visual Studio'daki tümleşik hata ayıklama ortamı hakkında bilgi için Hata [Ayıklama Ortamları](/windows-hardware/drivers/debugger/debuggers-in-the-debugging-tools-for-windows-package)bölümüne bakın.

Ayrıca [WinDbg.exe hata ayıklama](/windows-hardware/drivers/debugger/debugger-download-tools) içine yükleyerek ve WinDbg.exe içinde komutları yürüterek SOS Hata Ayıklama Uzantısı kullanabilirsiniz.

SOS Hata Ayıklama Uzantısı'nı WinDbg.exe hata ayıklayıcısına yüklemek için, aşağıdaki komutu araçta çalıştırın:

```console
.loadby sos clr
```

WinDbg.exe ve Visual Studio, kullanımda olan Mscorwks.dll'ye karşılık gelen SOS.dll'nin bir sürümünü kullanır. Varsayılan olarak, Mscorwks.dll'nin geçerli sürümüyle eşleşen SOS.dll sürümünü kullanmanız gerekir.

Başka bir bilgisayarda oluşturulan bir döküm dosyasını kullanmak için, yüklemeyle birlikte gelen Mscorwks.dll dosyasının simge yolunuzda olduğundan emin olun ve ilgili SOS.dll sürümünü yükleyin.

SOS.dll'nin özel bir sürümünü yüklemek için, aşağıdaki komutu Windows Hata Ayıklayıcı'ya yazın:

```console
.load <full path to sos.dll>
```

## <a name="examples"></a>Örnekler

Aşağıdaki komut, adresteki `00ad28d0`bir dizinin içeriğini görüntüler.  Görüntü ikinci öğeden başlar ve beş öğe boyunca devam eder.

```console
!dumparray -start 2 -length 5 -detail 00ad28d0
```

Aşağıdaki komut, adreste `1ca248`bir derlemenin içeriğini görüntüler.

```console
!dumpassembly 1ca248
```

Aşağıdaki komut, çöp toplayıcı yığınıyla ilgili bilgileri görüntüler.

```console
!dumpheap
```

Aşağıdaki komut, bellek içi yük günlüğünün içeriğini, geçerli dizindeki StressLog.txt adlı bir dosyaya (varsayılan) yazar.

```console
!DumpLog
```

Aşağıdaki komut adresteki `MethodDesc` `902f40`yapıyı görüntüler.

```console
!dumpmd 902f40
```

Aşağıdaki komut, adreste `1caa50`bir modül le ilgili bilgileri görüntüler.

```console
!dumpmodule 1caa50
```

Aşağıdaki komut, adresteki `a79d40`bir nesne yle ilgili bilgileri görüntüler.

```console
!DumpObj a79d40
```

Aşağıdaki komut, adresteki `00a79d9c` `0090320c`yöntem tablosunu kullanarak adresteki bir değer sınıfının alanlarını görüntüler.

```console
!DumpVC 0090320c 00a79d9c
```

Aşağıdaki komut, çöp toplayıcı tarafından kullanılan işlem belleğini görüntüler.

```console
!eeheap -gc
```

Aşağıdaki komut, sonlandırma için zamanlanan tüm nesneleri görüntüler.

```console
!finalizequeue
```

Aşağıdaki komut, adresteki `00a79d98`bir nesnenin uygulama etki alanını belirler.

```console
!findappdomain 00a79d98
```

Aşağıdaki komut, geçerli işlemdeki tüm çöp toplayıcı tanıtıcılarını görüntüler.

```console
!gcinfo 5b68dbb8
```

Aşağıdaki komut, `MethodTable` modüldeki `EEClass` `unittest.exe`sınıftaki `Main` `MainClass` yöntemin ve yapılarını görüntüler.

```console
!name2ee unittest.exe MainClass.Main
```

Aşağıdaki komut, modüldeki `02000003` `unittest.exe`adreste meta veri belirteci yle ilgili bilgileri görüntüler.

```console
!token2ee unittest.exe 02000003
```

## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [Komut İstemleri](developer-command-prompt-for-vs.md)
