---
title: Zaman Uyumlu Metotları Zaman Uyumsuz Olarak Çağırma
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
ms.openlocfilehash: 06df584f0120fbd4978e18647854a3ee844a2095
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73105123"
---
# <a name="calling-synchronous-methods-asynchronously"></a>Zaman Uyumlu Metotları Zaman Uyumsuz Olarak Çağırma

.NET Framework, herhangi bir yöntemi eşzamanlı olarak aramanızı sağlar. Bunu yapmak için aramak istediğiniz yöntemle aynı imzaya sahip bir temsilci tanımlarsınız; ortak dil çalışma süresi otomatik `BeginInvoke` `EndInvoke` olarak tanımlar ve uygun imzaları ile bu temsilci için yöntemler.

> [!NOTE]
> Eşzamanlı temsilci çağrıları, özellikle `BeginInvoke` .net `EndInvoke` Compact Framework'de desteklenmez.

Yöntem, `BeginInvoke` eşzamanlı çağrıyı başlatır. Eş senkronize olarak yürütmek istediğiniz yöntemle aynı parametrelere ve iki ek isteğe bağlı parametreye sahiptir. İlk parametre, <xref:System.AsyncCallback> eşyoknöz çağrı tamamlandığında çağrılacak bir yönteme başvuran bir temsilcidir. İkinci parametre, bilgileri geri arama yöntemine aktaran kullanıcı tanımlı bir nesnedir. `BeginInvoke`hemen döner ve eşzamanlı aramanın tamamlanmasını beklemez. `BeginInvoke`eşzamanlı <xref:System.IAsyncResult>aramanın ilerlemesini izlemek için kullanılabilecek bir , döndürür.

Yöntem, `EndInvoke` eşzamanlı aramanın sonuçlarını alır. Sonra her zaman `BeginInvoke`çağrılabilir. Eşkron arama tamamlanmadıysa, `EndInvoke` arama iş parçacığı tamamlanana kadar engeller. `EndInvoke` `out` Parametreleri ve `ref` parametreleri`<Out>` `ByRef` (ve `ByRef` Visual Basic) eşzamanlı olarak yürütmek istediğiniz yöntemin yanı <xref:System.IAsyncResult> sıra `BeginInvoke`döndürülen yöntemi içerir.

> [!NOTE]
> Visual Studio'daki `BeginInvoke` `EndInvoke`IntelliSense özelliği, Visual Studio veya benzer bir araç kullanmıyorsanız veya Visual Studio ile C# kullanıyorsanız, bu yöntemler için tanımlanan parametrelerin açıklaması için [Asynchronous Programming Model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) bölümüne bakın.

Bu konudaki kod örnekleri, eşkron `BeginInvoke` `EndInvoke` arama yapmak ve kullanmak için dört yaygın yol gösterir. Aradıktan `BeginInvoke` sonra aşağıdakileri yapabilirsiniz:

- Biraz iş yapın `EndInvoke` ve arama tamamlanana kadar engellemeyi arayın.

- <xref:System.IAsyncResult.AsyncWaitHandle%2A?displayProperty=nameWithType> Özelliği <xref:System.Threading.WaitHandle> kullanarak edinin, sinyal <xref:System.Threading.WaitHandle.WaitOne%2A> verilene kadar <xref:System.Threading.WaitHandle> yürütmeyi engellemek için `EndInvoke`yöntemini kullanın ve sonra arayın.

- Eşzamanlı <xref:System.IAsyncResult> aramanın `BeginInvoke` ne zaman tamamlandığını belirlemek için döndürülen `EndInvoke`tarafından anket ve ardından arayın.

- Geri arama yöntemi için bir `BeginInvoke`temsilciyi ' ye geçirin. Yöntem, eşkron <xref:System.Threading.ThreadPool> çağrı tamamlandığında bir iş parçacığı üzerinde yürütülür. Geri arama yöntemi `EndInvoke`çağırır.

> [!IMPORTANT]
> Hangi tekniği kullanırsanız kullanın, `EndInvoke` her zaman eşzamanlı aramanızı tamamlamak için arayın.

## <a name="defining-the-test-method-and-asynchronous-delegate"></a>Test Yöntemini ve Eşzamanlı Temsilciyi Tanımlama
 İzleyen kod örnekleri, `TestMethod`aynı uzun süren yöntemi eş zamanlı olarak adlandırmanın çeşitli yollarını gösterir. Yöntem, `TestMethod` işleme başladığını, birkaç saniye uyuduğuve sonra sona erdiğini göstermek için bir konsol iletisi görüntüler. `TestMethod`bu `out` parametrelerin imzalara nasıl eklenmediğini gösteren bir `BeginInvoke` `EndInvoke`parametreye sahiptir ve . Parametreleri `ref` benzer şekilde işleyebilirsiniz.

 Aşağıdaki kod örneği, eşsenkronize olarak `AsyncMethodCaller` aramak `TestMethod` için kullanılabilecek tanımını `TestMethod` ve adlandırılmış temsilciyi gösterir. Kod örneklerini derlemek için, `TestMethod` temsilcinin tanımlarını `AsyncMethodCaller` ve temsilciyi eklemeniz gerekir.

 [!code-cpp[AsyncDelegateExamples#1](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/TestMethod.cpp#1)]
 [!code-csharp[AsyncDelegateExamples#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/TestMethod.cs#1)]
 [!code-vb[AsyncDelegateExamples#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/TestMethod.vb#1)]

## <a name="waiting-for-an-asynchronous-call-with-endinvoke"></a>EndInvoke ile Eşzamanlı Arama Bekleniyor
 Bir yöntemi eş senkronize olarak yürütmenin en basit yolu, temsilcinin `BeginInvoke` yöntemini çağırarak yöntemi yürütmeye başlamak, ana iş `EndInvoke` parçacığı üzerinde bazı işler yapmak ve ardından temsilcinin yöntemini çağırmaktır. `EndInvoke`eşyokkron çağrı tamamlanana kadar geri dönmediği için arama iş parçacığı engelleyebilir. Bu, dosya veya ağ işlemleri ile kullanmak için iyi bir tekniktir.

> [!IMPORTANT]
> Engelleyebileceğinden, `EndInvoke` kullanıcı arabirimine hizmet veren iş parçacıklarından asla aramamalısınız.

 [!code-cpp[AsyncDelegateExamples#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/EndInvoke.cpp#2)]
 [!code-csharp[AsyncDelegateExamples#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/EndInvoke.cs#2)]
 [!code-vb[AsyncDelegateExamples#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/EndInvoke.vb#2)]

## <a name="waiting-for-an-asynchronous-call-with-waithandle"></a>WaitHandle ile Eşzamanlı Arama Bekleniyor
 Tarafından <xref:System.IAsyncResult> döndürülen <xref:System.Threading.WaitHandle> <xref:System.IAsyncResult.AsyncWaitHandle%2A> özelliğini kullanarak a `BeginInvoke`elde edebilirsiniz. Eşkron <xref:System.Threading.WaitHandle> arama tamamlandığında sinyal verilir ve <xref:System.Threading.WaitHandle.WaitOne%2A> yöntemi arayarak bunu bekleyebilirsiniz.

 Bir <xref:System.Threading.WaitHandle>, eşsenkronize arama tamamlanmadan önce veya sonra, ancak sonuçları almak `EndInvoke` için aramadan önce ek işleme gerçekleştirebilirsiniz.

> [!NOTE]
> Arama yaptığınızda bekleme tutamacı otomatik `EndInvoke`olarak kapatılmaz. Bekleme tanıtıcısına yapılan tüm başvuruları serbest ederseniz, çöp toplama bekleme tutamacını geri aldığında sistem kaynakları serbest bırakılır. Bekleme tutamacını kullanmayı bitirir bitirmez sistem kaynaklarını serbest hale getirmek <xref:System.Threading.WaitHandle.Close%2A?displayProperty=nameWithType> için, yöntemi arayarak sistemden kurtulun. Tek kullanımlık nesneler açıkça imha edildiğinde çöp toplama daha verimli çalışır.

 [!code-cpp[AsyncDelegateExamples#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/waithandle.cpp#3)]
 [!code-csharp[AsyncDelegateExamples#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/waithandle.cs#3)]
 [!code-vb[AsyncDelegateExamples#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/WaitHandle.vb#3)]

## <a name="polling-for-asynchronous-call-completion"></a>Eşzamanlı Çağrı Tamamlama Için Yoklama
 Eşzamanlı aramanın <xref:System.IAsyncResult.IsCompleted%2A> ne <xref:System.IAsyncResult> zaman `BeginInvoke` tamamlaşabileceğini keşfetmek için döndürülenin özelliğini kullanabilirsiniz. Bunu, kullanıcı arabirimine hizmet veren bir iş parçacığından asynchronous aramayaparken yapabilirsiniz. Tamamlanma için yoklama, eşkron çağrı bir <xref:System.Threading.ThreadPool> iş parçacığı üzerinde yürütülürken arama iş parçacığıyürütmeye devam etmesine olanak sağlar.

 [!code-cpp[AsyncDelegateExamples#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/polling.cpp#4)]
 [!code-csharp[AsyncDelegateExamples#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/polling.cs#4)]
 [!code-vb[AsyncDelegateExamples#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/polling.vb#4)]

## <a name="executing-a-callback-method-when-an-asynchronous-call-completes"></a>Bir Eşzamanlı Arama Tamamlandığında Geri Arama Yöntemini Yürütme
 Eşzamanlı aramayı başlatan iş parçacığının sonuçları işleyen iş parçacığı olması gerekmiyorsa, arama tamamlandığında bir geri arama yöntemi yürütebilirsiniz. Geri arama yöntemi bir <xref:System.Threading.ThreadPool> iş parçacığı üzerinde yürütülür.

 Geri arama yöntemini kullanmak için `BeginInvoke` <xref:System.AsyncCallback> geri arama yöntemini temsil eden bir temsilciyi geçmeniz gerekir. Geri arama yöntemi tarafından kullanılacak bilgileri içeren bir nesneyi de geçirebilirsiniz. Geri arama yönteminde, geri <xref:System.IAsyncResult>arama yönteminin tek parametresi olan , <xref:System.Runtime.Remoting.Messaging.AsyncResult> bir nesneye döküm yapabilirsiniz. Daha sonra aramayı <xref:System.Runtime.Remoting.Messaging.AsyncResult.AsyncDelegate%2A?displayProperty=nameWithType> başlatmak için kullanılan temsilciyi almak için özelliği kullanabilirsiniz, böylece arayabilirsiniz. `EndInvoke`

 Örnekteki notlar:

- `threadId` Parametresi `TestMethod` `out` bir parametredir`<Out>` `ByRef` (Visual Basic'te), bu nedenle giriş `TestMethod`değeri . `BeginInvoke` Sahte bir değişken çağrıya aktarılır. `threadId` `ref` Parametre bir parametre olsaydı`ByRef` (Visual Basic'te), değişkenin sınıf düzeyinde bir alan olması gerekir, böylece her ikisine `BeginInvoke` de ve `EndInvoke`.

- Aktarılan durum bilgileri, `BeginInvoke` geri arama yönteminin bir çıktı iletisini biçimlendirmek için kullandığı biçim dizesidir. Tür <xref:System.Object>olarak geçirildiği için, durum bilgilerinin kullanılmadan önce uygun türüne aktarılması gerekir.

- Geri arama bir <xref:System.Threading.ThreadPool> iş parçacığı üzerinde yapılır. <xref:System.Threading.ThreadPool>iş parçacıkları, ana iş parçacığı sona erdiğinde uygulamayı çalışır durumda tutmayan arka plan iş parçacıklarıdır, bu nedenle örneğin ana iş parçacığının geri aramanın bitmesi için yeterince uzun süre uyuması gerekmektedir.

 [!code-cpp[AsyncDelegateExamples#5](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/callback.cpp#5)]
 [!code-csharp[AsyncDelegateExamples#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/callback.cs#5)]
 [!code-vb[AsyncDelegateExamples#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/callback.vb#5)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Delegate>
- [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
