---
title: WS İşlem Akışı
ms.date: 03/30/2017
helpviewer_keywords:
- Transactions
ms.assetid: f8eecbcf-990a-4dbb-b29b-c3f9e3b396bd
ms.openlocfilehash: 8b037a2faa6ed5f7c77ea9347b92af7dc1ec2c27
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183163"
---
# <a name="ws-transaction-flow"></a><span data-ttu-id="a4b69-102">WS İşlem Akışı</span><span class="sxs-lookup"><span data-stu-id="a4b69-102">WS Transaction Flow</span></span>
<span data-ttu-id="a4b69-103">Bu örnek, istemci tarafından koordine edilmiş bir işlemin kullanımını ve WS-Atomik İşlem veya OleTransactions protokolünü kullanarak işlem akışı için istemci ve sunucu seçeneklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a4b69-103">This sample demonstrates the use of a client-coordinated transaction and the client and server options for transaction flow using either the WS-Atomic Transaction or OleTransactions protocol.</span></span> <span data-ttu-id="a4b69-104">Bu örnek, bir hesap makinesi hizmetini uygulayan [Başlarken'e](../../../../docs/framework/wcf/samples/getting-started-sample.md) dayanır, ancak `TransactionFlowAttribute` işlemler, işlem akışının hangi derece etkin olduğunu belirlemek için **TransactionFlowOption** numaralandırması ile birlikte kullanımı göstermek için atfedilir.</span><span class="sxs-lookup"><span data-stu-id="a4b69-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service but the operations are attributed to demonstrate the use of the `TransactionFlowAttribute` with the **TransactionFlowOption** enumeration to determine to what degree transaction flow is enabled.</span></span> <span data-ttu-id="a4b69-105">Akışlı işlem kapsamında, istenen işlemlerin bir günlük bir veritabanına yazılır ve istemci koordine hareketi tamamlanana kadar devam eder - istemci hareketi tamamlanmazsa, Web hizmeti hareketi veritabanına uygun güncelleştirmeler taahhüt edilmez.</span><span class="sxs-lookup"><span data-stu-id="a4b69-105">Within the scope of the flowed transaction, a log of the requested operations is written to a database and persists until the client coordinated transaction has completed - if the client transaction does not complete, the Web service transaction ensures that the appropriate updates to the database are not committed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a4b69-106">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="a4b69-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="a4b69-107">Hizmete ve bir hareketle bağlantı başlattıktan sonra istemci çeşitli hizmet işlemlerine erişiyor.</span><span class="sxs-lookup"><span data-stu-id="a4b69-107">After initiating a connection to the service and a transaction, the client accesses several service operations.</span></span> <span data-ttu-id="a4b69-108">Hizmet için sözleşme, farklı bir ayar gösteren operasyonların her biri `TransactionFlowOption`ile aşağıdaki gibi tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="a4b69-108">The contract for the service is defined as follows with each of the operations demonstrating a different setting for the `TransactionFlowOption`.</span></span>  

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

 <span data-ttu-id="a4b69-109">Bu, işlemleri işlenecek sırayla tanımlar:</span><span class="sxs-lookup"><span data-stu-id="a4b69-109">This defines the operations in the order they are to be processed:</span></span>  
  
- <span data-ttu-id="a4b69-110">İşlem `Add` isteği, akışlı bir hareket içermelidir.</span><span class="sxs-lookup"><span data-stu-id="a4b69-110">An `Add` operation request must include a flowed transaction.</span></span>  
  
- <span data-ttu-id="a4b69-111">İşlem `Subtract` isteği akışlı bir hareket içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a4b69-111">A `Subtract` operation request may include a flowed transaction.</span></span>  
  
- <span data-ttu-id="a4b69-112">İşlem `Multiply` isteği, açık İzin Verilmeyen ayar üzerinden akan bir hareketi içermemelidir.</span><span class="sxs-lookup"><span data-stu-id="a4b69-112">A `Multiply` operation request must not include a flowed transaction through the explicit NotAllowed setting.</span></span>  
  
- <span data-ttu-id="a4b69-113">İşlem `Divide` isteği, bir `TransactionFlow` öznitelik ihmal yoluyla akan bir hareket içermemelidir.</span><span class="sxs-lookup"><span data-stu-id="a4b69-113">A `Divide` operation request must not include a flowed transaction through the omission of a `TransactionFlow` attribute.</span></span>  
  
 <span data-ttu-id="a4b69-114">Hareket akışını etkinleştirmek için, [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) uygun işlem özniteliklerine ek olarak hareketAkışı>özelliği etkinleştirilmiş bağlamalar kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a4b69-114">To enable transaction flow, bindings with the [\<transactionFlow>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) property enabled must be used in addition to the appropriate operation attributes.</span></span> <span data-ttu-id="a4b69-115">Bu örnekte, hizmetin yapılandırması meta veri alışverişi bitiş noktasına ek olarak bir TCP bitiş noktası ve bir HTTP bitiş noktasını ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="a4b69-115">In this sample, the service's configuration exposes a TCP endpoint and an HTTP endpoint in addition to a Metadata Exchange endpoint.</span></span> <span data-ttu-id="a4b69-116">TCP bitiş noktası ve HTTP bitiş noktası, her ikisi de [ \<hareket Akışı>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) özelliği etkin olan aşağıdaki bağlamaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="a4b69-116">The TCP endpoint and the HTTP endpoint use the following bindings, both of which have the [\<transactionFlow>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) property enabled.</span></span>  
  
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
> <span data-ttu-id="a4b69-117">Sistem tarafından sağlanan netTcpBinding işlemProtokolü'nün belirtimine izin vererken, sistem tarafından sağlanan wsHttpBinding yalnızca daha birlikte çalışabilir WSAtomicTransactionOctober2004 protokolünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="a4b69-117">The system-provided netTcpBinding allows specification of the transactionProtocol whereas the system-provided wsHttpBinding uses only the more interoperable WSAtomicTransactionOctober2004 protocol.</span></span> <span data-ttu-id="a4b69-118">OleTransactions protokolü yalnızca Windows Communication Foundation (WCF) istemcileri tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a4b69-118">The OleTransactions protocol is only available for use by Windows Communication Foundation (WCF) clients.</span></span>  
  
 <span data-ttu-id="a4b69-119">`ICalculator` Arabirimi uygulayan sınıf için, `true`tüm yöntemler <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> .</span><span class="sxs-lookup"><span data-stu-id="a4b69-119">For the class that implements the `ICalculator` interface, all of the methods are attributed with <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property set to `true`.</span></span> <span data-ttu-id="a4b69-120">Bu ayar, yöntem içinde gerçekleştirilen tüm eylemlerin bir işlem kapsamında gerçekleştiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="a4b69-120">This setting declares that all actions taken within the method occur within the scope of a transaction.</span></span> <span data-ttu-id="a4b69-121">Bu durumda, gerçekleştirilen eylemler günlük veritabanına kayıt içerir.</span><span class="sxs-lookup"><span data-stu-id="a4b69-121">In this case, the actions taken include recording to the log database.</span></span> <span data-ttu-id="a4b69-122">İşlem isteği akışlı bir hareket içeriyorsa, eylemler gelen işlem kapsamında oluşur veya yeni bir hareket kapsamı otomatik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a4b69-122">If the operation request includes a flowed transaction then the actions occur within the scope of the incoming transaction or a new transaction scope is automatically generated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a4b69-123">Özellik, <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> hizmet yöntemi uygulamalarına yerel davranış tanımlar ve istemcinin bir işlem akışı için yeteneğini veya gereksinimini tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="a4b69-123">The <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property defines behavior local to the service method implementations and does not define the client's ability to or requirement for flowing a transaction.</span></span>  

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

 <span data-ttu-id="a4b69-124">İstemcide, hizmetin `TransactionFlowOption` işlemlerdeki ayarları istemcinin oluşturulan `ICalculator` arabirimi tanımına yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="a4b69-124">On the client, the service's `TransactionFlowOption` settings on the operations are reflected in the client's generated definition of the `ICalculator` interface.</span></span> <span data-ttu-id="a4b69-125">Ayrıca, hizmetin `transactionFlow` özellik ayarları istemcinin uygulama yapılandırmasında yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="a4b69-125">Also, the service's `transactionFlow` property settings are reflected in the client's application configuration.</span></span> <span data-ttu-id="a4b69-126">İstemci uygun `endpointConfigurationName`seçerek aktarım ve protokolü seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4b69-126">The client can select the transport and protocol by selecting the appropriate `endpointConfigurationName`.</span></span>  

```csharp
// Create a client using either wsat or oletx endpoint configurations  
CalculatorClient client = new CalculatorClient("WSAtomicTransaction_endpoint");  
// CalculatorClient client = new CalculatorClient("OleTransactions_endpoint");  
```

> [!NOTE]
> <span data-ttu-id="a4b69-127">Hangi protokol veya aktarım seçilirse seçilsin, bu örneğin gözlenen davranışı aynıdır.</span><span class="sxs-lookup"><span data-stu-id="a4b69-127">The observed behavior of this sample is the same no matter which protocol or transport is chosen.</span></span>  
  
 <span data-ttu-id="a4b69-128">Hizmetbağlantısını başlatan istemci, hizmet işlemlerine yapılan `TransactionScope` çağrılar etrafında yeni bir yeni oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a4b69-128">Having initiated the connection to the service, the client creates a new `TransactionScope` around the calls to the service operations.</span></span>  

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

 <span data-ttu-id="a4b69-129">İşlemlere yapılan aramalar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="a4b69-129">The calls to the operations are as follows:</span></span>  
  
- <span data-ttu-id="a4b69-130">İstek, `Add` gerekli hareketi hizmete akar ve hizmetin eylemleri istemcinin hareketi kapsamında gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="a4b69-130">The `Add` request flows the required transaction to the service and the service's actions occur within the scope of the client's transaction.</span></span>  
  
- <span data-ttu-id="a4b69-131">İlk `Subtract` istek ayrıca izin verilen hareketi hizmete akar ve yine hizmetin eylemleri istemcinin hareketi kapsamında gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="a4b69-131">The first `Subtract` request also flows the allowed transaction to the service and again the service's actions occur within the scope of the client's transaction.</span></span>  
  
- <span data-ttu-id="a4b69-132">İkinci `Subtract` `TransactionScopeOption.Suppress` istek, seçenekle birlikte bildirilen yeni bir hareket kapsamı içinde gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="a4b69-132">The second `Subtract` request is performed within a new transaction scope declared with the `TransactionScopeOption.Suppress` option.</span></span> <span data-ttu-id="a4b69-133">Bu, istemcinin ilk dış işlemini bastırır ve istek hizmete bir hareket akışı sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="a4b69-133">This suppresses the client's initial outer transaction and the request does not flow a transaction to the service.</span></span> <span data-ttu-id="a4b69-134">Bu yaklaşım, istemcinin gerekli olmadığında bir işlemi bir hizmete akmasına karşı açıkça devre dışı bırakmasına ve korumasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="a4b69-134">This approach allows a client to explicitly opt-out of and protect against flowing a transaction to a service when that is not required.</span></span> <span data-ttu-id="a4b69-135">Hizmetin eylemleri yeni ve bağlantısız bir işlem kapsamında gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="a4b69-135">The service's actions occur within the scope of a new and unconnected transaction.</span></span>  
  
- <span data-ttu-id="a4b69-136">`Multiply` İstemcinin oluşturulan `ICalculator` arabirim tanımı bir <xref:System.ServiceModel.TransactionFlowAttribute> dizi <xref:System.ServiceModel.TransactionFlowOption> `NotAllowed`içerdiğinden, istek hizmete bir hareket akışı sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="a4b69-136">The `Multiply` request does not flow a transaction to the service because the client's generated definition of the `ICalculator` interface includes a <xref:System.ServiceModel.TransactionFlowAttribute> set to <xref:System.ServiceModel.TransactionFlowOption>`NotAllowed`.</span></span>  
  
- <span data-ttu-id="a4b69-137">Yine `Divide` istemcinin oluşturulan `ICalculator` arabirim tanımı bir `TransactionFlowAttribute`.</span><span class="sxs-lookup"><span data-stu-id="a4b69-137">The `Divide` request does not flow a transaction to the service because again the client's generated definition of the `ICalculator` interface does not include a `TransactionFlowAttribute`.</span></span> <span data-ttu-id="a4b69-138">Hizmetin eylemleri, yeni ve bağlantısız başka bir işlem kapsamında yeniden oluşur.</span><span class="sxs-lookup"><span data-stu-id="a4b69-138">The service's actions again occur within the scope of another new and unconnected transaction.</span></span>  
  
 <span data-ttu-id="a4b69-139">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a4b69-139">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="a4b69-140">İstemciyi kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="a4b69-140">Press ENTER in the client window to shut down the client.</span></span>  
  
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
  
 <span data-ttu-id="a4b69-141">Servis işlemi isteklerinin günlüğe kaydi bölümü, hizmetin konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a4b69-141">The logging of the service operation requests are displayed in the service's console window.</span></span> <span data-ttu-id="a4b69-142">İstemciyi kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="a4b69-142">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Press <ENTER> to terminate the service.  
  Writing row to database: Adding 100 to 15.99  
  Writing row to database: Subtracting 76.54 from 145  
  Writing row to database: Subtracting 42.16 from 21.05  
  Writing row to database: Multiplying 9 by 81.25  
  Writing row to database: Dividing 22 by 7  
```  
  
 <span data-ttu-id="a4b69-143">Başarılı bir yürütmeden sonra, istemcinin işlem kapsamı tamamlanır ve bu kapsamda gerçekleştirilen tüm eylemler taahhüt edilir.</span><span class="sxs-lookup"><span data-stu-id="a4b69-143">After a successful execution, the client's transaction scope completes and all actions taken within that scope are committed.</span></span> <span data-ttu-id="a4b69-144">Özellikle, belirtilen 5 kayıt hizmetin veritabanında kalıcıdır.</span><span class="sxs-lookup"><span data-stu-id="a4b69-144">Specifically, the noted 5 records are persisted in the service's database.</span></span> <span data-ttu-id="a4b69-145">Bunlardan ilk ikisi müşterinin işlem kapsamında meydana gelmiştir.</span><span class="sxs-lookup"><span data-stu-id="a4b69-145">The first 2 of these have occurred within the scope of the client's transaction.</span></span>  
  
 <span data-ttu-id="a4b69-146">İstemcinin herhangi bir yerinde `TransactionScope` bir özel durum oluştuysa, işlem tamamlanamaz.</span><span class="sxs-lookup"><span data-stu-id="a4b69-146">If an exception occurred anywhere within the client's `TransactionScope` then the transaction cannot complete.</span></span> <span data-ttu-id="a4b69-147">Bu, bu kapsamda günlüğe kaydedilen kayıtların veritabanına kaydedilmemelerine neden olur.</span><span class="sxs-lookup"><span data-stu-id="a4b69-147">This causes the records logged within that scope to not be committed to the database.</span></span> <span data-ttu-id="a4b69-148">Bu etki, dış `TransactionScope`tamamlamak için çağrı dışarı yorumlama sonra örnek çalıştırmak tekrarlayarak görülebilir.</span><span class="sxs-lookup"><span data-stu-id="a4b69-148">This effect can be observed by repeating the sample run after commenting out the call to complete the outer `TransactionScope`.</span></span> <span data-ttu-id="a4b69-149">Böyle bir çalıştırmada, istemci hareketi bunlara `Subtract`akmaydığından yalnızca son 3 eylem (ikinci, istek `Multiply` ve `Divide` istekten) günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="a4b69-149">On such a run, only the last 3 actions (from the second `Subtract`, the `Multiply` and the `Divide` requests) are logged because the client transaction did not flow to those.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a4b69-150">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="a4b69-150">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a4b69-151">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için Windows Communication Foundation Örneklerini Oluşturma yönergelerini](../../../../docs/framework/wcf/samples/building-the-samples.md) izleyin</span><span class="sxs-lookup"><span data-stu-id="a4b69-151">To build the C# or Visual Basic .NET version of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)</span></span>  
  
2. <span data-ttu-id="a4b69-152">SQL Server Express Edition veya SQL Server yüklediğinizden ve bağlantı dizesinin hizmetin uygulama yapılandırma dosyasında doğru şekilde ayarlandığını sağlayın.</span><span class="sxs-lookup"><span data-stu-id="a4b69-152">Ensure that you have installed SQL Server Express Edition or SQL Server, and that the connection string has been correctly set in the service’s application configuration file.</span></span> <span data-ttu-id="a4b69-153">Veritabanı kullanmadan örneği çalıştırmak için, `usingSql` hizmetin uygulama yapılandırma dosyasındaki değeri`false`</span><span class="sxs-lookup"><span data-stu-id="a4b69-153">To run the sample without using a database, set the `usingSql` value in the service’s application configuration file to `false`</span></span>  
  
3. <span data-ttu-id="a4b69-154">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="a4b69-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="a4b69-155">Makineler arası yapılandırma için, Aşağıdaki yönergeleri kullanarak Dağıtılmış İşlem Koordinatörü'ne olanak sağlayın ve WCF İşlemleri ağ desteğini etkinleştirmek için Windows SDK'daki WsatConfig.exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="a4b69-155">For cross-machine configuration, enable the Distributed Transaction Coordinator using the instructions below, and use the WsatConfig.exe tool from the Windows SDK to enable WCF Transactions network support.</span></span> <span data-ttu-id="a4b69-156">WsatConfig.exe kurulumu hakkında daha fazla bilgi için [WS-Atomik İşlem Desteğini Yapılandırma'ya](../feature-details/configuring-ws-atomic-transaction-support.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="a4b69-156">For information on setting up WsatConfig.exe, see [Configuring WS-Atomic Transaction Support](../feature-details/configuring-ws-atomic-transaction-support.md).</span></span>  
  
 <span data-ttu-id="a4b69-157">Örneği ister aynı bilgisayarda ister farklı bilgisayarlarda çalıştırın, ağ hareket akışını etkinleştirmek ve WCF işlemleri ağ desteğini etkinleştirmek için WsatConfig.exe aracını kullanmak için Microsoft Dağıtılmış Hareket Koordinatörü'nu (MSDTC) yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a4b69-157">Whether you run the sample on the same computer or on different computers, you must configure the Microsoft Distributed Transaction Coordinator (MSDTC) to enable network transaction flow and use the WsatConfig.exe tool to enable WCF transactions network support.</span></span>  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample"></a><span data-ttu-id="a4b69-158">Microsoft Distributed Transaction Koordinatörü'nü (MSDTC) örneği çalıştırmak için yapılandırmak</span><span class="sxs-lookup"><span data-stu-id="a4b69-158">To configure the Microsoft Distributed Transaction Coordinator (MSDTC) to support running the sample</span></span>  
  
1. <span data-ttu-id="a4b69-159">Windows Server 2003 veya Windows XP çalıştıran bir servis makinesinde, bu yönergeleri izleyerek gelen ağ işlemlerine izin verecek şekilde MSDTC'yi yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="a4b69-159">On a service machine running Windows Server 2003 or Windows XP, configure MSDTC to allow incoming network transactions by following these instructions.</span></span>  
  
    1. <span data-ttu-id="a4b69-160">**Başlat** menüsünden Denetim **Masası'na,** ardından **Yönetim Araçları'na**ve ardından **Bileşen Hizmetleri'ne**gidin.</span><span class="sxs-lookup"><span data-stu-id="a4b69-160">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2. <span data-ttu-id="a4b69-161">**Bileşen Hizmetlerini**Genişletin.</span><span class="sxs-lookup"><span data-stu-id="a4b69-161">Expand **Component Services**.</span></span> <span data-ttu-id="a4b69-162">**Bilgisayarlar** klasörünü açın.</span><span class="sxs-lookup"><span data-stu-id="a4b69-162">Open the **Computers** folder.</span></span>  
  
    3. <span data-ttu-id="a4b69-163">**Bilgisayarım'ı** sağ tıklatın ve **Özellikler'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="a4b69-163">Right-click **My Computer** and select **Properties**.</span></span>  
  
    4. <span data-ttu-id="a4b69-164">**MSDTC** sekmesinde **Güvenlik Yapılandırması'nı**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="a4b69-164">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    5. <span data-ttu-id="a4b69-165">**Ağ DTC Erişimini** Denetleyin ve **GelenE İzin Verin.**</span><span class="sxs-lookup"><span data-stu-id="a4b69-165">Check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    6. <span data-ttu-id="a4b69-166">**TAMAM'ı**tıklatın, ardından MSDTC hizmetini yeniden başlatmak için **Evet'i** tıklatın.</span><span class="sxs-lookup"><span data-stu-id="a4b69-166">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    7. <span data-ttu-id="a4b69-167">**Tamam**’a tıklayarak iletişim kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="a4b69-167">Click **OK** to close the dialog box.</span></span>  
  
2. <span data-ttu-id="a4b69-168">Windows Server 2008 veya Windows Vista çalıştıran bir servis makinesinde, bu yönergeleri izleyerek gelen ağ hareketlerine izin verecek şekilde MSDTC'yi yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="a4b69-168">On a service machine running Windows Server 2008 or Windows Vista, configure MSDTC to allow incoming network transactions by following these instructions.</span></span>  
  
    1. <span data-ttu-id="a4b69-169">**Başlat** menüsünden Denetim **Masası'na,** ardından **Yönetim Araçları'na**ve ardından **Bileşen Hizmetleri'ne**gidin.</span><span class="sxs-lookup"><span data-stu-id="a4b69-169">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2. <span data-ttu-id="a4b69-170">**Bileşen Hizmetlerini**Genişletin.</span><span class="sxs-lookup"><span data-stu-id="a4b69-170">Expand **Component Services**.</span></span> <span data-ttu-id="a4b69-171">**Bilgisayarlar** klasörünü açın.</span><span class="sxs-lookup"><span data-stu-id="a4b69-171">Open the **Computers** folder.</span></span> <span data-ttu-id="a4b69-172">**Dağıtılmış Hareket Koordinatörü'nü**seçin.</span><span class="sxs-lookup"><span data-stu-id="a4b69-172">Select **Distributed Transaction Coordinator**.</span></span>  
  
    3. <span data-ttu-id="a4b69-173">**DTC Koordinatörü'ne** sağ tıklayın ve **Özellikler'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="a4b69-173">Right-click **DTC Coordinator** and select **Properties**.</span></span>  
  
    4. <span data-ttu-id="a4b69-174">**Güvenlik** sekmesinde, **Ağ DTC Erişimi'ni** denetleyin ve **GelenE İzin Ver.**</span><span class="sxs-lookup"><span data-stu-id="a4b69-174">On the **Security** tab, check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    5. <span data-ttu-id="a4b69-175">**TAMAM'ı**tıklatın, ardından MSDTC hizmetini yeniden başlatmak için **Evet'i** tıklatın.</span><span class="sxs-lookup"><span data-stu-id="a4b69-175">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    6. <span data-ttu-id="a4b69-176">**Tamam**’a tıklayarak iletişim kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="a4b69-176">Click **OK** to close the dialog box.</span></span>  
  
3. <span data-ttu-id="a4b69-177">İstemci makinesinde, giden ağ hareketlerine izin verecek şekilde MSDTC'yi yapılandırın:</span><span class="sxs-lookup"><span data-stu-id="a4b69-177">On the client machine, configure MSDTC to allow outgoing network transactions:</span></span>  
  
    1. <span data-ttu-id="a4b69-178">**Başlat** menüsünden, ardından `Control Panel` **Yönetim Araçları'na**ve ardından **Bileşen Hizmetleri'ne**gidin.</span><span class="sxs-lookup"><span data-stu-id="a4b69-178">From the **Start** menu, navigate to `Control Panel`, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2. <span data-ttu-id="a4b69-179">**Bilgisayarım'ı** sağ tıklatın ve **Özellikler'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="a4b69-179">Right-click **My Computer** and select **Properties**.</span></span>  
  
    3. <span data-ttu-id="a4b69-180">**MSDTC** sekmesinde **Güvenlik Yapılandırması'nı**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="a4b69-180">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    4. <span data-ttu-id="a4b69-181">**Ağ DTC Erişimini** Denetleyin ve **Gidene İzin Verin.**</span><span class="sxs-lookup"><span data-stu-id="a4b69-181">Check **Network DTC Access** and **Allow Outbound**.</span></span>  
  
    5. <span data-ttu-id="a4b69-182">**TAMAM'ı**tıklatın, ardından MSDTC hizmetini yeniden başlatmak için **Evet'i** tıklatın.</span><span class="sxs-lookup"><span data-stu-id="a4b69-182">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    6. <span data-ttu-id="a4b69-183">**Tamam**’a tıklayarak iletişim kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="a4b69-183">Click **OK** to close the dialog box.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a4b69-184">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="a4b69-184">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a4b69-185">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a4b69-185">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="a4b69-186">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="a4b69-186">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a4b69-187">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="a4b69-187">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\TransactionFlow`
