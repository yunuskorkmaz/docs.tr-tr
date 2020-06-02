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
ms.openlocfilehash: 389e851782edb82578c216951be440070b92723c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286008"
---
# <a name="garbage-collection-notifications"></a>Çöp Toplama Bildirimleri
Ortak dil çalışma zamanı ile tam çöp toplamanın (yani 2. nesil bir koleksiyon) performansı olumsuz etkileyebileceği durumlar vardır. Bu, özellikle büyük hacimli istekleri işleyen sunucularla ilgili bir sorun olabilir; Bu durumda, uzun bir atık toplama bir istek zaman aşımına neden olabilir. Kritik bir süre boyunca tam bir koleksiyonun oluşmasını önlemek için, tam bir çöp toplamanın yaklaştığı ve iş yükünü başka bir sunucu örneğine yeniden yönlendirmek için işlem gerçekleştirilecek şekilde bir uyarı alabilirsiniz. Ayrıca, geçerli sunucu örneğinin istekleri işlemesini gerektirmeyen bir koleksiyonu kendiniz de yazabilirsiniz.  
  
 <xref:System.GC.RegisterForFullGCNotification%2A>Yöntemi, çalışma zamanı tam çöp toplama işlemini yaklaştığında bir bildirimin bir bildirimine kaydolur. Bu bildirimin iki bölümü vardır: tam çöp toplama yaklaşıyorsa ve tam çöp toplama tamamlandığında.  
  
> [!WARNING]
> Yalnızca atık koleksiyonları engelleme bildirimleri yükseltir. [\<gcConcurrent>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)Yapılandırma öğesi etkinleştirildiğinde, arka plan atık koleksiyonları bildirim oluşturmaz.  
  
 Bir bildirimin ne zaman kabarık olduğunu anlamak için <xref:System.GC.WaitForFullGCApproach%2A> ve <xref:System.GC.WaitForFullGCComplete%2A> yöntemlerini kullanın. Genellikle, `while` <xref:System.GCNotificationStatus> bildirim durumunu gösteren bir sabit listesi elde etmek için bu yöntemleri bir döngüde kullanırsınız. Bu değer ise, şunları yapabilirsiniz <xref:System.GCNotificationStatus.Succeeded> :  
  
- Yöntemiyle elde edilen bir bildirime yanıt olarak <xref:System.GC.WaitForFullGCApproach%2A> , iş yükünü yeniden yönlendirebilir ve muhtemelen bir koleksiyonu kendiniz bulabilirsiniz.  
  
- Yöntemiyle elde edilen bir bildirime yanıt olarak <xref:System.GC.WaitForFullGCComplete%2A> , geçerli sunucu örneğini istekleri yeniden işlemek için kullanılabilir hale getirebilirsiniz. Ayrıca, bilgi toplayabilirsiniz. Örneğin, <xref:System.GC.CollectionCount%2A> koleksiyon sayısını kaydetmek için yöntemini kullanabilirsiniz.  
  
 <xref:System.GC.WaitForFullGCApproach%2A>Ve <xref:System.GC.WaitForFullGCComplete%2A> yöntemleri birlikte çalışmak üzere tasarlanmıştır. Diğeri olmadan kullanmak, belirsiz sonuçlar doğurabilir.  
  
## <a name="full-garbage-collection"></a>Tam çöp toplama  
 Aşağıdaki senaryolardan herhangi biri doğru olduğunda, çalışma zamanı tam çöp toplamaya neden olur:  
  
- Bir sonraki nesil 2 toplamaya neden olacak şekilde 2. nesil bir bellek yükseltildi.  
  
- Bir sonraki nesil 2 toplamaya neden olmak için büyük nesne yığınına yeterli bellek yükseltildi.  
  
- 1. nesil bir koleksiyon, diğer faktörler nedeniyle 2. nesil bir toplamaya ilerletildi.  
  
 Yönteminde belirttiğiniz eşikler <xref:System.GC.RegisterForFullGCNotification%2A> ilk iki senaryo için geçerlidir. Ancak, ilk senaryoda bildirimi her zaman, iki nedenden dolayı belirttiğiniz eşik değerleriyle orantılı şekilde almazsınız:  
  
- Çalışma zamanı her küçük nesne ayırmayı denetlemez (performans nedenleriyle).  
  
- Yalnızca 1. nesil koleksiyonlar belleği 2. nesil olarak yükseltir.  
  
 Ayrıca üçüncü senaryo, bildirimi alacağınız zaman açıklanmayacak şekilde katkıda bulunur. Bu bir garanti olmamasına karşın, bu süre boyunca istekleri yeniden yönlendirerek veya daha iyi bir hale gelebileceği zaman koleksiyonu kendiniz gerçekleştirerek, inopportune tam çöp toplamanın etkilerini azaltmak için faydalı bir yol olduğunu kanıtlamaz.  
  
## <a name="notification-threshold-parameters"></a>Bildirim eşiği parametreleri  
 <xref:System.GC.RegisterForFullGCNotification%2A>Yöntemi 2. nesil nesnelerin eşik değerlerini ve büyük nesne yığınını belirtmek için iki parametreye sahiptir. Bu değerler karşılandığında bir çöp toplama bildirimi oluşturulmalıdır. Aşağıdaki tabloda bu parametreler açıklanmaktadır.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`maxGenerationThreshold`|2. nesil üzerinde yükseltilen nesneler temelinde bildirimin ne zaman oluşturulması gerektiğini belirten, 1 ile 99 arasında bir sayı.|  
|`largeObjectHeapThreshold`|Büyük nesne yığınında ayrılan nesneler temelinde bildirimin ne zaman oluşturulması gerektiğini belirten, 1 ile 99 arasında bir sayı.|  
  
 Çok yüksek bir değer belirtirseniz, bir bildirim almanız, ancak çalışma zamanı bir koleksiyona neden olması için çok uzun bir süre olabilir. Bir koleksiyonu kendiniz kullandıysanız, çalışma zamanı koleksiyona neden olursa daha fazla nesne geri kazanırsınız.  
  
 Çok düşük bir değer belirtirseniz çalışma zamanı, bildirim almak için yeterli zamana girmeden önce koleksiyona neden olabilir.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Description  
 Aşağıdaki örnekte, bir sunucu grubu gelen Web istekleri hizmetidir. İstekleri işleme iş yükünün benzetimini yapmak için, bir koleksiyona bayt dizileri eklenir <xref:System.Collections.Generic.List%601> . Her sunucu bir çöp toplama bildirimine kaydolduktan sonra `WaitForFullGCProc` <xref:System.GCNotificationStatus> , ve yöntemleri tarafından döndürülen numaralandırmayı sürekli olarak izlemek için Kullanıcı yönteminde bir iş parçacığı başlatır <xref:System.GC.WaitForFullGCApproach%2A> <xref:System.GC.WaitForFullGCComplete%2A> .  
  
 <xref:System.GC.WaitForFullGCApproach%2A>Ve yöntemleri, <xref:System.GC.WaitForFullGCComplete%2A> bir bildirim oluşturulduğunda ilgili olay işleme Kullanıcı yöntemlerini çağırır:  
  
- `OnFullGCApproachNotify`  
  
     Bu yöntem, `RedirectRequests` istek Kuyruklama sunucusuna istekleri sunucuya göndermeyi askıya almaya yönlendiren Kullanıcı yöntemini çağırır. Bu, sınıf düzeyi değişkeni, `bAllocate` `false` daha fazla nesne ayrılmaması için olarak ayarlanarak benzetilir.  
  
     Ardından, `FinishExistingRequests` bekleyen sunucu isteklerini işlemeyi tamamlayacak Kullanıcı yöntemi çağırılır. Bu, koleksiyonu temizleyerek benzetilir <xref:System.Collections.Generic.List%601> .  
  
     Son olarak, iş yükü hafif olduğundan bir çöp toplama işlemi yapılır.  
  
- `OnFullGCCompleteNotify`  
  
     Bu yöntem, `AcceptRequests` sunucu artık tam bir atık toplama için savunmasız olmadığından istekleri kabul etmek için Kullanıcı yöntemini çağırır. Bu eylem, `bAllocate` `true` nesnenin koleksiyona eklenmeyi sürdürmesini sağlamak için değişkeni olarak ayarlanarak benzetilir <xref:System.Collections.Generic.List%601> .  
  
 Aşağıdaki kod, `Main` Örneğin yöntemini içerir.  
  
 [!code-cpp[GCNotification#2](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#2)]
 [!code-csharp[GCNotification#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#2)]
 [!code-vb[GCNotification#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#2)]  
  
 Aşağıdaki kod `WaitForFullGCProc` , atık toplama bildirimlerini denetlemek için sürekli while döngüsünü içeren Kullanıcı yöntemini içerir.  
  
 [!code-cpp[GCNotification#8](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#8)]
 [!code-csharp[GCNotification#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#8)]
 [!code-vb[GCNotification#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#8)]  
  
 Aşağıdaki kod `OnFullGCApproachNotify` ,  
  
 `WaitForFullGCProc`yöntemidir.  
  
 [!code-cpp[GCNotification#5](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#5)]
 [!code-csharp[GCNotification#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#5)]
 [!code-vb[GCNotification#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#5)]  
  
 Aşağıdaki kod `OnFullGCApproachComplete` ,  
  
 `WaitForFullGCProc`yöntemidir.  
  
 [!code-cpp[GCNotification#6](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#6)]
 [!code-csharp[GCNotification#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#6)]
 [!code-vb[GCNotification#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#6)]  
  
 Aşağıdaki kod, ve yöntemlerinden çağrılan Kullanıcı yöntemlerini içerir `OnFullGCApproachNotify` `OnFullGCCompleteNotify` . Kullanıcı yöntemleri istekleri yeniden yönlendirir, mevcut istekleri bitirir ve sonra tam çöp toplama gerçekleştirildikten sonra istekleri sürdürür.  
  
 [!code-cpp[GCNotification#9](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#9)]
 [!code-csharp[GCNotification#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#9)]
 [!code-vb[GCNotification#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#9)]  
  
 Tüm kod örneği aşağıdaki gibidir:  
  
 [!code-cpp[GCNotification#1](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#1)]
 [!code-csharp[GCNotification#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#1)]
 [!code-vb[GCNotification#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çöp toplama](index.md)
