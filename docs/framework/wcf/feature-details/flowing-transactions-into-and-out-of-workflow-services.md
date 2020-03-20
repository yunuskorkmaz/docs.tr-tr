---
title: İş Akışı Hizmetlerine İşlemlerin Giriş ve Çıkış Akışını Gerçekleştirme
ms.date: 03/30/2017
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
ms.openlocfilehash: fe03047dd931d25ec94bbc5e00c479d1b42397bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185273"
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a>İş Akışı Hizmetlerine İşlemlerin Giriş ve Çıkış Akışını Gerçekleştirme
İş akışı hizmetleri ve istemciler hareketlere katılabilir.  Bir hizmet işleminin ortam hareketinin bir parçası <xref:System.ServiceModel.Activities.Receive> olması için <xref:System.ServiceModel.Activities.TransactedReceiveScope> bir etkinliği bir etkinlik içine yerleştirin. Bir <xref:System.ServiceModel.Activities.Send> veya bir <xref:System.ServiceModel.Activities.SendReply> etkinlik içinde <xref:System.ServiceModel.Activities.TransactedReceiveScope> yapılan tüm aramalar da ortam hareketi içinde yapılacaktır. İş akışı istemcisi uygulaması, ortam işlemini <xref:System.Activities.Statements.TransactionScope> kullanarak etkinlik ve çağrı hizmeti işlemlerini kullanarak bir ortam hareketi oluşturabilir. Bu konu, hareketlere katılan bir iş akışı hizmeti ve iş akışı istemcisi oluşturmakonusunda size yol gösterir.  
  
> [!WARNING]
> Bir iş akışı hizmeti örneği bir hareket içinde yüklenirse ve iş akışı bir <xref:System.Activities.Statements.Persist> etkinlik içeriyorsa, iş akışı örneği işlem süreleri bitene kadar engellenir.  
  
> [!IMPORTANT]
> Ne zaman bir <xref:System.ServiceModel.Activities.TransactedReceiveScope> kullandığınızda, tüm Alır'yı iş <xref:System.ServiceModel.Activities.TransactedReceiveScope> akışına etkinlikler içinde yerleştirmeniz önerilir.  
  
> [!IMPORTANT]
> Kullanma <xref:System.ServiceModel.Activities.TransactedReceiveScope> ve iletiler yanlış sırada geldiğinde, ilk sipariş dışı iletisini teslim etmeye çalışırken iş akışı iptal edilecektir. İş akışı boşta kaldığında iş akışınızın her zaman tutarlı bir durdurma noktasında olduğundan emin olmalısınız. Bu, iş akışı iptal edilmesi halinde önceki bir kalıcılık noktasından iş akışını yeniden başlatmanızı sağlar.  
  
### <a name="create-a-shared-library"></a>Paylaşılan kitaplık oluşturma  
  
1. Yeni bir boş Visual Studio Çözümü oluşturun.  
  
2. 'li yeni bir `Common`sınıf kitaplığı projesi ekleyin. Aşağıdaki derlemelere başvurular ekleyin:  
  
    - Sistem.Etkinlikler.dll  
  
    - System.ServiceModel.dll  
  
    - Sistem.ServiceModel.Activities.dll  
  
    - System.Transactions.dll  
  
3. `Common` Projeye çağrılan `PrintTransactionInfo` yeni bir sınıf ekleyin. Bu sınıf yöntemden <xref:System.Activities.NativeActivity> türetilir ve aşırı yüklenir. <xref:System.Activities.NativeActivity.Execute%2A>  
  
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
  
     Bu, ortam hareketi yle ilgili bilgileri görüntüleyen ve bu konuda kullanılan hem hizmet hem de istemci iş akışlarında kullanılan yerel bir etkinliktir. Bu etkinliği **Araç Kutusu'nun** **Ortak** bölümünde kullanılabilir hale getirmek için çözüm oluşturun.  
  
### <a name="implement-the-workflow-service"></a>İş akışı hizmetini uygulayın  
  
1. `Common` Projeye çağrılan `WorkflowService` yeni bir WCF İş Akışı Hizmeti ekleyin. Bunu yapmak için `Common` projeyi sağ tıklatın, **Ekle**, **Yeni Öğe ...**, Yüklü **Şablonlar** altında **İş Akışını** seçin ve **WCF İş Akışı Hizmeti'ni**seçin.  
  
     ![İş Akışı Hizmeti Ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/add-workflow-service.jpg)  
  
2. Varsayılan `ReceiveRequest` ve `SendResponse` etkinlikleri silin.  
  
3. Bir <xref:System.Activities.Statements.WriteLine> etkinliği sürükleyin `Sequential Service` ve aktiviteye bırakın. Metin özelliğini `"Workflow Service starting ..."` aşağıdaki örnekte gösterildiği gibi ayarlayın.  
  
     ! [Sıralı Hizmet etkinliğine WriteLine etkinliği ekleme(./ortam/akan-hareketler-iş akışı-hizmetler/add-writeline-sequential-service.jpg)  
  
4. Etkinlikten <xref:System.Activities.Statements.WriteLine> sonra <xref:System.ServiceModel.Activities.TransactedReceiveScope> bir sürükle ve bırak. <xref:System.ServiceModel.Activities.TransactedReceiveScope> Etkinlik, **Araç Kutusu'nun** **Mesajlaşma** bölümünde bulunabilir. Etkinlik, **İstek** ve Gövde olmak için iki bölümden oluşmaktadır. **Body** <xref:System.ServiceModel.Activities.TransactedReceiveScope> **İstek** bölümü <xref:System.ServiceModel.Activities.Receive> etkinliği içerir. **Gövde** bölümü, ileti alındıktan sonra bir hareket içinde yürütülecek etkinlikleri içerir.  
  
     ![TransactedReceiveScope etkinliği ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/transactedreceivescope-activity.jpg)  
  
5. <xref:System.ServiceModel.Activities.TransactedReceiveScope> Etkinliği seçin ve **Değişkenler** düğmesini tıklatın. Aşağıdaki değişkenleri ekleyin.  
  
     ![TransactedReceiveScope'a değişken ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/add-transactedreceivescope-variables.jpg)  
  
    > [!NOTE]
    > Varsayılan olarak var olan veri değişkenini silebilirsiniz. Varolan tutamaç değişkenini de kullanabilirsiniz.  
  
6. Etkinliğin İstek <xref:System.ServiceModel.Activities.Receive> bölümündeki bir etkinliği sürükleyin ve bırakın. **Request** <xref:System.ServiceModel.Activities.TransactedReceiveScope> Aşağıdaki özellikleri ayarlayın:  
  
    |Özellik|Değer|  
    |--------------|-----------|  
    |CanCreateInstance|True (onay kutusunu işaretleyin)|  
    |ThrottledRequests|BaşlangıçÖrneği|  
    |Hizmet Sözleşme Adı|ITransactionSample|  
  
     İş akışı aşağıdaki gibi görünmelidir:  
  
     ![Alma etkinliği ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/add-receive-activity.jpg)  
  
7. <xref:System.ServiceModel.Activities.Receive> Etkinlikte **Tanımla...** bağlantısını tıklatın ve aşağıdaki ayarları yapın:  
  
     ![Al etkinliği için ileti ayarlarını ayarlama](./media/flowing-transactions-into-and-out-of-workflow-services/receive-message-settings.jpg)  
  
8. Sürükleyin ve <xref:System.Activities.Statements.Sequence> Vücut bölümüne bir <xref:System.ServiceModel.Activities.TransactedReceiveScope>etkinlik bırakın. <xref:System.Activities.Statements.Sequence> Etkinlik içinde sürükleyin <xref:System.Activities.Statements.WriteLine> ve iki <xref:System.Activities.Statements.WriteLine.Text%2A> etkinlik bırakın ve aşağıdaki tabloda gösterildiği gibi özellikleri ayarlayın.  
  
    |Etkinlik|Değer|  
    |--------------|-----------|  
    |1. WriteLine|"Hizmet: Tamamlanmış Alma"|  
    |2. WriteLine|"Hizmet: Alınan = " + requestMessage|  
  
     İş akışı şimdi şu şekilde görünmelidir:  
  
     ![WriteLine etkinliklerini ekledikten sonra sıra](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-writelines.jpg)  
  
9. **Aktivitedeki** <xref:System.ServiceModel.Activities.TransactedReceiveScope> Ikinci `PrintTransactionInfo` <xref:System.Activities.Statements.WriteLine> etkinlikten sonra etkinliği sürükleyin ve bırakın.  
  
     ![PrintTransactionInfo ekledikten sonra sıra](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-printtransactioninfo.jpg )  
  
10. Etkinlikten `PrintTransactionInfo` sonra <xref:System.Activities.Statements.Assign> bir etkinliği sürükleyin ve bırakın ve özelliklerini aşağıdaki tabloya göre ayarlayın.  
  
    |Özellik|Değer|  
    |--------------|-----------|  
    |Alıcı|replyMessage|  
    |Değer|"Hizmet: Yanıt gönderme."|  
  
11. Etkinlikten <xref:System.Activities.Statements.WriteLine> <xref:System.Activities.Statements.Assign> sonra bir etkinliği sürükleyin <xref:System.Activities.Statements.WriteLine.Text%2A> ve bırakın ve özelliğini "Hizmet: Yanıtla başlat" olarak ayarlayın.  
  
     İş akışı şimdi şu şekilde görünmelidir:  
  
     ![Atama ve WriteLine ekledikten sonra](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-sbr-writeline.jpg)  
  
12. Etkinliği sağ tıklatın ve **SendReply oluştur'u** seçin <xref:System.Activities.Statements.WriteLine> ve son etkinlikten sonra yapıştırın. <xref:System.ServiceModel.Activities.Receive> `SendReplyToReceive` Etkinlikte **Tanımla...** bağlantısını tıklatın ve aşağıdaki ayarları yapın.  
  
     ![İleti ayarlarını yanıtla](./media/flowing-transactions-into-and-out-of-workflow-services/reply-message-settings.jpg)  
  
13. Etkinlikten <xref:System.Activities.Statements.WriteLine> `SendReplyToReceive` sonra bir etkinliği sürükleyin ve <xref:System.Activities.Statements.WriteLine.Text%2A> bırakın ve özelliğini "Hizmet: Gönderilen Yanıt" olarak ayarlayın.  
  
14. Bir <xref:System.Activities.Statements.WriteLine> etkinliği iş akışının en altında sürükleyin <xref:System.Activities.Statements.WriteLine.Text%2A> ve bırakın ve özelliğini "Hizmet: İş akışı sona erer, çıkmak için ENTER tuşuna basın." olarak ayarlayın.  
  
     Tamamlanan hizmet iş akışı aşağıdaki gibi görünmelidir:  
  
     ![Komple Servis İş Akışı](./media/flowing-transactions-into-and-out-of-workflow-services/service-complete-workflow.jpg)  
  
### <a name="implement-the-workflow-client"></a>İş akışı istemcisini uygulama  
  
1. `Common` Projeye çağrılan `WorkflowClient` yeni bir WCF İş Akışı uygulaması ekleyin. Bunu yapmak için `Common` projeyi sağ tıklatın, **Ekle**, **Yeni Öğe ... ,** Yüklü **Şablonlar** altında **İş Akışı'nı** seçin ve **Etkinlik'i**seçin.  
  
     ![Etkinlik projesi ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/add-activity-project.jpg)  
  
2. Bir <xref:System.Activities.Statements.Sequence> etkinliği tasarım yüzeyine sürükleyin ve bırakın.  
  
3. Etkinlik içinde sürükleyin <xref:System.Activities.Statements.WriteLine> ve bir <xref:System.Activities.Statements.WriteLine.Text%2A> etkinliği bırakın ve özelliğini `"Client: Workflow starting"` <xref:System.Activities.Statements.Sequence> İş akışı şimdi şu şekilde görünmelidir:  
  
     ![WriteLine etkinliği ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-activity.jpg)  
  
4. Etkinlikten <xref:System.Activities.Statements.WriteLine> sonra <xref:System.Activities.Statements.TransactionScope> bir etkinliği sürükleyin ve bırakın.  <xref:System.Activities.Statements.TransactionScope> Etkinliği seçin, Değişkenler düğmesini tıklatın ve aşağıdaki değişkenleri ekleyin.  
  
     ![TransactionScope'a değişken ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/transactionscope-variables.jpg)  
  
5. Bir <xref:System.Activities.Statements.Sequence> etkinliği sürükleyin ve aktivitenin <xref:System.Activities.Statements.TransactionScope> gövdesine bırakın.  
  
6. Bir `PrintTransactionInfo` etkinliği sürükleyin ve bırakın<xref:System.Activities.Statements.Sequence>  
  
7. Etkinlikten <xref:System.Activities.Statements.WriteLine> `PrintTransactionInfo` sonra bir etkinliği sürükleyin <xref:System.Activities.Statements.WriteLine.Text%2A> ve bırakın ve özelliğini "İstemci: Başlangıç Gönder" olarak ayarlayın. İş akışı şimdi şu şekilde görünmelidir:  
  
     ![İstemci Ekleme: Gönderme etkinliklerini başlangıç](./media/flowing-transactions-into-and-out-of-workflow-services/client-add-cbs-writeline.jpg)  
  
8. Etkinlikten <xref:System.Activities.Statements.Assign> sonra <xref:System.ServiceModel.Activities.Send> bir etkinliği sürükleyin ve bırakın ve aşağıdaki özellikleri ayarlayın:  
  
    |Özellik|Değer|  
    |--------------|-----------|  
    |Endpointconfigurationname|iş akışıServiceEndpoint|  
    |ThrottledRequests|BaşlangıçÖrneği|  
    |Hizmet Sözleşme Adı|ITransactionSample|  
  
     İş akışı şimdi şu şekilde görünmelidir:  
  
     ![Gönder etkinlik özelliklerini ayarlama](./media/flowing-transactions-into-and-out-of-workflow-services/client-send-activity-settings.jpg)  
  
9. **Tanımla...** bağlantısını tıklayın ve aşağıdaki ayarları yapın:  
  
     ![Etkinlik iletisi ayarları gönderme](./media/flowing-transactions-into-and-out-of-workflow-services/send-message-settings.jpg)  
  
10. <xref:System.ServiceModel.Activities.Send> Etkinliği sağ tıklatın ve **YanıtLa oluştur'u**seçin. Etkinlik, <xref:System.ServiceModel.Activities.ReceiveReply> etkinlikten <xref:System.ServiceModel.Activities.Send> sonra otomatik olarak yerleştirilir.  
  
11. Tanımla'yı tıklatın... ReceiveReplyForSend etkinliğinde bağlantı kurun ve aşağıdaki ayarları yapın:  
  
     ![ReceiveForSend ileti ayarlarını ayarlama](./media/flowing-transactions-into-and-out-of-workflow-services/client-reply-message-settings.jpg)  
  
12. <xref:System.Activities.Statements.WriteLine> Bir etkinliği sürükleyin <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.ReceiveReply> bırakın ve <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "İstemci: Eksiksiz Gönder" olarak ayarlayın.  
  
13. Etkinlikten <xref:System.Activities.Statements.WriteLine> <xref:System.ServiceModel.Activities.ReceiveReply> sonra bir etkinliği sürükleyin <xref:System.Activities.Statements.WriteLine.Text%2A> ve bırakın ve özelliğini "İstemci tarafına: Alınan yanıt = " + yanıtİletim  
  
14. Etkinlikten <xref:System.Activities.Statements.WriteLine> sonra `PrintTransactionInfo` bir etkinliği sürükleyin ve bırakın.  
  
15. Bir <xref:System.Activities.Statements.WriteLine> etkinliği iş akışının sonunda sürükleyin ve <xref:System.Activities.Statements.WriteLine.Text%2A> bırakın ve özelliğini "İstemci iş akışı sona erer" olarak ayarlayın. Tamamlanan istemci iş akışı aşağıdaki diyagram gibi görünmelidir.  
  
     ![Tamamlanan istemci iş akışı](./media/flowing-transactions-into-and-out-of-workflow-services/client-complete-workflow.jpg)  
  
16. Çözümü derleyin.  
  
### <a name="create-the-service-application"></a>Hizmet uygulamasını oluşturma  
  
1. Çözüme yeni `Service` bir Konsol Uygulaması projesi ekleyin. Aşağıdaki derlemelere başvurular ekleyin:  
  
    1. Sistem.Etkinlikler.dll  
  
    2. System.ServiceModel.dll  
  
    3. Sistem.ServiceModel.Activities.dll  
  
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
  
3. Projeye aşağıdaki app.config dosyasını ekleyin.  
  
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
  
### <a name="create-the-client-application"></a>İstemci uygulamasını oluşturma  
  
1. Çözüme yeni `Client` bir Konsol Uygulaması projesi ekleyin. System.Activities.dll adresine bir başvuru ekleyin.  
  
2. program.cs dosyasını açın ve aşağıdaki kodu ekleyin.  
  
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
