---
title: "Hizmet İşlem Davranışı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Service Transaction Behavior Sample [Windows Communication Foundation]
ms.assetid: 1a9842a3-e84d-427c-b6ac-6999cbbc2612
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a4c7c9c78b821f7457f193d24bae031d49b301ec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="service-transaction-behavior"></a><span data-ttu-id="d6048-102">Hizmet İşlem Davranışı</span><span class="sxs-lookup"><span data-stu-id="d6048-102">Service Transaction Behavior</span></span>
<span data-ttu-id="d6048-103">Bu örnek, bir istemci Eşgüdümlü işlem kullanımını ve ServiceBehaviorAttribute ve OperationBehaviorAttribute hizmet işlem davranışı denetlemek için ayarları gösterir.</span><span class="sxs-lookup"><span data-stu-id="d6048-103">This sample demonstrates the use of a client-coordinated transaction and the settings of ServiceBehaviorAttribute and OperationBehaviorAttribute to control service transaction behavior.</span></span> <span data-ttu-id="d6048-104">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) , hesap makinesi hizmetinin uygular, ancak bir veritabanı tablosu ve hesaplama işlemleri için toplam çalışan bir durum bilgisi olan gerçekleştirilen işlemler server günlüğünü korumak için genişletilir.</span><span class="sxs-lookup"><span data-stu-id="d6048-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service, but is extended to maintain a server log of the performed operations in a database table and a stateful running total for the calculator operations.</span></span> <span data-ttu-id="d6048-105">Kalıcı yazma sunucu günlüğü tablosu için bağımlı istemci işlemi tamamlanmazsa Eşgüdümlü istemci işlem - sonuca Web hizmeti işlemi veritabanına güncelleştirmeleri iletilmez sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6048-105">Persisted writes to the server log table are dependent upon the outcome of a client coordinated transaction - if the client transaction does not complete, the Web service transaction ensures that the updates to the database are not committed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d6048-106">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="d6048-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="d6048-107">Tüm işlemlerini istekleriyle akışını bir işlem gerektiren hizmet sözleşmesini tanımlar:</span><span class="sxs-lookup"><span data-stu-id="d6048-107">The contract for the service defines that all of the operations require a transaction to be flowed with requests:</span></span>  
  
```  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples",  
                    SessionMode = SessionMode.Required)]  
public interface ICalculator  
{  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Add(double n);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Subtract(double n);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Multiply(double n);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Divide(double n);  
}  
```  
  
 <span data-ttu-id="d6048-108">Gelen işlem akışını etkinleştirmek için hizmet sistem tarafından sağlanan wsHttpBinding kümesine transactionFlow özniteliği ile yapılandırılan `true`.</span><span class="sxs-lookup"><span data-stu-id="d6048-108">To enable the incoming transaction flow, the service is configured with the system-provided wsHttpBinding with the transactionFlow attribute set to `true`.</span></span> <span data-ttu-id="d6048-109">Bu bağlama birlikte çalışabilen WSAtomicTransactionOctober2004 protokolünü kullanır:</span><span class="sxs-lookup"><span data-stu-id="d6048-109">This binding uses the interoperable WSAtomicTransactionOctober2004 protocol:</span></span>  
  
```xml  
<bindings>  
  <wsHttpBinding>  
    <binding name="transactionalBinding" transactionFlow="true" />  
  </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="d6048-110">Hem başlatmadan sonra hizmet ve işlem, istemci bağlantı kapsamı içinde bu işlem birkaç hizmet işlemlerini erişir ve ardından işlem tamamlandıktan ve bağlantıyı kapatır:</span><span class="sxs-lookup"><span data-stu-id="d6048-110">After initiating both a connection to the service and a transaction, the client accesses several service operations within the scope of that transaction and then completes the transaction and closes the connection:</span></span>  
  
```  
// Create a client  
CalculatorClient client = new CalculatorClient();  
  
// Create a transaction scope with the default isolation level of Serializable  
using (TransactionScope tx = new TransactionScope())  
{  
    Console.WriteLine("Starting transaction");  
  
    // Call the Add service operation.  
    double value = 100.00D;  
    Console.WriteLine("  Adding {0}, running total={1}",  
                                        value, client.Add(value));  
  
    // Call the Subtract service operation.  
    value = 45.00D;  
    Console.WriteLine("  Subtracting {0}, running total={1}",  
                                        value, client.Subtract(value));  
  
    // Call the Multiply service operation.  
    value = 9.00D;  
    Console.WriteLine("  Multiplying by {0}, running total={1}",  
                                        value, client.Multiply(value));  
  
    // Call the Divide service operation.  
    value = 15.00D;  
    Console.WriteLine("  Dividing by {0}, running total={1}",  
                                        value, client.Divide(value));  
  
    Console.WriteLine("  Completing transaction");  
    tx.Complete();  
}  
  
Console.WriteLine("Transaction committed");  
  
// Closing the client gracefully closes the connection and cleans up resources  
client.Close();  
```  
  
 <span data-ttu-id="d6048-111">Hizmet üzerinde hizmet işlem davranışı etkileyen üç öznitelik ve bunu aşağıdaki yollarla yapın:</span><span class="sxs-lookup"><span data-stu-id="d6048-111">On the service, there are three attributes that affect the service transaction behavior, and they do so in the following ways:</span></span>  
  
-   <span data-ttu-id="d6048-112">Üzerinde `ServiceBehaviorAttribute`:</span><span class="sxs-lookup"><span data-stu-id="d6048-112">On the `ServiceBehaviorAttribute`:</span></span>  
  
    -   <span data-ttu-id="d6048-113">`TransactionTimeout` Özelliği, içinde bir işlem tamamlanmalıdır zaman aralığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d6048-113">The `TransactionTimeout` property specifies the time period within which a transaction must complete.</span></span> <span data-ttu-id="d6048-114">Bu örnekte 30 saniye olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="d6048-114">In this sample it is set to 30 seconds.</span></span>  
  
    -   <span data-ttu-id="d6048-115">`TransactionIsolationLevel` Özelliği, hizmeti destekler yalıtım düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d6048-115">The `TransactionIsolationLevel` property specifies the isolation level that the service supports.</span></span> <span data-ttu-id="d6048-116">Bu, istemcinin yalıtım düzeyi eşleştirmek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d6048-116">This is required to match the client's isolation level.</span></span>  
  
    -   <span data-ttu-id="d6048-117">`ReleaseServiceInstanceOnTransactionComplete` Özelliği, bir işlem tamamlandığında, hizmet örneği geri dönüştürüldüğünde olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d6048-117">The `ReleaseServiceInstanceOnTransactionComplete` property specifies whether the service instance is recycled when a transaction completes.</span></span> <span data-ttu-id="d6048-118">Ayarlayarak `false`, hizmet işlemi istekler genelinde aynı hizmet örneği bulundurur.</span><span class="sxs-lookup"><span data-stu-id="d6048-118">By setting it to `false`, the service maintains the same service instance across the operation requests.</span></span> <span data-ttu-id="d6048-119">Bu, çalışan toplam korumak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d6048-119">This is required to maintain the running total.</span></span> <span data-ttu-id="d6048-120">Varsa kümesine `true`, her eylem tamamlandıktan sonra yeni bir örneği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d6048-120">If set to `true`, a new instance is generated after each completed action.</span></span>  
  
    -   <span data-ttu-id="d6048-121">`TransactionAutoCompleteOnSessionClose` Özelliği, oturumu kapattığında bekleyen işlemler tamamlandıktan olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d6048-121">The `TransactionAutoCompleteOnSessionClose` property specifies whether outstanding transactions are completed when the session closes.</span></span> <span data-ttu-id="d6048-122">Ayarlayarak `false`, tek tek işlemleri ayarlayın ya da gerekli `OperationBehaviorAttribute``TransactionAutoComplete` özelliğine `true` veya açıkça bir çağrı gerektirecek şekilde `SetTransactionComplete` işlemleri tamamlamak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="d6048-122">By setting it to `false`, the individual operations are required to either set the `OperationBehaviorAttribute``TransactionAutoComplete` property to `true` or to explicitly require a call to the `SetTransactionComplete` method to complete transactions.</span></span> <span data-ttu-id="d6048-123">Bu örnek, her iki yaklaşımın gösterir.</span><span class="sxs-lookup"><span data-stu-id="d6048-123">This sample demonstrates both approaches.</span></span>  
  
-   <span data-ttu-id="d6048-124">Üzerinde `ServiceContractAttribute`:</span><span class="sxs-lookup"><span data-stu-id="d6048-124">On the `ServiceContractAttribute`:</span></span>  
  
    -   <span data-ttu-id="d6048-125">`SessionMode` Özelliği, hizmet uygun istekleri mantıksal bir oturuma karşılık gelen olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d6048-125">The `SessionMode` property specifies whether the service correlates the appropriate requests into a logical session.</span></span> <span data-ttu-id="d6048-126">Bu hizmet için OperationBehaviorAttribute TransactionAutoComplete özelliğinin ayarlandığı işlemleri içerdiğinden `false` (çarpma ve bölme), `SessionMode.Required` belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="d6048-126">Because this service includes operations where the OperationBehaviorAttribute TransactionAutoComplete property is set to `false` (Multiply and Divide), `SessionMode.Required` must be specified.</span></span> <span data-ttu-id="d6048-127">Örneğin, Çarp işlemi işlemini tamamlaması değil ve bunun yerine kullanarak tamamlamak için bir sonraki çağrı bölme kullanır. `SetTransactionComplete` yöntemi; hizmeti bu işlemleri aynı oturumunda yaşanan belirlemek mümkün olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d6048-127">For example, the Multiply operation does not complete its transaction and instead relies upon a later call to Divide to complete using the `SetTransactionComplete` method; the service must be able to determine that these operations are occurring within the same session.</span></span>  
  
-   <span data-ttu-id="d6048-128">Üzerinde `OperationBehaviorAttribute`:</span><span class="sxs-lookup"><span data-stu-id="d6048-128">On the `OperationBehaviorAttribute`:</span></span>  
  
    -   <span data-ttu-id="d6048-129">`TransactionScopeRequired` Özelliği, işlem Eylemler bir işlem kapsamı içinde gerçekleştirilip gerçekleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d6048-129">The `TransactionScopeRequired` property specifies whether the operation's actions should be executed within a transaction scope.</span></span> <span data-ttu-id="d6048-130">Bu ayar `true` bu tüm işlemleri için örnek ve, tüm işlemleri için kendi işlem istemci akar olduğundan, Eylemler, istemci işlem kapsamı içinde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="d6048-130">This is set to `true` for all operations in this sample and, because the client flows its transaction to all operations, the actions occur within the scope of that client transaction.</span></span>  
  
    -   <span data-ttu-id="d6048-131">`TransactionAutoComplete` Özelliği, İşlenmeyen özel durumlar oluşursa işlemin hangi yöntemi yürütüldükten otomatik olarak tamamlandı olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d6048-131">The `TransactionAutoComplete` property specifies whether the transaction in which the method executes is automatically completed if no unhandled exceptions occur.</span></span> <span data-ttu-id="d6048-132">Daha önce açıklandığı gibi bu ayar `true` ekleme ve çıkarma işlemleri için ancak `false` Multiply ve bölme işlemleri.</span><span class="sxs-lookup"><span data-stu-id="d6048-132">As previously described, this is set to `true` for the Add and Subtract operations but `false` for the Multiply and Divide operations.</span></span> <span data-ttu-id="d6048-133">Ekleme ve çıkarma işlemleri eylemlerini otomatik olarak tamamlamak, bölme için açık bir çağrı aracılığıyla, işlemlerini tamamlamadan `SetTransactionComplete` yöntemi Multiply eylemlerini tamamlanmazsa, ancak bunun yerine bağlı kullanır ve bir sonraki çağrı gibi gerektirir , Eylemleri tamamlaması için bölün.</span><span class="sxs-lookup"><span data-stu-id="d6048-133">The Add and Subtract operations complete their actions automatically, the Divide completes its actions through an explicit call to the `SetTransactionComplete` method, and the Multiply does not complete its actions but instead relies upon and requires a later call, such as to Divide, to complete the actions.</span></span>  
  
 <span data-ttu-id="d6048-134">Öznitelikli hizmet uygulaması aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="d6048-134">The attributed service implementation is as follows:</span></span>  
  
```  
[ServiceBehavior(  
    TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable,  
    TransactionTimeout = "00:00:30",  
    ReleaseServiceInstanceOnTransactionComplete = false,  
    TransactionAutoCompleteOnSessionClose = false)]  
public class CalculatorService : ICalculator  
{  
    double runningTotal;  
  
    public CalculatorService()  
    {  
        Console.WriteLine("Creating new service instance...");  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public double Add(double n)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Adding {0} to {1}", n, runningTotal));  
        runningTotal = runningTotal + n;  
        return runningTotal;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public double Subtract(double n)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Subtracting {0} from {1}", n, runningTotal));  
        runningTotal = runningTotal - n;  
        return runningTotal;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = false)]  
    public double Multiply(double n)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Multiplying {0} by {1}", runningTotal, n));  
        runningTotal = runningTotal * n;  
        return runningTotal;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = false)]  
    public double Divide(double n)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Dividing {0} by {1}", runningTotal, n));  
        runningTotal = runningTotal / n;  
        OperationContext.Current.SetTransactionComplete();  
        return runningTotal;  
    }  
  
    // Logging method ommitted for brevity  
}   
```  
  
 <span data-ttu-id="d6048-135">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d6048-135">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="d6048-136">İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d6048-136">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Starting transaction  
Performing calculations...  
  Adding 100, running total=100  
  Subtracting 45, running total=55  
  Multiplying by 9, running total=495  
  Dividing by 15, running total=33  
  Completing transaction  
Transaction committed  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="d6048-137">Hizmet işlemi isteklerin günlüğe yazılmasını hizmetin konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d6048-137">The logging of the service operation requests are displayed in the service's console window.</span></span> <span data-ttu-id="d6048-138">İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d6048-138">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Press <ENTER> to terminate service.  
Creating new service instance...  
  Writing row 1 to database: Adding 100 to 0  
  Writing row 2 to database: Subtracting 45 from 100  
  Writing row 3 to database: Multiplying 55 by 9  
  Writing row 4 to database: Dividing 495 by 15  
```  
  
 <span data-ttu-id="d6048-139">Çalışan toplam tutma yanı sıra unutmayın hesaplamalar hizmet örnekleri (Bu örnek için bir örnek) oluşturulmasını raporları ve işlem isteklerini bir veritabanında günlüğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="d6048-139">Note that in addition to keeping the running total of the calculations, the service reports the creation of instances (one instance for this sample) and logs the operation requests to a database.</span></span> <span data-ttu-id="d6048-140">Tüm istekleri istemcinin işlem akışı nedeniyle, tüm veritabanı işlemleri geri alınıyor bu işlemi tamamlamak için herhangi bir hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="d6048-140">Because all of the requests flow the client's transaction, any failure to complete that transaction results in all of the database operations being rolled back.</span></span> <span data-ttu-id="d6048-141">Bu gösterilen çeşitli yollarla:</span><span class="sxs-lookup"><span data-stu-id="d6048-141">This can be demonstrated in a number of ways:</span></span>  
  
-   <span data-ttu-id="d6048-142">İstemcinin çağrısına çıkışı açıklama `tx.Complete`() ve yeniden çalıştırın - bu sonuçları istemci işlemini tamamlamadan işlem kapsamı çıkılıyor.</span><span class="sxs-lookup"><span data-stu-id="d6048-142">Comment out the client's call to `tx.Complete`() and rerun - this results in the client exiting the transaction scope without completing its transaction.</span></span>  
  
-   <span data-ttu-id="d6048-143">Out bölme hizmet işlemi çağrısı - bu sonuçları tarafından başlatılan eylemi engellemek yorum işlemin tamamlanmasını çarpma ve böylece istemcinin işlem sonunda de tamamlamak başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="d6048-143">Comment out the call to the Divide service operation - this results prevent the action initiated by the Multiply operation from completing and thus the client's transaction ultimately also fails to complete.</span></span>  
  
-   <span data-ttu-id="d6048-144">İstemcinin işlem kapsamı içinde herhangi bir yere işlenmeyen bir özel durum - bu, bir işlem tamamlanmadan benzer şekilde istemci önler.</span><span class="sxs-lookup"><span data-stu-id="d6048-144">Throw an unhandled exception anywhere in the client's transaction scope - this similarly prevents the client from completing its transaction.</span></span>  
  
 <span data-ttu-id="d6048-145">Bunlardan herhangi birinde bu kapsamında gerçekleştirilen işlemler hiçbiri kaydedilir ve satır sayısı veritabanına kalıcı sonucudur değil artırın.</span><span class="sxs-lookup"><span data-stu-id="d6048-145">The result of any of these is that none of the operations performed within that scope are committed and the count of rows persisted to the database do not increment.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d6048-146">Derleme işleminin bir parçası veritabanı dosyasını bin klasörüne kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="d6048-146">As part of the build process the database file is copied to the bin folder.</span></span> <span data-ttu-id="d6048-147">Visual Studio projeye dahil dosya yerine günlüğe kalıcı satırları izlemek için veritabanı dosyası bu kopyayı bakmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="d6048-147">You must look at that copy of the database file to observe the rows that are persisted to the log rather than the file that is included in the Visual Studio project.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d6048-148">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="d6048-148">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d6048-149">SQL Server 2005 Express Edition veya SQL Server 2005'in yüklü olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="d6048-149">Ensure that you have installed SQL Server 2005 Express Edition or SQL Server 2005.</span></span> <span data-ttu-id="d6048-150">Hizmetin App.config dosyasında veritabanı `connectionString` kümesi veya etkileşimleri appSettings ayarlayarak devre dışı bırakılabilir veritabanı olabilir `usingSql` değeri `false`.</span><span class="sxs-lookup"><span data-stu-id="d6048-150">In the service's App.config file, the database `connectionString` may be set or the database interactions may be disabled by setting the appSettings `usingSql` value to `false`.</span></span>  
  
2.  <span data-ttu-id="d6048-151">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d6048-151">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="d6048-152">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d6048-152">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
 <span data-ttu-id="d6048-153">Makine genelinde örneği çalıştırırsanız, Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) ağ işlem akışını etkinleştirmek ve etkinleştirmek için WsatConfig.exe Aracı'nı kullanmak için yapılandırmanız gerekir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] işlemleri ağ desteği.</span><span class="sxs-lookup"><span data-stu-id="d6048-153">If you run the sample across machines, you must configure the Microsoft Distributed Transaction Coordinator (MSDTC) to enable network transaction flow and use the WsatConfig.exe tool to enable [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] transactions network support.</span></span>  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample-across-machines"></a><span data-ttu-id="d6048-154">Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) örnek makinelerde çalışmasını desteklemek için yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="d6048-154">To configure the Microsoft Distributed Transaction Coordinator (MSDTC) to support running the sample across machines</span></span>  
  
1.  <span data-ttu-id="d6048-155">Hizmeti makinede MSDTC gelen ağ işlemlerine izin verecek biçimde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="d6048-155">On the service machine, configure MSDTC to allow incoming network transactions.</span></span>  
  
    1.  <span data-ttu-id="d6048-156">Gelen **Başlat** menüsünde gidin **Denetim Masası**, ardından **Yönetimsel Araçlar**ve ardından **Bileşen Hizmetleri**.</span><span class="sxs-lookup"><span data-stu-id="d6048-156">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2.  <span data-ttu-id="d6048-157">Sağ **Bilgisayarım** seçip **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="d6048-157">Right-click **My Computer** and select **Properties**.</span></span>  
  
    3.  <span data-ttu-id="d6048-158">Üzerinde **MSDTC** sekmesini tıklatın, **Güvenlik Yapılandırması**.</span><span class="sxs-lookup"><span data-stu-id="d6048-158">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    4.  <span data-ttu-id="d6048-159">Denetleme **ağ DTC erişimi** ve **izin gelen**.</span><span class="sxs-lookup"><span data-stu-id="d6048-159">Check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    5.  <span data-ttu-id="d6048-160">Tıklatın **Evet** MS DTC hizmetini yeniden başlatın ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="d6048-160">Click **Yes** to restart the MS DTC service and then click **OK**.</span></span>  
  
    6.  <span data-ttu-id="d6048-161">İletişim kutusunu kapatmak için **Tamam** 'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="d6048-161">Click **OK** to close the dialog box.</span></span>  
  
2.  <span data-ttu-id="d6048-162">Hizmet makine ve istemci makine Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) dışarıda tutulan uygulamalar listesine eklemek için Windows Güvenlik Duvarı yapılandırın:</span><span class="sxs-lookup"><span data-stu-id="d6048-162">On the service machine and the client machine, configure the Windows Firewall to include the Microsoft Distributed Transaction Coordinator (MSDTC) to the list of excepted applications:</span></span>  
  
    1.  <span data-ttu-id="d6048-163">Windows Güvenlik Duvarı uygulama Denetim Masası'ndan çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d6048-163">Run the Windows Firewall application from Control Panel.</span></span>  
  
    2.  <span data-ttu-id="d6048-164">Gelen **özel durumları** sekmesini tıklatın, **Program Ekle**.</span><span class="sxs-lookup"><span data-stu-id="d6048-164">From the **Exceptions** tab, click **Add Program**.</span></span>  
  
    3.  <span data-ttu-id="d6048-165">C:\WINDOWS\System32 klasöre göz atın.</span><span class="sxs-lookup"><span data-stu-id="d6048-165">Browse to the folder C:\WINDOWS\System32.</span></span>  
  
    4.  <span data-ttu-id="d6048-166">MSDTC.exe tıklatıp **açık**.</span><span class="sxs-lookup"><span data-stu-id="d6048-166">Select Msdtc.exe and click **Open**.</span></span>  
  
    5.  <span data-ttu-id="d6048-167">Tıklatın **Tamam** kapatmak için **Program Ekle** iletişim kutusu ve tıklatın **Tamam** Windows Güvenlik Duvarı uygulamasını kapatın.</span><span class="sxs-lookup"><span data-stu-id="d6048-167">Click **OK** to close the **Add Program** dialog box, and click **OK** again to close the Windows Firewall applet.</span></span>  
  
3.  <span data-ttu-id="d6048-168">İstemci makinesinde MSDTC giden ağ işlemlerine izin verecek biçimde yapılandırın:</span><span class="sxs-lookup"><span data-stu-id="d6048-168">On the client machine, configure MSDTC to allow outgoing network transactions:</span></span>  
  
    1.  <span data-ttu-id="d6048-169">Gelen **Başlat** menüsünde gidin **Denetim Masası**, ardından **Yönetimsel Araçlar**ve ardından **Bileşen Hizmetleri**.</span><span class="sxs-lookup"><span data-stu-id="d6048-169">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2.  <span data-ttu-id="d6048-170">Sağ **Bilgisayarım** seçip **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="d6048-170">Right-click **My Computer** and select **Properties**.</span></span>  
  
    3.  <span data-ttu-id="d6048-171">Üzerinde **MSDTC** sekmesini tıklatın, **Güvenlik Yapılandırması**.</span><span class="sxs-lookup"><span data-stu-id="d6048-171">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    4.  <span data-ttu-id="d6048-172">Denetleme **ağ DTC erişimi** ve **Gidene izin ver**.</span><span class="sxs-lookup"><span data-stu-id="d6048-172">Check **Network DTC Access** and **Allow Outbound**.</span></span>  
  
    5.  <span data-ttu-id="d6048-173">Tıklatın **Evet** MS DTC hizmetini yeniden başlatın ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="d6048-173">Click **Yes** to restart the MS DTC service and then click **OK**.</span></span>  
  
    6.  <span data-ttu-id="d6048-174">İletişim kutusunu kapatmak için **Tamam** 'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="d6048-174">Click **OK** to close the dialog box.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d6048-175">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="d6048-175">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d6048-176">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d6048-176">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d6048-177">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="d6048-177">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d6048-178">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="d6048-178">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Transactions`  
  
## <a name="see-also"></a><span data-ttu-id="d6048-179">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d6048-179">See Also</span></span>
