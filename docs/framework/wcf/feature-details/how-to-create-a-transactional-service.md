---
title: 'Nasıl yapılır: İşlemsel Hizmet Oluşturma'
ms.date: 03/30/2017
ms.assetid: 1bd2e4ed-a557-43f9-ba98-4c70cb75c154
ms.openlocfilehash: be364e7638394a30c199b05dd15ef4c44e18e688
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964014"
---
# <a name="how-to-create-a-transactional-service"></a><span data-ttu-id="4246f-102">Nasıl yapılır: İşlemsel Hizmet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4246f-102">How to: Create a Transactional Service</span></span>
<span data-ttu-id="4246f-103">Bu örnek, işlemsel bir hizmet oluşturmanın ve hizmet işlemlerini koordine etmek için istemci tarafından başlatılan bir işlemin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4246f-103">This sample demonstrates various aspects of creating a transactional service and the use of a client-initiated transaction to coordinate service operations.</span></span>  
  
### <a name="creating-a-transactional-service"></a><span data-ttu-id="4246f-104">İşlemsel hizmet oluşturma</span><span class="sxs-lookup"><span data-stu-id="4246f-104">Creating a transactional service</span></span>  
  
1. <span data-ttu-id="4246f-105">Gelen işlem gereksinimlerini belirtmek için, bir hizmet sözleşmesi oluşturun ve istenen ayarı <xref:System.ServiceModel.TransactionFlowOption> Numaralandırmadaki işlemlere ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4246f-105">Create a service contract and annotate the operations with the desired setting from the <xref:System.ServiceModel.TransactionFlowOption> enumeration to specify the incoming transaction requirements.</span></span> <span data-ttu-id="4246f-106">Ayrıca, <xref:System.ServiceModel.TransactionFlowAttribute> uygulanan hizmet sınıfına da yerleştirebileceğinizi unutmayın.</span><span class="sxs-lookup"><span data-stu-id="4246f-106">Note that you can also place the <xref:System.ServiceModel.TransactionFlowAttribute> on the service class being implemented.</span></span> <span data-ttu-id="4246f-107">Bu, bir arabirimin tek bir uygulamasının her uygulama yerine bu işlem ayarlarını kullanmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="4246f-107">This allows for a single implementation of an interface to use these transaction settings, instead of every implementation.</span></span>  
  
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
  
2. <span data-ttu-id="4246f-108">Bir uygulama sınıfı oluşturun ve isteğe bağlı olarak <xref:System.ServiceModel.ServiceBehaviorAttribute> bir <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> ve <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>belirtmek için öğesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="4246f-108">Create an implementation class, and use the <xref:System.ServiceModel.ServiceBehaviorAttribute> to optionally specify a <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> and a <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>.</span></span> <span data-ttu-id="4246f-109">Çoğu durumda, varsayılan değer <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> olan 60 saniye ve `Unspecified` varsayılan <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> değer olarak uygun olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="4246f-109">You should note that in many cases, the default <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> of 60 seconds and the default <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> of `Unspecified` are appropriate.</span></span> <span data-ttu-id="4246f-110">Her işlem için, yöntemi içinde gerçekleştirilen çalışmanın <xref:System.ServiceModel.OperationBehaviorAttribute> , <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> özniteliğin değerine göre bir işlem kapsamı kapsamında gerçekleşmeyeceğini belirtmek için özniteliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4246f-110">For each operation, you can use the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute to specify whether work performed within the method should occur within the scope of a transaction scope according to the value of the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> attribute.</span></span> <span data-ttu-id="4246f-111">Bu durumda, `Add` yöntemi için kullanılan işlem, istemciden aktarılan zorunlu gelen işlem ile aynıdır ve `Subtract` bu işlem, bir işlem ise gelen işlem ile aynı olur istemciden veya yeni bir örtük ve yerel olarak oluşturulan işlemden.</span><span class="sxs-lookup"><span data-stu-id="4246f-111">In this case, the transaction used for the `Add` method is the same as the mandatory incoming transaction that is flowed from the client, and the transaction used for the `Subtract` method is either the same as the incoming transaction if one was flowed from the client, or a new implicitly and locally created transaction.</span></span>  
  
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
  
3. <span data-ttu-id="4246f-112">Yapılandırma dosyasında, işlem bağlamının akışını ve bunu yapmak için kullanılacak protokolleri belirten bağlamaları yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="4246f-112">Configure the bindings in the configuration file, specifying that the transaction context should be flowed, and the protocols to be used to do so.</span></span> <span data-ttu-id="4246f-113">Daha fazla bilgi için bkz. [ServiceModel Işlem yapılandırması](servicemodel-transaction-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="4246f-113">For more information, see [ServiceModel Transaction Configuration](servicemodel-transaction-configuration.md).</span></span> <span data-ttu-id="4246f-114">Özellikle, bağlama türü, uç nokta öğesinin `binding` özniteliğinde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="4246f-114">Specifically, the binding type is specified in the endpoint element’s `binding` attribute.</span></span> <span data-ttu-id="4246f-115">`bindingConfiguration` `transactionalOleTransactionsTcpBinding` [ Uçnokta>öğesi,aşağıdakiörnekyapılandırmadagösterildiği\<](../../configure-apps/file-schema/wcf/endpoint-element.md) gibi adlı bağlama yapılandırmasına başvuran bir özniteliği içerir.</span><span class="sxs-lookup"><span data-stu-id="4246f-115">The [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) element contains a `bindingConfiguration` attribute that references a binding configuration named `transactionalOleTransactionsTcpBinding`, as shown in the following sample configuration.</span></span>  
  
    ```xml  
    <service name="CalculatorService">  
      <endpoint address="net.tcp://localhost:8008/CalcService"  
        binding="netTcpBinding"  
        bindingConfiguration="transactionalOleTransactionsTcpBinding"  
        contract="ICalculator"  
        name="OleTransactions_endpoint" />  
    </service>  
    ```  
  
     <span data-ttu-id="4246f-116">İşlem akışı, `transactionFlow` özniteliği kullanılarak yapılandırma düzeyinde etkinleştirilir ve işlem protokolü Aşağıdaki yapılandırmada gösterildiği gibi `transactionProtocol` özniteliği kullanılarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="4246f-116">Transaction flow is enabled at the configuration level by using the `transactionFlow` attribute, and the transaction protocol is specified using the `transactionProtocol` attribute, as shown in the following configuration.</span></span>  
  
    ```xml  
    <bindings>  
      <netTcpBinding>  
        <binding name="transactionalOleTransactionsTcpBinding"  
          transactionFlow="true"  
          transactionProtocol="OleTransactions"/>  
      </netTcpBinding>  
    </bindings>  
    ```  
  
### <a name="supporting-multiple-transaction-protocols"></a><span data-ttu-id="4246f-117">Birden çok işlem protokolünü destekleme</span><span class="sxs-lookup"><span data-stu-id="4246f-117">Supporting multiple transaction protocols</span></span>  
  
1. <span data-ttu-id="4246f-118">En iyi performans için, Windows Communication Foundation (WCF) kullanılarak yazılmış bir istemciyi ve hizmeti içeren senaryolar için OleTransactions protokolünü kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4246f-118">For optimal performance, you should use the OleTransactions protocol for scenarios involving a client and service written using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="4246f-119">Ancak, WS-AtomicTransaction (WS-AT) protokolü, üçüncü taraf protokol yığınları ile birlikte çalışabilirlik gerektiğinde senaryolar için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="4246f-119">However, the WS-AtomicTransaction (WS-AT) protocol is useful for scenarios when interoperability with third-party protocol stacks is required.</span></span> <span data-ttu-id="4246f-120">Aşağıdaki örnek yapılandırmada gösterildiği gibi, uygun protokole özgü bağlamaları olan birden fazla uç nokta sağlayarak WCF hizmetlerini her iki protokolü de kabul edecek şekilde yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4246f-120">You can configure WCF services to accept both protocols by providing multiple endpoints with appropriate protocol-specific bindings, as shown in the following sample configuration.</span></span>  
  
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
  
     <span data-ttu-id="4246f-121">İşlem protokolü `transactionProtocol` özniteliği kullanılarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="4246f-121">The transaction protocol is specified using the `transactionProtocol` attribute.</span></span> <span data-ttu-id="4246f-122">Ancak, bu öznitelik yalnızca ws-at protokolünü kullanabilmesi için `wsHttpBinding`, bu öznitelik sistem tarafından sağlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="4246f-122">However, this attribute is absent from the system-provided `wsHttpBinding`, because this binding can only use the WS-AT protocol.</span></span>  
  
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
  
### <a name="controlling-the-completion-of-a-transaction"></a><span data-ttu-id="4246f-123">Bir işlemin tamamlanmasını denetleme</span><span class="sxs-lookup"><span data-stu-id="4246f-123">Controlling the completion of a transaction</span></span>  
  
1. <span data-ttu-id="4246f-124">Varsayılan olarak, işlenmeyen özel durum oluşturulmaz, WCF işlemleri işlemleri otomatik olarak tamamlar.</span><span class="sxs-lookup"><span data-stu-id="4246f-124">By default, WCF operations automatically complete transactions if no unhandled exceptions are thrown.</span></span> <span data-ttu-id="4246f-125">Bu davranışı <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> özelliğini <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> ve yöntemini kullanarak değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4246f-125">You can modify this behavior by using the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property and the <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> method.</span></span> <span data-ttu-id="4246f-126">Bir işlemin başka bir işlemle aynı işlem içinde gerçekleşmesi gerektiği zaman (örneğin, bir borç ve kredi işlemi), <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> `false` özelliği aşağıdaki şekildegösterildiğigibiolarakayarlayarakotomatiktamamlamadavranışınıdevredışıbırakabilirsiniz`Debit` işlem örneği.</span><span class="sxs-lookup"><span data-stu-id="4246f-126">When an operation is required to occur within the same transaction as another operation (for example, a debit and credit operation), you can disable the autocomplete behavior by setting the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property to `false` as shown in the following `Debit` operation example.</span></span> <span data-ttu-id="4246f-127">`true` İşleminkullandığı<xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> işlem, <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> işlem`Credit1`içinde gösterildiği gibi, özelliği olarak ayarlanmış bir yöntem çağrılana kadar veya yöntem açıkça işaretlemek üzere çağrıldığında bu işlem tamamlanmaz. `Debit` işlemde gösterildiği `Credit2`gibi işlem tamamlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4246f-127">The transaction the `Debit` operation uses is not completed until a method with the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property set to `true` is called, as shown in the operation `Credit1`, or when the <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> method is called to explicitly mark the transaction as complete, as shown in the operation `Credit2`.</span></span> <span data-ttu-id="4246f-128">İki kredi işleminin illüstrasyon amacıyla gösterildiğini ve tek bir kredi işleminin daha tipik olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="4246f-128">Note that the two credit operations are shown for illustration purposes, and that a single credit operation would be more typical.</span></span>  
  
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
  
2. <span data-ttu-id="4246f-129">İşlem bağıntı amaçları doğrultusunda, <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> özelliği olarak `false` ayarlamak, bir oturumsuz bağlamanın kullanılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="4246f-129">For the purposes of transaction correlation, setting the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property to `false` requires the use of a sessionful binding.</span></span> <span data-ttu-id="4246f-130">Bu gereksinim, `SessionMode` <xref:System.ServiceModel.ServiceContractAttribute>üzerinde özelliği ile belirtilir.</span><span class="sxs-lookup"><span data-stu-id="4246f-130">This requirement is specified with the `SessionMode` property on the <xref:System.ServiceModel.ServiceContractAttribute>.</span></span>  
  
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
  
### <a name="controlling-the-lifetime-of-a-transactional-service-instance"></a><span data-ttu-id="4246f-131">Bir işlem hizmeti örneğinin ömrünü denetleme</span><span class="sxs-lookup"><span data-stu-id="4246f-131">Controlling the lifetime of a transactional service instance</span></span>  
  
1. <span data-ttu-id="4246f-132">WCF, bir <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> işlem tamamlandığında temeldeki hizmet örneğinin serbest bırakılıp başlatılmayacağını belirtmek için özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="4246f-132">WCF uses the <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> property to specify whether the underlying service instance is released when a transaction completes.</span></span> <span data-ttu-id="4246f-133">Bu varsayılan olarak `true`, aksi belirtilmedikçe, WCF etkin ve öngörülebilir bir "tam zamanında" etkinleştirme davranışı sergiler.</span><span class="sxs-lookup"><span data-stu-id="4246f-133">Since this defaults to `true`, unless configured otherwise, WCF exhibits an efficient and predictable "just-in-time" activation behavior.</span></span> <span data-ttu-id="4246f-134">Sonraki bir işlem üzerindeki bir hizmete yapılan çağrılar, önceki işlemin durumuna göre hiçbir şekilde, yeni bir hizmet örneğini garanti altına alır.</span><span class="sxs-lookup"><span data-stu-id="4246f-134">Calls to a service on a subsequent transaction are assured a new service instance with no remnants of the previous transaction's state.</span></span> <span data-ttu-id="4246f-135">Bu genellikle yararlı olsa da, bazen işlem tamamlandıktan sonra hizmet örneği içinde durumu korumak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4246f-135">While this is often useful, sometimes you may want to maintain state within the service instance beyond the transaction completion.</span></span> <span data-ttu-id="4246f-136">Bunun örnekleri, gerekli durum veya kaynak tanıtıcılarının alınması veya edilmeyen ne kadar pahalı olduğu durumdur.</span><span class="sxs-lookup"><span data-stu-id="4246f-136">Examples of this would be when required state or handles to resources are expensive to retrieve or reconstitute.</span></span> <span data-ttu-id="4246f-137">Bunu, <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> özelliğini olarak `false`ayarlayarak yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4246f-137">You can do this by setting the <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> property to `false`.</span></span> <span data-ttu-id="4246f-138">Bu ayar ile, örnek ve ilişkili herhangi bir durum sonraki çağrılarda kullanılabilir olacaktır.</span><span class="sxs-lookup"><span data-stu-id="4246f-138">With that setting, the instance and any associated state will be available on subsequent calls.</span></span> <span data-ttu-id="4246f-139">Bunu kullanırken, durum ve işlemlerin ne zaman ve nasıl temizleneceği ve tamamlanalınacağını göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="4246f-139">When using this, give careful consideration to when and how state and transactions will be cleared and completed.</span></span> <span data-ttu-id="4246f-140">Aşağıdaki örnek, örneği `runningTotal` değişkenle birlikte tutarak bunun nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4246f-140">The following sample demonstrates how to do this by maintaining the instance with the `runningTotal` variable.</span></span>  
  
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
    > <span data-ttu-id="4246f-141">Örnek yaşam süresi, hizmete iç bir davranış olduğundan ve <xref:System.ServiceModel.ServiceBehaviorAttribute> özelliği aracılığıyla denetlendiğinden, örnek davranışını ayarlamak için hizmet yapılandırmasında veya hizmet sözleşmesinde hiçbir değişiklik yapılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="4246f-141">Since the instance lifetime is a behavior that is internal to the service, and controlled through the <xref:System.ServiceModel.ServiceBehaviorAttribute> property, no modification to the service configuration or service contract is required to set the instance behavior.</span></span> <span data-ttu-id="4246f-142">Ayrıca, hat bunun gösterimini içermez.</span><span class="sxs-lookup"><span data-stu-id="4246f-142">In addition, the wire will contain no representation of this.</span></span>
