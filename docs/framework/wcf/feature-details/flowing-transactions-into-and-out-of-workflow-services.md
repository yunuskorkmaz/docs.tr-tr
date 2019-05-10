---
title: İş Akışı Hizmetlerine İşlemlerin Giriş ve Çıkış Akışını Gerçekleştirme
ms.date: 03/30/2017
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
ms.openlocfilehash: 7c47810ae168d39d7ebcd96952a75d6a3ba4d263
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592819"
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a>İş Akışı Hizmetlerine İşlemlerin Giriş ve Çıkış Akışını Gerçekleştirme
İş akışı hizmetler ve istemcileri işlemlerine katılabilmesi.  Bir hizmet işlemi bir ortam işlem bir parçası haline getirin bir <xref:System.ServiceModel.Activities.Receive> etkinlik içinde bir <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinlik. Tarafından yapılan tüm çağrıların bir <xref:System.ServiceModel.Activities.Send> veya <xref:System.ServiceModel.Activities.SendReply> etkinliğ <xref:System.ServiceModel.Activities.TransactedReceiveScope> ortam işlem içinde de yapılacaktır. Bir iş akışı istemci uygulaması kullanarak bir ortam işlem oluşturabilirsiniz <xref:System.Activities.Statements.TransactionScope> ortam işlem kullanarak etkinlik ve arama hizmeti işlemleri. Bu konuda, bir iş akışı hizmeti ve katılan iş akışı istemci işlemleri oluşturma işlemini gösterir.  
  
> [!WARNING]
>  Bir iş akışı hizmet örneği, bir işlem içinde yüklenir ve iş akışı içeren bir <xref:System.Activities.Statements.Persist> etkinliği iş akışı örneği askıda işlem zaman aşımına uğrayana kadar.  
  
> [!IMPORTANT]
>  Kullandığınız her bir <xref:System.ServiceModel.Activities.TransactedReceiveScope> iş akışı tüm alır yerleştirmek için önerilen <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinlikler.  
  
> [!IMPORTANT]
>  Kullanırken <xref:System.ServiceModel.Activities.TransactedReceiveScope> ve iletiler geldiğinde yanlış sırada, iş akışı, ilk sıra dışında iletisi göndermeyi çalışırken iptal edilecek. İş akışı boş kalır, iş akışınızı her zaman tutarlı noktası durduruluyor emin olmanız gerekir. Bu, bir önceki Kalıcılık noktasından iş akışını iş akışı durduruldu yeniden başlatmanıza olanak tanır.  
  
### <a name="create-a-shared-library"></a>Paylaşılan bir kitaplık oluşturun  
  
1. Yeni bir boş Visual Studio çözümü oluşturun.  
  
2. Adlı yeni bir sınıf kitaplığı projesi Ekle `Common`. Aşağıdaki derlemelere başvurular ekleyin:  
  
    - System.Activities.dll  
  
    - System.ServiceModel.dll  
  
    - System.ServiceModel.Activities.dll  
  
    - System.Transactions.dll  
  
3. Adlı yeni bir sınıf ekleyin `PrintTransactionInfo` için `Common` proje. Bu sınıf türetilir <xref:System.Activities.NativeActivity> ve aşırı <xref:System.Activities.NativeActivity.Execute%2A> yöntemi.  
  
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
  
     Bu ortam işlem hakkında bilgi görüntüler ve bu konuda kullanılan hizmet ve istemci iş akışlarında kullanılan yerel bir etkinliktir. Bu etkinlik içinde kullanılabilir hale getirmek için çözümü derleyin **ortak** bölümünü **araç kutusu**.  
  
### <a name="implement-the-workflow-service"></a>Bir iş akışı hizmet ekleme  
  
1. Yeni bir WCF iş akışı adlı hizmet ekleme `WorkflowService` için `Common` proje. Bu sağ tıklama yapmanız `Common` proje, select **Ekle**, **yeni öğe...** Seçin **iş akışı** altında **yüklü şablonlar** seçip **WCF iş akışı hizmeti**.  
  
     ![Bir iş akışı hizmeti ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/add-workflow-service.jpg)  
  
2. Varsayılan silme `ReceiveRequest` ve `SendResponse` etkinlikler.  
  
3. Sürükle ve bırak bir <xref:System.Activities.Statements.WriteLine> etkinliğini `Sequential Service` etkinlik. Text özelliğinin ayarlanacağı ifade `"Workflow Service starting ..."` aşağıdaki örnekte gösterildiği gibi.  
  
     ! [İçin sıralı hizmeti activity(./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-sequential-service.jpg) WriteLine etkinlik ekleme  
  
4. Sürükle ve bırak bir <xref:System.ServiceModel.Activities.TransactedReceiveScope> sonra <xref:System.Activities.Statements.WriteLine> etkinlik. <xref:System.ServiceModel.Activities.TransactedReceiveScope> Etkinlik bulunabilir **Mesajlaşma** bölümünü **araç kutusu**. <xref:System.ServiceModel.Activities.TransactedReceiveScope> Etkinlik iki bölümden oluşan **istek** ve **gövdesi**. **İstek** bölüm içeren <xref:System.ServiceModel.Activities.Receive> etkinlik. **Gövdesi** bölümünde bir ileti aldıktan sonra bir işlem içinde çalıştırmak için etkinlikleri içerir.  
  
     ![TransactedReceiveScope etkinlik ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/transactedreceivescope-activity.jpg)  
  
5. Seçin <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinliği ve tıklatın **değişkenleri** düğmesi. Aşağıdaki değişkenleri ekleyin.  
  
     ![TransactedReceiveScope için değişkenleri ekleniyor](./media/flowing-transactions-into-and-out-of-workflow-services/add-transactedreceivescope-variables.jpg)  
  
    > [!NOTE]
    >  Varsayılan olarak yoktur veri değişkeni silebilirsiniz. Varolan bir tanıtıcı değişkeni de kullanabilirsiniz.  
  
6. Sürükle ve bırak bir <xref:System.ServiceModel.Activities.Receive> etkinliğ **istek** bölümünü <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinlik. Aşağıdaki özellikleri ayarlayın:  
  
    |Özellik|Değer|  
    |--------------|-----------|  
    |CanCreateInstance|TRUE (onay kutusu denetimi)|  
    |OperationName|StartSample|  
    |ServiceContractName|ITransactionSample|  
  
     İş akışı şu şekilde görünmelidir:  
  
     ![Receive etkinlik ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/add-receive-activity.jpg)  
  
7. Tıklayın **tanımlayın...**  bağlantısını <xref:System.ServiceModel.Activities.Receive> etkinlik ve şu ayarları yapın:  
  
     ![İleti Ayarları Al etkinliğinin ayarlama](./media/flowing-transactions-into-and-out-of-workflow-services/receive-message-settings.jpg)  
  
8. Sürükle ve bırak bir <xref:System.Activities.Statements.Sequence> gövde bölümünü etkinliğini <xref:System.ServiceModel.Activities.TransactedReceiveScope>. İçinde <xref:System.Activities.Statements.Sequence> etkinliğini sürükleyip iki <xref:System.Activities.Statements.WriteLine> etkinlikleri ve kümesi <xref:System.Activities.Statements.WriteLine.Text%2A> aşağıdaki tabloda gösterildiği gibi özellikleri.  
  
    |Etkinlik|Değer|  
    |--------------|-----------|  
    |1 WriteLine|"Hizmet: Tamamlanan Al"|  
    |2 WriteLine|"Hizmet: Alınan = "+ requestMessage|  
  
     İş akışı gibi görünmelidir:  
  
     ![WriteLine etkinlik ekledikten sonra sıra](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-writelines.jpg)  
  
9. Sürükle ve bırak `PrintTransactionInfo` etkinlikten sonra ikinci <xref:System.Activities.Statements.WriteLine> etkinliğinde **gövdesi** içinde <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinlik.  
  
     ![PrintTransactionInfo ekledikten sonra sıra](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-printtransactioninfo.jpg )  
  
10. Sürükle ve bırak bir <xref:System.Activities.Statements.Assign> etkinlikten sonra `PrintTransactionInfo` etkinlik ve aşağıdaki tabloya göre özelliklerini ayarlayın.  
  
    |Özellik|Değer|  
    |--------------|-----------|  
    |Bitiş|replyMessage|  
    |Değer|"Hizmet: Yanıtı gönderiliyor."|  
  
11. Sürükle ve bırak bir <xref:System.Activities.Statements.WriteLine> etkinlikten sonra <xref:System.Activities.Statements.Assign> etkinliği ve kümesi kendi <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "hizmeti: Yanıt başlar."  
  
     İş akışı gibi görünmelidir:  
  
     ![Atama ve WriteLine ekledikten sonra](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-sbr-writeline.jpg)  
  
12. Sağ tıklayın <xref:System.ServiceModel.Activities.Receive> etkinliği ve select **oluşturma SendReply** ve sonra son yapıştırın <xref:System.Activities.Statements.WriteLine> etkinlik. Tıklayın **tanımlayın...**  bağlantısını `SendReplyToReceive` etkinlik ve şu ayarları yapın.  
  
     ![Yanıt iletisi ayarları](./media/flowing-transactions-into-and-out-of-workflow-services/reply-message-settings.jpg)  
  
13. Sürükle ve bırak bir <xref:System.Activities.Statements.WriteLine> etkinlikten sonra `SendReplyToReceive` etkinliği ve kümesi sahip <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "hizmeti: Yanıt gönderildi."  
  
14. Sürükle ve bırak bir <xref:System.Activities.Statements.WriteLine> alt kümesi ve iş akışı etkinlik kendi <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "hizmeti: İş akışı, ENTER tuşuna basın çıkmak için sona erer."  
  
     Tamamlanmış hizmet iş akışı şu şekilde görünmelidir:  
  
     ![Tam hizmet iş akışı](./media/flowing-transactions-into-and-out-of-workflow-services/service-complete-workflow.jpg)  
  
### <a name="implement-the-workflow-client"></a>İş akışı istemcisini uygulama  
  
1. Adlı yeni bir WCF iş akışı uygulama ekleme `WorkflowClient` için `Common` proje. Bu sağ tıklama yapmanız `Common` proje, select **Ekle**, **yeni öğe...** Seçin **iş akışı** altında **yüklü şablonlar** seçip **etkinlik**.  
  
     ![Bir etkinlik proje ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/add-activity-project.jpg)  
  
2. Sürükle ve bırak bir <xref:System.Activities.Statements.Sequence> tasarım yüzeyine etkinlik.  
  
3. İçinde <xref:System.Activities.Statements.Sequence> etkinliğini sürükleyip bırakma bir <xref:System.Activities.Statements.WriteLine> etkinliği ve kümesi kendi <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini `"Client: Workflow starting"`. İş akışı gibi görünmelidir:  
  
     ![WriteLine etkinlik Ekle](./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-activity.jpg)  
  
4. Sürükle ve bırak bir <xref:System.Activities.Statements.TransactionScope> etkinlikten sonra <xref:System.Activities.Statements.WriteLine> etkinlik.  Seçin <xref:System.Activities.Statements.TransactionScope> etkinliği, değişkenleri düğmesini tıklatın ve aşağıdaki değişkenleri eklemek tıklayın.  
  
     ![TransactionScope için değişkenlerini ekleyin](./media/flowing-transactions-into-and-out-of-workflow-services/transactionscope-variables.jpg)  
  
5. Sürükle ve bırak bir <xref:System.Activities.Statements.Sequence> gövdesinin etkinliğini <xref:System.Activities.Statements.TransactionScope> etkinlik.  
  
6. Sürükle ve bırak bir `PrintTransactionInfo` etkinliğ <xref:System.Activities.Statements.Sequence>  
  
7. Sürükle ve bırak bir <xref:System.Activities.Statements.WriteLine> etkinlikten sonra `PrintTransactionInfo` etkinliği ve kümesi kendi <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "İstemci: Send başlamadan". İş akışı gibi görünmelidir:  
  
     ![İstemci ekleme: Gönderme işlemleri başlangıcı](./media/flowing-transactions-into-and-out-of-workflow-services/client-add-cbs-writeline.jpg)  
  
8. Sürükle ve bırak bir <xref:System.ServiceModel.Activities.Send> etkinlikten sonra <xref:System.Activities.Statements.Assign> etkinlik ve aşağıdaki özellikleri ayarlayın:  
  
    |Özellik|Değer|  
    |--------------|-----------|  
    |EndpointConfigurationName|workflowServiceEndpoint|  
    |OperationName|StartSample|  
    |ServiceContractName|ITransactionSample|  
  
     İş akışı gibi görünmelidir:  
  
     ![Send etkinlik özelliklerini ayarlama](./media/flowing-transactions-into-and-out-of-workflow-services/client-send-activity-settings.jpg)  
  
9. Tıklayın **tanımlayın...**  bağlayın ve şu ayarları yapın:  
  
     ![İleti ayarları etkinlik Gönder](./media/flowing-transactions-into-and-out-of-workflow-services/send-message-settings.jpg)  
  
10. Sağ tıklayın <xref:System.ServiceModel.Activities.Send> etkinliği ve select **oluşturma ReceiveReply**. <xref:System.ServiceModel.Activities.ReceiveReply> Etkinlik otomatik olarak yerleştirilecek sonra <xref:System.ServiceModel.Activities.Send> etkinlik.  
  
11. Tanımla... tıklayın ReceiveReplyForSend faaliyete bağlayın ve şu ayarları yapın:  
  
     ![ReceiveForSend ileti ayarları ayarlama](./media/flowing-transactions-into-and-out-of-workflow-services/client-reply-message-settings.jpg)  
  
12. Sürükle ve bırak bir <xref:System.Activities.Statements.WriteLine> arasında etkinliği <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.ReceiveReply> etkinlikleri ve kümesi kendi <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "İstemci: Tam gönderin."  
  
13. Sürükle ve bırak bir <xref:System.Activities.Statements.WriteLine> etkinlikten sonra <xref:System.ServiceModel.Activities.ReceiveReply> etkinliği ve kümesi kendi <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "istemci tarafında: Alınan yanıt = "+ replyMessage  
  
14. Sürükle ve bırak bir `PrintTransactionInfo` etkinlikten sonra <xref:System.Activities.Statements.WriteLine> etkinlik.  
  
15. Sürükle ve bırak bir <xref:System.Activities.Statements.WriteLine> sonunda kümesi ve iş akışı, etkinlik kendi <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "İstemci iş akışı sona erer." Tamamlanan istemci iş akışı aşağıdaki diyagramda gibi görünmelidir.  
  
     ![Tamamlanan istemci iş akışı](./media/flowing-transactions-into-and-out-of-workflow-services/client-complete-workflow.jpg)  
  
16. Çözümü oluşturun.  
  
### <a name="create-the-service-application"></a>Hizmet Uygulaması Oluştur  
  
1. Adlı yeni bir konsol uygulaması projesi eklemek `Service` çözüm. Aşağıdaki derlemelere başvurular ekleyin:  
  
    1. System.Activities.dll  
  
    2. System.ServiceModel.dll  
  
    3. System.ServiceModel.Activities.dll  
  
2. Aşağıdaki kod oluşturulan Program.cs dosyasını açın:  
  
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
  
3. Aşağıdaki app.config dosyasını projeye ekleyin.  
  
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
  
1. Adlı yeni bir konsol uygulaması projesi eklemek `Client` çözüm. System.Activities.dll bir başvuru ekleyin.  
  
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
