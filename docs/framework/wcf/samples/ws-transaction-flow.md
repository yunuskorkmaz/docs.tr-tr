---
title: "WS İşlem Akışı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Transactions
ms.assetid: f8eecbcf-990a-4dbb-b29b-c3f9e3b396bd
caps.latest.revision: "43"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bf441831a205b022899999b1bf34e1505b8fb6bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ws-transaction-flow"></a><span data-ttu-id="4c00a-102">WS İşlem Akışı</span><span class="sxs-lookup"><span data-stu-id="4c00a-102">WS Transaction Flow</span></span>
<span data-ttu-id="4c00a-103">Bu örnek bir istemci Eşgüdümlü işlem kullanımını gösterir ve işlem için istemci ve sunucu seçenekleri WS-Atomic işlem veya OleTransactions protokolü kullanarak akış.</span><span class="sxs-lookup"><span data-stu-id="4c00a-103">This sample demonstrates the use of a client-coordinated transaction and the client and server options for transaction flow using either the WS-Atomic Transaction or OleTransactions protocol.</span></span> <span data-ttu-id="4c00a-104">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hesap makinesi hizmetinin uygulayan ancak kullanımını göstermek için işlemleri öznitelikli `TransactionFlowAttribute` ile **TransactionFlowOption** ne derece işlem akışı etkin belirlemek için numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="4c00a-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service but the operations are attributed to demonstrate the use of the `TransactionFlowAttribute` with the **TransactionFlowOption** enumeration to determine to what degree transaction flow is enabled.</span></span> <span data-ttu-id="4c00a-105">Akışlı işlem kapsamı içinde istenen işlem günlüğünü veritabanına yazılır ve Eşgüdümlü istemci işlemi tamamlanana kadar - istemci işlemi tamamlanmazsa devam ederse Web hizmeti işlemi sağlar veritabanı için uygun güncelleştirmeleri iletilmez.</span><span class="sxs-lookup"><span data-stu-id="4c00a-105">Within the scope of the flowed transaction, a log of the requested operations is written to a database and persists until the client coordinated transaction has completed - if the client transaction does not complete, the Web service transaction ensures that the appropriate updates to the database are not committed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4c00a-106">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="4c00a-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="4c00a-107">İstemci, hizmet ve işlem bağlantı başlatıldıktan sonra birkaç hizmet işlemleri erişir.</span><span class="sxs-lookup"><span data-stu-id="4c00a-107">After initiating a connection to the service and a transaction, the client accesses several service operations.</span></span> <span data-ttu-id="4c00a-108">Hizmet sözleşmesini gibi her biri için farklı bir ayar gösteren işlemleri ile tanımlanmış `TransactionFlowOption`.</span><span class="sxs-lookup"><span data-stu-id="4c00a-108">The contract for the service is defined as follows with each of the operations demonstrating a different setting for the `TransactionFlowOption`.</span></span>  
  
```  
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
  
 <span data-ttu-id="4c00a-109">Bu, işlenmeyi oldukları sırada operations tanımlar:</span><span class="sxs-lookup"><span data-stu-id="4c00a-109">This defines the operations in the order they are to be processed:</span></span>  
  
-   <span data-ttu-id="4c00a-110">Bir `Add` işlem isteği akışlı bir işlem içermelidir.</span><span class="sxs-lookup"><span data-stu-id="4c00a-110">An `Add` operation request must include a flowed transaction.</span></span>  
  
-   <span data-ttu-id="4c00a-111">A `Subtract` işlem isteği akışlı bir işlem içerebilir.</span><span class="sxs-lookup"><span data-stu-id="4c00a-111">A `Subtract` operation request may include a flowed transaction.</span></span>  
  
-   <span data-ttu-id="4c00a-112">A `Multiply` işlem isteği açık QueuedDeliveryRequirements ayarı ile akışlı bir işlem değil içermelidir.</span><span class="sxs-lookup"><span data-stu-id="4c00a-112">A `Multiply` operation request must not include a flowed transaction through the explicit NotAllowed setting.</span></span>  
  
-   <span data-ttu-id="4c00a-113">A `Divide` işlem isteği akan işlem Java'daki üzerinden değil içermelidir bir `TransactionFlow` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="4c00a-113">A `Divide` operation request must not include a flowed transaction through the omission of a `TransactionFlow` attribute.</span></span>  
  
 <span data-ttu-id="4c00a-114">İşlem akışını, bağlamalarla etkinleştirmek için [ \<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) etkin özelliğinin yanı sıra uygun işlemi öznitelikler kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4c00a-114">To enable transaction flow, bindings with the [\<transactionFlow>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) property enabled must be used in addition to the appropriate operation attributes.</span></span> <span data-ttu-id="4c00a-115">Bu örnekte, TCP uç noktası ve bir HTTP uç noktası bir meta veri değişimi uç noktası ek olarak hizmet yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4c00a-115">In this sample, the service's configuration exposes a TCP endpoint and an HTTP endpoint in addition to a Metadata Exchange endpoint.</span></span> <span data-ttu-id="4c00a-116">Her ikisi de sahip olan aşağıdaki bağlamaları TCP uç noktasını ve HTTP uç noktası kullan [ \<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) etkin özelliği.</span><span class="sxs-lookup"><span data-stu-id="4c00a-116">The TCP endpoint and the HTTP endpoint use the following bindings, both of which have the [\<transactionFlow>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) property enabled.</span></span>  
  
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
>  <span data-ttu-id="4c00a-117">Sistem tarafından sağlanan netTcpBinding transactionProtocol belirtimi sağlarken sistem tarafından sağlanan wsHttpBinding yalnızca daha birlikte çalışabilir WSAtomicTransactionOctober2004 protokolünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="4c00a-117">The system-provided netTcpBinding allows specification of the transactionProtocol whereas the system-provided wsHttpBinding uses only the more interoperable WSAtomicTransactionOctober2004 protocol.</span></span> <span data-ttu-id="4c00a-118">OleTransactions protokolü tarafından kullanılmak üzere yalnızca kullanılabilir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] istemciler.</span><span class="sxs-lookup"><span data-stu-id="4c00a-118">The OleTransactions protocol is only available for use by [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] clients.</span></span>  
  
 <span data-ttu-id="4c00a-119">Uygulayan sınıfa için `ICalculator` arabirimi, tüm yöntemleri öznitelikli ile <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="4c00a-119">For the class that implements the `ICalculator` interface, all of the methods are attributed with <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property set to `true`.</span></span> <span data-ttu-id="4c00a-120">Bu ayar yöntemi içinde yapılan tüm eylemler bir işlem kapsamı içinde ortaya bildirir.</span><span class="sxs-lookup"><span data-stu-id="4c00a-120">This setting declares that all actions taken within the method occur within the scope of a transaction.</span></span> <span data-ttu-id="4c00a-121">Bu durumda, veritabanı günlük kaydı gerçekleştirilen eylemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="4c00a-121">In this case, the actions taken include recording to the log database.</span></span> <span data-ttu-id="4c00a-122">İşlem isteğini akışlı bir işlem içeriyorsa eylemleri gelen işlem kapsamında meydana gelen veya yeni bir işlem kapsamı otomatik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4c00a-122">If the operation request includes a flowed transaction then the actions occur within the scope of the incoming transaction or a new transaction scope is automatically generated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4c00a-123"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> Özellik için hizmet yöntemi uygulamaları davranışını yerel tanımlar ve istemcinin yeteneği veya bir işlem akan gereksinim tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="4c00a-123">The <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property defines behavior local to the service method implementations and does not define the client's ability to or requirement for flowing a transaction.</span></span>  
  
```  
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
  
 <span data-ttu-id="4c00a-124">İstemci, hizmet üzerinde `TransactionFlowOption` işlemlerini ayarları, istemcinin oluşturulan tanımında yansıtılır `ICalculator` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="4c00a-124">On the client, the service's `TransactionFlowOption` settings on the operations are reflected in the client's generated definition of the `ICalculator` interface.</span></span> <span data-ttu-id="4c00a-125">Ayrıca, hizmetin `transactionFlow` özellik ayarları, istemci uygulama yapılandırmasında yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="4c00a-125">Also, the service's `transactionFlow` property settings are reflected in the client's application configuration.</span></span> <span data-ttu-id="4c00a-126">İstemci taşıma ve protokolü uygun seçerek seçebilirsiniz `endpointConfigurationName`.</span><span class="sxs-lookup"><span data-stu-id="4c00a-126">The client can select the transport and protocol by selecting the appropriate `endpointConfigurationName`.</span></span>  
  
```  
// Create a client using either wsat or oletx endpoint configurations  
CalculatorClient client = new CalculatorClient("WSAtomicTransaction_endpoint");  
// CalculatorClient client = new CalculatorClient("OleTransactions_endpoint");  
```  
  
> [!NOTE]
>  <span data-ttu-id="4c00a-127">Bu örnekte gözlenen davranışını hangi protokolü veya taşıma seçilir aynıdır.</span><span class="sxs-lookup"><span data-stu-id="4c00a-127">The observed behavior of this sample is the same no matter which protocol or transport is chosen.</span></span>  
  
 <span data-ttu-id="4c00a-128">Hizmeti bağlantısı başlatılan istemci yeni bir oluşturur `TransactionScope` hizmet işlemleri çağrıları geçici.</span><span class="sxs-lookup"><span data-stu-id="4c00a-128">Having initiated the connection to the service, the client creates a new `TransactionScope` around the calls to the service operations.</span></span>  
  
```  
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
  
 <span data-ttu-id="4c00a-129">İşlem çağrıları aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="4c00a-129">The calls to the operations are as follows:</span></span>  
  
-   <span data-ttu-id="4c00a-130">`Add` İstek akışları hizmetine gerekli işlem ve hizmetin Eylemler istemcinin işlem kapsamı içinde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="4c00a-130">The `Add` request flows the required transaction to the service and the service's actions occur within the scope of the client's transaction.</span></span>  
  
-   <span data-ttu-id="4c00a-131">İlk `Subtract` istek Ayrıca hizmet için izin verilen işlem akışları ve yeniden hizmetin Eylemler istemcinin işlem kapsamı içinde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="4c00a-131">The first `Subtract` request also flows the allowed transaction to the service and again the service's actions occur within the scope of the client's transaction.</span></span>  
  
-   <span data-ttu-id="4c00a-132">İkinci `Subtract` isteği ile bildirilen yeni bir işlem kapsamı içinde gerçekleştirilir `TransactionScopeOption.Suppress` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="4c00a-132">The second `Subtract` request is performed within a new transaction scope declared with the `TransactionScopeOption.Suppress` option.</span></span> <span data-ttu-id="4c00a-133">Bu istemcinin başlangıç dış işlem önler ve isteğin bir işlem hizmetine akış değil.</span><span class="sxs-lookup"><span data-stu-id="4c00a-133">This suppresses the client's initial outer transaction and the request does not flow a transaction to the service.</span></span> <span data-ttu-id="4c00a-134">Bu yaklaşım açıkça, çevirin ve gerekli olmadığında bir hizmet için bir işlem akan karşı korumak bir istemci sağlar.</span><span class="sxs-lookup"><span data-stu-id="4c00a-134">This approach allows a client to explicitly opt-out of and protect against flowing a transaction to a service when that is not required.</span></span> <span data-ttu-id="4c00a-135">Hizmetin Eylemler yeni ve bağlantısız bir işlem kapsamı içinde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="4c00a-135">The service's actions occur within the scope of a new and unconnected transaction.</span></span>  
  
-   <span data-ttu-id="4c00a-136">`Multiply` İsteği akan hizmetine bir işlem istemci tanımını oluşturan çünkü `ICalculator` arabirimi içeren bir <xref:System.ServiceModel.TransactionFlowAttribute> kümesine <xref:System.ServiceModel.TransactionFlowOption> `NotAllowed`.</span><span class="sxs-lookup"><span data-stu-id="4c00a-136">The `Multiply` request does not flow a transaction to the service because the client's generated definition of the `ICalculator` interface includes a <xref:System.ServiceModel.TransactionFlowAttribute> set to <xref:System.ServiceModel.TransactionFlowOption>`NotAllowed`.</span></span>  
  
-   <span data-ttu-id="4c00a-137">`Divide` İsteği akan hizmetine bir işlem istemci tanımını yeniden oluşturulmuş için `ICalculator` arabirim içermez bir `TransactionFlowAttribute`.</span><span class="sxs-lookup"><span data-stu-id="4c00a-137">The `Divide` request does not flow a transaction to the service because again the client's generated definition of the `ICalculator` interface does not include a `TransactionFlowAttribute`.</span></span> <span data-ttu-id="4c00a-138">Hizmetin Eylemler yeniden başka bir yeni ve bağlantısız işlem kapsamı içinde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="4c00a-138">The service's actions again occur within the scope of another new and unconnected transaction.</span></span>  
  
 <span data-ttu-id="4c00a-139">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4c00a-139">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="4c00a-140">İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="4c00a-140">Press ENTER in the client window to shut down the client.</span></span>  
  
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
  
 <span data-ttu-id="4c00a-141">Hizmet işlemi isteklerin günlüğe yazılmasını hizmetin konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4c00a-141">The logging of the service operation requests are displayed in the service's console window.</span></span> <span data-ttu-id="4c00a-142">İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="4c00a-142">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Press <ENTER> to terminate the service.  
  Writing row to database: Adding 100 to 15.99  
  Writing row to database: Subtracting 76.54 from 145  
  Writing row to database: Subtracting 42.16 from 21.05  
  Writing row to database: Multiplying 9 by 81.25  
  Writing row to database: Dividing 22 by 7  
```  
  
 <span data-ttu-id="4c00a-143">Başarılı bir yürütme sonra istemcinin işlem kapsamı tamamlar ve bu kapsamı içinde yapılan tüm eylemler uygulanır.</span><span class="sxs-lookup"><span data-stu-id="4c00a-143">After a successful execution, the client's transaction scope completes and all actions taken within that scope are committed.</span></span> <span data-ttu-id="4c00a-144">Özellikle, not ettiğiniz 5 kayıtları hizmetin veritabanında kalıcı niteliktedir.</span><span class="sxs-lookup"><span data-stu-id="4c00a-144">Specifically, the noted 5 records are persisted in the service's database.</span></span> <span data-ttu-id="4c00a-145">Bu ilk 2 istemcinin işlem kapsamı içinde oluştu.</span><span class="sxs-lookup"><span data-stu-id="4c00a-145">The first 2 of these have occurred within the scope of the client's transaction.</span></span>  
  
 <span data-ttu-id="4c00a-146">Bir özel durum istemcinin içinde herhangi bir yere oluştuysa `TransactionScope` sonra işlem tamamlanamıyor.</span><span class="sxs-lookup"><span data-stu-id="4c00a-146">If an exception occurred anywhere within the client's `TransactionScope` then the transaction cannot complete.</span></span> <span data-ttu-id="4c00a-147">Bu veritabanına işleminde değil, kapsam içinde kaydedilmiş kayıtları neden olur.</span><span class="sxs-lookup"><span data-stu-id="4c00a-147">This causes the records logged within that scope to not be committed to the database.</span></span> <span data-ttu-id="4c00a-148">Bu etkiyi dış tamamlamak için duyurmak yorum sonra çalıştırmak örnek tekrarlayarak gösterilebilir `TransactionScope`.</span><span class="sxs-lookup"><span data-stu-id="4c00a-148">This effect can be observed by repeating the sample run after commenting out the call to complete the outer `TransactionScope`.</span></span> <span data-ttu-id="4c00a-149">Bu tür bir çalıştırmada, yalnızca son 3 eylemleri (ikinci `Subtract`, `Multiply` ve `Divide` istekleri) istemci işlemi bu akış değil çünkü kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="4c00a-149">On such a run, only the last 3 actions (from the second `Subtract`, the `Multiply` and the `Divide` requests) are logged because the client transaction did not flow to those.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4c00a-150">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="4c00a-150">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="4c00a-151">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)</span><span class="sxs-lookup"><span data-stu-id="4c00a-151">To build the C# or Visual Basic .NET version of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)</span></span>  
  
2.  <span data-ttu-id="4c00a-152">SQL Server Express Edition veya SQL Server yüklü olduğundan ve bağlantı dizesini hizmetin uygulama yapılandırma dosyasında doğru ayarlandığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="4c00a-152">Ensure that you have installed SQL Server Express Edition or SQL Server, and that the connection string has been correctly set in the service’s application configuration file.</span></span> <span data-ttu-id="4c00a-153">Örnek bir veritabanı kullanmadan çalışacak şekilde ayarlanmış `usingSql` hizmetin uygulama yapılandırma dosyasında değeri`false`</span><span class="sxs-lookup"><span data-stu-id="4c00a-153">To run the sample without using a database, set the `usingSql` value in the service’s application configuration file to `false`</span></span>  
  
3.  <span data-ttu-id="4c00a-154">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4c00a-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4c00a-155">Çapraz makine yapılandırması için aşağıdaki yönergeleri kullanarak Dağıtılmış İşlem Düzenleyicisi etkinleştirin ve WCF işlemleri ağ desteğini etkinleştirmek için Windows SDK'sı WsatConfig.exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="4c00a-155">For cross-machine configuration, enable the Distributed Transaction Coordinator using the instructions below, and use the WsatConfig.exe tool from the Windows SDK to enable WCF Transactions network support.</span></span> <span data-ttu-id="4c00a-156">Bkz: [WS-Atomic işlem desteğini yapılandırma](http://go.microsoft.com/fwlink/?LinkId=190370) WsatConfig.exe ayarlama hakkında bilgi için.</span><span class="sxs-lookup"><span data-stu-id="4c00a-156">See [Configuring WS-Atomic Transaction Support](http://go.microsoft.com/fwlink/?LinkId=190370) for information on setting up WsatConfig.exe.</span></span>  
  
 <span data-ttu-id="4c00a-157">Aynı bilgisayarda veya farklı bilgisayarlarda örneği çalıştırmak isteyip Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) ağ işlem akışını etkinleştirmek ve etkinleştirmek için WsatConfig.exe Aracı'nı kullanmak için yapılandırmanız gerekir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] işlemleri Ağ desteği.</span><span class="sxs-lookup"><span data-stu-id="4c00a-157">Whether you run the sample on the same computer or on different computers, you must configure the Microsoft Distributed Transaction Coordinator (MSDTC) to enable network transaction flow and use the WsatConfig.exe tool to enable [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transactions network support.</span></span>  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample"></a><span data-ttu-id="4c00a-158">Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) örnek çalıştırılmasını desteklemek üzere yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="4c00a-158">To configure the Microsoft Distributed Transaction Coordinator (MSDTC) to support running the sample</span></span>  
  
1.  <span data-ttu-id="4c00a-159">Windows Server 2003 veya Windows XP çalıştıran bir hizmeti makinede MSDTC bu yönergeleri izleyerek gelen ağ işlemlerine izin verecek biçimde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="4c00a-159">On a service machine running Windows Server 2003 or Windows XP, configure MSDTC to allow incoming network transactions by following these instructions.</span></span>  
  
    1.  <span data-ttu-id="4c00a-160">Gelen **Başlat** menüsünde gidin **Denetim Masası**, ardından **Yönetimsel Araçlar**ve ardından **Bileşen Hizmetleri**.</span><span class="sxs-lookup"><span data-stu-id="4c00a-160">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2.  <span data-ttu-id="4c00a-161">Genişletme **Bileşen Hizmetleri**.</span><span class="sxs-lookup"><span data-stu-id="4c00a-161">Expand **Component Services**.</span></span> <span data-ttu-id="4c00a-162">Açık **bilgisayarlar** klasör.</span><span class="sxs-lookup"><span data-stu-id="4c00a-162">Open the **Computers** folder.</span></span>  
  
    3.  <span data-ttu-id="4c00a-163">Sağ **Bilgisayarım** seçip **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="4c00a-163">Right-click **My Computer** and select **Properties**.</span></span>  
  
    4.  <span data-ttu-id="4c00a-164">Üzerinde **MSDTC** sekmesini tıklatın, **Güvenlik Yapılandırması**.</span><span class="sxs-lookup"><span data-stu-id="4c00a-164">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    5.  <span data-ttu-id="4c00a-165">Denetleme **ağ DTC erişimi** ve **izin gelen**.</span><span class="sxs-lookup"><span data-stu-id="4c00a-165">Check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    6.  <span data-ttu-id="4c00a-166">Tıklatın **Tamam**, ardından **Evet** MSDTC hizmeti yeniden başlatmak için.</span><span class="sxs-lookup"><span data-stu-id="4c00a-166">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    7.  <span data-ttu-id="4c00a-167">İletişim kutusunu kapatmak için **Tamam** 'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="4c00a-167">Click **OK** to close the dialog box.</span></span>  
  
2.  <span data-ttu-id="4c00a-168">Windows Server 2008 veya Windows Vista çalıştıran bir hizmeti makinede MSDTC bu yönergeleri izleyerek gelen ağ işlemlerine izin verecek biçimde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="4c00a-168">On a service machine running Windows Server 2008 or Windows Vista, configure MSDTC to allow incoming network transactions by following these instructions.</span></span>  
  
    1.  <span data-ttu-id="4c00a-169">Gelen **Başlat** menüsünde gidin **Denetim Masası**, ardından **Yönetimsel Araçlar**ve ardından **Bileşen Hizmetleri**.</span><span class="sxs-lookup"><span data-stu-id="4c00a-169">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2.  <span data-ttu-id="4c00a-170">Genişletme **Bileşen Hizmetleri**.</span><span class="sxs-lookup"><span data-stu-id="4c00a-170">Expand **Component Services**.</span></span> <span data-ttu-id="4c00a-171">Açık **bilgisayarlar** klasör.</span><span class="sxs-lookup"><span data-stu-id="4c00a-171">Open the **Computers** folder.</span></span> <span data-ttu-id="4c00a-172">Seçin **Dağıtılmış İşlem Düzenleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="4c00a-172">Select **Distributed Transaction Coordinator**.</span></span>  
  
    3.  <span data-ttu-id="4c00a-173">Sağ **DTC Düzenleyicisi** seçip **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="4c00a-173">Right-click **DTC Coordinator** and select **Properties**.</span></span>  
  
    4.  <span data-ttu-id="4c00a-174">Üzerinde **güvenlik** sekmesi, onay **ağ DTC erişimi** ve **gelene izin ver**.</span><span class="sxs-lookup"><span data-stu-id="4c00a-174">On the **Security** tab, check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    5.  <span data-ttu-id="4c00a-175">Tıklatın **Tamam**, ardından **Evet** MSDTC hizmeti yeniden başlatmak için.</span><span class="sxs-lookup"><span data-stu-id="4c00a-175">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    6.  <span data-ttu-id="4c00a-176">İletişim kutusunu kapatmak için **Tamam** 'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="4c00a-176">Click **OK** to close the dialog box.</span></span>  
  
3.  <span data-ttu-id="4c00a-177">İstemci makinesinde MSDTC giden ağ işlemlerine izin verecek biçimde yapılandırın:</span><span class="sxs-lookup"><span data-stu-id="4c00a-177">On the client machine, configure MSDTC to allow outgoing network transactions:</span></span>  
  
    1.  <span data-ttu-id="4c00a-178">Gelen **Başlat** menüsünde gidin `Control Panel`, ardından **Yönetimsel Araçlar**ve ardından **Bileşen Hizmetleri**.</span><span class="sxs-lookup"><span data-stu-id="4c00a-178">From the **Start** menu, navigate to `Control Panel`, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2.  <span data-ttu-id="4c00a-179">Sağ **Bilgisayarım** seçip **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="4c00a-179">Right-click **My Computer** and select **Properties**.</span></span>  
  
    3.  <span data-ttu-id="4c00a-180">Üzerinde **MSDTC** sekmesini tıklatın, **Güvenlik Yapılandırması**.</span><span class="sxs-lookup"><span data-stu-id="4c00a-180">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    4.  <span data-ttu-id="4c00a-181">Denetleme **ağ DTC erişimi** ve **Gidene izin ver**.</span><span class="sxs-lookup"><span data-stu-id="4c00a-181">Check **Network DTC Access** and **Allow Outbound**.</span></span>  
  
    5.  <span data-ttu-id="4c00a-182">Tıklatın **Tamam**, ardından **Evet** MSDTC hizmeti yeniden başlatmak için.</span><span class="sxs-lookup"><span data-stu-id="4c00a-182">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    6.  <span data-ttu-id="4c00a-183">İletişim kutusunu kapatmak için **Tamam** 'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="4c00a-183">Click **OK** to close the dialog box.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4c00a-184">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="4c00a-184">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4c00a-185">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="4c00a-185">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4c00a-186">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="4c00a-186">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4c00a-187">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="4c00a-187">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\TransactionFlow`
