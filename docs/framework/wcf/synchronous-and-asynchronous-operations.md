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
ms.openlocfilehash: 6c464dc79e0f38b72f724fafcef59916d766e2d0
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="synchronous-and-asynchronous-operations"></a><span data-ttu-id="ed3ae-102">Zaman Uyumlu ve Zaman Uyumsuz İşlemler</span><span class="sxs-lookup"><span data-stu-id="ed3ae-102">Synchronous and Asynchronous Operations</span></span>
<span data-ttu-id="ed3ae-103">Bu konuda, uygulama ve zaman uyumsuz hizmet işlemlerini çağırma anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-103">This topic discusses implementing and calling asynchronous service operations.</span></span>  
  
 <span data-ttu-id="ed3ae-104">Yöntem çağrısının çalışırken yararlı iş yapmadan devam etmek uygulama sağladığından birçok uygulamaları yöntemleri zaman uyumsuz olarak çağırır.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-104">Many applications call methods asynchronously because it enables the application to continue doing useful work while the method call runs.</span></span> <span data-ttu-id="ed3ae-105">Windows Communication Foundation (WCF) hizmetlerini ve istemcilerin zaman uyumsuz işlem çağrıları düzeylerinde WCF uygulamaları karşı etkileşim dengeli verimliliği en üst düzeye çıkarmak için daha fazla esneklik sağlayan iki ayrı uygulama katılabilir .</span><span class="sxs-lookup"><span data-stu-id="ed3ae-105">Windows Communication Foundation (WCF) services and clients can participate in asynchronous operation calls at two distinct levels of the application, which provide WCF applications even more flexibility to maximize throughput balanced against interactivity.</span></span>  
  
## <a name="types-of-asynchronous-operations"></a><span data-ttu-id="ed3ae-106">Zaman uyumsuz işlemleri türleri</span><span class="sxs-lookup"><span data-stu-id="ed3ae-106">Types of Asynchronous Operations</span></span>  
 <span data-ttu-id="ed3ae-107">Tüm hizmet olsun parametre türü WCF içinde sözleşmeler ve dönüş değerleri, WCF öznitelikleri hizmeti ile istemci arasında belirli ileti değişim deseni belirtmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-107">All service contracts in WCF, no matter the parameters types and return values, use WCF attributes to specify a particular message exchange pattern between client and service.</span></span> <span data-ttu-id="ed3ae-108">WCF gelen ve giden iletileri uygun hizmet işlemi ya da çalışan istemci kodu otomatik olarak yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-108">WCF automatically routes inbound and outbound messages to the appropriate service operation or running client code.</span></span>  
  
 <span data-ttu-id="ed3ae-109">İstemci, yalnızca belirli bir işlem için ileti değişim deseni belirtir hizmet sözleşmesini sahip olur.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-109">The client possesses only the service contract, which specifies the message exchange pattern for a particular operation.</span></span> <span data-ttu-id="ed3ae-110">Temel alınan ileti değişim deseni gözlenir sürece istemciler Geliştirici tercih ettikleri, herhangi bir programlama modeli sunabilir.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-110">Clients can offer the developer any programming model they choose, so long as the underlying message exchange pattern is observed.</span></span> <span data-ttu-id="ed3ae-111">Belirtilen ileti deseni gözlenir sürece bu nedenle, çok, hizmetleri işlemleri herhangi bir biçimde uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-111">So, too, can services implement operations in any manner, so long as the specified message pattern is observed.</span></span>  
  
 <span data-ttu-id="ed3ae-112">Hizmet sözleşmesi bağımsızlığı hizmet veya istemci uygulamadan WCF uygulamaları zaman uyumsuz yürütme aşağıdaki biçimlerden sağlar:</span><span class="sxs-lookup"><span data-stu-id="ed3ae-112">The independence of the service contract from either the service or client implementation enables the following forms of asynchronous execution in WCF applications:</span></span>  
  
-   <span data-ttu-id="ed3ae-113">İstemcilerin zaman uyumsuz olarak zaman uyumlu ileti exchange kullanarak istek/yanıt işlemleri çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-113">Clients can invoke request/response operations asynchronously using a synchronous message exchange.</span></span>  
  
-   <span data-ttu-id="ed3ae-114">Hizmetleri zaman uyumsuz olarak zaman uyumlu ileti exchange ile bir istek/yanıt işlemi uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-114">Services can implement a request/response operation asynchronously using a synchronous message exchange.</span></span>  
  
-   <span data-ttu-id="ed3ae-115">İleti alışverişlerinde tek yönlü, bağımsız olarak istemci veya hizmet uygulaması olabilir.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-115">Message exchanges can be one-way, regardless of the implementation of the client or service.</span></span>  
  
### <a name="suggested-asynchronous-scenarios"></a><span data-ttu-id="ed3ae-116">Önerilen zaman uyumsuz senaryolar</span><span class="sxs-lookup"><span data-stu-id="ed3ae-116">Suggested Asynchronous Scenarios</span></span>  
 <span data-ttu-id="ed3ae-117">İşlemi hizmet uygulaması g/ç iş yapmadan gibi bir engelleme çağrı yaparsa bir hizmet işlemi uygulamasında zaman uyumsuz bir yaklaşım kullanın.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-117">Use an asynchronous approach in a service operation implementation if the operation service implementation makes a blocking call, such as doing I/O work.</span></span> <span data-ttu-id="ed3ae-118">Zaman uyumsuz işlemleri ve zaman uyumsuz çağrı yolu mümkün olduğunca genişletmek için yöntemleri çağırmak bir zaman uyumsuz işlem uygulamasında olduğunda deneyin.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-118">When you are in an asynchronous operation implementation, try to call asynchronous operations and methods to extend the asynchronous call path as far as possible.</span></span> <span data-ttu-id="ed3ae-119">Örneğin, bir `BeginOperationTwo()` içinden `BeginOperationOne()`.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-119">For example, call a `BeginOperationTwo()` from within `BeginOperationOne()`.</span></span>  
  
-   <span data-ttu-id="ed3ae-120">Bir istemci zaman uyumsuz bir yaklaşım veya çağrı yapan uygulamanın şu durumlarda kullanın:</span><span class="sxs-lookup"><span data-stu-id="ed3ae-120">Use an asynchronous approach in a client or calling application in the following cases:</span></span>  
  
-   <span data-ttu-id="ed3ae-121">Orta katman uygulama işlemlerinden çağırdığınız durumunda.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-121">If you are invoking operations from a middle-tier application.</span></span> <span data-ttu-id="ed3ae-122">(Bu tür senaryoları hakkında daha fazla bilgi için bkz: [orta katman istemci uygulamaları](../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md).)</span><span class="sxs-lookup"><span data-stu-id="ed3ae-122">(For more information about such scenarios, see [Middle-Tier Client Applications](../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md).)</span></span>  
  
-   <span data-ttu-id="ed3ae-123">Bir ASP.NET sayfasının işlemlerini çağırdığınız, zaman uyumsuz sayfalar kullanın.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-123">If you are invoking operations within an ASP.NET page, use asynchronous pages.</span></span>  
  
-   <span data-ttu-id="ed3ae-124">Tek iş parçacıklı, Windows Forms veya Windows Presentation Foundation (WPF) gibi herhangi bir uygulamadan işlemleri çağırdığınız durumunda.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-124">If you are invoking operations from any application that is single threaded, such as Windows Forms or Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="ed3ae-125">Olay tabanlı zaman uyumsuz çağırma modeli kullanılırken, birden çok iş parçacığı kendiniz işlemek gerek kalmadan uygulama yanıt hızını ekleme kullanıcı Arabirimi iş parçacığı üzerinde sonuç olay tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-125">When using the event-based asynchronous calling model, the result event is raised on the UI thread, adding responsiveness to the application without requiring you to handle multiple threads yourself.</span></span>  
  
-   <span data-ttu-id="ed3ae-126">Genel olarak, bir zaman uyumlu ve zaman uyumsuz çağrı arasında bir seçim varsa, zaman uyumsuz çağrı seçin.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-126">In general, if you have a choice between a synchronous and asynchronous call, choose the asynchronous call.</span></span>  
  
### <a name="implementing-an-asynchronous-service-operation"></a><span data-ttu-id="ed3ae-127">Zaman uyumsuz hizmet işlemi uygulama</span><span class="sxs-lookup"><span data-stu-id="ed3ae-127">Implementing an Asynchronous Service Operation</span></span>  
 <span data-ttu-id="ed3ae-128">Zaman uyumsuz işlemleri üç aşağıdaki yöntemlerden birini kullanarak uygulanabilir:</span><span class="sxs-lookup"><span data-stu-id="ed3ae-128">Asynchronous operations can be implemented by using one of the three following methods:</span></span>  
  
1.  <span data-ttu-id="ed3ae-129">Görev tabanlı zaman uyumsuz desen</span><span class="sxs-lookup"><span data-stu-id="ed3ae-129">The task-based asynchronous pattern</span></span>  
  
2.  <span data-ttu-id="ed3ae-130">Olay tabanlı zaman uyumsuz desen</span><span class="sxs-lookup"><span data-stu-id="ed3ae-130">The event-based asynchronous pattern</span></span>  
  
3.  <span data-ttu-id="ed3ae-131">IAsyncResult zaman uyumsuz desen</span><span class="sxs-lookup"><span data-stu-id="ed3ae-131">The IAsyncResult asynchronous pattern</span></span>  
  
#### <a name="task-based-asynchronous-pattern"></a><span data-ttu-id="ed3ae-132">Görev tabanlı zaman uyumsuz desen</span><span class="sxs-lookup"><span data-stu-id="ed3ae-132">Task-Based Asynchronous Pattern</span></span>  
 <span data-ttu-id="ed3ae-133">Görev tabanlı zaman uyumsuz desen kolay ve çoğu düz İleri olduğundan zaman uyumsuz işlemleri uygulamak için önerilen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-133">The task-based asynchronous pattern is the preferred way to implement asynchronous operations because it is the easiest and most straight forward.</span></span> <span data-ttu-id="ed3ae-134">Bu yöntemi kullanmak için sadece bir hizmet işlemi uygulama ve görev dönüş türünü belirtmeniz\<T >, burada T mantıksal işlem tarafından döndürülen tür.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-134">To use this method simply implement your service operation and specify a return type of Task\<T>, where T is the type returned by the logical operation.</span></span> <span data-ttu-id="ed3ae-135">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="ed3ae-135">For example:</span></span>  
  
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
  
 <span data-ttu-id="ed3ae-136">Görev SampleMethodTaskAsync işlemi döndürür\<dize > çünkü mantıksal işlemi bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-136">The SampleMethodTaskAsync operation returns Task\<string> because the logical operation returns a string.</span></span> <span data-ttu-id="ed3ae-137">Görev tabanlı zaman uyumsuz desen hakkında daha fazla bilgi için bkz: [The Task-Based zaman uyumsuz desen](http://go.microsoft.com/fwlink/?LinkId=232504).</span><span class="sxs-lookup"><span data-stu-id="ed3ae-137">For more information about the task-based asynchronous pattern, see [The Task-Based Asynchronous Pattern](http://go.microsoft.com/fwlink/?LinkId=232504).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="ed3ae-138">Bir özel durum işleminin tamamlanması beklenirken hata oluşursa görev tabanlı zaman uyumsuz desen kullanırken, bir T:System.AggregateException durum.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-138">When using the task-based asynchronous pattern, a T:System.AggregateException may be thrown if an exception occurs while waiting on the completion of the operation.</span></span> <span data-ttu-id="ed3ae-139">Bu durum istemci ve hizmetler oluşabilir</span><span class="sxs-lookup"><span data-stu-id="ed3ae-139">This exception may occur on the client or services</span></span>  
  
#### <a name="event-based-asynchronous-pattern"></a><span data-ttu-id="ed3ae-140">Olay tabanlı zaman uyumsuz desen</span><span class="sxs-lookup"><span data-stu-id="ed3ae-140">Event-Based Asynchronous Pattern</span></span>  
 <span data-ttu-id="ed3ae-141">Olay tabanlı zaman uyumsuz deseni destekleyen bir hizmet MethodNameAsync adlı bir veya daha fazla işlem sahip olur.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-141">A service that supports the Event-based Asynchronous Pattern will have one or more operations named MethodNameAsync.</span></span> <span data-ttu-id="ed3ae-142">Bu yöntemler, geçerli iş parçacığı üzerinde aynı işlemi zaman uyumlu sürümleri yansıtma.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-142">These methods may mirror synchronous versions, which perform the same operation on the current thread.</span></span> <span data-ttu-id="ed3ae-143">Sınıf MethodNameCompleted olay da sahip olabilirsiniz ve MethodNameAsyncCancel (veya yalnızca CancelAsync) olabilir yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-143">The class may also have a MethodNameCompleted event and it may have a MethodNameAsyncCancel (or simply CancelAsync) method.</span></span> <span data-ttu-id="ed3ae-144">Çağrı işlemi isteyen bir istemci işlem tamamlandığında çağrılacak olay işleyicisi tanımlayacaksınız,</span><span class="sxs-lookup"><span data-stu-id="ed3ae-144">A client wishing to call the operation will define an event handler to be called when the operation completes,</span></span>  
  
 <span data-ttu-id="ed3ae-145">Aşağıdaki kod parçacığını olay tabanlı zaman uyumsuz desen kullanarak zaman uyumsuz işlemleri bildirmeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-145">The following code snippet illustrates how to declare asynchronous operations using the event-based asynchronous pattern.</span></span>  
  
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
  
 <span data-ttu-id="ed3ae-146">Olay tabanlı zaman uyumsuz desen hakkında daha fazla bilgi için bkz: [The Event-Based zaman uyumsuz desen](http://go.microsoft.com/fwlink/?LinkId=232515).</span><span class="sxs-lookup"><span data-stu-id="ed3ae-146">For more information about the Event-based Asynchronous Pattern, see [The Event-Based Asynchronous Pattern](http://go.microsoft.com/fwlink/?LinkId=232515).</span></span>  
  
#### <a name="iasyncresult-asynchronous-pattern"></a><span data-ttu-id="ed3ae-147">IAsyncResult zaman uyumsuz desen</span><span class="sxs-lookup"><span data-stu-id="ed3ae-147">IAsyncResult Asynchronous Pattern</span></span>  
 <span data-ttu-id="ed3ae-148">Bir hizmet işlemi kullanarak bir zaman uyumsuz biçimde uygulanabilir [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] zaman uyumsuz desen programlama ve İşaretleme `<Begin>` yöntemiyle <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-148">A service operation can be implemented in an asynchronous fashion using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] asynchronous programming pattern and marking the `<Begin>` method with the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property set to `true`.</span></span> <span data-ttu-id="ed3ae-149">Bu durumda, zaman uyumsuz işlem eşzamanlı bir işlem olarak aynı formda meta verilerde sunulur: bir istek iletisi ve ilişkili yanıt iletisi ile tek bir işlem olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-149">In this case, the asynchronous operation is exposed in metadata in the same form as a synchronous operation: It is exposed as a single operation with a request message and a correlated response message.</span></span> <span data-ttu-id="ed3ae-150">İstemci programlama modelleri sonra bir seçeneğiniz vardır.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-150">Client programming models then have a choice.</span></span> <span data-ttu-id="ed3ae-151">Hizmet çağrıldığında bir istek-yanıt iletisi exchange gerçekleşir sürece, bu deseni eşzamanlı bir işlem veya zaman uyumsuz bir olarak gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-151">They can represent this pattern as a synchronous operation or as an asynchronous one, so long as when the service is invoked a request-response message exchange takes place.</span></span>  
  
 <span data-ttu-id="ed3ae-152">Genel olarak, sistemleri ile zaman uyumsuz yapısı, bir bağımlılık iş parçacıklarında almamalıdır.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-152">In general, with the asynchronous nature of the systems, you should not take a dependency on the threads.</span></span>  <span data-ttu-id="ed3ae-153">Veri geçirme işlemi gönderme işleminin çeşitli aşamaları için en güvenilir yol uzantıları kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-153">The most reliable way of passing data to various stages of operation dispatch processing is to use extensions.</span></span>  
  
 <span data-ttu-id="ed3ae-154">Bir örnek için bkz: [nasıl yapılır: zaman uyumsuz bir hizmet işlemi uygulama](../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span><span class="sxs-lookup"><span data-stu-id="ed3ae-154">For an example, see [How to: Implement an Asynchronous Service Operation](../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span></span>  
  
 <span data-ttu-id="ed3ae-155">Bir sözleşme işlemi tanımlamak için `X` , yürütüldüğünde zaman uyumsuz olarak istemci uygulamasında nasıl çağrılır bağımsız olarak:</span><span class="sxs-lookup"><span data-stu-id="ed3ae-155">To define a contract operation `X` that is executed asynchronously regardless of how it is called in the client application:</span></span>  
  
-   <span data-ttu-id="ed3ae-156">Desen kullanan iki yöntem tanımlamak `BeginOperation` ve `EndOperation`.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-156">Define two methods using the pattern `BeginOperation` and `EndOperation`.</span></span>  
  
-   <span data-ttu-id="ed3ae-157">`BeginOperation` Yöntemi içerir `in` ve `ref` parametreleri döndürür ve işlem için bir <xref:System.IAsyncResult> türü.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-157">The `BeginOperation` method includes `in` and `ref` parameters for the operation and returns an <xref:System.IAsyncResult> type.</span></span>  
  
-   <span data-ttu-id="ed3ae-158">`EndOperation` Yöntemi içeren bir <xref:System.IAsyncResult> parametresi yanı sıra `out` ve `ref` parametreleri ve döndürür işlemleri dönüş türü.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-158">The `EndOperation` method includes an <xref:System.IAsyncResult> parameter as well as the `out` and `ref` parameters and returns the operations return type.</span></span>  
  
 <span data-ttu-id="ed3ae-159">Örneğin, aşağıdaki yöntemi bakın.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-159">For example, see the following method.</span></span>  
  
```csharp  
int DoWork(string data, ref string inout, out string outonly)  
```  
  
```vb  
Function DoWork(ByVal data As String, ByRef inout As String, _out outonly As out) As Integer  
```  
  
 <span data-ttu-id="ed3ae-160">Zaman uyumsuz bir işlem oluşturmak için iki yöntem olacaktır:</span><span class="sxs-lookup"><span data-stu-id="ed3ae-160">To create an asynchronous operation, the two methods would be:</span></span>  
  
```csharp  
[OperationContract(AsyncPattern=true)]IAsyncResult BeginDoWork(string data,                           ref string inout,                           AsyncCallback callback,                           object state);int EndDoWork(ref string inout, out string outonly, IAsyncResult result);  
```  
  
```vb  
<OperationContract(AsyncPattern := True)>  _Function BeginDoWork(ByVal data As String, _                 ByRef inout As String, _                 ByVal callback As AsyncCallback, _                 ByVal state As Object) _As IAsyncResult Function EndDoWork(ByRef inout As String, _        ByRef outonly As String, _        ByVal result As IAsyncResult) _As Integer  
```  
  
> [!NOTE]
>  <span data-ttu-id="ed3ae-161"><xref:System.ServiceModel.OperationContractAttribute> Özniteliği yalnızca uygulanan `BeginDoWork` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-161">The <xref:System.ServiceModel.OperationContractAttribute> attribute is applied only to the `BeginDoWork` method.</span></span> <span data-ttu-id="ed3ae-162">Adlı bir WSDL işleminde ortaya çıkan sözleşmeyi var `DoWork`.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-162">The resulting contract has one WSDL operation named `DoWork`.</span></span>  
  
### <a name="client-side-asynchronous-invocations"></a><span data-ttu-id="ed3ae-163">İstemci tarafı zaman uyumsuz çağrıları</span><span class="sxs-lookup"><span data-stu-id="ed3ae-163">Client-Side Asynchronous Invocations</span></span>  
 <span data-ttu-id="ed3ae-164">Bir WCF istemci uygulamasının daha önce açıklanan üç zaman uyumsuz çağırma modellerinden herhangi biri kullanabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="ed3ae-164">A WCF client application can use any of three asynchronous calling models described previously</span></span>  
  
 <span data-ttu-id="ed3ae-165">Görev tabanlı modeli kullanılırken, yalnızca aşağıdaki kod parçacığında gösterildiği gibi bekleme anahtar kullanarak işlemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-165">When using the task-based model, simply call the operation using the await keyword as shown in the following code snippet.</span></span>  
  
```  
await simpleServiceClient.SampleMethodTaskAsync("hello, world");  
```  
  
 <span data-ttu-id="ed3ae-166">Olay tabanlı zaman uyumsuz desen kullanma yalnızca--yanıt ve sonuçta elde edilen olay bildirim almak için bir olay işleyicisi kullanıcı arabirimi iş parçacığı üzerinde otomatik olarak tetiklenir ekleme gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-166">Using the event-based asynchronous pattern only requires adding an event handler to receive a notification of the response -- and the resulting event is raised on the user interface thread automatically.</span></span> <span data-ttu-id="ed3ae-167">Bu yaklaşımı kullanmak için her ikisini de belirtin **/async** ve **/tcv:Version35** komutu seçenekleri ile [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), aşağıdaki gibi örnek.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-167">To use this approach, specify both the **/async** and **/tcv:Version35** command options with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), as in the following example.</span></span>  
  
```  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async /tcv:Version35  
```  
  
 <span data-ttu-id="ed3ae-168">Bu yapıldığında, Svcutil.exe WCF istemci sınıfı uygulamak ve yanıtını alma ve uygun eylemi gerçekleştirin olay işleyici atamak çağrı yapan uygulamanın sağlayan olay alt yapısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-168">When this is done, Svcutil.exe generates a WCF client class with the event infrastructure that enables the calling application to implement and assign an event handler to receive the response and take the appropriate action.</span></span> <span data-ttu-id="ed3ae-169">Tam bir örnek için bkz: [nasıl yapılır: hizmet işlemlerini zaman uyumsuz çağrı](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="ed3ae-169">For a complete example, see [How to: Call Service Operations Asynchronously](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span>  
  
 <span data-ttu-id="ed3ae-170">Olay tabanlı zaman uyumsuz modeli, ancak yalnızca kullanılabilir [!INCLUDE[netfx35_long](../../../includes/netfx35-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ed3ae-170">The event-based asynchronous model, however, is only available in [!INCLUDE[netfx35_long](../../../includes/netfx35-long-md.md)].</span></span> <span data-ttu-id="ed3ae-171">Ayrıca, bile desteklenmez [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] bir WCF istemcisi kanalını oluşturulduğunda kullanarak bir <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-171">In addition, it is not supported even in [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] when a WCF client channel is created by using a <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ed3ae-172">WCF istemci kanalı nesneleriyle kullanmalısınız <xref:System.IAsyncResult?displayProperty=nameWithType> nesneleri işlemlerinizin zaman uyumsuz olarak çağırma.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-172">With WCF client channel objects, you must use <xref:System.IAsyncResult?displayProperty=nameWithType> objects to invoke your operations asynchronously.</span></span> <span data-ttu-id="ed3ae-173">Bu yaklaşımı kullanmak için belirtmek **/async** komut seçeneğiyle [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), aşağıdaki örnekte olduğu gibi.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-173">To use this approach, specify the **/async** command option with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), as in the following example.</span></span>  
  
```  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async   
```  
  
 <span data-ttu-id="ed3ae-174">Bu hizmet sözleşmesini oluşturur, her bir işlem olarak Modellenen içinde bir `<Begin>` yöntemiyle <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> özelliğini `true` ve karşılık gelen `<End>` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-174">This generates a service contract in which each operation is modeled as a `<Begin>` method with the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property set to `true` and a corresponding `<End>` method.</span></span> <span data-ttu-id="ed3ae-175">Tam örnek kullanmak için bir <xref:System.ServiceModel.ChannelFactory%601>, bkz: [nasıl yapılır: çağrı işlemlerini zaman uyumsuz olarak kullanarak bir kanal fabrikası](../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span><span class="sxs-lookup"><span data-stu-id="ed3ae-175">For a complete example using a <xref:System.ServiceModel.ChannelFactory%601>, see [How to: Call Operations Asynchronously Using a Channel Factory](../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span></span>  
  
 <span data-ttu-id="ed3ae-176">Hizmet eşzamanlı olarak, bir uygulamanın aynı düzeni zaman uyumsuz olarak yerel bir zaman uyumlu yöntemi çağırmak için kullanabileceği aynı şekilde uygulanır olsa bile her iki durumda da, uygulamalar bir işlem zaman uyumsuz olarak çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-176">In either case, applications can invoke an operation asynchronously even if the service is implemented synchronously, in the same way that an application can use the same pattern to invoke asynchronously a local synchronous method.</span></span> <span data-ttu-id="ed3ae-177">İşlemi nasıl uygulandığını istemciye önemli değildir; yanıt iletisi geldiğinde içeriğini istemcinin zaman uyumsuz gönderilir <`End`> yöntemi ve istemci bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-177">How the operation is implemented is not significant to the client; when the response message arrives, its content is dispatched to the client's asynchronous <`End`> method and the client retrieves the information.</span></span>  
  
### <a name="one-way-message-exchange-patterns"></a><span data-ttu-id="ed3ae-178">Tek yönlü ileti Exchange desenleri</span><span class="sxs-lookup"><span data-stu-id="ed3ae-178">One-Way Message Exchange Patterns</span></span>  
 <span data-ttu-id="ed3ae-179">Zaman uyumsuz ileti değişim deseni tek yönlü hangi işlemleri de oluşturabilirsiniz (işlemleri için hangi <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> olan `true` bağıntılı yanıt sahip) herhangi bir yönde istemci veya hizmet birbirinden gönderilebilecek yan.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-179">You can also create an asynchronous message exchange pattern in which one-way operations (operations for which the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> is `true` have no correlated response) can be sent in either direction by the client or service independently of the other side.</span></span> <span data-ttu-id="ed3ae-180">(Bu çift yönlü ileti değişim deseni tek yönlü iletilerle kullanır.) Bu durumda, hizmet sözleşmesi zaman uyumsuz çağrılar veya uygulamaları ya da değil, uygun taraflardan uygulayabileceğiniz bir tek yönlü ileti değişimi belirtir.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-180">(This uses the duplex message exchange pattern with one-way messages.) In this case, the service contract specifies a one-way message exchange that either side can implement as asynchronous calls or implementations, or not, as appropriate.</span></span> <span data-ttu-id="ed3ae-181">Sözleşme tek yönlü iletilerinin bir exchange olduğunda, bir ileti gönderildikten sonra uygulama yanıt beklemez ve diğer iş yapmadan devam etmek için genellikle, uygulamaları büyük ölçüde zaman uyumsuz olabilir.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-181">Generally, when the contract is an exchange of one-way messages, the implementations can largely be asynchronous because once a message is sent the application does not wait for a reply and can continue doing other work.</span></span>  
  
### <a name="event-based-asynchronous-clients-and-message-contracts"></a><span data-ttu-id="ed3ae-182">Olay tabanlı zaman uyumsuz istemcileri ve ileti sözleşmeleri</span><span class="sxs-lookup"><span data-stu-id="ed3ae-182">Event-based Asynchronous Clients and Message Contracts</span></span>  
 <span data-ttu-id="ed3ae-183">Olay tabanlı zaman uyumsuz modeli için tasarım yönergeleri birden fazla değer döndürülürse, tek bir değer olarak döndürülen durum `Result` özelliği ve diğerleri döndürülür özellikleri olarak üzerinde <xref:System.EventArgs> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-183">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="ed3ae-184">Bunun bir sonucu olduğundan, bu, istemci olay tabanlı zaman uyumsuz komut seçeneklerini kullanarak meta verilerini alır ve birden fazla değer, varsayılan işlemi döndürürse <xref:System.EventArgs> nesnesi döndüren bir değer olarak `Result` özelliği ve geri kalan özelliklerini <xref:System.EventArgs> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-184">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.</span></span>  
  
 <span data-ttu-id="ed3ae-185">İleti nesnesi olarak almak istiyorsanız `Result` özelliği ve bu nesne üzerinde özellikleri kullanma gibi döndürülen değerlere sahip **/messageContract** komut seçeneği.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-185">If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the **/messageContract** command option.</span></span> <span data-ttu-id="ed3ae-186">Bu olarak yanıt iletisi döndüren bir imza oluşturur `Result` özellikte <xref:System.EventArgs> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-186">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="ed3ae-187">Tüm iç dönüş değerleri yanıt iletisi nesnesi sonra özellikleridir.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-187">All internal return values are then properties of the response message object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed3ae-188">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ed3ae-188">See Also</span></span>  
 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A>  
 <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A>
