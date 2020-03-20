---
title: .NET Framework'teki Performans Sayaçları
ms.date: 03/30/2017
helpviewer_keywords:
- performance, .NET Framework applications
- performance counters
- performance monitoring, counters
ms.assetid: 06a4ae8c-eeb2-4d5a-817e-b1b95c0653e1
ms.openlocfilehash: 44a5d1cb70d294d720290a4754bb5f5cb47f79a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400024"
---
# <a name="performance-counters-in-the-net-framework"></a>.NET Çerçevesindeki performans sayaçları

Bu [konu, Windows Performans İzleyicisi'nde](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc749249%28v=ws.11%29)bulabileceğiniz performans sayaçlarının bir listesini sağlar.  

## <a name="exception-performance-counters"></a>Özel durum performans sayaçları  
 Performans konsolu .NET CLR Özel Durumlar kategorisi, bir uygulama tarafından atılan özel durumlar hakkında bilgi sağlayan sayaçları içerir. Aşağıdaki tabloda bu performans sayaçları açıklanmaktadır.  
  
|Performans sayacı|Açıklama|  
|-------------------------|-----------------|  
|**# Exceps Atılmış**|Uygulama başladığından beri atılan toplam özel durum sayısını görüntüler. Buna hem .NET özel durumları hem de .NET özel durumlara dönüştürülen yönetilmeyen özel durumları içerir. Örneğin, yönetilmeyen koddan döndürülen bir HRESULT, yönetilen kodda özel bir özel durum olarak dönüştürülür.<br /><br /> Bu sayaç hem işlenmiş hem de işlenmemiş özel durumları içerir. Yeniden atılan özel durumlar yeniden sayılır.|  
|**# Exceps Atılmış / Sn**|Saniyede atılan özel durum sayısını görüntüler. Buna hem .NET özel durumları hem de .NET özel durumlara dönüştürülen yönetilmeyen özel durumları içerir. Örneğin, yönetilmeyen koddan döndürülen bir HRESULT, yönetilen kodda özel bir özel durum olarak dönüştürülür.<br /><br /> Bu sayaç hem işlenmiş hem de işlenmemiş özel durumları içerir. Bu zaman içinde bir ortalama değildir; örnek aralığının süresine bölünen son iki örnekte gözlenen değerler arasındaki farkı görüntüler. Bu sayaç, büyük (>100'lü >) sayıda özel durum atılırsa olası performans sorunlarının bir göstergesidir.|  
|**# filtreler / Sec**|Saniyede çalıştırılan .NET özel durum filtrelerinin sayısını görüntüler. Özel durum filtresi, özel durum işlenip işlenmediğine bakılmaksızın değerlendirir.<br /><br /> Bu sayaç zaman içinde bir ortalama değildir; örnek aralığının süresine bölünen son iki örnekte gözlenen değerler arasındaki farkı görüntüler.|  
|**# / Sn**|Saniyede çalıştırılan son blokların sayısını görüntüler. Try bloğunun nasıl çıktığına bakılmaksızın son bloğun yürütülmesi garanti edilir.  Yalnızca bir özel durum için çalıştırılan son bloklar sayılır; son olarak normal kod yollarında bloklar bu sayaç tarafından sayılmaz.<br /><br /> Bu sayaç zaman içinde bir ortalama değildir; örnek aralığının süresine bölünen son iki örnekte gözlenen değerler arasındaki farkı görüntüler.|  
|**Catch Depth / Sec atmak**|Özel durumu atan çerçeveden, saniyede özel durumu işleyen çerçeveye geçen yığın çerçevelerinin sayısını görüntüler. Bir özel durum işleyicisi girildiğinde bu sayaç sıfırlanır, bu nedenle iç içe geçen özel durumlar işleyiciden işleyici yığını derinliğini gösterir.<br /><br /> Bu sayaç zaman içinde bir ortalama değildir; örnek aralığının süresine bölünen son iki örnekte gözlenen değerler arasındaki farkı görüntüler.|  

## <a name="interop-performance-counters"></a>Interop performans sayaçları  
 Performans konsolu .NET CLR Interop kategorisi, bir uygulamanın COM bileşenleri, COM+ hizmetleri ve dış tür kitaplıklarıyla etkileşimi hakkında bilgi sağlayan sayaçları içerir. Aşağıdaki tabloda bu performans sayaçları açıklanmaktadır.  
  
|Performans sayacı|Açıklama|  
|-------------------------|-----------------|  
|**# CCWs ve**|Geçerli COM çağrılabilir sarmalayıcı (CCW) sayısını görüntüler. CCW, yönetilmeyen bir COM istemcisinden başvurulan yönetilen bir nesnenin proxy'sidir. Bu sayaç, yönetilmeyen COM kodu tarafından başvurulan yönetilen nesnelerin sayısını gösterir.|  
|**# mareşallik**|Uygulama başladığından beri yönetilen koddan yönetilmeyen koda kadar toplam kaç kez bağımsız değişken ve döndürme değeri olduğunu görüntüler. Saplamalar çizgiliise bu sayaç artımlı değildir. (Saplamalar bağımsız değişkenleri ve döndürme değerlerini mareşallemeden sorumludur). Pareşal yükü küçükse, saplamalar genellikle sıralanır.|  
|**# Saplamalar**|Ortak dil çalışma zamanı tarafından oluşturulan geçerli saplama sayısını görüntüler. Saplamalar, yönetilen koddan yönetilmeyen koda bağımsız değişkenleri ve döndürme değerlerini mareşallemekten sorumludur ve bunun tersi, com interop çağrısı veya platform çağrı çağrısı sırasında.|  
|**# TLB ihracat / sn**|Daha sonraki kullanımlar için ayrılmıştır.|  
|**# TLB ithalat / sn**|Daha sonraki kullanımlar için ayrılmıştır.|  

## <a name="jit-performance-counters"></a>JIT performans sayaçları  
 Performans konsolu .NET CLR JIT kategorisi, JIT tarafından derlenen kod hakkında bilgi sağlayan sayaçlar içerir. Aşağıdaki tabloda bu performans sayaçları açıklanmaktadır.  
  
|Performans sayacı|Açıklama|  
|-------------------------|-----------------|  
|**# IL Bayt jitted ve**|Uygulama başladığından beri tam zamanında (JIT) derleyicisi tarafından derlenen toplam Microsoft ara dili (MSIL) bayt sayısını görüntüler. Bu **sayaç, IL BaytJitted sayacının Toplam #una** eşdeğerdir.|  
|**# Yöntemleri JITted**|Uygulama başladığından beri JIT tarafından derlenen toplam yöntem sayısını görüntüler. Bu sayaç, JIT öncesi derlenmiş yöntemleri içermez.|  
|**Jit'te % Zaman**|Son JIT derleme aşamasından bu yana JIT derlemesinde harcanan geçen süre yüzdesini görüntüler. Bu sayaç her JIT derleme aşamasının sonunda güncelleştirilir. Bir yöntem ve bağımlılıkları derlendiğinde JIT derleme aşaması oluşur.|  
|**IL Bayt Jitted / sn**|Saniyede JIT tarafından derlenen MSIL baytlarının sayısını görüntüler. Bu sayaç zaman içinde bir ortalama değildir; örnek aralığının süresine bölünen son iki örnekte gözlenen değerler arasındaki farkı görüntüler.|  
|**Standart Jit Hataları**|JIT derleyicisinin uygulama başladığından beri derlemediği en yüksek yöntem sayısını görüntüler. MSIL doğrulanamıyorsa veya JIT derleyicisinde bir iç hata varsa bu hata oluşabilir.|  
|**Toplam # IL Bayt Jitted**|Uygulama başladığından beri derlenen toplam MSIL baytJIT'i görüntüler. Bu sayaç IL **Bayt Jitted sayacının #** eşdeğerdir.|  

## <a name="loading-performance-counters"></a>Yükleme performans sayaçları  
 Performans konsolu .NET CLR Yükleme kategorisi, yüklenen derlemeler, sınıflar ve uygulama etki alanları hakkında bilgi sağlayan sayaçları içerir. Aşağıdaki tabloda bu performans sayaçları açıklanmaktadır.  
  
|Performans sayacı|Açıklama|  
|-------------------------|-----------------|  
|**% Zaman Yükleme**|Daha sonraki kullanımlar için ayrılmıştır.|  
|**Montaj Arama Uzunluğu**|Daha sonraki kullanımlar için ayrılmıştır.|  
|**Yükleyici Yığınında Baytlar**|Sınıf yükleyicisi tarafından tüm uygulama etki alanlarında işlenen belleğin geçerli boyutunu baytolarak görüntüler. Taahhüt edilen bellek, disk sayfalama dosyasında ayrılmış fiziksel alandır.|  
|**Geçerli etki alanları**|Bu uygulamada yüklenen geçerli uygulama etki alanı sayısını görüntüler.|  
|**Geçerli Meclisler**|Geçerli olan uygulamadaki tüm uygulama etki alanlarında yüklenen geçerli derleme sayısını görüntüler. Derleme birden çok uygulama etki alanından etki alanı nötr olarak yüklenirse, bu sayaç yalnızca bir kez artımlanır.|  
|**Yüklenen Geçerli Sınıflar**|Tüm derlemelerde yüklenen sınıfların geçerli sayısını görüntüler.|  
|**Etki alanlarının oranı**|Saniyede yüklenen uygulama etki alanı sayısını görüntüler. Bu sayaç zaman içinde bir ortalama değildir; örnek aralığının süresine bölünen son iki örnekte gözlenen değerler arasındaki farkı görüntüler.|  
|**Çıkarılan etki alanlarının oranı**|Saniyede boşaltılan uygulama etki alanı sayısını görüntüler. Bu sayaç zaman içinde bir ortalama değildir; örnek aralığının süresine bölünen son iki örnekte gözlenen değerler arasındaki farkı görüntüler.|  
|**Meclisoranı**|Tüm uygulama etki alanlarında saniyede yüklenen derleme sayısını görüntüler. Derleme birden çok uygulama etki alanından etki alanı nötr olarak yüklenirse, bu sayaç yalnızca bir kez artımlanır.<br /><br /> Bu sayaç zaman içinde bir ortalama değildir; örnek aralığının süresine bölünen son iki örnekte gözlenen değerler arasındaki farkı görüntüler.|  
|**Yüklenen Sınıfların Oranı**|Tüm derlemelerde saniyede yüklenen sınıf sayısını görüntüler. Bu sayaç zaman içinde bir ortalama değildir; örnek aralığının süresine bölünen son iki örnekte gözlenen değerler arasındaki farkı görüntüler.|  
|**Yük Arızaoranı**|Saniyede yüklenemeyen sınıf ların sayısını görüntüler. Bu sayaç zaman içinde bir ortalama değildir; örnek aralığının süresine bölünen son iki örnekte gözlenen değerler arasındaki farkı görüntüler.<br /><br /> Yük hataları, yetersiz güvenlik veya geçersiz biçim gibi birçok nedenden dolayı oluşabilir. Ayrıntılar için profil oluşturma hizmetleri Yardım'a bakın.|  
|**Yük Hatalarıtoplamı #**|Uygulama başladığından beri yüklenemeyen en yüksek sınıf sayısını görüntüler.<br /><br /> Yük hataları, yetersiz güvenlik veya geçersiz biçim gibi birçok nedenden dolayı oluşabilir. Ayrıntılar için profil oluşturma hizmetleri Yardım'a bakın.|  
|**Toplam Appdomains**|Uygulama başladığından beri yüklenen en yüksek uygulama etki alanı sayısını görüntüler.|  
|**Toplam etki alanları boşaltıldı**|Uygulama başladığından beri boşaltılan toplam uygulama etki alanı sayısını görüntüler. Bir uygulama etki alanı birden çok kez yüklenir ve boşaltılırsa, bu sayaç her uygulama etki alanı boşaltıldığında artış lar.|  
|**Toplam Meclisler**|Uygulama başladığından beri yüklenen toplam derleme sayısını görüntüler. Derleme birden çok uygulama etki alanından etki alanı nötr olarak yüklenirse, bu sayaç yalnızca bir kez artımlanır.|  
|**Yüklenen Toplam Sınıf Sayısı**|Uygulama başladığından beri tüm derlemelerde yüklenen sınıfların kümülatif sayısını görüntüler.|  

## <a name="lock-and-thread-performance-counters"></a>Kilit ve iş parçacığı performans sayaçları  
 Performans konsolu .NET CLR LocksAndThreads kategorisi, bir uygulamanın kullandığı yönetilen kilitler ve iş parçacıkları hakkında bilgi sağlayan sayaçları içerir. Aşağıdaki tabloda bu performans sayaçları açıklanmaktadır.  
  
|Performans sayacı|Açıklama|  
|-------------------------|-----------------|  
|**# geçerli mantıksal Konuları**|Uygulamadaki geçerli yönetilen iş parçacığı nesnelerinin sayısını görüntüler. Bu sayaç, hem çalışan hem de durdurulan iş parçacığı sayısını korur. Bu sayaç zaman içinde bir ortalama değildir; yalnızca son gözlenen değeri gösterir.|  
|**# geçerli fiziksel Konuları**|Yönetilen iş parçacığı nesneleri için altta yatan iş parçacıkları olarak hareket etmek için ortak dil çalışma zamanı tarafından oluşturulan ve sahip olunan yerel işletim sistemi iş parçacığı sayısını görüntüler. Bu sayacın değeri, çalışma zamanı tarafından kullanılan iş parçacıklarını iç işlemlerinde içermez; işletme sistemi işlemindeki iş parçacıklarının bir alt kümesidir.|  
|**# geçerli tanınan iş parçacıkları**|Şu anda çalışma zamanı tarafından tanınan iş parçacığı sayısını görüntüler. Bu iş parçacıkları karşılık gelen yönetilen iş parçacığı nesnesi ile ilişkilidir. Çalışma zamanı bu iş parçacıklarını oluşturmaz, ancak çalışma süresi içinde en az bir kez çalıştırılabın.<br /><br /> Yalnızca benzersiz iş parçacıkları izlenir; çalışma süresini yeniden giren veya iş parçacığı çıktılarından sonra yeniden oluşturulan aynı iş parçacığı kimliğine sahip iş parçacıkları iki kez sayılmaz.|  
|**# toplam tanınan Konuları**|Uygulamanın başlamasından bu yana çalışma süresi tarafından tanınan toplam iş parçacığı sayısını görüntüler. Bu iş parçacıkları karşılık gelen yönetilen iş parçacığı nesnesi ile ilişkilidir. Çalışma zamanı bu iş parçacıklarını oluşturmaz, ancak çalışma süresi içinde en az bir kez çalıştırılabın.<br /><br /> Yalnızca benzersiz iş parçacıkları izlenir; çalışma süresini yeniden giren veya iş parçacığı çıktılarından sonra yeniden oluşturulan aynı iş parçacığı kimliğine sahip iş parçacıkları iki kez sayılmaz.|  
|**Çekişme Oranı / Sn**|Yönetilen bir kilidi başarısız bir şekilde elde etmek için çalışma zamanındaki iş parçacıklarının çalışma hızını görüntüler.|  
|**Geçerli Sıra Uzunluğu**|Uygulamada yönetilen bir kilit elde etmek için bekleyen toplam iş parçacığı sayısını görüntüler. Bu sayaç zaman içinde bir ortalama değildir; son gözlenen değeri gösterir.|  
|**Sıra Uzunluğu / sn**|Uygulamada kilit elde etmek için bekleyen saniyede iş parçacığı sayısını görüntüler. Bu sayaç zaman içinde bir ortalama değildir; örnek aralığının süresine bölünen son iki örnekte gözlenen değerler arasındaki farkı görüntüler.|  
|**Sıra Uzunluğu Tepe Noktası**|Uygulama başladığından beri yönetilen bir kilit elde etmek için bekleyen toplam iş parçacığı sayısını görüntüler.|  
|**tanınan iş parçacığı / sn oranı**|Çalışma zamanı tarafından tanınan saniyede iş parçacığı sayısını görüntüler. Bu iş parçacıkları karşılık gelen yönetilen iş parçacığı nesnesi ile ilişkilidir. Çalışma zamanı bu iş parçacıklarını oluşturmaz, ancak çalışma süresi içinde en az bir kez çalıştırılabın.<br /><br /> Yalnızca benzersiz iş parçacıkları izlenir; çalışma süresini yeniden giren veya iş parçacığı çıktılarından sonra yeniden oluşturulan aynı iş parçacığı kimliğine sahip iş parçacıkları iki kez sayılmaz.<br /><br /> Bu sayaç zaman içinde bir ortalama değildir; örnek aralığının süresine bölünen son iki örnekte gözlenen değerler arasındaki farkı görüntüler.|  
|**Çekişmelerin Toplam #**|Çalışma zamanında iş parçacıklarının yönetilen bir kilidi başarısız bir şekilde elde etmeye çalıştığı toplam sayısını görüntüler.|  

## <a name="memory-performance-counters"></a>Bellek performans sayaçları  
 Performans konsolu .NET CLR Bellek kategorisi, çöp toplayıcısı hakkında bilgi sağlayan sayaçları içerir. Aşağıdaki tabloda bu performans sayaçları açıklanmaktadır.  
  
|Performans sayacı|Açıklama|  
|-------------------------|-----------------|  
|**# Tüm Yığınlar içinde Bayt**|**Gen 1 Yığın Boyutu,** Gen **2 Yığın Boyutu**ve Büyük Nesne Yığın **Boyutu** sayaçlarının toplamını görüntüler. Bu sayaç, çöp toplama yığınlarıüzerinde baytayrılan geçerli belleği gösterir.|  
|**# GC Kolları**|Kullanılan çöp toplama tanıtıcılarının geçerli sayısını görüntüler. Çöp toplama tanıtıcıları, ortak dil çalışma süresi ve yönetilen ortam dışında kaynaklara işlenir.|  
|**# Gen 0 Koleksiyonları**|Uygulama başladığından beri nesil 0 nesnelerinin (yani en genç, en son ayrılan nesnelerin) kaç kez toplandığını görüntüler.<br /><br /> Nesil 0 çöp toplama, nesil 0'daki kullanılabilir bellek ayırma isteğini karşılamak için yeterli olmadığında oluşur. Bu sayaç bir nesil 0 çöp toplama sonunda artımlı. Yüksek nesil çöp koleksiyonları tüm alt nesil koleksiyonları içerir. Bu sayaç, daha yüksek nesil (nesil 1 veya 2) çöp toplama gerçekleştiğinde açıkça artımlanır.<br /><br /> Bu sayaç, gözlenen son değeri görüntüler. sayaç değeri **_Global\_ ** doğru değildir ve göz ardı edilmelidir.|  
|**# Gen 1 Koleksiyonları**|Uygulama başladığından beri nesil 1 nesnelerin in kaç kez toplandığını görüntüler.<br /><br /> Sayaç, nesil 1 çöp toplama sonunda artıya lanır. Yüksek nesil çöp koleksiyonları tüm alt nesil koleksiyonları içerir. Bu sayaç, daha yüksek nesil (nesil 2) çöp toplama gerçekleştiğinde açıkça artımlanır.<br /><br /> Bu sayaç, gözlenen son değeri görüntüler. sayaç değeri **_Global\_ ** doğru değildir ve göz ardı edilmelidir.|  
|**# Gen 2 Koleksiyonları**|Uygulama başladığından beri nesil 2 nesnelerin kaç kez toplandığını görüntüler. Sayaç, nesil 2 çöp toplama (tam çöp toplama olarak da adlandırılır) sonunda artımlı.<br /><br /> Bu sayaç, gözlenen son değeri görüntüler. sayaç değeri **_Global\_ ** doğru değildir ve göz ardı edilmelidir.|  
|**# Indüklenen GC**|Açık bir çağrı nedeniyle çöp toplamanın en yüksek <xref:System.GC.Collect%2A?displayProperty=nameWithType>kaç kez gerçekleştirildiği görüntülenir. Çöp toplayıcısının koleksiyonlarının sıklığını ayarlamasına izin vermek iyi bir uygulamadır.|  
|**# Sabitlenmiş Nesneler**|Son çöp koleksiyonunda karşılaşılan sabitlenmiş nesne sayısını görüntüler. Sabitlenmiş nesne, çöp toplayıcısının bellekte taşıyamadığı bir nesnedir. Bu sayaç, sabitlenmiş nesneleri yalnızca toplanan çöp yığınlarında izler. Örneğin, bir nesil 0 çöp toplama yalnızca nesil 0 yığın sabitlenmiş nesnelerin numaralandırma neden olur.|  
|**# kullanılan Lavabo Blokları**|Geçerli eşzamanlılık bloklarının geçerli sayısını görüntüler. Eşitleme blokları, eşitleme bilgilerini depolamak için ayrılan nesne başına veri yapılarıdır. Yönetilen nesnelere zayıf başvurular tutarlar ve çöp toplayıcı sı tarafından taranmalıdır. Eşitleme blokları eşitleme bilgilerini depolamakla sınırlı değildir; ayrıca COM interop meta verilerini de saklayabilirler. Bu sayaç, eşitleme ilkellerinin yoğun kullanımıyla ilgili performans sorunlarını gösterir.|  
|**# Toplam taahhüt Bayt**|Çöp toplayıcıtarafından şu anda işlenen sanal bellek miktarını baytlar halinde görüntüler. Taahhüt edilen bellek, disk sayfalama dosyasında boşluk rezerve edilen fiziksel bellektir.|  
|**# Toplam ayrılmış Bayt**|Şu anda çöp toplayıcı tarafından ayrılmış olan sanal bellek miktarını baytlar halinde görüntüler. Ayrılmış bellek, disk veya ana bellek sayfaları kullanılmadığında uygulama için ayrılmış sanal bellek alanıdır.|  
|**GC'de % Süre**|Son çöp toplama döngüsünden bu yana çöp toplama gerçekleştirme için harcanan geçen süre yüzdesini görüntüler. Bu sayaç genellikle çöp toplayıcı tarafından yapılan işi gösterir ve uygulama adına bellek sıkıştırmak için. Bu sayaç yalnızca her çöp toplama nın sonunda güncelleştirilir. Bu sayaç bir ortalama değildir; değeri son gözlenen değeri yansıtır.|  
|**Ayrılan Bayt/saniye**|Çöp toplama yığınına ayrılan saniyede bayt sayısını görüntüler. Bu sayaç, her ayırmada değil, her çöp toplamanın sonunda güncelleştirilir. Bu sayaç zaman içinde bir ortalama değildir; örnek aralığının süresine bölünen son iki örnekte gözlenen değerler arasındaki farkı görüntüler.|  
|**Sonlandırma Kurtulanlar**|Sonuçlanmasını bekledikleri için koleksiyondan kurtulan çöple toplanan nesnelerin sayısını görüntüler. Bu nesneler diğer nesnelere başvuru tutuyorsa, bu nesneler de hayatta kalır, ancak bu sayaç tarafından sayılmaz. **Gen 0 sayacından Tanıtılan Sonlandırma-Bellek,** sonlandırma nedeniyle hayatta kalan tüm belleği temsil eder.<br /><br /> Bu sayaç kümülatif değildir; sadece o toplama sırasında kurtulanların sayısı ile her çöp toplama sonunda güncellenir. Bu sayaç, uygulamanın sonlandırma nedeniyle maruz kılabileceği ek yükü gösterir.|  
|**Gen 0 yığın boyutu**|Nesil 0'da ayrılabilen maksimum baytları görüntüler; nesil 0'da ayrılan geçerli bayt sayısını göstermez.<br /><br /> Son koleksiyondan sonraki ayırmalar bu boyutu aştığında bir nesil 0 çöp toplama oluşur. Nesil 0 boyutu çöp toplayıcı tarafından ayarlanır ve uygulamanın yürütülmesi sırasında değişebilir. Bir nesil 0 koleksiyonunun sonunda nesil 0 yığınının boyutu 0 bayttır. Bu sayaç, yeni nesil 0 çöp toplama çağıran ayırmaların boyutunu, baytlar olarak görüntüler.<br /><br /> Bu sayaç, her ayırmada değil, çöp toplamanın sonunda güncelleştirilir.|  
|**Gen 0 Terfi Bayt/Sn**|Nesil 0'dan nesil 1'e yükseltilen saniyede baytları görüntüler. Bellek, çöp toplamadan kurtulduğunda tanıtılır. Bu sayaç, saniyede oluşturulan nispeten uzun ömürlü nesnelerin bir göstergesidir.<br /><br /> Bu sayaç, son iki örnekte gözlenen değerler arasındaki farkı, örnek aralığının süresine bölünür.|  
|**Gen 1 yığın boyutu**|Nesil 1'deki geçerli bayt sayısını görüntüler; bu sayaç nesil 1 maksimum boyutu görüntülemez. Nesneler bu nesilde doğrudan tahsis edilmez; onlar önceki nesil 0 çöp toplama teşvik edilmektedir. Bu sayaç, her ayırmada değil, çöp toplamanın sonunda güncelleştirilir.|  
|**Gen 1 Terfi Bayt/Sn**|Nesil 1'den nesil 2'ye yükseltilen saniyede baytları görüntüler. Yalnızca sonuçlandırılmasını bekledikleri için tanıtılan nesneler bu sayaça dahil edilmez.<br /><br /> Bellek, çöp toplamadan kurtulduğunda tanıtılır. En eski nesil olduğu için hiçbir şey nesil 2'den terfi ettirilir. Bu sayaç, saniyede oluşturulan çok uzun ömürlü nesnelerin bir göstergesidir.<br /><br /> Bu sayaç, son iki örnekte gözlenen değerler arasındaki farkı, örnek aralığının süresine bölünür.|  
|**Gen 2 yığın boyutu**|Nesil 2'deki geçerli bayt sayısını görüntüler. Nesneler bu nesilde doğrudan tahsis edilmez; onlar nesil 1 önceki nesil 1 çöp koleksiyonları sırasında terfi ettirilir. Bu sayaç, her ayırmada değil, çöp toplamanın sonunda güncelleştirilir.|  
|**Büyük Nesne Yığını boyutu**|Büyük nesne yığınının geçerli boyutunu baytlar halinde görüntüler. Yaklaşık 85.000 bayttan büyük nesneler çöp toplayıcı tarafından büyük nesneler olarak kabul edilir ve doğrudan özel bir yığın ayrılır. Nesiller boyunca terfi etmiyorlar. Bu sayaç, her ayırmada değil, çöp toplamanın sonunda güncelleştirilir.|  
|**İşlem Kimliği**|İzlenen CLR işlem örneğinin işlem kimliğini görüntüler.|  
|**Gen 0'dan Terfi Finalleştirme-Bellek**|Yalnızca sonolarak tamamlanmayı bekledikleri için nesil 0'dan nesil 1'e yükseltilen bellek baytlarını görüntüler. Bu sayaç kümülatif değildir; son çöp toplama nın sonunda gözlenen değeri görüntüler.|  
|**Gen 0'dan Tanıtılan Bellek**|Çöp toplamadan kurtulan ve nesil 0'dan nesil 1'e yükseltilen bellek baytlarını görüntüler. Yalnızca sonuçlandırılmasını bekledikleri için tanıtılan nesneler bu sayaça dahil edilmez. Bu sayaç kümülatif değildir; son çöp toplama nın sonunda gözlenen değeri görüntüler.|  
|**Gen 1'den Tanıtılan Bellek**|Çöp toplamadan kurtulan ve nesil 1'den nesil 2'ye yükseltilen bellek baytlarını görüntüler. Yalnızca sonuçlandırılmasını bekledikleri için tanıtılan nesneler bu sayaça dahil edilmez. Bu sayaç kümülatif değildir; son çöp toplama nın sonunda gözlenen değeri görüntüler. Son çöp toplama yalnızca nesil 0 koleksiyonu ysa, bu sayaç 0'a sıfırlanır.|  

## <a name="networking-performance-counters"></a>Ağ performans sayaçları  

Performans konsolu .NET CLR Ağ kategorisi, bir uygulamanın ağ üzerinden gönderdiği ve aldığı veriler hakkında bilgi sağlayan sayaçları içerir. Aşağıdaki tabloda bu performans sayaçları açıklanmaktadır.  
  
|Performans sayacı|Açıklama|  
|-------------------------|-----------------|  
|**Alınan Baytlar**|İşlemin başlamasından <xref:System.Net.Sockets.Socket> <xref:System.AppDomain> bu yana içindeki tüm nesneler tarafından alınan toplam bayt sayısı. Bu sayı, tcp/IP tarafından tanımlanmayan verileri ve protokol bilgilerini içerir.|  
|**Gönderilen Baytlar**|İşlemin başlamasından <xref:System.Net.Sockets.Socket> <xref:System.AppDomain> bu yana içindeki tüm nesneler tarafından gönderilen baytların kümülatif sayısı. Bu sayı, tcp/IP tarafından tanımlanmayan verileri ve protokol bilgilerini içerir.|  
|**Kurulan Bağlantılar**|İşlemin başlamasından <xref:System.Net.Sockets.Socket> <xref:System.AppDomain> bu yana bağlı olan akış yuvaları için toplam nesne sayısı.|  
|**Alınan Datagramlar**|İşlemin başlamasından <xref:System.Net.Sockets.Socket> <xref:System.AppDomain> bu yana içindeki tüm nesneler tarafından alınan toplam verigramı paketi sayısı.|  
|**Gönderilen Datagramlar**|İşlemin başlamasından <xref:System.Net.Sockets.Socket> <xref:System.AppDomain> bu yana içindeki tüm nesneler tarafından gönderilen toplam veri gram ı paketi sayısı.|  
|**httpwebRequest Ortalama Ömür Boyu**|İşlemin başlamasından <xref:System.Net.HttpWebRequest> <xref:System.AppDomain> bu yana son aralıkta sona eren tüm nesneler için ortalama tamamlanma süresi.|  
|**httpwebRequest Ortalama Sıra Süresi**|İşlemin başlamasından <xref:System.Net.HttpWebRequest> <xref:System.AppDomain> bu yana son aralıkta sırayı bırakan tüm nesneler için ortalama sıralı süre.|  
|**HttpWebRequests Oluşturuldu/sn**|Içinde saniyede <xref:System.Net.HttpWebRequest> oluşturulan nesnelerin <xref:System.AppDomain>sayısı.|  
|**HttpWebRequests Sıraya/sn**|'deki <xref:System.Net.HttpWebRequest> kuyruğa eklenen nesne <xref:System.AppDomain>sayısı.|  
|**HttpWebRequests İptal /sn**|Uygulamanın <xref:System.Net.HttpWebRequest> içinde saniye başına <xref:System.Net.HttpWebRequest.Abort%2A> yöntem olarak adlandırılan <xref:System.AppDomain>nesnelerin sayısı.|  
|**HttpWebRequests Başarısız / sn**|Sunucudan <xref:System.Net.HttpWebRequest> saniye başına başarısız bir durum kodu alan nesnelerin <xref:System.AppDomain>sayısı .|  
  
 Desteklenen ağ performans sayaçları çeşitli sınıflar vardır:  
  
- Bazı olayın oluşma sayısını ölçen olay sayaçları.  
  
- Gönderilen veya alınan veri miktarını ölçen veri sayaçları.  
  
- Farklı işlemlerin ne kadar sürdüğünü ölçen süre sayaçları. Saatler, farklı durumlardan çıktıktan sonra her aralıkta (genellikle saniye cinsinden) nesneler üzerinde ölçülür.  
  
- Aralık başına belirli bir geçiş yapan nesnelerin sayısını ölçen Aralık Başına sayaçlar (normalde saniye başına).  
  
Etkinlikler için ağ performans sayaçları şunlardır:  
  
- **Kurulan Bağlantılar**  
  
- **Alınan Datagramlar**  
  
- **Gönderilen Datagramlar**  
  
 Bu performans sayaçları, işlem başladığından beri sayımlar sağlar. Kurulan <xref:System.Net.Sockets.Socket> bağlantı sayısı, bir <xref:System.Net.Sockets.Socket> uygulama tarafından kurulan akış soketi bağlantısının yanı sıra diğer sınıflar tarafından<xref:System.Net.HttpWebRequest> <xref:System.Net.FtpWebRequest>sınıfa <xref:System.Net.WebClient> <xref:System.Net.Sockets.TcpClient> <xref:System.Net.Sockets.Socket> (, , ve örneğin) yapılan dahili çağrıları içeren açık yöntem çağrılarını içerir  
  
 **Alınan Datagramlar** ve **Gönderilen Datagramlar** için sayımlar, <xref:System.Net.Sockets.Socket> bir uygulama tarafından açık yöntem çağrıları kullanılarak<xref:System.Net.Sockets.UdpClient>gönderilen veya alınan <xref:System.Net.Sockets.Socket>verigram ı paketlerinin yanı sıra diğer sınıflar tarafından yapılan dahili aramaları da (örneğin) . Sınıfı. **Datagramalınan** ve **Gönderilen Datagramsayısı,** bir datagram için ortalama bir boyut üstlenerek verigramı kullanılarak kaç bayt gönderildiğinin veya alındığının çok kaba bir ölçüsünü sağlamak için de kullanılabilir.  
  
 Veriler için ağ performans sayaçları şunlardır:  
  
- **Alınan Baytlar**  
  
- **Gönderilen Baytlar**  
  
 Yukarıdaki sayaçlar, işlem başladığından beri bayt sayısını sağlar.  
  
 <xref:System.Net.HttpWebRequest> Nesnelerin tüm yaşam döngülerinden ya da sadece bir kısmından geçmelerinin ne kadar sürdüğünü ölçen iki süre sayacı vardır:  
  
- **httpwebRequest Ortalama Ömür Boyu**  
  
- **httpwebRequest Ortalama Sıra Süresi**  
  
 **HttpWebRequest Ortalama Yaşam Süresi** sayacı <xref:System.Net.HttpWebRequest> için, çoğu nesnenin ömrü her zaman yanıt akışı uygulama tarafından kapatılanakadar nesnenin oluşturulduğu süreyle başlar. İki nadir durum vardır:  
  
- Uygulama hiçbir zaman <xref:System.Net.HttpWebRequest.GetResponse%2A> veya <xref:System.Net.HttpWebRequest.BeginGetResponse%2A> yöntemleri aramaz, <xref:System.Net.HttpWebRequest> nesnenin ömrü yoksayılır.  
  
- <xref:System.Net.HttpWebRequest> Nesne çağıran <xref:System.Net.HttpWebRequest.GetResponse%2A> veya <xref:System.Net.HttpWebRequest.EndGetResponse%2A> <xref:System.Net.WebException> yöntemleri a atarsa, özel durum atıldığında kullanım ömrü sona erer. Teknik olarak, bu noktada temel yanıt akışı da kapatılır (kullanıcıya döndürülen yanıt akışı gerçekten yanıt akışının bir kopyasını içeren bir bellek akışıdır).  
  
 Belirli <xref:System.Net.HttpWebRequest> nesne sorunlarını aralık başına izleyen dört sayaç vardır. Bu performans sayaçları, uygulama geliştiricilerinin, yöneticilerin ve <xref:System.Net.HttpWebRequest> destek personelinin nesnelerin ne yaptığını daha iyi anlamalarına yardımcı olabilir. Sayaçlar şunlardır:  
  
- **HttpWebRequests Oluşturuldu/sn**  
  
- **HttpWebRequests Sıraya/sn**  
  
- **HttpWebRequests İptal /sn**  
  
- **HttpWebRequests Başarısız / sn**  
  
 **HttpWebRequests İptal/sn** sayacı için, <xref:System.Net.HttpWebRequest.Abort%2A> dahili aramalar da sayılır. Bu dahili çağrılar genellikle bir uygulamanın ölçmek isteyebileceği zaman eklerinden kaynaklanır.  
  
 **HttpWebRequests Failed/sec** sayacı, <xref:System.Net.HttpWebRequest> sunucudan saniyede başarısız bir durum kodu alan nesne sayısını içerir. Bu, isteğin sonunda Http sunucusundan alınan durum kodunun 200 ile 299 arasında aralıkta olmadığı anlamına gelir. İşlenen ve yeni bir istekle sonuçlanan durum kodları (örneğin, 401 Yetkisiz durum kodlarının çoğu) yeniden denemenin sonucuna bağlı olarak başarısız olur veya başarısız olmaz. Uygulama yeniden denemedayalı bir hata görürseniz, bu sayaç artımlı.  
  
 Ağ performans sayaçlarına <xref:System.Diagnostics.PerformanceCounter> <xref:System.Diagnostics> ad alanındaki ilgili sınıflar kullanılarak erişilebilir ve yönetilebilir. Ağ performans sayaçları, Windows Performance Monitor konsolu ile de görüntülenebilir.  
  
 Ağ performans sayaçlarının kullanılacak yapılandırma dosyasında etkinleştirilmesi gerekir. Yapılandırma dosyasında tek bir ayar la tüm ağ performans sayaçları etkin veya devre dışı bırakılır. Tek tek ağ performans sayaçları etkinleştirilemez veya devre dışı tutulamaz. Daha fazla bilgi için [ \<performanceCounter> Öğesi (Ağ Ayarları)](../configure-apps/file-schema/network/performancecounter-element-network-settings.md)bakın.  
  
 Ağ sayaçları etkinse, bu hem AppDomain başına hem de genel performans sayaçları oluşturur ve güncellenir. Devre dışı bırakılırsa, uygulama herhangi bir ağ performans sayacı verisağlamaz.  
  
 Performans sayaçları Kategoriler olarak gruplandırılır. Bir uygulama aşağıdaki örnek kodu ile tüm kategorileri listeleyebilir:  
  
```csharp
PerformanceCounterCategory[] Array = PerformanceCounterCategory.GetCategories();  
for (int i = 0; i < Array.Length; i++)  
{  
    Console.Out.WriteLine("{0}. Name={1} Help={2}", i, Array[i].CategoryName, Array[i].CategoryHelp);  
}  
```  
  
 Ağ performans sayaçları iki kategoride listelenir:  
  
- ".NET CLR Networking" - .NET Framework Version 2'de tanıtılan ve .NET Framework Version 2 ve sonraki sürümlerde desteklenen orijinal performans sayaçları.  
  
- ".NET CLR Networking 4.0.0.0" - Yukarıdaki soket sayaçlarının tümü artı .NET Framework Version 4 ve sonraki sürümlerde desteklenen yeni performans sayaçları. Bu yeni sayaçlar nesneler <xref:System.Net.HttpWebRequest> üzerinde performans bilgileri sağlar.  
  
 Bir uygulamadaki performans sayaçlarına erişim ve yönetme hakkında daha fazla bilgi için [Performans Sayaçları'na](performance-counters.md)bakın.  

## <a name="security-performance-counters"></a>Güvenlik performans sayaçları  
 Performans konsolu .NET CLR Güvenlik kategorisi, ortak dil çalışma zamanının bir uygulama için gerçekleştirdiği güvenlik denetimleri hakkında bilgi sağlayan sayaçlar içerir. Aşağıdaki tabloda bu performans sayaçları açıklanmaktadır.  
  
|Performans sayacı|Açıklama|  
|-------------------------|-----------------|  
|**# Bağlantı Zaman Kontrolleri**|Uygulama başladığından beri toplam bağlantı zamanı kodu erişim güvenlik denetimleri sayısını görüntüler. Bağlantı zamanı kodu erişim güvenlik denetimleri, arayan tam zamanında belirli bir izin istediğinde (JIT) derleme zamanı. Arayan başına bir kez bağlantı zamanı denetimi gerçekleştirilir. Bu sayım ciddi performans sorunlarının göstergesi değildir; yalnızca güvenlik sistemi etkinliğinin göstergesidir.|  
|**RT kontrollerinde % Süre**|Son örnekten bu yana runtime kodu erişim güvenlik denetimleri gerçekleştirmek için harcanan geçen süre yüzdesini görüntüler. Bu sayaç ,NET Framework güvenlik denetiminin sonunda güncelleştirilir. Bu bir ortalama değildir; son gözlenen değeri temsil eder.|  
|**% Zaman Sig Kimlik Doğrulama**|Daha sonraki kullanımlar için ayrılmıştır.|  
|**Yığın Yürüyüş Derinliği**|Son çalışma zamanı kodu erişim güvenlik denetimi sırasında yığının derinliğini görüntüler. Runtime kodu erişim güvenlik denetimleri yığını yürüyerek gerçekleştirilir. Bu sayaç bir ortalama değildir; yalnızca son gözlenen değeri gösterir.|  
|**Toplam Çalışma Süresi Denetimleri**|Uygulama başladığından beri gerçekleştirilen toplam çalışma zamanı kodu erişim güvenlik denetimleri sayısını görüntüler. Bir arayan belirli bir izin istediğinde runtime kodu erişim güvenlik denetimleri gerçekleştirilir. Çalışma zamanı denetimi, arayan tarafından her aramada yapılır ve arayanın geçerli iş parçacığı yığınını inceler. Stack Walk **Depth** sayacıile kullanıldığında, bu sayaç güvenlik denetimleri için oluşan performans cezasını gösterir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Performans Sayaçları](performance-counters.md)
- [Çalışma Zamanı Profili Oluşturma](runtime-profiling.md)
