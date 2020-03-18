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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73131541"
---
# <a name="garbage-collection-notifications"></a>Çöp Toplama Bildirimleri
Ortak dil çalışma süresine göre tam bir çöp toplamanın (yani bir nesil 2 koleksiyonunun) performansı olumsuz etkileyebileceği durumlar vardır. Bu, özellikle büyük büyük sayıda isteği işleyen sunucularla ilgili bir sorun olabilir; bu durumda, uzun bir çöp toplama isteği zaman ayarı neden olabilir. Kritik bir dönemde tam bir koleksiyonun oluşmasını önlemek için, tam bir çöp toplamanın yaklaştığını bildirebilir ve ardından iş yükünü başka bir sunucu örneğine yönlendirmek için harekete geçebilirsiniz. Geçerli sunucu örneğinin istekleri işlemesi gerekmediği sürece, bir koleksiyonu kendiniz de ikna edebilirsiniz.  
  
 Yöntem, <xref:System.GC.RegisterForFullGCNotification%2A> çalışma zamanı tam bir çöp toplamanın yaklaştığını algıladığında yükseltilecek bir bildirim için kaydeder. Bu bildirimin iki bölümü vardır: tam çöp toplama yaklaşırken ve tam çöp toplama tamamlandığında.  
  
> [!WARNING]
> Yalnızca çöp toplamaları engelleme bildirimleri yükseltmek. gcConcurrent>yapılandırma öğesi etkinleştirildiğinde, arka plan çöp koleksiyonları bildirimleri yükseltmez. [ \<](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)  
  
 Bildirimin ne zaman yükseltildiğini belirlemek <xref:System.GC.WaitForFullGCApproach%2A> <xref:System.GC.WaitForFullGCComplete%2A> için, bu bildirimi ve yöntemleri kullanın. Genellikle, bildirimin durumunu gösteren `while` bir <xref:System.GCNotificationStatus> numaralandırma elde etmek için bu yöntemleri bir döngü içinde kullanırsınız. Bu değer <xref:System.GCNotificationStatus.Succeeded>ise, aşağıdakileri yapabilirsiniz:  
  
- <xref:System.GC.WaitForFullGCApproach%2A> Yöntemle elde edilen bir bildirime yanıt olarak, iş yükünü yeniden yönlendirebilir ve büyük olasılıkla bir koleksiyonu kendiniz ikna edebilirsiniz.  
  
- <xref:System.GC.WaitForFullGCComplete%2A> Yöntemle elde edilen bir bildirime yanıt olarak, geçerli sunucu örneğini istekleri yeniden işlemek için kullanılabilir hale getirebilirsiniz. Ayrıca bilgi toplayabilirsiniz. Örneğin, koleksiyon sayısını <xref:System.GC.CollectionCount%2A> kaydetmek için yöntemi kullanabilirsiniz.  
  
 Ve <xref:System.GC.WaitForFullGCApproach%2A> <xref:System.GC.WaitForFullGCComplete%2A> yöntemler birlikte çalışacak şekilde tasarlanmıştır. Birini diğeri olmadan kullanmak belirsiz sonuçlar üretebilir.  
  
## <a name="full-garbage-collection"></a>Tam Çöp Toplama  
 Çalışma zamanı, aşağıdaki senaryolardan herhangi biri doğru olduğunda tam bir çöp toplama neden olur:  
  
- Yeterli bellek nesil 2 sonraki nesil 2 koleksiyonu neden yükseltildi.  
  
- Yeterli bellek sonraki nesil 2 toplama neden büyük nesne yığını na yükseltildi.  
  
- Nesil 1 koleksiyonu, diğer faktörler nedeniyle nesil 2 koleksiyonuna yükseltilir.  
  
 <xref:System.GC.RegisterForFullGCNotification%2A> Yöntemde belirttiğiniz eşikler ilk iki senaryoya uygulanır. Ancak, ilk senaryoda her zaman iki nedenden dolayı belirttiğiniz eşik değerleri ile orantılı zamanda bildirim almazsınız:  
  
- Çalışma süresi her küçük nesne ayırmayı denetlemez (performans nedenleriyle).  
  
- Yalnızca nesil 1 koleksiyonları belleği nesil 2'ye dönüştürür.  
  
 Üçüncü senaryo, bildirimi ne zaman alacağınız konusundaki belirsizliğe de katkıda bulunur. Bu bir garanti olmasa da, bu süre içinde istekleri yeniden yönlendirerek veya daha iyi barındırılabilir zaman toplama kendiniz indükleyerek bir uygunsuz tam çöp toplama etkilerini azaltmak için yararlı bir yol olduğunu kanıtlıyor.  
  
## <a name="notification-threshold-parameters"></a>Bildirim Eşik Parametreleri  
 Yöntem, <xref:System.GC.RegisterForFullGCNotification%2A> nesil 2 nesnelerin eşik değerlerini ve büyük nesne yığınını belirtmek için iki parametreye sahiptir. Bu değerler karşılandığında, bir çöp toplama bildirimi yükseltilmelidir. Aşağıdaki tabloda bu parametreler açıklanmaktadır.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`maxGenerationThreshold`|Bildirimin nesil 2'de tanıtılan nesnelere göre ne zaman yükseltilmesi gerektiğini belirten 1 ile 99 arasındaki bir sayı.|  
|`largeObjectHeapThreshold`|Bildirimin büyük nesne yığınına ayrılan nesnelere göre ne zaman yükseltilmesi gerektiğini belirten 1 ile 99 arasındaki bir sayı.|  
  
 Çok yüksek bir değer belirtirseniz, bildirim alma olasılığınız yüksektir, ancak çalışma süresinin koleksiyona neden olmasını beklemek çok uzun olabilir. Bir koleksiyona kendiniz neden olursanız, çalışma zamanı koleksiyona neden olursa geri alınacaktan daha fazla nesne geri alabilirsiniz.  
  
 Çok düşük bir değer belirtirseniz, bildirimalmak için yeterli zamana sahip olmadan önce çalışma süresi koleksiyona neden olabilir.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnekte, bir sunucu grubu gelen Web isteklerini karşılar. İşlem isteklerinin iş yükünü simüle etmek için, <xref:System.Collections.Generic.List%601> bir koleksiyona bayt dizileri eklenir. Her sunucu bir çöp toplama bildirimi için kaydeder `WaitForFullGCProc` ve sonra sürekli ve <xref:System.GCNotificationStatus> <xref:System.GC.WaitForFullGCApproach%2A> <xref:System.GC.WaitForFullGCComplete%2A> yöntemleri tarafından döndürülen numaralandırma izlemek için kullanıcı yöntemi üzerinde bir iş parçacığı başlar.  
  
 Ve <xref:System.GC.WaitForFullGCApproach%2A> <xref:System.GC.WaitForFullGCComplete%2A> yöntemler, bir bildirim yükseltildiğinde kendi olay işleme kullanıcı yöntemlerini çağırır:  
  
- `OnFullGCApproachNotify`  
  
     Bu yöntem, `RedirectRequests` istek sıraya sunucusunucuya istekleri göndermeyi askıya almak için talimat kullanıcı yöntemi çağırır. Bu, sınıf düzeyi değişkenini `bAllocate` daha `false` fazla nesne nin ayrılmaması için ayarlayarak simüle edilir.  
  
     Ardından, `FinishExistingRequests` bekleyen sunucu isteklerini işlemeyi bitirmek için kullanıcı yöntemi çağrılır. Bu, koleksiyonun temizlenmesiyle <xref:System.Collections.Generic.List%601> simüle edilir.  
  
     Son olarak, iş yükü hafif olduğundan bir çöp toplama neden oldu.  
  
- `OnFullGCCompleteNotify`  
  
     Bu yöntem, sunucu `AcceptRequests` artık tam bir çöp toplama duyarlı olmadığından istekleri kabul devam etmek için kullanıcı yöntemi çağırır. Bu eylem, nesnelerin `bAllocate` `true` <xref:System.Collections.Generic.List%601> koleksiyona eklenmeye devam edilebilmeleri için değişkeni ayarlayarak simüle edilir.  
  
 Aşağıdaki kod, `Main` örneğin yöntemini içerir.  
  
 [!code-cpp[GCNotification#2](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#2)]
 [!code-csharp[GCNotification#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#2)]
 [!code-vb[GCNotification#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#2)]  
  
 Aşağıdaki kod, `WaitForFullGCProc` çöp toplama bildirimlerini denetlemek için sürekli bir süre döngüsü içeren kullanıcı yöntemini içerir.  
  
 [!code-cpp[GCNotification#8](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#8)]
 [!code-csharp[GCNotification#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#8)]
 [!code-vb[GCNotification#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#8)]  
  
 Aşağıdaki kod, `OnFullGCApproachNotify`  
  
 `WaitForFullGCProc`Yöntem.  
  
 [!code-cpp[GCNotification#5](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#5)]
 [!code-csharp[GCNotification#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#5)]
 [!code-vb[GCNotification#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#5)]  
  
 Aşağıdaki kod, `OnFullGCApproachComplete`  
  
 `WaitForFullGCProc`Yöntem.  
  
 [!code-cpp[GCNotification#6](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#6)]
 [!code-csharp[GCNotification#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#6)]
 [!code-vb[GCNotification#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#6)]  
  
 Aşağıdaki kod, yöntem ve `OnFullGCApproachNotify` `OnFullGCCompleteNotify` yöntemden çağrılan kullanıcı yöntemlerini içerir. Kullanıcı yöntemleri istekleri yeniden yönlendirir, varolan istekleri ni tamamlar ve tam bir çöp toplama oluştuktan sonra istekleri devam ettirin.  
  
 [!code-cpp[GCNotification#9](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#9)]
 [!code-csharp[GCNotification#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#9)]
 [!code-vb[GCNotification#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#9)]  
  
 Kod örneğinin tamamı aşağıdaki gibidir:  
  
 [!code-cpp[GCNotification#1](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#1)]
 [!code-csharp[GCNotification#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#1)]
 [!code-vb[GCNotification#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çöp Toplama](../../../docs/standard/garbage-collection/index.md)
