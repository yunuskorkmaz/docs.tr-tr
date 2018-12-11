---
title: 'Nasıl Yapılır: İşlemsel hizmet oluşturma'
ms.date: 03/30/2017
ms.assetid: 1bd2e4ed-a557-43f9-ba98-4c70cb75c154
ms.openlocfilehash: c4d2db0ca912be8840788bc363f86d621fa76e34
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245645"
---
# <a name="how-to-create-a-transactional-service"></a>Nasıl Yapılır: İşlemsel hizmet oluşturma
Bu örnek, bir işlem hizmeti ve hizmet işlemleri koordine etmek için bir istemci tarafından başlatılan işlem kullanımı oluşturma çeşitli yönlerini gösterir.  
  
### <a name="creating-a-transactional-service"></a>İşlemsel hizmet oluşturma  
  
1.  Bir hizmet sözleşmesi oluşturma ve istenen ayarından işlemleriyle açıklama <xref:System.ServiceModel.TransactionFlowOption> gelen işlem gereksinimlerini belirtmek için sabit listesi. Ayrıca yerleştirebilirsiniz Not <xref:System.ServiceModel.TransactionFlowAttribute> uygulanmakta olan hizmet sınıfı üzerinde. Bu, bu işlem ayarları kullanmak yerine her uygulama için bir arabirim için tek bir uygulama sağlar.  
  
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
  
2.  Bir uygulama sınıfı oluşturun ve kullanın <xref:System.ServiceModel.ServiceBehaviorAttribute> isteğe bağlı olarak belirtmek için bir <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> ve <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>. Çoğu durumda, varsayılan unutmamalısınız <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> 60 saniye ve varsayılan <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> , `Unspecified` uygundur. Her işlem için kullanabileceğiniz <xref:System.ServiceModel.OperationBehaviorAttribute> iş yöntemi içinde gerçekleştirip gerçekleştirmediğini belirlemek için öznitelik değerini göre işlem kapsamı kapsamında <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> özniteliği. Bu durumda, işlem için kullanılan `Add` yöntem istemciden aktarılan zorunlu gelen işlem aynı olduğunu ve işlem için kullanılan `Subtract` yöntemi ise ya da aynı gelen işlem olarak bir aktarılan İstemci, veya yeni bir örtük olarak ve yerel olarak oluşturulan işlem.  
  
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
  
3.  İşlem bağlamı akışını olduğunu, belirterek yapılandırma dosyası ve bunu yapmak için kullanılan protokoller bağlamaları yapılandırın. Daha fazla bilgi için [ServiceModel işlem Yapılandırması](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md). Uç nokta öğenin belirtilen bağlama türü özellikle `binding` özniteliği. [ \<Uç noktası >](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) öğesi içeren bir `bindingConfiguration` adlı bir bağlama yapılandırmasını başvuran öznitelik `transactionalOleTransactionsTcpBinding`aşağıdaki örnek yapılandırmada gösterildiği gibi.  
  
    ```xml  
    <service name="CalculatorService">  
      <endpoint address="net.tcp://localhost:8008/CalcService"  
        binding="netTcpBinding"  
        bindingConfiguration="transactionalOleTransactionsTcpBinding"  
        contract="ICalculator"  
        name="OleTransactions_endpoint" />  
    </service>  
    ```  
  
     İşlem akışı kullanarak yapılandırma düzeyinde etkinleştirilir `transactionFlow` özniteliği ve işlem protokolünü belirtilen kullanarak `transactionProtocol` aşağıdaki yapılandırmayı gösterildiği gibi öznitelik.  
  
    ```xml  
    <bindings>  
      <netTcpBinding>  
        <binding name="transactionalOleTransactionsTcpBinding"  
          transactionFlow="true"  
          transactionProtocol="OleTransactions"/>  
      </netTcpBinding>  
    </bindings>  
    ```  
  
### <a name="supporting-multiple-transaction-protocols"></a>Birden çok işlem protokollerin desteklenmesi  
  
1.  En iyi performans için bir istemci ve Windows Communication Foundation (WCF) kullanılarak yazılmış hizmeti içeren senaryolar için OleTransactions Protokolü kullanmanız gerekir. Ancak, üçüncü taraf protokol yığınlarının ile birlikte çalışabilirlik gerektiğinde WS-AtomicTransaction (WS-AT) protokolü senaryoları için kullanışlıdır. WCF hizmetleri iki protokolü de uygun protokole özgü bağlamaları ile birden fazla uç nokta sağlayarak aşağıdaki örnek yapılandırmada gösterildiği gibi kabul edecek şekilde yapılandırabilirsiniz.  
  
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
  
     İşlem protokolünü kullanarak belirtilen `transactionProtocol` özniteliği. Ancak, bu özniteliği yoksa, sistem tarafından sağlanan gelen `wsHttpBinding`, çünkü bu bağlama yalnızca WS-AT protokolünü kullanabilirsiniz.  
  
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
  
### <a name="controlling-the-completion-of-a-transaction"></a>İşlem tamamlandığında denetleme  
  
1.  Eğer işlenmeyen özel durumlar harekete varsayılan olarak, WCF işlem işlemleri otomatik olarak tamamlar. Kullanarak bu davranışı değiştirebilirsiniz <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> özelliği ve <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> yöntemi. Bir işlem başka bir işlem (örneğin, bir banka ve iade işlemi) olarak aynı işlem içinde gerçekleşmesi için gerekli olduğunda, otomatik tamamlama davranışını ayarlayarak devre dışı bırakabilirsiniz <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> özelliğini `false` aşağıda gösterildiği gibi `Debit` işlem örneği. İşlem `Debit` işlemi kullanan bir yöntemle kadar tamamlanmaz <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> özelliğini `true` çağrılır, işlemde gösterildiği `Credit1`, veya <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> yöntemi açıkça çağrılmaz işlem işleme gösterildiği gibi tam `Credit2`. Gösterim amacıyla iki kredi işlem gösterilir ve tek bir işlem kredi daha tipik olacağını unutmayın.  
  
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
  
2.  Ayarlama, işlem korelasyon amaçları için <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> özelliğini `false` kapatamaması bağlama kullanılmasını gerektirir. Bu gereksinim, ile belirtilen `SessionMode` özellikte <xref:System.ServiceModel.ServiceContractAttribute>.  
  
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
  
### <a name="controlling-the-lifetime-of-a-transactional-service-instance"></a>Bir işlem hizmeti örneğinin kullanım ömrü denetleme  
  
1.  WCF kullanan <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> bir işlem tamamlandığında, temel alınan hizmet örneği serbest olup olmadığını belirlemek için özellik. Bu varsayılan olarak bu yana `true`, aksi durumda, WCF sergiler bir verimli ve tahmin edilebilir "just-in-time" etkinleştirme davranışı yapılandırılmış sürece. Bir sonraki işlemde bir hizmete çağrı hiçbir kalanları önceki işlem durumu ile yeni bir hizmet örneği geleceğinden emin olursunuz. Bazen bu genellikle kullanışlı olmakla birlikte, hizmet örneği işlem tamamlandığında ötesinde içinde durumunu korumak isteyebilirsiniz. Buna örnek olarak, gerekli durumu veya kaynakları tanıtıcıları almak veya yeniden oluşturmak pahalı olduğunda olacaktır. Bunu ayarlayarak yapabilirsiniz <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> özelliğini `false`. Bu ayar, örneği ve herhangi bir ilişkili durumu üzerinde yapılan sonraki çağrılar kullanıma sunulacaktır. Bu kullanırken dikkatli için zaman verin ve nasıl durumunu ve işlem temizlenmiş tamamlandı ve. Aşağıdaki örnek bu örnekle tutarak bunu nasıl yapacağınızı gösterir `runningTotal` değişkeni.  
  
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
    >  İç hizmet ve aracılığıyla denetlenen bir davranış örneğinin kullanım ömrü olduğundan <xref:System.ServiceModel.ServiceBehaviorAttribute> özelliği, hizmet yapılandırması veya hizmet sözleşmesini hiçbir değişiklik yapmadan örnek davranışını ayarlamanız gerekiyor. Ayrıca, kablo bu herhangi bir gösterimini içerir.
