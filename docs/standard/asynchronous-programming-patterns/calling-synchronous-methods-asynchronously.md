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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 371e958aca87c922c902d8efd945d94d611672d9
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46519162"
---
# <a name="calling-synchronous-methods-asynchronously"></a>Zaman Uyumlu Metotları Zaman Uyumsuz Olarak Çağırma

.NET Framework zaman uyumsuz olarak herhangi bir yöntemi çağırmanızı sağlar. Bunu yapmak için aynı imzaya sahip bir temsilci yöntemi çağırmak istediğinizde olarak tanımlayın. Ortak dil çalışma zamanı otomatik olarak tanımlar `BeginInvoke` ve `EndInvoke` uygun imzalara sahip bu temsilci yöntemleri.

> [!NOTE]
> Zaman uyumsuz temsilcisini çağırır, özellikle `BeginInvoke` ve `EndInvoke` yöntemler .NET Compact Framework desteklenmez.

`BeginInvoke` Yöntemi zaman uyumsuz çağrı başlatır. Bu yöntemin zaman uyumsuz olarak yürütmek istediğiniz aynı parametreleri yanı sıra, iki ek isteğe bağlı parametreye sahiptir. İlk parametre bir <xref:System.AsyncCallback> zaman uyumsuz çağrısı tamamlandığında çağrılacak bir yönteme başvuran temsilci. İkinci parametre bilgileri geri çağırma yöntemi içinde oluşturulmuş bir kullanıcı tanımlı bir nesnedir. `BeginInvoke` hemen döner ve zaman uyumsuz çağrının tamamlanmasını beklemez. `BeginInvoke` döndürür bir <xref:System.IAsyncResult>, zaman uyumsuz çağrı ilerlemesini izlemek için kullanılabilir.

`EndInvoke` Yöntemi zaman uyumsuz çağrının sonucunu alır. Sonra her zaman çağrılabilir `BeginInvoke`. Zaman uyumsuz çağrı tamamlanmazsa `EndInvoke` işlem tamamlanana kadar çağıran iş parçacığını engeller. Parametreleri `EndInvoke` dahil `out` ve `ref` parametreleri (`<Out>` `ByRef` ve `ByRef` Visual Basic'te) zaman uyumsuz olarak yürütmek istediğiniz yöntemin artı <xref:System.IAsyncResult> tarafından döndürülen `BeginInvoke`.

> [!NOTE]
> Visual Studio IntelliSense özelliği parametrelerini görüntüler `BeginInvoke` ve `EndInvoke`. Visual Studio veya benzer bir araç kullanmıyorsanız veya C# ile Visual Studio kullanıyorsanız, bkz: [zaman uyumsuz programlama modeli (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) bu yöntemler için tanımlanan parametrelerin bir açıklaması.

Bu konudaki kod örnekleri kullanmak için dört yaygın yolları göstermek `BeginInvoke` ve `EndInvoke` zaman uyumsuz çağrıları yapma. Arama sonra `BeginInvoke` aşağıdakileri yapabilirsiniz:

-   Bazı iş yapmak ve sonra çağrı `EndInvoke` çağrı tamamlanana kadar bloğu için.

-   Elde bir <xref:System.Threading.WaitHandle> kullanarak <xref:System.IAsyncResult.AsyncWaitHandle%2A?displayProperty=nameWithType> özelliğini kullanın, <xref:System.Threading.WaitHandle.WaitOne%2A> kadar blok yürütme yöntemine <xref:System.Threading.WaitHandle> işareti verilen ve sonra çağrı `EndInvoke`.

-   Yoklama <xref:System.IAsyncResult> tarafından döndürülen `BeginInvoke` zaman uyumsuz çağrı tamamlanıp tamamlanmadığını belirlemek ve ardından çağırmak için `EndInvoke`.

-   Bir temsilci için bir geri çağırma yöntemine geçirmek `BeginInvoke`. Yöntem üzerinde yürütülen bir <xref:System.Threading.ThreadPool> zaman uyumsuz çağrı tamamlandığında iş parçacığı. Geri çağırma yöntemi çağrıları `EndInvoke`.

> [!IMPORTANT]
> Hangi yöntem ne olursa olsun kullanın, her zaman çağrı `EndInvoke` , zaman uyumsuz çağrı tamamlanması.

## <a name="defining-the-test-method-and-asynchronous-delegate"></a>Test yöntemi ve zaman uyumsuz temsilci tanımlama
 Aşağıdaki kod örnekleri aynı uzun süreli metot çağrısının çeşitli yolları göstermeye `TestMethod`, zaman uyumsuz olarak. `TestMethod` Yöntemi bu işlem, birkaç saniye için uyku başlattı ve sonra sona erer göstermek için bir konsol iletisi görüntüler. `TestMethod` sahip bir `out` imzalarını için tür parametreleri eklendi yol göstermek için parametre `BeginInvoke` ve `EndInvoke`. İşleyebilirsiniz `ref` parametreleri benzer.

 Aşağıdaki kod örneği tanımı gösterilmektedir `TestMethod` ve adlı temsilcinin `AsyncMethodCaller` çağırmak için kullanılabilecek `TestMethod` zaman uyumsuz olarak. Kod örnekleri derlemek için tanımları içerir `TestMethod` ve `AsyncMethodCaller` temsilci.

 [!code-cpp[AsyncDelegateExamples#1](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/TestMethod.cpp#1)]
 [!code-csharp[AsyncDelegateExamples#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/TestMethod.cs#1)]
 [!code-vb[AsyncDelegateExamples#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/TestMethod.vb#1)]

## <a name="waiting-for-an-asynchronous-call-with-endinvoke"></a>EndInvoke ile zaman uyumsuz bir çağrı bekleniyor
 Temsilcinin çağırarak yöntemi yürütmeye başlamak için bir yöntem zaman uyumsuz olarak yürütmek için en kolay yolu olan `BeginInvoke` yöntemi, bazı ana iş parçacığı üzerinde çalışır ve temsilcinin çağırma `EndInvoke` yöntemi. `EndInvoke` zaman uyumsuz çağrı tamamlanana kadar döndürmeyen çünkü çağıran iş parçacığını engelleyebilir. Bu dosya veya ağ işlemleriyle kullanmak iyi bir tekniktir.

> [!IMPORTANT]
> Çünkü `EndInvoke` engelleyebilir, hiçbir zaman bu hizmet kullanıcı arabirimi iş parçacığından çağırmalısınız.

 [!code-cpp[AsyncDelegateExamples#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/EndInvoke.cpp#2)]
 [!code-csharp[AsyncDelegateExamples#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/EndInvoke.cs#2)]
 [!code-vb[AsyncDelegateExamples#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/EndInvoke.vb#2)]

## <a name="waiting-for-an-asynchronous-call-with-waithandle"></a>WaitHandle ile zaman uyumsuz bir çağrı bekleniyor
 Alabilirsiniz bir <xref:System.Threading.WaitHandle> kullanarak <xref:System.IAsyncResult.AsyncWaitHandle%2A> özelliği <xref:System.IAsyncResult> tarafından döndürülen `BeginInvoke`. <xref:System.Threading.WaitHandle> Zaman uyumsuz çağrı tamamlanana ve bunun için çağırarak bekleyin sinyal <xref:System.Threading.WaitHandle.WaitOne%2A> yöntemi.

 Kullanıyorsanız bir <xref:System.Threading.WaitHandle>, önce veya zaman uyumsuz çağrı tamamlandıktan sonra ek işleme gerçekleştirebilirsiniz ancak çağırmadan önce `EndInvoke` sonuçlarını almak için.

> [!NOTE]
> Çağırdığınızda bekleme tanıtıcısı otomatik olarak kapatılmamış `EndInvoke`. Bekleme tanıtıcısı tüm başvurularını serbest bırakırsanız, çöp toplama bekleme tanıtıcısı kazandığında sistem kaynaklarının kurtulurlar. Bekleme tanıtıcısı kullanarak tamamladıktan hemen sonra sistem kaynaklarını serbest için bunu çağırarak dispose <xref:System.Threading.WaitHandle.Close%2A?displayProperty=nameWithType> yöntemi. Atılabilir bir nesne açıkça elden olduğunda çöp toplamanın daha verimli bir şekilde çalışır.

 [!code-cpp[AsyncDelegateExamples#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/waithandle.cpp#3)]
 [!code-csharp[AsyncDelegateExamples#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/waithandle.cs#3)]
 [!code-vb[AsyncDelegateExamples#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/WaitHandle.vb#3)]

## <a name="polling-for-asynchronous-call-completion"></a>Zaman uyumsuz çağrı tamamlanması için yoklama
 Kullanabileceğiniz <xref:System.IAsyncResult.IsCompleted%2A> özelliği <xref:System.IAsyncResult> tarafından döndürülen `BeginInvoke` zaman uyumsuz çağrı tamamlandığında bulunacak. Bir iş parçacığından zaman uyumsuz çağrı yapmak için kullanıcı arabirimi Hizmetleri, bunu yapabilirsiniz. Zaman uyumsuz çağrı üzerinde çalışırken yürütmeye devam çağıran iş parçacığını tamamlama sağlar yoklama bir <xref:System.Threading.ThreadPool> iş parçacığı.

 [!code-cpp[AsyncDelegateExamples#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/polling.cpp#4)]
 [!code-csharp[AsyncDelegateExamples#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/polling.cs#4)]
 [!code-vb[AsyncDelegateExamples#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/polling.vb#4)]

## <a name="executing-a-callback-method-when-an-asynchronous-call-completes"></a>Zaman uyumsuz bir çağrı tamamlandığında bir geri çağırma metodu yürütülüyor
 Zaman uyumsuz çağrı başlatır iş parçacığı sonuçlarını işleyen iş parçacığı olması gerekmez, bir geri çağırma yöntemi çağrısı tamamlandığında yürütebilir. Geri çağırma yöntemi, üzerinde yürütülen bir <xref:System.Threading.ThreadPool> iş parçacığı.

 Bir geri çağırma yöntemi kullanmak için geçmelidir `BeginInvoke` bir <xref:System.AsyncCallback> geri çağırma yöntemi temsil eden bir temsilci. Ayrıca geri çağırma yöntemi tarafından kullanılacak bilgileri içeren bir nesne geçirebilirsiniz. Geri çağırma yöntemi, verdiğiniz <xref:System.IAsyncResult>, için geri çağırma yöntemini tek parametre olduğu bir <xref:System.Runtime.Remoting.Messaging.AsyncResult> nesne. Ardından <xref:System.Runtime.Remoting.Messaging.AsyncResult.AsyncDelegate%2A?displayProperty=nameWithType> çağırabilirsiniz, aramayı başlatmak için kullanılan temsilci almak için özellik `EndInvoke`.

 Bu örnek ile ilgili notlar:

-   `threadId` Parametresinin `TestMethod` olduğu bir `out` parametre ([`<Out>` `ByRef` Visual Basic'te), giriş değeri tarafından hiç kullanılmamış `TestMethod`. İşlevsiz bir değişken geçirilir `BeginInvoke` çağırın. Varsa `threadId` parametresi olan bir `ref` parametre (`ByRef` Visual Basic'te), değişkeni bir sınıf seviyesi alanını böylece, her iki geçirilebilir olması gerekirdi `BeginInvoke` ve `EndInvoke`.

-   Geçirilen durum bilgilerini `BeginInvoke` çıkış iletisini biçimlendirmek için geri çağırma yöntemi kullanan bir biçim dizesi. Türü olarak geçtiğinden <xref:System.Object>, kullanılmadan önce durum bilgisi, doğru türe dönüştürmeniz gerekir.

-   Geri çağırma üzerinde yapılan bir <xref:System.Threading.ThreadPool> iş parçacığı. <xref:System.Threading.ThreadPool> Ana iş parçacığı sona ererse, ana iş parçacığı örneğin tamamlamak yeteri kadar geri çağırma için uyku moduna sahiptir çalışan uygulama tutma arka plan iş parçacığı akışlardır.

 [!code-cpp[AsyncDelegateExamples#5](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/callback.cpp#5)]
 [!code-csharp[AsyncDelegateExamples#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/callback.cs#5)]
 [!code-vb[AsyncDelegateExamples#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/callback.vb#5)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Delegate>
- [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
