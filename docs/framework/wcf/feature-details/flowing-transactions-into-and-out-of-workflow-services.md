---
title: "İş Akışı Hizmetlerine İşlemlerin Giriş ve Çıkış Akışını Gerçekleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a38c0c224c93941efa767d142aa7738296a62f15
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a>İş Akışı Hizmetlerine İşlemlerin Giriş ve Çıkış Akışını Gerçekleştirme
İş akışı hizmetleri ve istemciler işlemlerde yer alabilir.  Bir hizmet işlemi ortam bir işlemin parçası olmaya yerleştirin bir <xref:System.ServiceModel.Activities.Receive> içinde etkinlik bir <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinlik. Tarafından yapılan çağrılar bir <xref:System.ServiceModel.Activities.Send> veya <xref:System.ServiceModel.Activities.SendReply> içinde etkinlik <xref:System.ServiceModel.Activities.TransactedReceiveScope> ortam işlem içinde da yapılır. Bir iş akışı istemci uygulamasını kullanarak bir ortam işlem oluşturabilirsiniz <xref:System.Activities.Statements.TransactionScope> ortam hareket kullanarak etkinliği ve çağrı hizmet işlemleri. Bu konu bir iş akışı hizmeti ve katılmak iş akışı istemci işlemleri oluşturmada size yol gösterir.  
  
> [!WARNING]
>  Bir iş akışı hizmeti örneği bir işlem içinde yüklenir ve iş akışı içeren bir <xref:System.Activities.Statements.Persist> etkinlik, iş akışı örneği askıda işlem zaman aşımına uğrayana kadar.  
  
> [!IMPORTANT]
>  Kullandığınız her bir <xref:System.ServiceModel.Activities.TransactedReceiveScope> iş akışı tüm Receives yerleştirmek için önerilen <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinlikler.  
  
> [!IMPORTANT]
>  Kullanırken <xref:System.ServiceModel.Activities.TransactedReceiveScope> ve iletiler geldiğinde yanlış sırayla, iş akışı, ilk bozuk ileti teslim çalışılırken iptal edilecek. İş akışı boş kalır, iş akışınızı her zaman tutarlı noktası durduruluyor emin olmanız gerekir. Bu iş akışı iptal önceki Kalıcılık noktası iş akışını yeniden başlatmanıza olanak tanır.  
  
### <a name="create-a-shared-library"></a>Paylaşılan bir kitaplık oluşturma  
  
1.  Yeni bir boş Visual Studio çözümü oluşturun.  
  
2.  Adlı yeni bir sınıf kitaplığı proje ekleme `Common`. Aşağıdaki derlemelere başvurular ekleyin:  
  
    -   System.Activities.dll  
  
    -   System.ServiceModel.dll  
  
    -   System.ServiceModel.Activities.dll  
  
    -   System.Transactions.dll  
  
3.  Adlı yeni bir sınıf ekleyin `PrintTransactionInfo` için `Common` projesi. Bu sınıfın türetildiği <xref:System.Activities.NativeActivity> ve overloads <xref:System.Activities.NativeActivity.Execute%2A> yöntemi.  
  
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
  
     Bu ortam işlem bilgilerini görüntüler ve bu konuda kullanılan hem hizmet hem de istemci iş akışlarında kullanılan yerel bir etkinliktir. Bu etkinlik olarak kullanılabilir hale getirmek çözümü derlemek **ortak** bölümünü **araç**.  
  
### <a name="implement-the-workflow-service"></a>İş akışı hizmeti uygulama  
  
1.  Yeni bir ekleme [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] adlı iş akışı hizmeti `WorkflowService` için `Common` projesi. Bu sağ tıklatma yapmak için `Common` proje, select **Ekle**, **yeni öğe...** Seçin **iş akışı** altında **yüklü şablonlar** seçip **WCF iş akışı hizmeti**.  
  
     ![Bir iş akışı hizmeti ekleme](../../../../docs/framework/wcf/feature-details/media/addwfservice.JPG "AddWFService")  
  
2.  Varsayılan silme `ReceiveRequest` ve `SendResponse` etkinlikler.  
  
3.  Sürükleme ve bırakma bir <xref:System.Activities.Statements.WriteLine> etkinliğini `Sequential Service` etkinlik. Text özelliğini `"Workflow Service starting ..."` aşağıdaki örnekte gösterildiği gibi.  
  
     ![WriteLine etkinlik ekleme](../../../../docs/framework/wcf/feature-details/media/addwriteline.JPG "AddWriteLine")  
  
4.  Sürükleme ve bırakma bir <xref:System.ServiceModel.Activities.TransactedReceiveScope> sonra <xref:System.Activities.Statements.WriteLine> etkinlik. <xref:System.ServiceModel.Activities.TransactedReceiveScope> Etkinlik bulunabilir **ileti** bölümünü **araç**. <xref:System.ServiceModel.Activities.TransactedReceiveScope> Etkinlik iki bölümden oluşan **isteği** ve **gövde**. **İsteği** bölüm içerir <xref:System.ServiceModel.Activities.Receive> etkinlik. **Gövde** bölüm, bir işlem içinde bir ileti alındı sonra yürütülecek etkinlikleri içerir.  
  
     ![TransactedReceiveScope etkinlik ekleme](../../../../docs/framework/wcf/feature-details/media/trs.JPG "TRS")  
  
5.  Seçin <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinliği ve tıklatın **değişkenleri** düğmesi. Aşağıdaki değişkenler ekleyin.  
  
     ![Değişkenleri TransactedReceiveScope ekleme](../../../../docs/framework/wcf/feature-details/media/trsvariables.JPG "TRSVariables")  
  
    > [!NOTE]
    >  Varsayılan olarak var olan veri değişken silebilirsiniz. Varolan bir tanıtıcı değişkeni de kullanabilirsiniz.  
  
6.  Sürükleme ve bırakma bir <xref:System.ServiceModel.Activities.Receive> içinde etkinlik **isteği** bölümünü <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinlik. Aşağıdaki özellikleri ayarlayın:  
  
    |Özellik|Değer|  
    |--------------|-----------|  
    |CanCreateInstance|TRUE (onay kutusunu işaretleyin)|  
    |OperationName|StartSample|  
    |ServiceContractName|ITransactionSample|  
  
     İş akışını aşağıdaki gibi görünmelidir:  
  
     ![Alma etkinlik ekleme](../../../../docs/framework/wcf/feature-details/media/serviceaddreceive.JPG "ServiceAddReceive")  
  
7.  Tıklatın **tanımlayın...**  bağlamak <xref:System.ServiceModel.Activities.Receive> etkinliği ve aşağıdaki ayarları yapın:  
  
     ![İleti ayarları alma etkinliğinin ayarı](../../../../docs/framework/wcf/feature-details/media/receivemessagesettings.JPG "ReceiveMessageSettings")  
  
8.  Sürükleme ve bırakma bir <xref:System.Activities.Statements.Sequence> gövde bölümünü etkinliğini <xref:System.ServiceModel.Activities.TransactedReceiveScope>. İçinde <xref:System.Activities.Statements.Sequence> etkinlik sürükleyip iki <xref:System.Activities.Statements.WriteLine> etkinlikleri ve kümesi <xref:System.Activities.Statements.WriteLine.Text%2A> aşağıdaki tabloda gösterildiği gibi özellikler.  
  
    |Etkinlik|Değer|  
    |--------------|-----------|  
    |1 WriteLine|"Hizmet: tamamlanmış alırsınız"|  
    |2 WriteLine|"Hizmet: alınan =" + requestMessage|  
  
     İş akışı gibi görünmelidir:  
  
     ![WriteLine etkinlikleri ekleme](../../../../docs/framework/wcf/feature-details/media/afteraddingwritelines.JPG "AfterAddingWriteLines")  
  
9. Sürükleme ve bırakma `PrintTransactionInfo` etkinlikten saniye sonra <xref:System.Activities.Statements.WriteLine> etkinliğinde **gövde** içinde <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinlik.  
  
     ![PrintTransactionInfo ekledikten sonra](../../../../docs/framework/wcf/feature-details/media/afteraddingprinttransactioninfo.JPG "AfterAddingPrintTransactionInfo")  
  
10. Sürükleme ve bırakma bir <xref:System.Activities.Statements.Assign> etkinlikten sonra `PrintTransactionInfo` etkinliği ve özelliklerini aşağıdaki tabloya göre ayarlayın.  
  
    |Özellik|Değer|  
    |--------------|-----------|  
    |Bitiş|replyMessage|  
    |Değer|"Hizmet: yanıt gönderme."|  
  
11. Sürükleme ve bırakma bir <xref:System.Activities.Statements.WriteLine> etkinlikten sonra <xref:System.Activities.Statements.Assign> etkinliği ve kümesi kendi <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğine "Hizmet: başlamak yanıt."  
  
     İş akışı gibi görünmelidir:  
  
     ![Atama ve WriteLine ekledikten sonra](../../../../docs/framework/wcf/feature-details/media/afteraddingsbrwriteline.JPG "AfterAddingSBRWriteLine")  
  
12. Sağ tıklayın <xref:System.ServiceModel.Activities.Receive> etkinliği ve select **oluşturma SendReply** ve sonra son yapıştırın <xref:System.Activities.Statements.WriteLine> etkinlik. Tıklatın **tanımlayın...**  bağlamak `SendReplyToReceive` etkinliği ve aşağıdaki ayarları yapın.  
  
     ![Yanıt iletisi ayarları](../../../../docs/framework/wcf/feature-details/media/replymessagesettings.JPG "ReplyMessageSettings")  
  
13. Sürükleme ve bırakma bir <xref:System.Activities.Statements.WriteLine> etkinlikten sonra `SendReplyToReceive` etkinliği ve kümesi var. <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğine "Hizmet: yanıt gönderildi."  
  
14. Sürükleme ve bırakma bir <xref:System.Activities.Statements.WriteLine> alt kümesi ve iş akışı etkinlik kendi <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğine "Hizmet: iş akışı sona erer, çıkmak için ENTER tuşuna basın."  
  
     Tamamlanmış hizmet iş akışı aşağıdaki gibi görünmelidir:  
  
     ![Hizmeti iş akışı tamamlamak](../../../../docs/framework/wcf/feature-details/media/servicecomplete.jpg "ServiceComplete")  
  
### <a name="implement-the-workflow-client"></a>İş akışı istemcisini uygulama  
  
1.  Adlı yeni bir WCF iş akışı uygulama eklemek `WorkflowClient` için `Common` projesi. Bu sağ tıklatma yapmak için `Common` proje, select **Ekle**, **yeni öğe...** Seçin **iş akışı** altında **yüklü şablonlar** seçip **etkinlik**.  
  
     ![Bir etkinlik proje ekleyin](../../../../docs/framework/wcf/feature-details/media/addactivity.JPG "AddActivity")  
  
2.  Sürükleme ve bırakma bir <xref:System.Activities.Statements.Sequence> tasarım yüzeyine etkinlik.  
  
3.  İçinde <xref:System.Activities.Statements.Sequence> etkinlik sürükle ve bırak bir <xref:System.Activities.Statements.WriteLine> etkinliği ve kümesi kendi <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğine `"Client: Workflow starting"`. İş akışı gibi görünmelidir:  
  
     ![WriteLine etkinlik eklemek](../../../../docs/framework/wcf/feature-details/media/clientaddwriteline.JPG "ClientAddWriteLine")  
  
4.  Sürükleme ve bırakma bir <xref:System.Activities.Statements.TransactionScope> etkinlikten sonra <xref:System.Activities.Statements.WriteLine> etkinlik.  Seçin <xref:System.Activities.Statements.TransactionScope> etkinliği, değişkenleri düğmesine tıklayın ve aşağıdaki değişkenleri eklemek tıklatın.  
  
     ![TransactionScope değişkenleri eklemek](../../../../docs/framework/wcf/feature-details/media/tsvariables.JPG "TSVariables")  
  
5.  Sürükleme ve bırakma bir <xref:System.Activities.Statements.Sequence> gövdesine etkinlik <xref:System.Activities.Statements.TransactionScope> etkinlik.  
  
6.  Sürükleme ve bırakma bir `PrintTransactionInfo` içinde etkinlik<xref:System.Activities.Statements.Sequence>  
  
7.  Sürükleme ve bırakma bir <xref:System.Activities.Statements.WriteLine> etkinlikten sonra `PrintTransactionInfo` etkinliği ve kümesi kendi <xref:System.Activities.Statements.WriteLine.Text%2A> "İstemci başına: Gönder" özelliğine. İş akışı gibi görünmelidir:  
  
     ![Etkinlikler ekleme](../../../../docs/framework/wcf/feature-details/media/clientaddcbswriteline.JPG "ClientAddCBSWriteLine")  
  
8.  Sürükleme ve bırakma bir <xref:System.ServiceModel.Activities.Send> etkinlikten sonra <xref:System.Activities.Statements.Assign> etkinliği ve aşağıdaki özellikleri ayarlayın:  
  
    |Özellik|Değer|  
    |--------------|-----------|  
    |EndpointConfigurationName|workflowServiceEndpoint|  
    |OperationName|StartSample|  
    |ServiceContractName|ITransactionSample|  
  
     İş akışı gibi görünmelidir:  
  
     ![Gönder etkinliği özellikleri ayarlama](../../../../docs/framework/wcf/feature-details/media/clientsendsettings.JPG "ClientSendSettings")  
  
9. Tıklatın **tanımlayın...**  bağlamak ve aşağıdaki ayarları yapın:  
  
     ![İleti ayarları etkinlik Gönder](../../../../docs/framework/wcf/feature-details/media/sendmessagesettings.JPG "SendMessageSettings")  
  
10. Sağ tıklayın <xref:System.ServiceModel.Activities.Send> etkinliği ve select **oluşturma ReceiveReply**. <xref:System.ServiceModel.Activities.ReceiveReply> Etkinlik otomatik olarak yerleştirilecek sonra <xref:System.ServiceModel.Activities.Send> etkinlik.  
  
11. Tanımla...'yı tıklatın bağlantı ReceiveReplyForSend faaliyete ve aşağıdaki ayarları yapın:  
  
     ![ReceiveForSend ileti ayarları ayarı](../../../../docs/framework/wcf/feature-details/media/clientreplymessagesettings.JPG "ClientReplyMessageSettings")  
  
12. Sürükleme ve bırakma bir <xref:System.Activities.Statements.WriteLine> etkinlik arasında <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.ReceiveReply> etkinlikleri ve kümesi kendi <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğine "İstemci: tamamını göndermek."  
  
13. Sürükleme ve bırakma bir <xref:System.Activities.Statements.WriteLine> etkinlikten sonra <xref:System.ServiceModel.Activities.ReceiveReply> etkinliği ve kümesi kendi <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğine "istemci tarafında: alınan yanıt =" + replyMessage  
  
14. Sürükleme ve bırakma bir `PrintTransactionInfo` etkinlikten sonra <xref:System.Activities.Statements.WriteLine> etkinlik.  
  
15. Sürükleme ve bırakma bir <xref:System.Activities.Statements.WriteLine> kümesi ve iş akışının sonunda etkinlik kendi <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "İstemci iş akışı sona erer." Tamamlanan istemci iş akışı aşağıdaki diyagramda gibi görünmelidir.  
  
     ![Tamamlanan istemci workfliow](../../../../docs/framework/wcf/feature-details/media/clientcompleteworkflow.jpg "ClientCompleteWorkflow")  
  
16. Çözümü oluşturun.  
  
### <a name="create-the-service-application"></a>Hizmet Uygulaması Oluştur  
  
1.  Adlı yeni bir konsol uygulaması projesi eklemek `Service` çözüme. Aşağıdaki derlemelere başvurular ekleyin:  
  
    1.  System.Activities.dll  
  
    2.  System.ServiceModel.dll  
  
    3.  System.ServiceModel.Activities.dll  
  
2.  Oluşturulan Program.cs dosyasının ve aşağıdaki kodu açın:  
  
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
  
3.  Aşağıdaki app.config dosyası projeye ekleyin.  
  
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
  
1.  Adlı yeni bir konsol uygulaması projesi eklemek `Client` çözüme. System.Activities.dll bir başvuru ekleyin.  
  
2.  Program.cs dosyasını açın ve aşağıdaki kodu ekleyin.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş Akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Windows Communication Foundation İşlemleri Genel Bakış](../../../../docs/framework/wcf/feature-details/transactions-overview.md)  
 [TransactedReceiveScope Kullanımı](../../../../docs/framework/windows-workflow-foundation/samples/use-of-transactedreceivescope.md)
