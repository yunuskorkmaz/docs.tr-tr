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
ms.openlocfilehash: c2948cf76f7763eae51689973346965bc6c720a8
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47171302"
---
# <a name="synchronous-and-asynchronous-operations"></a><span data-ttu-id="07597-102">Zaman Uyumlu ve Zaman Uyumsuz İşlemler</span><span class="sxs-lookup"><span data-stu-id="07597-102">Synchronous and Asynchronous Operations</span></span>
<span data-ttu-id="07597-103">Bu konuda, uygulama ve zaman uyumsuz hizmet işlemleri çağırma anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="07597-103">This topic discusses implementing and calling asynchronous service operations.</span></span>  
  
 <span data-ttu-id="07597-104">Yöntem çağrısının çalışırken yararlı iş yapmadan devam etmek uygulamayı sağladığından, birçok uygulama yöntemler zaman uyumsuz olarak çağırır.</span><span class="sxs-lookup"><span data-stu-id="07597-104">Many applications call methods asynchronously because it enables the application to continue doing useful work while the method call runs.</span></span> <span data-ttu-id="07597-105">Windows Communication Foundation (WCF) hizmet ve istemcileri, WCF uygulamaları göre etkileşim olanağı sunan aktarım hızını en üst düzeye çıkarmak için daha fazla esneklik sağlayan iki farklı düzeyde uygulama zaman uyumsuz işlem çağrıları katılabilir .</span><span class="sxs-lookup"><span data-stu-id="07597-105">Windows Communication Foundation (WCF) services and clients can participate in asynchronous operation calls at two distinct levels of the application, which provide WCF applications even more flexibility to maximize throughput balanced against interactivity.</span></span>  
  
## <a name="types-of-asynchronous-operations"></a><span data-ttu-id="07597-106">Zaman uyumsuz işlemlerin türleri</span><span class="sxs-lookup"><span data-stu-id="07597-106">Types of Asynchronous Operations</span></span>  
 <span data-ttu-id="07597-107">Tüm hizmet ne olursa olsun parametre türleri WCF, sözleşmeler ve dönüş değerleri, WCF öznitelikleri, hizmet ve istemci arasında belirli bir ileti değişim deseni belirtin kullanacağınız.</span><span class="sxs-lookup"><span data-stu-id="07597-107">All service contracts in WCF, no matter the parameters types and return values, use WCF attributes to specify a particular message exchange pattern between client and service.</span></span> <span data-ttu-id="07597-108">WCF uygun bir hizmet işlemi ya da çalışan istemci kodu gelen ve giden iletileri otomatik olarak yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="07597-108">WCF automatically routes inbound and outbound messages to the appropriate service operation or running client code.</span></span>  
  
 <span data-ttu-id="07597-109">İstemci, yalnızca belirli bir işlem için ileti değişim deseni belirtir hizmet sözleşmesini sahiptir.</span><span class="sxs-lookup"><span data-stu-id="07597-109">The client possesses only the service contract, which specifies the message exchange pattern for a particular operation.</span></span> <span data-ttu-id="07597-110">Temel alınan ileti değişim deseni gözlemlenen sürece istemciler Geliştirici tercih ettikleri herhangi bir programlama modeli sunabilir.</span><span class="sxs-lookup"><span data-stu-id="07597-110">Clients can offer the developer any programming model they choose, so long as the underlying message exchange pattern is observed.</span></span> <span data-ttu-id="07597-111">Belirtilen iletiyi deseni gözlemlenen sürece bu nedenle, çok, hizmetleri işlemleri herhangi bir şekilde uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="07597-111">So, too, can services implement operations in any manner, so long as the specified message pattern is observed.</span></span>  
  
 <span data-ttu-id="07597-112">Hizmet sözleşmesinin bağımsızlığı hizmet veya istemci uygulamadan WCF uygulamalarında zaman uyumsuz yürütme aşağıdaki biçimleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="07597-112">The independence of the service contract from either the service or client implementation enables the following forms of asynchronous execution in WCF applications:</span></span>  
  
-   <span data-ttu-id="07597-113">İstemciler, zaman uyumsuz olarak bir eş zamanlı ileti alışverişi kullanarak istek/yanıt işlemleri çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07597-113">Clients can invoke request/response operations asynchronously using a synchronous message exchange.</span></span>  
  
-   <span data-ttu-id="07597-114">Hizmetleri, zaman uyumsuz olarak bir eş zamanlı ileti alışverişi kullanarak bir istek/yanıt işlemi uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="07597-114">Services can implement a request/response operation asynchronously using a synchronous message exchange.</span></span>  
  
-   <span data-ttu-id="07597-115">Mesaj tek yönlü istemci veya hizmet ne olursa olsun uygulaması olabilir.</span><span class="sxs-lookup"><span data-stu-id="07597-115">Message exchanges can be one-way, regardless of the implementation of the client or service.</span></span>  
  
### <a name="suggested-asynchronous-scenarios"></a><span data-ttu-id="07597-116">Önerilen zaman uyumsuz senaryolar</span><span class="sxs-lookup"><span data-stu-id="07597-116">Suggested Asynchronous Scenarios</span></span>  
 <span data-ttu-id="07597-117">İşlemi hizmet uygulaması g/ç iş yapmak gibi bir engelleme çağrı yaparsa bir hizmet işlemi uygulamasında zaman uyumsuz bir yaklaşım kullanın.</span><span class="sxs-lookup"><span data-stu-id="07597-117">Use an asynchronous approach in a service operation implementation if the operation service implementation makes a blocking call, such as doing I/O work.</span></span> <span data-ttu-id="07597-118">Zaman uyumsuz işlem uygulama olduğunda zaman uyumsuz işlemler ve zaman uyumsuz çağrı yolun mümkün olduğunca uzak onaylamaktan genişletmek için yöntemleri çağırmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="07597-118">When you are in an asynchronous operation implementation, try to call asynchronous operations and methods to extend the asynchronous call path as far as possible.</span></span> <span data-ttu-id="07597-119">Örneğin, bir `BeginOperationTwo()` içinden `BeginOperationOne()`.</span><span class="sxs-lookup"><span data-stu-id="07597-119">For example, call a `BeginOperationTwo()` from within `BeginOperationOne()`.</span></span>  
  
-   <span data-ttu-id="07597-120">Zaman uyumsuz bir yaklaşım istemcisinde veya çağıran uygulama aşağıdaki durumlarda kullanın:</span><span class="sxs-lookup"><span data-stu-id="07597-120">Use an asynchronous approach in a client or calling application in the following cases:</span></span>  
  
-   <span data-ttu-id="07597-121">Bir orta katman uygulamasından işlemleri çağırdığınız durumunda.</span><span class="sxs-lookup"><span data-stu-id="07597-121">If you are invoking operations from a middle-tier application.</span></span> <span data-ttu-id="07597-122">(Bu tür senaryolar hakkında daha fazla bilgi için bkz. [orta katman istemci uygulamaları](../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md).)</span><span class="sxs-lookup"><span data-stu-id="07597-122">(For more information about such scenarios, see [Middle-Tier Client Applications](../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md).)</span></span>  
  
-   <span data-ttu-id="07597-123">ASP.NET sayfası içinde işlemleri çağırdığınız, zaman uyumsuz sayfalar kullanın.</span><span class="sxs-lookup"><span data-stu-id="07597-123">If you are invoking operations within an ASP.NET page, use asynchronous pages.</span></span>  
  
-   <span data-ttu-id="07597-124">Tek iş parçacıklı, Windows Forms veya Windows Presentation Foundation (WPF) gibi herhangi bir uygulamadan işlemleri çağırdığınız durumunda.</span><span class="sxs-lookup"><span data-stu-id="07597-124">If you are invoking operations from any application that is single threaded, such as Windows Forms or Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="07597-125">Olay tabanlı zaman uyumsuz çağırma modeli kullanılırken, sonuç olay yanıt hızını kendiniz birden çok iş parçacığı işlemeye gerek kalmadan uygulamaya ekleme UI iş parçacığı üzerinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="07597-125">When using the event-based asynchronous calling model, the result event is raised on the UI thread, adding responsiveness to the application without requiring you to handle multiple threads yourself.</span></span>  
  
-   <span data-ttu-id="07597-126">Genel olarak, zaman uyumlu ve zaman uyumsuz bir çağrı arasında seçim yapma varsa, zaman uyumsuz çağrı'ı seçin.</span><span class="sxs-lookup"><span data-stu-id="07597-126">In general, if you have a choice between a synchronous and asynchronous call, choose the asynchronous call.</span></span>  
  
### <a name="implementing-an-asynchronous-service-operation"></a><span data-ttu-id="07597-127">Zaman uyumsuz bir hizmet işlemi uygulama</span><span class="sxs-lookup"><span data-stu-id="07597-127">Implementing an Asynchronous Service Operation</span></span>  
 <span data-ttu-id="07597-128">Aşağıdaki üç yöntemden birini kullanarak zaman uyumsuz işlemler uygulanabilir:</span><span class="sxs-lookup"><span data-stu-id="07597-128">Asynchronous operations can be implemented by using one of the three following methods:</span></span>  
  
1.  <span data-ttu-id="07597-129">Görev tabanlı zaman uyumsuz desen</span><span class="sxs-lookup"><span data-stu-id="07597-129">The task-based asynchronous pattern</span></span>  
  
2.  <span data-ttu-id="07597-130">Olay tabanlı zaman uyumsuz desen</span><span class="sxs-lookup"><span data-stu-id="07597-130">The event-based asynchronous pattern</span></span>  
  
3.  <span data-ttu-id="07597-131">IAsyncResult zaman uyumsuz desen</span><span class="sxs-lookup"><span data-stu-id="07597-131">The IAsyncResult asynchronous pattern</span></span>  
  
#### <a name="task-based-asynchronous-pattern"></a><span data-ttu-id="07597-132">Görev tabanlı zaman uyumsuz desen</span><span class="sxs-lookup"><span data-stu-id="07597-132">Task-Based Asynchronous Pattern</span></span>  
 <span data-ttu-id="07597-133">Görev tabanlı zaman uyumsuz desen, kolay ve oldukça büyük olduğundan zaman uyumsuz işlemleri uygulamak için tercih edilen yoludur.</span><span class="sxs-lookup"><span data-stu-id="07597-133">The task-based asynchronous pattern is the preferred way to implement asynchronous operations because it is the easiest and most straight forward.</span></span> <span data-ttu-id="07597-134">Bu yöntemi kullanmak için yalnızca, bir hizmet işlemi uygulama ve görev dönüş türü belirtin\<T >, burada T mantıksal işlem tarafından döndürülen türdür.</span><span class="sxs-lookup"><span data-stu-id="07597-134">To use this method simply implement your service operation and specify a return type of Task\<T>, where T is the type returned by the logical operation.</span></span> <span data-ttu-id="07597-135">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="07597-135">For example:</span></span>  
  
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
  
 <span data-ttu-id="07597-136">Görev SampleMethodTaskAsync işlemi döndürür\<dizesi > çünkü mantıksal işlemi bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="07597-136">The SampleMethodTaskAsync operation returns Task\<string> because the logical operation returns a string.</span></span> <span data-ttu-id="07597-137">Görev tabanlı zaman uyumsuz desen hakkında daha fazla bilgi için bkz: [The Task-Based zaman uyumsuz desen](https://go.microsoft.com/fwlink/?LinkId=232504).</span><span class="sxs-lookup"><span data-stu-id="07597-137">For more information about the task-based asynchronous pattern, see [The Task-Based Asynchronous Pattern](https://go.microsoft.com/fwlink/?LinkId=232504).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="07597-138">Üzerinde işlemin tamamlanması beklenirken bir özel durum oluştuğu takdirde görev tabanlı zaman uyumsuz deseni kullanılırken, bir T:System.AggregateException durum.</span><span class="sxs-lookup"><span data-stu-id="07597-138">When using the task-based asynchronous pattern, a T:System.AggregateException may be thrown if an exception occurs while waiting on the completion of the operation.</span></span> <span data-ttu-id="07597-139">Bu durum istemci veya hizmet oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="07597-139">This exception may occur on the client or services</span></span>  
  
#### <a name="event-based-asynchronous-pattern"></a><span data-ttu-id="07597-140">Olay tabanlı zaman uyumsuz desen</span><span class="sxs-lookup"><span data-stu-id="07597-140">Event-Based Asynchronous Pattern</span></span>  
 <span data-ttu-id="07597-141">Olay tabanlı zaman uyumsuz deseni destekleyen bir hizmet MethodNameAsync adlı bir veya daha fazla işlem gerekir.</span><span class="sxs-lookup"><span data-stu-id="07597-141">A service that supports the Event-based Asynchronous Pattern will have one or more operations named MethodNameAsync.</span></span> <span data-ttu-id="07597-142">Bu yöntemler, zaman uyumlu sürümler, geçerli iş parçacığında aynı işlemi yansıtma.</span><span class="sxs-lookup"><span data-stu-id="07597-142">These methods may mirror synchronous versions, which perform the same operation on the current thread.</span></span> <span data-ttu-id="07597-143">Sınıfı ayrıca MethodNameCompleted olay olabilir ve bir MethodNameAsyncCancel (veya yalnızca CancelAsync) olabilir yöntemi.</span><span class="sxs-lookup"><span data-stu-id="07597-143">The class may also have a MethodNameCompleted event and it may have a MethodNameAsyncCancel (or simply CancelAsync) method.</span></span> <span data-ttu-id="07597-144">İşlem çağırma isteyen bir istemci işlemi tamamlandığında çağrılacak bir olay işleyicisi tanımlar,</span><span class="sxs-lookup"><span data-stu-id="07597-144">A client wishing to call the operation will define an event handler to be called when the operation completes,</span></span>  
  
 <span data-ttu-id="07597-145">Aşağıdaki kod parçacığı, olay tabanlı zaman uyumsuz deseni kullanarak zaman uyumsuz işlemleri nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="07597-145">The following code snippet illustrates how to declare asynchronous operations using the event-based asynchronous pattern.</span></span>  
  
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
  
 <span data-ttu-id="07597-146">Olay tabanlı zaman uyumsuz desen hakkında daha fazla bilgi için bkz: [The Event-Based zaman uyumsuz desen](https://go.microsoft.com/fwlink/?LinkId=232515).</span><span class="sxs-lookup"><span data-stu-id="07597-146">For more information about the Event-based Asynchronous Pattern, see [The Event-Based Asynchronous Pattern](https://go.microsoft.com/fwlink/?LinkId=232515).</span></span>  
  
#### <a name="iasyncresult-asynchronous-pattern"></a><span data-ttu-id="07597-147">IAsyncResult zaman uyumsuz desen</span><span class="sxs-lookup"><span data-stu-id="07597-147">IAsyncResult Asynchronous Pattern</span></span>  
 <span data-ttu-id="07597-148">Bir zaman uyumsuz bir biçimde kullanarak bir hizmet işlemi uygulanabilir [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] zaman uyumsuz desen programlama ve İşaretleme `<Begin>` yöntemiyle <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="07597-148">A service operation can be implemented in an asynchronous fashion using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] asynchronous programming pattern and marking the `<Begin>` method with the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property set to `true`.</span></span> <span data-ttu-id="07597-149">Bu durumda, zaman uyumsuz işlemi eşzamanlı bir işlem olarak aynı biçiminde meta veriler de sağlanmaktadır: bir istek iletisi ve ilişkili yanıt iletisi ile tek bir işlem olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="07597-149">In this case, the asynchronous operation is exposed in metadata in the same form as a synchronous operation: It is exposed as a single operation with a request message and a correlated response message.</span></span> <span data-ttu-id="07597-150">İstemci programlama modelleri ardından seçeneğiniz vardır.</span><span class="sxs-lookup"><span data-stu-id="07597-150">Client programming models then have a choice.</span></span> <span data-ttu-id="07597-151">Hizmet çağrıldığında bir istek-yanıt iletisi exchange gerçekleşmeden sürece, bu düzen eşzamanlı bir işlem veya zaman uyumsuz bir olarak gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="07597-151">They can represent this pattern as a synchronous operation or as an asynchronous one, so long as when the service is invoked a request-response message exchange takes place.</span></span>  
  
 <span data-ttu-id="07597-152">Genel olarak, sistemleri ile zaman uyumsuz yapısı, bir bağımlılık iş parçacıklarında almamalıdır.</span><span class="sxs-lookup"><span data-stu-id="07597-152">In general, with the asynchronous nature of the systems, you should not take a dependency on the threads.</span></span>  <span data-ttu-id="07597-153">En güvenilir veri geçirme işlemi gönderme işleminin çeşitli aşamaları için uzantıları kullanmak için yoludur.</span><span class="sxs-lookup"><span data-stu-id="07597-153">The most reliable way of passing data to various stages of operation dispatch processing is to use extensions.</span></span>  
  
 <span data-ttu-id="07597-154">Bir örnek için bkz. [nasıl yapılır: zaman uyumsuz bir hizmet işlemi uygulama](../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span><span class="sxs-lookup"><span data-stu-id="07597-154">For an example, see [How to: Implement an Asynchronous Service Operation](../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span></span>  
  
 <span data-ttu-id="07597-155">Bir sözleşme işlemi tanımlamak için `X` , yürütüldüğünde zaman uyumsuz olarak istemci uygulamasına nasıl adlandırılır bağımsız olarak:</span><span class="sxs-lookup"><span data-stu-id="07597-155">To define a contract operation `X` that is executed asynchronously regardless of how it is called in the client application:</span></span>  
  
-   <span data-ttu-id="07597-156">Desenini kullanarak, iki definovat `BeginOperation` ve `EndOperation`.</span><span class="sxs-lookup"><span data-stu-id="07597-156">Define two methods using the pattern `BeginOperation` and `EndOperation`.</span></span>  
  
-   <span data-ttu-id="07597-157">`BeginOperation` İncludes yöntemi `in` ve `ref` döndürür ve işlem parametreleri bir <xref:System.IAsyncResult> türü.</span><span class="sxs-lookup"><span data-stu-id="07597-157">The `BeginOperation` method includes `in` and `ref` parameters for the operation and returns an <xref:System.IAsyncResult> type.</span></span>  
  
-   <span data-ttu-id="07597-158">`EndOperation` Yöntemi içeren bir <xref:System.IAsyncResult> parametresi hem de `out` ve `ref` parametreleri ve işlemleri döndürür dönüş türü.</span><span class="sxs-lookup"><span data-stu-id="07597-158">The `EndOperation` method includes an <xref:System.IAsyncResult> parameter as well as the `out` and `ref` parameters and returns the operations return type.</span></span>  
  
 <span data-ttu-id="07597-159">Örneğin, aşağıdaki yöntemi bakın.</span><span class="sxs-lookup"><span data-stu-id="07597-159">For example, see the following method.</span></span>  
  
```csharp  
int DoWork(string data, ref string inout, out string outonly)  
```  
  
```vb  
Function DoWork(ByVal data As String, ByRef inout As String, _out outonly As out) As Integer  
```  
  
 <span data-ttu-id="07597-160">Zaman uyumsuz bir işlem oluşturmak için iki yöntem olacaktır:</span><span class="sxs-lookup"><span data-stu-id="07597-160">To create an asynchronous operation, the two methods would be:</span></span>  
  
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
>  <span data-ttu-id="07597-161"><xref:System.ServiceModel.OperationContractAttribute> Özniteliği yalnızca uygulandığında `BeginDoWork` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="07597-161">The <xref:System.ServiceModel.OperationContractAttribute> attribute is applied only to the `BeginDoWork` method.</span></span> <span data-ttu-id="07597-162">Elde edilen sözleşmesi adlı tek bir WSDL işlem sahip `DoWork`.</span><span class="sxs-lookup"><span data-stu-id="07597-162">The resulting contract has one WSDL operation named `DoWork`.</span></span>  
  
### <a name="client-side-asynchronous-invocations"></a><span data-ttu-id="07597-163">İstemci tarafı zaman uyumsuz çağrılar</span><span class="sxs-lookup"><span data-stu-id="07597-163">Client-Side Asynchronous Invocations</span></span>  
 <span data-ttu-id="07597-164">WCF istemci uygulaması daha önce açıklanan üç zaman uyumsuz çağırma model dilediğinizi kullanabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="07597-164">A WCF client application can use any of three asynchronous calling models described previously</span></span>  
  
 <span data-ttu-id="07597-165">Görev tabanlı modeli kullanılırken, aşağıdaki kod parçacığında gösterildiği gibi await anahtar sözcüğü kullanılarak işlemi çağırarak yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="07597-165">When using the task-based model, simply call the operation using the await keyword as shown in the following code snippet.</span></span>  
  
```  
await simpleServiceClient.SampleMethodTaskAsync("hello, world");  
```  
  
 <span data-ttu-id="07597-166">Olay tabanlı zaman uyumsuz desen kullanma yalnızca yanıt--ve sonuçta elde edilen olay bildirim almak için bir olay işleyicisi kullanıcı arabirimi iş parçacığı üzerinde otomatik olarak oluşturulan ekleme gerektirir.</span><span class="sxs-lookup"><span data-stu-id="07597-166">Using the event-based asynchronous pattern only requires adding an event handler to receive a notification of the response -- and the resulting event is raised on the user interface thread automatically.</span></span> <span data-ttu-id="07597-167">Bu yaklaşımı kullanmak için her ikisini birden belirtin **/async** ve **/tcv:Version35** komutu seçeneklerle [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), aşağıdaki gibi örnek.</span><span class="sxs-lookup"><span data-stu-id="07597-167">To use this approach, specify both the **/async** and **/tcv:Version35** command options with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), as in the following example.</span></span>  
  
```  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async /tcv:Version35  
```  
  
 <span data-ttu-id="07597-168">Bu yapıldığında, bir WCF istemcisi sınıfı uygulamak ve uygun eylemi gerçekleştirin ve yanıt almak için bir olay işleyicisi atamak çağıran uygulama sağlayan bir olay altyapı Svcutil.exe oluşturur.</span><span class="sxs-lookup"><span data-stu-id="07597-168">When this is done, Svcutil.exe generates a WCF client class with the event infrastructure that enables the calling application to implement and assign an event handler to receive the response and take the appropriate action.</span></span> <span data-ttu-id="07597-169">Tam bir örnek için bkz. [nasıl yapılır: hizmet işlemlerini zaman uyumsuz çağrı](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="07597-169">For a complete example, see [How to: Call Service Operations Asynchronously](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span>  
  
 <span data-ttu-id="07597-170">Olay tabanlı zaman uyumsuz model, ancak yalnızca kullanılabilir [!INCLUDE[netfx35_long](../../../includes/netfx35-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="07597-170">The event-based asynchronous model, however, is only available in [!INCLUDE[netfx35_long](../../../includes/netfx35-long-md.md)].</span></span> <span data-ttu-id="07597-171">Ayrıca, bu bile desteklenmez [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] bir WCF istemcisi kanalını oluşturulduğunda kullanarak bir <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="07597-171">In addition, it is not supported even in [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] when a WCF client channel is created by using a <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="07597-172">WCF istemci kanal nesneleriyle kullanmalısınız <xref:System.IAsyncResult?displayProperty=nameWithType> işlemlerinizi zaman uyumsuz olarak çağrılacak nesneleri.</span><span class="sxs-lookup"><span data-stu-id="07597-172">With WCF client channel objects, you must use <xref:System.IAsyncResult?displayProperty=nameWithType> objects to invoke your operations asynchronously.</span></span> <span data-ttu-id="07597-173">Bu yaklaşımı kullanmak için belirtin **/async** komut seçeneğiyle [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), aşağıdaki örnekte olduğu gibi.</span><span class="sxs-lookup"><span data-stu-id="07597-173">To use this approach, specify the **/async** command option with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), as in the following example.</span></span>  
  
```  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async   
```  
  
 <span data-ttu-id="07597-174">Bu hizmet sözleşmesini oluşturur, her bir işlem olarak modellenir içinde bir `<Begin>` yöntemiyle <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> özelliğini `true` ve karşılık gelen `<End>` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="07597-174">This generates a service contract in which each operation is modeled as a `<Begin>` method with the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property set to `true` and a corresponding `<End>` method.</span></span> <span data-ttu-id="07597-175">Kullanarak tam bir örnek için bir <xref:System.ServiceModel.ChannelFactory%601>, bkz: [nasıl yapılır: çağrı işlemlerini zaman uyumsuz olarak kullanarak kanal fabrikası](../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span><span class="sxs-lookup"><span data-stu-id="07597-175">For a complete example using a <xref:System.ServiceModel.ChannelFactory%601>, see [How to: Call Operations Asynchronously Using a Channel Factory](../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span></span>  
  
 <span data-ttu-id="07597-176">Hizmet eşzamanlı olarak, bir uygulama zaman uyumsuz olarak yerel bir zaman uyumlu yöntem çağırmak için aynı yöntemi kullanabileceğiniz aynı şekilde uygulanır olsa bile her iki durumda da, uygulamaları bir işlem zaman uyumsuz olarak çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07597-176">In either case, applications can invoke an operation asynchronously even if the service is implemented synchronously, in the same way that an application can use the same pattern to invoke asynchronously a local synchronous method.</span></span> <span data-ttu-id="07597-177">İşleminin nasıl uygulandığını istemciye önemli değildir; yanıt iletisi geldiğinde içeriğini istemcinin zaman uyumsuz gönderilir <`End`> yöntemi ve istemcinin bilgileri alır.</span><span class="sxs-lookup"><span data-stu-id="07597-177">How the operation is implemented is not significant to the client; when the response message arrives, its content is dispatched to the client's asynchronous <`End`> method and the client retrieves the information.</span></span>  
  
### <a name="one-way-message-exchange-patterns"></a><span data-ttu-id="07597-178">Tek yönlü mesaj Exchange desenleri</span><span class="sxs-lookup"><span data-stu-id="07597-178">One-Way Message Exchange Patterns</span></span>  
 <span data-ttu-id="07597-179">Bir zaman uyumsuz ileti değişim deseni tek yönlü hangi işlemleri oluşturabilirsiniz (hangi işlemleri <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> olduğu `true` bağıntılı yanıt sahip) herhangi bir yönde birbirinden hizmet ve istemci tarafından gönderilen yan.</span><span class="sxs-lookup"><span data-stu-id="07597-179">You can also create an asynchronous message exchange pattern in which one-way operations (operations for which the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> is `true` have no correlated response) can be sent in either direction by the client or service independently of the other side.</span></span> <span data-ttu-id="07597-180">(Bu çift yönlü ileti değişim deseni ile tek yönlü iletilerini kullanır.) Bu durumda, hizmet sözleşmesi zaman uyumsuz çağrıları veya uygulamaları ya da değil, uygun şekilde, her iki tarafında uygulayan bir tek yönlü mesaj exchange belirtir.</span><span class="sxs-lookup"><span data-stu-id="07597-180">(This uses the duplex message exchange pattern with one-way messages.) In this case, the service contract specifies a one-way message exchange that either side can implement as asynchronous calls or implementations, or not, as appropriate.</span></span> <span data-ttu-id="07597-181">Sözleşmenin bir exchange tek yönlü bir ileti olduğunda, bir ileti gönderildikten sonra uygulama için bir yanıt beklemez'yı ve başka çalışma yapmaya devam edebilirsiniz genel olarak, uygulamaları büyük ölçüde zaman uyumsuz olabilir.</span><span class="sxs-lookup"><span data-stu-id="07597-181">Generally, when the contract is an exchange of one-way messages, the implementations can largely be asynchronous because once a message is sent the application does not wait for a reply and can continue doing other work.</span></span>  
  
### <a name="event-based-asynchronous-clients-and-message-contracts"></a><span data-ttu-id="07597-182">Olay tabanlı zaman uyumsuz istemcileri ve ileti sözleşmeleri</span><span class="sxs-lookup"><span data-stu-id="07597-182">Event-based Asynchronous Clients and Message Contracts</span></span>  
 <span data-ttu-id="07597-183">Olay tabanlı zaman uyumsuz model için tasarım yönergeleri birden fazla değer döndürmüyorsa, bir değer olarak döndürülen durum `Result` özelliği ve diğerleri döndürülür özellikleri olarak üzerinde <xref:System.EventArgs> nesne.</span><span class="sxs-lookup"><span data-stu-id="07597-183">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="07597-184">Bunun bir sonucu olduğundan, bu, bir istemci, olay tabanlı zaman uyumsuz komut seçeneklerini kullanarak meta verilerini içeri aktarır ve işlemin birden fazla değer, varsayılan döndürürse <xref:System.EventArgs> nesnesini bir değer olarak döndürür `Result` özelliği ve kalan özelliklerini <xref:System.EventArgs> nesne.</span><span class="sxs-lookup"><span data-stu-id="07597-184">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.</span></span>  
  
 <span data-ttu-id="07597-185">İleti nesnesi olarak almak istiyorsanız `Result` özelliği ve o nesnenin özellikleri olarak döndürülen değerlerin **/messageContract** seçeneği komutu.</span><span class="sxs-lookup"><span data-stu-id="07597-185">If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the **/messageContract** command option.</span></span> <span data-ttu-id="07597-186">Bu yanıt iletisi olarak döndüren bir imza oluşturur `Result` özelliği <xref:System.EventArgs> nesne.</span><span class="sxs-lookup"><span data-stu-id="07597-186">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="07597-187">Tüm iç dönüş değerleri ardından yanıt iletisi nesnenin özellikleridir.</span><span class="sxs-lookup"><span data-stu-id="07597-187">All internal return values are then properties of the response message object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07597-188">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="07597-188">See Also</span></span>  
 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A>  
 <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A>
