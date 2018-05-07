---
title: Uzun Süre Çalışan Bir İş Akışı Hizmeti Oluşturma
ms.date: 03/30/2017
ms.assetid: 4c39bd04-5b8a-4562-a343-2c63c2821345
ms.openlocfilehash: 1ddb995b849a15451c36d5d11c95a4904a3e0496
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="creating-a-long-running-workflow-service"></a>Uzun Süre Çalışan Bir İş Akışı Hizmeti Oluşturma
Bu konu, uzun süre çalışan iş akışı hizmeti oluşturmayı açıklar. İş akışı hizmetleri uzun süre çalışan uzun bir süre için çalıştırabilirsiniz. Belirli bir noktada iş akışı için bazı ek bilgiler bekleyen boşta gidebilir. Bu meydana geldiğinde iş akışını bir SQL veritabanına kalıcı ve bellekten kaldırılır. Ek bilgi kullanılabilir hale geldiğinde iş akışı örneği belleğe geri yüklenir ve yürütmeye devam eder.  Bu senaryoda, oldukça basitleştirilmiş bir sıralama sistem uyguluyorsanız.  İstemci sırasını başlatmak için iş akışı hizmeti için bir Başlangıç iletisi gönderir. Bu, istemciye bir sipariş Kimliğini döndürür. Bu noktada iş akışı hizmeti istemciden başka bir ileti bekliyor ve boşta durumuna geçtiğinde ve SQL Server veritabanına kalıcı.  İstemci öğeyi sıralamak için sonraki ileti gönderdiğinde, iş akışı hizmeti belleğe geri yüklenmez ve sipariş işleme tamamlanır. Kod örneğinde öğe siparişe eklenmiş belirten bir dize döndürür. Kod örneği teknolojisi, ancak bunun yerine bir uzun süre çalışan iş akışı hizmetleri gösterilmektedir basit örnek gerçek dünya uygulamasının olması düşünülmemiştir. Bu konu nasıl oluşturulacağını bilmeniz varsayar [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] projeler ve çözümler.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu anlatımda kullanmak için aşağıdaki yazılımlar olmalıdır:  
  
1.  Microsoft SQL Server 2008  
  
2.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]  
  
3.  Microsoft  [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]  
  
4.  WCF ile tanıdık ve [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ve projeleri/çözümler oluşturmak nasıl biliyorsunuz.  
  
### <a name="to-setup-the-sql-database"></a>SQL veritabanı kurulumu için  
  
1.  Kalıcı olmasını iş akışı hizmeti örnekleri için Microsoft SQL Server'ın yüklü olması gerekir ve kalıcı iş akışı örneklerini depolamak için bir veritabanı yapılandırmanız gerekir. Microsoft SQL Management Studio'yu tıklayarak çalıştırın **Başlat** düğmesi, seçme **tüm programlar**, **Microsoft SQL Server 2008**, ve **Microsoft SQL Management Studio'yu**.  
  
2.  Tıklatın **Bağlan** SQL Server örneğine oturum düğmesi  
  
3.  Sağ tıklayın **veritabanları** ağaç görünümü seçip **yeni veritabanı...** adlı yeni bir veritabanı oluşturmak için `SQLPersistenceStore`.  
  
4.  Gerekli veritabanı şemalarını ayarlamak için SQLPersistenceStore veritabanında C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en dizininde bulunan SqlWorkflowInstanceStoreSchema.sql komut dosyasını çalıştırın.  
  
5.  Gerekli veritabanı mantığı oluşturan ayarlamak için SQLPersistenceStore veritabanında C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en dizininde bulunan SqlWorkflowInstanceStoreLogic.sql komut dosyasını çalıştırın.  
  
### <a name="to-create-the-web-hosted-workflow-service"></a>Web oluşturmak için iş akışı hizmeti barındırılan  
  
1.  Boş bir oluşturma [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] çözümü adlandırın `OrderProcessing`.  
  
2.  Adlı yeni bir WCF iş akışı hizmeti uygulaması projesi eklemek `OrderService` çözüme.  
  
3.  Proje Özellikleri iletişim kutusunda seçin **Web** sekmesi.  
  
    1.  Altında **eylemi Başlat** seçin **belirli sayfa** ve belirtin `Service1.xamlx`.  
  
         ![İş akışı hizmeti proje Web özellikleri](../../../../docs/framework/wcf/feature-details/media/startaction.png "StartAction")  
  
    2.  Altında **sunucuları** seçin **yerel IIS Web sunucusunu kullan**.  
  
         ![Yerel Web sunucusu ayarları](../../../../docs/framework/wcf/feature-details/media/uselocalwebserver.png "UseLocalWebServer")  
  
        > [!WARNING]
        >  Çalıştırmalısınız [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] bu ayarı yapmak için Yönetici modunda.  
  
         Bu iki adımı, IIS tarafından barındırılması için iş akışı hizmeti projesini yapılandırın.  
  
4.  Açık `Service1.xamlx` açık ve varolan silme ise **ReceiveRequest** ve **SendResponse** etkinlikler.  
  
5.  Seçin **sıralı hizmet** etkinliği ve tıklatın **değişkenleri** bağlamak ve aşağıdaki çizimde gösterilen değişkenleri ekleyin. Bunun yapılması kullanılacak bazı değişkenler daha sonra iş akışı hizmetinde ekler.  
  
    > [!NOTE]
    >  CorrelationHandle değişken türü açılan değilse seçin **türleri için Gözat** gelen açılır. Yazın, CorrelationHandle **türü adı** kutusuna liste kutusundan CorrelationHandle seçin ve tıklatın **Tamam**.  
  
     ![Değişkenleri eklemek](../../../../docs/framework/wcf/feature-details/media/addvariables.gif "AddVariables")  
  
6.  Sürükleme ve bırakma bir **ReceiveAndSendReply** etkinlik şablonuna **sıralı hizmet** etkinlik. Bu etkinlik kümesinin bir istemciden bir ileti alırsınız ve yanıt geri gönderin.  
  
    1.  Seçin **alma** etkinliği ve özellikler aşağıdaki çizimde vurgulanan kümesi.  
  
         ![Küme alacak etkinlik özellikleri](../../../../docs/framework/wcf/feature-details/media/setreceiveproperties.png "SetReceiveProperties")  
  
         DisplayName özelliğini Al etkinliğinin Tasarımcısı'nda görüntülenen adını ayarlar. ServiceContractName ve OperationName özellikleri hizmet sözleşmesini ve Al etkinliği tarafından uygulanan işlem adını belirtin. İş akışı hizmetleri sözleşmeleri nasıl kullanıldığı konusunda daha fazla bilgi için bkz: [iş akışında sözleşmeleri kullanma](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).  
  
    2.  Tıklatın **tanımlayın...**  bağlamak **ReceiveStartOrder** etkinliği ve aşağıdaki çizimde gösterilen özellikleri ayarlayın.  Dikkat **parametreleri** radyo düğmesi seçilirse, adlı bir parametre `p_customerName` bağlı `customerName` değişkeni. Bu yapılandırır **alma** bazı veri almasına ve bu verileri yerel değişkenlere bağlamak için etkinlik.  
  
         ![Al etkinliği tarafından alınan veri ayarı](../../../../docs/framework/wcf/feature-details/media/setreceivecontent.png "SetReceiveContent")  
  
    3.  Seçin **SendReplyToReceive** etkinliği ve aşağıdaki çizimde gösterilen vurgulanan özelliğini ayarlayın.  
  
         ![SendReply etkinlik özelliklerini ayarlama](../../../../docs/framework/wcf/feature-details/media/setreplyproperties.png "SetReplyProperties")  
  
    4.  Tıklatın **tanımlayın...**  bağlamak **SendReplyToStartOrder** etkinliği ve aşağıdaki çizimde gösterilen özellikleri ayarlayın. Dikkat **parametreleri** radyo düğmesinin seçili; adlı bir parametre `p_orderId` bağlı `orderId` değişkeni. Bu ayar SendReplyToStartOrder etkinlik çağırana dize türünde değer döndürme belirtir.  
  
         ![SendReply etkinlik içerik verileri yapılandırma](../../../../docs/framework/wcf/feature-details/media/setreplycontent.png "SetReplyContent")  
  
    5.  Ata aktivite arasında sürükleyip **alma** ve **SendReply** etkinlikleri ve aşağıdaki çizimde gösterildiği gibi özellikleri ayarlayın:  
  
         ![Ata etkinlik ekleme](../../../../docs/framework/wcf/feature-details/media/addassign.png "AddAssign")  
  
         Bu yeni bir sıra kimliği oluşturur ve OrderID değişken değeri yerleştirir.  
  
    6.  Seçin **ReplyToStartOrder** etkinlik. Üç nokta düğmesini Özellikler penceresinde **CorrelationInitializers**. Seçin **Başlatıcısı ekleme** bağlantı, girin `orderIdHandle` Başlatıcı metin kutusuna bağıntı türü için sorgu bağıntı başlatıcı seçin ve XPATH sorguları açılan kutusundan altında p_orderId seçin. Bu ayarlar aşağıdaki çizimde gösterilmektedir. **Tamam**'ı tıklatın.  Bu iş akışı hizmeti örneği ile istemci arasında bir ilişki başlatır. Kimliği alınan bu sırada içeren bir ileti olduğunda bu iş akışı hizmeti örneğine yönlendirilir.  
  
         ![Bağıntı başlatıcı ekleme](../../../../docs/framework/wcf/feature-details/media/addcorrelationinitializers.png "AddCorrelationInitializers")  
  
7.  Sürükleme ve bırakma başka **ReceiveAndSendReply** etkinliği iş akışı sonuna (dışında **dizisi** ilk içeren **alma** ve  **SendReply** etkinlikleri). Bu, istemci tarafından gönderilen ikinci bir ileti alırsınız ve yanıtlamak.  
  
    1.  Seçin **dizisi** yeni eklenen içeren **alma** ve **SendReply** etkinlikleri ve tıklatın **değişkenleri** düğmesi. Aşağıdaki çizimde vurgulanan değişkeni ekleyin:  
  
         ![Yeni değişkenleri ekleme](../../../../docs/framework/wcf/feature-details/media/addorderitemidvariable.png "AddOrderItemIdVariable")  
  
    2.  Seçin **alma** etkinliği ve aşağıdaki çizimde gösterilen özellikleri ayarlayın:  
  
         ![Alma acitivity özelliklerini ayarlamak](../../../../docs/framework/wcf/feature-details/media/setreceiveproperties2.png "SetReceiveProperties2")  
  
    3.  Tıklatın **tanımlayın...**  bağlamak **ReceiveAddItem** etkinliği ve aşağıdaki çizimde gösterilen parametreler ekleyin: Bu iki parametre, sipariş kimliği ve sipariş öğenin kimliği kabul etmek için alma etkinliğini yapılandırır.  
  
         ![Alma için ikinci parametrelerini belirterek](../../../../docs/framework/wcf/feature-details/media/addreceive2parameters.png "AddReceive2Parameters")  
  
    4.  Tıklatın **CorrelateOn** üç nokta düğmesini tıklatın ve girin `orderIdHandle`. Altında **XPath sorguları**, açılan oku tıklatın ve seçin `p_orderId`. Bu ikinci bağıntı yapılandırır etkinlik alırsınız. Bağıntı hakkında daha fazla bilgi için bkz: [bağıntı](../../../../docs/framework/wcf/feature-details/correlation.md).  
  
         ![CorrelatesOn özelliğinin ayarlanması](../../../../docs/framework/wcf/feature-details/media/correlateson.png "CorrelatesOn")  
  
    5.  Sürükleme ve bırakma bir **varsa** etkinlik hemen sonra **ReceiveAddItem** etkinlik. Bu etkinlik yalnızca bir if gibi davranan deyimi.  
  
        1.  Ayarlama **koşulu** özelliği `itemId=="Zune HD" (itemId="Zune HD" for Visual Basic)`  
  
        2.  Sürükleme ve bırakma bir **atamak** etkinliğinde için **sonra** bölümü ve başka bir dosyaya **Else** bölüm özelliklerini ayarlamak **atamak** Aşağıdaki çizimde gösterildiği gibi etkinlikler.  
  
             ![Hizmet çağrının sonucu atama](../../../../docs/framework/wcf/feature-details/media/resultassign.png "ResultAssign")  
  
             Koşul ise `true` **sonra** bölüm yürütülür. Koşul ise `false` **Else** bölüm gerçekleştirilir.  
  
        3.  Seçin **SendReplyToReceive** etkinliği ve kümesi **DisplayName** aşağıdaki çizimde gösterilen özelliği.  
  
             ![SendReply etkinlik özelliklerini ayarlama](../../../../docs/framework/wcf/feature-details/media/setreply2properties.png "SetReply2Properties")  
  
        4.  Tıklatın **tanımlayın...**  bağlamak **SetReplyToAddItem** etkinliği ve aşağıdaki çizimde gösterildiği gibi yapılandırın. Bu yapılandırır **SendReplyToAddItem** değeri döndürmek için etkinliği `orderResult` değişkeni.  
  
             ![Veri bağlama SendReply aktivite için ayarı](../../../../docs/framework/wcf/feature-details/media/replytoadditemcontent.gif "ReplyToAddItemContent")  
  
8.  Web.config dosyasını açın ve aşağıdaki öğeleri ekleyin \<davranışı > bölümü iş akışı kalıcılığı etkinleştir.  
  
    ```xml  
    <sqlWorkflowInstanceStore connectionString="Data Source=your-machine\SQLExpress;Initial Catalog=SQLPersistenceStore;Integrated Security=True;Asynchronous Processing=True" instanceEncodingOption="None" instanceCompletionAction="DeleteAll" instanceLockedExceptionAction="BasicRetry" hostLockRenewalPeriod="00:00:30" runnableInstancesDetectionPeriod="00:00:02" />  
              <workflowIdle timeToUnload="0"/>  
    ```  
  
    > [!WARNING]
    >  Önceki kod parçacığında bulunan SQL server örneği adı ve ana bilgisayar değiştirdiğinizden emin olun.  
  
9. Çözümü oluşturun.  
  
### <a name="to-create-a-client-application-to-call-the-workflow-service"></a>İş akışı hizmeti çağırmak için bir istemci uygulaması oluşturmak için  
  
1.  Adlı yeni bir konsol uygulama projesi eklemek `OrderClient` çözüme.  
  
2.  Aşağıdaki derlemelerine başvurular ekleyin `OrderClient` proje  
  
    1.  System.ServiceModel.dll  
  
    2.  System.ServiceModel.Activities.dll  
  
3.  Bir iş akışı hizmetine hizmet başvurusu ekleyin ve belirtin `OrderService` ad alanı olarak.  
  
4.  İçinde `Main()` istemci projesinin yöntemi aşağıdaki kodu ekleyin:  
  
    ```  
    static void Main(string[] args)  
    {  
       // Send initial message to start the workflow service  
       Console.WriteLine("Sending start message");  
       StartOrderClient startProxy = new StartOrderClient();  
       string orderId = startProxy.StartOrder("Kim Abercrombie");  
  
       // The workflow service is now waiting for the second message to be sent  
       Console.WriteLine("Workflow service is idle...");  
       Console.WriteLine("Press [ENTER] to send an add item message to reactivate the workflow service...");  
       Console.ReadLine();  
  
       // Send the second message  
       Console.WriteLine("Sending add item message");  
       AddItemClient addProxy = new AddItemClient();  
       AddItem item = new AddItem();  
       item.p_itemId = "Zune HD";  
       item.p_orderId = orderId;  
  
       string orderResult = addProxy.AddItem(item);  
       Console.WriteLine("Service returned: " + orderResult);  
    }  
    ```  
  
5.  Çözümü derleme ve çalıştırma `OrderClient` uygulama. İstemci aşağıdaki metni görüntülenir:  
  
    ```Output  
    Sending start messageWorkflow service is idle...Press [ENTER] to send an add item message to reactivate the workflow service...  
    ```  
  
6.  İş akışı hizmeti kalıcı olduğunu doğrulamak için SQL Server Management Studio adresine giderek başlatın **Başlat** menüsünde seçme **tüm programlar**, **Microsoft SQL Server 2008**, **SQL Server Management Studio**.  
  
    1.  Sol bölmedeki'nı genişletin, **veritabanları**, **SQLPersistenceStore**, **görünümleri** ve sağ tıklatma **System.Activities.DurableInstancing.Instances**  seçip **ilk 1000 satırı Seç**. İçinde **sonuçları** bölmesinde listelenen en az bir örnek görmek doğrulayın. Çalıştırılırken bir özel durum oluştu durumunda diğer önceki çalıştırır örneklerden olabilir. Sağ tıklayarak var olan satırları silebilirsiniz **System.Activities.DurableInstancing.Instances** ve seçerek **Düzenle üst 200 satırı**, ENTER tuşuna basın **yürütme** düğmesi Sonuçlar bölmesinde tüm satırları ve seçerek **silmek**.  Veritabanında görüntülenen örneği doğrulamak için örnek uygulamanızın oluşturulan, örnekleri görünüm istemci çalıştırılmadan önce boş olduğundan emin olun. İstemci yeniden çalışan çalıştırın (ilk 1000 satırı Seç) sorgu ve doğrulama sonra yeni bir örneği eklendi.  
  
7.  İş akışı hizmeti Ekle öğesini ileti göndermek için enter tuşuna basın. İstemci aşağıdaki metni görüntülenir:  
  
    ```Output  
    Sending add item messageService returned: Item added to orderPress any key to continue . . .  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş Akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)
