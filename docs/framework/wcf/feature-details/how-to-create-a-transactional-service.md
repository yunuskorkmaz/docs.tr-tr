---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Işlemsel hizmet oluşturma'
title: 'Nasıl yapılır: İşlemsel Hizmet Oluşturma'
ms.date: 03/30/2017
ms.assetid: 1bd2e4ed-a557-43f9-ba98-4c70cb75c154
ms.openlocfilehash: 78ad922a7e1f174715be7bd1a8466572425411be
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643442"
---
# <a name="how-to-create-a-transactional-service"></a><span data-ttu-id="5835a-103">Nasıl yapılır: İşlemsel Hizmet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5835a-103">How to: Create a Transactional Service</span></span>

<span data-ttu-id="5835a-104">Bu örnek, işlemsel bir hizmet oluşturmanın ve hizmet işlemlerini koordine etmek için istemci tarafından başlatılan bir işlemin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5835a-104">This sample demonstrates various aspects of creating a transactional service and the use of a client-initiated transaction to coordinate service operations.</span></span>  
  
### <a name="creating-a-transactional-service"></a><span data-ttu-id="5835a-105">İşlemsel hizmet oluşturma</span><span class="sxs-lookup"><span data-stu-id="5835a-105">Creating a transactional service</span></span>  
  
1. <span data-ttu-id="5835a-106">Gelen işlem gereksinimlerini belirtmek için, bir hizmet sözleşmesi oluşturun ve istenen ayarı <xref:System.ServiceModel.TransactionFlowOption> Numaralandırmadaki işlemlere ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5835a-106">Create a service contract and annotate the operations with the desired setting from the <xref:System.ServiceModel.TransactionFlowOption> enumeration to specify the incoming transaction requirements.</span></span> <span data-ttu-id="5835a-107">Ayrıca, uygulanan hizmet sınıfına da yerleştirebileceğinizi unutmayın <xref:System.ServiceModel.TransactionFlowAttribute> .</span><span class="sxs-lookup"><span data-stu-id="5835a-107">Note that you can also place the <xref:System.ServiceModel.TransactionFlowAttribute> on the service class being implemented.</span></span> <span data-ttu-id="5835a-108">Bu, bir arabirimin tek bir uygulamasının her uygulama yerine bu işlem ayarlarını kullanmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="5835a-108">This allows for a single implementation of an interface to use these transaction settings, instead of every implementation.</span></span>  
  
    ```csharp
    [ServiceContract]  
    public interface ICalculator  
    {  
        [OperationContract]  
        // Use this to require an incoming transaction  
        [TransactionFlow(TransactionFlowOption.Mandatory)]  
        double Add(double n1, double n2);  
        [OperationContract]  
        // Use this to permit an incoming transaction  
        [TransactionFlow(TransactionFlowOption.Allowed)]  
        double Subtract(double n1, double n2);  
    }  
    ```  
  
2. <span data-ttu-id="5835a-109">Bir uygulama sınıfı oluşturun ve <xref:System.ServiceModel.ServiceBehaviorAttribute> isteğe bağlı olarak bir ve belirtmek için öğesini kullanın <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> .</span><span class="sxs-lookup"><span data-stu-id="5835a-109">Create an implementation class, and use the <xref:System.ServiceModel.ServiceBehaviorAttribute> to optionally specify a <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> and a <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>.</span></span> <span data-ttu-id="5835a-110">Çoğu durumda, varsayılan değer olan <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> 60 saniye ve varsayılan değer olarak uygun olduğunu unutmayın <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> `Unspecified` .</span><span class="sxs-lookup"><span data-stu-id="5835a-110">You should note that in many cases, the default <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> of 60 seconds and the default <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> of `Unspecified` are appropriate.</span></span> <span data-ttu-id="5835a-111">Her işlem için, <xref:System.ServiceModel.OperationBehaviorAttribute> yöntemi içinde gerçekleştirilen çalışmanın, özniteliğin değerine göre bir işlem kapsamı kapsamında gerçekleşmeyeceğini belirtmek için özniteliğini kullanabilirsiniz <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> .</span><span class="sxs-lookup"><span data-stu-id="5835a-111">For each operation, you can use the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute to specify whether work performed within the method should occur within the scope of a transaction scope according to the value of the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> attribute.</span></span> <span data-ttu-id="5835a-112">Bu durumda, yöntemi için kullanılan işlem, `Add` istemciden aktarılan zorunlu gelen işlemle aynıdır ve yöntemi için kullanılan işlem `Subtract` , istemciden veya yeni bir örtük olarak oluşturulan yeni bir işlem olduğunda gelen işlem ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="5835a-112">In this case, the transaction used for the `Add` method is the same as the mandatory incoming transaction that is flowed from the client, and the transaction used for the `Subtract` method is either the same as the incoming transaction if one was flowed from the client, or a new implicitly and locally created transaction.</span></span>  
  
    ```csharp
    [ServiceBehavior(  
        TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable,  
        TransactionTimeout = "00:00:45")]  
    public class CalculatorService : ICalculator  
    {  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Add(double n1, double n2)  
        {  
            // Perform transactional operation  
            RecordToLog($"Adding {n1} to {n2}");
            return n1 + n2;  
        }  
  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Subtract(double n1, double n2)  
        {  
            // Perform transactional operation  
            RecordToLog($"Subtracting {n2} from {n1}");
            return n1 - n2;  
        }  
  
        private static void RecordToLog(string recordText)  
        {  
            // Database operations omitted for brevity  
            // This is where the transaction provides specific benefit  
            // - changes to the database will be committed only when  
            // the transaction completes.  
        }  
    }  
    ```  
  
3. <span data-ttu-id="5835a-113">Yapılandırma dosyasında, işlem bağlamının akışını ve bunu yapmak için kullanılacak protokolleri belirten bağlamaları yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="5835a-113">Configure the bindings in the configuration file, specifying that the transaction context should be flowed, and the protocols to be used to do so.</span></span> <span data-ttu-id="5835a-114">Daha fazla bilgi için bkz. [ServiceModel Işlem yapılandırması](servicemodel-transaction-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="5835a-114">For more information, see [ServiceModel Transaction Configuration](servicemodel-transaction-configuration.md).</span></span> <span data-ttu-id="5835a-115">Özellikle, bağlama türü, uç nokta öğesinin `binding` özniteliğinde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="5835a-115">Specifically, the binding type is specified in the endpoint element’s `binding` attribute.</span></span> <span data-ttu-id="5835a-116">[\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md)Öğesi `bindingConfiguration` `transactionalOleTransactionsTcpBinding` , aşağıdaki örnek yapılandırmada gösterildiği gibi adlı bir bağlama yapılandırmasına başvuran bir özniteliği içerir.</span><span class="sxs-lookup"><span data-stu-id="5835a-116">The [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) element contains a `bindingConfiguration` attribute that references a binding configuration named `transactionalOleTransactionsTcpBinding`, as shown in the following sample configuration.</span></span>  
  
    ```xml  
    <service name="CalculatorService">  
      <endpoint address="net.tcp://localhost:8008/CalcService"  
        binding="netTcpBinding"  
        bindingConfiguration="transactionalOleTransactionsTcpBinding"  
        contract="ICalculator"  
        name="OleTransactions_endpoint" />  
    </service>  
    ```  
  
     <span data-ttu-id="5835a-117">İşlem akışı, özniteliği kullanılarak yapılandırma düzeyinde etkinleştirilir `transactionFlow` ve işlem protokolü `transactionProtocol` Aşağıdaki yapılandırmada gösterildiği gibi özniteliği kullanılarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="5835a-117">Transaction flow is enabled at the configuration level by using the `transactionFlow` attribute, and the transaction protocol is specified using the `transactionProtocol` attribute, as shown in the following configuration.</span></span>  
  
    ```xml  
    <bindings>  
      <netTcpBinding>  
        <binding name="transactionalOleTransactionsTcpBinding"  
          transactionFlow="true"  
          transactionProtocol="OleTransactions"/>  
      </netTcpBinding>  
    </bindings>  
    ```  
  
### <a name="supporting-multiple-transaction-protocols"></a><span data-ttu-id="5835a-118">Birden çok işlem protokolünü destekleme</span><span class="sxs-lookup"><span data-stu-id="5835a-118">Supporting multiple transaction protocols</span></span>  
  
1. <span data-ttu-id="5835a-119">En iyi performans için, Windows Communication Foundation (WCF) kullanılarak yazılmış bir istemciyi ve hizmeti içeren senaryolar için OleTransactions protokolünü kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5835a-119">For optimal performance, you should use the OleTransactions protocol for scenarios involving a client and service written using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="5835a-120">Ancak, WS-AtomicTransaction (WS-AT) protokolü, üçüncü taraf protokol yığınları ile birlikte çalışabilirlik gerektiğinde senaryolar için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="5835a-120">However, the WS-AtomicTransaction (WS-AT) protocol is useful for scenarios when interoperability with third-party protocol stacks is required.</span></span> <span data-ttu-id="5835a-121">Aşağıdaki örnek yapılandırmada gösterildiği gibi, uygun protokole özgü bağlamaları olan birden fazla uç nokta sağlayarak WCF hizmetlerini her iki protokolü de kabul edecek şekilde yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5835a-121">You can configure WCF services to accept both protocols by providing multiple endpoints with appropriate protocol-specific bindings, as shown in the following sample configuration.</span></span>  
  
    ```xml  
    <service name="CalculatorService">  
      <endpoint address="http://localhost:8000/CalcService"  
        binding="wsHttpBinding"  
        bindingConfiguration="transactionalWsatHttpBinding"  
        contract="ICalculator"  
        name="WSAtomicTransaction_endpoint" />  
      <endpoint address="net.tcp://localhost:8008/CalcService"  
        binding="netTcpBinding"  
        bindingConfiguration="transactionalOleTransactionsTcpBinding"  
        contract="ICalculator"  
        name="OleTransactions_endpoint" />  
    </service>  
    ```  
  
     <span data-ttu-id="5835a-122">İşlem protokolü özniteliği kullanılarak belirtilir `transactionProtocol` .</span><span class="sxs-lookup"><span data-stu-id="5835a-122">The transaction protocol is specified using the `transactionProtocol` attribute.</span></span> <span data-ttu-id="5835a-123">Ancak, bu öznitelik `wsHttpBinding` yalnızca ws-at protokolünü kullanabilmesi için, bu öznitelik sistem tarafından sağlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="5835a-123">However, this attribute is absent from the system-provided `wsHttpBinding`, because this binding can only use the WS-AT protocol.</span></span>  
  
    ```xml  
    <bindings>  
      <wsHttpBinding>  
        <binding name="transactionalWsatHttpBinding"  
          transactionFlow="true" />  
      </wsHttpBinding>  
      <netTcpBinding>  
        <binding name="transactionalOleTransactionsTcpBinding"  
          transactionFlow="true"  
          transactionProtocol="OleTransactions"/>  
      </netTcpBinding>  
    </bindings>  
    ```  
  
### <a name="controlling-the-completion-of-a-transaction"></a><span data-ttu-id="5835a-124">Bir işlemin tamamlanmasını denetleme</span><span class="sxs-lookup"><span data-stu-id="5835a-124">Controlling the completion of a transaction</span></span>  
  
1. <span data-ttu-id="5835a-125">Varsayılan olarak, işlenmeyen özel durum oluşturulmaz, WCF işlemleri işlemleri otomatik olarak tamamlar.</span><span class="sxs-lookup"><span data-stu-id="5835a-125">By default, WCF operations automatically complete transactions if no unhandled exceptions are thrown.</span></span> <span data-ttu-id="5835a-126">Bu davranışı <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> özelliğini ve yöntemini kullanarak değiştirebilirsiniz <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> .</span><span class="sxs-lookup"><span data-stu-id="5835a-126">You can modify this behavior by using the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property and the <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> method.</span></span> <span data-ttu-id="5835a-127">Bir işlemin başka bir işlemle aynı işlem içinde gerçekleşmesi gerektiğinde (örneğin, bir borç ve kredi işlemi), <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> `false` aşağıdaki işlem örneğinde gösterildiği gibi özelliğini olarak ayarlayarak otomatik tamamlama davranışını devre dışı bırakabilirsiniz `Debit` .</span><span class="sxs-lookup"><span data-stu-id="5835a-127">When an operation is required to occur within the same transaction as another operation (for example, a debit and credit operation), you can disable the autocomplete behavior by setting the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property to `false` as shown in the following `Debit` operation example.</span></span> <span data-ttu-id="5835a-128">İşlemin kullandığı işlem, işlem içinde `Debit` gösterildiği gibi, özelliği olarak ayarlanmış bir yöntem çağrılana kadar ya da işlem, işlemde <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> `true` `Credit1` <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> gösterildiği gibi işlemi tamamlandı olarak işaretlemek üzere çağrıldığında `Credit2` işlem tamamlanmaz.</span><span class="sxs-lookup"><span data-stu-id="5835a-128">The transaction the `Debit` operation uses is not completed until a method with the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property set to `true` is called, as shown in the operation `Credit1`, or when the <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> method is called to explicitly mark the transaction as complete, as shown in the operation `Credit2`.</span></span> <span data-ttu-id="5835a-129">İki kredi işleminin illüstrasyon amacıyla gösterildiğini ve tek bir kredi işleminin daha tipik olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5835a-129">Note that the two credit operations are shown for illustration purposes, and that a single credit operation would be more typical.</span></span>  
  
    ```csharp
    [ServiceBehavior]  
    public class CalculatorService : IAccount  
    {  
        [OperationBehavior(  
            TransactionScopeRequired = true, TransactionAutoComplete = false)]  
        public void Debit(double n)  
        {  
            // Perform debit operation  
  
            return;  
        }  
  
        [OperationBehavior(  
            TransactionScopeRequired = true, TransactionAutoComplete = true)]  
        public void Credit1(double n)  
        {  
            // Perform credit operation  
  
            return;  
        }  
  
        [OperationBehavior(  
            TransactionScopeRequired = true, TransactionAutoComplete = false)]  
        public void Credit2(double n)  
        {  
            // Perform alternate credit operation  
  
            OperationContext.Current.SetTransactionComplete();  
            return;  
        }  
    }  
    ```  
  
2. <span data-ttu-id="5835a-130">İşlem bağıntı amaçları doğrultusunda, özelliği olarak ayarlamak, <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> `false` bir oturumsuz bağlamanın kullanılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5835a-130">For the purposes of transaction correlation, setting the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property to `false` requires the use of a sessionful binding.</span></span> <span data-ttu-id="5835a-131">Bu gereksinim `SessionMode` , üzerinde özelliği ile belirtilir <xref:System.ServiceModel.ServiceContractAttribute> .</span><span class="sxs-lookup"><span data-stu-id="5835a-131">This requirement is specified with the `SessionMode` property on the <xref:System.ServiceModel.ServiceContractAttribute>.</span></span>  
  
    ```csharp
    [ServiceContract(SessionMode = SessionMode.Required)]  
    public interface IAccount  
    {  
        [OperationContract]  
        [TransactionFlow(TransactionFlowOption.Allowed)]  
        void Debit(double n);  
        [OperationContract]  
        [TransactionFlow(TransactionFlowOption.Allowed)]  
        void Credit1(double n);  
        [OperationContract]  
        [TransactionFlow(TransactionFlowOption.Allowed)]  
        void Credit2(double n);  
    }  
    ```  
  
### <a name="controlling-the-lifetime-of-a-transactional-service-instance"></a><span data-ttu-id="5835a-132">Bir işlem hizmeti örneğinin ömrünü denetleme</span><span class="sxs-lookup"><span data-stu-id="5835a-132">Controlling the lifetime of a transactional service instance</span></span>  
  
1. <span data-ttu-id="5835a-133">WCF, <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> bir işlem tamamlandığında temeldeki hizmet örneğinin serbest bırakılıp başlatılmayacağını belirtmek için özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="5835a-133">WCF uses the <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> property to specify whether the underlying service instance is released when a transaction completes.</span></span> <span data-ttu-id="5835a-134">Bu varsayılan olarak `true` , aksi belirtilmedikçe, WCF etkin ve öngörülebilir bir "tam zamanında" etkinleştirme davranışı sergiler.</span><span class="sxs-lookup"><span data-stu-id="5835a-134">Since this defaults to `true`, unless configured otherwise, WCF exhibits an efficient and predictable "just-in-time" activation behavior.</span></span> <span data-ttu-id="5835a-135">Sonraki bir işlem üzerindeki bir hizmete yapılan çağrılar, önceki işlemin durumuna göre hiçbir şekilde, yeni bir hizmet örneğini garanti altına alır.</span><span class="sxs-lookup"><span data-stu-id="5835a-135">Calls to a service on a subsequent transaction are assured a new service instance with no remnants of the previous transaction's state.</span></span> <span data-ttu-id="5835a-136">Bu genellikle yararlı olsa da, bazen işlem tamamlandıktan sonra hizmet örneği içinde durumu korumak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5835a-136">While this is often useful, sometimes you may want to maintain state within the service instance beyond the transaction completion.</span></span> <span data-ttu-id="5835a-137">Bunun örnekleri, gerekli durum veya kaynak tanıtıcılarının alınması veya edilmeyen ne kadar pahalı olduğu durumdur.</span><span class="sxs-lookup"><span data-stu-id="5835a-137">Examples of this would be when required state or handles to resources are expensive to retrieve or reconstitute.</span></span> <span data-ttu-id="5835a-138">Bunu, <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> özelliğini olarak ayarlayarak yapabilirsiniz `false` .</span><span class="sxs-lookup"><span data-stu-id="5835a-138">You can do this by setting the <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> property to `false`.</span></span> <span data-ttu-id="5835a-139">Bu ayar ile, örnek ve ilişkili herhangi bir durum sonraki çağrılarda kullanılabilir olacaktır.</span><span class="sxs-lookup"><span data-stu-id="5835a-139">With that setting, the instance and any associated state will be available on subsequent calls.</span></span> <span data-ttu-id="5835a-140">Bunu kullanırken, durum ve işlemlerin ne zaman ve nasıl temizleneceği ve tamamlanalınacağını göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="5835a-140">When using this, give careful consideration to when and how state and transactions will be cleared and completed.</span></span> <span data-ttu-id="5835a-141">Aşağıdaki örnek, örneği değişkenle birlikte tutarak bunun nasıl yapılacağını gösterir `runningTotal` .</span><span class="sxs-lookup"><span data-stu-id="5835a-141">The following sample demonstrates how to do this by maintaining the instance with the `runningTotal` variable.</span></span>  
  
    ```csharp
    [ServiceBehavior(TransactionIsolationLevel = [ServiceBehavior(  
        ReleaseServiceInstanceOnTransactionComplete = false)]  
    public class CalculatorService : ICalculator  
    {  
        double runningTotal = 0;  
  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Add(double n)  
        {  
            // Perform transactional operation  
            RecordToLog($"Adding {n} to {runningTotal}");
            runningTotal = runningTotal + n;  
            return runningTotal;  
        }  
  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Subtract(double n)  
        {  
            // Perform transactional operation  
            RecordToLog($"Subtracting {n} from {runningTotal}");
            runningTotal = runningTotal - n;  
            return runningTotal;  
        }  
  
        private static void RecordToLog(string recordText)  
        {  
            // Database operations omitted for brevity  
        }  
    }  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="5835a-142">Örnek yaşam süresi, hizmete iç bir davranış olduğundan ve özelliği aracılığıyla denetlendiğinden <xref:System.ServiceModel.ServiceBehaviorAttribute> , örnek davranışını ayarlamak için hizmet yapılandırmasında veya hizmet sözleşmesinde hiçbir değişiklik yapılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="5835a-142">Since the instance lifetime is a behavior that is internal to the service, and controlled through the <xref:System.ServiceModel.ServiceBehaviorAttribute> property, no modification to the service configuration or service contract is required to set the instance behavior.</span></span> <span data-ttu-id="5835a-143">Ayrıca, hat bunun gösterimini içermez.</span><span class="sxs-lookup"><span data-stu-id="5835a-143">In addition, the wire will contain no representation of this.</span></span>
