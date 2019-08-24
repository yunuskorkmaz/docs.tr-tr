---
title: İş Akışı Hizmetlerine İşlemlerin Giriş ve Çıkış Akışını Gerçekleştirme
ms.date: 03/30/2017
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
ms.openlocfilehash: ae99c53bbb859f3ade075d4d60ad2ae7e5e7272b
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988811"
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a>İş Akışı Hizmetlerine İşlemlerin Giriş ve Çıkış Akışını Gerçekleştirme
İş akışı hizmetleri ve istemcileri işlemlere katılabilir.  Bir hizmet işleminin bir çevresel işlemin bir parçası haline gelmesi için etkinlik <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.TransactedReceiveScope> içine bir etkinlik koyun. Bir <xref:System.ServiceModel.Activities.Send> veyaiçindeki<xref:System.ServiceModel.Activities.TransactedReceiveScope> bir etkinlik tarafından yapılan tüm çağrılar çevresel işlem içinde de yapılır. <xref:System.ServiceModel.Activities.SendReply> Bir iş akışı istemci uygulaması, <xref:System.Activities.Statements.TransactionScope> etkinlikleri kullanarak ve ortam işlemini kullanarak hizmet işlemlerini çağıran bir ortam işlemi oluşturabilir. Bu konu, işlemlere katılan bir iş akışı hizmeti ve iş akışı istemcisi oluşturma konusunda size yol gösterir.  
  
> [!WARNING]
> Bir iş akışı hizmeti örneği bir işlem içinde yüklenirse ve iş akışı bir <xref:System.Activities.Statements.Persist> etkinlik içeriyorsa, iş akışı örneği işlem zaman aşımına uğrayana kadar engeller.  
  
> [!IMPORTANT]
> Her kullanışınızda <xref:System.ServiceModel.Activities.TransactedReceiveScope> , iş akışına tüm alma işlemleri etkinlikleri içinde <xref:System.ServiceModel.Activities.TransactedReceiveScope> yerleştirmeniz önerilir.  
  
> [!IMPORTANT]
> Kullanırken <xref:System.ServiceModel.Activities.TransactedReceiveScope> ve iletileri yanlış sırada geldiğinde, ilk sipariş dışı ileti teslim edilmeye çalışılırken iş akışı iptal edilir. İş akışınızın iş akışı kimliği her zaman tutarlı bir durdurma noktasında olduğundan emin olmanız gerekir. Bu, iş akışını önceki bir Kalıcılık noktasından yeniden başlatmanıza olanak tanır.  
  
### <a name="create-a-shared-library"></a>Paylaşılan kitaplık oluşturma  
  
1. Yeni boş bir Visual Studio çözümü oluşturun.  
  
2. Adlı `Common`yeni bir sınıf kitaplığı projesi ekleyin. Aşağıdaki derlemelere başvurular ekleyin:  
  
    - System. Activities. dll  
  
    - System.ServiceModel.dll  
  
    - System. ServiceModel. Activities. dll  
  
    - System.Transactions.dll  
  
3. Projeye`Common` adlı `PrintTransactionInfo` yeni bir sınıf ekleyin. Bu sınıf, <xref:System.Activities.NativeActivity> <xref:System.Activities.NativeActivity.Execute%2A> öğesinden türetilir ve yöntemini aşırı yükler.  
  
    ```  
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
  
1. Projeye`Common` adlı `WorkflowService` yeni bir WCF iş akışı hizmeti ekleyin. Bunu yapmak için `Common` projeye tıklayın, **Ekle**, **Yeni öğe...** öğesini seçin, **yüklü şablonlar** altında **iş akışı** ' nı seçin ve **WCF iş akışı hizmeti**' ni seçin.  
  
     ![Iş akışı hizmeti ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/add-workflow-service.jpg)  
  
2. Varsayılan `ReceiveRequest` ve`SendResponse` etkinlikleri silin.  
  
3. Etkinliği sürükleyip `Sequential Service` etkinliğe bırakın <xref:System.Activities.Statements.WriteLine> . Text özelliğini `"Workflow Service starting ..."` aşağıdaki örnekte gösterildiği gibi olarak ayarlayın.  
  
     ! [Sıralı hizmet etkinliğine bir WriteLine etkinliği ekleme (./Media/flowing-Transactions-into-and-out-of-Workflow-Services/Add-WriteLine-Sequential-Service.jpg)  
  
4. <xref:System.Activities.Statements.WriteLine> Etkinlikten <xref:System.ServiceModel.Activities.TransactedReceiveScope> sonra sürükleyip bırakın. Etkinlik, **araç kutusunun**Mesajlaşma bölümünde bulunabilir. <xref:System.ServiceModel.Activities.TransactedReceiveScope> Etkinlik, iki bölümden oluşan **istek** ve gövdeden oluşur. <xref:System.ServiceModel.Activities.TransactedReceiveScope> **İstek** bölümü <xref:System.ServiceModel.Activities.Receive> etkinliği içerir. **Gövde** bölümü bir ileti alındıktan sonra bir işlem içinde yürütülecek etkinlikleri içerir.  
  
     ![TransactedReceiveScope etkinliği ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/transactedreceivescope-activity.jpg)  
  
5. Etkinliği seçin ve değişkenler düğmesine tıklayın. <xref:System.ServiceModel.Activities.TransactedReceiveScope> Aşağıdaki değişkenleri ekleyin.  
  
     ![TransactedReceiveScope 'a değişken ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/add-transactedreceivescope-variables.jpg)  
  
    > [!NOTE]
    > Varsayılan olarak bulunan veri değişkenini silebilirsiniz. Ayrıca var olan tanıtıcı değişkenini de kullanabilirsiniz.  
  
6. Etkinliğin <xref:System.ServiceModel.Activities.Receive> **istek** bölümü<xref:System.ServiceModel.Activities.TransactedReceiveScope> içinde bir etkinliği sürükleyip bırakın. Aşağıdaki özellikleri ayarlayın:  
  
    |Özellik|Değer|  
    |--------------|-----------|  
    |CanCreateInstance|True (onay kutusunu işaretleyin)|  
    |OperationName|StartSample|  
    |ServiceContractName|Itransactionsample|  
  
     İş akışı şöyle görünmelidir:  
  
     ![Alma etkinliği ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/add-receive-activity.jpg)  
  
7. <xref:System.ServiceModel.Activities.Receive> Etkinlikteki **tanımla...** bağlantısına tıklayın ve aşağıdaki ayarları yapın:  
  
     ![Alma etkinliği için ileti ayarlarını ayarlama](./media/flowing-transactions-into-and-out-of-workflow-services/receive-message-settings.jpg)  
  
8. Bir <xref:System.Activities.Statements.Sequence> etkinliği sürükleyin ve ' <xref:System.ServiceModel.Activities.TransactedReceiveScope>ın gövde bölümüne bırakın. Etkinlik içinde iki <xref:System.Activities.Statements.WriteLine> etkinliği sürükleyip bırakın ve aşağıdaki tabloda gösterildiği gibi <xref:System.Activities.Statements.WriteLine.Text%2A> özellikleri ayarlayın. <xref:System.Activities.Statements.Sequence>  
  
    |Etkinlik|Değer|  
    |--------------|-----------|  
    |1\. WriteLine|Hizmetle Alma tamamlandı "|  
    |2\. WriteLine|Hizmetle Alındı = "+ requestMessage|  
  
     İş akışı artık şöyle görünmelidir:  
  
     ![WriteLine etkinlikleri eklendikten sonra sıra](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-writelines.jpg)  
  
9. Etkinliğin <xref:System.Activities.Statements.WriteLine> **gövdesinde** `PrintTransactionInfo`bulunanikincietkinlikten sonraetkinliğisürükleyipbırakın<xref:System.ServiceModel.Activities.TransactedReceiveScope> .  
  
     ![PrintTransactionInfo eklendikten sonra sıra](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-printtransactioninfo.jpg )  
  
10. Etkinlikten sonra bir <xref:System.Activities.Statements.Assign> etkinliği sürükleyip bırakın ve aşağıdaki tabloya göre özelliklerini ayarlayın. `PrintTransactionInfo`  
  
    |Özellik|Değer|  
    |--------------|-----------|  
    |Bitiş|replyMessage|  
    |Değer|Hizmetle Yanıt gönderiliyor. "|  
  
11. Etkinlikten <xref:System.Activities.Statements.WriteLine> <xref:System.Activities.Statements.Assign> sonra bir etkinliği sürükleyip bırakın ve <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "hizmet" olarak ayarlayın. Yanıtla ' yı başlatın. "  
  
     İş akışı artık şöyle görünmelidir:  
  
     ![Assign ve WriteLine eklendikten sonra](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-sbr-writeline.jpg)  
  
12. <xref:System.ServiceModel.Activities.Receive> Etkinliğe sağ tıklayın ve **SendReply oluştur** ' u seçin ve son <xref:System.Activities.Statements.WriteLine> etkinlikten sonra yapıştırın. `SendReplyToReceive` Etkinlikteki **tanımla...** bağlantısına tıklayın ve aşağıdaki ayarları yapın.  
  
     ![Yanıt iletisi ayarları](./media/flowing-transactions-into-and-out-of-workflow-services/reply-message-settings.jpg)  
  
13. Etkinlikten <xref:System.Activities.Statements.WriteLine> `SendReplyToReceive` sonra bir etkinliği sürükleyip bırakın ve <xref:System.Activities.Statements.WriteLine.Text%2A> özelliği "hizmet" olarak ayarlayın. Yanıt gönderildi. "  
  
14. İş akışının alt kısmındaki <xref:System.Activities.Statements.WriteLine> bir etkinliği sürükleyip bırakın ve <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "hizmet" olarak ayarlayın. İş akışı sona erdiğinde çıkmak için ENTER tuşuna basın. "  
  
     Tamamlanmış hizmet iş akışı şöyle görünmelidir:  
  
     ![Hizmet Iş akışını doldurun](./media/flowing-transactions-into-and-out-of-workflow-services/service-complete-workflow.jpg)  
  
### <a name="implement-the-workflow-client"></a>İş akışı istemcisini uygulama  
  
1. Projeye`Common` adlı `WorkflowClient` yeni bir WCF iş akışı uygulaması ekleyin. Bunu yapmak için `Common` projeye sağ tıklayın, **Ekle**, **Yeni öğe...** öğesini seçin, **yüklü şablonlar** altında **iş akışı** ' nı seçin ve **etkinlik**' ı seçin.  
  
     ![Etkinlik projesi ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/add-activity-project.jpg)  
  
2. Tasarım yüzeyine bir <xref:System.Activities.Statements.Sequence> etkinliği sürükleyip bırakın.  
  
3. Etkinlik içinde bir <xref:System.Activities.Statements.WriteLine> etkinliği sürükleyip bırakın ve <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini olarak `"Client: Workflow starting"`ayarlayın. <xref:System.Activities.Statements.Sequence> İş akışı artık şöyle görünmelidir:  
  
     ![WriteLine etkinliği ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-activity.jpg)  
  
4. Etkinlikten sonra bir <xref:System.Activities.Statements.TransactionScope> etkinliği sürükleyip bırakın. <xref:System.Activities.Statements.WriteLine>  <xref:System.Activities.Statements.TransactionScope> Etkinliği seçin, değişkenler düğmesine tıklayın ve aşağıdaki değişkenleri ekleyin.  
  
     ![TransactionScope 'a değişken ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/transactionscope-variables.jpg)  
  
5. Etkinliğin gövdesine <xref:System.Activities.Statements.Sequence> <xref:System.Activities.Statements.TransactionScope> bir etkinlik sürükleyip bırakın.  
  
6. İçindeki bir `PrintTransactionInfo` etkinliği sürükleyip bırakma<xref:System.Activities.Statements.Sequence>  
  
7. Etkinlikten <xref:System.Activities.Statements.WriteLine> `PrintTransactionInfo` sonra bir etkinliği sürükleyip bırakın ve <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "Client:" olarak ayarlayın Gönderme başlatılıyor ". İş akışı artık şöyle görünmelidir:  
  
     ![Istemci ekleniyor: Gönderme etkinlikleri başlatılıyor](./media/flowing-transactions-into-and-out-of-workflow-services/client-add-cbs-writeline.jpg)  
  
8. Etkinlikten sonra bir <xref:System.ServiceModel.Activities.Send> etkinliği sürükleyip bırakın ve aşağıdaki özellikleri ayarlayın: <xref:System.Activities.Statements.Assign>  
  
    |Özellik|Değer|  
    |--------------|-----------|  
    |EndpointConfigurationName|workflowServiceEndpoint|  
    |OperationName|StartSample|  
    |ServiceContractName|Itransactionsample|  
  
     İş akışı artık şöyle görünmelidir:  
  
     ![Gönderme etkinliği özelliklerini ayarlama](./media/flowing-transactions-into-and-out-of-workflow-services/client-send-activity-settings.jpg)  
  
9. **Tanımla...** bağlantısına tıklayın ve aşağıdaki ayarları yapın:  
  
     ![Etkinlik iletisi ayarlarını gönder](./media/flowing-transactions-into-and-out-of-workflow-services/send-message-settings.jpg)  
  
10. <xref:System.ServiceModel.Activities.Send> Etkinliğe sağ tıklayın ve **ReceiveReply oluştur**' u seçin. <xref:System.ServiceModel.Activities.ReceiveReply> Etkinlik <xref:System.ServiceModel.Activities.Send> etkinlikten sonra otomatik olarak yerleştirilecek.  
  
11. Tanımla... öğesine tıklayın ReceiveReplyForSend etkinliğinin bağlantısını yapın ve aşağıdaki ayarları yapın:  
  
     ![ReceiveForSend ileti ayarlarını ayarlama](./media/flowing-transactions-into-and-out-of-workflow-services/client-reply-message-settings.jpg)  
  
12. Ve etkinlikleri arasında bir <xref:System.Activities.Statements.WriteLine> etkinliği sürükleyip bırakın ve özelliğini"Client:"olarakayarlayın.<xref:System.Activities.Statements.WriteLine.Text%2A> <xref:System.ServiceModel.Activities.ReceiveReply> <xref:System.ServiceModel.Activities.Send> Gönderme tamam. "  
  
13. Etkinlikten <xref:System.Activities.Statements.WriteLine> <xref:System.ServiceModel.Activities.ReceiveReply> sonra bir etkinliği sürükleyip bırakın ve <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "istemci tarafı:" olarak ayarlayın. Yanıt alındı = "+ replyMessage  
  
14. Etkinlikten sonra bir `PrintTransactionInfo` etkinliği sürükleyip bırakın. <xref:System.Activities.Statements.WriteLine>  
  
15. İş akışının sonundaki bir <xref:System.Activities.Statements.WriteLine> etkinliği sürükleyip bırakın ve <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "istemci iş akışı bitişi" olarak ayarlayın. Tamamlanan istemci iş akışı aşağıdaki diyagram gibi görünmelidir.  
  
     ![Tamamlanan istemci iş akışı](./media/flowing-transactions-into-and-out-of-workflow-services/client-complete-workflow.jpg)  
  
16. Çözümü oluşturun.  
  
### <a name="create-the-service-application"></a>Hizmet uygulaması oluşturma  
  
1. Çözüme adlı `Service` yeni bir konsol uygulaması projesi ekleyin. Aşağıdaki derlemelere başvurular ekleyin:  
  
    1. System. Activities. dll  
  
    2. System.ServiceModel.dll  
  
    3. System. ServiceModel. Activities. dll  
  
2. Oluşturulan Program.cs dosyasını ve aşağıdaki kodu açın:  
  
    ```  
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
  
1. Çözüme adlı `Client` yeni bir konsol uygulaması projesi ekleyin. System. Activities. dll dosyasına bir başvuru ekleyin.  
  
2. Program.cs dosyasını açın ve aşağıdaki kodu ekleyin.  
  
    ```  
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
