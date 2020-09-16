---
title: .NET Framework'teki Performans Sayaçları
description: .NET 'teki performans sayaçları hakkında bilgi edinin. Özel durumlar, birlikte çalışabilirlik, JıT derleyiciler, yükleme, bellek, ağ, güvenlik ve daha fazlası için performans sayaçları vardır.
ms.date: 03/30/2017
helpviewer_keywords:
- performance, .NET Framework applications
- performance counters
- performance monitoring, counters
ms.assetid: 06a4ae8c-eeb2-4d5a-817e-b1b95c0653e1
ms.openlocfilehash: 1b5ca6484f45dcee33009d8b8c12a43fa41f63de
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554455"
---
# <a name="performance-counters-in-the-net-framework"></a>.NET Framework performans sayaçları

Bu konu, [Windows Performans İzleyicisi](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc749249(v=ws.11))'nde bulabileceğiniz performans sayaçlarının bir listesini sağlar.  

## <a name="exception-performance-counters"></a>Özel durum performans sayaçları  
 Performans konsolu .NET CLR özel durumları kategorisi, bir uygulama tarafından oluşturulan özel durumlar hakkında bilgi sağlayan sayaçlar içerir. Aşağıdaki tabloda bu performans sayaçları açıklanmaktadır.  
  
|Performans sayacı|Description|  
|-------------------------|-----------------|  
|**Atılan Exceps sayısı**|Uygulama başladıktan sonra oluşturulan toplam özel durum sayısını görüntüler. Bu hem .NET özel durumlarını hem de .NET özel durumlarına dönüştürülmüş yönetilmeyen özel durumları içerir. Örneğin, yönetilmeyen koddan döndürülen bir HRESULT, Yönetilen koddaki özel duruma dönüştürülür.<br /><br /> Bu sayaç hem işlenmiş hem de işlenmemiş özel durumları içerir. Yeniden oluşturulan özel durumlar tekrar sayılır.|  
|**Oluşturulan Exceps sayısı/sn**|Saniye başına oluşturulan özel durumların sayısını görüntüler. Bu hem .NET özel durumlarını hem de .NET özel durumlarına dönüştürülmüş yönetilmeyen özel durumları içerir. Örneğin, yönetilmeyen koddan döndürülen bir HRESULT, Yönetilen koddaki özel duruma dönüştürülür.<br /><br /> Bu sayaç hem işlenmiş hem de işlenmemiş özel durumları içerir. Bu, zaman içinde bir ortalama değildir; Son iki örnekte gözlenen değerler arasındaki farkı örnek aralığın süresine göre gösterir. Bu sayaç, büyük bir (>100s) özel durum sayısı oluşturulursa olası performans sorunlarının göstergesidir.|  
|**Filtre sayısı/sn**|Saniye başına yürütülen .NET özel durum filtrelerinin sayısını görüntüler. Özel durum filtresi, bir özel durumun işlenmiş olup olmamasından bağımsız olarak değerlendirilir.<br /><br /> Bu sayaç, zaman içinde bir ortalama değil; Son iki örnekte gözlenen değerler arasındaki farkı örnek aralığın süresine göre gösterir.|  
|**Finallys sayısı/sn**|Saniye başına yürütülen son blok sayısını görüntüler. Try bloğunun çıkış şeklinden bağımsız olarak bir finally bloğunun yürütülmesi garanti edilir.  Yalnızca bir özel durum için yürütülen finally blokları sayılır; normal kod yollarındaki son bloklar Bu sayaç tarafından sayılmaz.<br /><br /> Bu sayaç, zaman içinde bir ortalama değil; Son iki örnekte gözlenen değerler arasındaki farkı örnek aralığın süresine göre gösterir.|  
|**Catch derinliğine/sn 'ye throw**|Özel durumu, saniye başına işlenen çerçeveye özel durum veren kareden geçen yığın çerçevelerinin sayısını görüntüler. Bir özel durum işleyicisi girildiğinde bu sayaç sıfıra sıfırlanır, bu yüzden iç içe geçmiş özel durumlar işleyicinin işleyici yığın derinliğini gösterir.<br /><br /> Bu sayaç, zaman içinde bir ortalama değil; Son iki örnekte gözlenen değerler arasındaki farkı örnek aralığın süresine göre gösterir.|  

## <a name="interop-performance-counters"></a>Birlikte çalışabilirlik performans sayaçları  
 Performans konsolu .NET CLR birlikte çalışma kategorisi, bir uygulamanın COM bileşenleri, COM+ Hizmetleri ve dış tür kitaplıklarıyla etkileşimi hakkında bilgi sağlayan sayaçlar içerir. Aşağıdaki tabloda bu performans sayaçları açıklanmaktadır.  
  
|Performans sayacı|Description|  
|-------------------------|-----------------|  
|**CCWs sayısı**|Geçerli COM çağrılabilir sarmalayıcılarının (CCWs) sayısını görüntüler. Bir CCW, yönetilmeyen bir COM istemcisinden başvurulmakta olan yönetilen bir nesne için bir ara sunucu. Bu sayaç, yönetilmeyen COM kodu tarafından başvurulan yönetilen nesne sayısını gösterir.|  
|**sıralama sayısı**|Bağımsız değişkenlerin ve dönüş değerlerinin yönetilen ve yönetilmeyen koddan kaç kez sıralandığına ve uygulamanın başlamasından bu yana tam tersi gösterir. Saplamalar satır içine alınır ise bu sayaç arttırılır. (Saplamalar, bağımsız değişkenleri ve dönüş değerlerini sıralama sorumludur). Hazırlama ek yükü küçükse, saplamalar genellikle satır içine alınır.|  
|**Saplamalar sayısı**|Ortak dil çalışma zamanı tarafından oluşturulan geçerli saplamalar sayısını görüntüler. Saplamalar, bağımsız değişkenleri sıralama ve yönetilen değerden yönetilmeyen koda döndürme ve bir COM birlikte çalışma çağrısı sırasında veya platform çağırma çağrısı sırasında sorumludur.|  
|**TLB dışarı aktarma sayısı/sn**|Daha sonraki kullanımlar için ayrılmıştır.|  
|**TLB içeri aktarma sayısı/sn**|Daha sonraki kullanımlar için ayrılmıştır.|  

## <a name="jit-performance-counters"></a>JIT performans sayaçları  
 Performans konsolu .NET CLR JıT kategorisi, JıT derlenmiş kod hakkında bilgi sağlayan sayaçlar içerir. Aşağıdaki tabloda bu performans sayaçları açıklanmaktadır.  
  
|Performans sayacı|Description|  
|-------------------------|-----------------|  
|**anında derlenen IL bayt sayısı**|Uygulamanın başlatılmasından bu yana tam zamanında (JıT) derleyici tarafından derlenen Microsoft ara dili (MSIL) baytlarının toplam sayısını görüntüler. Bu sayaç, **derlenen toplam IL bayt sayacı sayısına** eşittir.|  
|**anında derlenen Yöntem sayısı**|Uygulamanın başlatılmasından bu yana JıT ile derlenen yöntemlerin toplam sayısını görüntüler. Bu sayaç önceden JıT ile derlenen yöntemler içermez.|  
|**JIT 'de% Time**|Son JıT derleme aşamasından bu yana JıT derlemesinde harcanan geçen sürenin yüzdesini görüntüler. Bu sayaç her JıT derleme aşamasının sonunda güncelleştirilir. Bir yöntem ve bağımlılıkları derlendiğinde bir JıT derleme aşaması oluşur.|  
|**Anında derlenen IL bayt/sn**|Saniye başına JıT olarak derlenen MSIL bayt sayısını görüntüler. Bu sayaç, zaman içinde bir ortalama değil; Son iki örnekte gözlenen değerler arasındaki farkı örnek aralığın süresine göre gösterir.|  
|**Standart JIT sorunları**|Uygulama başladıktan sonra JıT derleyicisinin derleyemeyeceği en yüksek Yöntem sayısını görüntüler. Bu hata, MSIL doğrulanamazsa veya JıT derleyicisinde bir iç hata varsa meydana gelebilir.|  
|**Anında derlenen toplam IL bayt sayısı**|Uygulamanın başlatılmasından bu yana JıT ile derlenen toplam MSIL bayt sayısını görüntüler. Bu sayaç, derlenen **IL bayt** sayısı ile eşdeğerdir.|  

## <a name="loading-performance-counters"></a>Performans sayaçları yükleniyor  
 Performans konsolu .NET CLR Yükleme kategorisi, yüklenen derlemeler, sınıflar ve uygulama etki alanları hakkında bilgi sağlayan sayaçları içerir. Aşağıdaki tabloda bu performans sayaçları açıklanmaktadır.  
  
|Performans sayacı|Description|  
|-------------------------|-----------------|  
|**Yükleme zamanı yüzdesi**|Daha sonraki kullanımlar için ayrılmıştır.|  
|**Derleme arama uzunluğu**|Daha sonraki kullanımlar için ayrılmıştır.|  
|**Yükleyici yığınındaki baytlar**|Tüm uygulama etki alanları genelinde sınıf yükleyicisi tarafından kaydedilen belleğin bayt cinsinden geçerli boyutunu görüntüler. Kaydedilmiş bellek, disk disk belleği dosyasında ayrılan fiziksel alandır.|  
|**Geçerli AppDomain 'ler**|Bu uygulamada yüklenen uygulama etki alanlarının geçerli sayısını görüntüler.|  
|**Geçerli derlemeler**|O anda çalışan uygulamadaki tüm uygulama etki alanları genelinde yüklenen derlemelerin geçerli sayısını görüntüler. Derleme birden çok uygulama etki alanında etki alanı nötr olarak yüklenirse, bu sayaç yalnızca bir kez artırılır.|  
|**Geçerli sınıflar yüklendi**|Tüm derlemelerde yüklenen sınıfların geçerli sayısını görüntüler.|  
|**AppDomain oranı**|Saniye başına yüklenen uygulama etki alanı sayısını görüntüler. Bu sayaç, zaman içinde bir ortalama değil; Son iki örnekte gözlenen değerler arasındaki farkı örnek aralığın süresine göre gösterir.|  
|**Bellekten kaldırılan AppDomain oranı**|Saniye başına bellekten kaldırılan uygulama etki alanı sayısını görüntüler. Bu sayaç, zaman içinde bir ortalama değil; Son iki örnekte gözlenen değerler arasındaki farkı örnek aralığın süresine göre gösterir.|  
|**Derleme oranı**|Tüm uygulama etki alanlarında saniye başına yüklenen derlemelerin sayısını görüntüler. Derleme birden çok uygulama etki alanında etki alanı nötr olarak yüklenirse, bu sayaç yalnızca bir kez artırılır.<br /><br /> Bu sayaç, zaman içinde bir ortalama değil; Son iki örnekte gözlenen değerler arasındaki farkı örnek aralığın süresine göre gösterir.|  
|**Yüklenen sınıfların oranı**|Tüm derlemelerdeki saniye başına yüklenen sınıfların sayısını görüntüler. Bu sayaç, zaman içinde bir ortalama değil; Son iki örnekte gözlenen değerler arasındaki farkı örnek aralığın süresine göre gösterir.|  
|**Yükleme hatalarının oranı**|Saniye başına yüklenmeyen sınıfların sayısını görüntüler. Bu sayaç, zaman içinde bir ortalama değil; Son iki örnekte gözlenen değerler arasındaki farkı örnek aralığın süresine göre gösterir.<br /><br /> Yetersiz güvenlik veya geçersiz biçim gibi birçok nedenden dolayı yükleme başarısız olabilir. Ayrıntılar için bkz. profil oluşturma Hizmetleri Yardımı.|  
|**Toplam yükleme başarısızlığı sayısı**|Uygulamanın başlatılmasından bu yana yükleme başarısız olan sınıfların en yüksek sayısını görüntüler.<br /><br /> Yetersiz güvenlik veya geçersiz biçim gibi birçok nedenden dolayı yükleme başarısız olabilir. Ayrıntılar için bkz. profil oluşturma Hizmetleri Yardımı.|  
|**Toplam AppDomain**|Uygulamanın başlatılmasından bu yana yüklenen uygulama etki alanlarının en yüksek sayısını görüntüler.|  
|**Bellekten kaldırılan toplam AppDomain**|Uygulama başladıktan sonra bellekten kaldırılan uygulama etki alanlarının toplam sayısını görüntüler. Bir uygulama etki alanı yüklenip birden çok kez kaldırıldığında, bu sayaç uygulama etki alanının her kaldırıldığında artar.|  
|**Toplam derleme sayısı**|Uygulama başladıktan sonra yüklenen derlemelerin toplam sayısını görüntüler. Derleme birden çok uygulama etki alanında etki alanı nötr olarak yüklenirse, bu sayaç yalnızca bir kez artırılır.|  
|**Toplam yüklenen sınıf**|Uygulamanın başlatılmasından bu yana tüm derlemelerde yüklenen sınıfların birikmiş sayısını görüntüler.|  

## <a name="lock-and-thread-performance-counters"></a>Kilit ve iş parçacığı performans sayaçları  
 Performans konsolu .NET CLR LocksAndThreads kategorisi, bir uygulamanın kullandığı yönetilen kilitler ve iş parçacıkları hakkında bilgi sağlayan sayaçları içerir. Aşağıdaki tabloda bu performans sayaçları açıklanmaktadır.  
  
|Performans sayacı|Description|  
|-------------------------|-----------------|  
|**geçerli mantıksal Iş parçacığı sayısı**|Uygulamadaki geçerli yönetilen iş parçacığı nesnelerinin sayısını görüntüler. Bu sayaç hem çalışan hem de durdurulan iş parçacıklarının sayısını tutar. Bu sayaç, zaman içinde bir ortalama değil; yalnızca son gözlemlenen değeri görüntüler.|  
|**geçerli fiziksel Iş parçacığı sayısı**|Yönetilen iş parçacığı nesneleri için temel alınan iş parçacıkları olarak görev yapacak ortak dil çalışma zamanına ait ve oluşturulan yerel işletim sistemi iş parçacıklarının sayısını görüntüler. Bu sayacın değeri, iç işlemlerinde çalışma zamanı tarafından kullanılan iş parçacıklarını içermez; Bu, işletim sistemi işlemindeki iş parçacıklarının bir alt kümesidir.|  
|**geçerli tanınan iş parçacıklarının sayısı**|Çalışma zamanı tarafından şu anda tanınan iş parçacığı sayısını görüntüler. Bu iş parçacıkları karşılık gelen bir yönetilen iş parçacığı nesnesiyle ilişkilendirilir. Çalışma zamanı bu iş parçacıklarını oluşturmaz, ancak çalışma zamanı içinde en az bir kez çalıştırılırlar.<br /><br /> Yalnızca benzersiz iş parçacıkları izlenir; çalışma zamanını yeniden girerek veya iş parçacığının çıktıktan sonra yeniden oluşturulmuş iş parçacığı KIMLIĞINE sahip iş parçacıkları iki kez sayılmaz.|  
|**Toplam tanınan Iş parçacığı sayısı**|Uygulama başlatıldığından bu yana çalışma zamanı tarafından tanınan toplam iş parçacığı sayısını görüntüler. Bu iş parçacıkları karşılık gelen bir yönetilen iş parçacığı nesnesiyle ilişkilendirilir. Çalışma zamanı bu iş parçacıklarını oluşturmaz, ancak çalışma zamanı içinde en az bir kez çalıştırılırlar.<br /><br /> Yalnızca benzersiz iş parçacıkları izlenir; çalışma zamanını yeniden girerek veya iş parçacığının çıktıktan sonra yeniden oluşturulmuş iş parçacığı KIMLIĞINE sahip iş parçacıkları iki kez sayılmaz.|  
|**Çekişme oranı/sn**|Çalışma zamanındaki iş parçacıklarının yönetilen kilidi alma girişimi hızını görüntüler.|  
|**Geçerli kuyruk uzunluğu**|Uygulamada yönetilen bir kilidi almak için bekleyen iş parçacıklarının toplam sayısını görüntüler. Bu sayaç, zaman içinde bir ortalama değil; son gözlenen değeri görüntüler.|  
|**Sıra uzunluğu/sn**|Uygulamada bir kilit elde etmek için bekleyen, saniye başına iş parçacığı sayısını görüntüler. Bu sayaç, zaman içinde bir ortalama değil; Son iki örnekte gözlenen değerler arasındaki farkı örnek aralığın süresine göre gösterir.|  
|**En yüksek kuyruk uzunluğu**|Uygulamanın başlatılmasından bu yana yönetilen bir kilit almayı bekleyen iş parçacıklarının toplam sayısını görüntüler.|  
|**tanınan iş parçacığı oranı/sn**|Bir saniyede çalışma zamanı tarafından tanınan iş parçacığı sayısını görüntüler. Bu iş parçacıkları karşılık gelen bir yönetilen iş parçacığı nesnesiyle ilişkilendirilir. Çalışma zamanı bu iş parçacıklarını oluşturmaz, ancak çalışma zamanı içinde en az bir kez çalıştırılırlar.<br /><br /> Yalnızca benzersiz iş parçacıkları izlenir; çalışma zamanını yeniden girerek veya iş parçacığının çıktıktan sonra yeniden oluşturulmuş iş parçacığı KIMLIĞINE sahip iş parçacıkları iki kez sayılmaz.<br /><br /> Bu sayaç, zaman içinde bir ortalama değil; Son iki örnekte gözlenen değerler arasındaki farkı örnek aralığın süresine göre gösterir.|  
|**Toplam çekişmeler sayısı**|Çalışma zamanındaki iş parçacıklarının yönetilen kilit alma girişimi başarısız olan toplam sayısını görüntüler.|  

## <a name="memory-performance-counters"></a>Bellek performans sayaçları  
 Performans konsolu .NET CLR bellek kategorisi, çöp toplayıcısı hakkında bilgi sağlayan sayaçlar içerir. Aşağıdaki tabloda bu performans sayaçları açıklanmaktadır.  
  
|Performans sayacı|Description|  
|-------------------------|-----------------|  
|**Tüm yığınlardaki bayt sayısı**|**Gen 1 yığın boyutu**, **Gen 2 yığın boyutu**ve **büyük nesne yığın boyutu** sayaçlarının toplamını görüntüler. Bu sayaç, çöp toplama yığınlarında bayt cinsinden ayrılan geçerli belleği gösterir.|  
|**# GC tutamaçları**|Kullanımdaki çöp toplama tanıtıcılarının geçerli sayısını görüntüler. Çöp toplama tutamaçları, ortak dil çalışma zamanı ve yönetilen ortam dışındaki kaynaklara yönelik tanıtıcılardır.|  
|**# Gen 0 toplamaları**|Oluşturma 0 nesnelerinin (yani, kardeşinizin, en son ayrılan nesnelerin), uygulamanın başlatılmasından bu yana atık olarak toplanarak sayısını görüntüler.<br /><br /> Nesil 0, kuşak 0 ' daki kullanılabilir bellek, bir ayırma isteğini karşılamak için yeterli olmadığında oluşur. Bu sayaç, 1. nesil atık toplamanın sonunda artırılır. Daha yüksek kuşak çöp koleksiyonları, tüm düşük nesil koleksiyonları içerir. Bu sayaç, daha yüksek bir oluşturma (1 veya 2. nesil) çöp toplama gerçekleştiğinde açıkça artırılır.<br /><br /> Bu sayaç, son gözlemlenen değeri görüntüler. **_Global \_ ** sayaç değeri doğru değil ve göz ardı edilmelidir.|  
|**# Gen 1 toplamaları**|Uygulamanın başlatılmasından bu yana 1. nesil nesnelerin atık olarak toplandığı kaç kez toplandığını gösterir.<br /><br /> Sayaç, 1. nesil atık toplamanın sonunda artırılır. Daha yüksek kuşak çöp koleksiyonları, tüm düşük nesil koleksiyonları içerir. Bu sayaç, daha yüksek bir oluşturma (2. nesil) atık toplama gerçekleştiğinde açıkça artırılır.<br /><br /> Bu sayaç, son gözlemlenen değeri görüntüler. **_Global \_ ** sayaç değeri doğru değil ve göz ardı edilmelidir.|  
|**Gen 2 toplamaları sayısı**|Uygulamanın başlatılmasından bu yana 2. nesil nesnelerinin çöp toplama sayısını görüntüler. Sayaç, 2. nesil atık toplamanın (tam çöp toplama da denir) sonunda artırılır.<br /><br /> Bu sayaç, son gözlemlenen değeri görüntüler. **_Global \_ ** sayaç değeri doğru değil ve göz ardı edilmelidir.|  
|**Igelemiş GC**|' A açık bir çağrı nedeniyle çöp toplamanın en yoğun sayısını görüntüler <xref:System.GC.Collect%2A?displayProperty=nameWithType> . Atık toplayıcısının koleksiyonların sıklığını ayarlamaya olanak sağlamak iyi bir uygulamadır.|  
|**Sabitlenmiş nesne sayısı**|Son çöp toplama işleminde karşılaşılan sabitlenmiş nesne sayısını görüntüler. Sabitlenmiş nesne, çöp toplayıcısının bellekte taşıyamayacağını belirten bir nesnedir. Bu sayaç, Sabitlenmiş nesneleri yalnızca atık toplanan yığınlardaki izler. Örneğin, nesil 0 çöp toplama, sabitlenmiş nesnelerin yalnızca nesil 0 yığınında numaralandırılmasına neden olur.|  
|**Kullanımdaki havuz bloklarının sayısı**|Kullanımdaki eşitleme bloklarının geçerli sayısını görüntüler. Eşitleme blokları, eşitleme bilgilerini depolamak için ayrılan nesne başına veri yapılarıdır. Bunlar yönetilen nesnelere zayıf başvuruları tutar ve çöp toplayıcı tarafından taranmalıdır. Eşitleme blokları, eşitleme bilgilerini depolamak için sınırlı değildir; Ayrıca, COM birlikte çalışma meta verilerini de saklayabilir. Bu sayaç, eşitleme temel temellerinin yoğun kullanımıyla ilgili performans sorunlarını gösterir.|  
|**Toplam kaydedilmiş bayt sayısı**|Çöp toplayıcı tarafından şu anda işlenen sanal bellek miktarını bayt cinsinden görüntüler. Kaydedilmiş bellek, disk disk belleği dosyasında ayrılan alanın fiziksel belleğidir.|  
|**Toplam ayrılan bayt sayısı**|Çöp toplayıcı tarafından şu anda ayrılmış olan sanal bellek miktarını bayt cinsinden görüntüler. Ayrılan bellek, disk veya ana bellek sayfası kullanılmadığınızda uygulama için ayrılan sanal bellek alanıdır.|  
|**GC 'de% Time**|Son çöp toplama döngüsünden bu yana bir çöp toplama işlemi için harcanan geçen sürenin yüzdesini görüntüler. Bu sayaç genellikle çöp toplayıcı tarafından uygulama adına bellek toplamak ve sıkıştırmak için yapılan işi gösterir. Bu sayaç yalnızca her çöp toplamanın sonunda güncelleştirilir. Bu sayaç bir ortalama değil; değeri, son gözlemlenen değeri yansıtır.|  
|**Ayrılan bayt/saniye**|Çöp toplama yığınında ayrılan saniye başına bayt sayısını görüntüler. Bu sayaç her bir ayırmada değil her çöp toplamanın sonunda güncelleştirilir. Bu sayaç, zaman içinde bir ortalama değil; Son iki örnekte gözlenen değerler arasındaki farkı örnek aralığın süresine göre gösterir.|  
|**Kalan VNET 'leri sonlandırma**|Toplanmayı beklediği için bir koleksiyonun üzerinde kalan atık toplanmış nesne sayısını görüntüler. Bu nesneler diğer nesnelere başvurular içeriyorsa, bu nesneler de devam etmez ancak bu sayaç tarafından sayılmaz. **Yükseltilen sonlandırma süresi-Gen 0 sayacından alınan bellek** , sonlandırma nedeniyle kalan tüm belleği temsil eder.<br /><br /> Bu sayaç toplu değildir; her çöp toplamanın sonunda yalnızca söz konusu koleksiyon sırasında kalan sanal nesnelerin sayısıyla güncelleştirilir. Bu sayaç, sonlandırma nedeniyle uygulamanın tabi olabileceği ek yükü gösterir.|  
|**Gen 0 yığın boyutu**|Oluşturma 0 ' da ayrılabilecek maksimum bayt sayısını görüntüler; 0 kuşağında ayrılan geçerli bayt sayısını göstermez.<br /><br /> Kuşak 0 çöp toplama, son koleksiyonda bu yana olan ayırmalar bu boyutu aşarsa oluşur. Nesil 0 boyutu çöp toplayıcı tarafından ayarlanır ve uygulamanın yürütülmesi sırasında değişebilir. Nesil 0 koleksiyonunun sonunda nesil 0 yığını boyutu 0 bayttır. Bu sayaç, bir sonraki nesil 0 çöp toplamayı çağıran ayırmaların bayt cinsinden boyutunu görüntüler.<br /><br /> Bu sayaç her ayırmada değil çöp toplamanın sonunda güncelleştirilir.|  
|**G 0 yükseltilen bayt/sn**|Nesil 0 ' dan 1 ' e yükseltilen saniye başına bayt sayısını görüntüler. Bellek, atık toplama işlemi yaparken yükseltilir. Bu sayaç, saniye başına oluşturulan görece uzun süreli nesnelerin göstergesidir.<br /><br /> Bu sayaç, son iki örnekte gözlenen değerler arasındaki farkı örnek aralığın süresine göre gösterir.|  
|**Gen 1 yığın boyutu**|1. nesil geçerli bayt sayısını görüntüler; Bu sayaç, 1. nesil en büyük boyutunu görüntülemez. Nesneler bu Neste doğrudan ayrılmamış; Bunlar, önceki nesil 0 çöp toplamalarından yükseltilir. Bu sayaç her ayırmada değil çöp toplamanın sonunda güncelleştirilir.|  
|**G 1 yükseltilen bayt/sn**|1. nesil 2 ' ye kadar yükseltilen saniye başına bayt sayısını görüntüler. Yalnızca Sonlandırılmayı beklediği için yükseltilen nesneler bu sayaca dahil edilmez.<br /><br /> Bellek, atık toplama işlemi yaparken yükseltilir. 2. nesil, en eski nesil olduğundan hiçbir şey yükseltilmez. Bu sayaç, saniye başına oluşturulan çok uzun süreli nesnelerin göstergesidir.<br /><br /> Bu sayaç, son iki örnekte gözlenen değerler arasındaki farkı örnek aralığın süresine göre gösterir.|  
|**Gen 2 yığın boyutu**|2. nesil geçerli bayt sayısını görüntüler. Nesneler bu Neste doğrudan ayrılmamış; önceki nesil 1 atık koleksiyonlar sırasında 1. kuşak 'den yükseltilir. Bu sayaç her ayırmada değil çöp toplamanın sonunda güncelleştirilir.|  
|**Büyük nesne yığın boyutu**|Büyük nesne yığınının geçerli boyutunu bayt cinsinden görüntüler. Yaklaşık 85.000 bayttan büyük nesneler çöp toplayıcı tarafından büyük nesneler olarak değerlendirilir ve özel bir yığında doğrudan ayrılır. Nesiller aracılığıyla yükseltilmez. Bu sayaç her ayırmada değil çöp toplamanın sonunda güncelleştirilir.|  
|**İşlem Kimliği**|İzlenmekte olan CLR işlem örneğinin işlem KIMLIĞINI görüntüler.|  
|**Yükseltilen sonlandırma-bellek, Gen 0 ' dan**|1. nesil 0 ' dan 1 ' e yükseltilen bellek baytlarını yalnızca Sonlandırılmayı beklediği için görüntüler. Bu sayaç toplu değildir; Son atık toplamanın sonunda gözlemlenen değeri görüntüler.|  
|**Gen 0 ' dan yükseltilen bellek**|Atık toplamayı sürdüren ve 1. nesil 0 ' dan 1 ' e yükseltilen bellek baytlarını görüntüler. Yalnızca Sonlandırılmayı beklediği için yükseltilen nesneler bu sayaca dahil edilmez. Bu sayaç toplu değildir; Son atık toplamanın sonunda gözlemlenen değeri görüntüler.|  
|**Gen 1 ' den yükseltilen bellek**|Çöp toplama işlemini sürdüren ve 1. nesil 2 ' den 2 ' ye yükseltilen bellek baytlarını görüntüler. Yalnızca Sonlandırılmayı beklediği için yükseltilen nesneler bu sayaca dahil edilmez. Bu sayaç toplu değildir; Son atık toplamanın sonunda gözlemlenen değeri görüntüler. Bu sayaç, son çöp toplama işlemi yalnızca 0. kuşak bir koleksiyon ise 0 ' a sıfırlanır.|  

## <a name="networking-performance-counters"></a>Ağ performans sayaçları  

Performans konsolu .NET CLR ağ kategorisi, bir uygulamanın ağ üzerinden gönderdiği ve aldığı veriler hakkında bilgi sağlayan sayaçları içerir. Aşağıdaki tabloda bu performans sayaçları açıklanmaktadır.  
  
|Performans sayacı|Description|  
|-------------------------|-----------------|  
|**Alınan bayt**|<xref:System.Net.Sockets.Socket>İşlemin başlatılmasından bu yana içindeki tüm nesneler tarafından alınan toplam bayt sayısı <xref:System.AppDomain> . Bu sayı, TCP/IP tarafından tanımlanmayan verileri ve protokol bilgilerini içerir.|  
|**Gönderilen bayt**|<xref:System.Net.Sockets.Socket>İşlemin başlatılmasından bu yana içindeki tüm nesneler tarafından gönderilen toplam bayt sayısı <xref:System.AppDomain> . Bu sayı, TCP/IP tarafından tanımlanmayan verileri ve protokol bilgilerini içerir.|  
|**Kurulan bağlantılar**|<xref:System.Net.Sockets.Socket>İşlem başladıktan sonra, içinde hiç bağlı olan akış yuvaları için toplam nesne sayısı <xref:System.AppDomain> .|  
|**Alınan veri birimleri**|<xref:System.Net.Sockets.Socket>İşlemin başlatılmasından bu yana, içindeki tüm nesneler tarafından alınan toplam veri birimi paketlerinin birikimli sayısı <xref:System.AppDomain> .|  
|**Gönderilen veri birimleri**|<xref:System.Net.Sockets.Socket>İşlemin başlatılmasından bu yana, içindeki tüm nesneler tarafından gönderilen toplam veri birimi paketlerinin birikimli sayısı <xref:System.AppDomain> .|  
|**HttpWebRequest ortalama ömrü**|<xref:System.Net.HttpWebRequest>İşlem başladıktan sonra, içindeki son aralıkta sona eren geçen tüm nesneler için tamamlanması gereken ortalama süre <xref:System.AppDomain> .|  
|**HttpWebRequest Ortalama sıra süresi**|<xref:System.Net.HttpWebRequest>İşlemin başlatılmasından bu yana, içindeki son aralıktaki kuyruğu alan tüm nesneler için Ortalama sırada geçen süre <xref:System.AppDomain> .|  
|**Oluşturulan Httpwebistek/sn**|<xref:System.Net.HttpWebRequest>İçinde saniye başına oluşturulan nesne sayısı <xref:System.AppDomain> .|  
|**Sıraya alınan Httpwebistek/sn**|<xref:System.Net.HttpWebRequest>İçinde saniye başına sıraya eklenen nesne sayısı <xref:System.AppDomain> .|  
|**Durdurulan Httpwebistek/sn**|<xref:System.Net.HttpWebRequest>Uygulamanın <xref:System.Net.HttpWebRequest.Abort%2A> içinde saniye başına yöntem olarak çağırdığı nesne sayısı <xref:System.AppDomain> .|  
|**Başarısız Httpwebisteği/sn**|<xref:System.Net.HttpWebRequest>Sunucu içinden saniye başına hatalı durum kodu alan nesne sayısı <xref:System.AppDomain> .|  
  
 Desteklenen birkaç ağ performans sayacı sınıfı vardır:  
  
- Bazı olayların kaç kez oluştuğunu ölçen olay sayaçları.  
  
- Gönderilen veya alınan veri miktarını ölçen veri sayaçları.  
  
- Farklı işlemlerin ne kadar sürdüğünü ölçen Duration sayaçları. Süreler, farklı durumlardan çıktıktan sonra her Aralık (genellikle saniye cinsinden) nesneler üzerinde ölçülür.  
  
- Aralık başına belirli bir geçiş yapan nesne sayısını ölçen Aralık başına sayaçlar (normalde saniyede).  
  
Olaylar için ağ performans sayaçları şunları içerir:  
  
- **Kurulan bağlantılar**  
  
- **Alınan veri birimleri**  
  
- **Gönderilen veri birimleri**  
  
 Bu performans sayaçları, işlem başladıktan sonra sayımlar sağlar. <xref:System.Net.Sockets.Socket>Oluşturulan bağlantı sayısı, <xref:System.Net.Sockets.Socket> oluşturulan bir akış yuvası bağlantısı için bir uygulama tarafından açık Yöntem çağrıları ve diğer sınıflar tarafından yapılan iç çağrılar ( <xref:System.Net.HttpWebRequest> ,, <xref:System.Net.FtpWebRequest> <xref:System.Net.WebClient> ve <xref:System.Net.Sockets.TcpClient> , örneğin,) <xref:System.Net.Sockets.Socket> sınıfına dahildir  
  
 **Alınan veri birimleri** ve **gönderilen veri birimleri** için sayımlar, bir uygulama tarafından açık Yöntem çağrıları kullanılarak gönderilen veya alınan veri birimi paketleri içerir <xref:System.Net.Sockets.Socket> ( <xref:System.Net.Sockets.UdpClient> Örneğin,) <xref:System.Net.Sockets.Socket> . sınıfı. **Alınan** veri birimleri ve **gönderilen** veri birimleri, bir veri birimi için Ortalama bir boyut varsayarak, veri birimleri kullanılarak gönderilen veya alınan bayt sayısı çok kaba bir ölçü sağlamak için de kullanılabilir.  
  
 Veriler için ağ performans sayaçları şunları içerir:  
  
- **Alınan bayt**  
  
- **Gönderilen bayt**  
  
 Yukarıdaki sayaçlar, işlem başladıktan sonra gelen bayt sayısını sağlar.  
  
 <xref:System.Net.HttpWebRequest>Nesnelerin tüm yaşam döngüsü veya yalnızca bir parçası aracılığıyla geçmesi için geçen süreyi ölçen iki Duration sayacı vardır:  
  
- **HttpWebRequest ortalama ömrü**  
  
- **HttpWebRequest Ortalama sıra süresi**  
  
 **HttpWebRequest ortalama ömür süresi** sayacı için, çoğu nesnenin kullanım ömrü, <xref:System.Net.HttpWebRequest> yanıt akışının uygulama tarafından kapatılmadığı zamana kadar her zaman nesnenin oluşturulduğu zaman ile başlar. Yaygın olarak görülen iki durum vardır:  
  
- Uygulama hiçbir şekilde <xref:System.Net.HttpWebRequest.GetResponse%2A> veya yöntemini çağırmadıysa <xref:System.Net.HttpWebRequest.BeginGetResponse%2A> , <xref:System.Net.HttpWebRequest> nesne ömrü yok sayılır.  
  
- <xref:System.Net.HttpWebRequest>Nesne <xref:System.Net.WebException> , veya yöntemlerini çağırırken bir oluşturursa <xref:System.Net.HttpWebRequest.GetResponse%2A> <xref:System.Net.HttpWebRequest.EndGetResponse%2A> , özel durum oluştuğunda yaşam süresi sona erer. Teknik olarak, temel alınan yanıt akışı o noktada da kapatılır (kullanıcıya döndürülen yanıt akışı gerçekten yanıt akışının bir kopyasını içeren bir bellek akışıdır).  
  
 Her Aralık için belirli nesne sorunlarını izleyen dört sayaç vardır <xref:System.Net.HttpWebRequest> . Bu performans sayaçları, uygulama geliştiricilerinin, yöneticilerin ve destek personelinin nesnelerin ne yaptığını daha iyi anlamasına yardımcı olabilir <xref:System.Net.HttpWebRequest> . Sayaçlar şunları içerir:  
  
- **Oluşturulan Httpwebistek/sn**  
  
- **Sıraya alınan Httpwebistek/sn**  
  
- **Durdurulan Httpwebistek/sn**  
  
- **Başarısız Httpwebisteği/sn**  
  
 **Yürütülen HttpWebRequests/sn** sayacı için iç çağrılar <xref:System.Net.HttpWebRequest.Abort%2A> de sayılır. Bu iç çağrılar genellikle uygulamanın ölçmek isteyebileceğiniz zaman aşımları nedeniyle oluşur.  
  
 **Başarısız olan HttpWebRequests/sn** sayacı, <xref:System.Net.HttpWebRequest> sunucudan bir saniyede başarısız durum kodu alan nesne sayısını içerir. Yani, isteğin sonundaki HTTP sunucusundan alınan durum kodu 200 ile 299 arasında değildir. İşlenen ve yeni bir istek ile sonuçlanan durum kodları (örneğin, 401 Yetkisiz durum kodlarının çoğu) başarısız olur veya yeniden deneme sonucuna göre başarısız olmaz. Uygulama yeniden denemeye göre bir hata görebiliyorsa, bu sayaç artırılır.  
  
 Ağ performans sayaçlarına, <xref:System.Diagnostics.PerformanceCounter> ad alanındaki ve ilgili sınıflar kullanılarak erişilebilir ve yönetilebilir <xref:System.Diagnostics> . Ağ performans sayaçları, Windows performans Izleyicisi konsolu ile de görüntülenebilir.  
  
 Ağ performans sayaçlarının kullanılacak yapılandırma dosyasında etkinleştirilmesi gerekir. Tüm ağ performans sayaçları, yapılandırma dosyasında tek bir ayarla etkin veya devre dışı bırakıldı. Bireysel ağ performans sayaçları etkinleştirilemez veya devre dışı bırakılamaz. Daha fazla bilgi için bkz. [ \<performanceCounter> öğesi (ağ ayarları)](../configure-apps/file-schema/network/performancecounter-element-network-settings.md).  
  
 Ağ sayaçları etkinse bu, hem AppDomain başına hem de küresel performans sayaçlarını oluşturur ve güncelleştirir. Devre dışı bırakılırsa, uygulama herhangi bir ağ performans sayacı verisi sağlamacaktır.  
  
 Performans sayaçları kategoriler halinde gruplandırılır. Bir uygulama aşağıdaki örnek kodla tüm kategorileri listeleyebilir:  
  
```csharp
PerformanceCounterCategory[] Array = PerformanceCounterCategory.GetCategories();  
for (int i = 0; i < Array.Length; i++)  
{  
    Console.Out.WriteLine("{0}. Name={1} Help={2}", i, Array[i].CategoryName, Array[i].CategoryHelp);  
}  
```  
  
 Ağ performans sayaçları iki kategoride listelenmiştir:  
  
- ".NET CLR Networking"-.NET Framework sürüm 2 ' de tanıtılan ve .NET Framework sürüm 2 ve sonrasında desteklenen özgün performans sayaçları.  
  
- ".NET CLR Networking 4.0.0.0"-yukarıdaki yuva sayaçlarının yanı sıra .NET Framework sürüm 4 ve üzeri sürümlerde desteklenen yeni performans sayaçları. Bu yeni sayaçlar nesneler hakkında performans bilgileri sağlar <xref:System.Net.HttpWebRequest> .  
  
 Bir uygulamadaki performans sayaçlarına erişme ve bunları yönetme hakkında daha fazla bilgi için bkz. [performans sayaçları](performance-counters.md).  

## <a name="security-performance-counters"></a>Güvenlik performans sayaçları  
 Performans konsolu .NET CLR güvenlik kategorisi, ortak dil çalışma zamanının bir uygulama için gerçekleştirdiği güvenlik denetimleri hakkında bilgi sağlayan sayaçları içerir. Aşağıdaki tabloda bu performans sayaçları açıklanmaktadır.  
  
|Performans sayacı|Description|  
|-------------------------|-----------------|  
|**Bağlantı zamanı denetimleri sayısı**|Uygulama başladıktan sonra bağlantı zamanı kod erişimi güvenlik denetimlerinin toplam sayısını görüntüler. Bağlama zamanı kod erişimi güvenlik denetimleri, bir arayan belirli bir zamanda (JıT) derleme zamanında belirli bir izin talep ettiğinde gerçekleştirilir. Bir bağlantı zamanı denetimi, çağıran başına bir kez gerçekleştirilir. Bu sayı ciddi performans sorunlarının göstergesi değildir; yalnızca güvenlik sistemi etkinliğinin bir göstergesi vardır.|  
|**RT denetimlerinde% Time**|Son örnekten bu yana çalışma zamanı kodu erişim güvenlik denetimlerini gerçekleştirirken harcanan geçen sürenin yüzdesini görüntüler. Bu sayaç, .NET Framework bir güvenlik denetiminin sonunda güncelleştirilir. Ortalama değer değildir; Bu, son gözlemlenen değeri temsil eder.|  
|**% Saat SIG kimlik doğrulaması**|Daha sonraki kullanımlar için ayrılmıştır.|  
|**Yığın Ilerleme derinliği**|Son çalışma zamanı kod erişimi güvenlik denetimi sırasında yığının derinliğini görüntüler. Çalışma zamanı kod erişimi güvenlik denetimleri, yığın yürüyerek gerçekleştirilir. Bu sayaç bir ortalama değil; yalnızca son gözlemlenen değeri görüntüler.|  
|**Toplam çalışma zamanı denetimleri**|Uygulama başladıktan sonra gerçekleştirilen çalışma zamanı kodu erişimi güvenlik denetimlerinin toplam sayısını görüntüler. Çalışma zamanı kod erişimi güvenlik denetimleri, bir arayan belirli bir izin talep ettiğinde gerçekleştirilir. Çalışma zamanı denetimi, çağıran tarafından her çağrıda yapılır ve çağıranın geçerli iş parçacığı yığınını inceler. **Yığın Ilerleme derinliği** sayacı ile kullanıldığında, bu sayaç güvenlik denetimleri için gerçekleşen performans cezası olduğunu gösterir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Performans sayaçları](performance-counters.md)
- [Çalışma Zamanı Profili Oluşturma](runtime-profiling.md)
