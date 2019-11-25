---
title: İş Akışı Hizmetlerine İşlemlerin Giriş ve Çıkış Akışını Gerçekleştirme
ms.date: 03/30/2017
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
ms.openlocfilehash: ea14bc651258684fd31940aa6b88f9731348dcd1
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73978277"
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a>İş Akışı Hizmetlerine İşlemlerin Giriş ve Çıkış Akışını Gerçekleştirme
İş akışı hizmetleri ve istemcileri işlemlere katılabilir.  Bir hizmet işleminin bir ortam işleminin parçası haline gelmesi için, bir <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinliğine <xref:System.ServiceModel.Activities.Receive> etkinlik koyun. <xref:System.ServiceModel.Activities.Send> veya <xref:System.ServiceModel.Activities.TransactedReceiveScope> içindeki bir <xref:System.ServiceModel.Activities.SendReply> etkinliği tarafından yapılan çağrılar, çevresel işlem içinde de yapılır. Bir iş akışı istemci uygulaması, <xref:System.Activities.Statements.TransactionScope> etkinliğini kullanarak ve ortam işlemini kullanarak hizmet işlemlerini çağıran bir ortam işlemi oluşturabilir. Bu konu, işlemlere katılan bir iş akışı hizmeti ve iş akışı istemcisi oluşturma konusunda size yol gösterir.  
  
> [!WARNING]
> Bir iş akışı hizmeti örneği bir işlem içinde yüklenirse ve iş akışı bir <xref:System.Activities.Statements.Persist> etkinlik içeriyorsa, iş akışı örneği işlem zaman aşımına uğrayana kadar engeller.  
  
> [!IMPORTANT]
> <xref:System.ServiceModel.Activities.TransactedReceiveScope> kullandığınızda, tüm alma işlemlerini iş akışına <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinlikler dahilinde yerleştirmeniz önerilir.  
  
> [!IMPORTANT]
> <xref:System.ServiceModel.Activities.TransactedReceiveScope> kullanılırken ve iletileri yanlış sırada geldiğinde, ilk sipariş dışı ileti teslim edilmeye çalışılırken iş akışı iptal edilir. İş akışınızın iş akışı kimliği her zaman tutarlı bir durdurma noktasında olduğundan emin olmanız gerekir. Bu, iş akışını önceki bir Kalıcılık noktasından yeniden başlatmanıza olanak tanır.  
  
### <a name="create-a-shared-library"></a>Paylaşılan kitaplık oluşturma  
  
1. Yeni boş bir Visual Studio çözümü oluşturun.  
  
2. `Common`adlı yeni bir sınıf kitaplığı projesi ekleyin. Aşağıdaki derlemelere başvurular ekleyin:  
  
    - System. Activities. dll  
  
    - System.ServiceModel.dll  
  
    - System. ServiceModel. Activities. dll  
  
    - System.Transactions.dll  
  
3. `Common` projesine `PrintTransactionInfo` adlı yeni bir sınıf ekleyin. Bu sınıf <xref:System.Activities.NativeActivity> türetilir ve <xref:System.Activities.NativeActivity.Execute%2A> yöntemini aşırı yükler.  
  
    ```csharp
    using System;  
    using System;  
    using System.Activities;  
    using System.Transactions;  
  
    namespace Common  
    {  
        public class PrintTransactionInfo : NativeActivity  
        {  
            protected override void Execute(NativeActivityContext context)  
            {  
                RuntimeTransactionHandle rth = context.Properties.Find(typeof(RuntimeTransactionHandle).FullName) as RuntimeTransactionHandle;  
  
                if (rth == null)  
                {  
                    Console.WriteLine("There is no ambient RuntimeTransactionHandle");  
                }  
  
                Transaction t = rth.GetCurrentTransaction(context);  
  
                if (t == null)  
                {  
                    Console.WriteLine("There is no ambient transaction");  
                }  
                else  
                {  
                    Console.WriteLine("Transaction: {0} is {1}", t.TransactionInformation.DistributedIdentifier, t.TransactionInformation.Status);  
                }  
            }  
        }  
  
    }  
    ```  
  
     Bu, ortam işlem hakkındaki bilgileri görüntüleyen ve bu konuda kullanılan hizmet ve istemci iş akışlarında kullanılan yerel bir etkinliktir. Bu etkinliği **araç kutusunun** **ortak** bölümünde kullanılabilir hale getirmek için çözümü oluşturun.  
  
### <a name="implement-the-workflow-service"></a>İş akışı hizmetini uygulama  
  
1. `Common` projesine `WorkflowService` adlı yeni bir WCF Iş akışı hizmeti ekleyin. Bunu yapmak için `Common` projesine tıklayın, **Ekle**, **Yeni öğe...** öğesini seçin, **yüklü şablonlar** altında **Iş akışı** ' nı seçin ve **WCF iş akışı hizmeti**' ni seçin.  
  
     ![Iş akışı hizmeti ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/add-workflow-service.jpg)  
  
2. Varsayılan `ReceiveRequest` ve `SendResponse` etkinliklerini silin.  
  
3. <xref:System.Activities.Statements.WriteLine> etkinliğini sürükleyip `Sequential Service` etkinliğine bırakın. Aşağıdaki örnekte gösterildiği gibi, Text özelliğini `"Workflow Service starting ..."` olarak ayarlayın.  
  
     ! [Sıralı hizmet etkinliğine bir WriteLine etkinliği ekleme (./Media/flowing-Transactions-into-and-out-of-Workflow-Services/Add-WriteLine-Sequential-Service.jpg)  
  
4. <xref:System.Activities.Statements.WriteLine> etkinliğinden sonra bir <xref:System.ServiceModel.Activities.TransactedReceiveScope> sürükleyip bırakın. <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinliği **araç kutusunun** **mesajlaşma** bölümünde bulunabilir. <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinliği iki bölümden oluşan **istek** ve **gövdeden**oluşur. **İstek** bölümü <xref:System.ServiceModel.Activities.Receive> etkinliğini içerir. **Gövde** bölümü bir ileti alındıktan sonra bir işlem içinde yürütülecek etkinlikleri içerir.  
  
     ![TransactedReceiveScope etkinliği ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/transactedreceivescope-activity.jpg)  
  
5. <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinliğini seçin ve **değişkenler** düğmesine tıklayın. Aşağıdaki değişkenleri ekleyin.  
  
     ![TransactedReceiveScope 'a değişken ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/add-transactedreceivescope-variables.jpg)  
  
    > [!NOTE]
    > Varsayılan olarak bulunan veri değişkenini silebilirsiniz. Ayrıca var olan tanıtıcı değişkenini de kullanabilirsiniz.  
  
6. <xref:System.ServiceModel.Activities.Receive> etkinliğini <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinliğinin **istek** bölümünde sürükleyin ve bırakın. Aşağıdaki özellikleri ayarlayın:  
  
    |Özellik|Değer|  
    |--------------|-----------|  
    |CanCreateInstance|True (onay kutusunu işaretleyin)|  
    |OperationName|StartSample|  
    |ServiceContractName|Itransactionsample|  
  
     İş akışı şöyle görünmelidir:  
  
     ![Alma etkinliği ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/add-receive-activity.jpg)  
  
7. <xref:System.ServiceModel.Activities.Receive> etkinliğinde **tanımla...** bağlantısına tıklayın ve aşağıdaki ayarları yapın:  
  
     ![Alma etkinliği için ileti ayarlarını ayarlama](./media/flowing-transactions-into-and-out-of-workflow-services/receive-message-settings.jpg)  
  
8. <xref:System.Activities.Statements.Sequence> etkinliğini sürükleyip <xref:System.ServiceModel.Activities.TransactedReceiveScope>gövde bölümüne bırakın. <xref:System.Activities.Statements.Sequence> etkinliği içinde iki <xref:System.Activities.Statements.WriteLine> etkinliği sürükleyip bırakın ve aşağıdaki tabloda gösterildiği gibi <xref:System.Activities.Statements.WriteLine.Text%2A> özelliklerini ayarlayın.  
  
    |Etkinlik|Değer|  
    |--------------|-----------|  
    |1\. WriteLine|"Hizmet: alma tamamlandı"|  
    |2\. WriteLine|"Hizmet: alındı =" + requestMessage|  
  
     İş akışı artık şöyle görünmelidir:  
  
     ![WriteLine etkinlikleri eklendikten sonra sıra](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-writelines.jpg)  
  
9. `PrintTransactionInfo` etkinliğini <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinliğinde **gövdesinde** ikinci <xref:System.Activities.Statements.WriteLine> etkinlikten sonra sürükleyip bırakın.  
  
     ![PrintTransactionInfo eklendikten sonra sıra](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-printtransactioninfo.jpg )  
  
10. `PrintTransactionInfo` etkinliğinden sonra bir <xref:System.Activities.Statements.Assign> etkinliğini sürükleyip bırakın ve aşağıdaki tabloya göre özelliklerini ayarlayın.  
  
    |Özellik|Değer|  
    |--------------|-----------|  
    |Bitiş|replyMessage|  
    |Değer|"Hizmet: Yanıt gönderiliyor."|  
  
11. <xref:System.Activities.Statements.Assign> etkinliğinden sonra bir <xref:System.Activities.Statements.WriteLine> etkinliğini sürükleyip bırakın ve <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "Service: BEGIN Reply" olarak ayarlayın.  
  
     İş akışı artık şöyle görünmelidir:  
  
     ![Assign ve WriteLine eklendikten sonra](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-sbr-writeline.jpg)  
  
12. <xref:System.ServiceModel.Activities.Receive> etkinliğine sağ tıklayıp **SendReply oluştur** ' u seçin ve son <xref:System.Activities.Statements.WriteLine> etkinliğinden sonra yapıştırın. `SendReplyToReceive` etkinliğinde **tanımla...** bağlantısına tıklayın ve aşağıdaki ayarları yapın.  
  
     ![Yanıt iletisi ayarları](./media/flowing-transactions-into-and-out-of-workflow-services/reply-message-settings.jpg)  
  
13. `SendReplyToReceive` etkinliğinden sonra bir <xref:System.Activities.Statements.WriteLine> etkinliğini sürükleyip bırakın ve <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "Service: Reply gönderildi" olarak ayarlayın.  
  
14. İş akışının alt kısmındaki bir <xref:System.Activities.Statements.WriteLine> etkinliğini sürükleyip bırakın ve <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "Service: Workflow bitiyor, çıkmak için ENTER tuşuna basın" olarak ayarlayın.  
  
     Tamamlanmış hizmet iş akışı şöyle görünmelidir:  
  
     ![Hizmet Iş akışını doldurun](./media/flowing-transactions-into-and-out-of-workflow-services/service-complete-workflow.jpg)  
  
### <a name="implement-the-workflow-client"></a>İş akışı istemcisini uygulama  
  
1. `Common` projesine `WorkflowClient` adlı yeni bir WCF Iş akışı uygulaması ekleyin. Bunu yapmak için `Common` projesine tıklayın, **Ekle**, **Yeni öğe...** öğesini seçin, **yüklü şablonlar** altında **iş akışı** ' nı seçin ve **etkinlik**' ı seçin.  
  
     ![Etkinlik projesi ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/add-activity-project.jpg)  
  
2. <xref:System.Activities.Statements.Sequence> etkinliğini tasarım yüzeyine sürükleyip bırakın.  
  
3. <xref:System.Activities.Statements.Sequence> etkinliği içinde <xref:System.Activities.Statements.WriteLine> etkinliğini sürükleyip bırakın ve <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini `"Client: Workflow starting"`olarak ayarlayın. İş akışı artık şöyle görünmelidir:  
  
     ![WriteLine etkinliği ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-activity.jpg)  
  
4. <xref:System.Activities.Statements.TransactionScope> etkinliğini <xref:System.Activities.Statements.WriteLine> etkinliğinden sonra sürükleyip bırakın.  <xref:System.Activities.Statements.TransactionScope> etkinliğini seçin, değişkenler düğmesine tıklayın ve aşağıdaki değişkenleri ekleyin.  
  
     ![TransactionScope 'a değişken ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/transactionscope-variables.jpg)  
  
5. <xref:System.Activities.Statements.Sequence> etkinliğini sürükleyip <xref:System.Activities.Statements.TransactionScope> etkinliğinin gövdesine bırakın.  
  
6. <xref:System.Activities.Statements.Sequence> içinde `PrintTransactionInfo` etkinliğini sürükleyip bırakma  
  
7. <xref:System.Activities.Statements.WriteLine> etkinliğini `PrintTransactionInfo` etkinliğinden sonra sürükleyip bırakın ve <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "Client: Send başlatılıyor" olarak ayarlayın. İş akışı artık şöyle görünmelidir:  
  
     ![Istemci ekleniyor: gönderme etkinlikleri başlatılıyor](./media/flowing-transactions-into-and-out-of-workflow-services/client-add-cbs-writeline.jpg)  
  
8. <xref:System.ServiceModel.Activities.Send> etkinliğini <xref:System.Activities.Statements.Assign> etkinliğinden sonra sürükleyip bırakın ve aşağıdaki özellikleri ayarlayın:  
  
    |Özellik|Değer|  
    |--------------|-----------|  
    |EndpointConfigurationName|workflowServiceEndpoint|  
    |OperationName|StartSample|  
    |ServiceContractName|Itransactionsample|  
  
     İş akışı artık şöyle görünmelidir:  
  
     ![Gönderme etkinliği özelliklerini ayarlama](./media/flowing-transactions-into-and-out-of-workflow-services/client-send-activity-settings.jpg)  
  
9. **Tanımla...** bağlantısına tıklayın ve aşağıdaki ayarları yapın:  
  
     ![Etkinlik iletisi ayarlarını gönder](./media/flowing-transactions-into-and-out-of-workflow-services/send-message-settings.jpg)  
  
10. <xref:System.ServiceModel.Activities.Send> etkinliğine sağ tıklayın ve **ReceiveReply oluştur**' u seçin. <xref:System.ServiceModel.Activities.ReceiveReply> etkinlik <xref:System.ServiceModel.Activities.Send> etkinliğinden sonra otomatik olarak yerleştirilecek.  
  
11. Tanımla... öğesine tıklayın ReceiveReplyForSend etkinliğinin bağlantısını yapın ve aşağıdaki ayarları yapın:  
  
     ![ReceiveForSend ileti ayarlarını ayarlama](./media/flowing-transactions-into-and-out-of-workflow-services/client-reply-message-settings.jpg)  
  
12. <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.ReceiveReply> etkinlikleri arasında <xref:System.Activities.Statements.WriteLine> etkinliğini sürükleyip bırakın ve <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "Client: Send tamamlanmıştır" olarak ayarlayın.  
  
13. <xref:System.ServiceModel.Activities.ReceiveReply> etkinliğinden sonra bir <xref:System.Activities.Statements.WriteLine> etkinliğini sürükleyip bırakın ve <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "Istemci tarafı: Yanıtla alındı =" + replyMessage olarak ayarlayın  
  
14. `PrintTransactionInfo` etkinliğini <xref:System.Activities.Statements.WriteLine> etkinliğinden sonra sürükleyip bırakın.  
  
15. <xref:System.Activities.Statements.WriteLine> etkinliğini iş akışının sonuna sürükleyip bırakın ve <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "Istemci iş akışı bitişi" olarak ayarlayın. Tamamlanan istemci iş akışı aşağıdaki diyagram gibi görünmelidir.  
  
     ![Tamamlanan istemci iş akışı](./media/flowing-transactions-into-and-out-of-workflow-services/client-complete-workflow.jpg)  
  
16. Çözümü oluşturun.  
  
### <a name="create-the-service-application"></a>Hizmet uygulaması oluşturma  
  
1. Çözüme `Service` adlı yeni bir konsol uygulaması projesi ekleyin. Aşağıdaki derlemelere başvurular ekleyin:  
  
    1. System. Activities. dll  
  
    2. System.ServiceModel.dll  
  
    3. System. ServiceModel. Activities. dll  
  
2. Oluşturulan Program.cs dosyasını ve aşağıdaki kodu açın:  
  
    ```csharp
          static void Main()  
          {  
              Console.WriteLine("Building the server.");  
              using (WorkflowServiceHost host = new WorkflowServiceHost(new DeclarativeServiceWorkflow(), new Uri("net.tcp://localhost:8000/TransactedReceiveService/Declarative")))  
              {                
                  //Start the server  
                  host.Open();  
                  Console.WriteLine("Service started.");  
  
                  Console.WriteLine();  
                  Console.ReadLine();  
                  //Shutdown  
                  host.Close();  
              };         
          }  
    ```  
  
3. Projeye aşağıdaki App. config dosyasını ekleyin.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <!-- Copyright © Microsoft Corporation.  All rights reserved. -->  
    <configuration>  
        <system.serviceModel>  
            <bindings>  
                <netTcpBinding>  
                    <binding transactionFlow="true" />  
                </netTcpBinding>  
            </bindings>  
        </system.serviceModel>  
    </configuration>  
    ```  
  
### <a name="create-the-client-application"></a>İstemci uygulaması oluşturma  
  
1. Çözüme `Client` adlı yeni bir konsol uygulaması projesi ekleyin. System. Activities. dll dosyasına bir başvuru ekleyin.  
  
2. Program.cs dosyasını açın ve aşağıdaki kodu ekleyin.  
  
    ```csharp
    class Program  
    {  

        private static AutoResetEvent syncEvent = new AutoResetEvent(false);  
  
        static void Main(string[] args)  
        {  
            //Build client  
            Console.WriteLine("Building the client.");  
            WorkflowApplication client = new WorkflowApplication(new DeclarativeClientWorkflow());  
            client.Completed = Program.Completed;  
            client.Aborted = Program.Aborted;  
            client.OnUnhandledException = Program.OnUnhandledException;  
            //Wait for service to start  
            Console.WriteLine("Press ENTER once service is started.");  
            Console.ReadLine();  
  
            //Start the client              
            Console.WriteLine("Starting the client.");  
            client.Run();  
            syncEvent.WaitOne();  
  
            //Sample complete  
            Console.WriteLine();  
            Console.WriteLine("Client complete. Press ENTER to exit.");  
            Console.ReadLine();  
        }  
  
        private static void Completed(WorkflowApplicationCompletedEventArgs e)  
        {  
            Program.syncEvent.Set();  
        }  
  
        private static void Aborted(WorkflowApplicationAbortedEventArgs e)  
        {  
            Console.WriteLine("Client Aborted: {0}", e.Reason);  
            Program.syncEvent.Set();  
        }  
  
        private static UnhandledExceptionAction OnUnhandledException(WorkflowApplicationUnhandledExceptionEventArgs e)  
        {  
            Console.WriteLine("Client had an unhandled exception: {0}", e.UnhandledException);  
            return UnhandledExceptionAction.Cancel;  
        }  
    }  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Windows Communication Foundation İşlemleri Genel Bakış](../../../../docs/framework/wcf/feature-details/transactions-overview.md)
