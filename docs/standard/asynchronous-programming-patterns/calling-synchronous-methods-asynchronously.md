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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73105123"
---
# <a name="calling-synchronous-methods-asynchronously"></a>Zaman Uyumlu Metotları Zaman Uyumsuz Olarak Çağırma

.NET Framework, zaman uyumsuz olarak herhangi bir yöntemi çağırmanızı sağlar. Bunu yapmak için, çağırmak istediğiniz yöntemle aynı imzaya sahip bir temsilci tanımlayın; ortak dil çalışma zamanı, bu temsilci için uygun imzalara sahip `BeginInvoke` ve `EndInvoke` yöntemlerini otomatik olarak tanımlar.

> [!NOTE]
> Zaman uyumsuz temsilci çağrıları, özellikle `BeginInvoke` ve `EndInvoke` yöntemleri .NET Compact Framework desteklenmez.

`BeginInvoke` yöntemi, zaman uyumsuz çağrıyı başlatır. Zaman uyumsuz olarak yürütmek istediğiniz yöntemle aynı parametrelere ve ek olarak iki isteğe bağlı parametreye sahiptir. İlk parametre, zaman uyumsuz arama tamamlandığında çağrılacak bir yönteme başvuran bir <xref:System.AsyncCallback> temsilcisidir. İkinci parametre, geri çağırma yöntemine bilgi geçiren Kullanıcı tanımlı bir nesnedir. `BeginInvoke` hemen döndürülür ve zaman uyumsuz çağrının tamamlanmasını beklemez. `BeginInvoke`, zaman uyumsuz çağrının ilerlemesini izlemek için kullanılabilen bir <xref:System.IAsyncResult>döndürür.

`EndInvoke` yöntemi, zaman uyumsuz çağrının sonuçlarını alır. `BeginInvoke`sonra herhangi bir zaman çağrılabilir. Zaman uyumsuz çağrı tamamlanmazsa `EndInvoke`, çağıran iş parçacığını tamamlanana kadar engeller. `EndInvoke` parametreler, zaman uyumsuz olarak yürütmek istediğiniz yöntemin yanı sıra `ByRef` tarafından döndürülen `ByRef` `out` ve `ref` parametreleri (Visual Basic '`<Out>` <xref:System.IAsyncResult> ve `BeginInvoke`) içerir.

> [!NOTE]
> Visual Studio 'da IntelliSense özelliği `BeginInvoke` ve `EndInvoke`parametrelerini görüntüler. Visual Studio veya benzer bir araç kullanmıyorsanız veya Visual Studio ile kullanıyorsanız C# , bu yöntemler için tanımlanan parametrelerin açıklaması Için [zaman uyumsuz programlama modeli (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) bölümüne bakın.

Bu konudaki kod örnekleri, zaman uyumsuz çağrılar yapmak için `BeginInvoke` ve `EndInvoke` kullanmanın dört ortak yolunu göstermektedir. `BeginInvoke` çağrıldıktan sonra şunları yapabilirsiniz:

- Biraz iş yapın ve ardından çağrı tamamlanana kadar engellemek için `EndInvoke` çağırın.

- <xref:System.IAsyncResult.AsyncWaitHandle%2A?displayProperty=nameWithType> özelliğini kullanarak bir <xref:System.Threading.WaitHandle> edinin, <xref:System.Threading.WaitHandle> sinyallene kadar yürütmeyi engellemek için <xref:System.Threading.WaitHandle.WaitOne%2A> metodunu kullanın ve ardından `EndInvoke`çağırın.

- Zaman uyumsuz çağrının ne zaman tamamlandığını belirleyip `BeginInvoke` tarafından döndürülen <xref:System.IAsyncResult> yoklayın ve sonra `EndInvoke`çağırır.

- `BeginInvoke`için bir geri çağırma yöntemi için temsilci geçirin. Yöntemi, zaman uyumsuz arama tamamlandığında bir <xref:System.Threading.ThreadPool> iş parçacığında yürütülür. Geri arama yöntemi `EndInvoke`çağırır.

> [!IMPORTANT]
> Hangi tekniği kullanırsanız kullanın, zaman uyumsuz çağrın her zaman `EndInvoke` çağırın.

## <a name="defining-the-test-method-and-asynchronous-delegate"></a>Test yöntemini ve zaman uyumsuz temsilciyi tanımlama
 Aşağıdaki kod örnekleri, aynı uzun süre çalışan yöntemi `TestMethod`, zaman uyumsuz olarak çağırmanın çeşitli yollarını gösterir. `TestMethod` yöntemi, işleme başladığını, birkaç saniye uyku moduna geçeceğini ve sonra sona erdiğini göstermek için bir konsol iletisi görüntüler. `TestMethod`, bu tür parametrelerin `BeginInvoke` ve `EndInvoke`imzalara Eklenme şeklini göstermek için bir `out` parametresine sahiptir. `ref` parametrelerini benzer şekilde işleyebilirsiniz.

 Aşağıdaki kod örneği `TestMethod` tanımını ve zaman uyumsuz `TestMethod` çağırmak için kullanılabilecek `AsyncMethodCaller` adlı temsilciyi gösterir. Kod örneklerini derlemek için `TestMethod` tanımlarını ve `AsyncMethodCaller` temsilciyi dahil etmeniz gerekir.

 [!code-cpp[AsyncDelegateExamples#1](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/TestMethod.cpp#1)]
 [!code-csharp[AsyncDelegateExamples#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/TestMethod.cs#1)]
 [!code-vb[AsyncDelegateExamples#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/TestMethod.vb#1)]

## <a name="waiting-for-an-asynchronous-call-with-endinvoke"></a>EndInvoke ile zaman uyumsuz bir çağrı bekleniyor
 Bir yöntemi zaman uyumsuz olarak yürütmenin en kolay yolu, temsilcinin `BeginInvoke` metodunu çağırarak, ana iş parçacığında bazı işler yaparak ve sonra temsilcinin `EndInvoke` yöntemini çağırarak yöntemi yürütmeye başlamadır. `EndInvoke`, zaman uyumsuz çağrı tamamlanana kadar döndürülmediği için çağıran iş parçacığını engelleyebilir. Bu, dosya veya ağ işlemleriyle birlikte kullanmak için iyi bir tekniktir.

> [!IMPORTANT]
> `EndInvoke` engelleyebileceğinden, bunu Kullanıcı arabirimine hizmet veren iş parçacıklarından asla Çağırmamanız gerekir.

 [!code-cpp[AsyncDelegateExamples#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/EndInvoke.cpp#2)]
 [!code-csharp[AsyncDelegateExamples#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/EndInvoke.cs#2)]
 [!code-vb[AsyncDelegateExamples#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/EndInvoke.vb#2)]

## <a name="waiting-for-an-asynchronous-call-with-waithandle"></a>WaitHandle ile zaman uyumsuz bir çağrı bekleniyor
 `BeginInvoke`tarafından döndürülen <xref:System.IAsyncResult> <xref:System.IAsyncResult.AsyncWaitHandle%2A> özelliğini kullanarak bir <xref:System.Threading.WaitHandle> elde edebilirsiniz. Zaman uyumsuz çağrı tamamlandığında <xref:System.Threading.WaitHandle> sinyallidir ve <xref:System.Threading.WaitHandle.WaitOne%2A> metodunu çağırarak bunu bekleyebilirsiniz.

 <xref:System.Threading.WaitHandle>kullanıyorsanız, zaman uyumsuz çağrı tamamlanmadan önce veya sonra, ancak sonuçları almak için `EndInvoke` çağrılmadan önce ek işlem yapabilirsiniz.

> [!NOTE]
> `EndInvoke`çağırdığınızda bekleme tutamacı otomatik olarak kapanmaz. Bekleme tanıtıcısına yapılan tüm başvuruları serbest bırakırsanız, çöp toplama geri kazanır bekleme tutamacını, sistem kaynakları serbest bırakılır. Bekleme tutamacını kullanmayı tamamladıktan hemen sonra sistem kaynaklarını serbest bırakmak için <xref:System.Threading.WaitHandle.Close%2A?displayProperty=nameWithType> yöntemini çağırarak onu atın. Çöp toplama, atılabilir nesneleri açıkça atıldığı zaman daha verimli bir şekilde çalışabilir.

 [!code-cpp[AsyncDelegateExamples#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/waithandle.cpp#3)]
 [!code-csharp[AsyncDelegateExamples#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/waithandle.cs#3)]
 [!code-vb[AsyncDelegateExamples#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/WaitHandle.vb#3)]

## <a name="polling-for-asynchronous-call-completion"></a>Zaman uyumsuz çağrı tamamlama yoklaması
 Zaman uyumsuz çağrının ne zaman tamamlandığını saptamak için `BeginInvoke` tarafından döndürülen <xref:System.IAsyncResult> <xref:System.IAsyncResult.IsCompleted%2A> özelliğini kullanabilirsiniz. Bu işlem, Kullanıcı arabirimine hizmet veren bir iş parçacığından zaman uyumsuz çağrı yaparken yapabilirsiniz. Tamamlanma yoklaması, zaman uyumsuz çağrı bir <xref:System.Threading.ThreadPool> iş parçacığında yürütüldüğünde, çağıran iş parçacığının yürütmeye devam etmesine izin verir.

 [!code-cpp[AsyncDelegateExamples#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/polling.cpp#4)]
 [!code-csharp[AsyncDelegateExamples#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/polling.cs#4)]
 [!code-vb[AsyncDelegateExamples#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/polling.vb#4)]

## <a name="executing-a-callback-method-when-an-asynchronous-call-completes"></a>Zaman uyumsuz bir arama tamamlandığında bir geri çağırma yöntemi yürütülüyor
 Zaman uyumsuz çağrıyı başlatan iş parçacığının sonuçları işleyen iş parçacığı olması gerekmiyorsa, çağrı tamamlandığında bir geri çağırma yöntemi çalıştırabilirsiniz. Geri çağırma yöntemi bir <xref:System.Threading.ThreadPool> iş parçacığında yürütülür.

 Bir geri çağırma yöntemi kullanmak için, geri çağırma yöntemini temsil eden bir <xref:System.AsyncCallback> temsilcisini `BeginInvoke` geçirmeniz gerekir. Geri çağırma yöntemi tarafından kullanılacak bilgileri içeren bir nesnesi de geçirebilirsiniz. Geri çağırma yönteminde, geri çağırma yönteminin tek parametresi olan <xref:System.IAsyncResult><xref:System.Runtime.Remoting.Messaging.AsyncResult> nesnesine dönüştürebilirsiniz. Daha sonra, `EndInvoke`çağırabilmeniz için çağrıyı başlatmak üzere kullanılan temsilciyi almak için <xref:System.Runtime.Remoting.Messaging.AsyncResult.AsyncDelegate%2A?displayProperty=nameWithType> özelliğini kullanabilirsiniz.

 Örnekteki Not:

- `TestMethod` `threadId` parametresi bir `out` parametresidir (`ByRef``<Out>` Visual Basic), bu nedenle giriş değeri hiçbir şekilde `TestMethod`tarafından kullanılmaz. `BeginInvoke` çağrısına bir kukla değişken geçirilir. `threadId` parametresi bir `ref` parametresi (`ByRef` Visual Basic) ise, bu değişkenin hem `BeginInvoke` hem de `EndInvoke`geçirilecek bir sınıf düzeyi alan olması gerekir.

- `BeginInvoke` geçirilen durum bilgileri, geri çağırma yönteminin bir çıktı iletisini biçimlendirmek için kullandığı bir biçim dizesidir. <xref:System.Object>türü olarak geçirildiğinden, kullanılmadan önce durum bilgilerinin uygun türe dönüştürülmesi gerekir.

- Geri çağırma <xref:System.Threading.ThreadPool> bir iş parçacığında yapılır. <xref:System.Threading.ThreadPool> iş parçacıkları, ana iş parçacığı sona erdiğinde uygulamayı çalışır durumda tutmayan arka plan iş parçacığıdır. bu nedenle, örneğin ana iş parçacığı geri aramanın tamamlanabilmesi için yeterince uzun süre uykuya geçecek.

 [!code-cpp[AsyncDelegateExamples#5](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/callback.cpp#5)]
 [!code-csharp[AsyncDelegateExamples#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/callback.cs#5)]
 [!code-vb[AsyncDelegateExamples#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/callback.vb#5)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Delegate>
- [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
