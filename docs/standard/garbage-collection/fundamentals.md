---
title: "Çöp Toplamanın Temelleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- garbage collection, generations
- garbage collection, background garbage collection
- garbage collection, concurrent garbage collection
- garbage collection, server garbage collection
- garbage collection, workstation garbage collection
- garbage collection, managed heap
ms.assetid: 67c5a20d-1be1-4ea7-8a9a-92b0b08658d2
caps.latest.revision: "51"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c3fe36e93cdea1315ee92f2dfdf76953511309a2
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="fundamentals-of-garbage-collection"></a>Çöp Toplamanın Temelleri
<a name="top"></a>Ortak dil çalışma zamanı (CLR), atık toplayıcı otomatik bellek yöneticisi olarak görev yapar. Aşağıdaki avantajları sağlar:  
  
-   Belleği serbest bırakmak zorunda kalmadan uygulamanızı geliştirmenizi sağlar.  
  
-   Yönetilen yığın nesnelerde verimli bir şekilde ayırır.  
  
-   Artık kullanılmayan nesneler kaldırsa, kendi bellek temizler ve gelecekteki ayırmalarının kullanılabilir bellek tutar. Kendi Oluşturucular, her veri alanı başlatma gerekmez. böylece yönetilen nesneleri otomatik olarak temiz içeriği ile başlamak alın.  
  
-   Bir nesne başka bir nesnenin içeriğini kullanamazsınız sağlayarak bellek güvenliği sağlar.  
  
 Bu konu, atık toplama temel kavramlarını açıklar. Aşağıdaki bölümleri içerir:  
  
-   [Bellek temelleri](#fundamentals_of_memory)  
  
-   [Çöp toplama için koşullar](#conditions_for_a_garbage_collection)  
  
-   [Yönetilen yığın](#the_managed_heap)  
  
-   [Nesli](#generations)  
  
-   [Çöp toplama sırasında ne olur?](#what_happens_during_a_garbage_collection)  
  
-   [Yönetilmeyen kaynakları düzenleme](#manipulating_unmanaged_resources)  
  
-   [İş istasyonu ve sunucu çöp toplama](#workstation_and_server_garbage_collection)  
  
-   [Eş zamanlı çöp toplama](#concurrent_garbage_collection)  
  
-   [Arka plan iş istasyonu çöp toplama](#background_garbage_collection)  
  
-   [Arka plan sunucu çöp toplama](#background_server_garbage_collection)  
  
<a name="fundamentals_of_memory"></a>   
## <a name="fundamentals-of-memory"></a>Bellek temelleri  
 Aşağıdaki listede önemli CLR bellek kavramlarını özetler.  
  
-   Her işlem, kendi, ayrı sanal adres alanı yok. Tüm işlemler aynı bilgisayarda aynı fiziksel bellek paylaşın ve varsa sayfasında dosya paylaşımı.  
  
-   32-bit bilgisayarlarda varsayılan olarak her işlem 2 GB kullanıcı modu sanal adres alanına sahip değil.  
  
-   Bir uygulama geliştiricisi olarak yalnızca sanal adres alanı ile çalışır ve hiçbir zaman fiziksel bellek doğrudan düzenleyebilirsiniz. Çöp toplayıcı ayırır ve sanal bellek sizin için yönetilen yığında boşaltır.  
  
     Yerel kod yazıyorsanız, sanal adres alanı ile çalışmak için Win32 işlevleri kullanın. Bu işlevler ayırın ve sanal bellek sizin için yerel üzerinde yığınlardaki boş.  
  
-   Sanal bellek üç durumda olabilir:  
  
    -   Boş. Bellek bloğu yok başvuruları sahiptir ve ayırma için kullanılamıyor.  
  
    -   Ayrılmış. Bellek bloğuna yönelik kullanımınız için kullanılabilir ve diğer ayırma isteği için kullanılamaz. Ancak, kaydedilmiş olana kadar bu bellek bloğu için verileri depolanamıyor.  
  
    -   Kaydedilmiş. Bellek bloğu fiziksel depolama birimine atanır.  
  
-   Sanal adres alanı parçalanmış. Adres alanında olarak da bilinen delik ücretsiz vardır Bunun anlamı engeller. Sanal bellek ayırma istendiğinde bu ayırma isteğini yerine getirmek için büyük tek bir ücretsiz blok bulmak sanal bellek yöneticisi sahiptir. 2 GB boş alan olsa bile, tüm bu boş olmadığı sürece bir tek adres bloğu içinde 2 GB gerektirir ayırma başarısız olur.  
  
-   Sanal adres alanı ayırmak için veya tamamlamaya fiziksel alanı dışında çalıştırırsanız, bellek yetersiz çalıştırabilirsiniz.  
  
 Fiziksel bellek baskısı (diğer bir deyişle, talep fiziksel bellek) düşük olsa bile, sayfa dosyası kullanılır. Fiziksel bellek baskısı yüksek olduğunda ilk kez işletim sistemi verilerini depolamak için fiziksel bellekte yer gerekir ve bunu bazı disk belleği dosyası fiziksel bellekte olan verileri yedekler. Disk belleği fiziksel bellek baskısı çok düşük olduğu durumlarda karşılaşabileceğiniz olası olacak şekilde veri kadar disk belleği değil, yeterli olur. 
 
 [Başa dön](#top)  
  
<a name="conditions_for_a_garbage_collection"></a>   
## <a name="conditions-for-a-garbage-collection"></a>Çöp toplama için koşullar  
 Çöp toplama aşağıdaki koşullardan biri doğru olduğunda oluşur:  
  
-   Sistem fiziksel belleği yetersizdir. Bu işletim sistemi uygulamasından düşük bellek bildirimi veya ana bilgisayar tarafından belirtilen düşük bellek tarafından algılandı.
  
-   Yönetilen yığında ayrılmış nesneleri tarafından kullanılan bellek kabul edilebilir bir eşik değerini geçiyor. İşlem çalışırken bu eşik sürekli olarak ayarlanır.  
  
-   <xref:System.GC.Collect%2A?displayProperty=nameWithType> Yöntemi çağrılır. Çöp toplayıcı sürekli olarak çalıştığı için neredeyse her durumda, bu yöntemi çağırmak yok. Bu yöntem, öncelikle benzersiz durumları ve test için kullanılır.  
  
 [Başa dön](#top)  
  
<a name="the_managed_heap"></a>   
## <a name="the-managed-heap"></a>Yönetilen yığın  
 Çöp toplayıcı CLR tarafından başlatıldıktan sonra bir segment depolamak ve nesneleri yönetmek için bellek ayırır. Bu bellek işletim sisteminde yerel bir yığın aksine Yönetilen yığın adı verilir.  
  
 Yönetilen yığın yönetilen her işlem için yok. İşlemdeki tüm iş parçacıklarının aynı yığında nesneler için bellek ayırın.  
  
 Bellek ayırma için Win32 atık toplayıcı çağırır [VirtualAlloc](http://go.microsoft.com/fwlink/?LinkId=179047) işlevi ve yönetilen uygulamalar için aynı anda belleğin bir kesim yedekler. Atık toplayıcı ayrıca kesimleri gerektiği gibi ayırır ve işletim sistemi geri segmentlere (bunları herhangi bir nesne temizledikten sonra) Win32 çağırarak serbest bırakır [VirtualFree](http://go.microsoft.com/fwlink/?LinkId=179050) işlevi.  
  
> [!IMPORTANT]
>  Çöp toplayıcı tarafından ayrılan Segment boyutu uygulamasına özeldir ve düzenli güncelleştirmeleri dahil olmak üzere, istediğiniz zaman değiştirilebilir. Uygulamanız hiçbir zaman hakkında varsayımlar olun veya belirli bir segmentle boyutuna göre değişir ve segment ayırmalarının kullanılabilir bellek miktarını yapılandırmak için denemeniz gerekir.  
  
 Çöp toplayıcı ilgilidir daha az iş yığında ayrılmış daha az nesne. Nesneleri ayırdığınızda, yalnızca 15 bayt gerektiğinde 32 bir bayt dizisi ayırma gibi gereksinimlerinizi aşan yuvarlanmış değerler kullanmayın.  
  
 Çöp toplama tetiklendiğinde atık toplayıcı ölü nesneleri tarafından kullanılıyor bellek geri kazanır. Reclaiming işlem böylece öbek küçülterek birlikte taşınır ve kullanılmayan alanı kaldırılır, böylece Canlı nesneleri sıkıştırır. Bu arada ayrılmasını nesneleri kendi yere göre korumak için yönetilen öbek üzerinde kalmasını sağlar.  
  
 Çöp koleksiyonları zorla girme (sıklığı ve süresi), ayırma birimi sonucunu ve yönetilen yığın derdi bitti bellek miktarı ' dir.  
  
 Öbek iki yığınlara toplamı değerlendirilebilir: büyük nesne yığın ve küçük nesne yığın.  
  
 Büyük nesne yığın 85. 000 bayt çok büyük nesneler içerir ve daha büyük. Büyük nesne yığın nesnelerde genellikle dizidir. Bir örnek nesne son derece büyük olacak şekilde nadir görülen bir durumdur.  
  
 [Başa dön](#top)  
  
<a name="generations"></a>   
## <a name="generations"></a>Nesli  
 Kısa süreli ve uzun süreli nesneleri işleyebilmesi için yığın kuşağın düzenlenmiştir. Çöp toplama, öbek küçük bir bölümünü genellikle kaplar kısa süreli nesneleri geri kazanma ile öncelikle oluşur. Öbek nesnelerde üç nesli vardır:  
  
-   **Kuşak 0**. Bu yeni nesil ve kısa süreli nesnelerini içerir. Kısa süreli bir nesne örneği geçici bir değişkendir. Çöp toplama bu oluşturma en sık oluşur.  
  
     Yeni ayrılmış nesneleri form nesneleri yeni nesil ve büyük nesneler olmadığı sürece örtük olarak kuşak 0, koleksiyonlarıdır; bu durumda, 2. nesil koleksiyonundaki büyük nesne yığın gidin.  
  
     Çoğu nesneyi kuşak 0'daki çöp koleksiyonu için geri ve İleri nesil varlığını sürdürmesini değil.  
  
-   **1. nesil**. Bu oluşturma kısa süreli nesnelerini içerir ve kısa süreli ve uzun süreli nesneleri arasında bir tampon görevi görür.  
  
-   **2. nesil**. Bu oluşturma uzun süreli nesnelerini içerir. Uzun süreli bir nesne örneği işlemi boyunca Canlı statik verileri içeren bir sunucu uygulaması bulunan bir nesnedir.  
  
 Koşullar garanti gibi belirli nesli üzerinde çöp koleksiyonlarının meydana. Bir oluşturma toplama nesneleri nesil ve tüm küçük nesli toplama anlamına gelir. Tüm nesli (diğer bir deyişle, tüm nesneler yönetilen yığınındaki) içindeki tüm nesneleri kaldırsa 2. kuşak atık toplama olarak da bilinen tam atık toplama, çünkü.  
  
### <a name="survival-and-promotions"></a>Acil ihtiyaç ve yükseltmeleri  
 Bir atık toplama kazanılır değil nesneler survivors adlandırılır ve yeni nesil yükseltilmiş. Bir kuşak 0 atık toplama varlığını sürdürmesini nesneleri 1. nesil için öne çıkar; nesil 1 çöp toplama varlığını sürdürmesini nesneleri 2. nesil için öne çıkar; ve 2. kuşak atık toplama varlığını sürdürmesini nesneleri 2. nesil kalır.  
  
 Bu nedenle atık toplayıcı algıladığında hayatta kalma oranı bir oluşturma yüksekse, nesil için ayırmaları eşiğinin artırır, sonraki koleksiyon iadesi bellek önemli boyutunu alır. CLR sürekli olarak iki öncelikleri dengeleyen: uygulamanın engelleyerek çok büyük ve not çok fazla zaman çöp toplama izin vererek ayarla al çalışma kullanıcının.  
  
### <a name="ephemeral-generations-and-segments"></a>Kısa ömürlü nesli ve kesimleri  
 0 ve 1 nesli nesneleri kısa süreli olduğundan, bu nesli kısa ömürlü nesli bilinir.  
  
 Kısa ömürlü nesli kısa ömürlü kesim olarak bilinen bellek kesimdeki ayrılmış olmalıdır. Çöp toplayıcı tarafından alınan her yeni bir segment yeni kısa ömürlü segment olur ve bir kuşak 0 atık toplama derdi bitti nesnelerini içerir. Eski kısa ömürlü segment yeni nesil 2 segment olur.  
  
 Kısa ömürlü kesim boyutu, 32 veya 64-bit, bir sistem olup olmadığını ve çalışıp atıktoplayıcı türü bağlı olarak değişir. Varsayılan değerleri aşağıdaki tabloda gösterilmiştir.  
  
||32 bit:|64 bit|  
|-|-------------|-------------|  
|İş istasyonu GC|16 MB|256 MB|  
|Sunucu GC|64 MB|4 GB|  
|Server GC > 4 mantıksal CPU|32 MB|2 GB|  
|> 8 GC sunucusuyla mantıksal CPU|16 MB|1 GB|  
  
 Kısa ömürlü segment kuşak 2 nesnelerinin içerebilir. 2. nesil nesneleri birden çok parçalı (sayıda işleminizi gerektirir ve bellek sağlar) kullanabilirsiniz.  
  
 Kısa ömürlü çöp toplama boşaltılmış bellekten miktarını kısa ömürlü kesim boyutunu sınırlıdır. Serbest bellek miktarı tarafından kullanılmayan nesneler kapladığı alanı orantılıdır.  
  
 [Başa dön](#top)  
  
<a name="what_happens_during_a_garbage_collection"></a>   
## <a name="what-happens-during-a-garbage-collection"></a>Çöp toplama sırasında ne olur?  
 Çöp toplama aşağıdaki aşamadan oluşur:  
  
-   Bulur ve tüm Canlı nesnelerin bir listesini oluşturan bir işaretleme aşamasında.  
  
-   Sıkıştırılmış nesneleri başvuruları güncelleştirmeleri relocating aşaması.  
  
-   Ölü nesneleriyle kapladığı alanı geri kazanır ve geri kalan nesneleri sıkıştırır sıkıştırma aşaması. Sıkıştırma aşaması kesim eski sonuna doğru bir atık toplama derdi bitti nesneleri taşır.  
  
     2. nesil koleksiyonları birden çok parçalı kaplar çünkü 2. nesil yükseltilmiş nesneleri daha eski bir kesimi taşınabilir. 2. nesil için öne çıkar çünkü 1. nesil ve 2. nesil survivors farklı bir segmente taşınabilir.  
  
     Büyük nesneleri kopyalama performans cezası getirir çünkü normalde, büyük nesne yığın, sıkıştırıldıktan değil. Ancak, başlayarak [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], kullanabileceğiniz <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> isteğe bağlı büyük nesne yığın sıkıştırmak için özellik.  
  
 Çöp toplayıcı nesneleri canlı olup olmadığını belirlemek için aşağıdaki bilgileri kullanır:  
  
-   **Yığın kökleri**. Tam zamanında (JIT) derleyici ve yığın walker tarafından sağlanan değişkenleri yığın.  
  
-   **Çöp toplama tanıtıcıları**. Kullanıcı kodu veya ortak dil çalışma zamanı tarafından yönetilen nesneleri noktasına ve, ayrılabilen işler.  
  
-   **Statik veri**. Diğer nesneler başvuran uygulama etki alanlarında statik nesneleri. Her uygulama etki alanı, statik nesnelerini izler.  
  
 Çöp toplama başlamadan önce tüm yönetilen iş parçacığı çöp toplama tetiklenen iş parçacığı dışında askıya alınır.  
  
 Çöp toplama tetikler ve askıya alınmasına başka bir iş parçacığı neden olan bir iş parçacığı aşağıda gösterilmektedir.  
  
 ![Ne zaman bir iş parçacığı tetikleyen bir atık toplama](../../../docs/standard/garbage-collection/media/gc-triggered.png "GC_Triggered")  
Çöp toplama tetikler iş parçacığı  
  
 [Başa dön](#top)  
  
<a name="manipulating_unmanaged_resources"></a>   
## <a name="manipulating-unmanaged-resources"></a>Yönetilmeyen kaynakları düzenleme  
 Yerel dosya tanıtıcıları kullanarak yönetilen nesnelerinizi yönetilmeyen nesnelerine başvuru atık toplayıcı yalnızca yönetilen yığında bellek izlediğinden açıkça yönetilmeyen nesneleri boşaltmak varsa.  
  
 Kullanıcılar yönetilen nesnenizin nesne tarafından kullanılan yerel kaynakları dispose değil. Temizleme işlemini gerçekleştirmek için Yönetilen Nesne sonlandırılabilir olarak yapabilirsiniz. Nesne artık kullanımda olduğunda, yürütme temizleme işlemleri sonlandırma oluşur. Yönetilen Nesne sonlandıktan sonra kendi sonlandırıcıyı yönteminde belirtilen temizleme eylemleri gerçekleştirir.  
  
 Bir sonlandırılabilir ölü olmasını bulunduğunda, kendi sonlandırıcıyı temizleme eylemlerini yürütülür, ancak nesne için yeni nesil yükseltilir böylece sıraya konur. Bu nedenle, (olmayan mutlaka sonraki çöp toplama) nesil üzerinde gerçekleşen sonraki çöp toplama kadar beklemek zorunda nesne iadesi olup olmadığını belirlemek için.  
  
 [Başa dön](#top)  
  
<a name="workstation_and_server_garbage_collection"></a>   
## <a name="workstation-and-server-garbage-collection"></a>İş istasyonu ve sunucu çöp toplama  
 Çöp toplayıcı kendi kendini ayarlayabilir durumdadır ve çok çeşitli senaryoları çalışabilirsiniz. İş yükü özellikler temelinde çöp toplama türünü ayarlamak için bir yapılandırma dosyası ayarı kullanabilirsiniz. CLR çöp toplama aşağıdaki türlerini sağlar:  
  
-   Tüm istemci iş istasyonları ve tek başına bilgisayarlar için iş istasyonu çöp toplama. İçin varsayılan ayar budur [ \<gcServer > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) çalışma zamanı yapılandırma şemasında.  
  
     İş istasyonu çöp toplama eşzamanlı veya eşzamanlı olmayan olabilir. Eşzamanlı atık toplama işlemleri sırasında bir atık toplama devam etmek yönetilen iş parçacığı sağlar.  
  
     İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], arka plan çöp toplama eşzamanlı atık toplama yerini alır.  
  
-   Yüksek verimlilik ve ölçeklenebilirlik gereken sunucu uygulamaları için hedeflenen sunucu çöp toplama. Sunucu çöp toplama eşzamanlı olmayan veya arka plan.  
  
 Aşağıdaki çizimde bir sunucuda çöp toplama gerçekleştirmek adanmış iş parçacığı gösterir.  
  
 ![Sunucu çöp toplama iş parçacığı](../../../docs/standard/garbage-collection/media/gc-server.png "GC_Server")  
Sunucu çöp toplama  
  
### <a name="configuring-garbage-collection"></a>Çöp toplama yapılandırma  
 Kullanabileceğiniz [ \<gcServer > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) çöp toplama türünü belirtmek için çalışma zamanı yapılandırma şeması gerçekleştirmek için CLR istiyor. Bu öğenin `enabled` özniteliği `false` (varsayılan), iş istasyonu çöp toplama CLR gerçekleştirir. Ayarladığınızda `enabled` özniteliğini `true`, CLR sunucu çöp toplama gerçekleştirir.  
  
 Eşzamanlı atık toplama ile belirtilen [ \<gcConcurrent > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) çalışma zamanı yapılandırma şeması. Varsayılan ayar `enabled`. Bu ayar, her iki eşzamanlı denetler ve arka plan çöp toplama.  
  
 Sunucu çöp toplama ile yönetilmeyen barındırma arabirimleri de belirtebilirsiniz. Uygulamanız bu ortamları birini içinde barındırılıyorsa, ASP.NET ve SQL Server sunucu çöp toplama otomatik olarak etkinleştirdiğini unutmayın.  
  
### <a name="comparing-workstation-and-server-garbage-collection"></a>İş istasyonu ve sunucu çöp toplama karşılaştırma  
 İş istasyonu çöp toplama için iş parçacığı oluşturma ve performans konuları şunlardır:  
  
-   Çöp toplama ve aynı önceliğe bırakılmalıdır tetiklenen kullanıcı iş parçacığı üzerinde koleksiyon oluşur. Kullanıcı iş parçacıkları genellikle normal öncelikli olarak çalıştığından, (Bu, normal öncelikli iş parçacığı üzerinde çalışan) atık toplayıcı CPU süresi için başka bir iş parçacığı ile rekabet gerekir.  
  
     Yerel kod çalışan iş parçacıklarının askıya değil.  
  
-   İş istasyonu çöp toplama bağımsız olarak, yalnızca bir işlemciye sahip bir bilgisayarda kullanılan her zaman [ \<gcServer >](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) ayarı. Sunucu çöp toplama belirtirseniz, CLR iş istasyonu çöp toplama devre dışı eşzamanlılık ile kullanır.  
  
 Sunucu çöp toplama için iş parçacığı oluşturma ve performans konuları şunlardır:  
  
-   Koleksiyon konumunda çalışan birden fazla adanmış iş parçacığı meydana gelme `THREAD_PRIORITY_HIGHEST` öncelik düzeyi.  
  
-   Yığın ve atık toplama gerçekleştirmek için adanmış bir iş parçacığı her CPU için sağlanır ve aynı anda yığınlara toplanır. Her yığın küçük nesne yığın ve büyük nesne yığın içerir ve tüm yığın kullanıcı kodu tarafından erişilebilir. Farklı yığın nesnelerde birbirlerine başvurabilir.  
  
-   Birden çok atık toplama iş parçacığı birlikte çalışması için sunucu çöp toplama iş istasyonu çöp toplama aynı boyutu yığında hızlıdır.  
  
-   Sunucu çöp toplama genellikle daha büyük boyutu kesimler vardır. Ancak, bunun yalnızca Genelleştirme olduğunu unutmayın: kesim boyutu uygulamasına özeldir ve değiştirilebilir. Uygulamanızı ayarlama atık toplayıcısı tarafından tahsis kesimleri boyutu hakkında hiçbir varsayımlar olmanız gerekir.  
  
-   Sunucu çöp toplama yoğun bir kaynak olabilir. Örneğin, 4 işlemciye sahip bir bilgisayarda çalışan 12 işlemler varsa, olacaktır 48 ayrılmış atık toplama iş parçacıklarının tüm sunucu çöp toplama kullanıyorlarsa. Çöp toplama yapılması tüm işlemler başlatırsanız, yüksek bellek yükü durumda zamanlamak için 48 iş parçacığı atık toplayıcı sahip olur.  
  
 Uygulama örnekleri yüzlerce çalıştırıyorsanız, iş istasyonu çöp toplama devre dışı eşzamanlı atık toplama ile kullanmayı düşünün. Bu daha az içerik geçişi içinde performansı artırmak neden olacaktır.  
  
 [Başa dön](#top)  
  
<a name="concurrent_garbage_collection"></a>   
## <a name="concurrent-garbage-collection"></a>Eş zamanlı çöp toplama  
 İş istasyonu veya sunucu çöp toplama, toplama süresi çoğu için atık toplama gerçekleştiren adanmış bir iş parçacığı ile aynı anda çalıştırmak için iş parçacığı sağlar eşzamanlı atık toplama etkinleştirebilirsiniz. Bu seçenek yalnızca çöp koleksiyonları nesil 2 etkiler; çok hızlı tamamlamak için 0 ve 1 nesli eşzamanlı olmayan her zaman.  
  
 Eşzamanlı atık toplama daha iyi yanıt olarak bir koleksiyon için duraklatır en aza indirerek etkileşimli uygulamaları etkinleştirir. Yönetilen iş parçacığı eşzamanlı atık toplama iş parçacığı çalışırken çoğu zaman çalıştırmaya devam edebilirsiniz. Çöp toplama gerçekleştirildiği sırada bu içinde daha kısa duraklatır sonuçlanır.  
  
 Çeşitli işlemler çalıştırırken performansı artırmak için eşzamanlı atık toplama devre dışı bırakın. Bunu ekleyerek yapabilirsiniz bir [ \<gcConcurrent > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) uygulamanın yapılandırma dosyasında hem de değerini ayarlamak için kendi `enabled` özniteliğini `"false"`.  
  
 Eşzamanlı atık toplama, adanmış bir iş parçacığı üzerinde gerçekleştirilir. Varsayılan olarak, CLR iş istasyonu çöp toplama etkin eşzamanlı atık toplama ile çalışır. Bu, tek işlemcili ve birden çok işlemcili bilgisayarlar için geçerlidir.  
  
 Eşzamanlı atık toplama başladığında kısa ömürlü kesiminde kalan nesneler tarafından eşzamanlı atık toplama sırasında küçük nesneleri yığınındaki ayırma yeteneği sınırlıdır. Segmentinin sonunu ulaşmak hemen eşzamanlı atık toplama küçük nesne ayırmaları yapmak zorunda yönetilen iş parçacığı askıya sırada bitmesini bekleyin gerekecektir.  
  
 Eşzamanlı toplama sırasında nesneleri ayırabilirsiniz olduğundan eşzamanlı atık toplama (eşzamansız atık toplama ile karşılaştırıldığında) biraz daha büyük bir çalışma kümesi vardır. Ancak, tahsis nesneler çalışma kümesinin bir parçası haline çünkü bu performansını etkileyebilir. Esas olarak, bazı CPU ve bellek kısa duraklamalar için eş zamanlı çöp toplama trades.  
  
 Aşağıdaki çizimde, ayrı adanmış bir iş parçacığı üzerinde gerçekleştirilen eşzamanlı atık toplama gösterir.  
  
 ![Eşzamanlı atık toplama iş parçacığı](../../../docs/standard/garbage-collection/media/gc-concurrent.png "GC_Concurrent")  
Eş zamanlı çöp toplama  
  
 [Başa dön](#top)  
  
<a name="background_garbage_collection"></a>   
## <a name="background-workstation-garbage-collection"></a>Arka plan iş istasyonu çöp toplama  
 Arka plan çöp toplama (0 ve 1) kısa ömürlü nesil 2. nesil koleksiyonu işlemi devam ederken gerektiğinde toplanır. Arka plan çöp toplama için hiçbir ayar yoktur; eşzamanlı atık toplama ile otomatik olarak etkinleştirilir. Arka plan çöp toplama eşzamanlı atık toplama bir yerini alır. Eşzamanlı atık toplama ile arka plan çöp toplama adanmış bir iş parçacığı üzerinde gerçekleştirilir ve yalnızca 2. nesil koleksiyonları için geçerlidir.  
  
> [!NOTE]
>  Arka plan çöp toplama, yalnızca kullanılabilir [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] ve sonraki sürümler. İçinde [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], yalnızca iş istasyonu çöp toplama için desteklenir. .NET Framework 4. 5'ile başlayarak, arka plan çöp toplama iş istasyonu ve sunucu atık toplama için kullanılabilir.  
  
 Arka plan çöp toplama sırasında kısa ömürlü nesli bir koleksiyonda ön plan çöp toplama bilinir. Ön plan çöp koleksiyonlarının meydana geldiğinde, tüm yönetilen iş parçacıklarını askıya alınır.  
  
 Arka plan çöp toplama devam ederken ve kuşak 0 veya ayrılmış yeterli nesneleri, CLR kuşak 0 veya nesil 1 ön plan çöp toplama gerçekleştirir. Ön plan çöp toplama için bir istek olup olmadığını belirlemek için sık güvenli noktalarında ayrılmış arka plan çöp toplama iş parçacığı denetler. Varsa, ön plan çöp toplama gerçekleştirilmesi arka plan toplama kendisini askıya alır. Ön plan çöp toplama tamamlandıktan sonra adanmış bir arka plan çöp toplama iş parçacığı ve kullanıcı iş parçacıklarını sürdürme.  
  
 Kısa ömürlü çöp koleksiyonları arka plan çöp toplama sırasında olabileceği için arka plan çöp toplama eşzamanlı atık toplama tarafından uygulanan ayırma kısıtlamaları kaldırır. Bu arka plan çöp toplama ölü nesneleri kısa ömürlü kuşakta kaldırabilir ve Öbek nesil 1 çöp toplama sırasında gerekirse genişletebilirsiniz anlamına gelir.  
  
 Aşağıdaki çizimde, bir iş istasyonunda ayrı adanmış iş parçacığı üzerinde gerçekleştirilen arka plan çöp toplama gösterir.  
  
 ![Arka plan iş istasyonu çöp toplama](../../../docs/standard/garbage-collection/media/backgroundworkstn.png "BackgroundWorkstn")  
Arka plan iş istasyonu çöp toplama  
  
 [Başa dön](#top)  
  
<a name="background_server_garbage_collection"></a>   
## <a name="background-server-garbage-collection"></a>Arka plan sunucu çöp toplama  
 .NET Framework 4. 5'ile başlayarak, arka plan sunucu çöp toplama için varsayılan sunucu çöp toplama moddur. Bu mod seçmek için ayarlanmış `enabled` özniteliği [ \<gcServer > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) için `true` çalışma zamanı yapılandırma şemasında. Bu mod işlevleri arka plan iş istasyonu çöp toplama, benzer şekilde önceki bölümde açıklanan, ancak bazı farklar vardır. Arka plan sunucu çöp toplama genellikle bir adanmış iş parçacığı her mantıksal işlemci için birden çok iş parçacığı kullanırken bir adanmış arka plan çöp toplama iş parçacığı, arka plan iş istasyonu çöp toplama kullanır. İş istasyonu arka plan çöp toplama iş parçacığı, bu iş parçacıkları süresi dolmaz.  
  
 Aşağıdaki çizimde bir sunucuda ayrı adanmış iş parçacığı üzerinde gerçekleştirilen arka plan çöp toplama gösterir.  
  
 ![Sunucu çöp toplama arka plan](../../../docs/standard/garbage-collection/media/backgroundserver.png "BackgroundServer")  
Arka plan sunucu çöp toplama  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Atık Toplama](../../../docs/standard/garbage-collection/index.md)
