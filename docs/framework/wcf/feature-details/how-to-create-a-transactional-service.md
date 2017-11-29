---
title: "Nasıl yapılır: İşlemsel Hizmet Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1bd2e4ed-a557-43f9-ba98-4c70cb75c154
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a7ef8d4778b21d33501e3f3d4478b722bf1e1cc3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-transactional-service"></a>Nasıl yapılır: İşlemsel Hizmet Oluşturma
Bu örnek, çeşitli yönlerini oluşturma işlemsel hizmet ve hizmet işlemleri koordine etmek için bir istemci tarafından başlatılan işlem kullanımını gösterir.  
  
### <a name="creating-a-transactional-service"></a>İşlemsel hizmet oluşturma  
  
1.  Bir hizmet sözleşmesi oluşturma ve istenen ayarından işlemleriyle açıklama <xref:System.ServiceModel.TransactionFlowOption> numaralandırma gelen işlem gereksinimleri belirtin. Ayrıca, yerleştirebilirsiniz Not <xref:System.ServiceModel.TransactionFlowAttribute> uygulanan hizmet sınıfı üzerinde. Bu, bu işlem ayarları yerine her uygulama kullanmak için bir arabirim için tek bir uygulama sağlar.  
  
    ```  
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
  
2.  Bir uygulama sınıfı oluşturma ve kullanma <xref:System.ServiceModel.ServiceBehaviorAttribute> isteğe bağlı olarak belirtmek için bir <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> ve <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>. Çoğu durumda, varsayılan unutmamalısınız <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> 60 saniye ve varsayılan <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> , `Unspecified` uygundur. Her işlem için kullandığınız <xref:System.ServiceModel.OperationBehaviorAttribute> iş yöntemi içinde gerçekleştirilen olup olmadığını belirlemek için öznitelik değerini göre bir işlem kapsamı kapsamı içinde gerçekleşmelidir <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> özniteliği. Bu durumda, işlem için kullanılan `Add` yöntemi istemciden aktarılan zorunlu gelen işlem ile aynı olan ve işlem için kullanılan `Subtract` yöntemi ise ya da aynı gelen işlemin bir eylemine aktarıldı İstemci, veya yeni bir örtük olarak ve yerel olarak oluşturulan işlemi.  
  
    ```  
    [ServiceBehavior(  
        TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable,  
        TransactionTimeout = "00:00:45")]  
    public class CalculatorService : ICalculator  
    {  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Add(double n1, double n2)  
        {  
            // Perform transactional operation  
            RecordToLog(String.Format("Adding {0} to {1}", n1, n2));  
            return n1 + n2;  
        }  
  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Subtract(double n1, double n2)  
        {  
            // Perform transactional operation  
            RecordToLog(String.Format("Subtracting {0} from {1}", n2, n1));  
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
  
3.  Bağlamaları işlem bağlamı aktarılan olduğunu, belirterek yapılandırma dosyası ve bunu yapmak için kullanılan protokolleri yapılandırın. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][ServiceModel işlem Yapılandırması](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md). Uç nokta öğesinin belirtilen bağlama türü özellikle `binding` özniteliği. [ \<Uç noktası >](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) öğesi içeren bir `bindingConfiguration` adlı bir bağlama yapılandırması başvuran özniteliği `transactionalOleTransactionsTcpBinding`aşağıdaki örnek yapılandırmada gösterildiği gibi.  
  
    ```xml  
    <service name="CalculatorService">  
      <endpoint address="net.tcp://localhost:8008/CalcService"  
        binding="netTcpBinding"  
        bindingConfiguration="transactionalOleTransactionsTcpBinding"  
        contract="ICalculator"  
        name="OleTransactions_endpoint" />  
    </service>  
    ```  
  
     İşlem akışını kullanarak yapılandırma düzeyinde etkinleştirilir `transactionFlow` özniteliği ve işlem protokolü belirtilmezse `transactionProtocol` aşağıdaki yapılandırmada gösterildiği gibi öznitelik.  
  
    ```xml  
    <bindings>  
      <netTcpBinding>  
        <binding name="transactionalOleTransactionsTcpBinding"  
          transactionFlow="true"  
          transactionProtocol="OleTransactions"/>  
      </netTcpBinding>  
    </bindings>  
    ```  
  
### <a name="supporting-multiple-transaction-protocols"></a>Birden çok işlem protokolleri destekleme  
  
1.  En iyi performans için bir istemci ve hizmet kullanılarak yazılmış içeren senaryoları için OleTransactions Protokolü kullanması gereken [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Ancak, üçüncü taraf protokol yığını ile birlikte çalışabilirlik gerekli olduğunda WS-AtomicTransaction (WS-AT) protokolü senaryoları için kullanışlıdır. Yapılandırabileceğiniz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iki protokolü de uygun protokole özgü bağlamalarla birden çok uç nokta sağlayarak aşağıdaki örnek yapılandırmada gösterildiği gibi kabul etmek üzere Hizmetleri.  
  
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
  
     İşlem protokolü kullanarak belirtilen `transactionProtocol` özniteliği. Ancak, bu öznitelik eksik sistem tarafından sağlanan gelen `wsHttpBinding`, çünkü bu bağlama yalnızca WS-AT protokolü kullanabilirsiniz.  
  
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
  
### <a name="controlling-the-completion-of-a-transaction"></a>Bir işlemin tamamlanmasından denetleme  
  
1.  Varsayılan olarak, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] işlemleri hiçbir işlenmeyen özel durumlar varsa işlemleri otomatik olarak tamamlar. Kullanarak bu davranışı değiştirebilirsiniz <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> özelliği ve <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> yöntemi. Bir işlem başka bir işlem (örneğin, Borç ve alacak işlemi) olarak aynı işlem içinde gerçekleşmesi için gerekli olduğunda, otomatik tamamlama davranışı ayarlayarak devre dışı bırakabilirsiniz <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> özelliğine `false` aşağıda gösterildiği gibi `Debit` işlemi örnek. İşlem `Debit` işlemi kullanan bir yöntemle kadar tamamlanmaz <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> özelliğini `true` işlemde gösterildiği gibi denir `Credit1`, veya ne zaman <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> yöntemi açık olarak işaretlemek için çağrılır işlem işlemde gösterildiği gibi tam `Credit2`. İki kredi işlemleri gösterim amacıyla gösterilir ve tek bir işlem kredi daha tipik olacaktır unutmayın.  
  
    ```  
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
  
2.  Ayarlama, işlem bağıntı amacıyla <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> özelliğine `false` süre sonuyla bağlama kullanılmasını gerektirir. Bu gereksinim ile belirtilen `SessionMode` özelliği <xref:System.ServiceModel.ServiceContractAttribute>.  
  
    ```  
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
  
### <a name="controlling-the-lifetime-of-a-transactional-service-instance"></a>Bir işlem hizmet örneği ömrü denetleme  
  
1.  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]kullanan <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> özelliği bir işlem tamamlandığında, temel alınan hizmet örneği yayımlanan olup olmadığını belirtin. Bu varsayılan olarak bu yana `true`, aksi takdirde yapılandırılmadıkça [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] verimli ve öngörülebilir "tam zamanında" etkinleştirme davranışı sergiler. Bir hizmete bir sonraki işlem üzerinde yapılan çağrı hiçbir kalanları önceki işlemdeki durumu ile yeni bir hizmet örneği garanti. Bazen bu genellikle yararlı olsa da, işlem tamamlandığında ötesinde hizmet örneği içinde durumunu korumak isteyebilirsiniz. Gerekli durumu veya kaynakları işleyicilerine alınamıyor veya yeniden oluşturma pahalı olduğunda bu örnekleri olacaktır. Bunu ayarlayarak yapabilirsiniz <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> özelliğine `false`. Bu ayar, örneği ve herhangi bir ilişkili durum sonraki çağrılar kullanılabilir. Bu kullanırken için ne zaman etkinleştirildiğine ve nasıl durumu ve işlemleri temizlenmiş tamamlandı ve. Aşağıdaki örnek bu örnekle tutarak bunu nasıl yapacağınızı gösterir `runningTotal` değişkeni.  
  
    ```  
    [ServiceBehavior(TransactionIsolationLevel = [ServiceBehavior(  
        ReleaseServiceInstanceOnTransactionComplete = false)]  
    public class CalculatorService : ICalculator  
    {  
        double runningTotal = 0;  
  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Add(double n)  
        {  
            // Perform transactional operation  
            RecordToLog(String.Format("Adding {0} to {1}", n, runningTotal));  
            runningTotal = runningTotal + n;  
            return runningTotal;  
        }  
  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Subtract(double n)  
        {  
            // Perform transactional operation  
            RecordToLog(String.Format("Subtracting {0} from {1}", n, runningTotal));  
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
    >  Örnek kullanım ömrü hizmetine iç ve aracılığıyla denetlenen bir davranış olduğundan <xref:System.ServiceModel.ServiceBehaviorAttribute> özelliği, hizmet yapılandırması veya hizmet sözleşmesini hiçbir değişiklik yapmadan örneği davranışını ayarlamak için gereklidir. Ayrıca, kablo bu hiçbir gösterimini içerir.
