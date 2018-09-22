---
title: WS İşlem Akışı
ms.date: 03/30/2017
helpviewer_keywords:
- Transactions
ms.assetid: f8eecbcf-990a-4dbb-b29b-c3f9e3b396bd
ms.openlocfilehash: 35af3090c0f898578a5f8dfb81d02d22a0074ad2
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46577840"
---
# <a name="ws-transaction-flow"></a><span data-ttu-id="59eb1-102">WS İşlem Akışı</span><span class="sxs-lookup"><span data-stu-id="59eb1-102">WS Transaction Flow</span></span>
<span data-ttu-id="59eb1-103">Bu örnek, bir istemci Eşgüdümlü işlem kullanımını gösterir ve WS-Atomic işlem ya da OleTransactions protokolünü kullanarak işlem istemci ve sunucu seçeneklerini akış.</span><span class="sxs-lookup"><span data-stu-id="59eb1-103">This sample demonstrates the use of a client-coordinated transaction and the client and server options for transaction flow using either the WS-Atomic Transaction or OleTransactions protocol.</span></span> <span data-ttu-id="59eb1-104">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hesaplayıcı hizmet uygulayan ancak işlemleri kullanımını göstermek için öznitelikli `TransactionFlowAttribute` ile **TransactionFlowOption** ne derece işlem akışı etkin belirlemek için sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="59eb1-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service but the operations are attributed to demonstrate the use of the `TransactionFlowAttribute` with the **TransactionFlowOption** enumeration to determine to what degree transaction flow is enabled.</span></span> <span data-ttu-id="59eb1-105">Akışlı işlem kapsamında, istenen işlemlerin bir günlük veritabanına yazılır ve istemci işlemi tamamlanmazsa, Eşgüdümlü istemci işlemi tamamlanana kadar - devam ederse Web hizmeti işlemi sağlar ilgili güncelleştirmeleri veritabanına iletilmez.</span><span class="sxs-lookup"><span data-stu-id="59eb1-105">Within the scope of the flowed transaction, a log of the requested operations is written to a database and persists until the client coordinated transaction has completed - if the client transaction does not complete, the Web service transaction ensures that the appropriate updates to the database are not committed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="59eb1-106">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="59eb1-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="59eb1-107">İstemci bağlantısına hizmet ve işlem başlatıldıktan sonra birkaç hizmet işlemleri erişir.</span><span class="sxs-lookup"><span data-stu-id="59eb1-107">After initiating a connection to the service and a transaction, the client accesses several service operations.</span></span> <span data-ttu-id="59eb1-108">Hizmet sözleşmesi için farklı bir ayar gösteren işlemlerin her biri ile aşağıdaki gibi tanımlıdır `TransactionFlowOption`.</span><span class="sxs-lookup"><span data-stu-id="59eb1-108">The contract for the service is defined as follows with each of the operations demonstrating a different setting for the `TransactionFlowOption`.</span></span>  

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Add(double n1, double n2);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Allowed)]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.NotAllowed)]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);   
}  
```

 <span data-ttu-id="59eb1-109">Bu, işlenmek üzere oldukları sırayla operations tanımlar:</span><span class="sxs-lookup"><span data-stu-id="59eb1-109">This defines the operations in the order they are to be processed:</span></span>  
  
-   <span data-ttu-id="59eb1-110">Bir `Add` işlem isteği akışlı bir işlem içermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="59eb1-110">An `Add` operation request must include a flowed transaction.</span></span>  
  
-   <span data-ttu-id="59eb1-111">A `Subtract` işlem isteği akışlı bir işlem içerebilir.</span><span class="sxs-lookup"><span data-stu-id="59eb1-111">A `Subtract` operation request may include a flowed transaction.</span></span>  
  
-   <span data-ttu-id="59eb1-112">A `Multiply` işlem isteği açık noktayla ayarı üzerinden akan bir işlem değil içermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="59eb1-112">A `Multiply` operation request must not include a flowed transaction through the explicit NotAllowed setting.</span></span>  
  
-   <span data-ttu-id="59eb1-113">A `Divide` işlem isteği Java'daki üzerinden akan bir işlem değil içermelidir bir `TransactionFlow` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="59eb1-113">A `Divide` operation request must not include a flowed transaction through the omission of a `TransactionFlow` attribute.</span></span>  
  
 <span data-ttu-id="59eb1-114">İşlem akışını bağlamalarla etkinleştirmek için [ \<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) özelliği etkin uygun işlemi özniteliklerine ek olarak kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="59eb1-114">To enable transaction flow, bindings with the [\<transactionFlow>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) property enabled must be used in addition to the appropriate operation attributes.</span></span> <span data-ttu-id="59eb1-115">Bu örnekte, hizmet yapılandırmasının bir TCP uç noktası ve bir meta veri değişimi uç noktası yanı sıra bir HTTP uç noktasını kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="59eb1-115">In this sample, the service's configuration exposes a TCP endpoint and an HTTP endpoint in addition to a Metadata Exchange endpoint.</span></span> <span data-ttu-id="59eb1-116">TCP uç noktası ve HTTP uç noktası, hem de aşağıdaki bağlamaları kullanın [ \<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) özelliği etkin.</span><span class="sxs-lookup"><span data-stu-id="59eb1-116">The TCP endpoint and the HTTP endpoint use the following bindings, both of which have the [\<transactionFlow>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) property enabled.</span></span>  
  
```xml  
<bindings>  
  <netTcpBinding>  
    <binding name="transactionalOleTransactionsTcpBinding"  
             transactionFlow="true"  
             transactionProtocol="OleTransactions"/>  
  </netTcpBinding>  
  <wsHttpBinding>  
    <binding name="transactionalWsatHttpBinding"  
             transactionFlow="true" />  
  </wsHttpBinding>  
</bindings>  
```  
  
> [!NOTE]
>  <span data-ttu-id="59eb1-117">Sistem tarafından sağlanan wsHttpBinding yalnızca daha birlikte çalışabilen WSAtomicTransactionOctober2004 protokolünü kullanır ancak sistem tarafından sağlanan netTcpBinding transactionProtocol belirtilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="59eb1-117">The system-provided netTcpBinding allows specification of the transactionProtocol whereas the system-provided wsHttpBinding uses only the more interoperable WSAtomicTransactionOctober2004 protocol.</span></span> <span data-ttu-id="59eb1-118">Windows Communication Foundation (WCF) istemciler tarafından protokolü yalnızca kullanılabilir OleTransactions kullanın.</span><span class="sxs-lookup"><span data-stu-id="59eb1-118">The OleTransactions protocol is only available for use by Windows Communication Foundation (WCF) clients.</span></span>  
  
 <span data-ttu-id="59eb1-119">Uygulayan bir sınıf için `ICalculator` arabirimi, tüm yöntemleri öznitelikler atanmıştır ile <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="59eb1-119">For the class that implements the `ICalculator` interface, all of the methods are attributed with <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property set to `true`.</span></span> <span data-ttu-id="59eb1-120">Bu ayar, bir işlem kapsamında yöntemi içinde gerçekleştirilen tüm eylemler gerçekleşmesini bildirir.</span><span class="sxs-lookup"><span data-stu-id="59eb1-120">This setting declares that all actions taken within the method occur within the scope of a transaction.</span></span> <span data-ttu-id="59eb1-121">Bu durumda, gerçekleştirilen eylemler için veritabanı günlük kaydı içerir.</span><span class="sxs-lookup"><span data-stu-id="59eb1-121">In this case, the actions taken include recording to the log database.</span></span> <span data-ttu-id="59eb1-122">İşlem isteğini akışlı bir işlem içeriyorsa eylemleri meydana gelen işlem kapsamında veya yeni bir işlem kapsamı otomatik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="59eb1-122">If the operation request includes a flowed transaction then the actions occur within the scope of the incoming transaction or a new transaction scope is automatically generated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="59eb1-123"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> Özellik için hizmet yöntem uygulamaları davranışını yerel tanımlar ve istemcinin yeteneği veya gereksinim akışlı bir işlem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="59eb1-123">The <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property defines behavior local to the service method implementations and does not define the client's ability to or requirement for flowing a transaction.</span></span>  

```csharp
// Service class that implements the service contract.  
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CalculatorService : ICalculator  
{  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Add(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Adding {0} to {1}", n1, n2));  
        return n1 + n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Subtract(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Subtracting {0} from {1}", n2, n1));  
        return n1 - n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Multiply(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Multiplying {0} by {1}", n1, n2));  
        return n1 * n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Divide(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Dividing {0} by {1}", n1, n2));  
        return n1 / n2;  
    }  
  
    // Logging method omitted for brevity  
}  
```

 <span data-ttu-id="59eb1-124">İstemci, hizmeti üzerinde `TransactionFlowOption` işlemleri ayarları, istemcinin oluşturulan tanımı içinde yansıtılır `ICalculator` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="59eb1-124">On the client, the service's `TransactionFlowOption` settings on the operations are reflected in the client's generated definition of the `ICalculator` interface.</span></span> <span data-ttu-id="59eb1-125">Ayrıca, hizmetin `transactionFlow` özellik ayarları, istemci uygulama yapılandırmasında yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="59eb1-125">Also, the service's `transactionFlow` property settings are reflected in the client's application configuration.</span></span> <span data-ttu-id="59eb1-126">İstemci taşıma ve protokolü uygun seçerek seçebilirsiniz `endpointConfigurationName`.</span><span class="sxs-lookup"><span data-stu-id="59eb1-126">The client can select the transport and protocol by selecting the appropriate `endpointConfigurationName`.</span></span>  

```csharp
// Create a client using either wsat or oletx endpoint configurations  
CalculatorClient client = new CalculatorClient("WSAtomicTransaction_endpoint");  
// CalculatorClient client = new CalculatorClient("OleTransactions_endpoint");  
```

> [!NOTE]
>  <span data-ttu-id="59eb1-127">Bu örnek gözlemlenen davranışını hangi protokolü veya aktarım seçilir aynıdır.</span><span class="sxs-lookup"><span data-stu-id="59eb1-127">The observed behavior of this sample is the same no matter which protocol or transport is chosen.</span></span>  
  
 <span data-ttu-id="59eb1-128">İstemci hizmete bağlantı tarafından başlatılan yeni bir oluşturur `TransactionScope` geçici hizmet işlemlerine çağrıları.</span><span class="sxs-lookup"><span data-stu-id="59eb1-128">Having initiated the connection to the service, the client creates a new `TransactionScope` around the calls to the service operations.</span></span>  

```csharp
// Start a transaction scope  
using (TransactionScope tx =  
            new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    Console.WriteLine("Starting transaction");  
  
    // Call the Add service operation  
    //  - generatedClient will flow the required active transaction  
    double value1 = 100.00D;  
    double value2 = 15.99D;  
    double result = client.Add(value1, value2);  
    Console.WriteLine("  Add({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Subtract service operation  
    //  - generatedClient will flow the allowed active transaction  
    value1 = 145.00D;  
    value2 = 76.54D;  
    result = client.Subtract(value1, value2);  
    Console.WriteLine("  Subtract({0},{1}) = {2}", value1, value2, result);  
  
    // Start a transaction scope that suppresses the current transaction  
    using (TransactionScope txSuppress =  
                new TransactionScope(TransactionScopeOption.Suppress))  
    {  
        // Call the Subtract service operation  
        //  - the active transaction is suppressed from the generatedClient  
        //    and no transaction will flow  
        value1 = 21.05D;  
        value2 = 42.16D;  
        result = client.Subtract(value1, value2);  
        Console.WriteLine("  Subtract({0},{1}) = {2}", value1, value2, result);  
  
        // Complete the suppressed scope  
        txSuppress.Complete();  
    }  
  
    // Call the Multiply service operation  
    // - generatedClient will not flow the active transaction  
    value1 = 9.00D;  
    value2 = 81.25D;  
    result = client.Multiply(value1, value2);  
    Console.WriteLine("  Multiply({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Divide service operation.  
    // - generatedClient will not flow the active transaction  
    value1 = 22.00D;  
    value2 = 7.00D;  
    result = client.Divide(value1, value2);  
    Console.WriteLine("  Divide({0},{1}) = {2}", value1, value2, result);  
  
    // Complete the transaction scope  
    Console.WriteLine("  Completing transaction");  
    tx.Complete();  
}  
  
Console.WriteLine("Transaction committed");  
```

 <span data-ttu-id="59eb1-129">İşlem çağrıları aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="59eb1-129">The calls to the operations are as follows:</span></span>  
  
-   <span data-ttu-id="59eb1-130">`Add` Gerekli işlem hizmetine istek akışları ve hizmetin Eylemler istemcinin işlem kapsamında gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="59eb1-130">The `Add` request flows the required transaction to the service and the service's actions occur within the scope of the client's transaction.</span></span>  
  
-   <span data-ttu-id="59eb1-131">İlk `Subtract` istek, izin verilen işlem hizmetine de akar ve hizmetin Eylemler istemcinin işlem kapsamında yeniden gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="59eb1-131">The first `Subtract` request also flows the allowed transaction to the service and again the service's actions occur within the scope of the client's transaction.</span></span>  
  
-   <span data-ttu-id="59eb1-132">İkinci `Subtract` isteği ile bildirilen yeni bir işlem kapsamı içinde gerçekleştirilir `TransactionScopeOption.Suppress` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="59eb1-132">The second `Subtract` request is performed within a new transaction scope declared with the `TransactionScopeOption.Suppress` option.</span></span> <span data-ttu-id="59eb1-133">Bu istemcinin başlangıç dış işlem engeller ve isteğin bir işlem hizmetine akmaz.</span><span class="sxs-lookup"><span data-stu-id="59eb1-133">This suppresses the client's initial outer transaction and the request does not flow a transaction to the service.</span></span> <span data-ttu-id="59eb1-134">Bu yaklaşım, bir istemcinin açıkça, çevirme ve gerekli olmadığında, bir işlem hizmetine akan karşı koruma sağlar.</span><span class="sxs-lookup"><span data-stu-id="59eb1-134">This approach allows a client to explicitly opt-out of and protect against flowing a transaction to a service when that is not required.</span></span> <span data-ttu-id="59eb1-135">Hizmetin Eylemler, yeni ve bağlantısız bir işlem kapsamında gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="59eb1-135">The service's actions occur within the scope of a new and unconnected transaction.</span></span>  
  
-   <span data-ttu-id="59eb1-136">`Multiply` İsteği akan bir işlem hizmetine istemci tanımını üretilmiş çünkü `ICalculator` arabirimi içeren bir <xref:System.ServiceModel.TransactionFlowAttribute> kümesine <xref:System.ServiceModel.TransactionFlowOption> `NotAllowed`.</span><span class="sxs-lookup"><span data-stu-id="59eb1-136">The `Multiply` request does not flow a transaction to the service because the client's generated definition of the `ICalculator` interface includes a <xref:System.ServiceModel.TransactionFlowAttribute> set to <xref:System.ServiceModel.TransactionFlowOption>`NotAllowed`.</span></span>  
  
-   <span data-ttu-id="59eb1-137">`Divide` İsteği akan bir işlem hizmetine istemci tanımını yeniden üretilmiş çünkü `ICalculator` arabirimi içermez bir `TransactionFlowAttribute`.</span><span class="sxs-lookup"><span data-stu-id="59eb1-137">The `Divide` request does not flow a transaction to the service because again the client's generated definition of the `ICalculator` interface does not include a `TransactionFlowAttribute`.</span></span> <span data-ttu-id="59eb1-138">Hizmetin Eylemler, yeni ve bağlantısız başka bir işlem kapsamında yeniden gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="59eb1-138">The service's actions again occur within the scope of another new and unconnected transaction.</span></span>  
  
 <span data-ttu-id="59eb1-139">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="59eb1-139">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="59eb1-140">İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="59eb1-140">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Starting transaction  
  Add(100,15.99) = 115.99  
  Subtract(145,76.54) = 68.46  
  Subtract(21.05,42.16) = -21.11  
  Multiply(9,81.25) = 731.25  
  Divide(22,7) = 3.14285714285714  
  Completing transaction  
Transaction committed  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="59eb1-141">Hizmet işlemi isteklerini günlüğe hizmet konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="59eb1-141">The logging of the service operation requests are displayed in the service's console window.</span></span> <span data-ttu-id="59eb1-142">İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="59eb1-142">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Press <ENTER> to terminate the service.  
  Writing row to database: Adding 100 to 15.99  
  Writing row to database: Subtracting 76.54 from 145  
  Writing row to database: Subtracting 42.16 from 21.05  
  Writing row to database: Multiplying 9 by 81.25  
  Writing row to database: Dividing 22 by 7  
```  
  
 <span data-ttu-id="59eb1-143">Başarılı bir yürütme sonra istemcinin işlem kapsamı tamamlar ve bu kapsam içinde gerçekleştirilen tüm eylemler konusunda çok hassasız.</span><span class="sxs-lookup"><span data-stu-id="59eb1-143">After a successful execution, the client's transaction scope completes and all actions taken within that scope are committed.</span></span> <span data-ttu-id="59eb1-144">Özellikle, not ettiğiniz 5 kaydı hizmetin veritabanında kalır.</span><span class="sxs-lookup"><span data-stu-id="59eb1-144">Specifically, the noted 5 records are persisted in the service's database.</span></span> <span data-ttu-id="59eb1-145">Bu ilk 2 istemci işlemi kapsamında oluştu.</span><span class="sxs-lookup"><span data-stu-id="59eb1-145">The first 2 of these have occurred within the scope of the client's transaction.</span></span>  
  
 <span data-ttu-id="59eb1-146">Herhangi bir istemcinin içinde bir özel durum oluştuysa `TransactionScope` sonra işlem tamamlanamıyor.</span><span class="sxs-lookup"><span data-stu-id="59eb1-146">If an exception occurred anywhere within the client's `TransactionScope` then the transaction cannot complete.</span></span> <span data-ttu-id="59eb1-147">Bu veritabanına yürütülmesi yok o kapsam içinde kaydedilmiş kayıtları neden olur.</span><span class="sxs-lookup"><span data-stu-id="59eb1-147">This causes the records logged within that scope to not be committed to the database.</span></span> <span data-ttu-id="59eb1-148">Bu etkiyi duyurmak dış tamamlamak için yorum oluşturma sonrasında çalıştırma örneği tekrarlayarak gösterilebilir `TransactionScope`.</span><span class="sxs-lookup"><span data-stu-id="59eb1-148">This effect can be observed by repeating the sample run after commenting out the call to complete the outer `TransactionScope`.</span></span> <span data-ttu-id="59eb1-149">Böyle bir alıştırmada, yalnızca son 3 eylemleri (ikinci `Subtract`, `Multiply` ve `Divide` istekleri) istemci işlemi bu akışı değil çünkü kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="59eb1-149">On such a run, only the last 3 actions (from the second `Subtract`, the `Multiply` and the `Divide` requests) are logged because the client transaction did not flow to those.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="59eb1-150">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="59eb1-150">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="59eb1-151">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md)</span><span class="sxs-lookup"><span data-stu-id="59eb1-151">To build the C# or Visual Basic .NET version of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)</span></span>  
  
2.  <span data-ttu-id="59eb1-152">SQL Server Express Edition veya SQL Server yüklü olduğundan ve bağlantı dizesini hizmetin uygulama yapılandırma dosyasında doğru ayarlandığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="59eb1-152">Ensure that you have installed SQL Server Express Edition or SQL Server, and that the connection string has been correctly set in the service’s application configuration file.</span></span> <span data-ttu-id="59eb1-153">Bir veritabanı kullanmadan örneği çalıştırmak için ayarlanmış `usingSql` hizmetin uygulama yapılandırma dosyasına değeri `false`</span><span class="sxs-lookup"><span data-stu-id="59eb1-153">To run the sample without using a database, set the `usingSql` value in the service’s application configuration file to `false`</span></span>  
  
3.  <span data-ttu-id="59eb1-154">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="59eb1-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="59eb1-155">Çapraz makine yapılandırması için aşağıdaki yönergeleri kullanarak Dağıtılmış İşlem Düzenleyicisi'ni etkinleştir ve WCF işlemleri ağ desteğini etkinleştirmek için Windows SDK'sı WsatConfig.exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="59eb1-155">For cross-machine configuration, enable the Distributed Transaction Coordinator using the instructions below, and use the WsatConfig.exe tool from the Windows SDK to enable WCF Transactions network support.</span></span> <span data-ttu-id="59eb1-156">Bkz: [WS-Atomic işlem desteğini yapılandırma](https://go.microsoft.com/fwlink/?LinkId=190370) WsatConfig.exe hakkında bilgi.</span><span class="sxs-lookup"><span data-stu-id="59eb1-156">See [Configuring WS-Atomic Transaction Support](https://go.microsoft.com/fwlink/?LinkId=190370) for information on setting up WsatConfig.exe.</span></span>  
  
 <span data-ttu-id="59eb1-157">Örneği aynı bilgisayarda veya farklı bilgisayarlarda çalıştırmak ister, Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) ağ işlem akışını etkinleştirme ve WCF işlemleri ağ desteğini etkinleştirmek için WsatConfig.exe Aracı'nı kullanmak için yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="59eb1-157">Whether you run the sample on the same computer or on different computers, you must configure the Microsoft Distributed Transaction Coordinator (MSDTC) to enable network transaction flow and use the WsatConfig.exe tool to enable WCF transactions network support.</span></span>  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample"></a><span data-ttu-id="59eb1-158">Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) çalıştıran destekleyecek şekilde yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="59eb1-158">To configure the Microsoft Distributed Transaction Coordinator (MSDTC) to support running the sample</span></span>  
  
1.  <span data-ttu-id="59eb1-159">Windows Server 2003 veya Windows XP çalıştıran bir hizmeti makinede MSDTC gelen ağ işlemleri bu yönergeleri izleyerek izin verecek şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="59eb1-159">On a service machine running Windows Server 2003 or Windows XP, configure MSDTC to allow incoming network transactions by following these instructions.</span></span>  
  
    1.  <span data-ttu-id="59eb1-160">Gelen **Başlat** menüsünde gidin **Denetim Masası**, ardından **Yönetimsel Araçlar**, ardından **Bileşen Hizmetleri**.</span><span class="sxs-lookup"><span data-stu-id="59eb1-160">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2.  <span data-ttu-id="59eb1-161">Genişletin **Bileşen Hizmetleri**.</span><span class="sxs-lookup"><span data-stu-id="59eb1-161">Expand **Component Services**.</span></span> <span data-ttu-id="59eb1-162">Açık **bilgisayarlar** klasör.</span><span class="sxs-lookup"><span data-stu-id="59eb1-162">Open the **Computers** folder.</span></span>  
  
    3.  <span data-ttu-id="59eb1-163">Sağ **Bilgisayarım** seçip **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="59eb1-163">Right-click **My Computer** and select **Properties**.</span></span>  
  
    4.  <span data-ttu-id="59eb1-164">Üzerinde **MSDTC** sekmesinde **Güvenlik Yapılandırması**.</span><span class="sxs-lookup"><span data-stu-id="59eb1-164">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    5.  <span data-ttu-id="59eb1-165">Denetleme **ağ DTC erişimi** ve **izin gelen**.</span><span class="sxs-lookup"><span data-stu-id="59eb1-165">Check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    6.  <span data-ttu-id="59eb1-166">Tıklayın **Tamam**, ardından **Evet** MSDTC hizmetini yeniden başlatmak için.</span><span class="sxs-lookup"><span data-stu-id="59eb1-166">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    7.  <span data-ttu-id="59eb1-167">İletişim kutusunu kapatmak için **Tamam** 'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="59eb1-167">Click **OK** to close the dialog box.</span></span>  
  
2.  <span data-ttu-id="59eb1-168">Windows Server 2008 veya Windows Vista çalıştıran bir hizmeti makinede MSDTC gelen ağ işlemleri bu yönergeleri izleyerek izin verecek şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="59eb1-168">On a service machine running Windows Server 2008 or Windows Vista, configure MSDTC to allow incoming network transactions by following these instructions.</span></span>  
  
    1.  <span data-ttu-id="59eb1-169">Gelen **Başlat** menüsünde gidin **Denetim Masası**, ardından **Yönetimsel Araçlar**, ardından **Bileşen Hizmetleri**.</span><span class="sxs-lookup"><span data-stu-id="59eb1-169">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2.  <span data-ttu-id="59eb1-170">Genişletin **Bileşen Hizmetleri**.</span><span class="sxs-lookup"><span data-stu-id="59eb1-170">Expand **Component Services**.</span></span> <span data-ttu-id="59eb1-171">Açık **bilgisayarlar** klasör.</span><span class="sxs-lookup"><span data-stu-id="59eb1-171">Open the **Computers** folder.</span></span> <span data-ttu-id="59eb1-172">Seçin **Dağıtılmış İşlem Düzenleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="59eb1-172">Select **Distributed Transaction Coordinator**.</span></span>  
  
    3.  <span data-ttu-id="59eb1-173">Sağ **DTC Düzenleyicisi** seçip **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="59eb1-173">Right-click **DTC Coordinator** and select **Properties**.</span></span>  
  
    4.  <span data-ttu-id="59eb1-174">Üzerinde **güvenlik** sekmesinde, onay **ağ DTC erişimi** ve **gelene izin ver**.</span><span class="sxs-lookup"><span data-stu-id="59eb1-174">On the **Security** tab, check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    5.  <span data-ttu-id="59eb1-175">Tıklayın **Tamam**, ardından **Evet** MSDTC hizmetini yeniden başlatmak için.</span><span class="sxs-lookup"><span data-stu-id="59eb1-175">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    6.  <span data-ttu-id="59eb1-176">İletişim kutusunu kapatmak için **Tamam** 'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="59eb1-176">Click **OK** to close the dialog box.</span></span>  
  
3.  <span data-ttu-id="59eb1-177">İstemci makinesinde MSDTC giden ağ işlemleri izin verecek şekilde yapılandırın:</span><span class="sxs-lookup"><span data-stu-id="59eb1-177">On the client machine, configure MSDTC to allow outgoing network transactions:</span></span>  
  
    1.  <span data-ttu-id="59eb1-178">Gelen **Başlat** menüsünde gidin `Control Panel`, ardından **Yönetimsel Araçlar**, ardından **Bileşen Hizmetleri**.</span><span class="sxs-lookup"><span data-stu-id="59eb1-178">From the **Start** menu, navigate to `Control Panel`, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2.  <span data-ttu-id="59eb1-179">Sağ **Bilgisayarım** seçip **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="59eb1-179">Right-click **My Computer** and select **Properties**.</span></span>  
  
    3.  <span data-ttu-id="59eb1-180">Üzerinde **MSDTC** sekmesinde **Güvenlik Yapılandırması**.</span><span class="sxs-lookup"><span data-stu-id="59eb1-180">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    4.  <span data-ttu-id="59eb1-181">Denetleme **ağ DTC erişimi** ve **Gidene izin ver**.</span><span class="sxs-lookup"><span data-stu-id="59eb1-181">Check **Network DTC Access** and **Allow Outbound**.</span></span>  
  
    5.  <span data-ttu-id="59eb1-182">Tıklayın **Tamam**, ardından **Evet** MSDTC hizmetini yeniden başlatmak için.</span><span class="sxs-lookup"><span data-stu-id="59eb1-182">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    6.  <span data-ttu-id="59eb1-183">İletişim kutusunu kapatmak için **Tamam** 'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="59eb1-183">Click **OK** to close the dialog box.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="59eb1-184">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="59eb1-184">The samples may already be installed on your machine.</span></span> <span data-ttu-id="59eb1-185">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="59eb1-185">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="59eb1-186">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="59eb1-186">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="59eb1-187">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="59eb1-187">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\TransactionFlow`
