---
title: WS İşlem Akışı
ms.date: 03/30/2017
helpviewer_keywords:
- Transactions
ms.assetid: f8eecbcf-990a-4dbb-b29b-c3f9e3b396bd
ms.openlocfilehash: e6fd84d9cc1f7df397e26e41c55f51d45406228d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942161"
---
# <a name="ws-transaction-flow"></a><span data-ttu-id="a187e-102">WS İşlem Akışı</span><span class="sxs-lookup"><span data-stu-id="a187e-102">WS Transaction Flow</span></span>
<span data-ttu-id="a187e-103">Bu örnek, WS-Atomik Işlem veya OleTransactions protokolünü kullanarak, istemci ile eşgüdümlü bir işlemin ve işlem akışı için istemci ve sunucu seçeneklerinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a187e-103">This sample demonstrates the use of a client-coordinated transaction and the client and server options for transaction flow using either the WS-Atomic Transaction or OleTransactions protocol.</span></span> <span data-ttu-id="a187e-104">Bu örnek, bir Hesaplayıcı hizmeti uygulayan [kullanmaya](../../../../docs/framework/wcf/samples/getting-started-sample.md) Başlarken hizmetini temel alır, ancak bu işlemler, `TransactionFlowAttribute` ne ölçüde olduğunu belirlemek için **TransactionFlowOption** numaralandırması ile birlikte kullanımını gösterir. işlem akışı etkin.</span><span class="sxs-lookup"><span data-stu-id="a187e-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service but the operations are attributed to demonstrate the use of the `TransactionFlowAttribute` with the **TransactionFlowOption** enumeration to determine to what degree transaction flow is enabled.</span></span> <span data-ttu-id="a187e-105">Akışlı işlemin kapsamı içinde, istenen işlemlerin bir günlüğü veritabanına yazılır ve istemci ile Eşgüdümlü işlem tamamlanana kadar devam etmez-istemci işlemi tamamlanmazsa, Web hizmeti işlemi veritabanına yönelik uygun güncelleştirmeler yürütülmedi.</span><span class="sxs-lookup"><span data-stu-id="a187e-105">Within the scope of the flowed transaction, a log of the requested operations is written to a database and persists until the client coordinated transaction has completed - if the client transaction does not complete, the Web service transaction ensures that the appropriate updates to the database are not committed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a187e-106">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="a187e-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="a187e-107">Hizmet ve bir işlem bağlantısı başlattıktan sonra istemci çeşitli hizmet işlemlerine erişir.</span><span class="sxs-lookup"><span data-stu-id="a187e-107">After initiating a connection to the service and a transaction, the client accesses several service operations.</span></span> <span data-ttu-id="a187e-108">Hizmet sözleşmesi, `TransactionFlowOption`için farklı bir ayar gösteren işlemlerden her biriyle aşağıdaki gibi tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="a187e-108">The contract for the service is defined as follows with each of the operations demonstrating a different setting for the `TransactionFlowOption`.</span></span>  

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

 <span data-ttu-id="a187e-109">Bu işlem, işlemleri işlenecek sırada tanımlar:</span><span class="sxs-lookup"><span data-stu-id="a187e-109">This defines the operations in the order they are to be processed:</span></span>  
  
- <span data-ttu-id="a187e-110">`Add` İşlem isteği bir akışlı işlem içermelidir.</span><span class="sxs-lookup"><span data-stu-id="a187e-110">An `Add` operation request must include a flowed transaction.</span></span>  
  
- <span data-ttu-id="a187e-111">`Subtract` İşlem isteği, bir akışlı işlem içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a187e-111">A `Subtract` operation request may include a flowed transaction.</span></span>  
  
- <span data-ttu-id="a187e-112">`Multiply` İşlem isteği açık NotAllowed ayarı aracılığıyla bir akışlı işlem içermemelidir.</span><span class="sxs-lookup"><span data-stu-id="a187e-112">A `Multiply` operation request must not include a flowed transaction through the explicit NotAllowed setting.</span></span>  
  
- <span data-ttu-id="a187e-113">İşlem isteği bir `TransactionFlow` özniteliği atlama yoluyla bir akışlı işlem içermemelidir. `Divide`</span><span class="sxs-lookup"><span data-stu-id="a187e-113">A `Divide` operation request must not include a flowed transaction through the omission of a `TransactionFlow` attribute.</span></span>  
  
 <span data-ttu-id="a187e-114">İşlem akışını etkinleştirmek için, [ \<TransactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) özelliği etkinleştirilmiş bağlamaların uygun işlem özniteliklerine ek olarak kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a187e-114">To enable transaction flow, bindings with the [\<transactionFlow>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) property enabled must be used in addition to the appropriate operation attributes.</span></span> <span data-ttu-id="a187e-115">Bu örnekte, hizmetin yapılandırması bir TCP uç noktası ve bir meta veri değişimi uç noktasına ek olarak bir HTTP uç noktası sunar.</span><span class="sxs-lookup"><span data-stu-id="a187e-115">In this sample, the service's configuration exposes a TCP endpoint and an HTTP endpoint in addition to a Metadata Exchange endpoint.</span></span> <span data-ttu-id="a187e-116">TCP uç noktası ve HTTP uç noktası, her ikisi de [ \<TransactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) özelliği etkinleştirilmiş olan aşağıdaki bağlamaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="a187e-116">The TCP endpoint and the HTTP endpoint use the following bindings, both of which have the [\<transactionFlow>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) property enabled.</span></span>  
  
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
> <span data-ttu-id="a187e-117">Sistem tarafından sunulan netTcpBinding, transactionProtocol belirtimine izin verir, ancak sistem tarafından sunulan wsHttpBinding yalnızca daha fazla çalışabilen WSAtomicTransactionOctober2004 protokolünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="a187e-117">The system-provided netTcpBinding allows specification of the transactionProtocol whereas the system-provided wsHttpBinding uses only the more interoperable WSAtomicTransactionOctober2004 protocol.</span></span> <span data-ttu-id="a187e-118">OleTransactions protokolü yalnızca Windows Communication Foundation (WCF) istemcileri tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a187e-118">The OleTransactions protocol is only available for use by Windows Communication Foundation (WCF) clients.</span></span>  
  
 <span data-ttu-id="a187e-119">`ICalculator` Arabirimini uygulayan sınıf için tüm yöntemler, <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> özelliği olarak ayarlanmış şekilde `true`atanır.</span><span class="sxs-lookup"><span data-stu-id="a187e-119">For the class that implements the `ICalculator` interface, all of the methods are attributed with <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property set to `true`.</span></span> <span data-ttu-id="a187e-120">Bu ayar, yöntem içinde gerçekleştirilen tüm eylemlerin bir işlemin kapsamı içinde gerçekleştiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="a187e-120">This setting declares that all actions taken within the method occur within the scope of a transaction.</span></span> <span data-ttu-id="a187e-121">Bu durumda, gerçekleştirilen eylemler günlük veritabanına kayıt içerir.</span><span class="sxs-lookup"><span data-stu-id="a187e-121">In this case, the actions taken include recording to the log database.</span></span> <span data-ttu-id="a187e-122">İşlem isteği bir akışlı işlem içeriyorsa, eylemler gelen işlemin kapsamı içinde veya yeni bir işlem kapsamı otomatik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a187e-122">If the operation request includes a flowed transaction then the actions occur within the scope of the incoming transaction or a new transaction scope is automatically generated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a187e-123">Özelliği <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> , yerel davranışı hizmet yöntemi uygulamalarına göre tanımlar ve istemcinin bir işlemi akışa alma gereksinimini tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="a187e-123">The <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property defines behavior local to the service method implementations and does not define the client's ability to or requirement for flowing a transaction.</span></span>  

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

 <span data-ttu-id="a187e-124">İstemcide, işlemler üzerindeki hizmetin `TransactionFlowOption` ayarları, istemcinin oluşturulan tanımına `ICalculator` yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="a187e-124">On the client, the service's `TransactionFlowOption` settings on the operations are reflected in the client's generated definition of the `ICalculator` interface.</span></span> <span data-ttu-id="a187e-125">Ayrıca, hizmetin `transactionFlow` özellik ayarları istemcinin uygulama yapılandırmasına yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="a187e-125">Also, the service's `transactionFlow` property settings are reflected in the client's application configuration.</span></span> <span data-ttu-id="a187e-126">İstemci, uygun olanını `endpointConfigurationName`seçerek taşıma ve Protokolü seçebilir.</span><span class="sxs-lookup"><span data-stu-id="a187e-126">The client can select the transport and protocol by selecting the appropriate `endpointConfigurationName`.</span></span>  

```csharp
// Create a client using either wsat or oletx endpoint configurations  
CalculatorClient client = new CalculatorClient("WSAtomicTransaction_endpoint");  
// CalculatorClient client = new CalculatorClient("OleTransactions_endpoint");  
```

> [!NOTE]
> <span data-ttu-id="a187e-127">Bu örneğin gözlemlenen davranışı, hangi protokol veya taşımanın seçildiğine bakılmaksızın aynıdır.</span><span class="sxs-lookup"><span data-stu-id="a187e-127">The observed behavior of this sample is the same no matter which protocol or transport is chosen.</span></span>  
  
 <span data-ttu-id="a187e-128">Hizmet bağlantısını başlatmaktan, istemci, hizmet işlemlerine yapılan çağrılar etrafında yeni `TransactionScope` bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a187e-128">Having initiated the connection to the service, the client creates a new `TransactionScope` around the calls to the service operations.</span></span>  

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

 <span data-ttu-id="a187e-129">İşlemlere yapılan çağrılar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="a187e-129">The calls to the operations are as follows:</span></span>  
  
- <span data-ttu-id="a187e-130">`Add` İstek, gerekli işlemin hizmete akar ve hizmetin eylemleri istemci işleminin kapsamında oluşur.</span><span class="sxs-lookup"><span data-stu-id="a187e-130">The `Add` request flows the required transaction to the service and the service's actions occur within the scope of the client's transaction.</span></span>  
  
- <span data-ttu-id="a187e-131">İlk `Subtract` istek aynı zamanda izin verilen işlemi hizmete akar ve hizmetin eylemleri istemci işleminin kapsamı içinde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="a187e-131">The first `Subtract` request also flows the allowed transaction to the service and again the service's actions occur within the scope of the client's transaction.</span></span>  
  
- <span data-ttu-id="a187e-132">İkinci `Subtract` istek, `TransactionScopeOption.Suppress` seçeneğiyle belirtilen yeni bir işlem kapsamı içinde gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="a187e-132">The second `Subtract` request is performed within a new transaction scope declared with the `TransactionScopeOption.Suppress` option.</span></span> <span data-ttu-id="a187e-133">Bu, istemcinin ilk dış işlemini bastırır ve istek, hizmete bir işlem akışı yapmaz.</span><span class="sxs-lookup"><span data-stu-id="a187e-133">This suppresses the client's initial outer transaction and the request does not flow a transaction to the service.</span></span> <span data-ttu-id="a187e-134">Bu yaklaşım, bir istemcinin, gerekli olmadığında bir hizmetin bir işlemin akışını açıkça geri almasına ve korumasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="a187e-134">This approach allows a client to explicitly opt-out of and protect against flowing a transaction to a service when that is not required.</span></span> <span data-ttu-id="a187e-135">Hizmetin eylemleri, yeni ve bağlı olmayan bir işlemin kapsamı içinde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="a187e-135">The service's actions occur within the scope of a new and unconnected transaction.</span></span>  
  
- <span data-ttu-id="a187e-136">`ICalculator` İstemcitarafından<xref:System.ServiceModel.TransactionFlowAttribute> oluşturulan `Multiply` arabirimintanımlıbirkümesiiçerdiğindenistek,hizmetebir<xref:System.ServiceModel.TransactionFlowOption>işlem akışı yapmaz `NotAllowed`.</span><span class="sxs-lookup"><span data-stu-id="a187e-136">The `Multiply` request does not flow a transaction to the service because the client's generated definition of the `ICalculator` interface includes a <xref:System.ServiceModel.TransactionFlowAttribute> set to <xref:System.ServiceModel.TransactionFlowOption>`NotAllowed`.</span></span>  
  
- <span data-ttu-id="a187e-137">`TransactionFlowAttribute`İstemci, `ICalculator` arabirimin oluşturulan tanımının bir öğesini içermediğinden, istekhizmetebir`Divide` işlem akışı yapmaz.</span><span class="sxs-lookup"><span data-stu-id="a187e-137">The `Divide` request does not flow a transaction to the service because again the client's generated definition of the `ICalculator` interface does not include a `TransactionFlowAttribute`.</span></span> <span data-ttu-id="a187e-138">Hizmetin eylemleri, başka bir yeni ve bağlı olmayan işlemin kapsamı içinde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="a187e-138">The service's actions again occur within the scope of another new and unconnected transaction.</span></span>  
  
 <span data-ttu-id="a187e-139">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a187e-139">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="a187e-140">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="a187e-140">Press ENTER in the client window to shut down the client.</span></span>  
  
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
  
 <span data-ttu-id="a187e-141">Hizmet işlemi isteklerinin günlüğe kaydedilmesi, hizmetin konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a187e-141">The logging of the service operation requests are displayed in the service's console window.</span></span> <span data-ttu-id="a187e-142">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="a187e-142">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Press <ENTER> to terminate the service.  
  Writing row to database: Adding 100 to 15.99  
  Writing row to database: Subtracting 76.54 from 145  
  Writing row to database: Subtracting 42.16 from 21.05  
  Writing row to database: Multiplying 9 by 81.25  
  Writing row to database: Dividing 22 by 7  
```  
  
 <span data-ttu-id="a187e-143">Başarılı bir yürütme sonrasında, istemcinin işlem kapsamı tamamlanır ve bu kapsam içinde gerçekleştirilen tüm eylemler işlenir.</span><span class="sxs-lookup"><span data-stu-id="a187e-143">After a successful execution, the client's transaction scope completes and all actions taken within that scope are committed.</span></span> <span data-ttu-id="a187e-144">Özellikle, belirtilen 5 kayıt hizmetin veritabanında kalıcı hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="a187e-144">Specifically, the noted 5 records are persisted in the service's database.</span></span> <span data-ttu-id="a187e-145">Bunların ilk 2 ' nin, istemci işleminin kapsamı içinde meydana geldi.</span><span class="sxs-lookup"><span data-stu-id="a187e-145">The first 2 of these have occurred within the scope of the client's transaction.</span></span>  
  
 <span data-ttu-id="a187e-146">İstemci `TransactionScope` içinde herhangi bir yerde bir özel durum oluştuysa işlem tamamlanamaz.</span><span class="sxs-lookup"><span data-stu-id="a187e-146">If an exception occurred anywhere within the client's `TransactionScope` then the transaction cannot complete.</span></span> <span data-ttu-id="a187e-147">Bu, bu kapsam içinde günlüğe kaydedilen kayıtların veritabanına uygulanmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a187e-147">This causes the records logged within that scope to not be committed to the database.</span></span> <span data-ttu-id="a187e-148">Bu efekt, dış `TransactionScope`çalışmayı tamamlamaya yönelik çağrının yorum yapıldıktan sonra örnek çalıştırmayı tekrarlayarak gözlemlenebilir.</span><span class="sxs-lookup"><span data-stu-id="a187e-148">This effect can be observed by repeating the sample run after commenting out the call to complete the outer `TransactionScope`.</span></span> <span data-ttu-id="a187e-149">Bu tür bir çalıştırmada, istemci işlemi bu işlemlere akmadığı için yalnızca son `Subtract`3 Eylem `Multiply` (ikinciden, ve `Divide` istekler) günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="a187e-149">On such a run, only the last 3 actions (from the second `Subtract`, the `Multiply` and the `Divide` requests) are logged because the client transaction did not flow to those.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a187e-150">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="a187e-150">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a187e-151">Çözümün C# veya Visual Basic .NET sürümünü derlemek Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md) konusundaki yönergeleri izleyin</span><span class="sxs-lookup"><span data-stu-id="a187e-151">To build the C# or Visual Basic .NET version of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)</span></span>  
  
2. <span data-ttu-id="a187e-152">SQL Server Express Edition veya SQL Server yüklediğinizden ve bağlantı dizesinin hizmetin uygulama yapılandırma dosyasında doğru şekilde ayarlandığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="a187e-152">Ensure that you have installed SQL Server Express Edition or SQL Server, and that the connection string has been correctly set in the service’s application configuration file.</span></span> <span data-ttu-id="a187e-153">Örneği bir veritabanı kullanmadan çalıştırmak için, hizmetin uygulama yapılandırma dosyasındaki `usingSql` değeri olarak ayarlayın.`false`</span><span class="sxs-lookup"><span data-stu-id="a187e-153">To run the sample without using a database, set the `usingSql` value in the service’s application configuration file to `false`</span></span>  
  
3. <span data-ttu-id="a187e-154">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="a187e-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a187e-155">Platformlar arası yapılandırma için aşağıdaki yönergeleri kullanarak Dağıtılmış İşlem Düzenleyicisi etkinleştirin ve Windows SDK WCF Işlemleri ağ desteğini etkinleştirmek için WsatConfig. exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="a187e-155">For cross-machine configuration, enable the Distributed Transaction Coordinator using the instructions below, and use the WsatConfig.exe tool from the Windows SDK to enable WCF Transactions network support.</span></span> <span data-ttu-id="a187e-156">WsatConfig. exe ' yi ayarlama hakkında bilgi için bkz. [WS Atomik Işlem desteğini yapılandırma](https://go.microsoft.com/fwlink/?LinkId=190370) .</span><span class="sxs-lookup"><span data-stu-id="a187e-156">See [Configuring WS-Atomic Transaction Support](https://go.microsoft.com/fwlink/?LinkId=190370) for information on setting up WsatConfig.exe.</span></span>  
  
 <span data-ttu-id="a187e-157">Örneği aynı bilgisayarda veya farklı bilgisayarlarda çalıştırdığınız gibi, ağ işlem akışını etkinleştirmek için Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) yapılandırmanız ve WCF işlemleri ağ desteğini etkinleştirmek için WsatConfig. exe aracını kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a187e-157">Whether you run the sample on the same computer or on different computers, you must configure the Microsoft Distributed Transaction Coordinator (MSDTC) to enable network transaction flow and use the WsatConfig.exe tool to enable WCF transactions network support.</span></span>  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample"></a><span data-ttu-id="a187e-158">Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) örneğini çalıştırmayı destekleyecek şekilde yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="a187e-158">To configure the Microsoft Distributed Transaction Coordinator (MSDTC) to support running the sample</span></span>  
  
1. <span data-ttu-id="a187e-159">Windows Server 2003 veya Windows XP çalıştıran bir hizmet makinesinde, bu yönergeleri izleyerek MSDTC 'yi gelen ağ işlemlerine izin verecek şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="a187e-159">On a service machine running Windows Server 2003 or Windows XP, configure MSDTC to allow incoming network transactions by following these instructions.</span></span>  
  
    1. <span data-ttu-id="a187e-160">**Başlat** menüsünde, **Denetim Masası**' na, ardından **Yönetimsel Araçlar**' a ve ardından **Bileşen Hizmetleri**' ne gidin.</span><span class="sxs-lookup"><span data-stu-id="a187e-160">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2. <span data-ttu-id="a187e-161">**Bileşen Hizmetleri**' ni genişletin.</span><span class="sxs-lookup"><span data-stu-id="a187e-161">Expand **Component Services**.</span></span> <span data-ttu-id="a187e-162">**Bilgisayarlar** klasörünü açın.</span><span class="sxs-lookup"><span data-stu-id="a187e-162">Open the **Computers** folder.</span></span>  
  
    3. <span data-ttu-id="a187e-163">Bilgisayarım ' a sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="a187e-163">Right-click **My Computer** and select **Properties**.</span></span>  
  
    4. <span data-ttu-id="a187e-164">**MSDTC** sekmesinde **Güvenlik Yapılandırması**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a187e-164">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    5. <span data-ttu-id="a187e-165">**Ağ DTC erişimini** denetleyin ve **gelen erişime izin verin**.</span><span class="sxs-lookup"><span data-stu-id="a187e-165">Check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    6. <span data-ttu-id="a187e-166">**Tamam**' a tıklayın ve ardından **Evet** ' e tıklayarak MSDTC hizmetini yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="a187e-166">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    7. <span data-ttu-id="a187e-167">İletişim kutusunu kapatmak için **Tamam** 'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="a187e-167">Click **OK** to close the dialog box.</span></span>  
  
2. <span data-ttu-id="a187e-168">Windows Server 2008 veya Windows Vista çalıştıran bir hizmet makinesinde, bu yönergeleri izleyerek MSDTC 'yi gelen ağ işlemlerine izin verecek şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="a187e-168">On a service machine running Windows Server 2008 or Windows Vista, configure MSDTC to allow incoming network transactions by following these instructions.</span></span>  
  
    1. <span data-ttu-id="a187e-169">**Başlat** menüsünde, **Denetim Masası**' na, ardından **Yönetimsel Araçlar**' a ve ardından **Bileşen Hizmetleri**' ne gidin.</span><span class="sxs-lookup"><span data-stu-id="a187e-169">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2. <span data-ttu-id="a187e-170">**Bileşen Hizmetleri**' ni genişletin.</span><span class="sxs-lookup"><span data-stu-id="a187e-170">Expand **Component Services**.</span></span> <span data-ttu-id="a187e-171">**Bilgisayarlar** klasörünü açın.</span><span class="sxs-lookup"><span data-stu-id="a187e-171">Open the **Computers** folder.</span></span> <span data-ttu-id="a187e-172">**Dağıtılmış işlem Düzenleyicisi**seçin.</span><span class="sxs-lookup"><span data-stu-id="a187e-172">Select **Distributed Transaction Coordinator**.</span></span>  
  
    3. <span data-ttu-id="a187e-173">**DTC Düzenleyicisi** ' ne sağ tıklayıp **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="a187e-173">Right-click **DTC Coordinator** and select **Properties**.</span></span>  
  
    4. <span data-ttu-id="a187e-174">**Güvenlik** sekmesinde, **Ağ DTC erişimi** ' ni ve **gelen izin ver**' i işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="a187e-174">On the **Security** tab, check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    5. <span data-ttu-id="a187e-175">**Tamam**' a tıklayın ve ardından **Evet** ' e tıklayarak MSDTC hizmetini yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="a187e-175">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    6. <span data-ttu-id="a187e-176">İletişim kutusunu kapatmak için **Tamam** 'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="a187e-176">Click **OK** to close the dialog box.</span></span>  
  
3. <span data-ttu-id="a187e-177">İstemci makinesinde, giden ağ işlemlerine izin vermek için MSDTC 'yi yapılandırın:</span><span class="sxs-lookup"><span data-stu-id="a187e-177">On the client machine, configure MSDTC to allow outgoing network transactions:</span></span>  
  
    1. <span data-ttu-id="a187e-178">**Başlat** menüsünde `Control Panel`, **Yönetim Araçları**' na ve ardından **Bileşen Hizmetleri**' ne gidin.</span><span class="sxs-lookup"><span data-stu-id="a187e-178">From the **Start** menu, navigate to `Control Panel`, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2. <span data-ttu-id="a187e-179">Bilgisayarım ' a sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="a187e-179">Right-click **My Computer** and select **Properties**.</span></span>  
  
    3. <span data-ttu-id="a187e-180">**MSDTC** sekmesinde **Güvenlik Yapılandırması**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a187e-180">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    4. <span data-ttu-id="a187e-181">**Ağ DTC erişimini** denetleyin ve **giden erişime izin verin**.</span><span class="sxs-lookup"><span data-stu-id="a187e-181">Check **Network DTC Access** and **Allow Outbound**.</span></span>  
  
    5. <span data-ttu-id="a187e-182">**Tamam**' a tıklayın ve ardından **Evet** ' e tıklayarak MSDTC hizmetini yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="a187e-182">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    6. <span data-ttu-id="a187e-183">İletişim kutusunu kapatmak için **Tamam** 'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="a187e-183">Click **OK** to close the dialog box.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a187e-184">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="a187e-184">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a187e-185">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a187e-185">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a187e-186">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="a187e-186">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a187e-187">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="a187e-187">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\TransactionFlow`
