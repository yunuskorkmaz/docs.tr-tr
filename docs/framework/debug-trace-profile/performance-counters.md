---
title: .NET Framework'teki Performans Sayaçları
ms.date: 03/30/2017
helpviewer_keywords:
- performance, .NET Framework applications
- performance counters
- performance monitoring, counters
ms.assetid: 06a4ae8c-eeb2-4d5a-817e-b1b95c0653e1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4839513f28de0fd79de7a8dc5245d4d0a2fb1622
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49123806"
---
# <a name="performance-counters-in-the-net-framework"></a>.NET Framework'teki Performans Sayaçları
Bu konu içinde bulabilirsiniz performans sayaçları listesi sağlar [Windows Performans İzleyicisi'ni](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc749249%28v=ws.11%29).  
  
-   [Özel durum performans sayaçları](#exception)  
  
-   [Interop performans sayaçları](#interop)  
  
-   [JIT performans sayaçları](#jit)  
  
-   [Yükleme performans sayaçları](#loading)  
  
-   [Kilit ve iş parçacığı performans sayaçları](#lockthread)  
  
-   [Bellek performans sayaçları](#memory)  
  
-   [Ağ performans sayaçları](#networking)  
  
-   [Güvenlik performans sayaçları](#security)  
  
<a name="exception"></a>   
## <a name="exception-performance-counters"></a>Özel durum performans sayaçları  
 Performans konsolu .NET CLR özel durumları kategorisi, bir uygulama tarafından oluşturulan özel durumları hakkında bilgi sağlayan sayaçlar içerir. Aşağıdaki tabloda, bu performans sayaçları açıklanmaktadır.  
  
|Performans sayacı|Açıklama|  
|-------------------------|-----------------|  
|**Durum sayısı**|Uygulamanın başlatılmasından bu yana oluşturulan özel durumları toplam sayısını görüntüler. .NET özel durumları ve .NET özel durumlarına dönüştürülmüş yönetilmeyen özel durumlar hem de buna dahildir. Örneğin, bir HRESULT döndürdü yönetilmeyen koddan yönetilen kodda bir özel durum dönüştürülür.<br /><br /> Bu sayaç işlenen ve yakalanamayan özel durumları içerir. Döndükten özel durumlar yeniden sayılır.|  
|**sayısı oluşturulan / sn**|Saniye başına oluşturulan özel durumların sayısını görüntüler. .NET özel durumları ve .NET özel durumlarına dönüştürülmüş yönetilmeyen özel durumlar hem de buna dahildir. Örneğin, bir HRESULT döndürdü yönetilmeyen koddan yönetilen kodda bir özel durum dönüştürülür.<br /><br /> Bu sayaç işlenen ve yakalanamayan özel durumları içerir. Ortalama zaman içinde bir değer değil; örnek aralığının süresine son iki örnekte gözlenen değerler arasındaki farkı görüntüler. Bu sayaç olası performans sorunlarını göstergesi büyük ise (> 100'lük bloklar) özel durum sayısı oluşturulur.|  
|**Filtreler sayısı / sn**|Saniye başına yürütülen .NET özel durum filtreleri sayısını görüntüler. Özel Durum Filtresi, bir özel durum işlense bağımsız olarak değerlendirir.<br /><br /> Bu sayaç ortalama zaman içinde değil; örnek aralığının süresine son iki örnekte gözlenen değerler arasındaki farkı görüntüler.|  
|**Finallys sayısı / sn**|Finally blokları saniye başına yürütülen sayısını görüntüler. Bir finally bloğu nasıl try bloğu çıkıldı bağımsız olarak yürütülecek garanti edilir.  Yalnızca son olarak yürütülen bir özel durum blokları dikkate alınır; finally blokları normal kod yollarında Bu sayaç tarafından sayılmaz.<br /><br /> Bu sayaç ortalama zaman içinde değil; örnek aralığının süresine son iki örnekte gözlenen değerler arasındaki farkı görüntüler.|  
|**Derinlik yakalamak için throw / sn**|Özel durum işlense çerçevesine bir özel durum oluşturdu çerçeveye yığını çerçeve sayısı geçiş görüntüler saniye başına. Özel durum işleyicisi girildiğinde, iç içe geçmiş özel durum işleyicisi işleyici Yığın derinliği göstermek için bu sayaç sıfırlar.<br /><br /> Bu sayaç ortalama zaman içinde değil; örnek aralığının süresine son iki örnekte gözlenen değerler arasındaki farkı görüntüler.|  
  
<a name="interop"></a>   
## <a name="interop-performance-counters"></a>Interop performans sayaçları  
 Performans konsolu .NET CLR Interop kategorisinin uygulamanın etkileşime COM bileşenlerini, COM + Hizmetleri ve dış tür kitaplıkları hakkında bilgi sağlayan sayaçlar içerir. Aşağıdaki tabloda, bu performans sayaçları açıklanmaktadır.  
  
|Performans sayacı|Açıklama|  
|-------------------------|-----------------|  
|**CCWs sayısı**|COM aranabilir sarmalayıcılarını (CCWs) geçerli sayısını görüntüler. Bir saat, yönetilmeyen bir COM istemcisi tarafından başvurulan yönetilen bir nesne için proxy'dir. Bu sayaç, yönetilmeyen COM kodu tarafından başvurulan yönetilen nesne sayısını gösterir.|  
|**Hazırlama sayısı**|Toplam sayıyı görüntüler sürelerinin bağımsız değişkenler ve dönüş değerleri yönetilmeyen koda ve tersi, uygulamanın başlatılmasından bu yana yönetilen yönetilenden. Bu sayaç saptamalar yapılırlar olduğunda artmaz. (Yer tutucular bağımsız değişkenleri sıralama için sorumludur ve dönüş değerlerini). Saptamalar, genellikle yükü hazırlama küçükse yapılırlar.|  
|**Saptamalar sayısı**|Ortak dil çalışma zamanı tarafından oluşturulan saptamalar geçerli sayısını görüntüler. Saptamalar bağımsız değişkenleri sıralama için sorumludur ve dönüş değerleri yönetilen, yönetilmeyen koddan ve tersi, COM birlikte çalışabilirlik çağrısı veya bir platform sırasında arama çağırmak.|  
|**TLB dışarı aktarmaları sayısı / sn**|Daha sonraki kullanımlar için ayrılmıştır.|  
|**TLB içeri aktarmalar sayısı / sn**|Daha sonraki kullanımlar için ayrılmıştır.|  
  
<a name="jit"></a>   
## <a name="jit-performance-counters"></a>JIT performans sayaçları  
 Performans konsolu .NET CLR JIT kategorisi JIT olarak derlenmiş kodu hakkında bilgi sağlayan sayaçlar içerir. Aşağıdaki tabloda, bu performans sayaçları açıklanmaktadır.  
  
|Performans sayacı|Açıklama|  
|-------------------------|-----------------|  
|**IL bayt Jıtted sayısı**|Uygulama başladıktan sonra just-in-time (JIT) derleyici tarafından derlenmiş Microsoft Ara dili (MSIL) bayt toplam sayısını görüntüler. Bu sayaç eşdeğerdir **toplam sayısı IL bayt Jıtted** sayacı.|  
|**Yöntemleri Jıtted sayısı**|Yöntemleri toplam sayısını görüntüler JIT olarak derlenmiş uygulama beri başlatılmış. Bu sayaç öncesi JIT-derlenmiş yöntem içermez.|  
|**JIT harcanan % zaman**|JIT derlemesi son JIT derleme aşaması beri harcanan sürenin yüzdesini görüntüler. Bu sayaç, her JIT derleme aşamasının sonunda güncelleştirilir. JIT derleme aşaması, bir yöntem olduğunda gerçekleşir ve bağımlılıklarını derlenir.|  
|**IL bayt Jıtted / sn**|JIT olarak derlenmiş MSIL bayt sayısını görüntüler saniye başına. Bu sayaç ortalama zaman içinde değil; örnek aralığının süresine son iki örnekte gözlenen değerler arasındaki farkı görüntüler.|  
|**Standart JIT hataları**|Yöntemler, JIT derleyicisi, uygulamanın başlatılmasından bu yana derlemek için başarısız oldu en yüksek sayısını görüntüler. MSIL doğrulanamıyor veya JIT derleyicide bir iç hata varsa bu hata oluşabilir.|  
|**IL bayt Jıtted toplam sayısı**|Toplam MSIL bayt görüntüler JIT olarak derlenmiş uygulama beri başlatılmış. Bu sayaç eşdeğerdir **IL bayt Jıtted sayısı** sayacı.|  
  
<a name="loading"></a>   
## <a name="loading-performance-counters"></a>Yükleme performans sayaçları  
 Performans konsolu .NET CLR Yükleme kategorisi, derlemeleri, sınıflar ve yüklenen uygulama etki alanları hakkında bilgi sağlayan sayaçlar içerir. Aşağıdaki tabloda, bu performans sayaçları açıklanmaktadır.  
  
|Performans sayacı|Açıklama|  
|-------------------------|-----------------|  
|**% Zaman yükleniyor**|Daha sonraki kullanımlar için ayrılmıştır.|  
|**Bütünleştirilmiş kod arama uzunluğu**|Daha sonraki kullanımlar için ayrılmıştır.|  
|**Yükleyici yığın bayt**|Tüm uygulama etki alanları arasında sınıf yükleyicisi tarafından kaydedilen bellek bayt cinsinden geçerli boyutu, görüntüler. İşlenen bellek disk disk belleği dosyasında ayrılmış fiziksel bir alandır.|  
|**Geçerli uygulama etki alanları**|Geçerli uygulama etki alanları bu uygulamada yüklenen sayısını görüntüler.|  
|**Geçerli derlemeler**|Şu anda çalışan uygulamada tüm uygulama etki alanları arasında derlemeler yüklü geçerli sayısını görüntüler. Derlemenin birden çok uygulama etki alanından etki alanı nötr olarak yüklenirse, bu sayaç yalnızca bir kez artırılır.|  
|**Yüklenen geçerli sınıfları**|Tüm derlemeler içinde yüklenen sınıfların geçerli sayıyı gösterir.|  
|**Uygulama etki alanları oranı**|Saniye başına yüklenen uygulama etki alanları sayısını görüntüler. Bu sayaç ortalama zaman içinde değil; örnek aralığının süresine son iki örnekte gözlenen değerler arasındaki farkı görüntüler.|  
|**Uygulama etki alanları kaldırıldığında oranı**|Saniye başına yüklenmemiş bir uygulama etki alanları sayısını görüntüler. Bu sayaç ortalama zaman içinde değil; örnek aralığının süresine son iki örnekte gözlenen değerler arasındaki farkı görüntüler.|  
|**Derlemeleri oranı**|Başına yüklenen derlemelerin sayısını, tüm uygulama etki alanları arasında ikinci görüntüler. Derlemenin birden çok uygulama etki alanından etki alanı nötr olarak yüklenirse, bu sayaç yalnızca bir kez artırılır.<br /><br /> Bu sayaç ortalama zaman içinde değil; örnek aralığının süresine son iki örnekte gözlenen değerler arasındaki farkı görüntüler.|  
|**Yüklenen sınıfların oranı**|Tüm derlemeleri saniye başına yüklenen sınıfların sayısını görüntüler. Bu sayaç ortalama zaman içinde değil; örnek aralığının süresine son iki örnekte gözlenen değerler arasındaki farkı görüntüler.|  
|**Yükleme hataları oranı**|Yüklenemedi sınıfların sayısını görüntüler saniye başına. Bu sayaç ortalama zaman içinde değil; örnek aralığının süresine son iki örnekte gözlenen değerler arasındaki farkı görüntüler.<br /><br /> Yükleme hataları, yetersiz güvenlik ya da geçersiz biçim gibi birçok nedenden dolayı ortaya çıkabilir. Profil Oluşturma Hizmetleri Yardımı Ayrıntılar için bkz.|  
|**Yükleme hataları toplam sayısı**|Uygulama başladıktan sonra yüklemek için başarısız olan sınıfları en yüksek sayısını görüntüler.<br /><br /> Yükleme hataları, yetersiz güvenlik ya da geçersiz biçim gibi birçok nedenden dolayı ortaya çıkabilir. Profil Oluşturma Hizmetleri Yardımı Ayrıntılar için bkz.|  
|**Toplam uygulama etki alanları**|Uygulamanın başlatılmasından bu yana yüklenen uygulama etki alanlarının en yüksek sayısını görüntüler.|  
|**Yüklenmemiş toplam uygulama etki alanları**|Uygulama etki alanları uygulama başladıktan sonra kaldırıldığında toplam sayısını görüntüler. Bu sayaç, bir uygulama etki alanına yüklendiğinde ve birden çok kez kaldırıldığında, uygulama etki alanı kaldırılmadan her zaman artırır.|  
|**Toplam derlemeleri**|Uygulamanın başlatılmasından bu yana yüklenen derlemeler toplam sayısını görüntüler. Derlemenin birden çok uygulama etki alanından etki alanı nötr olarak yüklenirse, bu sayaç yalnızca bir kez artırılır.|  
|**Yüklenen Toplam sınıfları**|Tüm derlemelerde yüklenen sınıfların toplam sayısı, uygulamanın başlatılmasından bu yana görüntüler.|  
  
<a name="lockthread"></a>   
## <a name="lock-and-thread-performance-counters"></a>Kilit ve iş parçacığı performans sayaçları  
 Performans konsolu .NET CLR LocksAndThreads kategorisi yönetilen kilitleri hakkında bilgiler sağlayan sayaçları ve bir uygulamanın kullandığı iş parçacıklarını içerir. Aşağıdaki tabloda, bu performans sayaçları açıklanmaktadır.  
  
|Performans sayacı|Açıklama|  
|-------------------------|-----------------|  
|**Geçerli mantıksal iş parçacığı sayısı**|Uygulama geçerli yönetilen iş parçacığı nesneleri sayısını görüntüler. Bu sayaç, her iki çalışan sayısını tutar ve iş parçacığı durduruldu. Bu sayaç ortalama zaman içinde değil; Bu, yalnızca son görülen değeri görüntüler.|  
|**Geçerli fiziksel iş parçacığı sayısı**|Oluşturulan ve yönetilen iş parçacığı nesneleri için temel iş parçacıklarını olarak davranmak üzere ortak dil çalışma zamanı tarafından sahip olunan yerel işletim sistemi iş parçacığı sayısını görüntüler. Bu sayacın değeri dahili alt işlemlerin çalışma zamanı tarafından kullanılan iş parçacıklarının içermez; Bu işletim sistemi işlemdeki iş parçacıkları bir alt kümesidir.|  
|**tanınan geçerli iş parçacığı sayısı**|Şu anda çalışma zamanı tarafından tanınan iş parçacığı sayısını görüntüler. Bu iş parçacıkları, karşılık gelen bir yönetilen iş parçacığı nesnesi ile ilişkilendirilmiş. Çalışma zamanı bu iş parçacıkları oluşturmaz, ancak çalışma zamanı içinde en az bir kez çalıştırdığınız.<br /><br /> Yalnızca benzersiz iş parçacıkları izlenen; çalışma zamanı yeniden girin ya da iş parçacığı çıktıktan sonra yeniden iş parçacığı ile aynı iş parçacığı kimliği iki kez sayılmaz.|  
|**Toplam tanınan iş parçacığı sayısı**|Toplam uygulama başladıktan sonra çalışma zamanı tarafından tanınan iş parçacığı sayısını görüntüler. Bu iş parçacıkları, karşılık gelen bir yönetilen iş parçacığı nesnesi ile ilişkilendirilmiş. Çalışma zamanı bu iş parçacıkları oluşturmaz, ancak çalışma zamanı içinde en az bir kez çalıştırdığınız.<br /><br /> Yalnızca benzersiz iş parçacıkları izlenen; çalışma zamanı yeniden girin ya da iş parçacığı çıktıktan sonra yeniden iş parçacığı ile aynı iş parçacığı kimliği iki kez sayılmaz.|  
|**Çakışma oranı / sn**|Çalışma zamanında iş parçacığı yönetilen başarısız kilit girişimi hızını görüntüler.|  
|**Geçerli kuyruk uzunluğu**|Uygulama yönetilen bir kilidi almak için şu anda bekleyen iş parçacıklarının toplam sayısını görüntüler. Bu sayaç ortalama zaman içinde değil; Bu, son görülen değeri görüntüler.|  
|**Kuyruk uzunluğu / sn**|Uygulamada kilit için bekleyen iş parçacığı saniyede sayısını görüntüler. Bu sayaç ortalama zaman içinde değil; örnek aralığının süresine son iki örnekte gözlenen değerler arasındaki farkı görüntüler.|  
|**Kuyruk uzunluğu en yüksek**|Uygulama başladıktan sonra yönetilen bir kilidi için beklenen iş parçacığı toplam sayısını görüntüler.|  
|**hızı tanınan iş parçacığı sayısı / sn**|Çalışma zamanı tarafından tanınan saniye başına iş parçacığı sayısını görüntüler. Bu iş parçacıkları, karşılık gelen bir yönetilen iş parçacığı nesnesi ile ilişkilendirilmiş. Çalışma zamanı bu iş parçacıkları oluşturmaz, ancak çalışma zamanı içinde en az bir kez çalıştırdığınız.<br /><br /> Yalnızca benzersiz iş parçacıkları izlenen; çalışma zamanı yeniden girin ya da iş parçacığı çıktıktan sonra yeniden iş parçacığı ile aynı iş parçacığı kimliği iki kez sayılmaz.<br /><br /> Bu sayaç ortalama zaman içinde değil; örnek aralığının süresine son iki örnekte gözlenen değerler arasındaki farkı görüntüler.|  
|**Toplam Çekişme sayısı**|Çalışma zamanında iş parçacığı yönetilen başarısız kilit denemesi yaptınız toplam sayısını görüntüler.|  
  
<a name="memory"></a>   
## <a name="memory-performance-counters"></a>Bellek performans sayaçları  
 Performans konsolu .NET CLR bellek kategorisi çöp toplayıcısı hakkında bilgi sağlayan sayaçlar içerir. Aşağıdaki tabloda, bu performans sayaçları açıklanmaktadır.  
  
|Performans sayacı|Açıklama|  
|-------------------------|-----------------|  
|**# Tüm yığınlardaki bayt**|Toplamını görüntüler **Gen 1 yığın boyutu**, **Gen 2 yığın boyutu**, ve **büyük nesne yığın boyutu** sayaçları. Bu sayaç bayt çöp toplama üzerinde ayrılmış bellek gösterir yığınlar.|  
|**# GC işleme**|Çöp toplama göstergelerinin geçerli sayısını kullanımda görüntüler. Çöp toplama göstergeleri, ortak dil çalışma zamanı ve yönetilen ortam için dış kaynaklara tanıtıcılarıdır.|  
|**# Gen 0 toplamaları sayısı**|Nesil 0 (diğer bir deyişle, yeni, en son ayrılmış nesneleri) uygulama başladıktan sonra atık nesnelerdir sayısını görüntüler.<br /><br /> Nesil 0 çöp toplama, nesil 0'daki bellek ayırma isteğini karşılamak için yeterli olmadığında gerçekleşir. Bu sayaç, bir nesil 0 çöp toplamanın sonunda artırılır. Daha yüksek. nesil atık toplama, tüm alt nesil koleksiyonlar içerir. Bu sayaç, daha yüksek bir nesil (nesil 1 veya 2) çöp toplama oluştuğunda açık olarak artırılır.<br /><br /> Bu sayaç gözlenen son değeri görüntüler. **Sadece _Global\_**  sayaç değeri doğru değildir ve yoksayılmalıdır.|  
|**# Gen 1 toplamaları sayısı**|Uygulama başladıktan sonra atık kuşak 1 nesnelerinin olduğu durumlar sayısını görüntüler.<br /><br /> Kuşaktaki 1 atık toplama sonunda sayaç artırılır. Daha yüksek. nesil atık toplama, tüm alt nesil koleksiyonlar içerir. Bu sayaç, daha yüksek bir nesil (2. nesil) çöp toplama oluştuğunda açık olarak artırılır.<br /><br /> Bu sayaç gözlenen son değeri görüntüler. **Sadece _Global\_**  sayaç değeri doğru değildir ve yoksayılmalıdır.|  
|**# Gen 2 toplamaları sayısı**|2. nesil nesneler uygulama başladıktan sonra atık olduğu durumlar sayısını görüntüler. (Tam çöp toplama olarak da bilinir) bir nesil 2 çöp toplamanın sonunda sayaç artırılır.<br /><br /> Bu sayaç gözlenen son değeri görüntüler. **Sadece _Global\_**  sayaç değeri doğru değildir ve yoksayılmalıdır.|  
|**# Uyarılmış GC**|Çöp toplama işleminin gerçekleştirildiği için açık çağrı nedeniyle sürelerini en yüksek sayısını görüntüler <xref:System.GC.Collect%2A?displayProperty=nameWithType>. Çöp toplayıcı koleksiyonları sıklığını ayarlamak izin vermek için iyi bir uygulamadır.|  
|**Sabitlenen nesne sayısı**|Son çöp toplamada karşılaştı Sabitlenen nesne sayısını görüntüler. Sabitlenen nesne bellekte çöp toplayıcı taşınamıyor bir nesnedir. Bu sayaç, çöp olarak toplanacak olan yığınlar sabitlenmiş nesneleri izler. Örneğin, nesil 0 çöp toplamanın sabitlenmiş nesne numaralandırma yalnızca nesil 0 yığınında neden olur.|  
|**kullanılan havuz blokları sayısı**|Geçerli eşitleme blokların sayısı kullanımda görüntüler. Eşitleme, eşitleme bilgileri depolamak için ayrılan nesne başına veri yapılarını taşlarıdır. Zayıf başvurular yönetilen nesnelere ve çöp toplayıcısı tarafından taranan oldukları. Eşitleme blokları eşitleme bilgileri depolamak için sınırlı değildir; bunlar da COM birlikte çalışma meta verileri depolayabilirsiniz. Bu sayaç, performans sorunları yoğun eşitleme temellerine kullanımını gösterir.|  
|**# Toplam kaydedilmiş bayt**|Şu anda çöp toplayıcı tarafından kaydedilmiş bayt sanal bellek miktarını görüntüler. Kaydedilmiş bellek, disk disk belleği dosyasında alan ayrılmış fiziksel bellektir.|  
|**# Toplam bayt ayrılmış**|Sanal bellek miktarı, şu anda çöp toplayıcısının ayrılan bayt cinsinden görüntüler. Hiçbir disk veya ana bellek sayfalarının kullanıldığı zaman ayrılmış bellek sanal bellek uygulama için ayrılmış bir alandır.|  
|**Gc'de zaman**|Son çöp toplama döngüsünden beri çöp toplamaya harcanan süre yüzdesini görüntüler. Bu sayaç, genellikle Uygulama adına toplama ve compact belleğe çöp toplayıcı tarafından çalışmanın gösterir. Bu sayaç yalnızca her çöp toplamanın sonunda güncelleştirilir. Bu sayaç, ortalama değil; değerini son görülen değeri yansıtır.|  
|**Ayrılan bayt/saniye**|Çöp koleksiyonu yığınında ayrılmış saniye başına bayt sayısını görüntüler. Bu sayaç her ayırma zaman her çöp toplama işleminin sonunda güncelleştirilir. Bu sayaç ortalama zaman içinde değil; örnek aralığının süresine son iki örnekte gözlenen değerler arasındaki farkı görüntüler.|  
|**Sonlandırma Survivor**|Sonlandırılmayı bekleyen bulunduğundan bir toplamadan atık olarak toplanmış nesne sayısını görüntüler. Bu nesneleri diğer nesnelere başvurular tutarsanız, bu nesneler de varlığını sürdürmesini ancak bu sayaç tarafından sayılmaz. **Sonlandırma bellek yükseltilen Gen 0'dan** sayaç sonlandırılması nedeniyle kurtulan tüm belleği temsil eder.<br /><br /> Bu sayaç, toplu değil; yalnızca bu belirli toplama sırasında sayısını Dışarıda Kalanlar, her çöp toplama işleminin sonunda güncelleştirilir. Bu sayaç, uygulama sonlandırılması nedeniyle neden olabilecek ek yükü gösterir.|  
|**Gen 0 yığın boyutu**|Nesil 0 ayrılabilecek en fazla bayt görüntüler. Geçerli nesil 0 ayrılan bayt sayısı göstermez.<br /><br /> Bir nesil 0 çöp toplamanın ayırmaları son toplamadan beri bu boyutunu aşan oluşur. Nesil 0 boyutu çöp toplayıcı tarafından ayarlanmıştır ve uygulamanın yürütülmesi sırasında değiştirebilirsiniz. Bir nesil 0 toplama boyutu nesil sonunda 0 yığın 0 bayt'tır. Bu sayaç, İleri nesil 0 çöp toplamanın çağıran ayırmaları bayt cinsinden boyutunu görüntüler.<br /><br /> Bu sayaç her ayırma zaman bir atık toplama sonunda güncelleştirilir.|  
|**Gen 0 bayt/sn yükseltildi**|Saniye başına 1. nesil için nesil 0 ' yükseltilen bayt görüntüler. Bu bir atık toplama devam eder, bellek yükseltilir. Bu sayacı, saniye başına oluşturulan görece uzun süreli nesnelerin bir göstergesidir.<br /><br /> Bu sayaç, örnek aralığının süresine son iki örnekte gözlenen değerler arasındaki farkı görüntüler.|  
|**Gen 1 yığın boyutu**|Geçerli bayt sayısı, 1. nesil görüntüler. Bu sayaç, 1. kuşak en büyük boyutunu görüntülemez. Nesneleri doğrudan bu nesilde atanmayacağı; Bunlar, önceki nesil 0 çöp koleksiyonları yükseltilir. Bu sayaç her ayırma zaman bir atık toplama sonunda güncelleştirilir.|  
|**Gen 1 bayt/sn yükseltildi**|Saniye başına 2. nesil için nesil 1 ' yükseltilir bayt görüntüler. Sonlandırılmayı yalnızca bekleyen çünkü yükseltilir nesneler bu sayaca dahil edilmez.<br /><br /> Bu bir atık toplama devam eder, bellek yükseltilir. Eski nesil olduğundan hiçbir şey 2. yükseltilir. Bu sayacı, saniye başına oluşturulan çok uzun süreli nesnelerin bir göstergesidir.<br /><br /> Bu sayaç, örnek aralığının süresine son iki örnekte gözlenen değerler arasındaki farkı görüntüler.|  
|**Gen 2 yığın boyutu**|Geçerli bayt sayısı, kuşak 2 görüntüler. Nesneleri doğrudan bu nesilde atanmayacağı; önceki nesil 1 atık toplama sırasında nesil 1'den yükseltilir. Bu sayaç her ayırma zaman bir atık toplama sonunda güncelleştirilir.|  
|**Büyük nesne yığın boyutu**|Büyük nesne yığını bayt cinsinden geçerli boyutu, görüntüler. Yaklaşık 85.000 bayt değerinden daha büyük olan nesneler büyük nesneler çöp toplayıcısı tarafından kabul edilir ve doğrudan özel bir yığında ayrılır; nesiller yükseltilen değil. Bu sayaç her ayırma zaman bir atık toplama sonunda güncelleştirilir.|  
|**İşlem kimliği**|İzlenmekte olan CLR işlem örneği işlem Kimliğini görüntüler.|  
|**Gen 0'dan yükseltilen sonlandırma-bellek**|Sonlandırılmayı yalnızca bekleyen olduğundan, nesil 0 ' 1 yeni nesle yükseltilir bayt bellek görüntüler. Bu sayaç, toplu değil; Bu, son çöp toplamanın sonunda gözlemlenen değeri görüntüler.|  
|**Gen 0'dan yükseltilen bellek**|Çöp toplamadan ve nesil 0 ' 1 yeni nesle yükseltilir bayt bellek görüntüler. Sonlandırılmayı yalnızca bekleyen çünkü yükseltilir nesneler bu sayaca dahil edilmez. Bu sayaç, toplu değil; Bu, son çöp toplamanın sonunda gözlemlenen değeri görüntüler.|  
|**Yükseltilen bellekten Gen 1**|Nesil 1 ' 2. nesil için yükseltilir ve çöp toplamadan bayt bellek görüntüler. Sonlandırılmayı yalnızca bekleyen çünkü yükseltilir nesneler bu sayaca dahil edilmez. Bu sayaç, toplu değil; Bu, son çöp toplamanın sonunda gözlemlenen değeri görüntüler. Bu sayaç, bir nesil 0 toplama yalnızca son çöp toplama ise 0 olarak sıfırlanır.|  
  
<a name="networking"></a>   
## <a name="networking-performance-counters"></a>Ağ performans sayaçları  
 Performans konsolu .NET CLR ağ kategorisinin uygulamanın gönderir ve ağ üzerinden gelen verileri hakkında bilgiler sağlayan sayaçlar içerir. Aşağıdaki tabloda, bu performans sayaçları açıklanmaktadır.  
  
|Performans sayacı|Açıklama|  
|-------------------------|-----------------|  
|**Alınan bayt sayısı**|Tüm tarafından alınan bayt sayısı, toplam birikimli sayısını <xref:System.Net.Sockets.Socket> içindeki nesneleri <xref:System.AppDomain> işlemi başladıktan sonra. Bu sayı, verileri ve TCP/IP'yi tarafından tanımlı değil tüm Protokolü bilgileri içerir.|  
|**Gönderilen bayt sayısı**|Tüm tarafından gönderilen bayt birikimli sayısını <xref:System.Net.Sockets.Socket> içindeki nesneleri <xref:System.AppDomain> işlemi başladıktan sonra. Bu sayı, verileri ve TCP/IP'yi tarafından tanımlı değil tüm Protokolü bilgileri içerir.|  
|**Kurulan bağlantılar**|Toplam toplam sayısı <xref:System.Net.Sockets.Socket> nesneler içinde hiç bağlı Akış yuvaları için <xref:System.AppDomain> işlemi başladıktan sonra.|  
|**Alınan veri birimi sayısı**|Veri birimi paketler tarafından alınan toplam birikimli sayısını <xref:System.Net.Sockets.Socket> içindeki nesneleri <xref:System.AppDomain> işlemi başladıktan sonra.|  
|**Gönderilen veri birimi**|Veri birimi paketler tarafından gönderilen toplam birikimli sayısını <xref:System.Net.Sockets.Socket> içindeki nesneleri <xref:System.AppDomain> işlemi başladıktan sonra.|  
|**HttpWebRequest ortalama yaşam süresi**|Tüm tamamlanması için ortalama süre <xref:System.Net.HttpWebRequest> içinde son aralığı sona erdi nesneleri <xref:System.AppDomain> işlemi başladıktan sonra.|  
|**HttpWebRequest ortalama kuyruk süresi**|Ortalama üzerinde sıraya süresi tüm <xref:System.Net.HttpWebRequest> sıra içinde son aralığında kalan nesneler <xref:System.AppDomain> işlemi başladıktan sonra.|  
|**Oluşturulan HttpWebRequests/sn**|Sayısını <xref:System.Net.HttpWebRequest> içinde saniye başına oluşturulan nesneleri <xref:System.AppDomain>.|  
|**Kuyruğa Alınan HttpWebRequests/sn**|Sayısını <xref:System.Net.HttpWebRequest> içinde saniyede sıraya eklenen nesneleri <xref:System.AppDomain>.|  
|**İptal HttpWebRequests/sn**|Sayısını <xref:System.Net.HttpWebRequest> burada uygulama adı verilen nesneleri <xref:System.Net.HttpWebRequest.Abort%2A> yöntemi içinde saniyede <xref:System.AppDomain>.|  
|**Başarısız HttpWebRequests/sn**|Sayısını <xref:System.Net.HttpWebRequest> sunucudan saniye içinde başına başarısız durum kodu alındı nesneleri <xref:System.AppDomain>.|  
  
 Ağ performans sayaçları desteklenen çeşitli sınıfı vardır:  
  
-   Olay sayaçları, bazı olay sayısını ölçer.  
  
-   Gönderilen veya alınan veri miktarı ölçen verileri sayaçları.  
  
-   Ne kadar süreyle farklı süreçlerini ölçen sayaçları süresi yararlanın. Nesnelerde süreleri ölçülür her zaman aralığını (genellikle saniye) farklı durumlar dışında geldikleri sonra.  
  
-   Belirli bir yapan nesne sayısını ölçmek aralığı başına sayaçları (normalde saniyede) aralığı başına işleme geçiş.  
  
 Ağ performans sayaçları olayları için şunları içerir:  
  
-   **Kurulan bağlantılar**  
  
-   **Alınan veri birimi sayısı**  
  
-   **Gönderilen veri birimi**  
  
 İşlem başlatıldığından bu yana bu performans sayaçlarını sayımları sağlar. Sayısı <xref:System.Net.Sockets.Socket> kurulan bağlantılar içeren açık <xref:System.Net.Sockets.Socket> olan akış yuva diğer sınıfları tarafından yapılan de internal olarak çağrıları ile bağlantı için bir uygulama tarafından yöntemini çağırır (<xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.WebClient>, ve <xref:System.Net.Sockets.TcpClient>, örneğin) için <xref:System.Net.Sockets.Socket> sınıfı  
  
 Sayıları **alınıp** ve **veri birimi gönderilen** gönderilen veya alınan açık kullanarak veri birimi paketleri içerir <xref:System.Net.Sockets.Socket> yöntemi çağıran bir uygulama ile yapılan iyi iç çağrıları olarak sınıflar (<xref:System.Net.Sockets.UdpClient>, örneğin) için <xref:System.Net.Sockets.Socket>. sınıf. Sayıları **alınıp** ve **veri birimi gönderilen** kaç bayt gönderilen veya alınan bir veri birimi için bir ortalama boyutu üstlenerek veri birimlerini kullanarak çok kaba bir ölçü sağlamak için de kullanılabilir.  
  
 Ağ performans sayaçları veriler için aşağıdakileri içerir:  
  
-   **Alınan bayt sayısı**  
  
-   **Gönderilen bayt sayısı**  
  
 İşlem başlatıldığından bu yana yukarıdaki sayaçları bayt sayısını sağlar.  
  
 Ne kadar sürdüğünü izleyen iki süresi sayaçları vardır <xref:System.Net.HttpWebRequest> aracılığıyla kendi ömrü geçirilecek nesneleri döngüsü veya sadece bu parçası:  
  
-   **HttpWebRequest ortalama yaşam süresi**  
  
-   **HttpWebRequest ortalama kuyruk süresi**  
  
 İçin **HttpWebRequest ortalama yaşam süresi** sayacı, çoğu kullanım ömrünü <xref:System.Net.HttpWebRequest> nesneleri uygulamanın yanıt akışına kapalı zaman gönderinizi nesne oluşturulduktan zaman ile her zaman başlar. Genel olmayan iki durum vardır:  
  
-   Uygulamanın hiçbir zaman çağırırsa <xref:System.Net.HttpWebRequest.GetResponse%2A> veya <xref:System.Net.HttpWebRequest.BeginGetResponse%2A> yöntemleri ve ardından ömrünü <xref:System.Net.HttpWebRequest> nesne göz ardı edilir.  
  
-   Varsa <xref:System.Net.HttpWebRequest> nesnesi oluşturur bir <xref:System.Net.WebException> çağırırken <xref:System.Net.HttpWebRequest.GetResponse%2A> veya <xref:System.Net.HttpWebRequest.EndGetResponse%2A> yöntemleri ömrü sona erer özel durum oluştuğunda. Teknik olarak, temel alınan yanıt akış da bu noktada kapalı (kullanıcı tarafından döndürülen yanıt akışına yanıt akışına bir kopyasını içeren bir bellek akış gerçekten değer).  
  
 Belirli izleme dört sayaç vardır <xref:System.Net.HttpWebRequest> aralığı başına işleme sorunları nesne. Uygulama geliştiricileri, Yöneticiler, bu performans sayaçlarını yardımcı olabilir ve destek personeli daha iyi anlamak ne <xref:System.Net.HttpWebRequest> nesneleri yapıyor. Sayaçlar aşağıdakileri içerir:  
  
-   **Oluşturulan HttpWebRequests/sn**  
  
-   **Kuyruğa Alınan HttpWebRequests/sn**  
  
-   **İptal HttpWebRequests/sn**  
  
-   **Başarısız HttpWebRequests/sn**  
  
 İçin **HttpWebRequests iptal edildi/sn** sayaç, dahili çağrıları <xref:System.Net.HttpWebRequest.Abort%2A> de sayılır. Bu iç çağrıları, genellikle uygulamanın ölçmek istediğiniz zaman aşımları tarafından neden olur.  
  
 **HttpWebRequests başarısız/sn** sayacı sayısını içerir <xref:System.Net.HttpWebRequest> sunucudan saniye başına başarısız durum alındı nesneleri kod. Bu istek sonunda Http sunucusundan alınan durum kodu 200 için 299 aralığında anlamına gelir. İşlenir ve (örneğin 401 yetkilendirilmedi durum kodlarını birçoğu) başarısız veya başarısız deneme sonucuna bağlı olmayan yeni bir istek neden durum kodları. Ardından, uygulamayı yeniden denemede dayalı olarak bir hata göreceğiniz, bu sayaç artırılır.  
  
 Ağ performans sayaçları, erişilebilir ve yönetilen kullanarak <xref:System.Diagnostics.PerformanceCounter> ve ilgili sınıflar <xref:System.Diagnostics> ad alanı. Ağ performans sayaçları Windows Performans İzleyicisi'ni konsoluyla birlikte görüntülenebilir.  
  
 Ağ performans sayaçları yapılandırma dosyasında kullanılacak etkinleştirilmesi gerekir. Tüm ağ performans sayaçları etkin veya yapılandırma dosyasında tek bir ayarı ile devre dışı. Ağ performans sayaçları tek etkin veya devre dışı. Daha fazla bilgi için [ \<performanceCounter > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/performancecounter-element-network-settings.md).  
  
 Ağ sayaçları etkinleştirilirse, bu oluşturun ve hem AppDomain başına hem de genel performans sayaçları güncelleştirin. Devre dışı bırakılırsa, uygulama ağ performans sayacı verisi sağlamaz.  
  
 Performans sayaçları, kategoriler halinde gruplandırılır. Bir uygulama, aşağıdaki kod örneği ile kategorilerin tümünü listeleyebilirsiniz:  
  
```  
PerformanceCounterCategory[] Array = PerformanceCounterCategory.GetCategories();  
for (int i = 0; i < Array.Length; i++)  
{  
    Console.Out.WriteLine("{0}. Name={1} Help={2}", i, Array[i].CategoryName, Array[i].CategoryHelp);  
}  
```  
  
 Ağ performans sayaçları, iki kategoride listelenmiştir:  
  
-   ".NET CLR - özgün ağ performans sayaçları sunulan .NET Framework sürüm 2 ve .NET Framework sürüm 2'de desteklenir ve daha sonra".  
  
-   ".NET CLR ağ 4.0.0.0" - Yukarıdaki yuva tüm yeni performans desteklenen .NET Framework sürüm 4 ve üzeri sayaçları. Bu yeni sayaçları performans bilgilerini sağlamaları <xref:System.Net.HttpWebRequest> nesneleri.  
  
 Erişim ve uygulamada performans sayaçları hakkında daha fazla bilgi için bkz. [performans sayaçları](../../../docs/framework/debug-trace-profile/performance-counters.md).  
  
<a name="security"></a>   
## <a name="security-performance-counters"></a>Güvenlik performans sayaçları  
 Performans konsolu .NET CLR güvenlik kategorisi, ortak dil çalışma zamanı'nın bir uygulama için gerçekleştirdiği denetimleri güvenlik hakkında bilgi sağlayan sayaçlar içerir. Aşağıdaki tabloda, bu performans sayaçları açıklanmaktadır.  
  
|Performans sayacı|Açıklama|  
|-------------------------|-----------------|  
|**# Bağlantı zamanı denetimleri**|Görüntüler, uygulamanın başlatılmasından bu yana bağlama zamanı kod erişim güvenliği toplam sayısını denetler. Bağlama zamanı kod erişim güvenliği denetimlerini, bir çağıranın tam zamanında (JIT) derleme zamanında belirli bir izin talep ettiğinde gerçekleştirilir. Bağlama zamanı onay arayan bir kez gerçekleştirilir. Bu sayı ciddi performans sorunlarını göstergesi değil; yalnızca güvenlik sistem etkinliğini gösterir.|  
|**RT denetimleri harcanan % zaman**|Son örnekten beri geçen süre çalışma zamanı kod erişim güvenlik denetimleri gerçekleştirme yüzdesini görüntüler. Bu sayaç, bir .NET Framework güvenlik denetimi sonunda güncelleştirilir. Ortalama bir değer değil; Bu, son görülen değeri temsil eder.|  
|**% Sig zaman kimlik doğrulaması**|Daha sonraki kullanımlar için ayrılmıştır.|  
|**Yığın ilerlemesi derinliği**|Yığın derinliği, son çalışma zamanı kod erişim güvenlik denetimi sırasında görüntüler. Çalışma zamanı kod erişim güvenlik denetimleri, yığın walking tarafından gerçekleştirilir. Bu sayaç, ortalama değil; Bu, yalnızca son görülen değeri görüntüler.|  
|**Toplam çalışma zamanı denetimleri**|Toplam çalışma zamanı kod erişim güvenlik denetimlerini uygulama başladıktan sonra gerçekleştirilen görüntüler. Çalışma zamanı kod erişim güvenlik çağıran bir özel izin talep ettiğinde önleme denetimleri yapıldıktan. Çalışma zamanı denetimi her çağrıda arayan tarafından oluşturulur ve geçerli iş parçacığı yığınının arayanın inceler. İle kullanıldığında **Yığın derinliği yol** sayaç, bu sayaç, güvenlik denetimleri için ortaya çıkan performans cezası gösterir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans Sayaçları](../../../docs/framework/debug-trace-profile/performance-counters.md)  
 [Çalışma Zamanı Profili Oluşturma](../../../docs/framework/debug-trace-profile/runtime-profiling.md)
