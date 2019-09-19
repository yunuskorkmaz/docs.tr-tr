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
ms.openlocfilehash: 9a8d41228c46de0f18b5a92def0591d6373d3d69
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044092"
---
# <a name="sosdll-sos-debugging-extension"></a>SOS. dll (SOS hata ayıklama uzantısı)

SOS hata ayıklama uzantısı (SOS. dll), iç ortak dil çalışma zamanı (CLR) ortamı hakkında bilgi sağlayarak Visual Studio 'da ve Windows hata ayıklayıcısında (WinDbg. exe) yönetilen programlarda hata ayıklamanıza yardımcı olur. Bu araç, projenizde yönetilmeyen hata ayıklamanın etkin olmasını gerektirir. SOS.dll, .NET Framework ile birlikte otomatik olarak yüklenir. SOS. dll dosyasını Visual Studio 'da kullanmak için, [Windows Sürücü Seti 'ni (WDK)](/windows-hardware/drivers/download-the-wdk)yükler.

## <a name="syntax"></a>Sözdizimi

```console
![command] [options]
```

## <a name="commands"></a>Komutlar

|Komut|Açıklama|
|-------------|-----------------|
|**Analiz Zeoom** (**Ao**)|Çöp toplama yığınına yönelik bir ayırma isteğinde gerçekleşen son bellek (OOM) bilgilerini görüntüler. (Sunucu çöpü toplamada, her bir çöp toplama yığınında varsa OOM görüntüler.)|
|**Bpmd** [ **-nofuturemodule**] [\< <*Modül adı* \< Yöntem adı >] [-md`MethodDesc`>]-liste-bekleyen kesme noktası numarasını Temizle> \< >  **-ClearAll**|Belirtilen modül içinde belirtilen yöntemde bir kesme noktası oluşturur.<br /><br /> Belirtilen modül ve yöntem yüklenmediyse, bu komut, modülün yüklendiğine ve bir kesme noktası oluşturmadan önce tam zamanında (JIT) derlediğine ilişkin bir bildirim bekler.<br /><br /> Bekleyen kesme noktalarının listesini **-list**, **-clear**ve **-ClearAll** seçeneklerini kullanarak yönetebilirsiniz:<br /><br /> **-List** seçeneği, tüm bekleyen kesme noktalarının bir listesini oluşturur. Bir bekleyen kesme noktasının sıfır olmayan bir modül kimliği varsa, o kesme noktası o belirli modüldeki bir işleve özeldir. Bekleyen kesme noktasının modül kimliği sıfırsa, o kesme noktası henüz yüklenmeyen modüller için geçerli olur.<br /><br /> Bekleyen kesme noktalarını listeden kaldırmak için **-clear** veya **-ClearAll** seçeneğini kullanın.|
|**CLRStack** [ **-a**] [ **-l**] [ **-p**] [ **- n**]|Yalnızca bir yönetilen kodların bir yığın izlemesini sağlar.<br /><br /> **-P** seçeneği, yönetilen işlevin bağımsız değişkenlerini gösterir.<br /><br /> **-L** seçeneği bir çerçevedeki yerel değişkenlerle ilgili bilgileri gösterir. SOS hata ayıklama uzantısı yerel adları alamıyor, bu nedenle yerel \<adların çıktısı yerel *Adres* >  **=** \< *değeri*> biçimindedir.<br /><br /> **-A**(Tümü) seçeneği için bir kısayoldur **-l** ve **-p** birleştirilmiş.<br /><br /> **-N** seçeneği, kaynak dosya adları ve satır numaralarının görüntüsünü devre dışı bırakır. Hata ayıklayıcı için SYMOPT_LOAD_LINES seçeneği belirtildiyse, SOS yönetilen her çerçeve için simgelere bakar ve başarılı olursa, ilgili dosya adını ve satır numarasını görüntüler. Bu davranışı devre dışı bırakmak için **-n** (satır numarası yok) parametresi belirtilebilir.<br /><br /> SOS Hata Ayıklama Uzantısı, x64 ve IA-64 tabanlı platformlarda geçiş çerçevelerini görüntülemez.|
|**COMState**|Her iş parçacığı için com grubu modelini ve `Context` varsa işaretçiyi listeler.|
|**DumpArray** [ **-başlangıç** \< *startIndex*>] [ **-uzunluk** \<*uzunluğu*>] [ **-Ayrıntılar**] [ **- nofields**] \<*dizi nesnesi adresi*><br /><br /> -veya-<br /><br /> **Da** [ **-Start** \< *startIndex*>] [ **-length** \< *uzunluğu*>] [ **-detail**] [ **-nofields**] *dizi nesne adresi*>|Bir dizi nesnesinin öğelerini inceler.<br /><br /> **-Start** seçeneği, öğelerin görüntüleneceği başlangıç dizinini belirtir.<br /><br /> **-Length** seçeneği, kaç öğe gösterileceğini belirtir.<br /><br /> **-Details** seçeneği, **DumpObj** ve **DumpVC** biçimlerini kullanarak öğesinin ayrıntılarını görüntüler.<br /><br /> **-Nofields** seçeneği, dizilerin görüntülenmesini önler. Bu seçenek yalnızca **-detail** seçeneği belirtildiğinde kullanılabilir.|
|**DumpAssembly** \< *derleme adresi*>|Bir derlemeyle ilgili bilgileri görüntüler.<br /><br /> **DumpAssembly** komutunda, varsa, birden çok modül listelenir.<br /><br /> Bir bütünleştirilmiş kod adresini **DumpDomain** komutunu kullanarak alabilirsiniz.|
|**DumpClass** *EEClass adresi* \<>|Bir türle ilişkili `EEClass` yapı hakkındaki bilgileri görüntüler.<br /><br /> **DumpClass** komutu statik alan değerlerini görüntüler, ancak statik olmayan alan değerlerini görüntülemez.<br /><br /> Bir Yapı`EEClass` adresi almak için dumpmt, **DumpObj**, Name2EE veya Token2EE komutunu kullanın.|
|**DumpDomain** [\<*etki alanı adresi*>]|<xref:System.Reflection.Assembly> Belirtilen<xref:System.AppDomain> nesne adresi içinde yüklenen her nesneyi numaralandırır.  Parametresiz çağrıldığında, **DumpDomain** komutu bir işlemdeki tüm <xref:System.AppDomain> nesneleri listeler.|
|**Dumpheap** [ **-stat**] [ **-dizeler**] [ **-Short**] [ **-Min** \< *Boyut*>] [ **-Max** \< *size*>] [ **-ölçülü kilit**] [ **-startatic sınır**] [ **-MT** \< *MethodTable Address*>] [ **-Type Kısmi tür** *adı*>] [*Başlangıç* [*End]]* \<|Toplanan çöp yığınıyla ilgili bilgileri ve nesnelerle ilgili toplama istatistiklerini görüntüler.<br /><br /> Çöp toplayıcı yığınında aşırı parçalanma algılarsa, **dumpheap** komutu bir uyarı görüntüler.<br /><br /> **-Stat** seçeneği, çıktıyı istatistiksel tür özetine kısıtlar.<br /><br /> **-Strings** seçeneği, çıktıyı istatistiksel bir dize değeri özetine kısıtlar.<br /><br /> **-Short** seçeneği çıktıyı yalnızca her nesnenin adresine sınırlandırır. Bu, otomasyon için komuttan başka bir hata ayıklayıcı komutuna kolayca çıktı yönlendirmenize olanak sağlar.<br /><br /> **-Min** seçeneği, `size` parametresinden daha küçük olan ve bayt cinsinden belirtilen nesneleri yoksayar.<br /><br /> **-Max** seçeneği, bayt olarak belirtilen `size` parametresinden daha büyük nesneleri yoksayar.<br /><br /> **-Ölçülü kilit** seçeneği, ölçülü kilitleri raporlar.  Daha fazla bilgi için bkz. **SyncBlk** komutu.<br /><br /> Seçeneği `-startAtLowerBound` , belirtilen bir adres aralığının alt sınırından başlayarak yığını başlamaya zorlar. Planlama aşamasında, nesneler taşınmakta olduğundan, yığın genellikle yürünebilir değildir. Bu seçenek, **dumpheap** 'ın belirtilen alt sınır üzerinden ilerlemesini başlatmaya zorlar. Bu seçeneğin çalışması alt sınır olarak geçerli bir nesne adresi sağlamanız gerekir. Sonraki yöntem tablosunu el ile bulmak için, bozuk bir nesnenin adresindeki belleği görüntüleyebilirsiniz. Çöp toplama şu anda öğesine yapılan `memcopy`bir çağrıdır, bir parametre olarak sağlanan başlangıç adresine boyutunu ekleyerek sonraki nesnenin adresini de bulabilirsiniz.<br /><br /> **-MT** seçeneği yalnızca belirtilen `MethodTable` yapıya karşılık gelen nesneleri listeler.<br /><br /> **-Type** seçeneği, yalnızca tür adı belirtilen dize ile bir alt dize eşleşmesi olan nesneleri listeler.<br /><br /> Parametre `start` , belirtilen adresten listelemeye başlar.<br /><br /> `end` Parametre belirtilen adreste listeyi durduruyor.|
|**Dumpıl** &#124; \< *Dynamicmethoddesc işaretçisi*> &#124; *işaretçisine* > *yönetilen DynamicMethod nesnesi* \< \<               >|Yönetilen bir yöntemle ilişkili Microsoft ara dilini (MSIL) görüntüler.<br /><br /> Dinamik MSIL'in bir derlemeden yüklenen MSIL'den farklı şekilde yayıldığını unutmayın. Dinamik MSIL, meta veri belirteçleri yerine, bir yönetilen nesne dizisindeki nesnelere başvurur.|
|**Dumplog** [ **-addr** \< *adresisofstresslog*>] [<*filenam*`e`>]|Bir bellek içi yük günlüğünün içeriğini belirtilen dosyaya yazar. Bir ad belirtmezseniz, bu komut geçerli dizinde StressLog.txt adlı bir dosya oluşturur.<br /><br /> Bellek içi yük güvenliği, kilitler veya G/Ç kullanmadan yük hatalarını tanılamanıza yardımcı olur. Stres günlüğünü etkinleştirmek için, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\altında aşağıdaki kayıt defteri anahtarlarını ayarlayın. NETFramework<br /><br /> (DWORD) StressLog = 1<br /><br /> (DWORD) LogFacility = 0xffffffff<br /><br /> (DWORD) StressLogSize = 65536<br /><br /> İsteğe bağlı `-addr` seçeneği, varsayılan günlüğün dışında bir stres günlüğü belirtmenize olanak tanır.|
|**Dumpmd** *MethodDesc adresi* \<>|Belirtilen adresteki bir `MethodDesc` yapıyla ilgili bilgileri görüntüler.<br /><br /> Yönetilen bir işlevden `MethodDesc` yapı adresini almak için **IP2MD** komutunu kullanabilirsiniz.|
|**Dumpmt** [ **-Md**] *MethodTable adresi* \<>|Belirtilen bir adresteki bir yöntem tablosuyla ilgili bilgileri görüntüler. **-Md** seçeneğini belirtmek nesneyle tanımlanan tüm yöntemlerin bir listesini görüntüler.<br /><br /> Her bir yönetilen nesne bir yöntem tablosu işaretçisi içerir.|
|**Dumpmethodsig** sigaddr > <*moduleadd* \<`r`>|Belirtilen adresteki bir `MethodSig` yapıyla ilgili bilgileri görüntüler.|
|**Dumpmodule** [ **-MT**] \< *Modül adresi*>|Belirtilen adresteki bir modülle ilgili bilgileri görüntüler. **-MT** seçeneği, modülde tanımlanan türleri ve modülün başvurduğu türleri görüntüler<br /><br /> Bir modülün adresini almak için **DumpDomain** veya **DumpAssembly** komutunu kullanabilirsiniz.|
|**DumpObj** [ **-nofields**] \< *nesne adresi*><br /><br /> -veya-<br /><br /> **YAPMAK** \<*nesne adresi*>|Belirtilen adresteki bir nesneyle ilgili bilgileri görüntüler. **DumpObj** komutu alanları, `EEClass` yapı bilgilerini, yöntem tablosunu ve nesnenin boyutunu görüntüler.<br /><br /> Bir nesnenin adresini almak için **DumpStackObjects** komutunu kullanabilirsiniz.<br /><br /> Aynı zamanda nesneler olduklarından, **DumpObj** komutunu türü `CLASS` alanlarda çalıştırabileceğinizi unutmayın.<br /><br /> Nofields seçeneği, nesne alanlarının görüntülenmesini önler, dize gibi nesneler için yararlıdır. `-`|
|**DumpRuntimeTypes**|Çöp toplayıcı yığınındaki çalışma zamanı türü nesneleri görüntüler ve ilişkili tür adlarını ve yöntem tablolarını listeler.|
|**DumpStack** [ **-Ee**] [ **-n**] [`top` *Stack* [`bottom`yığ]`k`]|Bir yığın izleme görüntüler.<br /><br /> **-Ee** seçeneği, **DumpStack** komutunun yalnızca yönetilen işlevleri görüntülemesine neden olur. X86 platformlarında görüntülenecek `bottom` yığın çerçevelerini sınırlamak için veparametrelerinikullanın.`top`<br /><br /> **-N** seçeneği, kaynak dosya adları ve satır numaralarının görüntüsünü devre dışı bırakır. Hata ayıklayıcı için SYMOPT_LOAD_LINES seçeneği belirtildiyse, SOS yönetilen her çerçeve için simgelere bakar ve başarılı olursa, ilgili dosya adını ve satır numarasını görüntüler. Bu davranışı devre dışı bırakmak için **-n** (satır numarası yok) parametresi belirtilebilir.<br /><br /> X86 ve x64 platformlarında, **DumpStack** komutu ayrıntılı yığın izleme oluşturur.<br /><br /> IA-64 tabanlı platformlarda, **DumpStack** komutu hata ayıklayıcının **K** komutunu taklit eder. `top` Ve`bottom` parametreleri, IA-64 tabanlı platformlarda yok sayılır.|
|**Dumpsıg** \<sigaddr>  moduleaddr\<>|Belirtilen adresteki bir `Sig` yapıyla ilgili bilgileri görüntüler.|
|**Dumpsıgelem** \<sigaddr>  moduleaddr\<>|Bir imza nesnesinin tek bir öğesini görüntüler. Çoğu durumda, tek tek imza nesnelerine bakmak için **Dumpsıg** kullanmanız gerekir. Ancak, bir imza bir şekilde bozuksa, onun geçerli bölümlerini okumak için **Dumpsıgelem** kullanabilirsiniz.|
|**DumpStackObjects** [ **-Doğrula**] [`top` *Stack* [`bottom` *Stack*]]<br /><br /> -veya-<br /><br /> **DSO** [ **-Doğrula**] [`top` *Stack* [`bottom` *Stack*]]|Geçerli yığının sınırları içinde bulunan tüm yönetilen nesneleri görüntüler.<br /><br /> **-Verify** seçeneği bir nesne alanının statik `CLASS` olmayan her alanını doğrular.<br /><br /> Yerel değişkenlerin ve parametrelerin değerlerini belirlemek için, **K** komutu ve **CLRStack** komutu gibi yığın Izleme komutlarıyla **dumpstackobject** komutunu kullanın.|
|**DumpVC** *MethodTable adres*> adresi\< \<>|Belirtilen adresteki bir değer sınıfının alanlarıyla ilgili bilgileri görüntüler.<br /><br /> **MethodTable** parametresi, **DumpVC** komutunun alanları doğru yorumlaması için izin verir. Değer sınıfları, ilk alanları olarak bir yöntem tablosuna sahip değildir.|
|**Eeheap** [ **-GC**] [ **-Loader**]|İç CLR veri yapıları tarafından tüketilen işlem belleği hakkındaki bilgileri görüntüler.<br /><br /> **-GC** ve **-Loader** seçenekleri, bu komutun çıkışını çöp toplayıcısı veya yükleyici veri yapıları ile sınırlar.<br /><br /> Çöp toplayıcıya ilişkin bilgiler, yönetilen yığındaki her bir segmentin aralıklarını listeler.  İşaretçi **-GC**tarafından verilen bir kesim aralığı içinde kalırsa, işaretçi bir nesne işaretçisidir.|
|**Eestack** [ **-Short**] [ **-Ee**]|İşlemdeki tüm iş parçacıklarında **DumpStack** komutunu çalıştırır.<br /><br /> **-Ee** seçeneği doğrudan **DumpStack** komutuna geçirilir. **-Short** parametresi, çıktıyı aşağıdaki iş parçacığı türleriyle sınırlar:<br /><br /> Kilit almış olan iş parçacıkları.<br /><br /> Çöp toplamaya olanak tanımak için durdurulmuş iş parçacıkları.<br /><br /> Yönetilen kodda bulunan iş parçacıkları.|
|**EEVersion**|CLR sürümünü görüntüler.|
|**EHInfo** [\<*MethodDesc adres*>] [\<*kod adresi*>]|Belirtilen bir yöntemdeki özel durum işleme bloklarını görüntüler.  Bu komut, yan tümce bloğunun ( `try` blok) ve işleyici bloğunun `catch` (blok) kod adreslerini ve uzaklıklarını görüntüler.|
|**SSS**|Sık sorulan soruları görüntüler.|
|**Finalizequeue** [ **-detail**] &#124; [ **-allready**] [ **-Short**]|Sonlandırma için kaydolan tüm nesneleri görüntüler.<br /><br /> **-Detail** seçeneği, temizlenmesi gereken her türlü `SyncBlocks` ve temizleme işlemini `RuntimeCallableWrappers` bekleen (RCWs) hakkında ek bilgiler görüntüler. Bu veri yapılarının her ikisi de, çalıştığı zaman sonlandırıcı tarafından ön belleğe kaydedilir.<br /><br /> Bu `-allReady` seçenek, atık toplama tarafından zaten işaretlenmiş olup olmadıklarına bakılmaksızın veya sonraki atık toplama tarafından işaretlenmeksizin, sonlandırmaya hazırlanma tüm nesneleri görüntüler. "Sonlandırma için hazır" listesinde olan nesneler, artık köklü olmayan sonlandırılabilir nesnelerdir. Sonlandırılabilir kuyruklarda bulunan tüm nesnelerin hala köklü olduğunu doğruladığından, bu seçenek çok pahalı olabilir.<br /><br /> `-short` Seçeneği, çıktıyı her nesnenin adresine sınırlandırır. **-Allready**ile birlikte kullanılırsa, artık kök olmayan bir sonlandırıcısı olan tüm nesneleri numaralandırır. Bağımsız olarak kullanılırsa, sonlandırılabilir ve "sonlandırmaya hazır" kuyruklardaki tüm nesneleri listeler.|
|**Findappdomain** \< *Nesne adresi*>|Belirtilen adresteki bir nesnenin uygulama etki alanını belirler.|
|**Findroots** **-Gen** &#124; &#124; *N >* **-Tüm** *nesne adreslerini* genel olarak \< \<>|Belirtilen oluşturmanın sonraki toplamasında, hata ayıklayıcının hatası ayıklanan öğeyi yarıda kesmesine neden olur. Kesme oluşur oluşmaz, etki sıfırlanır. Sonraki toplamayı kesmek için, komutu tekrar vermeniz gerekir. Bu komutun  *nesneadresi>formu,-genveya-genany'ninnedenolduğukesme\<* oluşturulduktan sonra kullanılır. Bu sırada, hata ayıklanan, geçerli Condemned nesiller içindeki nesnelerin köklerini belirlemek için **Findroots** 'nin doğru durumundadır.|
|**GCHandles** [ **-perdomain**]|İşlemdeki çöp toplayıcı tanıtıcılarıyla ilgili istatistikleri görüntüler.<br /><br /> **-Perdomain** seçeneği istatistikleri uygulama etki alanına göre düzenler.<br /><br /> Çöp toplayıcı tanıtıcı sızıntılarının neden olduğu bellek sızıntılarını bulmak için **GCHandles** komutunu kullanın. Örneğin, kesin olarak belirlenmiş bir çöp toplayıcı tanıtıcısı hala onu işaret ettiği için kod büyük bir diziyi tuttuğunda, bir bellek sızıntısı olur ve tanıtıcı onu serbest bırakmadan atılır.|
|**Gchandlet sızıntıları**|Kesin olarak belirlenmiş ve iliştirilmiş çöp toplayıcı tanıtıcılarına yapılan başvurular için bellekte arama yapar ve sonuçları görüntüler. Bir tanıtıcı bulunursa, **Gchandlesızıntı** komutu başvurunun adresini görüntüler. Bellekte bir tanıtıcı bulunmazsa, bu komut bir bildirim görüntüler.|
|**GCInfo** *MethodDesc*Adres>kodu\<adresi \<>|Kayıt defterlerinin ve yığın konumlarının yönetilen nesneleri ne zaman içerdiğini gösteren verileri görüntüler. Bir çöp toplama olursa, onları yeni nesne işaretçisi değerleriyle güncelleştirebilmesi için, toplayıcı nesnelere yapılan başvuruların konumlarını bilmelidir.|
|**Gcroot** [ **-noyığınlar**] \< *Nesne adresi*>|Belirtilen adresteki bir nesneye yapılan başvurularla (veya köklerle) ilgili bilgi görüntüler.<br /><br /> **Gcroot** komutu yönetilen yığının tamamını ve diğer nesneler içindeki tutamaçlar için tanıtıcı tablosunu ve yığındaki tutamaçları inceler. Sonra, her bir yığında nesne işaretçileri aranır ve sonlandırıcı kuyruğunda da arama yapılır.<br /><br /> Bu komut, bir yığın kökünün geçerli veya atılmış olduğunu belirlemez. Yığın kökünün hala kullanımda olup olmadığını anlamak için, yerel veya bağımsız değişken değerinin ait olduğu çerçeveyi ayırabilmek için **CLRStack** ve **U** komutlarını kullanın.<br /><br /> **-Noyığınlar** seçeneği, aramayı çöp toplayıcı tanıtıcıları ve erişilebilir nesneler olarak kısıtlar.|
|**GCWhere**  *\<nesnesi adresi>*|Geçirilen bağımsız değişkenin çöp toplama yığınındaki konumu ve büyüklüğü görüntüler. Bağımsız değişken yönetilen yığında yer aldığında, fakat geçerli bir nesne adresi olmadığında, büyüklük 0 (sıfır) olarak görüntülenir.|
|**Yardım** [\<*komut*>] [`faq`]|Parametre belirtilmediğinde kullanılabilir olan tüm komutları görüntüler veya belirli komutla ilgili ayrıntılı yardım bilgilerini görüntüler.<br /><br /> Parametresi `faq` , sık sorulan soruların yanıtlarını görüntüler.|
|**Heapstat** [ **-ınlunkökü belirtilmiş** &#124; **-IU**]|Her bir yığın için oluşturma büyüklüğünü ve her bir yığındaki her bir oluşturmada bulunan toplam boş alanı görüntüler. -**Inclunkökü** belirtilmiş seçeneği belirtilmişse rapor, artık kök olmayan atık toplama yığınından yönetilen nesneler hakkında bilgi içerir.|
|**Temizlediğinden**|`Hist` Komut ailesi tarafından kullanılan tüm kaynakları serbest bırakır.<br /><br /> Genellikle, her biri `HistClear` `HistInit` önceki kaynakları temizlediğinde, açıkça çağırmanız gerekmez.|
|**Histınit**|Hatası ayıklanana kaydedilen yük günlüğünden SOS yapılarını başlatır.|
|**HistObj**  *obj_address\<>*|Tüm yük günlüğü yeniden yerleştirme kayıtlarını inceler ve bir bağımsız değişken olarak geçirilen adrese yönlendirebilecek çöp toplama yeniden konumlandırmaları zincirini görüntüler.|
|*HistObjFind\<obj_address >*|Belirtilen adresteki bir nesneye başvuran tüm günlük girişlerini görüntüler.|
|**Histroot**  *kök\<>*|Belirtilen kökün tanıtımlarıyla ve yeniden konumlandırılmalarıyla ilişkili bilgileri görüntüler.<br /><br /> Kök değeri, bir nesnenin çöp toplamalar içindeki hareketini izlemek için kullanılabilir.|
|**IP2MD** \< *Kod adresi*>|JIT ile derlenen kodda belirtilen adresteki yapıyıgörüntüler.`MethodDesc`|
|`ListNearObj`(`lno` *) obj_address\<>*|Belirtilen adresten önceki ve sonraki nesneleri görüntüler. Komut, yönetilen bir nesnenin (geçerli bir yöntem tablosuna dayalı olarak) ve bağımsız değişken adresini izleyen nesnenin geçerli bir başlangıcı gibi görünen çöp toplama yığınında adresi arar.|
|**MinidumpMode** [**0**] [**1**]|Bir mini döküm kullanırken, güvenli olmayan komutların çalışmasını önler.<br /><br /> Bu özelliği etkinleştirmek için **0** geçirin veya **1 ' i** devre dışı bırakın. Varsayılan olarak, **MinidumpMode** değeri **0**olarak ayarlanır.<br /><br /> **. Dump/m** komutu veya **. dump** komutuyla oluşturulan mini dökümler, clr 'ye özgü sınırlı verilere sahıptır ve yalnızca bir sos komutlarının alt kümesini çalıştırmanızı sağlar. Gerekli bellek alanları eşleşmediğinden veya kısmen eşleştiğinden, bazı komutlar beklenmeyen hatalarla başarısız olabilir. Bu seçenek, mini dökümlere karşı güvenli olmayan komutları çalıştırmaktan sizi korur.|
|**Name2EE** \< *Modül*adıtürü> veya*Yöntem* adı\<><br /><br /> -veya-<br /><br /> **Name2EE** Modül adı **!** \<> *tür veya yöntem adı* \<>|Belirtilen modüldeki belirtilen tür `EEClass` veya metodun yapısınıveyapısınıgörüntüler.`MethodTable`<br /><br /> Belirtilen modülün işlemde yüklenmesi gerekir.<br /><br /> Uygun tür adını almak için, [ıdisksm. exe ' yi (IL Disassembler)](ildasm-exe-il-disassembler.md)kullanarak modüle göz atabilirsiniz. Ayrıca, yüklenmiş tüm `*` yönetilen modülleri aramak için modül adı parametresi olarak da geçiş yapabilirsiniz. *Modül adı* parametresi, `mscorlib` ya `image00400000`da gibi bir modülün hata ayıklayıcı adı olabilir.<br /><br /> Bu`module`komut <`!`> Windows>hataayıklayıcısözdiziminidestekler<.`type` Tür, tam olarak nitelenmiş olmalıdır.|
|**ObjSize** [\<*Nesne adresi*>] &#124; [ **-Aggregate**] [ **-stat**]|Belirtilen nesnenin boyutunu görüntüler. Herhangi bir parametre belirtmezseniz, **ObjSize** komutu yönetilen iş parçacıklarında bulunan tüm nesnelerin boyutunu görüntüler, işlemdeki tüm çöp toplayıcı tanıtıcılarını görüntüler ve bu tutamaçlar tarafından işaret edilen nesnelerin boyutunu toplar. **ObjSize** komutu, üst öğeye ek olarak tüm alt nesnelerin boyutunu içerir.<br /><br /> **-Aggregate** seçeneği, hala kök olarak belirtilen türlerin ayrıntılı bir görünümünü almak için **-stat** bağımsız değişkeniyle birlikte kullanılabilir. **! Dumpheap-stat** ve **! ObjSize-Aggregate-stat**kullanarak, artık hangi nesnelerin kök olmadığını belirleyebilir ve çeşitli bellek sorunlarını tanılayabilirsiniz.|
|**PrintException** [ **-iç içe**] [ **-Lines**] [\<*Özel durum nesnesi adresi*>]<br /><br /> -veya-<br /><br /> **PE** [ **-iç içe**] [\<*Özel durum nesnesi adresi*>]|Belirtilen adresteki <xref:System.Exception> sınıftan türetilmiş herhangi bir nesnenin alanlarını görüntüler ve biçimlendirir. Bir adres belirtmezseniz, **PrintException** komutu geçerli iş parçacığında oluşturulan son özel durumu görüntüler.<br /><br /> **İç içe** geçmiş seçeneği, iç içe geçmiş özel durum nesneleri hakkındaki ayrıntıları görüntüler.<br /><br /> **-Lines** seçeneği, varsa, kaynak bilgilerini görüntüler.<br /><br /> Bu komutu, bir ikili dizi olan `_stackTrace` alanını biçimlendirmek ve görüntülemek için kullanabilirsiniz.|
|**ProcInfo** [ **-env**] [ **-Time**] [ **-mem**]|İşlem, çekirdek CPU süresi ve bellek kullanımı istatistikleri için ortam değişkenlerini görüntüler.|
|**Rcwcleanuplist** *Rcwcleanuplist adresi* \<>|Belirtilen adreste temizlenmeyi bekleyen çalışma zamanı çağrılabilir sarmalayıcılarının listesini görüntüler.|
|**Savemodule** \< *Temel*adresDosya> adı\<>|Belirtilen adreste belleğe yüklenen bir görüntüyü belirtilen dosyaya yazar.|
|**SOSFlush**|Bir iç SOS önbelleğini temizler.|
|**Stoponexception** [ **-türetilmiş**] [ **-Create** &#124; **-Create2**] \< *Özel*durumsözde> kayıt numarası\<>|Belirtilen özel durum oluştuğunda hata ayıklayıcının durmasına, fakat diğer özel durumlar oluştuğunda çalışmaya devam etmesine neden olur.<br /><br /> **-Derived** seçeneği belirtilen özel durumu ve belirtilen özel durumdan türetilen her özel durumu yakalar.|
|**SyncBlk** [ **-Tüm** &#124; \< *SyncBlk numarası*>]|Belirtilen `SyncBlock` yapıyı veya tüm `SyncBlock` yapıları görüntüler.  Herhangi bir bağımsız değişken geçirmezseniz, **SyncBlk** komutu bir iş parçacığına ait `SyncBlock` olan nesnelere karşılık gelen yapıyı görüntüler.<br /><br /> `SyncBlock` Yapı, her nesne için oluşturulması gerekmeyen ek bilgiler için bir kapsayıcıdır. COM birlikte çalışabilirlik verilerini, karma kodları ve güvenli iş parçacığı işlemlerine ilişkin kilitleme bilgilerini tutabilir.|
|**Parçacığı**|Kuyruktaki iş isteklerinin sayısı, derleme bağlantı noktası iş parçacıklarının sayısı ve zamanlayıcıların sayısı dahil, yönetilen iş parçacığı havuzuyla ilgili bilgileri görüntüler.|
|**Token2EE** *Modül adı* belirteci \<> \<>|Belirtilen modüldeki belirtilen meta veri belirtecini bir `MethodTable` yapıya veya `MethodDesc` yapıya dönüştürür.<br /><br /> Bu belirtecin, `*` yüklenen her yönetilen modülde ne şekilde eşlendiğini bulmak için modül adı parametresi için geçiş yapabilirsiniz. Ayrıca, veya `mscorlib` `image00400000`gibi bir modül için hata ayıklayıcının adını geçirebilirsiniz.|
|**Iş parçacıkları** [ **-Live**] [ **-özel**]|İşlemdeki tüm yönetilen iş parçacıklarını görüntüler.<br /><br /> **Threads** komutu, hata AYıKLAYıCı Özet KIMLIĞI, clr Iş parçacığı kimliği ve işletim sistemi Iş parçacığı kimliğini görüntüler.  Ayrıca, **Iş parçacıkları** komutu, bir iş parçacığının yürütüldüğü uygulama etki ALANıNı, com apartman modunu görüntüleyen bir apt sütununu ve içinde oluşturulan son özel durumu gösteren bir özel durum sütununu gösteren bir etki alanı sütunu görüntüler. zincirinin.<br /><br /> **-Live** seçeneği, canlı bir iş parçacığıyla ilişkili iş parçacıklarını görüntüler.<br /><br /> **-Özel** SEÇENEĞI, CLR tarafından oluşturulan tüm özel iş parçacıklarını görüntüler. Özel iş parçacıkları çöp toplama iş parçacıklarını (eşzamanlı ve sunucu çöp toplama), hata ayıklayıcı yardımcı iş parçacıklarını, Sonlandırıcı <xref:System.AppDomain> iş parçacıklarını, kaldırma iş parçacıklarını ve iş parçacığı havuzu zamanlayıcı iş parçacıklarını içerir|
|**ThreadState \<**  *durum değeri alanı* **>**|Bir iş parçacığının durumunu görüntüler. Parametresi, **iş parçacıkları** rapor çıkışında `State` alanın değeridir. `value`<br /><br /> Örnek:<br /><br /> `0:003> !Threads     ThreadCount:      2     UnstartedThread:  0     BackgroundThread: 1     PendingThread:    0     DeadThread:       0     Hosted Runtime:   no                                           PreEmptive   GC Alloc           Lock            ID OSID ThreadOBJ    State     GC       Context       Domain   Count APT Exception        0    1  250 0019b068      a020 Disabled 02349668:02349fe8 0015def0     0 MTA        2    2  944 001a6020      b220 Enabled  00000000:00000000 0015def0     0 MTA (Finalizer)     0:003> !ThreadState b220         Legal to Join         Background         CLR Owns         CoInitialized         In Multi Threaded Apartment`|
|**TraverseHeap** [ **-XML**] \< *dosya adı*>|Yığın bilgilerini, CLR profil oluşturucusunun anlayacağı bir biçimde belirtilen dosyaya yazar. **-XML** seçeneği **TRAVERSEHEAP** komutunun dosyayı XML olarak biçimlendirmeye neden olur.<br /><br /> CLR Profiler 'ı [Microsoft Indirme merkezi](https://go.microsoft.com/fwlink/?LinkID=67325)' nden indirebilirsiniz.|
|**U** [ **- gcinfo**] [ **- ehinfo**] [ **- n**] \< *MethodDesc adresi*> &#124; \< *Kod adresi*>|Yöntemi için bir `MethodDesc` yapı işaretçisi veya Yöntem gövdesi içindeki bir kod adresi tarafından belirtilen yönetilen metodun açıklamalı bir ayrıştırılmış derlemesini görüntüler. **U** komutu başlangıçtan sonuna kadar tüm yöntemi, meta veri belirteçlerini adlara dönüştüren ek açıklamalarla görüntüler.<br /><br /> **-Gcinfo** seçeneği **U** komutunun yöntemin `GCInfo` yapısını görüntülemesine neden olur.<br /><br /> **-EHInfo** seçeneği, yöntemi için özel durum bilgilerini görüntüler. Bu bilgileri, **EHInfo** komutuyla da elde edebilirsiniz.<br /><br /> **-N** seçeneği, kaynak dosya adları ve satır numaralarının görüntüsünü devre dışı bırakır. Hata ayıklayıcı için SYMOPT_LOAD_LINES seçeneği belirtildiyse, SOS yönetilen her çerçeve için simgelere bakar ve başarılı olursa, ilgili dosya adını ve satır numarasını görüntüler. Bu davranışı devre dışı bırakmak için **-n** seçeneğini belirtebilirsiniz.|
|**VerifyHeap**|Bozulma işaretleri için çöp toplayıcı yığınını kontrol eder ve bulunan hataları görüntüler.<br /><br /> Yığın bozulmalarına, hatalı oluşturulan platform çağrıları neden olabilir.|
|**Doğrulamaları Yobj** \< *nesne adresi*>|Bir bağımsız değişken olarak geçirilen nesnede bozulma işaretleri olup olmadığını kontrol eder.|
|**VMMap**|Sanal adres alanını bir uçtan diğerine dolaşır ve her bir bölgeye uygulanan koruma türünü görüntüler.|
|**VMStat**|Sanal adres alanının bir özet görünümü, o belleğe (serbest, ayrılmış, adanmış, özel, eşlenmiş, görüntü) uygulanan her bir koruma türüne göre düzenlenmiş olarak sağlar. TOPLAM sütunu, ORTALAMA sütununun sonucunu BLK SAYIMI sütunuyla çarpılmış olarak görüntüler.|

## <a name="remarks"></a>Açıklamalar

SOS hata ayıklama uzantısı, CLR içinde çalışan kodla ilgili bilgileri görüntülemenize olanak sağlar. Örneğin, yönetilen yığınla ilgili bilgileri görüntülemek, yığın bozulmalarını aramak, çalışma zamanı tarafından kullanılan iç veri türlerini görüntülemek ve çalışma zamanı içinde çalışan tüm yönetilen kodla ilgili bilgileri görüntülemek için SOS Hata Ayıklama Uzantısı'nı kullanabilirsiniz.

SOS hata ayıklama uzantısını Visual Studio 'da kullanmak için, [Windows Sürücü Seti 'ni (WDK)](/windows-hardware/drivers/download-the-wdk)yükler. Visual Studio 'da tümleşik hata ayıklama ortamı hakkında daha fazla bilgi için bkz. [hata ayıklama ortamları](/windows-hardware/drivers/debugger/debuggers-in-the-debugging-tools-for-windows-package).

SOS hata ayıklama uzantısı 'nı [WinDbg. exe hata ayıklayıcısına](/windows-hardware/drivers/debugger/debugger-download-tools) yükleyerek ve WinDbg. exe içinde komutları çalıştırarak da kullanabilirsiniz.

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

Aşağıdaki komut, adresteki `1ca248`bir derlemenin içeriğini görüntüler.

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

Aşağıdaki komut, adresteki `MethodDesc` `902f40`yapıyı görüntüler.

```console
!dumpmd 902f40
```

Aşağıdaki komut adresteki `1caa50`bir modülle ilgili bilgileri görüntüler.

```console
!dumpmodule 1caa50
```

Aşağıdaki komut adresteki `a79d40`bir nesneyle ilgili bilgileri görüntüler.

```console
!DumpObj a79d40
```

Aşağıdaki komut adresteki bir değer sınıfının `00a79d9c` alanlarını adreste yöntem tablosunu `0090320c`kullanarak görüntüler.

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

Aşağıdaki komut adresteki `00a79d98`bir nesnenin uygulama etki alanını belirler.

```console
!findappdomain 00a79d98
```

Aşağıdaki komut, geçerli işlemdeki tüm çöp toplayıcı tanıtıcılarını görüntüler.

```console
!gcinfo 5b68dbb8
```

Aşağıdaki komut, modülündeki `MethodTable` `Main` `EEClass` sınıfındayöntemi`MainClass`içinve yapılarınıgörüntüler.`unittest.exe`

```console
!name2ee unittest.exe MainClass.Main
```

Aşağıdaki komut, modüldeki `02000003` `unittest.exe`adresteki meta veri belirteci hakkındaki bilgileri görüntüler.

```console
!token2ee unittest.exe 02000003
```

## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [Komut İstemleri](developer-command-prompt-for-vs.md)
