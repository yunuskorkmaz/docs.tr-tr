---
title: Zaman Uyumlu ve Zaman Uyumsuz İşlemler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], synchronous operations
- service contracts [WCF], asynchronous operations
ms.assetid: db8a51cb-67e6-411b-9035-e5821ed350c9
ms.openlocfilehash: 75a585efcdf316f407f3617fef8e1e279dcd922d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143219"
---
# <a name="synchronous-and-asynchronous-operations"></a><span data-ttu-id="f38c0-102">Zaman Uyumlu ve Zaman Uyumsuz İşlemler</span><span class="sxs-lookup"><span data-stu-id="f38c0-102">Synchronous and Asynchronous Operations</span></span>
<span data-ttu-id="f38c0-103">Bu konu, eşzamanlı hizmet işlemlerinin uygulanması ve çağrılma konulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f38c0-103">This topic discusses implementing and calling asynchronous service operations.</span></span>  
  
 <span data-ttu-id="f38c0-104">Yöntem çağrısı çalışırken uygulamanın yararlı işler yapmaya devam etmesini sağladığından, birçok uygulama yöntemleri eşzamanlı olarak çağırır.</span><span class="sxs-lookup"><span data-stu-id="f38c0-104">Many applications call methods asynchronously because it enables the application to continue doing useful work while the method call runs.</span></span> <span data-ttu-id="f38c0-105">Windows Communication Foundation (WCF) hizmetleri ve istemcileri, WCF uygulamalarına etkileşime karşı dengeli iş bikisini en üst düzeye çıkarmak için daha fazla esneklik sağlayan uygulamanın iki farklı düzeyindeki eşzamanlı operasyon çağrılarına katılabilirler .</span><span class="sxs-lookup"><span data-stu-id="f38c0-105">Windows Communication Foundation (WCF) services and clients can participate in asynchronous operation calls at two distinct levels of the application, which provide WCF applications even more flexibility to maximize throughput balanced against interactivity.</span></span>  
  
## <a name="types-of-asynchronous-operations"></a><span data-ttu-id="f38c0-106">Eşzamanlı İşlem Türleri</span><span class="sxs-lookup"><span data-stu-id="f38c0-106">Types of Asynchronous Operations</span></span>  
 <span data-ttu-id="f38c0-107">WCF'deki tüm hizmet sözleşmeleri, parametreler türleri ve iade değerleri ne olursa olsun, istemci ve hizmet arasında belirli bir ileti alışverişi deseni belirtmek için WCF özniteliklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f38c0-107">All service contracts in WCF, no matter the parameters types and return values, use WCF attributes to specify a particular message exchange pattern between client and service.</span></span> <span data-ttu-id="f38c0-108">WCF, gelen ve giden iletileri otomatik olarak uygun servis çalışmasına veya çalışan istemci koduna yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="f38c0-108">WCF automatically routes inbound and outbound messages to the appropriate service operation or running client code.</span></span>  
  
 <span data-ttu-id="f38c0-109">İstemci yalnızca belirli bir işlem için ileti alışverişi deseni belirten hizmet sözleşmesine sahip.</span><span class="sxs-lookup"><span data-stu-id="f38c0-109">The client possesses only the service contract, which specifies the message exchange pattern for a particular operation.</span></span> <span data-ttu-id="f38c0-110">İstemciler, temel ileti alışverişi deseni gözlendiği sürece geliştiriciye seçtikleri herhangi bir programlama modelini sunabilir.</span><span class="sxs-lookup"><span data-stu-id="f38c0-110">Clients can offer the developer any programming model they choose, so long as the underlying message exchange pattern is observed.</span></span> <span data-ttu-id="f38c0-111">Bu nedenle, belirtilen ileti deseni gözlendiği sürece hizmetler de işlemleri herhangi bir şekilde uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="f38c0-111">So, too, can services implement operations in any manner, so long as the specified message pattern is observed.</span></span>  
  
 <span data-ttu-id="f38c0-112">Hizmet sözleşmesinin hizmet veya istemci uygulamasından bağımsızlığı, WCF uygulamalarında aşağıdaki eşzamanlı yürütme biçimlerini sağlar:</span><span class="sxs-lookup"><span data-stu-id="f38c0-112">The independence of the service contract from either the service or client implementation enables the following forms of asynchronous execution in WCF applications:</span></span>  
  
- <span data-ttu-id="f38c0-113">İstemciler, eşzamanlı ileti alışverişi kullanarak istek/yanıt işlemlerini eş senkronize olarak çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="f38c0-113">Clients can invoke request/response operations asynchronously using a synchronous message exchange.</span></span>  
  
- <span data-ttu-id="f38c0-114">Hizmetler, eşzamanlı ileti alışverişi kullanarak bir istek/yanıt işlemini eşit olarak uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="f38c0-114">Services can implement a request/response operation asynchronously using a synchronous message exchange.</span></span>  
  
- <span data-ttu-id="f38c0-115">İleti alışverişi, istemci veya hizmetin uygulanmasından bağımsız olarak tek yönlü olabilir.</span><span class="sxs-lookup"><span data-stu-id="f38c0-115">Message exchanges can be one-way, regardless of the implementation of the client or service.</span></span>  
  
### <a name="suggested-asynchronous-scenarios"></a><span data-ttu-id="f38c0-116">Önerilen Eşzamanlı Senaryolar</span><span class="sxs-lookup"><span data-stu-id="f38c0-116">Suggested Asynchronous Scenarios</span></span>  
 <span data-ttu-id="f38c0-117">İşlem hizmeti uygulaması G/Ç çalışması yapmak gibi bir engelleme çağrısı yaparsa, hizmet işlemi uygulamasında eşzamanlı bir yaklaşım kullanın.</span><span class="sxs-lookup"><span data-stu-id="f38c0-117">Use an asynchronous approach in a service operation implementation if the operation service implementation makes a blocking call, such as doing I/O work.</span></span> <span data-ttu-id="f38c0-118">Eşzamanlı bir işlem uygulamasındaolduğunuzda, eşzamanlı çağrı yolunu mümkün olduğunca genişletmek için eşzamanlı işlemler ve yöntemler çağırmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="f38c0-118">When you are in an asynchronous operation implementation, try to call asynchronous operations and methods to extend the asynchronous call path as far as possible.</span></span> <span data-ttu-id="f38c0-119">Örneğin, içinden `BeginOperationTwo()` `BeginOperationOne()`bir çağrı .</span><span class="sxs-lookup"><span data-stu-id="f38c0-119">For example, call a `BeginOperationTwo()` from within `BeginOperationOne()`.</span></span>  
  
- <span data-ttu-id="f38c0-120">Aşağıdaki durumlarda istemcide asenkron bir yaklaşım veya arama uygulaması kullanın:</span><span class="sxs-lookup"><span data-stu-id="f38c0-120">Use an asynchronous approach in a client or calling application in the following cases:</span></span>  
  
- <span data-ttu-id="f38c0-121">Orta katmanbir uygulamadan işlem çağrıştırıyorsanız.</span><span class="sxs-lookup"><span data-stu-id="f38c0-121">If you are invoking operations from a middle-tier application.</span></span> <span data-ttu-id="f38c0-122">(Bu tür senaryolar hakkında daha fazla bilgi için [Orta Düzey İstemci Uygulamaları'na](./feature-details/middle-tier-client-applications.md)bakın.)</span><span class="sxs-lookup"><span data-stu-id="f38c0-122">(For more information about such scenarios, see [Middle-Tier Client Applications](./feature-details/middle-tier-client-applications.md).)</span></span>  
  
- <span data-ttu-id="f38c0-123">ASP.NET bir sayfa içinde işlem çağrıştırıyorsanız, eşzamanlı sayfalar kullanın.</span><span class="sxs-lookup"><span data-stu-id="f38c0-123">If you are invoking operations within an ASP.NET page, use asynchronous pages.</span></span>  
  
- <span data-ttu-id="f38c0-124">Windows Forms veya Windows Presentation Foundation (WPF) gibi tek iş parçacığı olan herhangi bir uygulamadan işlem istemiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="f38c0-124">If you are invoking operations from any application that is single threaded, such as Windows Forms or Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="f38c0-125">Olay tabanlı eşzamanlı arama modelini kullanırken, sonuç olayı Kullanıcı Arabirimi iş parçacığı üzerinde yükseltilir ve birden çok iş parçacığı kendiniz işlemenize gerek kalmadan uygulamaya yanıt ekler.</span><span class="sxs-lookup"><span data-stu-id="f38c0-125">When using the event-based asynchronous calling model, the result event is raised on the UI thread, adding responsiveness to the application without requiring you to handle multiple threads yourself.</span></span>  
  
- <span data-ttu-id="f38c0-126">Genel olarak, senkron ve eşzamanlı arama arasında bir seçeneğiniz varsa, eşzamanlı çağrıyı seçin.</span><span class="sxs-lookup"><span data-stu-id="f38c0-126">In general, if you have a choice between a synchronous and asynchronous call, choose the asynchronous call.</span></span>  
  
### <a name="implementing-an-asynchronous-service-operation"></a><span data-ttu-id="f38c0-127">Eşzamanlı Hizmet İşleminin Uygulanması</span><span class="sxs-lookup"><span data-stu-id="f38c0-127">Implementing an Asynchronous Service Operation</span></span>  
 <span data-ttu-id="f38c0-128">Asynchronous işlemleri aşağıdaki üç yöntemden biri kullanılarak uygulanabilir:</span><span class="sxs-lookup"><span data-stu-id="f38c0-128">Asynchronous operations can be implemented by using one of the three following methods:</span></span>  
  
1. <span data-ttu-id="f38c0-129">Görev tabanlı eşzamanlı desen</span><span class="sxs-lookup"><span data-stu-id="f38c0-129">The task-based asynchronous pattern</span></span>  
  
2. <span data-ttu-id="f38c0-130">Olay tabanlı eşzamanlı desen</span><span class="sxs-lookup"><span data-stu-id="f38c0-130">The event-based asynchronous pattern</span></span>  
  
3. <span data-ttu-id="f38c0-131">IAsyncResult asynchronous deseni</span><span class="sxs-lookup"><span data-stu-id="f38c0-131">The IAsyncResult asynchronous pattern</span></span>  
  
#### <a name="task-based-asynchronous-pattern"></a><span data-ttu-id="f38c0-132">Görev Tabanlı Eşzamanlı Desen</span><span class="sxs-lookup"><span data-stu-id="f38c0-132">Task-Based Asynchronous Pattern</span></span>  
 <span data-ttu-id="f38c0-133">Görev tabanlı eşzamanlı desen, en kolay ve en yalındır olduğundan, eşzamanlı işlemleri uygulamanın tercih edilen yoludur.</span><span class="sxs-lookup"><span data-stu-id="f38c0-133">The task-based asynchronous pattern is the preferred way to implement asynchronous operations because it is the easiest and most straight forward.</span></span> <span data-ttu-id="f38c0-134">Bu yöntemi kullanmak için yalnızca hizmet işleminizi uygulayın ve T'nin mantıksal işlemtarafından döndürülen tür olduğu Görev\<T>'nin iade türünü belirtin.</span><span class="sxs-lookup"><span data-stu-id="f38c0-134">To use this method simply implement your service operation and specify a return type of Task\<T>, where T is the type returned by the logical operation.</span></span> <span data-ttu-id="f38c0-135">Örnek:</span><span class="sxs-lookup"><span data-stu-id="f38c0-135">For example:</span></span>  
  
```csharp  
public class SampleService:ISampleService
{
   // ...  
   public async Task<string> SampleMethodTaskAsync(string msg)
   {
      return Task<string>.Factory.StartNew(() =>
      {
         return msg;
      });
   }  
   // ...  
}  
```  
  
 <span data-ttu-id="f38c0-136">Mantıksal işlem bir dize\<döndürür, çünkü SampleMethodTaskAsync işlemi görev dizesini> döndürür.</span><span class="sxs-lookup"><span data-stu-id="f38c0-136">The SampleMethodTaskAsync operation returns Task\<string> because the logical operation returns a string.</span></span> <span data-ttu-id="f38c0-137">Görev tabanlı eşenkron desen hakkında daha fazla bilgi için [Görev Tabanlı Asynchronous Deseni'ne](https://go.microsoft.com/fwlink/?LinkId=232504)bakın.</span><span class="sxs-lookup"><span data-stu-id="f38c0-137">For more information about the task-based asynchronous pattern, see [The Task-Based Asynchronous Pattern](https://go.microsoft.com/fwlink/?LinkId=232504).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="f38c0-138">Görev tabanlı eşsenkronize deseni kullanırken, işlemin tamamlanmasını beklerken bir özel durum oluşursa Bir T:System.AggregateException atılabilir.</span><span class="sxs-lookup"><span data-stu-id="f38c0-138">When using the task-based asynchronous pattern, a T:System.AggregateException may be thrown if an exception occurs while waiting on the completion of the operation.</span></span> <span data-ttu-id="f38c0-139">Bu özel durum istemci veya hizmetler de oluşabilir</span><span class="sxs-lookup"><span data-stu-id="f38c0-139">This exception may occur on the client or services</span></span>  
  
#### <a name="event-based-asynchronous-pattern"></a><span data-ttu-id="f38c0-140">Olay Tabanlı Asenkron Desen</span><span class="sxs-lookup"><span data-stu-id="f38c0-140">Event-Based Asynchronous Pattern</span></span>  
 <span data-ttu-id="f38c0-141">Olay tabanlı Asynchronous Modelini destekleyen bir hizmetin MethodNameAsync adında bir veya daha fazla işlemi olur.</span><span class="sxs-lookup"><span data-stu-id="f38c0-141">A service that supports the Event-based Asynchronous Pattern will have one or more operations named MethodNameAsync.</span></span> <span data-ttu-id="f38c0-142">Bu yöntemler, geçerli iş parçacığı üzerinde aynı işlemi gerçekleştiren senkron sürümleri yansıtabilir.</span><span class="sxs-lookup"><span data-stu-id="f38c0-142">These methods may mirror synchronous versions, which perform the same operation on the current thread.</span></span> <span data-ttu-id="f38c0-143">Sınıfın bir MethodNameCompleted olayı da olabilir ve bir MethodNameAsyncCancel (veya sadece CancelAsync) yöntemi olabilir.</span><span class="sxs-lookup"><span data-stu-id="f38c0-143">The class may also have a MethodNameCompleted event and it may have a MethodNameAsyncCancel (or simply CancelAsync) method.</span></span> <span data-ttu-id="f38c0-144">İşlemi çağırmak isteyen bir istemci, işlem tamamlandığında çağrılacak bir olay işleyicisi tanımlar,</span><span class="sxs-lookup"><span data-stu-id="f38c0-144">A client wishing to call the operation will define an event handler to be called when the operation completes,</span></span>  
  
 <span data-ttu-id="f38c0-145">Aşağıdaki kod snippet olay tabanlı eşzamanlı desen kullanarak eşzamanlı işlemleri nasıl bildirin gösteriş.</span><span class="sxs-lookup"><span data-stu-id="f38c0-145">The following code snippet illustrates how to declare asynchronous operations using the event-based asynchronous pattern.</span></span>  
  
```csharp  
public class AsyncExample  
{  
    // Synchronous methods.  
    public int Method1(string param);  
    public void Method2(double param);  
  
    // Asynchronous methods.  
    public void Method1Async(string param);  
    public void Method1Async(string param, object userState);  
    public event Method1CompletedEventHandler Method1Completed;  
  
    public void Method2Async(double param);  
    public void Method2Async(double param, object userState);  
    public event Method2CompletedEventHandler Method2Completed;  
  
    public void CancelAsync(object userState);  
  
    public bool IsBusy { get; }  
  
    // Class implementation not shown.  
}  
```  
  
 <span data-ttu-id="f38c0-146">Olay tabanlı Asynchronous Deseni hakkında daha fazla bilgi için [Olay Tabanlı Asynchronous Deseni'ne](../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="f38c0-146">For more information about the Event-based Asynchronous Pattern, see [The Event-Based Asynchronous Pattern](../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span></span>  
  
#### <a name="iasyncresult-asynchronous-pattern"></a><span data-ttu-id="f38c0-147">IAsyncResult Asynchronous Desen</span><span class="sxs-lookup"><span data-stu-id="f38c0-147">IAsyncResult Asynchronous Pattern</span></span>  
 <span data-ttu-id="f38c0-148">Bir hizmet işlemi .NET Framework asynchronous programlama deseni kullanılarak ve `<Begin>` yöntemi <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> `true`'' ye ayarlanan özellik ile işaretleme' kullanılarak eşzamanlı bir şekilde uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="f38c0-148">A service operation can be implemented in an asynchronous fashion using the .NET Framework asynchronous programming pattern and marking the `<Begin>` method with the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property set to `true`.</span></span> <span data-ttu-id="f38c0-149">Bu durumda, eşzamanlı işlem meta verilerde senkron işlemle aynı biçimde ortaya konur: İstek iletisi ve ilişkili yanıt iletisi ile tek bir işlem olarak ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="f38c0-149">In this case, the asynchronous operation is exposed in metadata in the same form as a synchronous operation: It is exposed as a single operation with a request message and a correlated response message.</span></span> <span data-ttu-id="f38c0-150">İstemci programlama modelleri daha sonra bir seçim var.</span><span class="sxs-lookup"><span data-stu-id="f38c0-150">Client programming models then have a choice.</span></span> <span data-ttu-id="f38c0-151">Bu deseni eşzamanlı bir işlem olarak veya eşzamanlı bir işlem olarak temsil edebilirler, ancak hizmet çağrıldığı sürece bir istek-yanıt iletisi değişimi gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="f38c0-151">They can represent this pattern as a synchronous operation or as an asynchronous one, so long as when the service is invoked a request-response message exchange takes place.</span></span>  
  
 <span data-ttu-id="f38c0-152">Genel olarak, sistemlerin eşzamanlı doğası ile, iş parçacıkları bir bağımlılık almamalıdır.</span><span class="sxs-lookup"><span data-stu-id="f38c0-152">In general, with the asynchronous nature of the systems, you should not take a dependency on the threads.</span></span>  <span data-ttu-id="f38c0-153">Veri işleminin çeşitli aşamalarına veri aktarmanın en güvenilir yolu uzantıları kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="f38c0-153">The most reliable way of passing data to various stages of operation dispatch processing is to use extensions.</span></span>  
  
 <span data-ttu-id="f38c0-154">Örneğin, [bkz.](how-to-implement-an-asynchronous-service-operation.md)</span><span class="sxs-lookup"><span data-stu-id="f38c0-154">For an example, see [How to: Implement an Asynchronous Service Operation](how-to-implement-an-asynchronous-service-operation.md).</span></span>  
  
 <span data-ttu-id="f38c0-155">İstemci uygulamasında `X` nasıl çağrıldığına bakılmaksızın eş senkronize olarak yürütülen bir sözleşme işlemini tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="f38c0-155">To define a contract operation `X` that is executed asynchronously regardless of how it is called in the client application:</span></span>  
  
- <span data-ttu-id="f38c0-156">Deseni `BeginOperation` kullanarak iki `EndOperation`yöntem tanımlayın ve .</span><span class="sxs-lookup"><span data-stu-id="f38c0-156">Define two methods using the pattern `BeginOperation` and `EndOperation`.</span></span>  
  
- <span data-ttu-id="f38c0-157">`BeginOperation` Yöntem, `in` işlem `ref` için parametreleri ve <xref:System.IAsyncResult> parametreleri içerir ve bir tür döndürür.</span><span class="sxs-lookup"><span data-stu-id="f38c0-157">The `BeginOperation` method includes `in` and `ref` parameters for the operation and returns an <xref:System.IAsyncResult> type.</span></span>  
  
- <span data-ttu-id="f38c0-158">Yöntem `EndOperation` bir <xref:System.IAsyncResult> parametre yanı sıra `out` `ref` ve parametreleri içerir ve işlemleri iade türü döndürür.</span><span class="sxs-lookup"><span data-stu-id="f38c0-158">The `EndOperation` method includes an <xref:System.IAsyncResult> parameter as well as the `out` and `ref` parameters and returns the operations return type.</span></span>  
  
 <span data-ttu-id="f38c0-159">Örneğin, aşağıdaki yönteme bakın.</span><span class="sxs-lookup"><span data-stu-id="f38c0-159">For example, see the following method.</span></span>  
  
```csharp  
int DoWork(string data, ref string inout, out string outonly)  
```  
  
```vb  
Function DoWork(ByVal data As String, ByRef inout As String, _out outonly As out) As Integer  
```  
  
 <span data-ttu-id="f38c0-160">Bir eşzamanlı işlem oluşturmak için iki yöntem olacaktır:</span><span class="sxs-lookup"><span data-stu-id="f38c0-160">To create an asynchronous operation, the two methods would be:</span></span>  
  
```csharp  
[OperationContract(AsyncPattern=true)]
IAsyncResult BeginDoWork(string data,
                         ref string inout,
                         AsyncCallback callback,
                         object state);
int EndDoWork(ref string inout, out string outonly, IAsyncResult result);  
```  
  
```vb  
<OperationContract(AsyncPattern := True)>
Function BeginDoWork(ByVal data As String, _
                     ByRef inout As String, _
                     ByVal callback As AsyncCallback, _
                     ByVal state As Object) As IAsyncResult
Function EndDoWork(ByRef inout As String, ByRef outonly As String, ByVal result As IAsyncResult) As Integer  
```  
  
> [!NOTE]
> <span data-ttu-id="f38c0-161">Öznitelik <xref:System.ServiceModel.OperationContractAttribute> yalnızca `BeginDoWork` yönteme uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f38c0-161">The <xref:System.ServiceModel.OperationContractAttribute> attribute is applied only to the `BeginDoWork` method.</span></span> <span data-ttu-id="f38c0-162">Ortaya çıkan sözleşmede . `DoWork`</span><span class="sxs-lookup"><span data-stu-id="f38c0-162">The resulting contract has one WSDL operation named `DoWork`.</span></span>  
  
### <a name="client-side-asynchronous-invocations"></a><span data-ttu-id="f38c0-163">İstemci Tarafı Asynchronous Çağrıları</span><span class="sxs-lookup"><span data-stu-id="f38c0-163">Client-Side Asynchronous Invocations</span></span>  
 <span data-ttu-id="f38c0-164">Bir WCF istemci uygulaması, daha önce açıklanan üç eşzamanlı arama modelinden herhangi birini kullanabilir</span><span class="sxs-lookup"><span data-stu-id="f38c0-164">A WCF client application can use any of three asynchronous calling models described previously</span></span>  
  
 <span data-ttu-id="f38c0-165">Görev tabanlı modeli kullanırken, aşağıdaki kod snippet'inde gösterildiği gibi bekleme anahtar sözcüklerini kullanarak işlemi aramanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="f38c0-165">When using the task-based model, simply call the operation using the await keyword as shown in the following code snippet.</span></span>  
  
```csharp  
await simpleServiceClient.SampleMethodTaskAsync("hello, world");  
```  
  
 <span data-ttu-id="f38c0-166">Olay tabanlı eşsenkronize deseni kullanmak yalnızca yanıtbildirimi almak için bir olay işleyicisi eklemeyi gerektirir ve ortaya çıkan olay kullanıcı arabirimi iş parçacığında otomatik olarak yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="f38c0-166">Using the event-based asynchronous pattern only requires adding an event handler to receive a notification of the response -- and the resulting event is raised on the user interface thread automatically.</span></span> <span data-ttu-id="f38c0-167">Bu yaklaşımı kullanmak için, aşağıdaki örnekte olduğu gibi [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)ile **/async** ve **/tcv:Version35** komut seçeneklerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="f38c0-167">To use this approach, specify both the **/async** and **/tcv:Version35** command options with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md), as in the following example.</span></span>  
  
```console  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async /tcv:Version35  
```  
  
 <span data-ttu-id="f38c0-168">Bu yapıldığında, Svcutil.exe, çağrı uygulamasının uygulanmasını ve yanıtı alması ve uygun eylemi gerçekleştirmesi için bir olay işleyicisini atamasını sağlayan olay altyapısına sahip bir WCF istemci sınıfı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f38c0-168">When this is done, Svcutil.exe generates a WCF client class with the event infrastructure that enables the calling application to implement and assign an event handler to receive the response and take the appropriate action.</span></span> <span data-ttu-id="f38c0-169">Tam bir örnek için [bkz: Hizmet İşlemleri'ni eşit bir şekilde arayın.](./feature-details/how-to-call-wcf-service-operations-asynchronously.md)</span><span class="sxs-lookup"><span data-stu-id="f38c0-169">For a complete example, see [How to: Call Service Operations Asynchronously](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span>  
  
 <span data-ttu-id="f38c0-170">Ancak olay tabanlı eşzamanlı model yalnızca .NET Framework 3.5'te kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f38c0-170">The event-based asynchronous model, however, is only available in .NET Framework 3.5.</span></span> <span data-ttu-id="f38c0-171">Buna ek olarak, bir WCF istemci kanalı kullanılarak oluşturulduğunda .NET Framework 3.5'te bile <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="f38c0-171">In addition, it is not supported even in .NET Framework 3.5 when a WCF client channel is created by using a <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f38c0-172">WCF istemci kanal nesneleri ile <xref:System.IAsyncResult?displayProperty=nameWithType> işlemlerinizi eş senkronize olarak çağırmak için nesneleri kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f38c0-172">With WCF client channel objects, you must use <xref:System.IAsyncResult?displayProperty=nameWithType> objects to invoke your operations asynchronously.</span></span> <span data-ttu-id="f38c0-173">Bu yaklaşımı kullanmak için, aşağıdaki örnekte olduğu gibi [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)ile **/async** komut seçeneğini belirtin.</span><span class="sxs-lookup"><span data-stu-id="f38c0-173">To use this approach, specify the **/async** command option with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md), as in the following example.</span></span>  
  
```console  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async
```  
  
 <span data-ttu-id="f38c0-174">Bu, her işlemin `<Begin>` ayarlanan <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> özellik `true` ve ilgili `<End>` yöntemle bir yöntem olarak modellendiği bir hizmet sözleşmesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f38c0-174">This generates a service contract in which each operation is modeled as a `<Begin>` method with the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property set to `true` and a corresponding `<End>` method.</span></span> <span data-ttu-id="f38c0-175">Tam bir <xref:System.ServiceModel.ChannelFactory%601>örnek için , [bkz.](./feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md)</span><span class="sxs-lookup"><span data-stu-id="f38c0-175">For a complete example using a <xref:System.ServiceModel.ChannelFactory%601>, see [How to: Call Operations Asynchronously Using a Channel Factory](./feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span></span>  
  
 <span data-ttu-id="f38c0-176">Her iki durumda da, uygulamalar, hizmet eşzamanlı olarak uygulansa bile, aynı şekilde bir uygulama nın eşzamanlı olarak yerel bir eşzamanlı yöntemi çağırmak için aynı deseni kullanabileceği şekilde, eşzamanlı olarak bir işlem başlatabilir.</span><span class="sxs-lookup"><span data-stu-id="f38c0-176">In either case, applications can invoke an operation asynchronously even if the service is implemented synchronously, in the same way that an application can use the same pattern to invoke asynchronously a local synchronous method.</span></span> <span data-ttu-id="f38c0-177">İşlemin nasıl uygulandığı istemci için önemli değildir; Yanıt iletisi geldiğinde, içeriği istemcinin asynchronous <`End`> yöntemine gönderilir ve istemci bilgileri alır.</span><span class="sxs-lookup"><span data-stu-id="f38c0-177">How the operation is implemented is not significant to the client; when the response message arrives, its content is dispatched to the client's asynchronous <`End`> method and the client retrieves the information.</span></span>  
  
### <a name="one-way-message-exchange-patterns"></a><span data-ttu-id="f38c0-178">Tek Yönlü İleti Değişim Desenleri</span><span class="sxs-lookup"><span data-stu-id="f38c0-178">One-Way Message Exchange Patterns</span></span>  
 <span data-ttu-id="f38c0-179">Ayrıca, tek yönlü işlemlerin <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> (ilişkili `true` yanıtın olmadığı işlemlerin) istemci veya hizmet tarafından diğer taraftan bağımsız olarak her iki yönde de gönderilebildiği bir eşzamanlı ileti değişimi deseni de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f38c0-179">You can also create an asynchronous message exchange pattern in which one-way operations (operations for which the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> is `true` have no correlated response) can be sent in either direction by the client or service independently of the other side.</span></span> <span data-ttu-id="f38c0-180">(Bu, tek yönlü iletilerle çift yönlü ileti alışverişi deseni kullanır.) Bu durumda, hizmet sözleşmesi, her iki tarafın da uygun olduğu şekilde eşzamanlı çağrılar veya uygulamalar olarak uygulayabileceği veya uygulayamayacağı tek yönlü bir ileti alışverişi belirtir.</span><span class="sxs-lookup"><span data-stu-id="f38c0-180">(This uses the duplex message exchange pattern with one-way messages.) In this case, the service contract specifies a one-way message exchange that either side can implement as asynchronous calls or implementations, or not, as appropriate.</span></span> <span data-ttu-id="f38c0-181">Genellikle, sözleşme tek yönlü iletialışverişi olduğunda, bir ileti gönderildikten sonra uygulama yanıt beklemez ve diğer işleri yapmaya devam edebilir, çünkü uygulamalar büyük ölçüde eşzamanlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="f38c0-181">Generally, when the contract is an exchange of one-way messages, the implementations can largely be asynchronous because once a message is sent the application does not wait for a reply and can continue doing other work.</span></span>  
  
### <a name="event-based-asynchronous-clients-and-message-contracts"></a><span data-ttu-id="f38c0-182">Olay Tabanlı Asynchronous İstemciler ve İleti Sözleşmeleri</span><span class="sxs-lookup"><span data-stu-id="f38c0-182">Event-based Asynchronous Clients and Message Contracts</span></span>  
 <span data-ttu-id="f38c0-183">Olay tabanlı eşsenkronize modelin tasarım yönergeleri, birden fazla değer döndürülürse, bir `Result` değerin özellik olarak döndürülür <xref:System.EventArgs> ve diğerlerinin nesneüzerinde özellik olarak döndürülür olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="f38c0-183">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="f38c0-184">Bunun bir sonucu, bir istemci olay tabanlı asynchronous komut seçeneklerini kullanarak meta veri aktarırken ve <xref:System.EventArgs> işlem birden fazla `Result` değer döndürürse, varsayılan nesne bir değer döndürür, özellik olarak varsayılan nesne döndürür ve geri kalan <xref:System.EventArgs> nesnenin özellikleridir.</span><span class="sxs-lookup"><span data-stu-id="f38c0-184">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.</span></span>  
  
 <span data-ttu-id="f38c0-185">İleti nesnesini `Result` özellik olarak almak ve döndürülen değerleri bu nesneüzerinde özellik olarak almak istiyorsanız, **/messageContract** komut u seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f38c0-185">If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the **/messageContract** command option.</span></span> <span data-ttu-id="f38c0-186">Bu, `Result` <xref:System.EventArgs> nesneüzerinde özellik olarak yanıt iletisi döndüren bir imza oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f38c0-186">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="f38c0-187">Tüm iç iade değerleri daha sonra yanıt iletisi nesnesinin özellikleridir.</span><span class="sxs-lookup"><span data-stu-id="f38c0-187">All internal return values are then properties of the response message object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f38c0-188">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f38c0-188">See also</span></span>

- <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A>
- <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A>
