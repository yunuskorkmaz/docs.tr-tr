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
ms.openlocfilehash: edf519621c2113843b89d96948243e9c095d2a57
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988867"
---
# <a name="garbage-collection-notifications"></a>Çöp Toplama Bildirimleri
Ortak dil çalışma zamanı ile tam çöp toplamanın (yani 2. nesil bir koleksiyon) performansı olumsuz etkileyebileceği durumlar vardır. Bu, özellikle büyük hacimli istekleri işleyen sunucularla ilgili bir sorun olabilir; Bu durumda, uzun bir atık toplama bir istek zaman aşımına neden olabilir. Kritik bir süre boyunca tam bir koleksiyonun oluşmasını önlemek için, tam bir çöp toplamanın yaklaştığı ve iş yükünü başka bir sunucu örneğine yeniden yönlendirmek için işlem gerçekleştirilecek şekilde bir uyarı alabilirsiniz. Ayrıca, geçerli sunucu örneğinin istekleri işlemesini gerektirmeyen bir koleksiyonu kendiniz de yazabilirsiniz.  
  
 <xref:System.GC.RegisterForFullGCNotification%2A> Yöntemi, çalışma zamanı tam çöp toplama işlemini yaklaştığında bir bildirimin bir bildirimine kaydolur. Bu bildirimin iki bölümü vardır: tam çöp toplama yaklaşıyorsa ve tam çöp toplama tamamlandığında.  
  
> [!WARNING]
> Yalnızca atık koleksiyonları engelleme bildirimleri yükseltir. GcConcurrent > yapılandırma öğesi etkinleştirildiğinde, arka plan atık koleksiyonları bildirim oluşturmaz. [ \<](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)  
  
 Bir bildirimin ne zaman kabarık olduğunu anlamak için <xref:System.GC.WaitForFullGCApproach%2A> ve <xref:System.GC.WaitForFullGCComplete%2A> yöntemlerini kullanın. Genellikle, bildirim durumunu gösteren bir `while` <xref:System.GCNotificationStatus> sabit listesi elde etmek için bu yöntemleri bir döngüde kullanırsınız. Bu değer ise <xref:System.GCNotificationStatus.Succeeded>, şunları yapabilirsiniz:  
  
- <xref:System.GC.WaitForFullGCApproach%2A> Yöntemiyle elde edilen bir bildirime yanıt olarak, iş yükünü yeniden yönlendirebilir ve muhtemelen bir koleksiyonu kendiniz bulabilirsiniz.  
  
- <xref:System.GC.WaitForFullGCComplete%2A> Yöntemiyle elde edilen bir bildirime yanıt olarak, geçerli sunucu örneğini istekleri yeniden işlemek için kullanılabilir hale getirebilirsiniz. Ayrıca, bilgi toplayabilirsiniz. Örneğin, koleksiyon sayısını kaydetmek için <xref:System.GC.CollectionCount%2A> yöntemini kullanabilirsiniz.  
  
 <xref:System.GC.WaitForFullGCApproach%2A> Veyöntemleri<xref:System.GC.WaitForFullGCComplete%2A> birlikte çalışmak üzere tasarlanmıştır. Diğeri olmadan kullanmak, belirsiz sonuçlar doğurabilir.  
  
## <a name="full-garbage-collection"></a>Tam çöp toplama  
 Aşağıdaki senaryolardan herhangi biri doğru olduğunda, çalışma zamanı tam çöp toplamaya neden olur:  
  
- Bir sonraki nesil 2 toplamaya neden olacak şekilde 2. nesil bir bellek yükseltildi.  
  
- Bir sonraki nesil 2 toplamaya neden olmak için büyük nesne yığınına yeterli bellek yükseltildi.  
  
- 1\. nesil bir koleksiyon, diğer faktörler nedeniyle 2. nesil bir toplamaya ilerletildi.  
  
 <xref:System.GC.RegisterForFullGCNotification%2A> Yönteminde belirttiğiniz eşikler ilk iki senaryo için geçerlidir. Ancak, ilk senaryoda bildirimi her zaman, iki nedenden dolayı belirttiğiniz eşik değerleriyle orantılı şekilde almazsınız:  
  
- Çalışma zamanı her küçük nesne ayırmayı denetlemez (performans nedenleriyle).  
  
- Yalnızca 1. nesil koleksiyonlar belleği 2. nesil olarak yükseltir.  
  
 Ayrıca üçüncü senaryo, bildirimi alacağınız zaman açıklanmayacak şekilde katkıda bulunur. Bu bir garanti olmamasına karşın, bu süre boyunca istekleri yeniden yönlendirerek veya daha iyi bir hale gelebileceği zaman koleksiyonu kendiniz gerçekleştirerek, inopportune tam çöp toplamanın etkilerini azaltmak için faydalı bir yol olduğunu kanıtlamaz.  
  
## <a name="notification-threshold-parameters"></a>Bildirim eşiği parametreleri  
 <xref:System.GC.RegisterForFullGCNotification%2A> Yöntemi 2. nesil nesnelerin eşik değerlerini ve büyük nesne yığınını belirtmek için iki parametreye sahiptir. Bu değerler karşılandığında bir çöp toplama bildirimi oluşturulmalıdır. Aşağıdaki tabloda bu parametreler açıklanmaktadır.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`maxGenerationThreshold`|2\. nesil üzerinde yükseltilen nesneler temelinde bildirimin ne zaman oluşturulması gerektiğini belirten, 1 ile 99 arasında bir sayı.|  
|`largeObjectHeapThreshold`|Büyük nesne yığınında ayrılan nesneler temelinde bildirimin ne zaman oluşturulması gerektiğini belirten, 1 ile 99 arasında bir sayı.|  
  
 Çok yüksek bir değer belirtirseniz, bir bildirim almanız, ancak çalışma zamanı bir koleksiyona neden olması için çok uzun bir süre olabilir. Bir koleksiyonu kendiniz kullandıysanız, çalışma zamanı koleksiyona neden olursa daha fazla nesne geri kazanırsınız.  
  
 Çok düşük bir değer belirtirseniz çalışma zamanı, bildirim almak için yeterli zamana girmeden önce koleksiyona neden olabilir.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnekte, bir sunucu grubu gelen Web istekleri hizmetidir. İstekleri işleme iş yükünün benzetimini yapmak için, bir <xref:System.Collections.Generic.List%601> koleksiyona bayt dizileri eklenir. Her sunucu bir `WaitForFullGCProc` çöp toplama bildirimine kaydolduktan sonra, <xref:System.GC.WaitForFullGCApproach%2A> ve <xref:System.GC.WaitForFullGCComplete%2A> yöntemleri tarafından döndürülen <xref:System.GCNotificationStatus> numaralandırmayı sürekli olarak izlemek için Kullanıcı yönteminde bir iş parçacığı başlatır.  
  
 Ve yöntemleri, <xref:System.GC.WaitForFullGCApproach%2A>birbildirim oluşturulduğundailgiliolayişlemeKullanıcıyöntemleriniçağırır:<xref:System.GC.WaitForFullGCComplete%2A>  
  
- `OnFullGCApproachNotify`  
  
     Bu yöntem, istek `RedirectRequests` Kuyruklama sunucusuna istekleri sunucuya göndermeyi askıya almaya yönlendiren Kullanıcı yöntemini çağırır. Bu, sınıf düzeyi değişkeni `bAllocate` , daha fazla nesne ayrılmaması için olarak `false` ayarlanarak benzetilir.  
  
     Ardından, `FinishExistingRequests` bekleyen sunucu isteklerini işlemeyi tamamlayacak Kullanıcı yöntemi çağırılır. Bu, <xref:System.Collections.Generic.List%601> koleksiyonu temizleyerek benzetilir.  
  
     Son olarak, iş yükü hafif olduğundan bir çöp toplama işlemi yapılır.  
  
- `OnFullGCCompleteNotify`  
  
     Bu yöntem, sunucu artık tam `AcceptRequests` bir atık toplama için savunmasız olmadığından istekleri kabul etmek için Kullanıcı yöntemini çağırır. Bu eylem, `bAllocate` nesnenin <xref:System.Collections.Generic.List%601> koleksiyona eklenmeyi sürdürmesini sağlamak `true` için değişkeni olarak ayarlanarak benzetilir.  
  
 Aşağıdaki kod, örneğin `Main` yöntemini içerir.  
  
 [!code-cpp[GCNotification#2](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#2)]
 [!code-csharp[GCNotification#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#2)]
 [!code-vb[GCNotification#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#2)]  
  
 Aşağıdaki kod, atık toplama `WaitForFullGCProc` bildirimlerini denetlemek için sürekli while döngüsünü içeren Kullanıcı yöntemini içerir.  
  
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
  
 Aşağıdaki kod, `OnFullGCApproachNotify` ve `OnFullGCCompleteNotify` yöntemlerinden çağrılan Kullanıcı yöntemlerini içerir. Kullanıcı yöntemleri istekleri yeniden yönlendirir, mevcut istekleri bitirir ve sonra tam çöp toplama gerçekleştirildikten sonra istekleri sürdürür.  
  
 [!code-cpp[GCNotification#9](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#9)]
 [!code-csharp[GCNotification#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#9)]
 [!code-vb[GCNotification#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#9)]  
  
 Tüm kod örneği aşağıdaki gibidir:  
  
 [!code-cpp[GCNotification#1](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#1)]
 [!code-csharp[GCNotification#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#1)]
 [!code-vb[GCNotification#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Atık Toplama](../../../docs/standard/garbage-collection/index.md)
