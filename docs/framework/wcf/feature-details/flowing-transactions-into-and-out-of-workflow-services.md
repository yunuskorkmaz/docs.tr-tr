---
title: İş Akışı Hizmetlerine İşlemlerin Giriş ve Çıkış Akışını Gerçekleştirme
ms.date: 03/30/2017
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
ms.openlocfilehash: 17c05139b5977c47e20e888e436a311ba145018a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597468"
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a>İş Akışı Hizmetlerine İşlemlerin Giriş ve Çıkış Akışını Gerçekleştirme
İş akışı hizmetleri ve istemcileri işlemlere katılabilir.  Bir hizmet işleminin bir çevresel işlemin bir parçası haline gelmesi için etkinlik içine bir <xref:System.ServiceModel.Activities.Receive> etkinlik koyun <xref:System.ServiceModel.Activities.TransactedReceiveScope> . Bir veya içindeki bir etkinlik tarafından yapılan tüm çağrılar <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.SendReply> <xref:System.ServiceModel.Activities.TransactedReceiveScope> çevresel işlem içinde de yapılır. Bir iş akışı istemci uygulaması <xref:System.Activities.Statements.TransactionScope> , etkinlikleri kullanarak ve ortam işlemini kullanarak hizmet işlemlerini çağıran bir ortam işlemi oluşturabilir. Bu konu, işlemlere katılan bir iş akışı hizmeti ve iş akışı istemcisi oluşturma konusunda size yol gösterir.  
  
> [!WARNING]
> Bir iş akışı hizmeti örneği bir işlem içinde yüklenirse ve iş akışı bir etkinlik içeriyorsa <xref:System.Activities.Statements.Persist> , iş akışı örneği işlem zaman aşımına uğrayana kadar engeller.  
  
> [!IMPORTANT]
> Her kullanışınızda, <xref:System.ServiceModel.Activities.TransactedReceiveScope> iş akışına tüm alma işlemleri etkinlikleri içinde yerleştirmeniz önerilir <xref:System.ServiceModel.Activities.TransactedReceiveScope> .  
  
> [!IMPORTANT]
> Kullanırken <xref:System.ServiceModel.Activities.TransactedReceiveScope> ve iletileri yanlış sırada geldiğinde, ilk sipariş dışı ileti teslim edilmeye çalışılırken iş akışı iptal edilir. İş akışınızın iş akışı kimliği her zaman tutarlı bir durdurma noktasında olduğundan emin olmanız gerekir. Bu, iş akışını önceki bir Kalıcılık noktasından yeniden başlatmanıza olanak tanır.  
  
### <a name="create-a-shared-library"></a>Paylaşılan kitaplık oluşturma  
  
1. Yeni boş bir Visual Studio çözümü oluşturun.  
  
2. Adlı yeni bir sınıf kitaplığı projesi ekleyin `Common` . Aşağıdaki derlemelere başvurular ekleyin:  
  
    - System. Activities. dll  
  
    - System.ServiceModel.dll  
  
    - System. ServiceModel. Activities. dll  
  
    - System.Transactions.dll  
  
3. Projeye adlı yeni bir sınıf ekleyin `PrintTransactionInfo` `Common` . Bu sınıf, öğesinden türetilir <xref:System.Activities.NativeActivity> ve yöntemini aşırı yükler <xref:System.Activities.NativeActivity.Execute%2A> .  
  
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
  
1. Projeye adlı yeni bir WCF Iş akışı hizmeti ekleyin `WorkflowService` `Common` . Bunu yapmak için `Common` projeye tıklayın, **Ekle**, **Yeni öğe...** öğesini seçin, **yüklü şablonlar** altında **Iş akışı** ' nı seçin ve **WCF iş akışı hizmeti**' ni seçin.  
  
     ![Iş akışı hizmeti ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/add-workflow-service.jpg)  
  
2. Varsayılan `ReceiveRequest` ve etkinlikleri silin `SendResponse` .  
  
3. Etkinliği sürükleyip etkinliğe bırakın <xref:System.Activities.Statements.WriteLine> `Sequential Service` . Text özelliğini `"Workflow Service starting ..."` Aşağıdaki örnekte gösterildiği gibi olarak ayarlayın.  
  
     ! [Sıralı hizmet etkinliğine bir WriteLine etkinliği ekleme (./Media/flowing-Transactions-into-and-out-of-Workflow-Services/Add-WriteLine-Sequential-Service.jpg)  
  
4. <xref:System.ServiceModel.Activities.TransactedReceiveScope>Etkinlikten sonra sürükleyip bırakın <xref:System.Activities.Statements.WriteLine> . <xref:System.ServiceModel.Activities.TransactedReceiveScope>Etkinlik, **araç kutusunun** **mesajlaşma** bölümünde bulunabilir. <xref:System.ServiceModel.Activities.TransactedReceiveScope>Etkinlik, iki bölümden oluşan **Istek** ve **gövdeden**oluşur. **İstek** bölümü <xref:System.ServiceModel.Activities.Receive> etkinliği içerir. **Gövde** bölümü bir ileti alındıktan sonra bir işlem içinde yürütülecek etkinlikleri içerir.  
  
     ![TransactedReceiveScope etkinliği ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/transactedreceivescope-activity.jpg)  
  
5. Etkinliği seçin <xref:System.ServiceModel.Activities.TransactedReceiveScope> ve **değişkenler** düğmesine tıklayın. Aşağıdaki değişkenleri ekleyin.  
  
     ![TransactedReceiveScope 'a değişken ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/add-transactedreceivescope-variables.jpg)  
  
    > [!NOTE]
    > Varsayılan olarak bulunan veri değişkenini silebilirsiniz. Ayrıca var olan tanıtıcı değişkenini de kullanabilirsiniz.  
  
6. Etkinliğin <xref:System.ServiceModel.Activities.Receive> **istek** bölümü içinde bir etkinliği sürükleyip bırakın <xref:System.ServiceModel.Activities.TransactedReceiveScope> . Aşağıdaki özellikleri ayarlayın:  
  
    |Özellik|Değer|  
    |--------------|-----------|  
    |CanCreateInstance|True (onay kutusunu işaretleyin)|  
    |ThrottledRequests|StartSample|  
    |ServiceContractName|Itransactionsample|  
  
     İş akışı şöyle görünmelidir:  
  
     ![Alma etkinliği ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/add-receive-activity.jpg)  
  
7. Etkinlikteki **tanımla...** bağlantısına tıklayın <xref:System.ServiceModel.Activities.Receive> ve aşağıdaki ayarları yapın:  
  
     ![Alma etkinliği için ileti ayarlarını ayarlama](./media/flowing-transactions-into-and-out-of-workflow-services/receive-message-settings.jpg)  
  
8. Bir etkinliği sürükleyin ve ' <xref:System.Activities.Statements.Sequence> ın gövde bölümüne bırakın <xref:System.ServiceModel.Activities.TransactedReceiveScope> . Etkinlik içinde <xref:System.Activities.Statements.Sequence> iki etkinliği sürükleyip bırakın <xref:System.Activities.Statements.WriteLine> ve <xref:System.Activities.Statements.WriteLine.Text%2A> Aşağıdaki tabloda gösterildiği gibi özellikleri ayarlayın.  
  
    |Etkinlik|Değer|  
    |--------------|-----------|  
    |1. WriteLine|"Hizmet: alma tamamlandı"|  
    |2. WriteLine|"Hizmet: alındı =" + requestMessage|  
  
     İş akışı artık şöyle görünmelidir:  
  
     ![WriteLine etkinlikleri eklendikten sonra sıra](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-writelines.jpg)  
  
9. Etkinliğin `PrintTransactionInfo` gövdesinde bulunan ikinci etkinlikten sonra etkinliği sürükleyip bırakın <xref:System.Activities.Statements.WriteLine> **Body** <xref:System.ServiceModel.Activities.TransactedReceiveScope> .  
  
     ![PrintTransactionInfo eklendikten sonra sıra](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-printtransactioninfo.jpg )  
  
10. <xref:System.Activities.Statements.Assign>Etkinlikten sonra bir etkinliği sürükleyip bırakın `PrintTransactionInfo` ve aşağıdaki tabloya göre özelliklerini ayarlayın.  
  
    |Özellik|Değer|  
    |--------------|-----------|  
    |Alıcı|replyMessage|  
    |Değer|"Hizmet: Yanıt gönderiliyor."|  
  
11. <xref:System.Activities.Statements.WriteLine>Etkinlikten sonra bir etkinliği sürükleyip bırakın <xref:System.Activities.Statements.Assign> ve <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "Service: BEGIN Reply" olarak ayarlayın.  
  
     İş akışı artık şöyle görünmelidir:  
  
     ![Assign ve WriteLine eklendikten sonra](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-sbr-writeline.jpg)  
  
12. Etkinliğe sağ tıklayın <xref:System.ServiceModel.Activities.Receive> ve **SendReply oluştur** ' u seçin ve son <xref:System.Activities.Statements.WriteLine> etkinlikten sonra yapıştırın. Etkinlikteki **tanımla...** bağlantısına tıklayın `SendReplyToReceive` ve aşağıdaki ayarları yapın.  
  
     ![Yanıt iletisi ayarları](./media/flowing-transactions-into-and-out-of-workflow-services/reply-message-settings.jpg)  
  
13. <xref:System.Activities.Statements.WriteLine>Etkinlikten sonra bir etkinliği sürükleyip bırakın `SendReplyToReceive` ve <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "Service: Reply gönderildi" olarak ayarlayın.  
  
14. <xref:System.Activities.Statements.WriteLine>İş akışının alt kısmındaki bir etkinliği sürükleyip bırakın ve <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "Service: Workflow bitiyor, ÇıKMAK için ENTER tuşuna basın" olarak ayarlayın.  
  
     Tamamlanmış hizmet iş akışı şöyle görünmelidir:  
  
     ![Hizmet Iş akışını doldurun](./media/flowing-transactions-into-and-out-of-workflow-services/service-complete-workflow.jpg)  
  
### <a name="implement-the-workflow-client"></a>İş akışı istemcisini uygulama  
  
1. Projeye adlı yeni bir WCF Iş akışı uygulaması ekleyin `WorkflowClient` `Common` . Bunu yapmak için projeye sağ tıklayın `Common` , **Ekle**, **Yeni öğe...** öğesini seçin, **yüklü şablonlar** altında **iş akışı** ' nı seçin ve **etkinlik**' ı seçin.  
  
     ![Etkinlik projesi ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/add-activity-project.jpg)  
  
2. <xref:System.Activities.Statements.Sequence>Tasarım yüzeyine bir etkinliği sürükleyip bırakın.  
  
3. Etkinlik içinde <xref:System.Activities.Statements.Sequence> bir etkinliği sürükleyip bırakın <xref:System.Activities.Statements.WriteLine> ve <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini olarak ayarlayın `"Client: Workflow starting"` . İş akışı artık şöyle görünmelidir:  
  
     ![WriteLine etkinliği ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-activity.jpg)  
  
4. <xref:System.Activities.Statements.TransactionScope>Etkinlikten sonra bir etkinliği sürükleyip bırakın <xref:System.Activities.Statements.WriteLine> .  Etkinliği seçin <xref:System.Activities.Statements.TransactionScope> , değişkenler düğmesine tıklayın ve aşağıdaki değişkenleri ekleyin.  
  
     ![TransactionScope 'a değişken ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/transactionscope-variables.jpg)  
  
5. Etkinliğin gövdesine bir etkinlik sürükleyip bırakın <xref:System.Activities.Statements.Sequence> <xref:System.Activities.Statements.TransactionScope> .  
  
6. İçindeki bir etkinliği sürükleyip bırakma `PrintTransactionInfo`<xref:System.Activities.Statements.Sequence>  
  
7. <xref:System.Activities.Statements.WriteLine>Etkinlikten sonra bir etkinliği sürükleyip bırakın `PrintTransactionInfo` ve <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "Client: Send başlatılıyor" olarak ayarlayın. İş akışı artık şöyle görünmelidir:  
  
     ![Istemci ekleniyor: gönderme etkinlikleri başlatılıyor](./media/flowing-transactions-into-and-out-of-workflow-services/client-add-cbs-writeline.jpg)  
  
8. <xref:System.ServiceModel.Activities.Send>Etkinlikten sonra bir etkinliği sürükleyip bırakın <xref:System.Activities.Statements.Assign> ve aşağıdaki özellikleri ayarlayın:  
  
    |Özellik|Değer|  
    |--------------|-----------|  
    |EndpointConfigurationName|workflowServiceEndpoint|  
    |ThrottledRequests|StartSample|  
    |ServiceContractName|Itransactionsample|  
  
     İş akışı artık şöyle görünmelidir:  
  
     ![Gönderme etkinliği özelliklerini ayarlama](./media/flowing-transactions-into-and-out-of-workflow-services/client-send-activity-settings.jpg)  
  
9. **Tanımla...** bağlantısına tıklayın ve aşağıdaki ayarları yapın:  
  
     ![Etkinlik iletisi ayarlarını gönder](./media/flowing-transactions-into-and-out-of-workflow-services/send-message-settings.jpg)  
  
10. Etkinliğe sağ tıklayın <xref:System.ServiceModel.Activities.Send> ve **ReceiveReply oluştur**' u seçin. Etkinlik <xref:System.ServiceModel.Activities.ReceiveReply> etkinlikten sonra otomatik olarak yerleştirilecek <xref:System.ServiceModel.Activities.Send> .  
  
11. Tanımla... öğesine tıklayın ReceiveReplyForSend etkinliğinin bağlantısını yapın ve aşağıdaki ayarları yapın:  
  
     ![ReceiveForSend ileti ayarlarını ayarlama](./media/flowing-transactions-into-and-out-of-workflow-services/client-reply-message-settings.jpg)  
  
12. <xref:System.Activities.Statements.WriteLine>Ve etkinlikleri arasında bir etkinlik sürükleyip bırakın <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> ve <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "istemci: gönderme Tamam" olarak ayarlayın.  
  
13. <xref:System.Activities.Statements.WriteLine>Etkinlikten sonra bir etkinliği sürükleyip bırakın <xref:System.ServiceModel.Activities.ReceiveReply> ve <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "Istemci tarafı: Yanıtla alındı =" + ReplyMessage olarak ayarlayın  
  
14. `PrintTransactionInfo`Etkinlikten sonra bir etkinliği sürükleyip bırakın <xref:System.Activities.Statements.WriteLine> .  
  
15. <xref:System.Activities.Statements.WriteLine>İş akışının sonundaki bir etkinliği sürükleyip bırakın ve <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "istemci iş akışı bitişi" olarak ayarlayın. Tamamlanan istemci iş akışı aşağıdaki diyagram gibi görünmelidir.  
  
     ![Tamamlanan istemci iş akışı](./media/flowing-transactions-into-and-out-of-workflow-services/client-complete-workflow.jpg)  
  
16. Çözümü derleyin.  
  
### <a name="create-the-service-application"></a>Hizmet uygulaması oluşturma  
  
1. Çözüme adlı yeni bir konsol uygulaması projesi ekleyin `Service` . Aşağıdaki derlemelere başvurular ekleyin:  
  
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
  
1. Çözüme adlı yeni bir konsol uygulaması projesi ekleyin `Client` . System. Activities. dll dosyasına bir başvuru ekleyin.  
  
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

- [İş Akışı Hizmetleri](workflow-services.md)
- [Windows Communication Foundation İşlemleri Genel Bakış](transactions-overview.md)
