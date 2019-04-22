---
title: Çöp toplamanın temelleri
description: Çöp toplayıcı nasıl çalıştığını ve en iyi performans için nasıl yapılandırılabileceğini öğrenin.
ms.date: 03/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, generations
- garbage collection, background garbage collection
- garbage collection, concurrent garbage collection
- garbage collection, server garbage collection
- garbage collection, workstation garbage collection
- garbage collection, managed heap
ms.assetid: 67c5a20d-1be1-4ea7-8a9a-92b0b08658d2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f6dcd8e47fcbbee1e17e9e9ca1cb93f6076b4475
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58826606"
---
# <a name="fundamentals-of-garbage-collection"></a>Çöp toplamanın temelleri
<a name="top"></a> Ortak dil çalışma zamanı (CLR), çöp toplayıcı otomatik bellek yöneticisi görev yapar. Bunu, aşağıdaki avantajları sağlar:  
  
-   Belleği boşaltmak zorunda kalmadan uygulamanızı geliştirmenizi sağlar.  
  
-   Yönetilen yığında nesneleri verimli şekilde ayırır.  
  
-   Artık kullanılmayan nesneleri geri kazanır, temizler ve belleği gelecekteki ayırmalar için kullanılabilir kalmasını sağlar. Oluşturucuları her veri alanını başlatmak zorunda değil yönetilen nesneleri otomatik olarak temiz içerik ile başlamak alın.  
  
-   Bir nesne başka bir nesnenin içeriğini kullanamazsınız sağlayarak bellek emniyet sağlar.  
  
 Bu konuda, çöp toplama işleminin temel kavramlar açıklanmaktadır. 
 
<a name="fundamentals_of_memory"></a>   
## <a name="fundamentals-of-memory"></a>Bellek temelleri  
 Aşağıdaki liste önemli CLR belleği kavramlarını özetlemektedir.  
  
-   Her işlem, kendi ayrı sanal adres alanı vardır. Aynı bilgisayardaki tüm işlemler aynı fiziksel belleği paylaşır ve varsa sayfa dosyasını paylaşır.  
  
-   Varsayılan olarak 32-bit bilgisayarlarda her işlem 2 GB kullanıcı modu sanal adres alanı vardır.  
  
-   Bir uygulama geliştiricisi olarak yalnızca sanal adres alanı ile çalışır ve hiçbir zaman fiziksel belleği doğrudan düzenlemezsiniz. Çöp toplayıcı ayırır ve sanal bellek yönetilen yığında sizin için serbest bırakır.  
  
     Yerel kod yazıyorsanız, sanal adres alanı ile çalışmak için Win32 işlevlerini kullanın. Bu işlevler, ayırabilir ve sanal belleği sizin için yerel yığınlarda ücretsiz.  
  
-   Sanal bellek, üç durumda olabilir:  
  
    -   Ücretsiz. Bellek bloğunun hiçbir başvurusu bulunmamaktadır ve ayırma için kullanılabilir.  
  
    -   Ayrılmış. Bellek bloğunu kullanabilirsiniz ve başka bir ayırma isteği için kullanılamaz. Ancak, kaydedilinceye kadar veri bu bellek bloğunda depolayamazsınız.  
  
    -   Taahhüt. Bellek bloğu fiziksel depolama alanına atanır.  
  
-   Sanal adres alanı parçalanabilir. Olarak da bilinir adres alanında delik ücretsiz vardır Bunun anlamı engeller. Sanal bellek ayırma istendiğinde, sanal bellek yöneticisinin ayırma isteğini karşılamak için yeterince büyük tek bir serbest öbek bulması gerekir. 2 GB boş alan olsa bile, bir tek adres bloğu içinde tüm bu boş alan sürece 2 GB gerektiren ayırma başarısız olur.  
  
-   Ayrılacak sanal adres alanınız veya kullanılabilecek fiziksel alanınız dışında çalıştırırsanız, bellek yetersiz çalıştırabilirsiniz.  
  
 Fiziksel bellek baskısı (diğer bir deyişle, fiziksel bellek talep) az olsa sayfa dosyanız kullanılır. Fiziksel bellek baskısının arttığı ilk kez işletim sistemi verilerin depolanacağı fiziksel bellekte yer açmak gerekir ve bu disk belleği dosyası fiziksel bellekte olan verilerin bazıları yedekler. Fiziksel bellek baskısının çok düşük olduğu durumlarda disk belleği karşılaşmak mümkündür veri kadar disk belleğine alınan değil, yeterli olur. 
 
 [Başa dön](#top)  
  
<a name="conditions_for_a_garbage_collection"></a>   
## <a name="conditions-for-a-garbage-collection"></a>Bir çöp toplama koşulları  
 Çöp toplama, aşağıdaki koşullardan biri doğru olduğunda oluşur:  
  
-   Sistem fiziksel belleği yetersizdir. Bu işletim sisteminden düşük bellek bildirimi ya da konak tarafından belirtilen bellek algılandı.
  
-   Yönetilen yığında ayrılmış nesneler tarafından kullanılan bellek kabul edilebilir bir eşik değerini geçiyor. İşlem çalışırken bu eşik sürekli olarak ayarlanır.  
  
-   <xref:System.GC.Collect%2A?displayProperty=nameWithType> Yöntemi çağrılır. Çöp toplayıcı sürekli çalıştığı için hemen hemen tüm durumlarda, bu yöntemi çağırmanız gerekmez. Bu yöntem öncelikle benzersiz durumlar ve sınamak için kullanılır.  
  
 [Başa dön](#top)  
  
<a name="the_managed_heap"></a>   
## <a name="the-managed-heap"></a>Yönetilen yığın  
 Çöp toplayıcı CLR tarafından başlatıldıktan sonra nesneleri depolamak ve yönetmek için bellek segmentini ayırır. Bu bellek işletim sisteminde yerel bir yığın yerine yönetilen yığında denir.  
  
 Yönetilen her işlem için bir yönetilen yığın yok. İşlemdeki tüm iş parçacıkları, aynı yığındaki nesneler için bellek ayrılamadı.  
  
 Bellek ayırmak için atık toplayıcısı Win32 çağırır [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) işlevi ve segmentini ayırır yönetilen uygulamalar için aynı anda bellek. Çöp toplayıcı da parçaları gerektiği gibi ayırır ve Win32 çağırarak parçaları için işletim sisteminde (bunları tüm nesnelerden temizledikten sonra) sürümleri [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) işlevi.  
  
> [!IMPORTANT]
>  Boyutu çöp toplayıcısının ayrılan parçaların uygulamaya özgü ve düzenli güncelleştirmeleri dahil olmak üzere dilediğiniz zaman değiştirilebilir. Uygulamanız hiçbir zaman hakkında varsayımlar veya belirli bir segment boyutuna göre değişir ve segment ayırma için kullanılabilir bellek miktarını yapılandırmak için denemeniz gerekir.  
  
 Çöp toplayıcı yapmak için iş yığın üzerinde ayrılan daha az nesne. Nesneleri ayırdığınızda, yalnızca 15 bayt'a gereksinim duyduğunuzda, bir dizi 32 bayt ayırma gibi gereksinimlerinizi aşan yuvarlanmış değerler kullanmayın.  
  
 Bir atık toplama işlemi tetiklendiğinde, çöp toplayıcı, etkin olmayan nesnelerin kapladığı belleği geri kazanır. Geri kazanma işlemi Canlı nesneleri küçülterek birlikte taşınır ve ölü boşluk kaldırılır, böylece öbek küçültülür. Bu, birlikte ayrılan nesnelerin yerleşimlerinin korunması için yönetilen yığında birlikte kalmasını sağlar.  
  
 Ne kadar zorlayıcı olduğunu (sıklığı ve süresi) çöp koleksiyonları sonucu ayırmaların hacminin ve yönetilen yığındaki kalan bellek miktarı ' dir.  
  
 Yığın, iki yığın birikmesi kabul edilebilir: [büyük nesne yığını](large-object-heap.md) ve küçük nesne yığını.  
  
 [Büyük nesne yığını](large-object-heap.md) 85.000 bayt çok geniş nesneleri içerir ve daha büyük. Büyük nesne yığını üzerindeki nesneler genellikle dizilerdir. Bir örnek nesne için çok büyük olmak nadir olarak rastlanıyor.  
  
 [Başa dön](#top)  
  
<a name="generations"></a>   
## <a name="generations"></a>Nesiller  
 Uzun süreli ve süreli nesneleri işleyebilmesi için yığın kuşaklar halinde düzenlenir. Çöp toplama, öncelikle genellikle yığın küçük bir bölümünü kaplayan kısa süreli nesneleri geri kazanma ile oluşur. Üç kuşak nesne yığını üzerindeki vardır:  
  
-   **Nesil 0**. Bu yeni nesildir ve süreli nesnelerini içerir. Kısa süreli bir nesne örneği geçici bir değişkendir. Çöp toplama en çok sıklıkla bu nesilde oluşur.  
  
     Yeni ayrılan nesneler yeni nesil nesneler oluşturmak ve büyük nesneler oldukları sürece dolaylı olarak kuşak 0 koleksiyonlarıdır bu durumda bunlar kuşak 2 koleksiyonundaki büyük nesne yığını üzerindeki gidin.  
  
     Çoğu nesneyi, nesil 0 çöp toplama için kazanılır ve gelecek oluşturmaya kadar varlığını sürdürmez.  
  
-   **1. kuşak**. Bu nesil süreli nesneleri içerir ve süreli ve uzun süreli nesneler arasında bir tampon görevi görür.  
  
-   **2. nesil**. Bu, uzun süreli nesneler içerir. Uzun süreli bir nesne örneği, bir sunucu uygulamasında işlem süresi boyunca Canlı olan statik verileri içeren bir nesnedir.  
  
 Çöp toplama işlemi, koşullar garantiledikçe belirli nesillerde oluşur. Nesil toplama, o nesildeki ve tüm genç nesillerdeki nesnelerin toplanması anlamına gelir. (Diğer bir deyişle yönetilen Yığındaki tüm nesneler) tüm nesillerdeki tüm nesneleri sahiplendiğinden bir nesil 2 çöp toplama, tam çöp toplama, ayrıca olarak bilinir.  
  
### <a name="survival-and-promotions"></a>Acil ihtiyaç ve promosyonlar  
 Bir çöp toplama geri olmayan nesneler, survivor olarak bilinir ve sonraki nesle yükseltilir. Bir nesil 0 çöp toplamadan nesneler, kuşak 1 yükseltilir; kuşak 1 çöp toplamadan nesneler, kuşak 2 yükseltilir; ve 2. nesil çöp toplamadan nesneler, kuşak 2 kalır.  
  
 Bu nedenle çöp toplayıcı algıladığında hayatta kalma oranı yüksek, bu ayırma eşiğini o nesle ilişkin sonraki toplamayı önemli bir geri Kazanılan bellek boyutunu alır. CLR sürekli olarak iki önceliği dengeler: uygulamanın uygulamanın çalışma çok büyük ve değil, çok fazla zaman alabileceğini çöp toplama izin kümesi Al.  
  
### <a name="ephemeral-generations-and-segments"></a>Kısa ömürlü nesiller ve Segmentler  
 0 ile 1 nesil nesneler kısa süreli olduğundan, bu nesiller kısa ömürlü nesiller olarak bilinir.  
  
 Kısa ömürlü nesiller kısa ömürlü segment olarak bilinen bellek segmentinde ayrılmalıdır. Çöp toplayıcısı tarafından alınan her yeni segment, yeni kısa ömürlü segment olur ve bir nesil 0 çöp toplamadan kurtulan nesneleri içerir. Eski kısa ömürlü segment yeni kuşak 2 segment olur.  
  
 Kısa ömürlü Segment boyutu, 32 veya 64-bit bir sistem olup olmadığını ve üzerinde çalıştığı atıktoplayıcı türüne bağlı olarak değişir. Varsayılan değerleri aşağıdaki tabloda gösterilmektedir.  
  
||32 bit:|64 bit|  
|-|-------------|-------------|  
|GC iş istasyonu|16 MB|256 MB|  
|Server GC|64 MB|4 GB|  
|GC sunucusuyla > 4 mantıksal CPU|32 MB|2 GB|  
|Sunucu GC > 8 ile mantıksal CPU|16 MB|1 GB|  
  
 Kısa ömürlü segment kuşak 2 nesneleri içerebilir. 2. nesil nesneler birden çok çok Segment (işleminiz gerektirdiği ve belleğiniz izin verdiği gibi) kullanabilirsiniz.  
  
 Kısa ömürlü atık toplamanın boşaltılmış bellek miktarı kısa ömürlü Segment boyutuyla sınırlıdır. Serbest bellek miktarı ölü nesneleri tarafından kaplanan alanı orantılıdır.  
  
 [Başa dön](#top)  
  
<a name="what_happens_during_a_garbage_collection"></a>   
## <a name="what-happens-during-a-garbage-collection"></a>Bir çöp toplama sırasında ne olur?  
 Bir çöp toplama aşağıdaki aşamaları içerir:  
  
-   Bulur ve tüm Canlı nesnelerin bir listesini oluşturan bir işaretleme aşaması.  
  
-   Sıkıştırılacak nesnelere başvuruları güncelleştiren bir yeniden konumlandırma aşaması.  
  
-   Ölü nesneler tarafından kaplanan alanı geri kazanır ve canlı nesneleri sıkıştıran bir sıkıştırma aşaması. Sıkıştırma aşaması parçanın eski ucuna doğru bir çöp toplamadan kurtulan nesneleri taşır.  
  
     2. nesil koleksiyonlar birden çok kesimi kaplayabileceğinden, 2. nesle yükseltilen nesneler daha eski bir kesime taşınabilir. Hem 1. nesil ve 2. nesil Dışarıda Kalanlar, 2. nesil için yükseltildiğinden farklı bir kesime taşınabilir.  
  
     Büyük nesneleri kopyalama bir performans cezası uygular çünkü normalde, büyük nesne yığını sıkıştırılmamıştır. Ancak, başlayarak [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], kullanabileceğiniz <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> üzerine büyük nesne yığınını sıkıştırmak için özellik.  
  
 Çöp toplayıcı nesnelerin Canlı olup olmadığını belirlemek için aşağıdaki bilgileri kullanır:  
  
-   **Yığın kökleri**. Just-ın-time (JIT) derleyici ve yığın yürüyüşçüsü tarafından sağlanan yığın değişkenleri. JIT iyileştirmelerini uzatın veya bölgeleri hangi yığın değişkenleri çöp Toplayıcıya raporlanır kısaltın unutmayın.
  
-   **Çöp toplama göstergelerinin**. Kullanıcı koduna veya ortak dil çalışma zamanı tarafından yönetilen nesneleri işaret ve, ayrılabilen işler.  
  
-   **Statik veri**. Diğer nesnelere başvurma uygulama alanlarındaki statik nesneler. Her uygulama etki alanı, statik nesnelerini izler.  
  
 Bir çöp toplama işlemi başlamadan önce tüm yönetilen iş parçacıkları Çöp toplamayı tetikleyen iş parçacığı dışında askıya alınır.  
  
 Aşağıdaki resimde bir atık toplama işlemini tetikleyen ve yakında askıya alınacak diğer iş parçacıklarını neden olan bir iş parçacığı gösterilmektedir.  
  
 ![Bir iş parçacığı bir atık toplama işlemi tetiklendiğinde](../../../docs/standard/garbage-collection/media/gc-triggered.png "GC_Triggered")  
Çöp toplama tetikleyen iş parçacığı  
  
 [Başa dön](#top)  
  
<a name="manipulating_unmanaged_resources"></a>   
## <a name="manipulating-unmanaged-resources"></a>Yönetilmeyen kaynakları düzenleme  
 Yönetilen nesneleriniz yerel dosya tanıtıcıları kullanılarak yönetilmeyen nesneleri başvuru atık toplayıcı yalnızca yönetilen yığında bellek izlediğinden yönetilmeyen nesneleri açıkça boşaltılacak varsa.  
  
 Yönetilen nesnenizin kullanıcıları, nesne tarafından kullanılan yerel kaynakları atmayabilir. Temizleme işlemini gerçekleştirmek için yönetilen nesnenizi sonlandırılabilir yapabilirsiniz. Sonlandırma, nesne artık kullanımda olmadığında yürüttüğünüz temizleme eylemlerinden oluşur. Yönetilen nesneniz sonlandığında, kendi Sonlandırıcı yönteminde belirtilen temizleme eylemlerini gerçekleştirir.  
  
 Sonlandırılabilir bir nesnenin etkin olmadığı anlaşıldığında, nesnenin Sonlandırıcısı böylece temizleme eylemleri yürütülür, ancak nesnenin kendisi sonraki nesle yükseltilir sıraya konur. (Bu mutlaka bir sonraki atık koleksiyonuna değildir) bu nesil oluşan bir sonraki atık koleksiyonuna kadar beklemek zorunda bu nedenle nesnenin geri kazanılıp kazanılmadığını belirlemek için.  
  
 [Başa dön](#top)  
  
<a name="workstation_and_server_garbage_collection"></a>   
## <a name="workstation-and-server-garbage-collection"></a>İş istasyonu ve sunucu çöp toplama  
 Çöp toplayıcı kendi kendini ayarlayabilir ve çok çeşitli senaryolarda çalışabilir. İş yükü özelliklerine dayanan çöp toplama türünü ayarlamak için yapılandırma dosyası ayarı kullanabilirsiniz. CLR çöp toplama aşağıdaki türlerini sağlar:  
  
-   Tüm istemci iş istasyonları ve tek başına çalışan bilgisayarlar için iş istasyonu çöp toplama. İçin varsayılan ayar budur [ \<gcServer > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) çalışma zamanı yapılandırma şemasında.  
  
     İş istasyonu çöp toplama, eşzamanlı veya eşzamansız olabilir. Eş zamanlı çöp toplama, yönetilen iş parçacıklarının çöp toplama sırasında işlemleri devam etmek sağlar.  
  
     İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], arka plan çöp toplama, eşzamanlı çöp toplama değiştirir.  
  
-   Yüksek performans ve ölçeklenebilirlik gerektiren sunucu uygulamaları için tasarlanmış sunucu çöp toplama. Sunucu çöp toplama, eşzamansız ya da arka plan.  
  
 Bir sunucuda atık toplama işini gerçekleştirmek adanmış iş parçacığı aşağıda gösterilmiştir.  
  
 ![Sunucu çöp toplama iş parçacıklarını](../../../docs/standard/garbage-collection/media/gc-server.png "GC_Server")  
Sunucu çöp toplama  
  
### <a name="configuring-garbage-collection"></a>Çöp toplamayı yapılandırma  
 Kullanabileceğiniz [ \<gcServer > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) CLR'nin gerçekleştirmesini istediğiniz çöp toplama türünü belirtmek için çalışma zamanı yapılandırma şemasının. Bu öğenin `enabled` özniteliği `false` (varsayılan), CLR iş istasyonu atık toplama gerçekleştirir. Ayarladığınızda `enabled` özniteliğini `true`, CLR sunucu atık toplama gerçekleştirir.  
  
 Eş zamanlı çöp toplama belirtilirse [ \<gcConcurrent > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) çalışma zamanı yapılandırma şemasının. Varsayılan ayar `enabled`. Bu ayar, her iki eşzamanlı denetler ve arka plan çöp toplama.  
  
 Yönetilmeyen barındırma arabirimleri ile sunucu çöp toplama da belirtebilirsiniz. Uygulamanız bu ortamların biri içinde barındırılıyorsa ASP.NET ve SQL Server sunucu çöp toplama otomatik olarak etkinleştirdiğine dikkat edin.  
  
### <a name="comparing-workstation-and-server-garbage-collection"></a>İş istasyonu ve sunucu Çöp toplamayı karşılaştırma  
 İş istasyonu çöp toplama iş parçacığı oluşturma ve performans değerlendirmeleri şunlardır:  
  
-   Toplama, aynı öncelik düzeyinde kalır ve çöp toplama tetikleyen kullanıcı iş parçacığı üzerinde oluşur. Kullanıcı iş parçacıkları genellikle normal öncelikte çalıştığından (Bu, normal öncelikli iş parçacığında çalışır) çöp toplayıcısı CPU süresi için diğer iş parçacıkları ile rekabet etmelidir.  
  
     Yerel kod çalıştıran iş parçacıkları askıya alınmaz.  
  
-   İş istasyonu çöp toplama bağımsız olarak, tek bir işlemci olan bir bilgisayarda her zaman kullanılır [ \<gcServer >](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) ayarı. Sunucu çöp toplama belirtirseniz, CLR eşzamanlılığın devre dışı olduğu iş istasyonu Çöp toplamayı kullanır.  
  
 Sunucu çöp toplama iş parçacığı oluşturma ve performans hakkında önemli noktalar şunlardır:  
  
-   Çalışan birden çok adanmış iş parçacığı üzerinde toplama oluşur `THREAD_PRIORITY_HIGHEST` öncelik düzeyi.  
  
-   Bir yığın ve çöp toplama için adanmış bir iş parçacığı her CPU için sağlanır ve aynı anda yığınlar toplanır. Her bir yığın küçük nesne yığını ve bir büyük nesne yığını içerir ve tüm yığınlara kullanıcı kodu tarafından erişilebilir. Farklı yığınlardaki nesneler birbirlerine başvurabilir.  
  
-   Birden çok çöp toplama iş parçacığı birlikte çalıştığından, sunucu çöp toplama iş istasyonu çöp toplama aynı boyutu yığındaki daha hızlıdır.  
  
-   Sunucu çöp toplama genellikle büyük boy segmentler içerir. Ancak, bu yalnızca bir Genelleştirme olduğunu unutmayın: kesim boyutunu uygulamaya özgü ve değişikliğe tabidir. Uygulamanızı ayarlarken çöp toplayıcısının ayrılan segmenti boyutu hakkında hiçbir varsayım olmanız gerekir.  
  
-   Sunucu çöp toplama yoğun kaynak olabilir. Örneğin, 4 işlemci bulunan bir bilgisayarda çalışan 12 işlem varsa, olacaktır 48 adanmış çöp toplama iş parçacıklarını tüm sunucu çöp toplama kullanıyorsanız. Tüm işlemler çöp toplamaya başlarsa, yüksek bellek yükleme durumunda, çöp toplayıcının zamanlayacak 48 iş parçacığı olacaktır.  
  
 Yüzlerce uygulama örneğini çalıştırıyorsanız, iş istasyonu çöp toplama, eşzamanlı çöp toplama devre dışı kullanarak göz önünde bulundurun. Bu daha az bağlam geçişiyle içinde performansın iyileşmesini sağlayabilecek neden olur.  
  
 [Başa dön](#top)  
  
<a name="concurrent_garbage_collection"></a>   
## <a name="concurrent-garbage-collection"></a>Eş zamanlı çöp toplama  
 İş istasyonu veya sunucu çöp toplama işleminde eş zamanlı çöp toplama, eşzamanlı atık toplama gerçekleştirir koleksiyon süresinin çoğu için adanmış bir iş parçacığı çalıştırmak iş parçacığı sağlayan etkinleştirebilirsiniz. Bu seçenek yalnızca çöp koleksiyonları kuşak 2 etkiler; çok hızlı için nesil 0 ve 1 her zaman eşzamanlı değildir.  
  
 Eş zamanlı çöp toplama, daha hızlı yanıt verdiğini bir koleksiyon için duraklamaları en aza indirerek etkileşimli uygulamaların sağlar. Yönetilen iş parçacıklarının eş zamanlı çöp toplama iş parçacığı çalışırken çoğu zaman çalışmaya devam edebilirsiniz. Bir çöp toplama oluştuğu sırada bu kısa duraklamaları sonuçlanır.  
  
 Birçok işlem çalışırken performansı artırmak için eşzamanlı atık toplamayı devre dışı. Bunu ekleyerek yapabilirsiniz bir [ \<gcConcurrent > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) uygulamanın yapılandırma dosyası ve değerini ayarlama, `enabled` özniteliğini `"false"`.  
  
 Eş zamanlı çöp toplama, adanmış bir iş parçacığı üzerinde gerçekleştirilir. Varsayılan olarak CLR, eşzamanlı çöp toplama etkin iş istasyonu çöp toplama çalışır. Bu, tek işlemci ve çok işlemcili bilgisayarlar için geçerlidir.  
  
 Eşzamanlı atık toplama başladığında kısa ömürlü segmenti kalan nesneler tarafından eş zamanlı çöp toplama sırasında yığındaki küçük nesneleri olanağınız sınırlı. Kesimin sonuna ulaştığınız anda, küçük nesne ayırma işlemleri yapması gereken yönetilen iş parçacıkları askıya alınırken eş zamanlı Çöp toplamayı beklemeniz gerekecektir.  
  
 Eş zamanlı toplama sırasında nesneler ayırabildiğiniz için eş zamanlı çöp toplama (eşzamanlı olmayan çöp toplamaya kıyasla) biraz daha büyük bir çalışma kümesi vardır. Ancak ayırdığınız nesneler, çalışma kümenizin bir parçası haline gelir çünkü bu performansını etkileyebilir. Aslında, eş zamanlı çöp toplama CPU ve daha kısa duraklamalar için bellek arasında denge kurar.  
  
 Aşağıdaki çizim, ayrı bir adanmış iş parçacığı üzerinde gerçekleştirilen eşzamanlı atık toplama gösterir.  
  
 ![Eş zamanlı çöp toplama iş parçacıklarını](../../../docs/standard/garbage-collection/media/gc-concurrent.png "GC_Concurrent")  
Eş zamanlı çöp toplama  
  
 [Başa dön](#top)  
  
<a name="background_garbage_collection"></a>   
## <a name="background-workstation-garbage-collection"></a>Arka plan iş istasyonu çöp toplama  
 Arka plan çöp toplamada, kısa ömürlü nesiller (0 ve 1) 2. nesil koleksiyonu işlemi devam ederken gerektiği gibi toplanır. Arka plan çöp toplama için hiçbir ayar yoktur; eş zamanlı çöp toplama ile otomatik olarak etkinleştirilir. Arka plan çöp toplama, eşzamanlı çöp toplamanın yerini almıştır. Eş zamanlı çöp toplama ile arka plan çöp toplama adanmış bir iş parçacığı üzerinde gerçekleştirilir ve yalnızca 2. nesil koleksiyonlar için geçerlidir.  
  
> [!NOTE]
>  Arka plan çöp toplama yalnızca [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] ve sonraki sürümler. İçinde [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], yalnızca iş istasyonu çöp toplama için desteklenir. .NET Framework 4.5 ile başlayarak, arka plan çöp toplama hem iş istasyonu ve sunucu çöp toplama için kullanılabilir.  
  
 Arka plan çöp toplama sırasında kısa ömürlü nesillerdeki bir koleksiyon, ön plan çöp toplama koleksiyonu olarak bilinir. Ön plan atık toplamaları olduğunda, tüm yönetilen iş parçacıkları askıya alınır.  
  
 Arka plan atık toplama devam ederken ve nesil 0 yeterli nesne ayırmış olmanız, CLR oluşturma 0 veya oluşturma 1 ön plan atık toplama gerçekleştirir. Ön plan çöp toplama için bir istek olup olmadığını belirlemek için sık güvenli noktalarında adanmış arka plan çöp toplama iş parçacığı denetler. Varsa, ön plan çöp toplama gerçekleştirilmesi arka plan koleksiyonu kendisini askıya alır. Ön plan çöp toplama işlemi tamamlandıktan sonra adanmış arka plan çöp toplama iş parçacığı ve kullanıcı iş parçacıkları sürdürün.  
  
 Arka plan çöp toplama sırasında kısa ömürlü çöp toplamalar oluşabileceğinden arka plan çöp toplama, eşzamanlı çöp toplamadan kaynaklanan ayırma kısıtlamalarını kaldırır. Başka bir deyişle, arka plan atık toplama ölü nesneleri kısa ömürlü nesillerde kaldırabilir ve Öbek kuşaktaki 1 atık toplama sırasında gerekirse genişletebilirsiniz.  
  
Aşağıdaki resimde bir iş istasyonunda ayrı adanmış iş parçacığı üzerinde gerçekleştirilen arka plan atık toplama gösterilmektedir:
  
 ![Arka plan iş istasyonu çöp toplama gösteren diyagram.](./media/fundamentals/background-workstation-garbage-collection.png)
   
 [Başa dön](#top)  
  
<a name="background_server_garbage_collection"></a>   
## <a name="background-server-garbage-collection"></a>Arka plan sunucusu çöp toplama  
 .NET Framework 4.5 ile başlayarak, arka plan sunucusu çöp toplama için varsayılan sunucu çöp toplama moddur. Bu modu seçmek için ayarlanmış `enabled` özniteliği [ \<gcServer > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) için `true` çalışma zamanı yapılandırma şemasında. Bu modu işlevlerine benzer şekilde arka plan iş istasyonu çöp toplama, önceki bölümde açıklanan, ancak bazı farklar vardır. Arka plan iş istasyonu atık toplama arka plan sunucusu çöp toplama, genellikle bir adanmış iş parçacığı her mantıksal işlemci için birden çok iş parçacığı kullanan bir adanmış arka plan çöp toplama iş parçacığı kullanır. İş istasyonu arka plan çöp toplama iş parçacığının tersine, bu iş parçacıkları zamanaşımına uğramaz.  
  
 Aşağıdaki resimde, bir sunucuda ayrı adanmış iş parçacığı üzerinde gerçekleştirilen arka plan atık toplama gösterilmektedir:  
  
 ![Arka plan sunucusu çöp toplama gösteren diyagram.](./media/fundamentals/background-server-garbage-collection.png)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Atık Toplama](../../../docs/standard/garbage-collection/index.md)
