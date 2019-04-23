---
title: 'Nasıl yapılır: İşlemsel Hizmet Oluşturma'
ms.date: 03/30/2017
ms.assetid: 1bd2e4ed-a557-43f9-ba98-4c70cb75c154
ms.openlocfilehash: 7f7f060db5a4ffd66524e220e3e3291debd8a3fc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59769664"
---
# <a name="how-to-create-a-transactional-service"></a><span data-ttu-id="f756e-102">Nasıl yapılır: İşlemsel Hizmet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f756e-102">How to: Create a Transactional Service</span></span>
<span data-ttu-id="f756e-103">Bu örnek, bir işlem hizmeti ve hizmet işlemleri koordine etmek için bir istemci tarafından başlatılan işlem kullanımı oluşturma çeşitli yönlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f756e-103">This sample demonstrates various aspects of creating a transactional service and the use of a client-initiated transaction to coordinate service operations.</span></span>  
  
### <a name="creating-a-transactional-service"></a><span data-ttu-id="f756e-104">İşlemsel hizmet oluşturma</span><span class="sxs-lookup"><span data-stu-id="f756e-104">Creating a transactional service</span></span>  
  
1. <span data-ttu-id="f756e-105">Bir hizmet sözleşmesi oluşturma ve istenen ayarından işlemleriyle açıklama <xref:System.ServiceModel.TransactionFlowOption> gelen işlem gereksinimlerini belirtmek için sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="f756e-105">Create a service contract and annotate the operations with the desired setting from the <xref:System.ServiceModel.TransactionFlowOption> enumeration to specify the incoming transaction requirements.</span></span> <span data-ttu-id="f756e-106">Ayrıca yerleştirebilirsiniz Not <xref:System.ServiceModel.TransactionFlowAttribute> uygulanmakta olan hizmet sınıfı üzerinde.</span><span class="sxs-lookup"><span data-stu-id="f756e-106">Note that you can also place the <xref:System.ServiceModel.TransactionFlowAttribute> on the service class being implemented.</span></span> <span data-ttu-id="f756e-107">Bu, bu işlem ayarları kullanmak yerine her uygulama için bir arabirim için tek bir uygulama sağlar.</span><span class="sxs-lookup"><span data-stu-id="f756e-107">This allows for a single implementation of an interface to use these transaction settings, instead of every implementation.</span></span>  
  
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
  
2. <span data-ttu-id="f756e-108">Bir uygulama sınıfı oluşturun ve kullanın <xref:System.ServiceModel.ServiceBehaviorAttribute> isteğe bağlı olarak belirtmek için bir <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> ve <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>.</span><span class="sxs-lookup"><span data-stu-id="f756e-108">Create an implementation class, and use the <xref:System.ServiceModel.ServiceBehaviorAttribute> to optionally specify a <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> and a <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>.</span></span> <span data-ttu-id="f756e-109">Çoğu durumda, varsayılan unutmamalısınız <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> 60 saniye ve varsayılan <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> , `Unspecified` uygundur.</span><span class="sxs-lookup"><span data-stu-id="f756e-109">You should note that in many cases, the default <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> of 60 seconds and the default <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> of `Unspecified` are appropriate.</span></span> <span data-ttu-id="f756e-110">Her işlem için kullanabileceğiniz <xref:System.ServiceModel.OperationBehaviorAttribute> iş yöntemi içinde gerçekleştirip gerçekleştirmediğini belirlemek için öznitelik değerini göre işlem kapsamı kapsamında <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="f756e-110">For each operation, you can use the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute to specify whether work performed within the method should occur within the scope of a transaction scope according to the value of the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> attribute.</span></span> <span data-ttu-id="f756e-111">Bu durumda, işlem için kullanılan `Add` yöntem istemciden aktarılan zorunlu gelen işlem aynı olduğunu ve işlem için kullanılan `Subtract` yöntemi ise ya da aynı gelen işlem olarak bir aktarılan İstemci, veya yeni bir örtük olarak ve yerel olarak oluşturulan işlem.</span><span class="sxs-lookup"><span data-stu-id="f756e-111">In this case, the transaction used for the `Add` method is the same as the mandatory incoming transaction that is flowed from the client, and the transaction used for the `Subtract` method is either the same as the incoming transaction if one was flowed from the client, or a new implicitly and locally created transaction.</span></span>  
  
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
  
3. <span data-ttu-id="f756e-112">İşlem bağlamı akışını olduğunu, belirterek yapılandırma dosyası ve bunu yapmak için kullanılan protokoller bağlamaları yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="f756e-112">Configure the bindings in the configuration file, specifying that the transaction context should be flowed, and the protocols to be used to do so.</span></span> <span data-ttu-id="f756e-113">Daha fazla bilgi için [ServiceModel işlem Yapılandırması](servicemodel-transaction-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="f756e-113">For more information, see [ServiceModel Transaction Configuration](servicemodel-transaction-configuration.md).</span></span> <span data-ttu-id="f756e-114">Uç nokta öğenin belirtilen bağlama türü özellikle `binding` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="f756e-114">Specifically, the binding type is specified in the endpoint element’s `binding` attribute.</span></span> <span data-ttu-id="f756e-115">[ \<Uç noktası >](../../configure-apps/file-schema/wcf/endpoint-element.md) öğesi içeren bir `bindingConfiguration` adlı bir bağlama yapılandırmasını başvuran öznitelik `transactionalOleTransactionsTcpBinding`aşağıdaki örnek yapılandırmada gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="f756e-115">The [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) element contains a `bindingConfiguration` attribute that references a binding configuration named `transactionalOleTransactionsTcpBinding`, as shown in the following sample configuration.</span></span>  
  
    ```xml  
    <service name="CalculatorService">  
      <endpoint address="net.tcp://localhost:8008/CalcService"  
        binding="netTcpBinding"  
        bindingConfiguration="transactionalOleTransactionsTcpBinding"  
        contract="ICalculator"  
        name="OleTransactions_endpoint" />  
    </service>  
    ```  
  
     <span data-ttu-id="f756e-116">İşlem akışı kullanarak yapılandırma düzeyinde etkinleştirilir `transactionFlow` özniteliği ve işlem protokolünü belirtilen kullanarak `transactionProtocol` aşağıdaki yapılandırmayı gösterildiği gibi öznitelik.</span><span class="sxs-lookup"><span data-stu-id="f756e-116">Transaction flow is enabled at the configuration level by using the `transactionFlow` attribute, and the transaction protocol is specified using the `transactionProtocol` attribute, as shown in the following configuration.</span></span>  
  
    ```xml  
    <bindings>  
      <netTcpBinding>  
        <binding name="transactionalOleTransactionsTcpBinding"  
          transactionFlow="true"  
          transactionProtocol="OleTransactions"/>  
      </netTcpBinding>  
    </bindings>  
    ```  
  
### <a name="supporting-multiple-transaction-protocols"></a><span data-ttu-id="f756e-117">Birden çok işlem protokollerin desteklenmesi</span><span class="sxs-lookup"><span data-stu-id="f756e-117">Supporting multiple transaction protocols</span></span>  
  
1. <span data-ttu-id="f756e-118">En iyi performans için bir istemci ve Windows Communication Foundation (WCF) kullanılarak yazılmış hizmeti içeren senaryolar için OleTransactions Protokolü kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f756e-118">For optimal performance, you should use the OleTransactions protocol for scenarios involving a client and service written using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="f756e-119">Ancak, üçüncü taraf protokol yığınlarının ile birlikte çalışabilirlik gerektiğinde WS-AtomicTransaction (WS-AT) protokolü senaryoları için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="f756e-119">However, the WS-AtomicTransaction (WS-AT) protocol is useful for scenarios when interoperability with third-party protocol stacks is required.</span></span> <span data-ttu-id="f756e-120">WCF hizmetleri iki protokolü de uygun protokole özgü bağlamaları ile birden fazla uç nokta sağlayarak aşağıdaki örnek yapılandırmada gösterildiği gibi kabul edecek şekilde yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f756e-120">You can configure WCF services to accept both protocols by providing multiple endpoints with appropriate protocol-specific bindings, as shown in the following sample configuration.</span></span>  
  
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
  
     <span data-ttu-id="f756e-121">İşlem protokolünü kullanarak belirtilen `transactionProtocol` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="f756e-121">The transaction protocol is specified using the `transactionProtocol` attribute.</span></span> <span data-ttu-id="f756e-122">Ancak, bu özniteliği yoksa, sistem tarafından sağlanan gelen `wsHttpBinding`, çünkü bu bağlama yalnızca WS-AT protokolünü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f756e-122">However, this attribute is absent from the system-provided `wsHttpBinding`, because this binding can only use the WS-AT protocol.</span></span>  
  
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
  
### <a name="controlling-the-completion-of-a-transaction"></a><span data-ttu-id="f756e-123">İşlem tamamlandığında denetleme</span><span class="sxs-lookup"><span data-stu-id="f756e-123">Controlling the completion of a transaction</span></span>  
  
1. <span data-ttu-id="f756e-124">Eğer işlenmeyen özel durumlar harekete varsayılan olarak, WCF işlem işlemleri otomatik olarak tamamlar.</span><span class="sxs-lookup"><span data-stu-id="f756e-124">By default, WCF operations automatically complete transactions if no unhandled exceptions are thrown.</span></span> <span data-ttu-id="f756e-125">Kullanarak bu davranışı değiştirebilirsiniz <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> özelliği ve <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f756e-125">You can modify this behavior by using the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property and the <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> method.</span></span> <span data-ttu-id="f756e-126">Bir işlem başka bir işlem (örneğin, bir banka ve iade işlemi) olarak aynı işlem içinde gerçekleşmesi için gerekli olduğunda, otomatik tamamlama davranışını ayarlayarak devre dışı bırakabilirsiniz <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> özelliğini `false` aşağıda gösterildiği gibi `Debit` işlem örneği.</span><span class="sxs-lookup"><span data-stu-id="f756e-126">When an operation is required to occur within the same transaction as another operation (for example, a debit and credit operation), you can disable the autocomplete behavior by setting the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property to `false` as shown in the following `Debit` operation example.</span></span> <span data-ttu-id="f756e-127">İşlem `Debit` işlemi kullanan bir yöntemle kadar tamamlanmaz <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> özelliğini `true` çağrılır, işlemde gösterildiği `Credit1`, veya <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> yöntemi açıkça çağrılmaz işlem işleme gösterildiği gibi tam `Credit2`.</span><span class="sxs-lookup"><span data-stu-id="f756e-127">The transaction the `Debit` operation uses is not completed until a method with the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property set to `true` is called, as shown in the operation `Credit1`, or when the <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> method is called to explicitly mark the transaction as complete, as shown in the operation `Credit2`.</span></span> <span data-ttu-id="f756e-128">Gösterim amacıyla iki kredi işlem gösterilir ve tek bir işlem kredi daha tipik olacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f756e-128">Note that the two credit operations are shown for illustration purposes, and that a single credit operation would be more typical.</span></span>  
  
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
  
2. <span data-ttu-id="f756e-129">Ayarlama, işlem korelasyon amaçları için <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> özelliğini `false` kapatamaması bağlama kullanılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f756e-129">For the purposes of transaction correlation, setting the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property to `false` requires the use of a sessionful binding.</span></span> <span data-ttu-id="f756e-130">Bu gereksinim, ile belirtilen `SessionMode` özellikte <xref:System.ServiceModel.ServiceContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="f756e-130">This requirement is specified with the `SessionMode` property on the <xref:System.ServiceModel.ServiceContractAttribute>.</span></span>  
  
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
  
### <a name="controlling-the-lifetime-of-a-transactional-service-instance"></a><span data-ttu-id="f756e-131">Bir işlem hizmeti örneğinin kullanım ömrü denetleme</span><span class="sxs-lookup"><span data-stu-id="f756e-131">Controlling the lifetime of a transactional service instance</span></span>  
  
1. <span data-ttu-id="f756e-132">WCF kullanan <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> bir işlem tamamlandığında, temel alınan hizmet örneği serbest olup olmadığını belirlemek için özellik.</span><span class="sxs-lookup"><span data-stu-id="f756e-132">WCF uses the <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> property to specify whether the underlying service instance is released when a transaction completes.</span></span> <span data-ttu-id="f756e-133">Bu varsayılan olarak bu yana `true`, aksi durumda, WCF sergiler bir verimli ve tahmin edilebilir "just-in-time" etkinleştirme davranışı yapılandırılmış sürece.</span><span class="sxs-lookup"><span data-stu-id="f756e-133">Since this defaults to `true`, unless configured otherwise, WCF exhibits an efficient and predictable "just-in-time" activation behavior.</span></span> <span data-ttu-id="f756e-134">Bir sonraki işlemde bir hizmete çağrı hiçbir kalanları önceki işlem durumu ile yeni bir hizmet örneği geleceğinden emin olursunuz.</span><span class="sxs-lookup"><span data-stu-id="f756e-134">Calls to a service on a subsequent transaction are assured a new service instance with no remnants of the previous transaction's state.</span></span> <span data-ttu-id="f756e-135">Bazen bu genellikle kullanışlı olmakla birlikte, hizmet örneği işlem tamamlandığında ötesinde içinde durumunu korumak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f756e-135">While this is often useful, sometimes you may want to maintain state within the service instance beyond the transaction completion.</span></span> <span data-ttu-id="f756e-136">Buna örnek olarak, gerekli durumu veya kaynakları tanıtıcıları almak veya yeniden oluşturmak pahalı olduğunda olacaktır.</span><span class="sxs-lookup"><span data-stu-id="f756e-136">Examples of this would be when required state or handles to resources are expensive to retrieve or reconstitute.</span></span> <span data-ttu-id="f756e-137">Bunu ayarlayarak yapabilirsiniz <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> özelliğini `false`.</span><span class="sxs-lookup"><span data-stu-id="f756e-137">You can do this by setting the <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> property to `false`.</span></span> <span data-ttu-id="f756e-138">Bu ayar, örneği ve herhangi bir ilişkili durumu üzerinde yapılan sonraki çağrılar kullanıma sunulacaktır.</span><span class="sxs-lookup"><span data-stu-id="f756e-138">With that setting, the instance and any associated state will be available on subsequent calls.</span></span> <span data-ttu-id="f756e-139">Bu kullanırken dikkatli için zaman verin ve nasıl durumunu ve işlem temizlenmiş tamamlandı ve.</span><span class="sxs-lookup"><span data-stu-id="f756e-139">When using this, give careful consideration to when and how state and transactions will be cleared and completed.</span></span> <span data-ttu-id="f756e-140">Aşağıdaki örnek bu örnekle tutarak bunu nasıl yapacağınızı gösterir `runningTotal` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="f756e-140">The following sample demonstrates how to do this by maintaining the instance with the `runningTotal` variable.</span></span>  
  
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
    >  <span data-ttu-id="f756e-141">İç hizmet ve aracılığıyla denetlenen bir davranış örneğinin kullanım ömrü olduğundan <xref:System.ServiceModel.ServiceBehaviorAttribute> özelliği, hizmet yapılandırması veya hizmet sözleşmesini hiçbir değişiklik yapmadan örnek davranışını ayarlamanız gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="f756e-141">Since the instance lifetime is a behavior that is internal to the service, and controlled through the <xref:System.ServiceModel.ServiceBehaviorAttribute> property, no modification to the service configuration or service contract is required to set the instance behavior.</span></span> <span data-ttu-id="f756e-142">Ayrıca, kablo bu herhangi bir gösterimini içerir.</span><span class="sxs-lookup"><span data-stu-id="f756e-142">In addition, the wire will contain no representation of this.</span></span>
