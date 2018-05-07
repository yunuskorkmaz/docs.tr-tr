---
title: Çöp Toplama Bildirimleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- garbage collection, notifications
ms.assetid: e12d8e74-31e3-4035-a87d-f3e66f0a9b89
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3470ebdd55adc97a60f07228c441cb7c94a53e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="garbage-collection-notifications"></a>Çöp Toplama Bildirimleri
Bazı durumlarda, tam atık toplama (diğer bir deyişle, 2. nesil toplama) ortak dil çalışma zamanı tarafından performansını olumsuz etkileyebilir. Bu, özellikle büyük miktarda istekleri işlemek sunucuları ile ilgili bir sorun olabilir; Bu durumda, uzun çöp toplama istek zaman aşımı neden olabilir. Tam bir koleksiyon kritik bir dönem boyunca oluşmasını önlemek için tam atık toplama yaklaştığını ve iş yükünü başka bir sunucu örneğine yönlendirmek için önlem bildirilebilir. Geçerli sunucu örneğini istekleri işleyen gerekmez koşuluyla, ayrıca bir koleksiyon kendiniz anlamına.  
  
 <xref:System.GC.RegisterForFullGCNotification%2A> Yöntemi, tam atık toplama yaklaştığını çalışma zamanı algılayan tetiklenir için bildirimini kaydeder. Bu bildirim için iki bölümden oluşur: tam atık toplama yaklaştığı ne zaman ve ne zaman tam atık toplama tamamlandı.  
  
> [!WARNING]
>  Yalnızca engelleme çöp koleksiyonları bildirimleri yükseltin. Zaman [ \<gcConcurrent >](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) yapılandırma öğesi etkinleştirildiğinde, arka plan çöp koleksiyonları değil bildirimleri Yükselt.  
  
 Ne zaman bir uyarı oluşturuldu belirlemek için <xref:System.GC.WaitForFullGCApproach%2A> ve <xref:System.GC.WaitForFullGCComplete%2A> yöntemleri. Bu yöntemleri genellikle, kullandığınız bir `while` sürekli olarak almak için döngü bir <xref:System.GCNotificationStatus> bildirim durumunu gösteren sabit listesi. Bu değer ise <xref:System.GCNotificationStatus.Succeeded>, aşağıdakileri yapabilirsiniz:  
  
-   Yanıt ile elde edilen bir bildirim olarak <xref:System.GC.WaitForFullGCApproach%2A> yöntemi, iş yükü yönlendirebilir ve büyük olasılıkla bir koleksiyon kendiniz anlamına.  
  
-   Yanıt ile elde edilen bir bildirim olarak <xref:System.GC.WaitForFullGCComplete%2A> yöntemi, geçerli sunucu örneğini yeniden isteklerini işlemek kullanılabilir yapabilirsiniz. Ayrıca, bilgi toplayabilir. Örneğin, kullanabileceğiniz <xref:System.GC.CollectionCount%2A> koleksiyon sayısı kaydetmek için yöntem.  
  
 <xref:System.GC.WaitForFullGCApproach%2A> Ve <xref:System.GC.WaitForFullGCComplete%2A> yöntemleri birlikte çalışmak üzere tasarlanmıştır. Diğer olmadan kullanarak belirsiz sonuçlara yol açabilir.  
  
## <a name="full-garbage-collection"></a>Tam çöp toplama  
 Aşağıdaki senaryoların herhangi biri doğru olduğunda çalışma zamanı tam atık toplama neden olur:  
  
-   Yeterli bellek, sonraki 2. nesil koleksiyonu neden 2. nesil yükseltildi.  
  
-   Yeterli bellek, sonraki 2. nesil koleksiyonu neden büyük nesne yığın yükseltildi.  
  
-   2. nesil diğer etkenler nedeniyle koleksiyonu için 1. nesil koleksiyonu ilerletilen.  
  
 Belirttiğiniz eşikleri <xref:System.GC.RegisterForFullGCNotification%2A> yöntemi ilk iki senaryo için geçerlidir. Ancak, ilk senaryoda, her zaman bildirim için iki nedenden dolayı belirttiğiniz eşik değerleri orantılı zaman almaz:  
  
-   Çalışma zamanı her küçük nesne ayırma (performans nedenleriyle) denetlemez.  
  
-   Yalnızca 1 koleksiyonları nesil 2. nesil bellek yükseltin.  
  
 Üçüncü senaryo da bildirim aldığınızda, belirsizlik katkıda bulunur. Bu bir garantisi olmasa da bu süre boyunca istekleri yönlendirme ya da daha iyi yerleştirilebilecek zaman koleksiyon kendiniz inducing çıkarsanız tam atık toplama etkilerini azaltmak için kullanışlı bir yoldur kanıtlar.  
  
## <a name="notification-threshold-parameters"></a>Bildirim eşiği parametreleri  
 <xref:System.GC.RegisterForFullGCNotification%2A> Yöntemi kuşak 2 nesnelerinin ve büyük nesne yığın eşik değerlerini belirtmek için iki parametreye sahiptir. Bu değerleri karşılandığında bir atık toplama bildirim oluşmalıdır. Aşağıdaki tabloda bu parametreler açıklanmaktadır.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`maxGenerationThreshold`|Bildirim ne zaman oluşturulması belirten bir sayı 1 ile 99 arasında nesil 2 yükseltilmiş nesneleri temel.|  
|`largeObjectHeapThreshold`|Bildirim ne zaman oluşturulması belirten bir sayı 1 ile 99 arasında büyük nesne yığın ayrılmış nesneleri temel.|  
  
 Çok yüksek bir değer belirtirseniz, bir bildirim alırsınız, ancak bir koleksiyon çalışma zamanı neden olmadan önce beklenecek çok uzun bir süre olabilir yüksek olasılık yoktur. Bir koleksiyon kendiniz anlamına, çalışma zamanı koleksiyonu neden olursa iadesi daha çok nesne geri.  
  
 Çok düşük bir değer belirtirseniz, bildirim almak için yeterli süre beklendiğinden önce çalışma zamanı koleksiyonu neden olabilir.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnekte, bir sunucu grubu gelen Web isteklerini hizmet. İstek işleme yükünü benzetimini yapmak için bayt dizileri eklenir bir <xref:System.Collections.Generic.List%601> koleksiyonu. Her sunucu için bir atık toplama bildirimi kaydeder ve ardından üzerinde bir iş parçacığı başlatır `WaitForFullGCProc` sürekli olarak izlemek için kullanıcı yöntemi <xref:System.GCNotificationStatus> tarafından döndürülen numaralandırma <xref:System.GC.WaitForFullGCApproach%2A> ve <xref:System.GC.WaitForFullGCComplete%2A> yöntemleri.  
  
 <xref:System.GC.WaitForFullGCApproach%2A> Ve <xref:System.GC.WaitForFullGCComplete%2A> yöntemleri bir uyarı oluştuğunda kendi ilgili olay işleme kullanıcı yöntemlerini çağırın:  
  
-   `OnFullGCApproachNotify`  
  
     Bu yöntemi çağırır `RedirectRequests` gönderme askıya alma isteği queuing sunucusuna bildirir kullanıcı yöntemi sunucuya ister. Bu sınıf düzeyi değişkeni ayarlayarak benzetilir `bAllocate` için `false` böylece daha fazla nesne ayrılır.  
  
     İleri `FinishExistingRequests` kullanıcı yöntemi bekleyen sunucu isteklerini işlemini bitirmek için çağrılır. Bu temizleyerek benzetilir <xref:System.Collections.Generic.List%601> koleksiyonu.  
  
     Son olarak, iş yükü açık olduğundan çöp toplama işleminden.  
  
-   `OnFullGCCompleteNotify`  
  
     Bu yöntem kullanıcı yöntemini çağırır `AcceptRequests` istekleri kabul edip, sunucu artık bir tam atık toplama uygulanmadıkça olmadığı için devam etmek için. Bu eylem ayarlayarak benzetimli `bAllocate` değişkenini `true` nesnelerin eklenmesini devam edebilmeniz için <xref:System.Collections.Generic.List%601> koleksiyonu.  
  
 Aşağıdaki kodu içeren `Main` örnek yöntemi.  
  
 [!code-cpp[GCNotification#2](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#2)]
 [!code-csharp[GCNotification#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#2)]
 [!code-vb[GCNotification#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#2)]  
  
 Aşağıdaki kodu içeren `WaitForFullGCProc` çöp toplama bildirimleri için denetlemek için döngü sırasında sürekli içeren kullanıcı yöntemi.  
  
 [!code-cpp[GCNotification#8](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#8)]
 [!code-csharp[GCNotification#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#8)]
 [!code-vb[GCNotification#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#8)]  
  
 Aşağıdaki kodu içeren `OnFullGCApproachNotify` çağrılır gibi yöntemi  
  
 `WaitForFullGCProc` yöntem.  
  
 [!code-cpp[GCNotification#5](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#5)]
 [!code-csharp[GCNotification#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#5)]
 [!code-vb[GCNotification#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#5)]  
  
 Aşağıdaki kodu içeren `OnFullGCApproachComplete` çağrılır gibi yöntemi  
  
 `WaitForFullGCProc` yöntem.  
  
 [!code-cpp[GCNotification#6](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#6)]
 [!code-csharp[GCNotification#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#6)]
 [!code-vb[GCNotification#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#6)]  
  
 Aşağıdaki kod gelen adlı kullanıcı yöntemleri içeren `OnFullGCApproachNotify` ve `OnFullGCCompleteNotify` yöntemleri. Kullanıcı yöntemlerini yeniden yönlendirme istekleri, var olan istekleri bitiş ve tam atık toplama gerçekleştikten sonra istekleri Sürdür.  
  
 [!code-cpp[GCNotification#9](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#9)]
 [!code-csharp[GCNotification#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#9)]
 [!code-vb[GCNotification#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#9)]  
  
 Tüm kodu örneği aşağıdaki gibidir:  
  
 [!code-cpp[GCNotification#1](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#1)]
 [!code-csharp[GCNotification#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#1)]
 [!code-vb[GCNotification#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Atık Toplama](../../../docs/standard/garbage-collection/index.md)
