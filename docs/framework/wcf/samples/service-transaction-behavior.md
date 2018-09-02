---
title: Hizmet İşlem Davranışı
ms.date: 03/30/2017
helpviewer_keywords:
- Service Transaction Behavior Sample [Windows Communication Foundation]
ms.assetid: 1a9842a3-e84d-427c-b6ac-6999cbbc2612
ms.openlocfilehash: 69f65ca833dc9a0f719541733be9e6066db37f6e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43391856"
---
# <a name="service-transaction-behavior"></a><span data-ttu-id="59afc-102">Hizmet İşlem Davranışı</span><span class="sxs-lookup"><span data-stu-id="59afc-102">Service Transaction Behavior</span></span>
<span data-ttu-id="59afc-103">Bu örnek, bir istemci Eşgüdümlü işlem kullanımı ve ServiceBehaviorAttribute ve OperationBehaviorAttribute hizmet işlem davranışı denetlemek için ayarları gösterir.</span><span class="sxs-lookup"><span data-stu-id="59afc-103">This sample demonstrates the use of a client-coordinated transaction and the settings of ServiceBehaviorAttribute and OperationBehaviorAttribute to control service transaction behavior.</span></span> <span data-ttu-id="59afc-104">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) , hesaplayıcı hizmet uygular, ancak gerçekleştirilen işlemlerin bir veritabanı tablosu ve hesap makinesi işlemleri için toplam çalışan bir durum bilgisi olan bir sunucu günlüğü korumak için genişletilir.</span><span class="sxs-lookup"><span data-stu-id="59afc-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service, but is extended to maintain a server log of the performed operations in a database table and a stateful running total for the calculator operations.</span></span> <span data-ttu-id="59afc-105">Sunucu günlüğü tablosu kalıcı Yazar bağımlı istemci işlemi tamamlanmazsa, bir istemci Eşgüdümlü işlem - sonucunu Web hizmeti işlemi güncelleştirmeleri veritabanına kaydedilmiş olmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="59afc-105">Persisted writes to the server log table are dependent upon the outcome of a client coordinated transaction - if the client transaction does not complete, the Web service transaction ensures that the updates to the database are not committed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="59afc-106">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="59afc-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="59afc-107">Tüm işlemlerin isteklerle akışını bir işlem gerektiren hizmet sözleşmesini tanımlar:</span><span class="sxs-lookup"><span data-stu-id="59afc-107">The contract for the service defines that all of the operations require a transaction to be flowed with requests:</span></span>  
  
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
  
 <span data-ttu-id="59afc-108">Gelen işlem akışını etkinleştirmek için hizmeti sistem tarafından sağlanan wsHttpBinding kümesine transactionFlow özniteliğine sahip yapılandırılmış `true`.</span><span class="sxs-lookup"><span data-stu-id="59afc-108">To enable the incoming transaction flow, the service is configured with the system-provided wsHttpBinding with the transactionFlow attribute set to `true`.</span></span> <span data-ttu-id="59afc-109">Bu bağlama birlikte çalışabilen WSAtomicTransactionOctober2004 protokolünü kullanır:</span><span class="sxs-lookup"><span data-stu-id="59afc-109">This binding uses the interoperable WSAtomicTransactionOctober2004 protocol:</span></span>  
  
```xml  
<bindings>  
  <wsHttpBinding>  
    <binding name="transactionalBinding" transactionFlow="true" />  
  </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="59afc-110">Her iki başlatmadan sonra hizmet ve işlem, istemci bağlantısı bu işlemin kapsamı içinde birkaç hizmet işlemleri erişen hareketi tamamlar ve bağlantıyı kapatır:</span><span class="sxs-lookup"><span data-stu-id="59afc-110">After initiating both a connection to the service and a transaction, the client accesses several service operations within the scope of that transaction and then completes the transaction and closes the connection:</span></span>  
  
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
  
 <span data-ttu-id="59afc-111">Hizmet, hizmet işlem davranışı etkileyen üç öznitelikleri vardır ve aşağıdaki yollarla bunu:</span><span class="sxs-lookup"><span data-stu-id="59afc-111">On the service, there are three attributes that affect the service transaction behavior, and they do so in the following ways:</span></span>  
  
-   <span data-ttu-id="59afc-112">Üzerinde `ServiceBehaviorAttribute`:</span><span class="sxs-lookup"><span data-stu-id="59afc-112">On the `ServiceBehaviorAttribute`:</span></span>  
  
    -   <span data-ttu-id="59afc-113">`TransactionTimeout` Özelliği, içinde bir işlem tamamlamalısınız süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="59afc-113">The `TransactionTimeout` property specifies the time period within which a transaction must complete.</span></span> <span data-ttu-id="59afc-114">Bu örnekte, 30 saniye olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="59afc-114">In this sample it is set to 30 seconds.</span></span>  
  
    -   <span data-ttu-id="59afc-115">`TransactionIsolationLevel` Özellik hizmetinin desteklediği yalıtım düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="59afc-115">The `TransactionIsolationLevel` property specifies the isolation level that the service supports.</span></span> <span data-ttu-id="59afc-116">Bu, istemcinin yalıtım düzeyi eşleştirmek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="59afc-116">This is required to match the client's isolation level.</span></span>  
  
    -   <span data-ttu-id="59afc-117">`ReleaseServiceInstanceOnTransactionComplete` Özelliği, bir işlem tamamlandığında, hizmet örneği geri olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="59afc-117">The `ReleaseServiceInstanceOnTransactionComplete` property specifies whether the service instance is recycled when a transaction completes.</span></span> <span data-ttu-id="59afc-118">Ayarlayarak `false`, hizmetin işlemi istekler genelinde aynı hizmet örneği tutar.</span><span class="sxs-lookup"><span data-stu-id="59afc-118">By setting it to `false`, the service maintains the same service instance across the operation requests.</span></span> <span data-ttu-id="59afc-119">Değişen Toplam korumak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="59afc-119">This is required to maintain the running total.</span></span> <span data-ttu-id="59afc-120">Varsa kümesine `true`, her eylem tamamlandıktan sonra yeni bir örneği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="59afc-120">If set to `true`, a new instance is generated after each completed action.</span></span>  
  
    -   <span data-ttu-id="59afc-121">`TransactionAutoCompleteOnSessionClose` Özelliği, bekleyen işlemler oturumu kapattığında tamamlanıp tamamlanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="59afc-121">The `TransactionAutoCompleteOnSessionClose` property specifies whether outstanding transactions are completed when the session closes.</span></span> <span data-ttu-id="59afc-122">Ayarlayarak `false`, tek işlemler için ayarlayın ya da gerekli `OperationBehaviorAttribute``TransactionAutoComplete` özelliğini `true` veya açıkça bir çağrı gerektirecek şekilde `SetTransactionComplete` işlemleri tamamlamak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="59afc-122">By setting it to `false`, the individual operations are required to either set the `OperationBehaviorAttribute``TransactionAutoComplete` property to `true` or to explicitly require a call to the `SetTransactionComplete` method to complete transactions.</span></span> <span data-ttu-id="59afc-123">Bu örnek iki yaklaşımı gösterir.</span><span class="sxs-lookup"><span data-stu-id="59afc-123">This sample demonstrates both approaches.</span></span>  
  
-   <span data-ttu-id="59afc-124">Üzerinde `ServiceContractAttribute`:</span><span class="sxs-lookup"><span data-stu-id="59afc-124">On the `ServiceContractAttribute`:</span></span>  
  
    -   <span data-ttu-id="59afc-125">`SessionMode` Özelliği, hizmet, mantıksal bir oturuma uygun istekleri ilişkilendiren olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="59afc-125">The `SessionMode` property specifies whether the service correlates the appropriate requests into a logical session.</span></span> <span data-ttu-id="59afc-126">Bu hizmet işlemleri için OperationBehaviorAttribute TransactionAutoComplete özelliğinin ayarlandığı içerdiğinden `false` (çarpma ve bölme), `SessionMode.Required` belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="59afc-126">Because this service includes operations where the OperationBehaviorAttribute TransactionAutoComplete property is set to `false` (Multiply and Divide), `SessionMode.Required` must be specified.</span></span> <span data-ttu-id="59afc-127">Örneğin, birden çok kez işlemi kendi işlem tamamlanmaz ve bunun yerine kullanarak tamamlamak için bir sonraki çağrı sırasında bölme kullanır `SetTransactionComplete` yöntemi; hizmeti bu işlemleri aynı oturumunda oluşan belirlemek mümkün olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="59afc-127">For example, the Multiply operation does not complete its transaction and instead relies upon a later call to Divide to complete using the `SetTransactionComplete` method; the service must be able to determine that these operations are occurring within the same session.</span></span>  
  
-   <span data-ttu-id="59afc-128">Üzerinde `OperationBehaviorAttribute`:</span><span class="sxs-lookup"><span data-stu-id="59afc-128">On the `OperationBehaviorAttribute`:</span></span>  
  
    -   <span data-ttu-id="59afc-129">`TransactionScopeRequired` Özelliği, işlem eylemlerini bir işlem kapsamında yürütülüp yürütülmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="59afc-129">The `TransactionScopeRequired` property specifies whether the operation's actions should be executed within a transaction scope.</span></span> <span data-ttu-id="59afc-130">Bu ayar `true` bu tüm işlemler için örnek ve istemci için tüm işlemleri, işlem akışları çünkü bu istemci işlemi kapsamında eylemler gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="59afc-130">This is set to `true` for all operations in this sample and, because the client flows its transaction to all operations, the actions occur within the scope of that client transaction.</span></span>  
  
    -   <span data-ttu-id="59afc-131">`TransactionAutoComplete` Özelliği, İşlenmeyen özel durumlar oluşursa yöntemi yürütür işlem otomatik olarak tamamlanıp tamamlanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="59afc-131">The `TransactionAutoComplete` property specifies whether the transaction in which the method executes is automatically completed if no unhandled exceptions occur.</span></span> <span data-ttu-id="59afc-132">Daha önce açıklandığı gibi bu ayar `true` ekleme ve çıkarma işlemlerinde ancak `false` Multiply ve bölme işlemleri için.</span><span class="sxs-lookup"><span data-stu-id="59afc-132">As previously described, this is set to `true` for the Add and Subtract operations but `false` for the Multiply and Divide operations.</span></span> <span data-ttu-id="59afc-133">Eylemlerini otomatik olarak ekleme ve çıkarma işlemleri tamamlamak, açık bir çağrı aracılığıyla eylemlerini Böl tamamlandıktan `SetTransactionComplete` yöntemi Multiply eylemlerini tamamlamak değil ancak bunun yerine bağlı kullanır ve bir sonraki çağrı gibi gerektirir Bölme, işlemleri tamamlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="59afc-133">The Add and Subtract operations complete their actions automatically, the Divide completes its actions through an explicit call to the `SetTransactionComplete` method, and the Multiply does not complete its actions but instead relies upon and requires a later call, such as to Divide, to complete the actions.</span></span>  
  
 <span data-ttu-id="59afc-134">Öznitelikli hizmet uygulaması aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="59afc-134">The attributed service implementation is as follows:</span></span>  
  
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
  
 <span data-ttu-id="59afc-135">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="59afc-135">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="59afc-136">İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="59afc-136">Press ENTER in the client window to shut down the client.</span></span>  
  
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
  
 <span data-ttu-id="59afc-137">Hizmet işlemi isteklerini günlüğe hizmet konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="59afc-137">The logging of the service operation requests are displayed in the service's console window.</span></span> <span data-ttu-id="59afc-138">İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="59afc-138">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Press <ENTER> to terminate service.  
Creating new service instance...  
  Writing row 1 to database: Adding 100 to 0  
  Writing row 2 to database: Subtracting 45 from 100  
  Writing row 3 to database: Multiplying 55 by 9  
  Writing row 4 to database: Dividing 495 by 15  
```  
  
 <span data-ttu-id="59afc-139">Değişen Toplam tutmanın yanı sıra dikkat edin, hesaplamaların hizmet örnekleri (Bu örnek için bir örnek) oluşturulmasını raporları ve işlem istekleri bir veritabanına kaydeder.</span><span class="sxs-lookup"><span data-stu-id="59afc-139">Note that in addition to keeping the running total of the calculations, the service reports the creation of instances (one instance for this sample) and logs the operation requests to a database.</span></span> <span data-ttu-id="59afc-140">Tüm isteklerin istemcinin işlem akış olduğundan, bu işlemi tamamlamak için herhangi bir hata geri alınan veritabanı işlemlerinin tümünde sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="59afc-140">Because all of the requests flow the client's transaction, any failure to complete that transaction results in all of the database operations being rolled back.</span></span> <span data-ttu-id="59afc-141">Bu gösterildiği çeşitli şekillerde:</span><span class="sxs-lookup"><span data-stu-id="59afc-141">This can be demonstrated in a number of ways:</span></span>  
  
-   <span data-ttu-id="59afc-142">İstemcinin çağrısına yorum `tx.Complete`() ve yeniden çalıştır - bu sonuçları istemci kendi işlem tamamlamadan işlem kapsamı çıkılıyor.</span><span class="sxs-lookup"><span data-stu-id="59afc-142">Comment out the client's call to `tx.Complete`() and rerun - this results in the client exiting the transaction scope without completing its transaction.</span></span>  
  
-   <span data-ttu-id="59afc-143">Açıklama çıkış bölme hizmet işlemi çağrısı - eylemi tarafından başlatılan bu sonuçları önlemek çarpma işleminin tamamlanmasını ve bu nedenle istemcinin işlem sonuçta da tamamlamak başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="59afc-143">Comment out the call to the Divide service operation - this results prevent the action initiated by the Multiply operation from completing and thus the client's transaction ultimately also fails to complete.</span></span>  
  
-   <span data-ttu-id="59afc-144">İstemci işlem kapsamı içindeki herhangi bir yere işlenmeyen bir özel durum - bu benzer şekilde istemci kendi işlem önler.</span><span class="sxs-lookup"><span data-stu-id="59afc-144">Throw an unhandled exception anywhere in the client's transaction scope - this similarly prevents the client from completing its transaction.</span></span>  
  
 <span data-ttu-id="59afc-145">Bu kapsam içinde gerçekleştirilen işlemleri hiçbiri kararlıyız ve veritabanında satır sayısı kalıcı bunlardan herhangi birinde sonucudur değil artırın.</span><span class="sxs-lookup"><span data-stu-id="59afc-145">The result of any of these is that none of the operations performed within that scope are committed and the count of rows persisted to the database do not increment.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="59afc-146">Yapı işleminin bir parçası olarak veritabanı dosyasını bin klasörüne kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="59afc-146">As part of the build process the database file is copied to the bin folder.</span></span> <span data-ttu-id="59afc-147">Bu Visual Studio projesinde bulunan dosya yerine günlüğe kalıcı satırları gözlemlemek için veritabanı dosyasının kopyasını gözden geçirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="59afc-147">You must look at that copy of the database file to observe the rows that are persisted to the log rather than the file that is included in the Visual Studio project.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="59afc-148">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="59afc-148">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="59afc-149">SQL Server 2005 Express Edition veya SQL Server 2005'in yüklü olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="59afc-149">Ensure that you have installed SQL Server 2005 Express Edition or SQL Server 2005.</span></span> <span data-ttu-id="59afc-150">Hizmetin App.config dosyasında, veritabanı `connectionString` kümesi veya etkileşimler appSettings ayarlayarak devre dışı bırakılabilir veritabanı `usingSql` değerini `false`.</span><span class="sxs-lookup"><span data-stu-id="59afc-150">In the service's App.config file, the database `connectionString` may be set or the database interactions may be disabled by setting the appSettings `usingSql` value to `false`.</span></span>  
  
2.  <span data-ttu-id="59afc-151">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="59afc-151">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="59afc-152">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="59afc-152">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
 <span data-ttu-id="59afc-153">Makineler arasında örneği çalıştırırsanız, Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) ağ işlem akışını etkinleştirme ve Windows Communication Foundation (WCF) işlemleri ağ etkinleştirmek için WsatConfig.exe Aracı'nı kullanmak için yapılandırmanız gerekir destekler.</span><span class="sxs-lookup"><span data-stu-id="59afc-153">If you run the sample across machines, you must configure the Microsoft Distributed Transaction Coordinator (MSDTC) to enable network transaction flow and use the WsatConfig.exe tool to enable Windows Communication Foundation (WCF) transactions network support.</span></span>  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample-across-machines"></a><span data-ttu-id="59afc-154">Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) örnek makinelerde çalışan destekleyecek şekilde yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="59afc-154">To configure the Microsoft Distributed Transaction Coordinator (MSDTC) to support running the sample across machines</span></span>  
  
1.  <span data-ttu-id="59afc-155">Hizmeti makinede MSDTC gelen ağ işlemleri izin verecek şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="59afc-155">On the service machine, configure MSDTC to allow incoming network transactions.</span></span>  
  
    1.  <span data-ttu-id="59afc-156">Gelen **Başlat** menüsünde gidin **Denetim Masası**, ardından **Yönetimsel Araçlar**, ardından **Bileşen Hizmetleri**.</span><span class="sxs-lookup"><span data-stu-id="59afc-156">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2.  <span data-ttu-id="59afc-157">Sağ **Bilgisayarım** seçip **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="59afc-157">Right-click **My Computer** and select **Properties**.</span></span>  
  
    3.  <span data-ttu-id="59afc-158">Üzerinde **MSDTC** sekmesinde **Güvenlik Yapılandırması**.</span><span class="sxs-lookup"><span data-stu-id="59afc-158">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    4.  <span data-ttu-id="59afc-159">Denetleme **ağ DTC erişimi** ve **izin gelen**.</span><span class="sxs-lookup"><span data-stu-id="59afc-159">Check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    5.  <span data-ttu-id="59afc-160">Tıklayın **Evet** MS DTC hizmetini yeniden başlatın ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="59afc-160">Click **Yes** to restart the MS DTC service and then click **OK**.</span></span>  
  
    6.  <span data-ttu-id="59afc-161">İletişim kutusunu kapatmak için **Tamam** 'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="59afc-161">Click **OK** to close the dialog box.</span></span>  
  
2.  <span data-ttu-id="59afc-162">Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) hariç tutulan uygulamalar listesine eklemek için Windows Güvenlik Duvarı hizmeti makinesi ve istemci makine üzerinde yapılandırın:</span><span class="sxs-lookup"><span data-stu-id="59afc-162">On the service machine and the client machine, configure the Windows Firewall to include the Microsoft Distributed Transaction Coordinator (MSDTC) to the list of excepted applications:</span></span>  
  
    1.  <span data-ttu-id="59afc-163">Windows Güvenlik Duvarı uygulaması Denetim Masası'ndan çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="59afc-163">Run the Windows Firewall application from Control Panel.</span></span>  
  
    2.  <span data-ttu-id="59afc-164">Gelen **özel durumları** sekmesinde **Program Ekle**.</span><span class="sxs-lookup"><span data-stu-id="59afc-164">From the **Exceptions** tab, click **Add Program**.</span></span>  
  
    3.  <span data-ttu-id="59afc-165">C:\WINDOWS\System32 klasöre göz atın.</span><span class="sxs-lookup"><span data-stu-id="59afc-165">Browse to the folder C:\WINDOWS\System32.</span></span>  
  
    4.  <span data-ttu-id="59afc-166">MSDTC.exe seçip tıklayın **açık**.</span><span class="sxs-lookup"><span data-stu-id="59afc-166">Select Msdtc.exe and click **Open**.</span></span>  
  
    5.  <span data-ttu-id="59afc-167">Tıklayın **Tamam** kapatmak için **Program Ekle** iletişim kutusu seçeneğine tıklayıp **Tamam** Windows Güvenlik Duvarı uygulamasını kapatın.</span><span class="sxs-lookup"><span data-stu-id="59afc-167">Click **OK** to close the **Add Program** dialog box, and click **OK** again to close the Windows Firewall applet.</span></span>  
  
3.  <span data-ttu-id="59afc-168">İstemci makinesinde MSDTC giden ağ işlemleri izin verecek şekilde yapılandırın:</span><span class="sxs-lookup"><span data-stu-id="59afc-168">On the client machine, configure MSDTC to allow outgoing network transactions:</span></span>  
  
    1.  <span data-ttu-id="59afc-169">Gelen **Başlat** menüsünde gidin **Denetim Masası**, ardından **Yönetimsel Araçlar**, ardından **Bileşen Hizmetleri**.</span><span class="sxs-lookup"><span data-stu-id="59afc-169">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2.  <span data-ttu-id="59afc-170">Sağ **Bilgisayarım** seçip **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="59afc-170">Right-click **My Computer** and select **Properties**.</span></span>  
  
    3.  <span data-ttu-id="59afc-171">Üzerinde **MSDTC** sekmesinde **Güvenlik Yapılandırması**.</span><span class="sxs-lookup"><span data-stu-id="59afc-171">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    4.  <span data-ttu-id="59afc-172">Denetleme **ağ DTC erişimi** ve **Gidene izin ver**.</span><span class="sxs-lookup"><span data-stu-id="59afc-172">Check **Network DTC Access** and **Allow Outbound**.</span></span>  
  
    5.  <span data-ttu-id="59afc-173">Tıklayın **Evet** MS DTC hizmetini yeniden başlatın ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="59afc-173">Click **Yes** to restart the MS DTC service and then click **OK**.</span></span>  
  
    6.  <span data-ttu-id="59afc-174">İletişim kutusunu kapatmak için **Tamam** 'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="59afc-174">Click **OK** to close the dialog box.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="59afc-175">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="59afc-175">The samples may already be installed on your machine.</span></span> <span data-ttu-id="59afc-176">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="59afc-176">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="59afc-177">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="59afc-177">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="59afc-178">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="59afc-178">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Transactions`  
  
## <a name="see-also"></a><span data-ttu-id="59afc-179">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="59afc-179">See Also</span></span>
