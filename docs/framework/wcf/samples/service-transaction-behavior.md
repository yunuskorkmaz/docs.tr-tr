---
description: 'Daha fazla bilgi edinin: hizmet Işlem davranışı'
title: Hizmet İşlem Davranışı
ms.date: 03/30/2017
helpviewer_keywords:
- Service Transaction Behavior Sample [Windows Communication Foundation]
ms.assetid: 1a9842a3-e84d-427c-b6ac-6999cbbc2612
ms.openlocfilehash: 1f8b76de250ef87ec5ca2d4ea4353a9a28bac248
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793070"
---
# <a name="service-transaction-behavior"></a><span data-ttu-id="fb81c-103">Hizmet İşlem Davranışı</span><span class="sxs-lookup"><span data-stu-id="fb81c-103">Service Transaction Behavior</span></span>

<span data-ttu-id="fb81c-104">Bu örnek, hizmet işlem davranışını denetlemek için istemci ile eşgüdümlü bir işlemin ve ServiceBehaviorAttribute ve OperationBehaviorAttribute ayarlarının kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fb81c-104">This sample demonstrates the use of a client-coordinated transaction and the settings of ServiceBehaviorAttribute and OperationBehaviorAttribute to control service transaction behavior.</span></span> <span data-ttu-id="fb81c-105">Bu örnek, bir Hesaplayıcı hizmeti uygulayan [kullanmaya](getting-started-sample.md) Başlarken hizmetini temel alır, ancak bir veritabanı tablosunda gerçekleştirilen işlemlerin sunucu günlüğünü ve Hesaplayıcı işlemleri için durum bilgisi olan bir çalışan toplamı korumak üzere genişletilir.</span><span class="sxs-lookup"><span data-stu-id="fb81c-105">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service, but is extended to maintain a server log of the performed operations in a database table and a stateful running total for the calculator operations.</span></span> <span data-ttu-id="fb81c-106">Sunucu günlüğü tablosuna kalıcı yazma işlemleri, istemci ile eşgüdümlü bir işlemin sonucuna bağımlıdır. istemci işlemi tamamlanmazsa, Web hizmeti işlemi veritabanı güncelleştirmelerinin yürütülmemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="fb81c-106">Persisted writes to the server log table are dependent upon the outcome of a client coordinated transaction - if the client transaction does not complete, the Web service transaction ensures that the updates to the database are not committed.</span></span>

> [!NOTE]
> <span data-ttu-id="fb81c-107">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="fb81c-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="fb81c-108">Hizmetin sözleşmesi, tüm işlemlerin isteklerle birlikte akışını gerektirdiğini tanımlar:</span><span class="sxs-lookup"><span data-stu-id="fb81c-108">The contract for the service defines that all of the operations require a transaction to be flowed with requests:</span></span>

```csharp
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

<span data-ttu-id="fb81c-109">Gelen işlem akışını etkinleştirmek için hizmet, transactionFlow özniteliği olarak ayarlanmış sistem tarafından sağlanmış wsHttpBinding ile yapılandırılır `true` .</span><span class="sxs-lookup"><span data-stu-id="fb81c-109">To enable the incoming transaction flow, the service is configured with the system-provided wsHttpBinding with the transactionFlow attribute set to `true`.</span></span> <span data-ttu-id="fb81c-110">Bu bağlama, birlikte çalışabilen WSAtomicTransactionOctober2004 protokolünü kullanır:</span><span class="sxs-lookup"><span data-stu-id="fb81c-110">This binding uses the interoperable WSAtomicTransactionOctober2004 protocol:</span></span>

```xml
<bindings>
  <wsHttpBinding>
    <binding name="transactionalBinding" transactionFlow="true" />
  </wsHttpBinding>
</bindings>
```

<span data-ttu-id="fb81c-111">Hem hizmet hem de bir işlem bağlantısı başlattıktan sonra istemci, bu işlemin kapsamındaki çeşitli hizmet işlemlerine erişir ve sonra işlemi tamamlar ve bağlantıyı kapatır:</span><span class="sxs-lookup"><span data-stu-id="fb81c-111">After initiating both a connection to the service and a transaction, the client accesses several service operations within the scope of that transaction and then completes the transaction and closes the connection:</span></span>

```csharp
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

<span data-ttu-id="fb81c-112">Hizmette, hizmet işlem davranışını etkileyen üç öznitelik vardır ve bunu aşağıdaki yollarla yapabilirler:</span><span class="sxs-lookup"><span data-stu-id="fb81c-112">On the service, there are three attributes that affect the service transaction behavior, and they do so in the following ways:</span></span>

- <span data-ttu-id="fb81c-113">Üzerinde `ServiceBehaviorAttribute` :</span><span class="sxs-lookup"><span data-stu-id="fb81c-113">On the `ServiceBehaviorAttribute`:</span></span>

  - <span data-ttu-id="fb81c-114">`TransactionTimeout`Özelliği, bir işlemin tamamlaması gereken zaman dilimini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fb81c-114">The `TransactionTimeout` property specifies the time period within which a transaction must complete.</span></span> <span data-ttu-id="fb81c-115">Bu örnekte, 30 saniyeye ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="fb81c-115">In this sample it is set to 30 seconds.</span></span>

  - <span data-ttu-id="fb81c-116">`TransactionIsolationLevel`Özelliği, hizmetin desteklediği yalıtım düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fb81c-116">The `TransactionIsolationLevel` property specifies the isolation level that the service supports.</span></span> <span data-ttu-id="fb81c-117">İstemcinin yalıtım düzeyini eşleştirmek için bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="fb81c-117">This is required to match the client's isolation level.</span></span>

  - <span data-ttu-id="fb81c-118">`ReleaseServiceInstanceOnTransactionComplete`Özelliği, bir işlem tamamlandığında hizmet örneğinin geri dönüştürülüp dönüştürülmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fb81c-118">The `ReleaseServiceInstanceOnTransactionComplete` property specifies whether the service instance is recycled when a transaction completes.</span></span> <span data-ttu-id="fb81c-119">Hizmet, olarak ayarlanarak `false` , işlem istekleri genelinde aynı hizmet örneğini tutar.</span><span class="sxs-lookup"><span data-stu-id="fb81c-119">By setting it to `false`, the service maintains the same service instance across the operation requests.</span></span> <span data-ttu-id="fb81c-120">Bu, toplam çalışma sağlamak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="fb81c-120">This is required to maintain the running total.</span></span> <span data-ttu-id="fb81c-121">Olarak ayarlanırsa `true` , tamamlanan her eylemden sonra yeni bir örnek oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="fb81c-121">If set to `true`, a new instance is generated after each completed action.</span></span>

  - <span data-ttu-id="fb81c-122">`TransactionAutoCompleteOnSessionClose`Özelliği, oturum kapandığında bekleyen işlemlerin tamamlanıp tamamlanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fb81c-122">The `TransactionAutoCompleteOnSessionClose` property specifies whether outstanding transactions are completed when the session closes.</span></span> <span data-ttu-id="fb81c-123">`false`' I ' a ayarlayarak, tek tek işlemler, <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete?displayProperty=nameWithType> özelliği, `true` işlemleri tamamlamaya yönelik bir yönteme çağrı yapmak ya da açıkça gerektirmek için gerekir <xref:System.ServiceModel.OperationContext.SetTransactionComplete?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fb81c-123">By setting it to `false`, the individual operations are required to either set the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete?displayProperty=nameWithType> property to `true` or to explicitly require a call to the <xref:System.ServiceModel.OperationContext.SetTransactionComplete?displayProperty=nameWithType> method to complete transactions.</span></span> <span data-ttu-id="fb81c-124">Bu örnekte her iki yaklaşım da gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fb81c-124">This sample demonstrates both approaches.</span></span>

- <span data-ttu-id="fb81c-125">Üzerinde `ServiceContractAttribute` :</span><span class="sxs-lookup"><span data-stu-id="fb81c-125">On the `ServiceContractAttribute`:</span></span>

  - <span data-ttu-id="fb81c-126">`SessionMode`Özelliği, hizmetin uygun istekleri mantıksal bir oturumla karşılıklı olarak içerip içermediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fb81c-126">The `SessionMode` property specifies whether the service correlates the appropriate requests into a logical session.</span></span> <span data-ttu-id="fb81c-127">Bu hizmet, OperationBehaviorAttribute TransactionAutoComplete özelliğinin `false` (çarp ve Böl) olarak ayarlandığı işlemleri içerdiğinden, `SessionMode.Required` belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="fb81c-127">Because this service includes operations where the OperationBehaviorAttribute TransactionAutoComplete property is set to `false` (Multiply and Divide), `SessionMode.Required` must be specified.</span></span> <span data-ttu-id="fb81c-128">Örneğin, çarpma işlemi, işlemini tamamlamaz ve bunun yerine yöntemi kullanılarak tamamlamaya bölmek için daha sonraki bir çağrıya bağımlıdır `SetTransactionComplete` ; hizmet, bu işlemlerin aynı oturum içinde gerçekleştiğini belirleyebilmelidir.</span><span class="sxs-lookup"><span data-stu-id="fb81c-128">For example, the Multiply operation does not complete its transaction and instead relies upon a later call to Divide to complete using the `SetTransactionComplete` method; the service must be able to determine that these operations are occurring within the same session.</span></span>

- <span data-ttu-id="fb81c-129">Üzerinde `OperationBehaviorAttribute` :</span><span class="sxs-lookup"><span data-stu-id="fb81c-129">On the `OperationBehaviorAttribute`:</span></span>

  - <span data-ttu-id="fb81c-130">`TransactionScopeRequired`Özelliği işlemin işlemlerinin bir işlem kapsamı içinde yürütülüp yürütülmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fb81c-130">The `TransactionScopeRequired` property specifies whether the operation's actions should be executed within a transaction scope.</span></span> <span data-ttu-id="fb81c-131">Bu, `true` Bu örnekteki tüm işlemler için olarak ayarlanır ve istemci, işlemini tüm işlemlere akdığı için, bu istemci işleminin kapsamında eylemler oluşur.</span><span class="sxs-lookup"><span data-stu-id="fb81c-131">This is set to `true` for all operations in this sample and, because the client flows its transaction to all operations, the actions occur within the scope of that client transaction.</span></span>

  - <span data-ttu-id="fb81c-132">`TransactionAutoComplete`Özelliği, işlenmeyen özel durumlar oluşursa yöntemin yürütme işleminin otomatik olarak tamamlanıp tamamlanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fb81c-132">The `TransactionAutoComplete` property specifies whether the transaction in which the method executes is automatically completed if no unhandled exceptions occur.</span></span> <span data-ttu-id="fb81c-133">Daha önce açıklandığı gibi, bu, `true` Ekle ve çıkart işlemleri için, `false` çarpma ve bölme işlemleri için olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="fb81c-133">As previously described, this is set to `true` for the Add and Subtract operations but `false` for the Multiply and Divide operations.</span></span> <span data-ttu-id="fb81c-134">Ekleme ve çıkarma işlemleri, eylemlerini otomatik olarak tamamlar, bölme kendi eylemlerini yöntemine açık bir çağrı aracılığıyla tamamlar `SetTransactionComplete` ve çarpma işlemleri eylemlerini tamamlamaz ve bunun yerine, eylemleri tamamlamaya yönelik daha sonraki bir çağrı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="fb81c-134">The Add and Subtract operations complete their actions automatically, the Divide completes its actions through an explicit call to the `SetTransactionComplete` method, and the Multiply does not complete its actions but instead relies upon and requires a later call, such as to Divide, to complete the actions.</span></span>

<span data-ttu-id="fb81c-135">Öznitelikli hizmet uygulamasını aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="fb81c-135">The attributed service implementation is as follows:</span></span>

```csharp
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

    // Logging method omitted for brevity
}
```

<span data-ttu-id="fb81c-136">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="fb81c-136">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="fb81c-137">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="fb81c-137">Press ENTER in the client window to shut down the client.</span></span>

```console
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

<span data-ttu-id="fb81c-138">Hizmet işlemi isteklerinin günlüğe kaydedilmesi, hizmetin konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="fb81c-138">The logging of the service operation requests are displayed in the service's console window.</span></span> <span data-ttu-id="fb81c-139">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="fb81c-139">Press ENTER in the client window to shut down the client.</span></span>

```console
Press <ENTER> to terminate service.
Creating new service instance...
  Writing row 1 to database: Adding 100 to 0
  Writing row 2 to database: Subtracting 45 from 100
  Writing row 3 to database: Multiplying 55 by 9
  Writing row 4 to database: Dividing 495 by 15
```

<span data-ttu-id="fb81c-140">Hesaplamaların toplam çalışma sayısını tutmanın yanı sıra hizmetin örneklerin oluşturulmasını (Bu örnek için bir örnek) raporluyor ve işlem isteklerinin bir veritabanına günlüğe kaydettiği unutulmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="fb81c-140">Note that in addition to keeping the running total of the calculations, the service reports the creation of instances (one instance for this sample) and logs the operation requests to a database.</span></span> <span data-ttu-id="fb81c-141">Tüm istekler istemcinin işlemini Flow için, bu işlemi tamamlamamaya yönelik herhangi bir hata, tüm veritabanı işlemlerinin geri alınmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="fb81c-141">Because all of the requests flow the client's transaction, any failure to complete that transaction results in all of the database operations being rolled back.</span></span> <span data-ttu-id="fb81c-142">Bu, çeşitli yollarla gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="fb81c-142">This can be demonstrated in a number of ways:</span></span>

- <span data-ttu-id="fb81c-143">İstemcinin `tx.Complete` () çağrısı yapın ve yeniden çalıştırın. Bu, istemcinin işlemini tamamlamadan işlem kapsamından çıkılıyor.</span><span class="sxs-lookup"><span data-stu-id="fb81c-143">Comment out the client's call to `tx.Complete`() and rerun - this results in the client exiting the transaction scope without completing its transaction.</span></span>

- <span data-ttu-id="fb81c-144">Ayırma hizmeti işlemine çağrı yap-bu sonuçlar, çarpma işlemi tarafından başlatılan eylemin tamamlanmasını önler ve bu nedenle istemcinin işleminin sonunda da tamamlanamamasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="fb81c-144">Comment out the call to the Divide service operation - this results prevent the action initiated by the Multiply operation from completing and thus the client's transaction ultimately also fails to complete.</span></span>

- <span data-ttu-id="fb81c-145">İstemcinin işlem kapsamında herhangi bir yerde işlenmeyen bir özel durum oluşturur. bu benzer şekilde istemcinin işlemini tamamlamasını önler.</span><span class="sxs-lookup"><span data-stu-id="fb81c-145">Throw an unhandled exception anywhere in the client's transaction scope - this similarly prevents the client from completing its transaction.</span></span>

<span data-ttu-id="fb81c-146">Bunlardan herhangi birinin sonucu, bu kapsamda gerçekleştirilen işlemlerin hiçbirinin yürütülmediği ve veritabanında kalıcı olan satırların sayısının artmadığı bir sonucudur.</span><span class="sxs-lookup"><span data-stu-id="fb81c-146">The result of any of these is that none of the operations performed within that scope are committed and the count of rows persisted to the database do not increment.</span></span>

> [!NOTE]
> <span data-ttu-id="fb81c-147">Yapı işleminin bir parçası olarak veritabanı dosyası bin klasörüne kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="fb81c-147">As part of the build process the database file is copied to the bin folder.</span></span> <span data-ttu-id="fb81c-148">Visual Studio projesinde yer alan dosya yerine günlüğe kalıcı olan satırları gözlemlemek için veritabanı dosyasının bu kopyasına bakmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fb81c-148">You must look at that copy of the database file to observe the rows that are persisted to the log rather than the file that is included in the Visual Studio project.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="fb81c-149">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="fb81c-149">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="fb81c-150">SQL Server 2005 Express Sürüm veya SQL Server 2005 ' i yüklediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="fb81c-150">Ensure that you have installed SQL Server 2005 Express Edition or SQL Server 2005.</span></span> <span data-ttu-id="fb81c-151">Hizmetin App.config dosyasında veritabanı `connectionString` ayarlanabilir veya appSettings değeri olarak ayarlanarak veritabanı etkileşimleri devre dışı bırakılabilir `usingSql` `false` .</span><span class="sxs-lookup"><span data-stu-id="fb81c-151">In the service's App.config file, the database `connectionString` may be set or the database interactions may be disabled by setting the appSettings `usingSql` value to `false`.</span></span>

2. <span data-ttu-id="fb81c-152">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="fb81c-152">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="fb81c-153">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="fb81c-153">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

<span data-ttu-id="fb81c-154">Örneği makinelerde çalıştırırsanız, ağ işlem akışını etkinleştirmek için Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) yapılandırmanız ve Windows Communication Foundation (WCF) işlemleri ağ desteğini etkinleştirmek için WsatConfig.exe aracını kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fb81c-154">If you run the sample across machines, you must configure the Microsoft Distributed Transaction Coordinator (MSDTC) to enable network transaction flow and use the WsatConfig.exe tool to enable Windows Communication Foundation (WCF) transactions network support.</span></span>

### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample-across-machines"></a><span data-ttu-id="fb81c-155">Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) hizmetini makineler genelinde çalıştırmayı destekleyecek şekilde yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="fb81c-155">To configure the Microsoft Distributed Transaction Coordinator (MSDTC) to support running the sample across machines</span></span>

1. <span data-ttu-id="fb81c-156">Hizmet makinesinde, gelen ağ işlemlerine izin vermek için MSDTC 'yi yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="fb81c-156">On the service machine, configure MSDTC to allow incoming network transactions.</span></span>

    1. <span data-ttu-id="fb81c-157">**Başlat** menüsünde, **Denetim Masası**' na, ardından **Yönetimsel Araçlar**' a ve ardından **Bileşen Hizmetleri**' ne gidin.</span><span class="sxs-lookup"><span data-stu-id="fb81c-157">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>

    2. <span data-ttu-id="fb81c-158">**Bilgisayarım ' a** sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="fb81c-158">Right-click **My Computer** and select **Properties**.</span></span>

    3. <span data-ttu-id="fb81c-159">**MSDTC** sekmesinde **Güvenlik Yapılandırması**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="fb81c-159">On the **MSDTC** tab, click **Security Configuration**.</span></span>

    4. <span data-ttu-id="fb81c-160">**Ağ DTC erişimini** denetleyin ve **gelen erişime izin verin**.</span><span class="sxs-lookup"><span data-stu-id="fb81c-160">Check **Network DTC Access** and **Allow Inbound**.</span></span>

    5. <span data-ttu-id="fb81c-161">MS DTC hizmetini yeniden başlatmak için **Evet** ' e tıklayın ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="fb81c-161">Click **Yes** to restart the MS DTC service and then click **OK**.</span></span>

    6. <span data-ttu-id="fb81c-162">**Tamam**’a tıklayarak iletişim kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="fb81c-162">Click **OK** to close the dialog box.</span></span>

2. <span data-ttu-id="fb81c-163">Hizmet makinesi ve istemci makinesinde, Windows Güvenlik Duvarı 'nı, hariç tutulan uygulamalar listesine Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) içerecek şekilde yapılandırın:</span><span class="sxs-lookup"><span data-stu-id="fb81c-163">On the service machine and the client machine, configure the Windows Firewall to include the Microsoft Distributed Transaction Coordinator (MSDTC) to the list of excepted applications:</span></span>

    1. <span data-ttu-id="fb81c-164">Windows Güvenlik Duvarı uygulamasını Denetim Masası 'ndan çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="fb81c-164">Run the Windows Firewall application from Control Panel.</span></span>

    2. <span data-ttu-id="fb81c-165">**Özel durumlar** sekmesinde **Program Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="fb81c-165">From the **Exceptions** tab, click **Add Program**.</span></span>

    3. <span data-ttu-id="fb81c-166">C:\WINDOWS\System32. klasörüne gidin</span><span class="sxs-lookup"><span data-stu-id="fb81c-166">Browse to the folder C:\WINDOWS\System32.</span></span>

    4. <span data-ttu-id="fb81c-167">Msdtc.exe seçip **Aç**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="fb81c-167">Select Msdtc.exe and click **Open**.</span></span>

    5. <span data-ttu-id="fb81c-168">**Tamam** ' a tıklayarak **Program Ekle** iletişim kutusunu kapatın ve yeniden **Tamam** ' a tıklayarak Windows Güvenlik Duvarı uygulamasını kapatın.</span><span class="sxs-lookup"><span data-stu-id="fb81c-168">Click **OK** to close the **Add Program** dialog box, and click **OK** again to close the Windows Firewall applet.</span></span>

3. <span data-ttu-id="fb81c-169">İstemci makinesinde, giden ağ işlemlerine izin vermek için MSDTC 'yi yapılandırın:</span><span class="sxs-lookup"><span data-stu-id="fb81c-169">On the client machine, configure MSDTC to allow outgoing network transactions:</span></span>

    1. <span data-ttu-id="fb81c-170">**Başlat** menüsünde, **Denetim Masası**' na, ardından **Yönetimsel Araçlar**' a ve ardından **Bileşen Hizmetleri**' ne gidin.</span><span class="sxs-lookup"><span data-stu-id="fb81c-170">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>

    2. <span data-ttu-id="fb81c-171">**Bilgisayarım ' a** sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="fb81c-171">Right-click **My Computer** and select **Properties**.</span></span>

    3. <span data-ttu-id="fb81c-172">**MSDTC** sekmesinde **Güvenlik Yapılandırması**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="fb81c-172">On the **MSDTC** tab, click **Security Configuration**.</span></span>

    4. <span data-ttu-id="fb81c-173">**Ağ DTC erişimini** denetleyin ve **giden erişime izin verin**.</span><span class="sxs-lookup"><span data-stu-id="fb81c-173">Check **Network DTC Access** and **Allow Outbound**.</span></span>

    5. <span data-ttu-id="fb81c-174">MS DTC hizmetini yeniden başlatmak için **Evet** ' e tıklayın ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="fb81c-174">Click **Yes** to restart the MS DTC service and then click **OK**.</span></span>

    6. <span data-ttu-id="fb81c-175">**Tamam**’a tıklayarak iletişim kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="fb81c-175">Click **OK** to close the dialog box.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fb81c-176">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="fb81c-176">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fb81c-177">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="fb81c-177">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="fb81c-178">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="fb81c-178">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fb81c-179">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="fb81c-179">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Transactions`
