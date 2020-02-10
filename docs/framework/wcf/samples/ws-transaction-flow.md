---
title: WS İşlem Akışı
ms.date: 03/30/2017
helpviewer_keywords:
- Transactions
ms.assetid: f8eecbcf-990a-4dbb-b29b-c3f9e3b396bd
ms.openlocfilehash: 781934e9ab27f761e71841c2edc509f9b8022aa7
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094754"
---
# <a name="ws-transaction-flow"></a><span data-ttu-id="95526-102">WS İşlem Akışı</span><span class="sxs-lookup"><span data-stu-id="95526-102">WS Transaction Flow</span></span>
<span data-ttu-id="95526-103">Bu örnek, WS-Atomik Işlem veya OleTransactions protokolünü kullanarak, istemci ile eşgüdümlü bir işlemin ve işlem akışı için istemci ve sunucu seçeneklerinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="95526-103">This sample demonstrates the use of a client-coordinated transaction and the client and server options for transaction flow using either the WS-Atomic Transaction or OleTransactions protocol.</span></span> <span data-ttu-id="95526-104">Bu örnek, bir Hesaplayıcı hizmeti uygulayan [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hizmetini temel alır ancak işlemler, işlem akışının ne derece etkin olduğunu belirlemek için **TransactionFlowOption** numaralandırmasıyla `TransactionFlowAttribute` kullanımını göstermeye yönelik olarak belirlenir.</span><span class="sxs-lookup"><span data-stu-id="95526-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service but the operations are attributed to demonstrate the use of the `TransactionFlowAttribute` with the **TransactionFlowOption** enumeration to determine to what degree transaction flow is enabled.</span></span> <span data-ttu-id="95526-105">Akışlı işlemin kapsamı içinde, istenen işlemlerin bir günlüğü veritabanına yazılır ve istemci ile Eşgüdümlü işlem tamamlanana kadar devam etmez-istemci işlemi tamamlanmazsa, Web hizmeti işlemi veritabanına yönelik uygun güncelleştirmeler yürütülmedi.</span><span class="sxs-lookup"><span data-stu-id="95526-105">Within the scope of the flowed transaction, a log of the requested operations is written to a database and persists until the client coordinated transaction has completed - if the client transaction does not complete, the Web service transaction ensures that the appropriate updates to the database are not committed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="95526-106">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="95526-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="95526-107">Hizmet ve bir işlem bağlantısı başlattıktan sonra istemci çeşitli hizmet işlemlerine erişir.</span><span class="sxs-lookup"><span data-stu-id="95526-107">After initiating a connection to the service and a transaction, the client accesses several service operations.</span></span> <span data-ttu-id="95526-108">Hizmet sözleşmesi, `TransactionFlowOption`farklı bir ayar gösteren işlemlerden her biriyle aşağıdaki gibi tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="95526-108">The contract for the service is defined as follows with each of the operations demonstrating a different setting for the `TransactionFlowOption`.</span></span>  

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

 <span data-ttu-id="95526-109">Bu işlem, işlemleri işlenecek sırada tanımlar:</span><span class="sxs-lookup"><span data-stu-id="95526-109">This defines the operations in the order they are to be processed:</span></span>  
  
- <span data-ttu-id="95526-110">`Add` işlem isteği bir akışlı işlem içermelidir.</span><span class="sxs-lookup"><span data-stu-id="95526-110">An `Add` operation request must include a flowed transaction.</span></span>  
  
- <span data-ttu-id="95526-111">Bir `Subtract` işlem isteği, bir akışlı işlem içerebilir.</span><span class="sxs-lookup"><span data-stu-id="95526-111">A `Subtract` operation request may include a flowed transaction.</span></span>  
  
- <span data-ttu-id="95526-112">`Multiply` işlem isteği açık NotAllowed ayarı aracılığıyla bir akışlı işlem içermemelidir.</span><span class="sxs-lookup"><span data-stu-id="95526-112">A `Multiply` operation request must not include a flowed transaction through the explicit NotAllowed setting.</span></span>  
  
- <span data-ttu-id="95526-113">Bir `Divide` işlem isteği, bir `TransactionFlow` özniteliği atlanmaz bir akışlı işlem içermemelidir.</span><span class="sxs-lookup"><span data-stu-id="95526-113">A `Divide` operation request must not include a flowed transaction through the omission of a `TransactionFlow` attribute.</span></span>  
  
 <span data-ttu-id="95526-114">İşlem akışını etkinleştirmek için, [\<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) özelliği etkinleştirilmiş bağlamaların uygun işlem özniteliklerine ek olarak kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="95526-114">To enable transaction flow, bindings with the [\<transactionFlow>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) property enabled must be used in addition to the appropriate operation attributes.</span></span> <span data-ttu-id="95526-115">Bu örnekte, hizmetin yapılandırması bir TCP uç noktası ve bir meta veri değişimi uç noktasına ek olarak bir HTTP uç noktası sunar.</span><span class="sxs-lookup"><span data-stu-id="95526-115">In this sample, the service's configuration exposes a TCP endpoint and an HTTP endpoint in addition to a Metadata Exchange endpoint.</span></span> <span data-ttu-id="95526-116">TCP uç noktası ve HTTP uç noktası, her ikisi de [\<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) özelliği etkin olan aşağıdaki bağlamaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="95526-116">The TCP endpoint and the HTTP endpoint use the following bindings, both of which have the [\<transactionFlow>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) property enabled.</span></span>  
  
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
> <span data-ttu-id="95526-117">Sistem tarafından sunulan netTcpBinding, transactionProtocol belirtimine izin verir, ancak sistem tarafından sunulan wsHttpBinding yalnızca daha fazla çalışabilen WSAtomicTransactionOctober2004 protokolünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="95526-117">The system-provided netTcpBinding allows specification of the transactionProtocol whereas the system-provided wsHttpBinding uses only the more interoperable WSAtomicTransactionOctober2004 protocol.</span></span> <span data-ttu-id="95526-118">OleTransactions protokolü yalnızca Windows Communication Foundation (WCF) istemcileri tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="95526-118">The OleTransactions protocol is only available for use by Windows Communication Foundation (WCF) clients.</span></span>  
  
 <span data-ttu-id="95526-119">`ICalculator` arabirimini uygulayan sınıf için tüm yöntemler, `true`olarak ayarlanan <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> özelliği ile ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="95526-119">For the class that implements the `ICalculator` interface, all of the methods are attributed with <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property set to `true`.</span></span> <span data-ttu-id="95526-120">Bu ayar, yöntem içinde gerçekleştirilen tüm eylemlerin bir işlemin kapsamı içinde gerçekleştiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="95526-120">This setting declares that all actions taken within the method occur within the scope of a transaction.</span></span> <span data-ttu-id="95526-121">Bu durumda, gerçekleştirilen eylemler günlük veritabanına kayıt içerir.</span><span class="sxs-lookup"><span data-stu-id="95526-121">In this case, the actions taken include recording to the log database.</span></span> <span data-ttu-id="95526-122">İşlem isteği bir akışlı işlem içeriyorsa, eylemler gelen işlemin kapsamı içinde veya yeni bir işlem kapsamı otomatik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="95526-122">If the operation request includes a flowed transaction then the actions occur within the scope of the incoming transaction or a new transaction scope is automatically generated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="95526-123"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> özelliği, yerel davranışı hizmet yöntemi uygulamalarına göre tanımlar ve istemcinin bir işlemi akışa alma gereksinimini tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="95526-123">The <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property defines behavior local to the service method implementations and does not define the client's ability to or requirement for flowing a transaction.</span></span>  

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

 <span data-ttu-id="95526-124">İstemcisinde, hizmetin işlemler üzerindeki `TransactionFlowOption` ayarları, istemcinin `ICalculator` arabiriminin oluşturulan tanımına yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="95526-124">On the client, the service's `TransactionFlowOption` settings on the operations are reflected in the client's generated definition of the `ICalculator` interface.</span></span> <span data-ttu-id="95526-125">Ayrıca, hizmetin `transactionFlow` özellik ayarları istemcinin uygulama yapılandırmasına yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="95526-125">Also, the service's `transactionFlow` property settings are reflected in the client's application configuration.</span></span> <span data-ttu-id="95526-126">İstemci, uygun `endpointConfigurationName`seçerek taşıma ve Protokolü seçebilir.</span><span class="sxs-lookup"><span data-stu-id="95526-126">The client can select the transport and protocol by selecting the appropriate `endpointConfigurationName`.</span></span>  

```csharp
// Create a client using either wsat or oletx endpoint configurations  
CalculatorClient client = new CalculatorClient("WSAtomicTransaction_endpoint");  
// CalculatorClient client = new CalculatorClient("OleTransactions_endpoint");  
```

> [!NOTE]
> <span data-ttu-id="95526-127">Bu örneğin gözlemlenen davranışı, hangi protokol veya taşımanın seçildiğine bakılmaksızın aynıdır.</span><span class="sxs-lookup"><span data-stu-id="95526-127">The observed behavior of this sample is the same no matter which protocol or transport is chosen.</span></span>  
  
 <span data-ttu-id="95526-128">Hizmet bağlantısını başlatmaktan, istemci, hizmet işlemlerine yapılan çağrılar etrafında yeni bir `TransactionScope` oluşturur.</span><span class="sxs-lookup"><span data-stu-id="95526-128">Having initiated the connection to the service, the client creates a new `TransactionScope` around the calls to the service operations.</span></span>  

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

 <span data-ttu-id="95526-129">İşlemlere yapılan çağrılar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="95526-129">The calls to the operations are as follows:</span></span>  
  
- <span data-ttu-id="95526-130">`Add` isteği, gerekli işlemi hizmete akar ve hizmetin eylemleri, istemci işleminin kapsamı içinde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="95526-130">The `Add` request flows the required transaction to the service and the service's actions occur within the scope of the client's transaction.</span></span>  
  
- <span data-ttu-id="95526-131">İlk `Subtract` isteği Ayrıca izin verilen işlemi hizmete akar ve hizmetin eylemleri istemci işleminin kapsamında oluşur.</span><span class="sxs-lookup"><span data-stu-id="95526-131">The first `Subtract` request also flows the allowed transaction to the service and again the service's actions occur within the scope of the client's transaction.</span></span>  
  
- <span data-ttu-id="95526-132">İkinci `Subtract` isteği, `TransactionScopeOption.Suppress` seçeneğiyle belirtilen yeni bir işlem kapsamı içinde gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="95526-132">The second `Subtract` request is performed within a new transaction scope declared with the `TransactionScopeOption.Suppress` option.</span></span> <span data-ttu-id="95526-133">Bu, istemcinin ilk dış işlemini bastırır ve istek, hizmete bir işlem akışı yapmaz.</span><span class="sxs-lookup"><span data-stu-id="95526-133">This suppresses the client's initial outer transaction and the request does not flow a transaction to the service.</span></span> <span data-ttu-id="95526-134">Bu yaklaşım, bir istemcinin, gerekli olmadığında bir hizmetin bir işlemin akışını açıkça geri almasına ve korumasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="95526-134">This approach allows a client to explicitly opt-out of and protect against flowing a transaction to a service when that is not required.</span></span> <span data-ttu-id="95526-135">Hizmetin eylemleri, yeni ve bağlı olmayan bir işlemin kapsamı içinde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="95526-135">The service's actions occur within the scope of a new and unconnected transaction.</span></span>  
  
- <span data-ttu-id="95526-136">`Multiply` isteği, istemcinin `ICalculator` arabiriminin oluşturulan tanımı <xref:System.ServiceModel.TransactionFlowOption>`NotAllowed`olarak ayarlanmış bir <xref:System.ServiceModel.TransactionFlowAttribute> içerdiğinden hizmete bir işlem Flow.</span><span class="sxs-lookup"><span data-stu-id="95526-136">The `Multiply` request does not flow a transaction to the service because the client's generated definition of the `ICalculator` interface includes a <xref:System.ServiceModel.TransactionFlowAttribute> set to <xref:System.ServiceModel.TransactionFlowOption>`NotAllowed`.</span></span>  
  
- <span data-ttu-id="95526-137">`Divide` isteği, istemcinin `ICalculator` arabiriminin oluşturulan tanımı bir `TransactionFlowAttribute`içermediği için bir işlemi hizmete Flow.</span><span class="sxs-lookup"><span data-stu-id="95526-137">The `Divide` request does not flow a transaction to the service because again the client's generated definition of the `ICalculator` interface does not include a `TransactionFlowAttribute`.</span></span> <span data-ttu-id="95526-138">Hizmetin eylemleri, başka bir yeni ve bağlı olmayan işlemin kapsamı içinde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="95526-138">The service's actions again occur within the scope of another new and unconnected transaction.</span></span>  
  
 <span data-ttu-id="95526-139">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="95526-139">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="95526-140">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="95526-140">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
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
  
 <span data-ttu-id="95526-141">Hizmet işlemi isteklerinin günlüğe kaydedilmesi, hizmetin konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="95526-141">The logging of the service operation requests are displayed in the service's console window.</span></span> <span data-ttu-id="95526-142">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="95526-142">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Press <ENTER> to terminate the service.  
  Writing row to database: Adding 100 to 15.99  
  Writing row to database: Subtracting 76.54 from 145  
  Writing row to database: Subtracting 42.16 from 21.05  
  Writing row to database: Multiplying 9 by 81.25  
  Writing row to database: Dividing 22 by 7  
```  
  
 <span data-ttu-id="95526-143">Başarılı bir yürütme sonrasında, istemcinin işlem kapsamı tamamlanır ve bu kapsam içinde gerçekleştirilen tüm eylemler işlenir.</span><span class="sxs-lookup"><span data-stu-id="95526-143">After a successful execution, the client's transaction scope completes and all actions taken within that scope are committed.</span></span> <span data-ttu-id="95526-144">Özellikle, belirtilen 5 kayıt hizmetin veritabanında kalıcı hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="95526-144">Specifically, the noted 5 records are persisted in the service's database.</span></span> <span data-ttu-id="95526-145">Bunların ilk 2 ' nin, istemci işleminin kapsamı içinde meydana geldi.</span><span class="sxs-lookup"><span data-stu-id="95526-145">The first 2 of these have occurred within the scope of the client's transaction.</span></span>  
  
 <span data-ttu-id="95526-146">İstemci `TransactionScope` bir özel durum oluştuysa, işlem tamamlanamaz.</span><span class="sxs-lookup"><span data-stu-id="95526-146">If an exception occurred anywhere within the client's `TransactionScope` then the transaction cannot complete.</span></span> <span data-ttu-id="95526-147">Bu, bu kapsam içinde günlüğe kaydedilen kayıtların veritabanına uygulanmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="95526-147">This causes the records logged within that scope to not be committed to the database.</span></span> <span data-ttu-id="95526-148">Bu efekt, dış `TransactionScope`tamamlamaya yönelik çağrının yorum yapıldıktan sonra örnek çalıştırmayı tekrarlayarak gözlemlenebilir.</span><span class="sxs-lookup"><span data-stu-id="95526-148">This effect can be observed by repeating the sample run after commenting out the call to complete the outer `TransactionScope`.</span></span> <span data-ttu-id="95526-149">Bu tür bir çalıştırmada, istemci işlemi bu işlemlere akmadığı için yalnızca son 3 eylem (ikinci `Subtract`, `Multiply` ve `Divide` istekleri) günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="95526-149">On such a run, only the last 3 actions (from the second `Subtract`, the `Multiply` and the `Divide` requests) are logged because the client transaction did not flow to those.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="95526-150">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="95526-150">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="95526-151">Çözümün C# veya Visual Basic .NET sürümünü derlemek Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md) konusundaki yönergeleri izleyin</span><span class="sxs-lookup"><span data-stu-id="95526-151">To build the C# or Visual Basic .NET version of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)</span></span>  
  
2. <span data-ttu-id="95526-152">SQL Server Express Edition veya SQL Server yüklediğinizden ve bağlantı dizesinin hizmetin uygulama yapılandırma dosyasında doğru şekilde ayarlandığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="95526-152">Ensure that you have installed SQL Server Express Edition or SQL Server, and that the connection string has been correctly set in the service’s application configuration file.</span></span> <span data-ttu-id="95526-153">Örneği bir veritabanı kullanmadan çalıştırmak için, hizmetin uygulama yapılandırma dosyasında `usingSql` değerini `false` olarak ayarlayın</span><span class="sxs-lookup"><span data-stu-id="95526-153">To run the sample without using a database, set the `usingSql` value in the service’s application configuration file to `false`</span></span>  
  
3. <span data-ttu-id="95526-154">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="95526-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="95526-155">Platformlar arası yapılandırma için aşağıdaki yönergeleri kullanarak Dağıtılmış İşlem Düzenleyicisi etkinleştirin ve Windows SDK WCF Işlemleri ağ desteğini etkinleştirmek için WsatConfig. exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="95526-155">For cross-machine configuration, enable the Distributed Transaction Coordinator using the instructions below, and use the WsatConfig.exe tool from the Windows SDK to enable WCF Transactions network support.</span></span> <span data-ttu-id="95526-156">WsatConfig. exe ' yi ayarlama hakkında daha fazla bilgi için bkz. [WS Atomik Işlem desteğini yapılandırma](../feature-details/configuring-ws-atomic-transaction-support.md).</span><span class="sxs-lookup"><span data-stu-id="95526-156">For information on setting up WsatConfig.exe, see [Configuring WS-Atomic Transaction Support](../feature-details/configuring-ws-atomic-transaction-support.md).</span></span>  
  
 <span data-ttu-id="95526-157">Örneği aynı bilgisayarda veya farklı bilgisayarlarda çalıştırdığınız gibi, ağ işlem akışını etkinleştirmek için Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) yapılandırmanız ve WCF işlemleri ağ desteğini etkinleştirmek için WsatConfig. exe aracını kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="95526-157">Whether you run the sample on the same computer or on different computers, you must configure the Microsoft Distributed Transaction Coordinator (MSDTC) to enable network transaction flow and use the WsatConfig.exe tool to enable WCF transactions network support.</span></span>  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample"></a><span data-ttu-id="95526-158">Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) örneğini çalıştırmayı destekleyecek şekilde yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="95526-158">To configure the Microsoft Distributed Transaction Coordinator (MSDTC) to support running the sample</span></span>  
  
1. <span data-ttu-id="95526-159">Windows Server 2003 veya Windows XP çalıştıran bir hizmet makinesinde, bu yönergeleri izleyerek MSDTC 'yi gelen ağ işlemlerine izin verecek şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="95526-159">On a service machine running Windows Server 2003 or Windows XP, configure MSDTC to allow incoming network transactions by following these instructions.</span></span>  
  
    1. <span data-ttu-id="95526-160">**Başlat** menüsünde, **Denetim Masası**' na, ardından **Yönetimsel Araçlar**' a ve ardından **Bileşen Hizmetleri**' ne gidin.</span><span class="sxs-lookup"><span data-stu-id="95526-160">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2. <span data-ttu-id="95526-161">**Bileşen Hizmetleri**' ni genişletin.</span><span class="sxs-lookup"><span data-stu-id="95526-161">Expand **Component Services**.</span></span> <span data-ttu-id="95526-162">**Bilgisayarlar** klasörünü açın.</span><span class="sxs-lookup"><span data-stu-id="95526-162">Open the **Computers** folder.</span></span>  
  
    3. <span data-ttu-id="95526-163">**Bilgisayarım ' a** sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="95526-163">Right-click **My Computer** and select **Properties**.</span></span>  
  
    4. <span data-ttu-id="95526-164">**MSDTC** sekmesinde **Güvenlik Yapılandırması**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="95526-164">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    5. <span data-ttu-id="95526-165">**Ağ DTC erişimini** denetleyin ve **gelen erişime izin verin**.</span><span class="sxs-lookup"><span data-stu-id="95526-165">Check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    6. <span data-ttu-id="95526-166">**Tamam**' a tıklayın ve ardından **Evet** ' e tıklayarak MSDTC hizmetini yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="95526-166">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    7. <span data-ttu-id="95526-167">**Tamam**’a tıklayarak iletişim kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="95526-167">Click **OK** to close the dialog box.</span></span>  
  
2. <span data-ttu-id="95526-168">Windows Server 2008 veya Windows Vista çalıştıran bir hizmet makinesinde, bu yönergeleri izleyerek MSDTC 'yi gelen ağ işlemlerine izin verecek şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="95526-168">On a service machine running Windows Server 2008 or Windows Vista, configure MSDTC to allow incoming network transactions by following these instructions.</span></span>  
  
    1. <span data-ttu-id="95526-169">**Başlat** menüsünde, **Denetim Masası**' na, ardından **Yönetimsel Araçlar**' a ve ardından **Bileşen Hizmetleri**' ne gidin.</span><span class="sxs-lookup"><span data-stu-id="95526-169">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2. <span data-ttu-id="95526-170">**Bileşen Hizmetleri**' ni genişletin.</span><span class="sxs-lookup"><span data-stu-id="95526-170">Expand **Component Services**.</span></span> <span data-ttu-id="95526-171">**Bilgisayarlar** klasörünü açın.</span><span class="sxs-lookup"><span data-stu-id="95526-171">Open the **Computers** folder.</span></span> <span data-ttu-id="95526-172">**Dağıtılmış işlem Düzenleyicisi**seçin.</span><span class="sxs-lookup"><span data-stu-id="95526-172">Select **Distributed Transaction Coordinator**.</span></span>  
  
    3. <span data-ttu-id="95526-173">**DTC Düzenleyicisi** ' ne sağ tıklayıp **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="95526-173">Right-click **DTC Coordinator** and select **Properties**.</span></span>  
  
    4. <span data-ttu-id="95526-174">**Güvenlik** sekmesinde, **Ağ DTC erişimi** ' ni ve **gelen izin ver**' i işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="95526-174">On the **Security** tab, check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    5. <span data-ttu-id="95526-175">**Tamam**' a tıklayın ve ardından **Evet** ' e tıklayarak MSDTC hizmetini yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="95526-175">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    6. <span data-ttu-id="95526-176">**Tamam**’a tıklayarak iletişim kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="95526-176">Click **OK** to close the dialog box.</span></span>  
  
3. <span data-ttu-id="95526-177">İstemci makinesinde, giden ağ işlemlerine izin vermek için MSDTC 'yi yapılandırın:</span><span class="sxs-lookup"><span data-stu-id="95526-177">On the client machine, configure MSDTC to allow outgoing network transactions:</span></span>  
  
    1. <span data-ttu-id="95526-178">**Başlat** menüsünden `Control Panel`, **Yönetim Araçları**ve ardından **Bileşen Hizmetleri**' ne gidin.</span><span class="sxs-lookup"><span data-stu-id="95526-178">From the **Start** menu, navigate to `Control Panel`, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2. <span data-ttu-id="95526-179">**Bilgisayarım ' a** sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="95526-179">Right-click **My Computer** and select **Properties**.</span></span>  
  
    3. <span data-ttu-id="95526-180">**MSDTC** sekmesinde **Güvenlik Yapılandırması**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="95526-180">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    4. <span data-ttu-id="95526-181">**Ağ DTC erişimini** denetleyin ve **giden erişime izin verin**.</span><span class="sxs-lookup"><span data-stu-id="95526-181">Check **Network DTC Access** and **Allow Outbound**.</span></span>  
  
    5. <span data-ttu-id="95526-182">**Tamam**' a tıklayın ve ardından **Evet** ' e tıklayarak MSDTC hizmetini yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="95526-182">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    6. <span data-ttu-id="95526-183">**Tamam**’a tıklayarak iletişim kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="95526-183">Click **OK** to close the dialog box.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="95526-184">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="95526-184">The samples may already be installed on your machine.</span></span> <span data-ttu-id="95526-185">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="95526-185">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="95526-186">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="95526-186">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="95526-187">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="95526-187">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\TransactionFlow`
