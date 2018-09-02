---
title: İşlem Yapılan Toplu İşlem
ms.date: 03/30/2017
ms.assetid: ecd328ed-332e-479c-a894-489609bcddd2
ms.openlocfilehash: abada9aaf5fac8f05599467f385e708e1898832f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43416654"
---
# <a name="transacted-batching"></a><span data-ttu-id="feb00-102">İşlem Yapılan Toplu İşlem</span><span class="sxs-lookup"><span data-stu-id="feb00-102">Transacted Batching</span></span>
<span data-ttu-id="feb00-103">Bu örnek, hizmetteki okuma Message Queuing (MSMQ) kullanarak toplu olarak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="feb00-103">This sample demonstrates how to batch transacted reads by using Message Queuing (MSMQ).</span></span> <span data-ttu-id="feb00-104">İşlenen toplu işleme kuyruğa alınan iletişim hizmetteki okumalar performans iyileştirme özelliği içindir.</span><span class="sxs-lookup"><span data-stu-id="feb00-104">Transacted Batching is a performance optimization feature for transacted reads in queued communication.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="feb00-105">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="feb00-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="feb00-106">Kuyruğa alınan iletişim kullanarak bir kuyruk hizmetine istemci iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="feb00-106">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="feb00-107">Daha kesin bir istemci bir kuyruğa iletiler gönderir.</span><span class="sxs-lookup"><span data-stu-id="feb00-107">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="feb00-108">Hizmet iletileri kuyruktan alır.</span><span class="sxs-lookup"><span data-stu-id="feb00-108">The service receives messages from the queue.</span></span> <span data-ttu-id="feb00-109">Hizmet ve istemci bu nedenle, bir kuyruk kullanarak iletişim kurmak için aynı anda çalıştırılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="feb00-109">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="feb00-110">Bu örnek, toplu işleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="feb00-110">This sample demonstrates transacted batching.</span></span> <span data-ttu-id="feb00-111">İşlenen toplu işleme, kuyruk ve bunları işlemeye çok iletileri okunurken tek bir işlem kullanımı sağlayan bir davranıştır.</span><span class="sxs-lookup"><span data-stu-id="feb00-111">Transacted batching is a behavior that enables the use of a single transaction when reading many messages in the queue and processing them.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="feb00-112">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="feb00-112">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="feb00-113">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="feb00-113">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="feb00-114">Hizmet ilk olarak çalıştırılırsa, sıranın mevcut olduğundan emin olun kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="feb00-114">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="feb00-115">Kuyruk yoksa, bir hizmeti oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="feb00-115">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="feb00-116">İlk sırayı oluşturmak için hizmet çalıştırabileceğiniz veya bir MSMQ Kuyruk Yöneticisi ile oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="feb00-116">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="feb00-117">Windows 2008'de bir kuyruk oluşturmak için aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="feb00-117">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="feb00-118">Sunucu Yöneticisi'nde açın [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="feb00-118">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="feb00-119">Genişletin **özellikleri** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="feb00-119">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="feb00-120">Sağ **özel ileti kuyrukları**seçip **yeni**, **özel sıra**.</span><span class="sxs-lookup"><span data-stu-id="feb00-120">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="feb00-121">Denetleme **işlem** kutusu.</span><span class="sxs-lookup"><span data-stu-id="feb00-121">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="feb00-122">Girin `ServiceModelSamplesTransacted` yeni Kuyruğun adı.</span><span class="sxs-lookup"><span data-stu-id="feb00-122">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="feb00-123">Bu örnekte istemci iletileri yüzlerce toplu bir parçası olarak gönderir.</span><span class="sxs-lookup"><span data-stu-id="feb00-123">In this sample the client sends hundreds of messages as part of the batch.</span></span> <span data-ttu-id="feb00-124">Bu işlem biraz zaman ayırın hizmet uygulaması için normal bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="feb00-124">It is normal for the service application to take some time to process these.</span></span>  
  
3.  <span data-ttu-id="feb00-125">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="feb00-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="feb00-126">Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="feb00-126">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="feb00-127">Örnek, bir çalışma grubuna veya active directory tümleştirmesi olmadan alanına katılmış bir bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="feb00-127">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>  
  
1.  <span data-ttu-id="feb00-128">Varsayılan olarak <xref:System.ServiceModel.NetMsmqBinding>, aktarım güvenliği etkin.</span><span class="sxs-lookup"><span data-stu-id="feb00-128">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="feb00-129">MSMQ taşıma güvenlik için iki ilgili özellik <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> ve <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` varsayılan olarak, kimlik doğrulama modu ayarlamak `Windows` ve koruma düzeyini ayarlamak `Sign`.</span><span class="sxs-lookup"><span data-stu-id="feb00-129">There are two relevant properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="feb00-130">MSMQ imzalama özelliği ve kimlik doğrulaması sağlamak için bir etki alanının parçası olması gerekir ve MSMQ active directory tümleştirme seçeneği yüklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="feb00-130">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="feb00-131">Bu ölçütleri karşılamayan bir bilgisayarda bu örneği çalıştırmak, bir hata alırsınız.</span><span class="sxs-lookup"><span data-stu-id="feb00-131">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>  
  
2.  <span data-ttu-id="feb00-132">Bilgisayarınız bir etki alanının parçası değil veya yüklü active directory tümleştirmesi yok, aktarım güvenliği devre dışı kimlik doğrulama modu ve koruma düzeyi ayarlayarak kapatma `None` aşağıdaki örnek yapılandırmada gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="feb00-132">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>  
  
    ```xml  
    <system.serviceModel>  
      <behaviors>  
        <serviceBehaviors>  
          <behavior name="ThrottlingBehavior">  
            <serviceMetadata httpGetEnabled="true"/>  
            <serviceThrottling maxConcurrentCalls="5"/>  
          </behavior>  
        </serviceBehaviors>  
  
        <endpointBehaviors>  
          <behavior name="BatchingBehavior">  
            <transactedBatching maxBatchSize="100"/>  
          </behavior>  
        </endpointBehaviors>  
      </behaviors>  
      <services>  
        <service   
            behaviorConfiguration="ThrottlingBehavior"   
            name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
          <host>  
            <baseAddresses>  
              <add baseAddress="http://localhost:8000/orderProcessor/transactedBatchingSample"/>  
            </baseAddresses>  
          </host>  
          <!-- Define NetMsmqEndpoint -->  
          <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTransactedBatching"  
                    binding="netMsmqBinding"  
                    bindingConfiguration="Binding1"   
                    behaviorConfiguration="BatchingBehavior"   
                    contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
          <endpoint address="mex"  
                    binding="mexHttpBinding"  
                    contract="IMetadataExchange" />  
        </service>  
      </services>  
  
      <bindings>  
        <netMsmqBinding>  
          <binding name="Binding1">  
            <security mode="None" />  
          </binding>  
        </netMsmqBinding>  
      </bindings>  
  
    </system.serviceModel>  
    ```  
  
3.  <span data-ttu-id="feb00-133">Örneği çalıştırmadan önce yapılandırma hem sunucu hem de istemci değiştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="feb00-133">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="feb00-134">Ayarı `security``mode` için `None` ayarlamakla eşdeğerdir <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, ve `Message` güvenlik `None`.</span><span class="sxs-lookup"><span data-stu-id="feb00-134">Setting `security``mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>  
  
4.  <span data-ttu-id="feb00-135">Veritabanı uzak bir bilgisayarda çalıştırmak için bağlantı dizesi, veritabanının bulunduğu bilgisayara işaret edecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="feb00-135">To run the database on a remote computer, change the connection string to point to the computer on which the database resides.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="feb00-136">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="feb00-136">Requirements</span></span>  
 <span data-ttu-id="feb00-137">Bu örneği çalıştırmak için MSMQ yüklü olması ve SQL veya SQL Express gereklidir.</span><span class="sxs-lookup"><span data-stu-id="feb00-137">To run this sample, MSMQ must be installed and SQL or SQL Express is required.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="feb00-138">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="feb00-138">Demonstrates</span></span>  
 <span data-ttu-id="feb00-139">İşlenen toplu işleme davranışını örnek gösterir.</span><span class="sxs-lookup"><span data-stu-id="feb00-139">The sample demonstrates transacted batching behavior.</span></span> <span data-ttu-id="feb00-140">İşlenen toplu işleme aktarım MSMQ ile sağlanan bir performans iyileştirme özelliği kuyruğa olur.</span><span class="sxs-lookup"><span data-stu-id="feb00-140">Transacted batching is a performance optimization feature provided with MSMQ queued transport.</span></span>  
  
 <span data-ttu-id="feb00-141">Gerçekten işlemler vardır ileti göndermek ve almak için kullanıldığında 2 hareketlerin ayırın.</span><span class="sxs-lookup"><span data-stu-id="feb00-141">When transactions are used to send and receive messages there are actually 2 separate transactions.</span></span> <span data-ttu-id="feb00-142">İstemci bir işlem kapsamı iletileri gönderdiğinde istemcinin ve istemci Kuyruk yöneticisi yerel bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="feb00-142">When the client sends messages within the scope of a transaction, the transaction is local to the client and the client queue manager.</span></span> <span data-ttu-id="feb00-143">Hizmet işlem kapsamı içindeki iletileri aldığında, hizmet ve alıcı Kuyruk yöneticisi yerel bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="feb00-143">When the service receives messages within the scope of the transaction, the transaction is local to the service and the receiving queue manager.</span></span> <span data-ttu-id="feb00-144">İstemciyi ve hizmeti aynı işlemde katılan değil olduğunu unutmamak çok önemlidir; Bunun yerine farklı işlemler işlemlerini (örneğin göndermek ve almak gibi) ile birlikte kuyruğa gerçekleştirirken kullandıkları.</span><span class="sxs-lookup"><span data-stu-id="feb00-144">It is very important to remember that the client and the service are not participating in the same transaction; rather they are using different transactions when performing their operations (such as send and receive) with the queue.</span></span>  
  
 <span data-ttu-id="feb00-145">Aşağıdaki örnekte birden çok hizmet işlemleri yürütülmesi için tek bir işlem kullanırız.</span><span class="sxs-lookup"><span data-stu-id="feb00-145">In the sample we use a single transaction for the execution of multiple service operations.</span></span> <span data-ttu-id="feb00-146">Bu, yalnızca Performans İyileştirme özelliği kullanılır ve uygulama semantiği etkilemez.</span><span class="sxs-lookup"><span data-stu-id="feb00-146">This is used only as a performance optimization feature and does not impact the semantics of the application.</span></span> <span data-ttu-id="feb00-147">Örnek dayanır [işlem temelli MSMQ bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span><span class="sxs-lookup"><span data-stu-id="feb00-147">The sample is based on [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span></span>  
  
## <a name="comments"></a><span data-ttu-id="feb00-148">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="feb00-148">Comments</span></span>  
 <span data-ttu-id="feb00-149">Bu örnekte, istemci bir işlem kapsamında hizmetten toplu iletiler gönderir.</span><span class="sxs-lookup"><span data-stu-id="feb00-149">In this sample, the client sends a batch of messages to the service from within the scope of a transaction.</span></span> <span data-ttu-id="feb00-150">Performans iyileştirmesi göstermek için çok sayıda ileti göndereceğiz; Bu durumda, 2500 iletileri kadar.</span><span class="sxs-lookup"><span data-stu-id="feb00-150">To show the performance optimization, we send a large number of messages; in this case, up to 2500 messages.</span></span>  
  
 <span data-ttu-id="feb00-151">Kuyruğa gönderilen iletiler, ardından hizmeti tarafından tanımlanan işlem kapsamında hizmeti tarafından alınır.</span><span class="sxs-lookup"><span data-stu-id="feb00-151">The messages sent to the queue are then received by the service within the transaction scope defined by the service.</span></span> <span data-ttu-id="feb00-152">Toplu işleme olmadan, bu hizmet işlemi her çalıştırılışı için 2500 işlemlerde sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="feb00-152">Without batching, this results in 2500 transactions for each invocation of the service operation.</span></span> <span data-ttu-id="feb00-153">Bu, sistemin performansını etkiler.</span><span class="sxs-lookup"><span data-stu-id="feb00-153">This impacts performance of the system.</span></span> <span data-ttu-id="feb00-154">İki kaynak yöneticileri ilgili - olduğu için MSMQ sırası ve `Orders` veritabanı-her tür işlem DTC işlem olduğu.</span><span class="sxs-lookup"><span data-stu-id="feb00-154">Because two resource managers are involved -the MSMQ queue and the `Orders` database- each such transaction is a DTC transaction.</span></span> <span data-ttu-id="feb00-155">Biz tek bir işlemde toplu iletiler ve hizmet işlemi çağrılarını gerçekleşen çok daha az sayıda sağlayarak işlemleri kullanarak iyileştirin.</span><span class="sxs-lookup"><span data-stu-id="feb00-155">We optimize this by using a much smaller number of transactions by ensuring that a batch of messages and service operation invocations happen in a single transaction.</span></span>  
  
 <span data-ttu-id="feb00-156">Toplu işlem özelliğiyle kullanırız:</span><span class="sxs-lookup"><span data-stu-id="feb00-156">We use the batching feature by:</span></span>  
  
-   <span data-ttu-id="feb00-157">İşlenen toplu işleme davranışını yapılandırmasında belirtme.</span><span class="sxs-lookup"><span data-stu-id="feb00-157">Specifying transacted batching behavior in configuration.</span></span>  
  
-   <span data-ttu-id="feb00-158">Bir toplu iş boyutu tek bir işlem kullanılarak okumak için ileti sayısı bakımından belirtme.</span><span class="sxs-lookup"><span data-stu-id="feb00-158">Specifying a batch size in terms of number of messages to be read using a single transaction.</span></span>  
  
-   <span data-ttu-id="feb00-159">Eş zamanlı toplu çalıştırmak için en fazla sayısını belirleme.</span><span class="sxs-lookup"><span data-stu-id="feb00-159">Specifying the maximum number of concurrent batches to run.</span></span>  
  
 <span data-ttu-id="feb00-160">Bu örnekte, performans kazancı elde edildi işlem sayısı 100 hizmet işlemleri tek bir işlemde bir işlem gerçekleştirmeden önce çağrılır sağlayarak azaltarak göstereceğiz.</span><span class="sxs-lookup"><span data-stu-id="feb00-160">In this example, we show performance gains by reducing the number of transactions by ensuring that 100 service operations are invoked in a single transaction before committing the transaction.</span></span>  
  
 <span data-ttu-id="feb00-161">Hizmet davranışı ile bir işlem davranışını tanımlar `TransactionScopeRequired` kümesine `true`.</span><span class="sxs-lookup"><span data-stu-id="feb00-161">The service behavior defines an operation behavior with `TransactionScopeRequired` set to `true`.</span></span> <span data-ttu-id="feb00-162">Bu, kuyruktan ileti almak için kullanılan aynı işlem kapsamı yöntemi tarafından erişilen tüm kaynak yöneticileri tarafından kullanılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="feb00-162">This ensures that the same transaction scope that is used to retrieve the message from the queue is used by any resource managers accessed by the method.</span></span> <span data-ttu-id="feb00-163">Bu örnekte, iletideki satın alma siparişi bilgileri depolamak için bir temel veritabanı kullanın.</span><span class="sxs-lookup"><span data-stu-id="feb00-163">In this example, we use a basic database to store the purchase order information contained in the message.</span></span> <span data-ttu-id="feb00-164">İşlem kapsamı yöntemi bir özel durum oluşturursa, kuyruğa ileti döndürülür garanti eder.</span><span class="sxs-lookup"><span data-stu-id="feb00-164">The transaction scope also guarantees that if the method throws an exception, the message is returned to the queue.</span></span> <span data-ttu-id="feb00-165">Bu işlemi davranışı ayar olmadan sıraya alınan bir kanal iletiyi kuyruktan okumak için bir işlem oluşturur ve böylece işlem başarısız olursa, ileti kaybolur dağıtılmasından önce otomatik olarak tamamlar.</span><span class="sxs-lookup"><span data-stu-id="feb00-165">Without setting this operation behavior, a queued channel creates a transaction to read the message from the queue and commits it automatically before it is dispatched so that if the operation fails, the message is lost.</span></span> <span data-ttu-id="feb00-166">Aşağıdaki kodda gösterildiği gibi bir kuyruktan ileti okumak için kullanılan işlem listeleme hizmet işlemleri için en yaygın senaryodur bakın.</span><span class="sxs-lookup"><span data-stu-id="feb00-166">The most common scenario is for service operations to enlist in the transaction that is used to read the message from the queue as demonstrated in the following code.</span></span>  
  
 <span data-ttu-id="feb00-167">Unutmayın `ReleaseServiceInstanceOnTransactionComplete` ayarlanır `false`.</span><span class="sxs-lookup"><span data-stu-id="feb00-167">Note that `ReleaseServiceInstanceOnTransactionComplete` is set to `false`.</span></span> <span data-ttu-id="feb00-168">Bu, toplu işleme için önemli bir gereksinimdir.</span><span class="sxs-lookup"><span data-stu-id="feb00-168">This is an important requirement for batching.</span></span> <span data-ttu-id="feb00-169">Özellik `ReleaseServiceInstanceOnTransactionComplete` üzerinde `ServiceBehaviorAttribute` hizmet örneği ile işlem tamamlandıktan sonra yapmanız gerekenler gösterir.</span><span class="sxs-lookup"><span data-stu-id="feb00-169">The property `ReleaseServiceInstanceOnTransactionComplete` on `ServiceBehaviorAttribute` indicates what to do with the service instance once the transaction is completed.</span></span> <span data-ttu-id="feb00-170">Varsayılan olarak, hizmet örneği, işlem tamamlandıktan sonra serbest bırakılır.</span><span class="sxs-lookup"><span data-stu-id="feb00-170">By default, the service instance is released upon completing the transaction.</span></span> <span data-ttu-id="feb00-171">Toplu işleme için çekirdek gönderme sırasındaki ileti sayısını ve okuma için tek bir işlem kullanımı yönüdür.</span><span class="sxs-lookup"><span data-stu-id="feb00-171">The core aspect to batching is the use of a single transaction for reading and dispatching many messages in the queue.</span></span> <span data-ttu-id="feb00-172">Bu nedenle hizmet örneği serbest çok kullanımını toplu beklenenden önce negating işlem Tamamlanıyor yukarı sona erer.</span><span class="sxs-lookup"><span data-stu-id="feb00-172">Therefore releasing the service instance ends up completing the transaction prematurely negating the very use of batching.</span></span> <span data-ttu-id="feb00-173">Bu özellik ayarlanırsa `true` ve toplu işlem doğrulama davranışını bir özel durum oluşturursa işlenen toplu işleme davranışını uç noktasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="feb00-173">If this property is set to `true` and transacted batching behavior is added to the endpoint, the batching validation behavior throws an exception.</span></span>  

```csharp
// Service class that implements the service contract.  
// Added code to write output to the console window.  
[ServiceBehavior(ReleaseServiceInstanceOnTransactionComplete=false,   
TransactionIsolationLevel=  
System.Transactions.IsolationLevel.Serializable, ConcurrencyMode=ConcurrencyMode.Multiple)]  
public class OrderProcessorService : IOrderProcessor  
{  
    [OperationBehavior(TransactionScopeRequired = true,  
                       TransactionAutoComplete = true)]  
    public void SubmitPurchaseOrder(PurchaseOrder po)  
    {  
        Orders.Add(po);  
        Console.WriteLine("Processing {0} ", po);  
    }  
    …  
}  
```

 <span data-ttu-id="feb00-174">`Orders` Sınıfı sırayla işlenmesini kapsüller.</span><span class="sxs-lookup"><span data-stu-id="feb00-174">The `Orders` class encapsulates the processing of the order.</span></span> <span data-ttu-id="feb00-175">Bu örnekte veritabanı ile satın alma siparişi bilgileri güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="feb00-175">In the sample, it updates the database with purchase order information.</span></span>  

```csharp
// Order Processing Logic  
public class Orders  
{  
    public static void Add(PurchaseOrder po)  
    {  
        // Insert purchase order.  
        SqlCommand insertPurchaseOrderCommand =   
        new SqlCommand(  
        "insert into PurchaseOrders(poNumber, customerId)   
                               values(@poNumber, @customerId)");  
        insertPurchaseOrderCommand.Parameters.Add("@poNumber",   
                                           SqlDbType.VarChar, 50);  
        insertPurchaseOrderCommand.Parameters.Add("@customerId",   
                                         SqlDbType.VarChar, 50);  
  
        // Insert product line item.  
        SqlCommand insertProductLineItemCommand =   
             new SqlCommand("insert into ProductLineItems(productId,   
                    unitCost, quantity, poNumber) values(@productId,   
                    @unitCost, @quantity, @poNumber)");  
        insertProductLineItemCommand.Parameters.Add("@productId",   
                                           SqlDbType.VarChar, 50);  
        insertProductLineItemCommand.Parameters.Add("@unitCost",   
                                                  SqlDbType.Float);  
        insertProductLineItemCommand.Parameters.Add("@quantity",   
                                                     SqlDbType.Int);  
        insertProductLineItemCommand.Parameters.Add("@poNumber",   
                                           SqlDbType.VarChar, 50);  
        int rowsAffected = 0;  
        using (TransactionScope scope =   
              new TransactionScope(TransactionScopeOption.Required))  
        {  
             using (SqlConnection conn = new   
                 SqlConnection(  
                 ConfigurationManager.AppSettings["connectionString"]))  
             {  
                 conn.Open();  
  
                // Insert into purchase order table.  
               insertPurchaseOrderCommand.Connection = conn;  
               insertPurchaseOrderCommand.Parameters["@poNumber"].Value   
                                                       = po.PONumber;  
             insertPurchaseOrderCommand.Parameters["@customerId"].Value   
                                                    =po.CustomerId;  
             insertPurchaseOrderCommand.ExecuteNonQuery();  
  
            // Insert into product line item table.  
            insertProductLineItemCommand.Connection = conn;  
            foreach (PurchaseOrderLineItem orderLineItem in   
                                        po.orderLineItems) {  
            insertProductLineItemCommand.Parameters["@poNumber"].Value   
                                                          =po.PONumber;  
            insertProductLineItemCommand.Parameters["@productId"].Value   
                                             = orderLineItem.ProductId;  
            insertProductLineItemCommand.Parameters["@unitCost"].Value   
                                             = orderLineItem.UnitCost;  
            insertProductLineItemCommand.Parameters["@quantity"].Value   
                                             = orderLineItem.Quantity;  
            rowsAffected +=   
            insertProductLineItemCommand.ExecuteNonQuery();  
            }  
            scope.Complete();  
        }  
     }  
     Console.WriteLine(  
     "Updated database with {0} product line items  for purchase order   
                                     {1} ", rowsAffected, po.PONumber);  
    }  
}  
```

 <span data-ttu-id="feb00-176">Toplu işleme davranışını ve yapılandırmasını, hizmet uygulama yapılandırmasında belirtilir.</span><span class="sxs-lookup"><span data-stu-id="feb00-176">The batching behavior and its configuration are specified in the service application configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <appSettings>  
    <!-- Use appSetting to configure MSMQ queue name. -->  
    <add key="queueName"   
     value=".\private$\ServiceModelSamplesTransactedBatching" />  
    <add key="baseAddress"   
     value=  
     "http://localhost:8000/orderProcessor/transactedBatchingSample"/>  
    <add key="connectionString" value="Data Source=.\SQLEXPRESS;AttachDbFilename=|DataDirectory|orders.mdf;Integrated Security=True;User Instance=True;" />  
  </appSettings>  
  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ThrottlingBehavior">  
          <serviceThrottling maxConcurrentCalls="5"/>  
        </behavior>  
      </serviceBehaviors>  
  
      <endpointBehaviors>  
        <behavior name="BatchingBehavior">  
          <transactedBatching maxBatchSize="100"/>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <services>  
      <service   
          behaviorConfiguration="ThrottlingBehavior"   
          name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
        <!-- Define NetMsmqEndpoint -->  
        <endpoint address=  
"net.msmq://localhost/private/ServiceModelSamplesTransactedBatching"  
                  binding="netMsmqBinding"  
                  behaviorConfiguration="BatchingBehavior"   
                  contract=  
                    "Microsoft.ServiceModel.Samples.IOrderProcessor" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
>  <span data-ttu-id="feb00-177">Toplu iş boyutu, sistem bir ipucu verir.</span><span class="sxs-lookup"><span data-stu-id="feb00-177">The batch size is a hint to the system.</span></span> <span data-ttu-id="feb00-178">Örneğin, 20 bir toplu iş boyutu belirtirseniz, ardından 20 ileti okunacağı ve tek bir işlem kullanılarak gönderilen ve işlem taahhüt eder.</span><span class="sxs-lookup"><span data-stu-id="feb00-178">For example, if you specify a batch size of 20, then 20 messages would be read and dispatched using a single transaction and then the transaction is committed.</span></span> <span data-ttu-id="feb00-179">Ancak, toplu iş boyutu ulaşılmadan önce burada batch hareketi durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="feb00-179">But there are cases where the transaction may commit the batch before the batch size is reached.</span></span>  
>   
>  <span data-ttu-id="feb00-180">Her bir işlemle ilişkili hareket oluşturulduktan sonra yolunda başlatan bir zaman aşımı olur.</span><span class="sxs-lookup"><span data-stu-id="feb00-180">Associated with every transaction is a timeout that starts ticking once the transaction is created.</span></span> <span data-ttu-id="feb00-181">Bu zaman aşımı süresi dolduğunda işlem iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="feb00-181">When this timeout expires the transaction is aborted.</span></span> <span data-ttu-id="feb00-182">Toplu iş boyutu bile ulaşılmadan önce süresi dolacak şekilde bu zaman aşımı için mümkündür.</span><span class="sxs-lookup"><span data-stu-id="feb00-182">It is possible for this timeout to expire even before the batch size is reached.</span></span> <span data-ttu-id="feb00-183">Toplu işlem nedeniyle durdurma, yeniden çalışma önlemek için `TransactedBatchingBehavior` işlem üzerinde ne kadar süre kaldığını olup olmadığını kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="feb00-183">To avoid re-working the batch because of the abort, the `TransactedBatchingBehavior` checks to see how much time is left on the transaction.</span></span> <span data-ttu-id="feb00-184">İşlem zaman aşımı değerini %80 kullanılması durumunda işlem taahhüt eder.</span><span class="sxs-lookup"><span data-stu-id="feb00-184">If 80% of the transaction timeout is used up, then the transaction is committed.</span></span>  
>   
>  <span data-ttu-id="feb00-185">Daha fazla ileti kuyruğu sonra toplu iş boyutu yerine getirilmesi için beklemek yerine varsa <xref:System.ServiceModel.Description.TransactedBatchingBehavior> hareketi tamamlar.</span><span class="sxs-lookup"><span data-stu-id="feb00-185">If there are no more messages in the queue then instead of waiting for the fulfillment of the batch size the <xref:System.ServiceModel.Description.TransactedBatchingBehavior> commits the transaction.</span></span>  
>   
>  <span data-ttu-id="feb00-186">Toplu iş boyutu seçimi, uygulamaya bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="feb00-186">The choice of the batch size is dependent on your application.</span></span> <span data-ttu-id="feb00-187">Toplu iş boyutu çok küçükse, istediğiniz performans alamayabilir.</span><span class="sxs-lookup"><span data-stu-id="feb00-187">If the batch size is too small, you may not get the desired performance.</span></span> <span data-ttu-id="feb00-188">Diğer taraftan toplu iş boyutu çok büyük ise, performans düşebilir.</span><span class="sxs-lookup"><span data-stu-id="feb00-188">On the other hand if the batch size is too big, it may deteriorate performance.</span></span> <span data-ttu-id="feb00-189">Örneğin, işlem artık canlı ve veritabanınızda kilitler barındırmıyorsa veya işlem kullanılmayan, geri ve iş Yinele olanak batch neden olabilecek kilitlenen.</span><span class="sxs-lookup"><span data-stu-id="feb00-189">For example, your transaction could live longer and hold locks on your database or your transaction could become dead locked, which could cause the batch to get rolled back and to redo the work.</span></span>  
  
 <span data-ttu-id="feb00-190">İstemci işlem kapsamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="feb00-190">The client creates a transaction scope.</span></span> <span data-ttu-id="feb00-191">Kuyruk ile iletişimi, burada tüm iletileri kuyruğa gönderilir ya da hiçbiri iletilerin kuyruğa gönderilen bir atomik birim olarak kabul edilmesi bu neden işlemin kapsamı içinde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="feb00-191">Communication with the queue takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages are sent to the queue or none of the messages are sent to the queue.</span></span> <span data-ttu-id="feb00-192">İşlem çağırarak kararlıdır <xref:System.Transactions.TransactionScope.Complete%2A> işlem kapsamı üzerinde.</span><span class="sxs-lookup"><span data-stu-id="feb00-192">The transaction is committed by calling <xref:System.Transactions.TransactionScope.Complete%2A> on the transaction scope.</span></span>  

```csharp
//Client implementation code.  
class Client  
{  
    static void Main()  
    {  
        Random randomGen = new Random();  
        for (int i = 0; i < 2500; i++)  
        {  
            // Create a client with given client endpoint configuration.  
            OrderProcessorClient client = new OrderProcessorClient("OrderProcessorEndpoint");  
  
            // Create the purchase order.  
            PurchaseOrder po = new PurchaseOrder();  
            po.CustomerId = "somecustomer" + i + ".com";  
            po.PONumber = Guid.NewGuid().ToString();  
  
            PurchaseOrderLineItem lineItem1 = new PurchaseOrderLineItem();  
            lineItem1.ProductId = "Blue Widget";  
            lineItem1.Quantity = randomGen.Next(1, 100);  
            lineItem1.UnitCost = (float)randomGen.NextDouble() * 10;  
  
            PurchaseOrderLineItem lineItem2 = new PurchaseOrderLineItem();  
            lineItem2.ProductId = "Red Widget";  
            lineItem2.Quantity = 890;  
            lineItem2.UnitCost = 45.89F;  
  
            po.orderLineItems = new PurchaseOrderLineItem[2];  
            po.orderLineItems[0] = lineItem1;  
            po.orderLineItems[1] = lineItem2;  
  
            //Create a transaction scope.  
            using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
            {  
                // Make a queued call to submit the purchase order.  
                client.SubmitPurchaseOrder(po);  
                // Complete the transaction.  
                scope.Complete();  
            }  
  
            client.Close();  
        }  
        Console.WriteLine();  
        Console.WriteLine("Press <ENTER> to terminate client.");  
        Console.ReadLine();  
    }  
}  
```

 <span data-ttu-id="feb00-193">Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hizmet ve istemci konsol pencerelerinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="feb00-193">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="feb00-194">İstemciden hizmet alma iletileri görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="feb00-194">You can see the service receive messages from the client.</span></span> <span data-ttu-id="feb00-195">Her konsol penceresi hizmet ve istemci kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="feb00-195">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="feb00-196">Sıraya alma kullanımda olduğundan, istemci ve hizmet aynı zamanda açık ve çalışıyor olması gerekmez, unutmayın.</span><span class="sxs-lookup"><span data-stu-id="feb00-196">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="feb00-197">İstemcisini çalıştıran da kapatın ve ardından hizmeti başlatın ve hala iletilerini alır.</span><span class="sxs-lookup"><span data-stu-id="feb00-197">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span> <span data-ttu-id="feb00-198">İletilerin bir toplu işte okuyun ve işlenen olarak sıralı bir çıkış görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="feb00-198">You can see a rolling output as messages are read in a batch and processed.</span></span>  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Updated database with 2 product line items for purchase order 493ac832-d216-4e94-b2a5-d7f492fb5e39  
Processing Purchase Order: 8b567f5b-0661-4662-aae2-6cef1bd6d278  
        Customer: somecustomer849.com  
        OrderDetails  
               Order LineItem: 80 of Blue Widget @unit price: $9.751623  
               Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $41622.23  
        Order status: Pending  
  
Updated database with 2 product line items for purchase order 41130b95-4ea8-40a9-91c3-2e129117fcb8  
Processing Purchase Order: 5ce2699d-9a31-4cc2-a8c5-64cda614b3c7  
        Customer: somecustomer850.com  
        OrderDetails  
               Order LineItem: 89 of Blue Widget @unit price: $6.369128  
               Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $41408.95  
        Order status: Pending  
  
Updated database with 2 product line items for purchase order 8b567f5b-0661-4662-aae2-6cef1bd6d278  
Processing Purchase Order: ea94486b-7c86-4309-a42d-2f06c00656cd  
        Customer: somecustomer851.com  
        OrderDetails  
             Order LineItem: 47 of Blue Widget @unit price: $0.9391424  
             Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $40886.24  
        Order status: Pending  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="feb00-199">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="feb00-199">The samples may already be installed on your computer.</span></span> <span data-ttu-id="feb00-200">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="feb00-200">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="feb00-201">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="feb00-201">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="feb00-202">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="feb00-202">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Batching`  
  
## <a name="see-also"></a><span data-ttu-id="feb00-203">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="feb00-203">See Also</span></span>
