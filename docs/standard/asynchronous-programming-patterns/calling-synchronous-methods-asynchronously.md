---
title: "Zaman Uyumlu Metotları Zaman Uyumsuz Olarak Çağırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- asynchronous programming, delegates
- asynchronous delegates
- AsyncWaitHandle property
- callback methods
- calling synchronous methods in asynchronous manner
- WaitHandle class, code examples
- asynchronous programming, status polling
- polling asynchronous operation status
- delegates [.NET Framework], asynchronous
- synchronous calling in asynchronous manner
- waiting for asynchronous calls
- status information [.NET Framework], asynchronous operations
ms.assetid: 41972034-92ed-450a-9664-ab93fcc6f1fb
caps.latest.revision: "24"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 965e5928c03ae573eacba98a7596f55b56aaba26
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="calling-synchronous-methods-asynchronously"></a>Zaman Uyumlu Metotları Zaman Uyumsuz Olarak Çağırma
.NET Framework, herhangi bir yöntemini zaman uyumsuz çağırma olanak sağlar. Bunu yapmak için aramak istediğiniz yöntemi olarak bir temsilci aynı imzayla tanımlayın; Ortak dil çalışma zamanı otomatik olarak tanımlayan `BeginInvoke` ve `EndInvoke` uygun imzaları ile bu temsilci için yöntemleri.  
  
> [!NOTE]
>  Zaman uyumsuz temsilcisini çağırır, özellikle `BeginInvoke` ve `EndInvoke` yöntemleri, .NET Compact Framework desteklenmiyor.  
  
 `BeginInvoke` Yöntemi zaman uyumsuz çağrı başlatır. Zaman uyumsuz olarak yürütülecek istediğiniz yöntemini aynı parametreleri yanı sıra, iki ek isteğe bağlı parametreye sahiptir. İlk parametre bir <xref:System.AsyncCallback> zaman uyumsuz çağrısı tamamlandığında çağrılacak bir yöntem başvuran temsilci. İkinci parametre bilgileri geri çağırma yöntemi geçirir bir kullanıcı tanımlı bir nesnedir. `BeginInvoke`hemen döndürür ve zaman uyumsuz çağrının tamamlanmasını beklemez. `BeginInvoke`döndüren bir <xref:System.IAsyncResult>, zaman uyumsuz çağrı ilerlemesini izlemek için kullanılabilir.  
  
 `EndInvoke` Yöntemi zaman uyumsuz çağrının sonucunu alır. Sonra her zaman çağrılabilir `BeginInvoke`. Zaman uyumsuz çağrı tamamlanmadıysa `EndInvoke` tamamlanana kadar çağıran iş parçacığı engeller. Parametreleri `EndInvoke` dahil `out` ve `ref` parametreleri (`<Out>` `ByRef` ve `ByRef` Visual Basic'te) zaman uyumsuz olarak yürütülecek istediğiniz yönteminin artı <xref:System.IAsyncResult> tarafından döndürülen `BeginInvoke`.  
  
> [!NOTE]
>  IntelliSense özelliğinde [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] parametrelerinin görüntüler `BeginInvoke` ve `EndInvoke`. Visual Studio ya da benzer bir aracı kullanmıyorsanız veya C# ile kullanıyorsanız [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], bkz: [zaman uyumsuz programlama modeli (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) bu yöntemleri için tanımlanan parametre açıklaması.  
  
 Bu konuda kod örnekleri kullanmak için dört yaygın yolları göstermek `BeginInvoke` ve `EndInvoke` zaman uyumsuz çağrıları yapma. Çağırdıktan sonra `BeginInvoke` aşağıdakileri yapabilirsiniz:  
  
-   Bazı iş ve ardından arama `EndInvoke` çağrı tamamlanana kadar bloğuna.  
  
-   Elde bir <xref:System.Threading.WaitHandle> kullanarak <xref:System.IAsyncResult.AsyncWaitHandle%2A?displayProperty=nameWithType> özelliği, kullanım, <xref:System.Threading.WaitHandle.WaitOne%2A> kadar blok yürütme yöntemine <xref:System.Threading.WaitHandle> işareti ve ardından arama `EndInvoke`.  
  
-   Yoklama <xref:System.IAsyncResult> tarafından döndürülen `BeginInvoke` zaman uyumsuz çağrı tamamlandığında belirleyin ve ardından çağırmak için `EndInvoke`.  
  
-   Bir geri çağırma yöntemi için bir temsilci geçirmek `BeginInvoke`. Yöntemi, üzerinde yürütülür bir <xref:System.Threading.ThreadPool> zaman uyumsuz çağrı tamamlandığında iş parçacığı. Geri çağırma yöntemi çağrıları `EndInvoke`.  
  
> [!IMPORTANT]
>  Hangi teknik olsun kullanın, her zaman çağrı `EndInvoke` zaman uyumsuz aramayı tamamlamak için.  
  
## <a name="defining-the-test-method-and-asynchronous-delegate"></a>Test yöntemi ve zaman uyumsuz temsilci tanımlama  
 İzleyin kod örnekleri aynı uzun süre çalışan yöntemi çağırma çeşitli yollarını gösteren `TestMethod`, zaman uyumsuz olarak. `TestMethod` Yöntemi işleme, birkaç saniye için uyku başladıktan ve ardından sona erer göstermek için bir konsol iletisi görüntüler. `TestMethod`sahip bir `out` gibi parametreleri imzalarını için eklenen yol göstermek için parametre `BeginInvoke` ve `EndInvoke`. İşleyebilir `ref` parametreleri benzer.  
  
 Aşağıdaki kod örneğinde tanımını gösterir `TestMethod` ve adlı temsilci `AsyncMethodCaller` çağırmak için kullanılabilecek `TestMethod` zaman uyumsuz olarak. Kod örnekleri derlemek için tanımları içeren `TestMethod` ve `AsyncMethodCaller` temsilci.  
  
 [!code-cpp[AsyncDelegateExamples#1](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/TestMethod.cpp#1)]
 [!code-csharp[AsyncDelegateExamples#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/TestMethod.cs#1)]
 [!code-vb[AsyncDelegateExamples#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/TestMethod.vb#1)]  
  
## <a name="waiting-for-an-asynchronous-call-with-endinvoke"></a>EndInvoke ile zaman uyumsuz bir çağrının bekleniyor  
 Temsilcinin çağırarak yöntemi çalıştırmaya başlamak için bir yöntem zaman uyumsuz olarak yürütülecek en basit yolu olan `BeginInvoke` yöntemi, bazı ana iş parçacığı üzerinde çalışır ve temsilcinin çağrı `EndInvoke` yöntemi. `EndInvoke`zaman uyumsuz çağrı tamamlanana kadar döndürmüyor çünkü çağıran iş parçacığı engelleyebilir. Bu dosya veya ağ işlemleriyle kullanmak için bir tekniktir.  
  
> [!IMPORTANT]
>  Çünkü `EndInvoke` engelliyor olabilir, bu kullanıcı arabirimi hizmet iş parçacığı tarafından hiçbir zaman çağırmanız gerekir.  
  
 [!code-cpp[AsyncDelegateExamples#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/EndInvoke.cpp#2)]
 [!code-csharp[AsyncDelegateExamples#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/EndInvoke.cs#2)]
 [!code-vb[AsyncDelegateExamples#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/EndInvoke.vb#2)]  
  
## <a name="waiting-for-an-asynchronous-call-with-waithandle"></a>WaitHandle ile zaman uyumsuz bir çağrının bekleniyor  
 Elde edebilirsiniz bir <xref:System.Threading.WaitHandle> kullanarak <xref:System.IAsyncResult.AsyncWaitHandle%2A> özelliği <xref:System.IAsyncResult> tarafından döndürülen `BeginInvoke`. <xref:System.Threading.WaitHandle> Zaman uyumsuz çağrı tamamlandığında ve bunun için çağırarak bekleyin işaret <xref:System.Threading.WaitHandle.WaitOne%2A> yöntemi.  
  
 Kullanırsanız, bir <xref:System.Threading.WaitHandle>, önce veya zaman uyumsuz çağrı tamamlandıktan sonra ek işleme gerçekleştirebilir ancak çağırmadan önce `EndInvoke` sonuçları alınamadı.  
  
> [!NOTE]
>  Çağırdığınızda bekleme tanıtıcısı otomatik olarak kapalı `EndInvoke`. Bekleme tanıtıcısı tüm başvurularını serbest, atık toplama bekleme tanıtıcısı geri kazanır, sistem kaynaklarını kurtulurlar. Bekleme tanıtıcısı kullanılarak tamamladıktan hemen sonra sistem kaynakları serbest bırakmak bunu çağırarak dispose <xref:System.Threading.WaitHandle.Close%2A?displayProperty=nameWithType> yöntemi. Tek kullanımlık nesneler açıkça atıldı çöp toplama daha verimli bir şekilde çalışır.  
  
 [!code-cpp[AsyncDelegateExamples#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/waithandle.cpp#3)]
 [!code-csharp[AsyncDelegateExamples#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/waithandle.cs#3)]
 [!code-vb[AsyncDelegateExamples#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/WaitHandle.vb#3)]  
  
## <a name="polling-for-asynchronous-call-completion"></a>Zaman uyumsuz çağrı tamamlanması için yoklama  
 Kullanabileceğiniz <xref:System.IAsyncResult.IsCompleted%2A> özelliği <xref:System.IAsyncResult> tarafından döndürülen `BeginInvoke` zaman uyumsuz çağrı tamamlandığında bulmak için. Akıştan zaman uyumsuz çağrı yaparak Hizmetleri kullanıcı arabirimi bunu yapabilirsiniz. Zaman uyumsuz çağrı üzerinde çalışırken çalıştırmaya devam etmeyi çağıran iş parçacığı tamamlama sağlar yoklama bir <xref:System.Threading.ThreadPool> iş parçacığı.  
  
 [!code-cpp[AsyncDelegateExamples#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/polling.cpp#4)]
 [!code-csharp[AsyncDelegateExamples#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/polling.cs#4)]
 [!code-vb[AsyncDelegateExamples#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/polling.vb#4)]  
  
## <a name="executing-a-callback-method-when-an-asynchronous-call-completes"></a>Zaman uyumsuz bir çağrı tamamlandığında çalıştırma bir geri çağırma yöntemi  
 Zaman uyumsuz çağrı başlatır iş parçacığı sonuçları işler iş parçacığı olması gerekmez, çağrısı tamamlandığında bir geri çağırma yöntemi yürütebilir. Geri çağırma yöntemi üzerinde yürütülür bir <xref:System.Threading.ThreadPool> iş parçacığı.  
  
 Bir geri çağırma yöntemini kullanmak için geçirdiğiniz gerekir `BeginInvoke` bir <xref:System.AsyncCallback> geri çağırma yöntemi temsil eden temsilci. Geri çağırma yöntemi tarafından kullanılacak bilgileri içeren bir nesne de geçirebilirsiniz. Geri çağırma yöntemi verdiğiniz <xref:System.IAsyncResult>, olduğu geri çağırma yönteminin yalnızca parametresi için bir <xref:System.Runtime.Remoting.Messaging.AsyncResult> nesnesi. Daha sonra <xref:System.Runtime.Remoting.Messaging.AsyncResult.AsyncDelegate%2A?displayProperty=nameWithType> çağırabilirsiniz böylece aramayı başlatmak için kullanılan temsilci almak için özellik `EndInvoke`.  
  
 Bu örnek ile ilgili notlar:  
  
-   `threadId` Parametresinin `TestMethod` olan bir `out` parametre ([`<Out>` `ByRef` Visual Basic'te), giriş değeri tarafından hiç kullanılmamış `TestMethod`. Sahte bir değişken geçirilir `BeginInvoke` çağırın. Varsa `threadId` parametresi olan bir `ref` parametre (`ByRef` Visual Basic'te), değişken, her iki gönderilebilir böylece sınıf düzeyi alan olması gerekir `BeginInvoke` ve `EndInvoke`.  
  
-   Geçirilir durum bilgisi `BeginInvoke` bir çıkış iletisini biçimlendirmek için geri çağırma yöntemi kullanır bir biçim dizesi. Türü olarak geçtiğinden <xref:System.Object>, kullanılabilmesi için durum bilgisi, uygun türe gerekir.  
  
-   Geri arama üzerinde yapılan bir <xref:System.Threading.ThreadPool> iş parçacığı. <xref:System.Threading.ThreadPool>iş parçacığı ana iş parçacığı sona ererse, ana iş parçacığı örneğin tamamlamak yeterince için geri çağırma uyku moduna nedenle çalışan uygulama tutma arka plan iş parçacıkları ' dir.  
  
 [!code-cpp[AsyncDelegateExamples#5](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/callback.cpp#5)]
 [!code-csharp[AsyncDelegateExamples#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/callback.cs#5)]
 [!code-vb[AsyncDelegateExamples#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/callback.vb#5)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Delegate>  
 [Olay tabanlı zaman uyumsuz desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
