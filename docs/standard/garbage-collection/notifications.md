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
ms.openlocfilehash: cc4850ff87d9ea827e86a16ee6b3a6953c1e3552
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64622701"
---
# <a name="garbage-collection-notifications"></a>Çöp Toplama Bildirimleri
Bazı durumlarda, ortak dil çalışma zamanı tarafından tam çöp toplama (diğer bir deyişle, 2. nesil koleksiyonu) performansını olumsuz yönde etkileyebilir. Bu, özellikle büyük hacimlerde istekleri işleyebilir sunucuları ile ilgili bir sorun olabilir. Bu durumda, uzun bir çöp toplama, istek zaman aşımı neden olabilir. Tam koleksiyonu bir kritik süre içinde oluşmasını önlemek için tam çöp toplama işleminin yaklaşmakta olduğunun ve eylem iş yükünü başka bir sunucu örneğine yeniden yönlendirmek için bildirim alabilirsiniz. Koşuluyla isteklerini işlemek geçerli sunucu örneği gerekmez, ayrıca koleksiyon kendiniz zorlarsınız.  
  
 <xref:System.GC.RegisterForFullGCNotification%2A> Yöntemi, bir tam çöp toplama işleminin yaklaşmakta olduğunun çalışma zamanı algılayan, oluşturulacak bildirim kaydeder. Bu bildirim için iki bölümden oluşur: ne zaman tam çöp toplama işleminin yaklaşmakta olduğunun ve ne zaman tam çöp toplama tamamlandı.  
  
> [!WARNING]
>  Yalnızca engelleme atık toplama bildirimleri yükseltin. Zaman [ \<gcConcurrent >](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) yapılandırma öğesi etkin olduğunda, arka plan atık toplama olmayan bildirimleri Yükselt.  
  
 Ne zaman bir bildiriminin tetiklendiğini belirlemek için <xref:System.GC.WaitForFullGCApproach%2A> ve <xref:System.GC.WaitForFullGCComplete%2A> yöntemleri. Bu yöntemleri genellikle, kullandığınız bir `while` döngü sürekli olarak almak için bir <xref:System.GCNotificationStatus> bildirim durumunu gösteren sabit listesi. Bu değer ise <xref:System.GCNotificationStatus.Succeeded>, aşağıdakileri yapabilirsiniz:  
  
- Bir bildirim ile alınan yanıtta <xref:System.GC.WaitForFullGCApproach%2A> yöntemi, iş yükü yönlendirmek ve büyük olasılıkla bir koleksiyon kendiniz anlamına.  
  
- Bir bildirim ile alınan yanıtta <xref:System.GC.WaitForFullGCComplete%2A> yöntemi, geçerli sunucu örneği istekleri yeniden işleyecek duruma kullanılabilir yapabilirsiniz. Ayrıca, bilgi toplayabilir. Örneğin, kullanabileceğiniz <xref:System.GC.CollectionCount%2A> koleksiyon sayısına kaydetmek için yöntemi.  
  
 <xref:System.GC.WaitForFullGCApproach%2A> Ve <xref:System.GC.WaitForFullGCComplete%2A> yöntemleri, birlikte çalışmak üzere tasarlanmıştır. Biri diğeri olmadan kullanarak belirsiz sonuçlara neden olabilir.  
  
## <a name="full-garbage-collection"></a>Tam çöp toplama  
 Aşağıdaki senaryolardan biri doğru olduğunda, çalışma zamanı tam çöp toplama neden olur:  
  
- Yeterli bellek, sonraki 2. nesil koleksiyonu neden 2. nesle yükseltildi.  
  
- Yeterli bellek, sonraki 2. nesil koleksiyonu neden büyük nesne yığını yükseltildi.  
  
- 1. nesil koleksiyonu 2. nesil diğer faktörler nedeniyle koleksiyonunu üzere ilerletilmiş.  
  
 Belirttiğiniz eşikleri <xref:System.GC.RegisterForFullGCNotification%2A> yöntemi ilk iki senaryo için geçerlidir. Ancak, ilk senaryoda, her zaman bildirim için iki nedenden dolayı zaman belirttiğiniz eşik değerleri orantılı almaz:  
  
- Çalışma zamanı, her küçük nesne ayırma (performans nedenleriyle) denetlemez.  
  
- Yalnızca 1 koleksiyonları kuşak 2. nesle bellek tanıtın.  
  
 Üçüncü senaryo da bildirim aldığınızda, belirsizlik katkıda bulunur. Bu bir garantisi olmasa da bu süre boyunca istekleri yönlendirme ya da daha iyi yerleştirilebilecek olduğunda koleksiyon kendiniz inducing çıkarsanız tam çöp toplama etkilerini azaltmak için kullanışlı bir yoldur anlamına gelmez.  
  
## <a name="notification-threshold-parameters"></a>Bildirim eşiği parametreleri  
 <xref:System.GC.RegisterForFullGCNotification%2A> Yöntemi 2. nesil nesneler ve büyük nesne yığını eşik değerlerini belirtmek için iki parametreye sahiptir. Bu değerleri karşılandığında bir çöp toplama bildirim oluşmalıdır. Aşağıdaki tabloda, bu parametreler açıklanmaktadır.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`maxGenerationThreshold`|Yükseltilen kuşak 2 nesneleri ne zaman bildirim harekete Geçirilmemesi gereken belirten bir sayı 1 ile 99 arasında temel.|  
|`largeObjectHeapThreshold`|Bildirim zaman harekete Geçirilmemesi gereken belirten bir sayı 1 ile 99 arasında büyük nesne yığınında ayrılmış nesneleri temel.|  
  
 Çok yüksek bir değer belirtirseniz, bir bildirim alırsınız, ancak çalışma zamanı bir koleksiyon neden olmadan önce beklenecek çok uzun bir süre olabilir yüksek olasılık yoktur. Kendiniz bir koleksiyon anlamına, koleksiyonu çalışma zamanı neden olursa kazanılacak çok daha fazla nesne geri kazan.  
  
 Çok düşük bir değer belirtirseniz, çalışma zamanı, bildirim almak için yeterli zamana önce koleksiyonu neden olabilir.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnekte, bir sunucu grubu, gelen Web isteklerini hizmeti. İstekleri işleme iş yükünün benzetimini yapmak için bayt dizileri için eklenen bir <xref:System.Collections.Generic.List%601> koleksiyonu. Her sunucu çöp toplama bildirim için kaydeder ve sonra üzerinde bir iş parçacığı başlattığını `WaitForFullGCProc` sürekli olarak izlemek için kullanıcı yöntemi <xref:System.GCNotificationStatus> tarafından döndürülen sabit listesi <xref:System.GC.WaitForFullGCApproach%2A> ve <xref:System.GC.WaitForFullGCComplete%2A> yöntemleri.  
  
 <xref:System.GC.WaitForFullGCApproach%2A> Ve <xref:System.GC.WaitForFullGCComplete%2A> bir uyarı ortaya çıktığında kendi ilgili olay işleme kullanıcı yöntemlerini yöntemlerini çağırın:  
  
- `OnFullGCApproachNotify`  
  
     Bu yöntemin çağırdığı `RedirectRequests` istekleri sunucuya gönderme askıya alma isteği sıraya alma sunucusuna bildirir kullanıcı yöntemi. Bu sınıf düzeyi değişkenleri ayarlayarak benzetimli `bAllocate` için `false` böylece daha fazla nesne ayrılır.  
  
     Ardından, `FinishExistingRequests` bekleyen sunucu istekleri işlemeyi tamamlamak için kullanıcı yöntemi çağrılır. Bu temizleyerek benzetimli <xref:System.Collections.Generic.List%601> koleksiyonu.  
  
     Son olarak, iş yükü açık olduğundan bir atık toplama işlemi başlattı.  
  
- `OnFullGCCompleteNotify`  
  
     Bu yöntem kullanıcı yöntemini çağırır `AcceptRequests` sunucusu artık tam çöp toplama için açık olduğundan, istekleri kabul sürdürmek için. Bu eylem ayarlayarak benzetimli `bAllocate` değişkenini `true` eklenen nesneleri devam edebilmeniz için <xref:System.Collections.Generic.List%601> koleksiyonu.  
  
 Aşağıdaki kodu içeren `Main` örnek yöntemi.  
  
 [!code-cpp[GCNotification#2](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#2)]
 [!code-csharp[GCNotification#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#2)]
 [!code-vb[GCNotification#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#2)]  
  
 Aşağıdaki kodu içeren `WaitForFullGCProc` while döngüsü için çöp toplama bildirimleri denetlemek için bir sürekli içeren kullanıcı yöntemi.  
  
 [!code-cpp[GCNotification#8](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#8)]
 [!code-csharp[GCNotification#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#8)]
 [!code-vb[GCNotification#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#8)]  
  
 Aşağıdaki kodu içeren `OnFullGCApproachNotify` çağrılır olarak yöntemi  
  
 `WaitForFullGCProc` yöntem.  
  
 [!code-cpp[GCNotification#5](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#5)]
 [!code-csharp[GCNotification#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#5)]
 [!code-vb[GCNotification#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#5)]  
  
 Aşağıdaki kodu içeren `OnFullGCApproachComplete` çağrılır olarak yöntemi  
  
 `WaitForFullGCProc` yöntem.  
  
 [!code-cpp[GCNotification#6](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#6)]
 [!code-csharp[GCNotification#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#6)]
 [!code-vb[GCNotification#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#6)]  
  
 Gelen adlı kullanıcı yöntemleri aşağıdaki kodu içeren `OnFullGCApproachNotify` ve `OnFullGCCompleteNotify` yöntemleri. Kullanıcı yöntemlerini yeniden yönlendirme istekleri, mevcut isteklerini tamamlamak ve sonra bir tam çöp toplama işlemi gerçekleştirildikten sonra istek'i sürdüremedi.  
  
 [!code-cpp[GCNotification#9](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#9)]
 [!code-csharp[GCNotification#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#9)]
 [!code-vb[GCNotification#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#9)]  
  
 Tüm kod örneği aşağıdaki gibidir:  
  
 [!code-cpp[GCNotification#1](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#1)]
 [!code-csharp[GCNotification#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#1)]
 [!code-vb[GCNotification#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Atık Toplama](../../../docs/standard/garbage-collection/index.md)
