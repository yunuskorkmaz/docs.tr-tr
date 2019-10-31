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
ms.openlocfilehash: d5646c4969c95350ab4cd63b16f6f99ffba3a4ec
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131541"
---
# <a name="garbage-collection-notifications"></a>Çöp Toplama Bildirimleri
Ortak dil çalışma zamanı ile tam çöp toplamanın (yani 2. nesil bir koleksiyon) performansı olumsuz etkileyebileceği durumlar vardır. Bu, özellikle büyük hacimli istekleri işleyen sunucularla ilgili bir sorun olabilir; Bu durumda, uzun bir atık toplama bir istek zaman aşımına neden olabilir. Kritik bir süre boyunca tam bir koleksiyonun oluşmasını önlemek için, tam bir çöp toplamanın yaklaştığı ve iş yükünü başka bir sunucu örneğine yeniden yönlendirmek için işlem gerçekleştirilecek şekilde bir uyarı alabilirsiniz. Ayrıca, geçerli sunucu örneğinin istekleri işlemesini gerektirmeyen bir koleksiyonu kendiniz de yazabilirsiniz.  
  
 <xref:System.GC.RegisterForFullGCNotification%2A> yöntemi, çalışma zamanı tam çöp toplama işlemini yaklaştığında bir bildirimin bir bildirimine kaydolur. Bu bildirimin iki bölümü vardır: tam çöp toplama yaklaşıyorsa ve tam çöp toplama tamamlandığında.  
  
> [!WARNING]
> Yalnızca atık koleksiyonları engelleme bildirimleri yükseltir. [\<gcConcurrent >](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) yapılandırma öğesi etkinleştirildiğinde, arka plan atık koleksiyonları bildirim oluşturmaz.  
  
 Bir bildirimin ne zaman ortaya çıkarılmadığını öğrenmek için <xref:System.GC.WaitForFullGCApproach%2A> ve <xref:System.GC.WaitForFullGCComplete%2A> yöntemlerini kullanın. Genellikle, bu yöntemleri bir `while` döngüsünde kullanarak sürekli olarak bildirimin durumunu gösteren bir <xref:System.GCNotificationStatus> numaralandırması elde edersiniz. Bu değer <xref:System.GCNotificationStatus.Succeeded>, şunları yapabilirsiniz:  
  
- <xref:System.GC.WaitForFullGCApproach%2A> yöntemiyle alınan bir bildirime yanıt olarak, iş yükünü yeniden yönlendirebilir ve muhtemelen bir koleksiyonu kendiniz de kullanabilirsiniz.  
  
- <xref:System.GC.WaitForFullGCComplete%2A> yöntemiyle alınan bir bildirime yanıt olarak, geçerli sunucu örneğini istekleri yeniden işlemek için kullanılabilir hale getirebilirsiniz. Ayrıca, bilgi toplayabilirsiniz. Örneğin, <xref:System.GC.CollectionCount%2A> yöntemini kullanarak koleksiyon sayısını kaydedebilirsiniz.  
  
 <xref:System.GC.WaitForFullGCApproach%2A> ve <xref:System.GC.WaitForFullGCComplete%2A> yöntemleri birlikte çalışmak üzere tasarlanmıştır. Diğeri olmadan kullanmak, belirsiz sonuçlar doğurabilir.  
  
## <a name="full-garbage-collection"></a>Tam çöp toplama  
 Aşağıdaki senaryolardan herhangi biri doğru olduğunda, çalışma zamanı tam çöp toplamaya neden olur:  
  
- Bir sonraki nesil 2 toplamaya neden olacak şekilde 2. nesil bir bellek yükseltildi.  
  
- Bir sonraki nesil 2 toplamaya neden olmak için büyük nesne yığınına yeterli bellek yükseltildi.  
  
- 1\. nesil bir koleksiyon, diğer faktörler nedeniyle 2. nesil bir toplamaya ilerletildi.  
  
 <xref:System.GC.RegisterForFullGCNotification%2A> yönteminde belirttiğiniz eşikler ilk iki senaryo için geçerlidir. Ancak, ilk senaryoda bildirimi her zaman, iki nedenden dolayı belirttiğiniz eşik değerleriyle orantılı şekilde almazsınız:  
  
- Çalışma zamanı her küçük nesne ayırmayı denetlemez (performans nedenleriyle).  
  
- Yalnızca 1. nesil koleksiyonlar belleği 2. nesil olarak yükseltir.  
  
 Ayrıca üçüncü senaryo, bildirimi alacağınız zaman açıklanmayacak şekilde katkıda bulunur. Bu bir garanti olmamasına karşın, bu süre boyunca istekleri yeniden yönlendirerek veya daha iyi bir hale gelebileceği zaman koleksiyonu kendiniz gerçekleştirerek, inopportune tam çöp toplamanın etkilerini azaltmak için faydalı bir yol olduğunu kanıtlamaz.  
  
## <a name="notification-threshold-parameters"></a>Bildirim eşiği parametreleri  
 <xref:System.GC.RegisterForFullGCNotification%2A> yöntemi 2. nesil nesnelerin eşik değerlerini ve büyük nesne yığınını belirtmek için iki parametreye sahiptir. Bu değerler karşılandığında bir çöp toplama bildirimi oluşturulmalıdır. Aşağıdaki tabloda bu parametreler açıklanmaktadır.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`maxGenerationThreshold`|2\. nesil üzerinde yükseltilen nesneler temelinde bildirimin ne zaman oluşturulması gerektiğini belirten, 1 ile 99 arasında bir sayı.|  
|`largeObjectHeapThreshold`|Büyük nesne yığınında ayrılan nesneler temelinde bildirimin ne zaman oluşturulması gerektiğini belirten, 1 ile 99 arasında bir sayı.|  
  
 Çok yüksek bir değer belirtirseniz, bir bildirim almanız, ancak çalışma zamanı bir koleksiyona neden olması için çok uzun bir süre olabilir. Bir koleksiyonu kendiniz kullandıysanız, çalışma zamanı koleksiyona neden olursa daha fazla nesne geri kazanırsınız.  
  
 Çok düşük bir değer belirtirseniz çalışma zamanı, bildirim almak için yeterli zamana girmeden önce koleksiyona neden olabilir.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnekte, bir sunucu grubu gelen Web istekleri hizmetidir. İstekleri işleme iş yükünün benzetimini yapmak için, bir <xref:System.Collections.Generic.List%601> koleksiyonuna bayt dizileri eklenir. Her sunucu bir çöp toplama bildirimine kaydolduktan sonra, <xref:System.GC.WaitForFullGCApproach%2A> ve <xref:System.GC.WaitForFullGCComplete%2A> yöntemleri tarafından döndürülen <xref:System.GCNotificationStatus> numaralandırmayı sürekli olarak izlemek için `WaitForFullGCProc` Kullanıcı yönteminde bir iş parçacığı başlatır.  
  
 <xref:System.GC.WaitForFullGCApproach%2A> ve <xref:System.GC.WaitForFullGCComplete%2A> yöntemleri, bir bildirim oluşturulduğunda ilgili olay işleme Kullanıcı yöntemlerini çağırır:  
  
- `OnFullGCApproachNotify`  
  
     Bu yöntem, istek sıraya alma sunucusuna istekleri sunucuya göndermeyi askıya almaya yönlendiren `RedirectRequests` Kullanıcı yöntemini çağırır. Bu, daha fazla nesne ayrılmaması için `bAllocate` sınıf düzeyi değişken `false` ayarlanarak benzetilir.  
  
     Ardından, `FinishExistingRequests` User yöntemi, bekleyen sunucu isteklerini işlemeyi tamamlayacak şekilde çağırılır. Bu, <xref:System.Collections.Generic.List%601> koleksiyonu temizlenerek benzetilir.  
  
     Son olarak, iş yükü hafif olduğundan bir çöp toplama işlemi yapılır.  
  
- `OnFullGCCompleteNotify`  
  
     Bu yöntem, sunucu artık tam bir atık toplamaya açık olmadığından istekleri kabul etmek için `AcceptRequests` Kullanıcı yöntemini çağırır. Bu eylem, nesnelerin <xref:System.Collections.Generic.List%601> koleksiyonuna eklenmeyi sürdürmesini sağlamak için `bAllocate` değişkeni `true` ayarlanarak benzetilir.  
  
 Aşağıdaki kod, örneğin `Main` yöntemini içerir.  
  
 [!code-cpp[GCNotification#2](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#2)]
 [!code-csharp[GCNotification#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#2)]
 [!code-vb[GCNotification#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#2)]  
  
 Aşağıdaki kod, atık toplama bildirimlerini denetlemek için sürekli while döngüsü içeren `WaitForFullGCProc` User yöntemini içerir.  
  
 [!code-cpp[GCNotification#8](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#8)]
 [!code-csharp[GCNotification#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#8)]
 [!code-vb[GCNotification#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#8)]  
  
 Aşağıdaki kod, ' dan çağrılan `OnFullGCApproachNotify` yöntemi içerir.  
  
 `WaitForFullGCProc` yöntemi.  
  
 [!code-cpp[GCNotification#5](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#5)]
 [!code-csharp[GCNotification#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#5)]
 [!code-vb[GCNotification#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#5)]  
  
 Aşağıdaki kod, ' dan çağrılan `OnFullGCApproachComplete` yöntemi içerir.  
  
 `WaitForFullGCProc` yöntemi.  
  
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
