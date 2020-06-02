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
ms.openlocfilehash: 6a3dd83fe9d3fc48f66a0bb6bef333e4ff399108
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289908"
---
# <a name="calling-synchronous-methods-asynchronously"></a>Zaman Uyumlu Metotları Zaman Uyumsuz Olarak Çağırma

.NET Framework, zaman uyumsuz olarak herhangi bir yöntemi çağırmanızı sağlar. Bunu yapmak için, çağırmak istediğiniz yöntemle aynı imzaya sahip bir temsilci tanımlayın; ortak dil çalışma zamanı, `BeginInvoke` `EndInvoke` Bu temsilci için uygun imzalara göre otomatik olarak tanımlar ve yöntemleri.

> [!NOTE]
> Özellikle ve yöntemleri, zaman uyumsuz temsilci çağrıları `BeginInvoke` `EndInvoke` .NET Compact Framework desteklenmez.

`BeginInvoke`Yöntemi, zaman uyumsuz çağrıyı başlatır. Zaman uyumsuz olarak yürütmek istediğiniz yöntemle aynı parametrelere ve ek olarak iki isteğe bağlı parametreye sahiptir. İlk parametre, <xref:System.AsyncCallback> zaman uyumsuz arama tamamlandığında çağrılacak bir yönteme başvuran bir temsilcisidir. İkinci parametre, geri çağırma yöntemine bilgi geçiren Kullanıcı tanımlı bir nesnedir. `BeginInvoke`hemen döndürür ve zaman uyumsuz çağrının tamamlanmasını beklemez. `BeginInvoke`<xref:System.IAsyncResult>zaman uyumsuz çağrının ilerlemesini izlemek için kullanılabilecek bir döndürür.

`EndInvoke`Yöntemi, zaman uyumsuz çağrının sonuçlarını alır. Bu, sonrasında herhangi bir kez çağrılabilir `BeginInvoke` . Zaman uyumsuz çağrı tamamlanmazsa, `EndInvoke` çağıran iş parçacığını tamamlanana kadar engeller. Parametresi, `EndInvoke` `out` `ref` `<Out>` `ByRef` `ByRef` zaman uyumsuz olarak yürütmek istediğiniz yöntemin ve parametrelerini (ve Visual Basic) içerir ve <xref:System.IAsyncResult> tarafından döndürülen `BeginInvoke` .

> [!NOTE]
> Visual Studio 'da IntelliSense özelliği ve parametrelerini görüntüler `BeginInvoke` `EndInvoke` . Visual Studio veya benzer bir araç kullanmıyorsanız ya da Visual Studio Ile C# kullanıyorsanız, bu yöntemler için tanımlanan parametrelerin bir açıklaması için bkz. [zaman uyumsuz programlama modeli (APM)](asynchronous-programming-model-apm.md) .

Bu konudaki kod örnekleri, `BeginInvoke` `EndInvoke` zaman uyumsuz çağrılar yapmak ve kullanmanın dört ortak yolunu göstermektedir. Öğesini çağırdıktan sonra şunları yapabilirsiniz `BeginInvoke` :

- Biraz iş yapın ve ardından `EndInvoke` çağrı tamamlanana kadar bloğa çağrı yapın.

- <xref:System.Threading.WaitHandle>Özelliğini kullanarak alma <xref:System.IAsyncResult.AsyncWaitHandle%2A?displayProperty=nameWithType> , <xref:System.Threading.WaitHandle.WaitOne%2A> sinyale kadar yürütmeyi engellemek için yöntemini kullanın <xref:System.Threading.WaitHandle> ve ardından öğesini çağırın `EndInvoke` .

- <xref:System.IAsyncResult>Tarafından döndürülen `BeginInvoke` zaman uyumsuz çağrının ne zaman tamamlandığını belirleme ve sonra çağırma `EndInvoke` .

- Bir geri çağırma yöntemi için bir temsilci geçirin `BeginInvoke` . <xref:System.Threading.ThreadPool>Zaman uyumsuz arama tamamlandığında yöntemi bir iş parçacığında yürütülür. Geri çağırma yöntemi çağırır `EndInvoke` .

> [!IMPORTANT]
> Hangi tekniği kullanırsanız kullanın, zaman `EndInvoke` uyumsuz çağrlarınızın tamamlanmasını her zaman çağırın.

## <a name="defining-the-test-method-and-asynchronous-delegate"></a>Test yöntemini ve zaman uyumsuz temsilciyi tanımlama
 Aşağıdaki kod örnekleri, zaman uyumsuz olarak aynı uzun süre çalışan yöntemi çağırmanın çeşitli yollarını gösterir `TestMethod` . `TestMethod`Yöntemi, işleme başlamış olduğunu göstermek için bir konsol iletisi görüntüler ve birkaç saniye uyku moduna geçin ve sonra sona erer. `TestMethod`, `out` ve imzaları için bu tür parametrelerin Eklenme şeklini gösteren bir parametreye sahiptir `BeginInvoke` `EndInvoke` . `ref`Parametreleri benzer şekilde işleyebilirsiniz.

 Aşağıdaki kod örneği, `TestMethod` `AsyncMethodCaller` zaman uyumsuz olarak çağırmak için kullanılabilen adlı temsilcinin ve tanımını gösterir `TestMethod` . Kod örneklerini derlemek için, ve temsilcisinin tanımlarını dahil etmeniz gerekir `TestMethod` `AsyncMethodCaller` .

 [!code-cpp[AsyncDelegateExamples#1](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/TestMethod.cpp#1)]
 [!code-csharp[AsyncDelegateExamples#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/TestMethod.cs#1)]
 [!code-vb[AsyncDelegateExamples#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/TestMethod.vb#1)]

## <a name="waiting-for-an-asynchronous-call-with-endinvoke"></a>EndInvoke ile zaman uyumsuz bir çağrı bekleniyor
 Bir yöntemi zaman uyumsuz olarak yürütmenin en basit yolu, temsilcinin `BeginInvoke` metodunu çağırarak, ana iş parçacığında bazı işler yaparak ve sonra temsilcinin metodunu çağıran yöntemi çalıştırmaya başlamadır `EndInvoke` . `EndInvoke`, zaman uyumsuz çağrı tamamlanana kadar döndürülmediği için çağıran iş parçacığını engelleyebilir. Bu, dosya veya ağ işlemleriyle birlikte kullanmak için iyi bir tekniktir.

> [!IMPORTANT]
> `EndInvoke`Engelleyebileceğinden, bunu Kullanıcı arabirimine hizmet veren iş parçacıklarından asla Çağırmamanız gerekir.

 [!code-cpp[AsyncDelegateExamples#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/EndInvoke.cpp#2)]
 [!code-csharp[AsyncDelegateExamples#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/EndInvoke.cs#2)]
 [!code-vb[AsyncDelegateExamples#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/EndInvoke.vb#2)]

## <a name="waiting-for-an-asynchronous-call-with-waithandle"></a>WaitHandle ile zaman uyumsuz bir çağrı bekleniyor
 <xref:System.Threading.WaitHandle> <xref:System.IAsyncResult.AsyncWaitHandle%2A> Tarafından döndürülen özelliğini kullanarak elde edebilirsiniz <xref:System.IAsyncResult> `BeginInvoke` . , <xref:System.Threading.WaitHandle> Zaman uyumsuz çağrı tamamlandığında sinyal alırsınız ve yöntemini çağırarak bunu bekleyebilirsiniz <xref:System.Threading.WaitHandle.WaitOne%2A> .

 Kullanıyorsanız <xref:System.Threading.WaitHandle> , zaman uyumsuz çağrı tamamlanmadan önce veya sonra, ancak sonuçları almak için çağrılmadan önce ek işlem yapabilirsiniz `EndInvoke` .

> [!NOTE]
> Bekleme tanıtıcısı, ' i çağırdığınızda otomatik olarak kapanmaz `EndInvoke` . Bekleme tanıtıcısına yapılan tüm başvuruları serbest bırakırsanız, çöp toplama geri kazanır bekleme tutamacını, sistem kaynakları serbest bırakılır. Bekleme tutamacını kullanmayı tamamladıktan hemen sonra sistem kaynaklarını serbest bırakmak için yöntemini çağırarak onu atın <xref:System.Threading.WaitHandle.Close%2A?displayProperty=nameWithType> . Çöp toplama, atılabilir nesneleri açıkça atıldığı zaman daha verimli bir şekilde çalışabilir.

 [!code-cpp[AsyncDelegateExamples#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/waithandle.cpp#3)]
 [!code-csharp[AsyncDelegateExamples#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/waithandle.cs#3)]
 [!code-vb[AsyncDelegateExamples#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/WaitHandle.vb#3)]

## <a name="polling-for-asynchronous-call-completion"></a>Zaman uyumsuz çağrı tamamlama yoklaması
 <xref:System.IAsyncResult.IsCompleted%2A> <xref:System.IAsyncResult> `BeginInvoke` Zaman uyumsuz çağrının ne zaman tamamlandığını saptamak için tarafından döndürülen özelliğini kullanabilirsiniz. Bu işlem, Kullanıcı arabirimine hizmet veren bir iş parçacığından zaman uyumsuz çağrı yaparken yapabilirsiniz. Tamamlanma yoklaması, zaman uyumsuz çağrı bir iş parçacığında yürütüldüğünde, çağıran iş parçacığının yürütmeye devam etmesine izin verir <xref:System.Threading.ThreadPool> .

 [!code-cpp[AsyncDelegateExamples#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/polling.cpp#4)]
 [!code-csharp[AsyncDelegateExamples#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/polling.cs#4)]
 [!code-vb[AsyncDelegateExamples#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/polling.vb#4)]

## <a name="executing-a-callback-method-when-an-asynchronous-call-completes"></a>Zaman uyumsuz bir arama tamamlandığında bir geri çağırma yöntemi yürütülüyor
 Zaman uyumsuz çağrıyı başlatan iş parçacığının sonuçları işleyen iş parçacığı olması gerekmiyorsa, çağrı tamamlandığında bir geri çağırma yöntemi çalıştırabilirsiniz. Geri çağırma yöntemi bir <xref:System.Threading.ThreadPool> iş parçacığında yürütülür.

 Bir geri çağırma yöntemi kullanmak için, `BeginInvoke` <xref:System.AsyncCallback> geri çağırma yöntemini temsil eden bir temsilci geçirmeniz gerekir. Geri çağırma yöntemi tarafından kullanılacak bilgileri içeren bir nesnesi de geçirebilirsiniz. Geri çağırma yönteminde, <xref:System.IAsyncResult> geri çağırma yönteminin tek parametresi olan öğesini bir <xref:System.Runtime.Remoting.Messaging.AsyncResult> nesnesine dönüştürebilirsiniz. Daha sonra <xref:System.Runtime.Remoting.Messaging.AsyncResult.AsyncDelegate%2A?displayProperty=nameWithType> çağrabilmeniz için çağrıyı başlatmak üzere kullanılan temsilciyi almak için özelliğini kullanabilirsiniz `EndInvoke` .

 Örnekteki Not:

- `threadId`Parametresi parametresi `TestMethod` `out` ([ `<Out>` `ByRef` Visual Basic içinde), bu nedenle giriş değeri tarafından hiçbir şekilde kullanılmaz `TestMethod` . Bir kukla değişken `BeginInvoke` çağrıya geçirilir. `threadId`Parametre bir `ref` parametre ise ( `ByRef` Visual Basic), her ikisine de geçirilebilmesi için değişkenin bir sınıf düzeyi alan olması gerekir `BeginInvoke` `EndInvoke` .

- Öğesine geçirilen durum bilgileri `BeginInvoke` , geri çağırma yönteminin bir çıktı iletisini biçimlendirmek için kullandığı bir biçim dizesidir. Tür olarak geçirildiğinden <xref:System.Object> , kullanılmadan önce durum bilgilerinin uygun türe dönüştürülmesi gerekir.

- Geri çağırma bir <xref:System.Threading.ThreadPool> iş parçacığında yapılır. <xref:System.Threading.ThreadPool>iş parçacıkları, ana iş parçacığı sona erdiğinde uygulamayı çalışır durumda tutmayan arka plan iş parçacığıdır. bu nedenle, örneğin ana iş parçacığı geri aramanın tamamlanabilmesi için yeterince uzun süre uykuya geçecek.

 [!code-cpp[AsyncDelegateExamples#5](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/callback.cpp#5)]
 [!code-csharp[AsyncDelegateExamples#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/callback.cs#5)]
 [!code-vb[AsyncDelegateExamples#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/callback.vb#5)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Delegate>
- [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](event-based-asynchronous-pattern-eap.md)
