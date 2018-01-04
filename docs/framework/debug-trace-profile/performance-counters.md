---
title: ".NET Framework'teki Performans Sayaçları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance, .NET Framework applications
- performance counters
- performance monitoring, counters
ms.assetid: 06a4ae8c-eeb2-4d5a-817e-b1b95c0653e1
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 15486a55fc15ba2cc3cc64db50f317b39dfd77bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="performance-counters-in-the-net-framework"></a>.NET Framework'teki Performans Sayaçları
Bu konu içinde bulabilirsiniz performans sayaçları listesini sağlar [Performans İzleyicisi'ni](http://technet.microsoft.com/library/cc749249.aspx).  
  
-   [Özel durum performans sayaçları](#exception)  
  
-   [Birlikte çalışma performans sayaçları](#interop)  
  
-   [JIT performans sayaçları](#jit)  
  
-   [Performans sayaçları yükleniyor](#loading)  
  
-   [Kilit ve iş parçacığı performans sayaçları](#lockthread)  
  
-   [Bellek performansı sayaçları](#memory)  
  
-   [Ağ performans sayaçları](#networking)  
  
-   [Güvenlik performans sayaçları](#security)  
  
<a name="exception"></a>   
## <a name="exception-performance-counters"></a>Özel durum performans sayaçları  
 Performans konsolu .NET CLR özel durumları kategorisi bir uygulama tarafından oluşturulan özel durumlar hakkında bilgi sağlayan sayaçlar içerir. Aşağıdaki tabloda bu performans sayaçları açıklanmaktadır.  
  
|Performans sayacı|Açıklama|  
|-------------------------|-----------------|  
|**Atılan sayısı**|Uygulama başlatıldığından bu yana oluşturulan özel durumları toplam sayısını görüntüler. Bu, .NET özel durumlarını ve .NET özel durumlarını dönüştürülür yönetilmeyen özel durumları içerir. Örneğin, yönetilmeyen koddan döndürülen HRESULT yönetilen kodda bir özel durum dönüştürülür.<br /><br /> Bu sayaç işlenen ve işlenmeyen özel durumları içerir. İşlenemezse özel durumlar yeniden sayılır.|  
|**Durum Sayısı / sn**|Saniye başına oluşturulan özel durumları sayısını görüntüler. Bu, .NET özel durumlarını ve .NET özel durumlarını dönüştürülür yönetilmeyen özel durumları içerir. Örneğin, yönetilmeyen koddan döndürülen HRESULT yönetilen kodda bir özel durum dönüştürülür.<br /><br /> Bu sayaç işlenen ve işlenmeyen özel durumları içerir. Bu ortalama zaman içinde değildir; örnek aralığının süresine son iki örnekte gözlenen değerler arasındaki farkı görüntüler. Bu sayaç bir gösterge olası performans sorunlarını büyük ise (> 100 saniye) özel durum sayısı oluşturulur.|  
|**Filtreler sayısı / sn**|Saniye başına yürütülen .NET özel durum filtreleri sayısını görüntüler. Bir özel durum filtresi bir özel durumun işlenip bağımsız olarak değerlendirir.<br /><br /> Bu sayaç ortalama zaman içinde değil; örnek aralığının süresine son iki örnekte gözlenen değerler arasındaki farkı görüntüler.|  
|**Finallys sayısı / sn**|Finally blokları saniye başına yürütülen sayısını görüntüler. Bir blok nasıl try bloğunun çıkıldı bağımsız olarak yürütülecek son olarak sağlanır.  Yalnızca finally blokları için bir özel durum yürütülen dikkate alınır; finally blokları normal kod yolları Bu sayaç tarafından sayılmaz.<br /><br /> Bu sayaç ortalama zaman içinde değil; örnek aralığının süresine son iki örnekte gözlenen değerler arasındaki farkı görüntüler.|  
|**Throw derinliği Catch / sn**|Özel durumun işlenip çerçeveye özel durum oluşturdu çerçeveden yığın çerçeveleri sayısı geçiş görüntüler saniyede. Bir özel durum işleyici girildiğinde, iç içe geçmiş özel durum işleyici işleyici Yığın derinliği göstermek için bu sayaç sıfırlar.<br /><br /> Bu sayaç ortalama zaman içinde değil; örnek aralığının süresine son iki örnekte gözlenen değerler arasındaki farkı görüntüler.|  
  
<a name="interop"></a>   
## <a name="interop-performance-counters"></a>Birlikte çalışma performans sayaçları  
 Performans konsolu .NET CLR Interop kategorisi COM bileşenlerini, COM + hizmetlerinin ve dış tür kitaplıklarının uygulamanın etkileşimi hakkında bilgi sağlayan sayaçlar içerir. Aşağıdaki tabloda bu performans sayaçları açıklanmaktadır.  
  
|Performans sayacı|Açıklama|  
|-------------------------|-----------------|  
|**CCWs sayısı**|COM aranabilir sarmalayıcılar (CCWs) geçerli sayısını görüntüler. Bir saatin tersi YÖNDE yönetilmeyen bir COM istemciden başvurulan yönetilen bir nesne için bir proxy ' dir. Bu sayaç tarafından yönetilmeyen COM kod başvurulan yönetilen nesne sayısını gösterir.|  
|**hazırlamaya #**|Toplam sayısını görüntüler sürelerinin bağımsız değişkenleri ve dönüş değerleri gelen yönetilmeyen kod için ve tersi, uygulama başladıktan sonra yönetilen sıralanmış durumda. Saplamalar içermesinden varsa bu sayaç artırılır değil. (Saplamalar bağımsız değişkenleri hazırlama için sorumludur ve dönüş değerleri). Ek yükü hazırlama küçükse saplamalar genellikle içermesinden.|  
|**Saplamalar sayısı**|Ortak dil çalışma zamanı tarafından oluşturulan saplamalar geçerli sayısını görüntüler. Saplamalar bağımsız değişkenleri hazırlama için sorumlu ve dönüş değerleri yönetilmeyen yönetilen koddan ve tersi yönde COM birlikte çalışma çağrısı veya bir platform sırasında çağrısı başlatılacak.|  
|**TLB dışarı sayısı / sn**|Daha sonraki kullanımlar için ayrılmıştır.|  
|**TLB içeri aktarmalar sayısı / sn**|Daha sonraki kullanımlar için ayrılmıştır.|  
  
<a name="jit"></a>   
## <a name="jit-performance-counters"></a>JIT performans sayaçları  
 Performans konsolu .NET CLR JIT kategorisi JIT derlenmiş kodu hakkında bilgi sağlayan sayaçlar içerir. Aşağıdaki tabloda bu performans sayaçları açıklanmaktadır.  
  
|Performans sayacı|Açıklama|  
|-------------------------|-----------------|  
|**IL bayt JITted sayısı**|Uygulama başladıktan sonra tam zamanında (JIT) derleyicisi tarafından derlenen Microsoft Ara dili (MSIL) bayt toplam sayısını görüntüler. Bu sayaç eşdeğerdir **toplam IL bayt Jitted sayısı** sayacı.|  
|**Yöntemleri JITted sayısı**|Yöntemleri toplam sayısını görüntüler JIT derlenmiş uygulama itibaren başlatıldı. Bu sayaç öncesi JIT derlenmiş yöntemleri dahil değildir.|  
|**JIT % zaman**|JIT derleme son JIT derleme aşaması itibaren harcadığı geçen sürenin yüzdesini görüntüler. Bu sayaç, her JIT derleme aşamasının sonunda güncelleştirilir. JIT derleme aşaması bir yöntem oluşur ve bağımlılıklarını derlenir.|  
|**IL bayt Jitted / sn**|JIT derlenmiş MSIL bayt sayısını görüntüler saniyede. Bu sayaç ortalama zaman içinde değil; örnek aralığının süresine son iki örnekte gözlenen değerler arasındaki farkı görüntüler.|  
|**Standart JIT hataları**|JIT derleme uygulama başladıktan sonra derlemek için başarısız oldu yöntemleri en yüksek sayısını görüntüler. MSIL doğrulanamazsa veya JIT Derleyici iç bir hata varsa bu hata oluşabilir.|  
|**IL bayt Jitted toplam sayısı**|Toplam MSIL bayt görüntüler JIT derlenmiş uygulama itibaren başlatıldı. Bu sayaç eşdeğerdir **IL bayt Jitted sayısı** sayacı.|  
  
<a name="loading"></a>   
## <a name="loading-performance-counters"></a>Performans sayaçları yükleniyor  
 Performans konsolu .NET CLR Yükleme kategorisi derlemeler, sınıflar ve yüklenen uygulama etki alanları hakkında bilgi sağlayan sayaçlar içerir. Aşağıdaki tabloda bu performans sayaçları açıklanmaktadır.  
  
|Performans sayacı|Açıklama|  
|-------------------------|-----------------|  
|**% Zaman yükleniyor**|Daha sonraki kullanımlar için ayrılmıştır.|  
|**Derleme arama uzunluğu**|Daha sonraki kullanımlar için ayrılmıştır.|  
|**Yükleyici Yığınındaki Bayt**|Tüm uygulama etki alanları arasında sınıf yükleyicisi tarafından kaydedilen belleğin bayt cinsinden geçerli boyutu görüntüler. Kaydedilmiş bellek disk belleği dosyasında ayrılmış fiziksel bir alandır.|  
|**Geçerli uygulama etki alanları**|Uygulama etki alanları bu uygulamada yüklenen geçerli sayısını görüntüler.|  
|**Geçerli derlemeler**|Şu anda çalışan uygulama için tüm uygulama alanlarında derlemeleri yüklenen geçerli sayısını görüntüler. Derleme birden çok uygulama etki alanından olarak etki alanı Tarafsız yüklerse Bu sayaç yalnızca bir kez artırılır.|  
|**Yüklenen geçerli sınıfları**|Tüm derlemelerde yüklenen sınıfların geçerli sayısı görüntüler.|  
|**Uygulama etki alanları oranı**|Uygulama etki alanları saniyede yüklenen sayısını görüntüler. Bu sayaç ortalama zaman içinde değil; örnek aralığının süresine son iki örnekte gözlenen değerler arasındaki farkı görüntüler.|  
|**Kaldırıldığında appdomains oluşturuyor oranı**|Saniye başına kaldırıldığında uygulama etki alanları sayısını görüntüler. Bu sayaç ortalama zaman içinde değil; örnek aralığının süresine son iki örnekte gözlenen değerler arasındaki farkı görüntüler.|  
|**Derlemeleri oranı**|Derlemeleri başına yüklenen tüm uygulama etki alanları arasında ikinci görüntüler. Derleme birden çok uygulama etki alanından olarak etki alanı Tarafsız yüklerse Bu sayaç yalnızca bir kez artırılır.<br /><br /> Bu sayaç ortalama zaman içinde değil; örnek aralığının süresine son iki örnekte gözlenen değerler arasındaki farkı görüntüler.|  
|**Yüklenen sınıfların oranı**|İkinci tüm derlemelerde başına yüklenen sınıfların sayısını görüntüler. Bu sayaç ortalama zaman içinde değil; örnek aralığının süresine son iki örnekte gözlenen değerler arasındaki farkı görüntüler.|  
|**Yükleme hataları oranı**|Yüklenemedi sınıfları görüntüler saniyede. Bu sayaç ortalama zaman içinde değil; örnek aralığının süresine son iki örnekte gözlenen değerler arasındaki farkı görüntüler.<br /><br /> Yükleme hataları, yetersiz güvenlik veya biçimi geçersiz gibi birçok nedenlerle ortaya çıkabilir. Profil Oluşturma Hizmetleri Yardımı Ayrıntılar için bkz.|  
|**Yükleme hataları toplam sayısı**|Uygulama başladıktan sonra yüklenemedi sınıfları en yüksek sayısını görüntüler.<br /><br /> Yükleme hataları, yetersiz güvenlik veya biçimi geçersiz gibi birçok nedenlerle ortaya çıkabilir. Profil Oluşturma Hizmetleri Yardımı Ayrıntılar için bkz.|  
|**Toplam uygulama etki alanları**|Uygulama etki alanları uygulama başlatıldığından bu yana yüklenen en yüksek sayısını görüntüler.|  
|**Toplam uygulama etki alanları kaldırıldı**|Uygulama etki alanları uygulama başladıktan sonra kaldırıldığında toplam sayısını görüntüler. Uygulama etki alanı yüklendiğinde ve birden çok kez kaldırıldığında, uygulama etki alanı kaldırılmadan her zaman bu sayaç artırılır.|  
|**Toplam derlemeler**|Uygulama başlatıldığından bu yana derlemeler yüklenen toplam sayısını görüntüler. Derleme birden çok uygulama etki alanından olarak etki alanı Tarafsız yüklerse Bu sayaç yalnızca bir kez artırılır.|  
|**Yüklenen Toplam sınıfları**|Uygulama başladıktan sonra tüm derlemelerde yüklenen sınıfların toplam sayısı görüntülenir.|  
  
<a name="lockthread"></a>   
## <a name="lock-and-thread-performance-counters"></a>Kilit ve iş parçacığı performans sayaçları  
 Performans konsolu .NET CLR LocksAndThreads kategorisi yönetilen kilitleri hakkında bilgi sağlayan sayaçları ve bir uygulamanın kullandığı iş parçacıklarının içerir. Aşağıdaki tabloda bu performans sayaçları açıklanmaktadır.  
  
|Performans sayacı|Açıklama|  
|-------------------------|-----------------|  
|**Geçerli mantıksal iş parçacığı sayısı**|Mevcut yönetilen iş parçacığı nesneleri uygulamada görüntüler. Bu sayaç, her iki çalışan sayısı tutar ve iş parçacığı durduruldu. Bu sayaç ortalama zaman içinde değil; yalnızca gözlenen son değeri görüntüler.|  
|**Geçerli fiziksel iş parçacığı sayısı**|Oluşturulan ve yönetilen iş parçacığı nesneleri için temel alınan iş parçacığı olarak davranmak üzere ortak dil çalışma zamanı tarafından sahip olunan yerel işletim sistemi iş parçacığı sayısını görüntüler. Bu sayacın değeri iç işlemlerini çalışma zamanı tarafından kullanılan iş parçacıklarını kapsamaz; işletim sistemi işlemdeki iş parçacıklarının alt kümesidir.|  
|**Geçerli tanınan iş parçacığı sayısı**|Şu anda çalışma zamanı tarafından tanınan iş parçacığı sayısını görüntüler. Bu iş parçacıkları karşılık gelen bir yönetilen iş parçacığı nesnesi ile ilişkilendirilmiş. Çalışma zamanı bu iş parçacıkları oluşturmaz, ancak çalışma zamanı içinde en az bir kez çalıştırdıktan.<br /><br /> Yalnızca benzersiz iş parçacığı izlenir; çalışma zamanı yeniden girin veya iş parçacığının çıktıktan sonra yeniden iş parçacığı aynı iş parçacığı Kimliğine sahip iki kez sayılmaz.|  
|**Toplam tanınan iş parçacığı sayısı**|Toplam uygulama başladıktan sonra çalışma zamanı tarafından tanınan iş parçacıklarının sayısını görüntüler. Bu iş parçacıkları karşılık gelen bir yönetilen iş parçacığı nesnesi ile ilişkilendirilmiş. Çalışma zamanı bu iş parçacıkları oluşturmaz, ancak çalışma zamanı içinde en az bir kez çalıştırdıktan.<br /><br /> Yalnızca benzersiz iş parçacığı izlenir; çalışma zamanı yeniden girin veya iş parçacığının çıktıktan sonra yeniden iş parçacığı aynı iş parçacığı Kimliğine sahip iki kez sayılmaz.|  
|**Çakışma oranı / sn**|Çalışma zamanı iş parçacıklarında başarısız yönetilen bir kilidi elde etmeye hızını görüntüler.|  
|**Geçerli sıra uzunluğu**|Şu anda uygulamasında yönetilen bir kilidi için bekleyen iş parçacığı toplam sayısını görüntüler. Bu sayaç ortalama zaman içinde değil; gözlenen son değeri görüntüler.|  
|**Kuyruk uzunluğu / sn**|Uygulamadaki bir kilit edinmeye bekleyen saniye başına iş parçacığı sayısını görüntüler. Bu sayaç ortalama zaman içinde değil; örnek aralığının süresine son iki örnekte gözlenen değerler arasındaki farkı görüntüler.|  
|**Kuyruk uzunluğu en yüksek**|Toplam uygulama başladıktan sonra yönetilen bir kilidi için beklenen iş parçacığı sayısını görüntüler.|  
|**oranı tanınan iş parçacığı sayısı / sn**|Çalışma zamanı tarafından tanınan saniye başına iş parçacığı sayısını görüntüler. Bu iş parçacıkları karşılık gelen bir yönetilen iş parçacığı nesnesi ile ilişkilendirilmiş. Çalışma zamanı bu iş parçacıkları oluşturmaz, ancak çalışma zamanı içinde en az bir kez çalıştırdıktan.<br /><br /> Yalnızca benzersiz iş parçacığı izlenir; çalışma zamanı yeniden girin veya iş parçacığının çıktıktan sonra yeniden iş parçacığı aynı iş parçacığı Kimliğine sahip iki kez sayılmaz.<br /><br /> Bu sayaç ortalama zaman içinde değil; örnek aralığının süresine son iki örnekte gözlenen değerler arasındaki farkı görüntüler.|  
|**Çekişmeleri toplam sayısı**|Çalışma zamanında iş parçacığı bir yönetilen başarısız kilidi denediniz toplam sayısını görüntüler.|  
  
<a name="memory"></a>   
## <a name="memory-performance-counters"></a>Bellek performansı sayaçları  
 Performans konsolu .NET CLR bellek kategorisi atık toplayıcı hakkında bilgi sağlayan sayaçlar içerir. Aşağıdaki tabloda bu performans sayaçları açıklanmaktadır.  
  
|Performans sayacı|Açıklama|  
|-------------------------|-----------------|  
|**# Tüm yığınlardaki bayt**|Toplamını görüntüler **Gen 1 yığın boyutu**, **Gen 2 yığın boyutu**, ve **büyük nesne yığın boyutu** sayaçları. Bu sayaç, atık toplama üzerinde ayrılan belleği bayt cinsinden geçerli gösterir. yığın.|  
|**# GC işleme**|Çöp toplama tanıtıcı geçerli sayısı kullanımda görüntüler. Çöp toplama tanıtıcıları ortak dil çalışma zamanı ve Yönetilen ortamlarda dış kaynaklara tanıtıcılarıdır.|  
|**# Gen 0 koleksiyonları**|Uygulama başlatıldığından beri çöp toplama (diğer bir deyişle, yeni, son ayrılmış nesnelerin) kuşak 0 nesnelerinin olan sayısını görüntüler.<br /><br /> 0 oluşturmada kullanılabilir bellek ayırma isteği karşılamak yeterli olmadığında kuşak 0 atık toplama oluşur. Bu sayaç, bir kuşak 0 atık toplama sonunda artırılır. Daha yüksek nesil çöp koleksiyonları tüm alt nesil koleksiyonları içerir. Bu sayaç, daha yüksek oluşturma (kuşak 1 veya 2) çöp toplama oluştuğunda açık olarak artırılır.<br /><br /> Bu sayaç gözlenen son değeri görüntüler. **Sadece _Global\_**  sayaç değeri tam doğru değildir ve yoksayılmalıdır.|  
|**# Gen 1 koleksiyonları**|Uygulama başladıktan sonra toplanacak 1. nesil nesneleridir sayısını görüntüler.<br /><br /> Nesil 1 çöp toplama sonunda sayaç artırılır. Daha yüksek nesil çöp koleksiyonları tüm alt nesil koleksiyonları içerir. Bu sayaç, daha yüksek oluşturma (2. nesil) çöp toplama oluştuğunda açık olarak artırılır.<br /><br /> Bu sayaç gözlenen son değeri görüntüler. **Sadece _Global\_**  sayaç değeri tam doğru değildir ve yoksayılmalıdır.|  
|**# Gen 2 koleksiyonları**|Uygulama başladıktan sonra toplanacak 2. nesil nesneleridir sayısını görüntüler. Bu sayaç, nesil 2 çöp toplama (tam atık toplama olarak da adlandırılır) sonunda artırılır.<br /><br /> Bu sayaç gözlenen son değeri görüntüler. **Sadece _Global\_**  sayaç değeri tam doğru değildir ve yoksayılmalıdır.|  
|**# Uyarılmış GC**|Tepe sayısı atık toplama gerçekleştirilir için açık bir çağrı nedeniyle görüntüler <xref:System.GC.Collect%2A?displayProperty=nameWithType>. Alt koleksiyonlar sıklığını ayarlamak için Atık toplayıcısının izin vermek için iyi bir uygulamadır.|  
|**Sabitlenmiş nesnelerin sayısı**|Son çöp toplama karşılaştı sabitlenmiş nesne sayısını görüntüler. Çöp toplayıcı bellekte taşıyamazsınız bir nesne bir sabitlenmiş nesnesidir. Bu sayaç, toplanacak olan yığınlara sabitlenmiş nesneleri izler. Örneğin, kuşak 0 çöp toplama sabitlenmiş nesneleri listesi yalnızca kuşak 0 yığınında neden olur.|  
|**Havuz blokları # kullanımda**|Geçerli eşitleme blokları kullanımda görüntüler. Eşitleme, eşitleme bilgilerini depolamak için ayrılan nesne başına veri yapılarını taşlarıdır. Zayıf başvurular için yönetilen nesnelerle ve atık toplayıcısı tarafından taranan tuttukları. Eşitleme blokları eşitleme bilgilerini depolamak için sınırlı değildir; Bunlar ayrıca COM birlikte çalışma meta veri depolayabilirsiniz. Bu sayaç, eşitleme temelleri kullanımına ağırlık performans sorunları gösterir.|  
|**# Toplam kaydedilmiş bayt**|Şu anda atık toplayıcısı tarafından kaydedilmiş bayt sanal bellek miktarını görüntüler. Kaydedilmiş bellek, disk belleği dosyasında alan ayrılmış fiziksel bellektir.|  
|**# Toplam bayt ayrılmış**|Çöp toplayıcı tarafından şu anda ayrılmış bayt cinsinden sanal bellek miktarını görüntüler. Hiçbir disk veya ana bellek sayfalarının kullanıldığı zaman ayrılmış uygulama için ayrılan sanal bellek alanı bellektir.|  
|**GC % zaman**|Son atık toplama döngüsünden beri çöp toplama gerçekleştirme harcandığını geçen sürenin yüzdesini görüntüler. Bu sayaç, genellikle Uygulama adına toplama ve compact belleğe atık toplayıcı tarafından çalışmanın gösterir. Bu sayaç yalnızca her çöp toplama sonunda güncelleştirilir. Bu sayaç, bir ortalama değil; değerini gözlenen son değeri yansıtır.|  
|**Ayrılan bayt/saniye**|Çöp toplama yığında ayrılmış saniyede bayt sayısını görüntüler. Bu sayaç her ayırma değil, her bir atık toplama işleminin sonunda güncelleştirilir. Bu sayaç ortalama zaman içinde değil; örnek aralığının süresine son iki örnekte gözlenen değerler arasındaki farkı görüntüler.|  
|**Sonlandırma Survivors**|Son haline için bekleyen olduğundan, bir koleksiyon varlığını sürdürmesini çöpünün toplanma nesne sayısını görüntüler. Bu nesneler diğer nesnelerin referansları tutarsanız, bu nesneler, aynı zamanda varlığını sürdürmesini ancak bu sayaç tarafından sayılmaz. **Sonlandırma bellek yükseltilmiş Gen 0'dan** sayaç sonlandırma nedeniyle derdi bitti tüm belleği temsil eder.<br /><br /> Bu sayaç kümülatif değildir; yalnızca bu belirli toplama sırasında survivors sayısı ile her çöp toplama işleminin sonunda güncelleştirilir. Bu sayaç, uygulama sonlandırma nedeniyle neden olabilecek ek yüke gösterir.|  
|**Gen 0 yığın boyutu**|Kuşak 0 ayrılabilecek en fazla bayt görüntüler; Geçerli nesil 0 ayrılan bayt sayısı göstermez.<br /><br /> Kuşak 0 atık toplama, son toplamadan beri ayırmaları bu boyutunu aşan oluşur. Kuşak 0 boyutu atık toplayıcısı tarafından ayarlanmıştır ve uygulama yürütme sırasında değiştirebilirsiniz. Nesil nesil 0 koleksiyon boyutu sonunda 0 yığın 0 bayt'tır. Bu sayaç, sonraki kuşak 0 atık toplama çağırır ayırmaları bayt cinsinden boyutu görüntüler.<br /><br /> Bu sayaç her ayırma değil, bir atık toplama işleminin sonunda güncelleştirilir.|  
|**Gen 0 yükseltilen bayt/sn**|Saniye başına 0 kuşaktan 1. nesil için öne çıkar bayt görüntüler. Çöp toplama devam eder, bellek yükseltilir. Bu sayaç, saniyede oluşturulan oldukça uzun süreli nesnelerin bir göstergesidir.<br /><br /> Bu sayaç, örnek aralığının süresine son iki örnekte gözlenen değerler arasındaki farkı görüntüler.|  
|**Gen 1 yığın boyutu**|Geçerli bayt sayısı 1. nesil görüntüler; Bu sayaç, 1. nesil en büyük boyutunu görüntülemez. Nesneleri bu oluşturma doğrudan ayrılmaz; Bunlar, önceki nesil 0 çöp koleksiyonları öne çıkar. Bu sayaç her ayırma değil, bir atık toplama işleminin sonunda güncelleştirilir.|  
|**Gen 1 yükseltilen bayt/sn**|Saniyede 1 kuşaktan 2. nesil için öne çıkar bayt görüntüler. Sonuçlandırılmış için yalnızca bekleyen için öne çıkar nesneleri bu sayaca dahil edilmez.<br /><br /> Çöp toplama devam eder, bellek yükseltilir. Eski nesil olduğundan hiçbir şey 2 kuşaktan yükseltilir. Bu sayaç, saniyede oluşturulan çok uzun süreli nesnelerin bir göstergesidir.<br /><br /> Bu sayaç, örnek aralığının süresine son iki örnekte gözlenen değerler arasındaki farkı görüntüler.|  
|**Gen 2 yığın boyutu**|Geçerli bayt sayısı 2. nesil görüntüler. Nesneleri bu oluşturma doğrudan ayrılmaz; Bunlar 1. nesil önceki nesil 1 çöp koleksiyonları sırasında öne çıkar. Bu sayaç her ayırma değil, bir atık toplama işleminin sonunda güncelleştirilir.|  
|**Büyük nesne yığın boyutu**|Geçerli boyutu büyük nesne yığın bayt cinsinden görüntüler. Yaklaşık 85. 000 bayttan büyük nesneleri büyük nesneler olarak atık toplayıcısı tarafından kabul edilir ve özel bir yığınında doğrudan ayrılır; nesli yükseltilmiş değil. Bu sayaç her ayırma değil, bir atık toplama işleminin sonunda güncelleştirilir.|  
|**İşlem kimliği**|İzlenmekte olan CLR işlem örneği işlem Kimliğini görüntüler.|  
|**Yükseltilen sonlandırma-bellekten Gen 0**|Son haline için yalnızca bekleyen bulunduğundan 0 kuşaktan 1. nesil için öne çıkar bayt bellek görüntüler. Bu sayaç kümülatif değildir; Son çöp toplama sonunda gözlenen değer görüntüler.|  
|**Yükseltilen bellekten Gen 0**|Çöp toplama varlığını sürdürmesini ve 0 kuşaktan 1. nesil için öne çıkar bayt bellek görüntüler. Sonuçlandırılmış için yalnızca bekleyen için öne çıkar nesneleri bu sayaca dahil edilmez. Bu sayaç kümülatif değildir; Son çöp toplama sonunda gözlenen değer görüntüler.|  
|**Yükseltilen bellekten Gen 1**|Çöp toplama varlığını sürdürmesini ve 1 kuşaktan 2. nesil için öne çıkar bayt bellek görüntüler. Sonuçlandırılmış için yalnızca bekleyen için öne çıkar nesneleri bu sayaca dahil edilmez. Bu sayaç kümülatif değildir; Son çöp toplama sonunda gözlenen değer görüntüler. Son atık toplama yalnızca kuşak 0 koleksiyona ise bu sayaç 0 değerine sıfırlanır.|  
  
<a name="networking"></a>   
## <a name="networking-performance-counters"></a>Ağ performans sayaçları  
 Performans konsolu .NET CLR ağ kategorisi alıp ağ üzerinden gönderen bir uygulama veriler hakkında bilgi sağlayan sayaçlar içerir. Aşağıdaki tabloda bu performans sayaçları açıklanmaktadır.  
  
|Performans sayacı|Açıklama|  
|-------------------------|-----------------|  
|**Alınan bayt**|Tüm tarafından alınan bayt toplam toplam sayısı <xref:System.Net.Sockets.Socket> içindeki nesneleri <xref:System.AppDomain> işlem başlatıldığından bu yana. Bu sayı, veri ve TCP/IP'yi tarafından tanımlanmayan herhangi bir protokolü bilgi içerir.|  
|**Gönderilen bayt**|Toplu tüm tarafından gönderilen bayt sayısı <xref:System.Net.Sockets.Socket> içindeki nesneleri <xref:System.AppDomain> işlem başlatıldığından bu yana. Bu sayı, veri ve TCP/IP'yi tarafından tanımlanmayan herhangi bir protokolü bilgi içerir.|  
|**Kurulan bağlantılar**|Toplu toplam sayısı <xref:System.Net.Sockets.Socket> nesneleri içinde herhangi bir zamanda bağlanmış akış yuvaları için <xref:System.AppDomain> işlem başlatıldığından bu yana.|  
|**Alınan veri birimi sayısı**|Tüm tarafından alınan veri birimi paketlerin toplam toplam sayısı <xref:System.Net.Sockets.Socket> içindeki nesneleri <xref:System.AppDomain> işlem başlatıldığından bu yana.|  
|**Gönderilen veri birimi**|Tüm tarafından gönderilen veri birimi paketlerin toplam toplam sayısı <xref:System.Net.Sockets.Socket> içindeki nesneleri <xref:System.AppDomain> işlem başlatıldığından bu yana.|  
|**HttpWebRequest ortalama yaşam süresi**|Tüm tamamlanmasını için ortalama süre <xref:System.Net.HttpWebRequest> son aralığı içinde sona nesneleri <xref:System.AppDomain> işlem başlatıldığından bu yana.|  
|**HttpWebRequest ortalama kuyruk süresi**|Ortalama üzerinde sıraya süresi tüm <xref:System.Net.HttpWebRequest> sıra içinde son aralığı left nesneleri <xref:System.AppDomain> işlem başlatıldığından bu yana.|  
|**Oluşturulan HttpWebRequests/sn**|Sayısı <xref:System.Net.HttpWebRequest> içinde saniye başına oluşturulan nesneler <xref:System.AppDomain>.|  
|**Sıraya alınan HttpWebRequests/sn**|Sayısı <xref:System.Net.HttpWebRequest> içinde saniyede sıraya eklenen nesneleri <xref:System.AppDomain>.|  
|**İptal HttpWebRequests/sn**|Sayısı <xref:System.Net.HttpWebRequest> burada uygulama adı verilen nesneleri <xref:System.Net.HttpWebRequest.Abort%2A> içinde Saniyedeki yöntemi <xref:System.AppDomain>.|  
|**Başarısız HttpWebRequests/sn**|Sayısı <xref:System.Net.HttpWebRequest> başarısız durum kodu sunucu içinde saniye başına alınan nesneleri <xref:System.AppDomain>.|  
  
 Performans sayaçları desteklenen ağ birkaç sınıfları şunlardır:  
  
-   Olay sayaçları, bazı olay sayısını ölçer.  
  
-   Gönderilen veya alınan verileri ölçü veri sayaçları.  
  
-   Ne kadar süreyle farklı işlemler ölçen süresi sayaçları alın. Zamanları nesnelerde ölçülür her zaman aralığını (genellikle saniye olarak) dışında farklı durumlara geldikleri sonra.  
  
-   Belirli bir yapmadan nesne sayısını ölçmek aralığı başına sayaçları (saniyede normalde) aralığa göre geçiş.  
  
 Olaylar için ağ performans sayaçları şunları içerir:  
  
-   **Kurulan bağlantılar**  
  
-   **Alınan veri birimi sayısı**  
  
-   **Gönderilen veri birimi**  
  
 İşlem başlatıldığından bu yana sayıları bu performans sayaçları sağlar. Sayısı <xref:System.Net.Sockets.Socket> kurulan bağlantılar içeren açık <xref:System.Net.Sockets.Socket> yöntemini çağıran bir uygulama tarafından olan akışa yuva diğer sınıflar tarafından yapılan de olarak iç çağrıları bağlantı için (<xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.WebClient>, ve <xref:System.Net.Sockets.TcpClient>, örneğin) için <xref:System.Net.Sockets.Socket> sınıfı  
  
 Sayılarını **alınan veri birimi** ve **veri birimleri gönderilen** gönderilen veya alınan açık kullanarak veri birimi paketlerini içeren <xref:System.Net.Sockets.Socket> yöntemini çağıran bir uygulama tarafından yapılan iyi iç çağrıları olarak tarafından sınıflar (<xref:System.Net.Sockets.UdpClient>, örneğin) için <xref:System.Net.Sockets.Socket>. Sınıf. Sayıları **alınan veri birimi** ve **veri birimleri gönderilen** kaç bayt gönderilen veya bir veri birimi için bir ortalama boyutu üstlenerek veri birimleri kullanılarak alınan çok kaba bir ölçü sağlamak için de kullanılabilir.  
  
 Veri ağ performans sayaçlarını aşağıdakileri içerir:  
  
-   **Alınan bayt**  
  
-   **Gönderilen bayt**  
  
 İşlem başlatıldığından bu yana yukarıdaki sayaçları bayt sayısını sağlar.  
  
 Ne kadar sürdüğü ölçmek iki süresi sayaç vardır <xref:System.Net.HttpWebRequest> ya da tüm oldukları yaşam süreleri geçirmek üzere nesneleri döngüsü veya sadece bu parçası:  
  
-   **HttpWebRequest ortalama yaşam süresi**  
  
-   **HttpWebRequest ortalama kuyruk süresi**  
  
 İçin **HttpWebRequest ortalama yaşam süresi** sayacı, çoğu ömrü <xref:System.Net.HttpWebRequest> nesneleri nesneyi yanıt akışına uygulama tarafından kapatıldığından zaman kadar oluşturulan zaman sahip her zaman başlatır. İki seyrek durumlar vardır:  
  
-   Uygulama hiçbir zaman çağırırsa <xref:System.Net.HttpWebRequest.GetResponse%2A> veya <xref:System.Net.HttpWebRequest.BeginGetResponse%2A> yöntemleri sonra ömrü <xref:System.Net.HttpWebRequest> nesne göz ardı edilir.  
  
-   Varsa <xref:System.Net.HttpWebRequest> nesne atar bir <xref:System.Net.WebException> çağrılırken <xref:System.Net.HttpWebRequest.GetResponse%2A> veya <xref:System.Net.HttpWebRequest.EndGetResponse%2A> yöntemleri, kullanım ömrü sona erer özel durum yakalandığında. Teknik olarak, temel alınan yanıt akış da bu noktada kapalı (gerçekten kullanıcıya döndürülen yanıt akışına yanıt akışına bir kopyasını içeren bir bellek akışı'dır).  
  
 Belirli izleme dört sayaç vardır <xref:System.Net.HttpWebRequest> nesne aralık başına sorunları. Bu performans sayaçlarını uygulama geliştiricileri, Yöneticiler, yardımcı olabilir ve destek personeli daha iyi anlamak ne <xref:System.Net.HttpWebRequest> nesneleri gittiğini. Sayaçlar şunlardır:  
  
-   **Oluşturulan HttpWebRequests/sn**  
  
-   **Sıraya alınan HttpWebRequests/sn**  
  
-   **İptal HttpWebRequests/sn**  
  
-   **Başarısız HttpWebRequests/sn**  
  
 İçin **HttpWebRequests iptal edildi/sn** sayaç, dahili çağrı <xref:System.Net.HttpWebRequest.Abort%2A> de sayılır. Bu dahili çağrıları genellikle uygulamanın ölçmek istediğiniz zaman aşımları tarafından hatalardır.  
  
 **HttpWebRequests başarısız/sn** sayısını içeriyor. sayaç <xref:System.Net.HttpWebRequest> başarısız durumu alınan nesneleri kod saniyede sunucusundan. Bu isteğin sonunda Http sunucusundan alınan durum kodu 200 için 299 arasındaki bir aralıkta değil anlamına gelir. İşlenir ve (örneğin 401 yetkilendirilmedi durum kodlarını birçoğu) başarısız veya yeniden deneme sonucuna göre başarısız olmayan yeni bir istek sonucunda durum kodları. Uygulama yeniden deneme sırasında temel bir hata görür, bu sayaç artırılır.  
  
 Performans sayaçları ağ erişilebilir ve yönetilen kullanarak <xref:System.Diagnostics.PerformanceCounter> ve ilgili sınıflar <xref:System.Diagnostics> ad alanı. Performans sayaçları ağ Windows Performans İzleyicisi konsoluyla birlikte görüntülenebilir.  
  
 Ağ performans sayaçları yapılandırma dosyasında kullanılacak etkinleştirilmesi gerekir. Tüm ağ performans sayaçlarını etkin veya yapılandırma dosyasında tek bir ayar ile devre dışı. Performans sayaçları ağ tek etkin veya devre dışı. Daha fazla bilgi için bkz: [ \<performanceCounter > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/performancecounter-element-network-settings.md).  
  
 Ağ sayaçları etkinleştirilirse, bu oluşturur ve güncelleştirme başına AppDomain ve genel performans sayaçları. Devre dışı bırakılırsa, uygulama ağ performans sayacı verileri sağlamaz.  
  
 Performans sayaçları kategorilerde gruplanır. Bir uygulama, aşağıdaki kod örneği ile kategorilerin tümünü listeleyebilirsiniz:  
  
```  
PerformanceCounterCategory[] Array = PerformanceCounterCategory.GetCategories();  
for (int i = 0; i < Array.Length; i++)  
{  
    Console.Out.WriteLine("{0}. Name={1} Help={2}", i, Array[i].CategoryName, Array[i].CategoryHelp);  
}  
```  
  
 Ağ performans sayaçları, iki kategoride listelenmiştir:  
  
-   ".NET CLR - .NET Framework sürüm 2 sürümünde sunulan ve .NET Framework sürüm 2'de desteklenir ve daha sonra özgün performans sayaçlarını ağ".  
  
-   ".NET CLR ağ 4.0.0.0" - Yukarıdaki yuva tümünün yeni performans sayaçları .NET Framework sürüm 4 ve üzerinde sayaçları. Bu yeni sayaçları performans bilgileri sağlayan <xref:System.Net.HttpWebRequest> nesneleri.  
  
 Verilere erişme ve uygulamada performans sayaçlarını yönetme hakkında daha fazla bilgi için bkz: [performans sayaçları](../../../docs/framework/debug-trace-profile/performance-counters.md).  
  
<a name="security"></a>   
## <a name="security-performance-counters"></a>Güvenlik performans sayaçları  
 Performans konsolu .NET CLR güvenlik kategorisi, ortak dil çalışma zamanı için bir uygulama yaptığı denetimleri güvenliği hakkında bilgi sağlayan sayaçlar içerir. Aşağıdaki tabloda bu performans sayaçları açıklanmaktadır.  
  
|Performans sayacı|Açıklama|  
|-------------------------|-----------------|  
|**# Bağlantı zamanı denetimleri**|Uygulama başlatıldığından bu yana görüntüler bağlama zamanı kodu erişim güvenliği toplam sayısını denetler. Tam zamanında (JIT) derleme zamanında belirli bir izin çağıran talep ettiğinde bağlama zamanı kodu erişim güvenlik denetimleri gerçekleştirilmez. Bir bağlama zamanı denetimi çağıran bir kez gerçekleştirilir. Bu sayı önemli performans sorunlarının göstergesi değil; Güvenlik sistem etkinliğini yalnızca göstergesi.|  
|**RT denetimleri % zaman**|Son örnekten beri geçen zamanın gerçekleştirme çalışma zamanı kod erişim güvenlik denetimlerini yüzdesini görüntüler. Bu sayaç, bir .NET Framework güvenlik denetimi sonunda güncelleştirilir. Ortalama bir değer değildir; gözlenen son değeri temsil eder.|  
|**% SIG zaman kimlik doğrulaması**|Daha sonraki kullanımlar için ayrılmıştır.|  
|**Yığın ilerlemesi derinliği**|Yığın derinliği bu son çalışma zamanı kod erişim güvenlik denetimi sırasında görüntüler. Çalışma zamanı kod erişim güvenlik denetimlerini yığın adım adım ilerlemenizi sağlayarak gerçekleştirilir. Bu sayaç, bir ortalama değil; yalnızca gözlenen son değeri görüntüler.|  
|**Toplam çalışma zamanı denetimleri**|Çalışma zamanı kodu toplam sayısı erişim güvenlik denetimleri uygulama başlatıldığından bu yana gerçekleştirilen görüntüler. Çalışma zamanı kodu erişim güvenlik çağıran belirli bir izin talep ettiğinde denetimleri yapılır. Çalışma zamanı onay her çağrıda çağıran tarafından oluşturulur ve geçerli çağıran iş parçacığı yığınını inceler. İle kullanıldığında **yığın yol derinliği** sayacı, bu sayaç, güvenlik denetimleri için ortaya çıkan yaşanan performans sorunları gösterir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans Sayaçları](../../../docs/framework/debug-trace-profile/performance-counters.md)  
 [Çalışma Zamanı Profili Oluşturma](../../../docs/framework/debug-trace-profile/runtime-profiling.md)
