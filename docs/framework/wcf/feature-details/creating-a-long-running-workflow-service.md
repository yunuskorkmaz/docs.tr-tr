---
title: Uzun Süre Çalışan Bir İş Akışı Hizmeti Oluşturma
ms.date: 03/30/2017
ms.assetid: 4c39bd04-5b8a-4562-a343-2c63c2821345
ms.openlocfilehash: 1ca0f2ed4c2ab900191165d100848811e5436c3c
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425415"
---
# <a name="creating-a-long-running-workflow-service"></a>Uzun Süre Çalışan Bir İş Akışı Hizmeti Oluşturma
Bu konuda, uzun süre çalışan iş akışı hizmeti oluşturma işlemini açıklar. İş akışı hizmetleri uzun süre çalışan uzun süreler için çalıştırabilirsiniz. İş akışını belirli bir noktada bazı ek bilgiler için bekleyen boşta gidebilir. Bu meydana geldiğinde iş akışını bir SQL veritabanı'na kalıcı ve bellekten kaldırılır. Ek bilgilerin kullanıma sunulduğunda iş akışı örneği belleğe geri yüklenir ve yürütmeye devam eder.  Bu senaryoda, oldukça basitleştirilmiş bir sipariş sistemi uyguluyor.  İstemci sırasını başlatmak için iş akışı hizmeti için bir Başlangıç iletisi gönderir. İstemciye bir sipariş kimliği döndürür. Bu noktada iş akışı hizmeti istemciden başka bir ileti bekliyor ve boşta durumuna girer ve bir SQL Server veritabanına kalıcı hale getirilir.  İstemci bir öğe sıralamak için sonraki iletiyi gönderdiğinde, iş akışı hizmeti belleğe geri yüklenir ve sırasını işlemeyi tamamladıktan sonra. Kod örneğinde öğe sırasını eklenmiş belirten bir dize döndürür. Kod örneği, teknoloji, ancak bunun yerine uzun süre çalışan iş akışı hizmetleri gösteren basit örnek bir gerçek dünya uygulaması olarak hazırlanmamıştır. Bu konu Visual Studio 2012 projeler ve çözümler oluşturulacağını bildiğinizi varsayar.

## <a name="prerequisites"></a>Önkoşullar
 Bu anlatımda kullanmak için aşağıdaki yazılımlar olmalıdır:

1. Microsoft SQL Server 2008

2. Visual Studio 2012

3. Microsoft  [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]

4. WCF ve Visual Studio 2012 ile ilgili bilgi sahibi olduğunuz ve proje/çözüm oluşturmayı biliyorsanız.

### <a name="to-setup-the-sql-database"></a>SQL veritabanı kurulumu için

1. Kalıcı için iş akışı hizmet örneklerine yönelik, Microsoft SQL Server'ın yüklü olması gerekir ve kalıcı iş akışı örnekleri depolamak için bir veritabanı oluşturmanız gerekir. Microsoft SQL Management Studio tıklayarak çalıştırın **Başlat** düğmesi, seçerek **tüm programlar**, **Microsoft SQL Server 2008**, ve **Microsoft SQL Management Studio'yu**.

2. Tıklayın **Connect** için SQL Server örneği oturum açma düğmesi

3. Sağ tıklayın **veritabanları** ağaç görünümü seçip **yeni veritabanı...** adlı yeni bir veritabanı oluşturmak için `SQLPersistenceStore`.

4. Gerekli veritabanı şemaları ayarlamak için SQLPersistenceStore veritabanında C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en dizininde bulunan SqlWorkflowInstanceStoreSchema.sql komut dosyasını çalıştırın.

5. SQLPersistenceStore veritabanında gerekli veritabanı mantığı oluşturma ayarlanacak C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en dizininde bulunan SqlWorkflowInstanceStoreLogic.sql komut dosyasını çalıştırın.

### <a name="to-create-the-web-hosted-workflow-service"></a>İş akışı hizmeti barındırılan Web oluşturmak için

1. Boş bir Visual Studio 2012 çözümü oluşturmak için adlandırın `OrderProcessing`.

2. Adlı yeni bir WCF iş akışı hizmeti uygulaması projesi eklemek `OrderService` çözüm.

3. Proje Özellikleri iletişim kutusunda, seçmek **Web** sekmesi.

    1. Altında **başlatma eylemi** seçin **belirli sayfa** belirtin `Service1.xamlx`.

         ![İş akışı hizmeti proje Web özellikleri](./media/creating-a-long-running-workflow-service/start-action-specific-page-option.png "- belirli bir sayfaya seçeneği barındırılan web iş akışı hizmeti oluşturma")

    2. Altında **sunucuları** seçin **yerel IIS Web sunucusunu kullan**.

         ![Yerel Web sunucusu ayarlarını](./media/creating-a-long-running-workflow-service/use-local-web-server.png "- yerel IIS Web sunucusu kullan seçeneği barındırılan web iş akışı hizmeti oluşturma")

        > [!WARNING]
        >  Bu ayar yapmak için Yönetici modunda Visual Studio 2012 çalıştırmanız gerekir.

         Bu iki adımı, IIS tarafından barındırılan iş akışı hizmeti projenin yapılandırın.

4. Açık `Service1.xamlx` açık ve mevcut değil ise **ReceiveRequest** ve **SendResponse** etkinlikler.

5. Seçin **sıralı hizmeti** etkinliği ve tıklatın **değişkenleri** bağlamak ve aşağıdaki çizimde gösterilen değişkenleri ekleyin. Bunun yapılması kullanılacak olan bazı değişkenler daha sonra iş akışı hizmetinde ekler.

    > [!NOTE]
    >  Değişken türü açılan menü CorrelationHandle değilse seçin **vyhledat Typy** açılır listeden. Türü içinde CorrelationHandle **tür adı** kutusunda, liste kutusundan CorrelationHandle seçin ve tıklayın **Tamam**.

     ![Değişkenleri ekleyin](./media/creating-a-long-running-workflow-service/add-variables-sequential-service-activity.gif "değişkenleri için sıralı hizmeti etkinliği ekleyin.")

6. Sürükle ve bırak bir **ReceiveAndSendReply** etkinlik şablona **sıralı hizmeti** etkinlik. Bu etkinlikler kümesi, bir istemciden bir ileti alırsınız ve bir yanıtı geri gönderir.

    1. Seçin **alma** etkinliği ve özellikleri aşağıdaki çizimde vurgulanan kümesi.

         ![Etkinlik özellikleri alma](./media/creating-a-long-running-workflow-service/set-receive-activity-properties.png "Receive etkinlik özelliklerini ayarlayın.")

         DisplayName özelliği için Receive etkinlik Tasarımcısı'nda görüntülenen adını ayarlar. ServiceContractName ve OperationName özellikleri hizmet sözleşmesini ve Al etkinliği tarafından uygulanan işlem adını belirtin. Sözleşme iş akışı hizmetleri nasıl kullanıldığı hakkında daha fazla bilgi için bkz. [iş akışında sözleşmeleri kullanma](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).

    2. Tıklayın **tanımlayın...**  bağlantısını **ReceiveStartOrder** etkinlik ve aşağıdaki çizimde gösterilen özellikleri ayarlayın.  Dikkat **parametreleri** radyo düğmesi seçilirse, adlı bir parametre `p_customerName` bağlı `customerName` değişkeni. Bu yapılandırır **alma** bazı veri almak ve yerel değişkenlere, veri bağlama için etkinlik.

         ![Receive etkinlik tarafından alınan veri ayarlama](./media/creating-a-long-running-workflow-service/set-properties-for-receive-content.png "Al etkinliği tarafından alınan veriler için özelliklerini ayarlayın.")

    3. Seçin **SendReplyToReceive** etkinliği ve aşağıdaki çizimde gösterilen vurgulanan özelliğini ayarlayın.

         ![SendReply etkinlik özelliklerini ayarlama](./media/creating-a-long-running-workflow-service/set-properties-for-reply-activities.png "SetReplyProperties")

    4. Tıklayın **tanımlayın...**  bağlantısını **SendReplyToStartOrder** etkinlik ve aşağıdaki çizimde gösterilen özellikleri ayarlayın. Dikkat **parametreleri** radyo düğmesi seçili; adlı bir parametre `p_orderId` bağlı `orderId` değişkeni. Bu ayar, SendReplyToStartOrder etkinlik dize türünde bir değer çağırana döndürmesi gerektiğini belirtir.

         ![İçerik verileri SendReply etkinliği yapılandırma](./media/creating-a-long-running-workflow-service/setreplycontent-for-sendreplytostartorder-activity.png "SetReplyToStartOrder etkinlik ayarını yapılandırın.")

    5. Bir Ata etkinlik arasında sürükleyip **alma** ve **SendReply** etkinlikleri ve aşağıdaki çizimde gösterildiği gibi özellikleri ayarlayın:

         ![Ata etkinlik ekleme](./media/creating-a-long-running-workflow-service/add-an-assign-activity.png "Ata etkinliği ekleyin.")

         Bu, yeni bir sipariş kimliği oluşturur ve değer OrderID değişkene yerleştirir.

    6. Seçin **ReplyToStartOrder** etkinlik. Özellikler penceresinde için üç nokta düğmesine **Correlationınitializer**. Seçin **Başlatıcı Ekle** bağlantı, girin `orderIdHandle` Başlatıcı metin kutusunda, bağıntı türü için sorgu bağıntı başlatıcı seçin ve XPATH sorgularını açılan kutunun altında p_orderId seçin. Bu ayarlar aşağıdaki çizimde gösterilmektedir. **Tamam**'ı tıklatın.  Bu, istemci ile bu iş akışı hizmeti örneği arasında bir bağıntı başlatır. Kimliği bu sırayı içeren bir ileti alındığında, bu iş akışı hizmeti örneğine yönlendirilir.

         ![Bağıntı başlatıcı ekleme](./media/creating-a-long-running-workflow-service/add-correlationinitializers.png "bağıntı başlatıcısını ekleyin.")

7. Sürükle ve bırak başka **ReceiveAndSendReply** etkinlik iş akışı sonuna (dışında **dizisi** ilk içeren **alma** ve  **SendReply** etkinlikler). İstemci tarafından gönderilen ikinci bir ileti alırsınız ve yanıtlayabilirsiniz.

    1. Seçin **dizisi** yeni eklenen içeren **alma** ve **SendReply** etkinlikleri ve tıklatın **değişkenleri** düğmesi. Aşağıdaki çizimde vurgulanan değişkeni ekleyin:

         ![Yeni değişkenleri ekleme](./media/creating-a-long-running-workflow-service/add-the-itemid-variable.png "ItemId değişkenini ekleyin.")
         
         Ayrıca `orderResult` olarak **dize** içinde `Sequence` kapsam.

    2. Seçin **alma** etkinlik ve aşağıdaki çizimde gösterilen özellikleri ayarlayın:

         ![Receive etkinlik özelliklerini ayarlama](./media/creating-a-long-running-workflow-service/set-receive-activities-properties.png "alma etkinlikleri özelliklerini ayarlayın.")
         
         > [!NOTE]
         >  Değiştirmeyi unutmayın **ServiceContractName** alanına `../IAddItem`.

    3. Tıklayın **tanımlayın...**  bağlantısını **ReceiveAddItem** etkinlik ve aşağıdaki çizimde gösterilen parametreler Ekle: Bu alma etkinliğini sipariş kimliği ve sıralanan öğenin kimliği iki parametre kabul edecek şekilde yapılandırır.

         ![İkinci alan için parametrelerini belirtme](./media/creating-a-long-running-workflow-service/add-receive-two-parameters.png "iki parametre almak için Al etkinliği yapılandırın.")

    4. Tıklayın **CorrelateOn** üç nokta düğmesine tıklayın ve girin `orderIdHandle`. Altında **XPath sorguları**, aşağı açılan oku tıklatın ve seçin `p_orderId`. Bu ikinci bağıntı yapılandırır etkinlik alırsınız. Bağıntı hakkında daha fazla bilgi için bkz. [bağıntı](../../../../docs/framework/wcf/feature-details/correlation.md).

         ![CorrelatesOn özelliğini ayarlayarak](./media/creating-a-long-running-workflow-service/correlateson-setting.png "CorrelatesOn özelliğini ayarlayın.")

    5. Sürükle ve bırak bir **varsa** etkinlik hemen sonra **ReceiveAddItem** etkinlik. Bu etkinlik bir IF gibi davranan deyimi.

        1. Ayarlama **koşul** özelliği `itemId=="Zune HD" (itemId="Zune HD" for Visual Basic)`

        2. Sürükle ve bırak bir **atama** etkinlik için **ardından** bölümü ve başka bir **Else** bölümü özelliklerini ayarlayın **atama** Aşağıdaki çizimde gösterildiği gibi etkinlikler.

             ![Hizmet çağrısı sonucunu atama](./media/creating-a-long-running-workflow-service/assign-result-of-service-call.png "hizmet çağrısı sonucunu atayın.")

             Koşul ise `true` **ardından** bölüm yürütülür. Koşul ise `false` **Else** bölüm yürütülür.

        3. Seçin **SendReplyToReceive** etkinliği ve kümesi **DisplayName** aşağıdaki çizimde gösterilen özelliği.

             ![SendReply etkinlik özelliklerini ayarlama](./media/creating-a-long-running-workflow-service/send-reply-activity-property.png "SendReply etkinlik özelliğini ayarlayın.")

        4. Tıklayın **tanımlayın...**  bağlantısını **SetReplyToAddItem** etkinlik ve aşağıdaki çizimde gösterildiği gibi yapılandırın. Bu yapılandırır **SendReplyToAddItem** değeri döndürmek için etkinliği `orderResult` değişkeni.

             ![Veri bağlama SendReply etkinliğinin ayarlama](./media/creating-a-long-running-workflow-service/set-property-for-sendreplytoadditem.gif "SendReplyToAddItem etkinliğinin özelliğini ayarlayın.")

8. Web.config dosyasını açın ve aşağıdaki öğeleri ekleyin \<davranışı > bölümü iş akışı kalıcılığı etkinleştir.

    ```xml
    <sqlWorkflowInstanceStore connectionString="Data Source=your-machine\SQLExpress;Initial Catalog=SQLPersistenceStore;Integrated Security=True;Asynchronous Processing=True" instanceEncodingOption="None" instanceCompletionAction="DeleteAll" instanceLockedExceptionAction="BasicRetry" hostLockRenewalPeriod="00:00:30" runnableInstancesDetectionPeriod="00:00:02" />
              <workflowIdle timeToUnload="0"/>
    ```

    > [!WARNING]
    >  Konak ve SQL server örneği adı önceki kod parçacığında değiştirdiğinizden emin olun.

9. Çözümü oluşturun.

### <a name="to-create-a-client-application-to-call-the-workflow-service"></a>İş akışı hizmeti çağırmak için bir istemci uygulaması oluşturmak için

1. Adlı yeni bir konsol uygulama projesi Ekle `OrderClient` çözüm.

2. Aşağıdaki derlemelere başvurular ekleyin `OrderClient` proje

    1. System.ServiceModel.dll

    2. System.ServiceModel.Activities.dll

3. Bir iş akışı hizmetine hizmet başvurusu eklemek ve belirtmek `OrderService` ad alanı olarak.

4. İçinde `Main()` istemci projesinin bir yöntem aşağıdaki kodu ekleyin:

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

5. Çözümü derleyin ve çalıştırın `OrderClient` uygulama. İstemci, aşağıdaki metni görüntülenir:

    ```Output
    Sending start messageWorkflow service is idle...Press [ENTER] to send an add item message to reactivate the workflow service...
    ```

6. İş akışı hizmeti kalıcı olduğunu doğrulamak için SQL Server Management Studio adresine giderek başlatın **Başlat** menüsünde seçme **tüm programlar**, **Microsoft SQL Server 2008**, **SQL Server Management Studio'yu**.

    1. Sol taraftaki bölmede genişletin, **veritabanları**, **SQLPersistenceStore**, **görünümleri** ve sağ tıklatma **System.Activities.DurableInstancing.Instances**  seçip **ilk 1000 satırı Seç**. İçinde **sonuçları** bölmesinde doğrulayın listelenen en az bir örneğe bakın. Çalıştırılırken bir özel durum oluştuysa diğer örnekleri önceki çalıştırmalardan olabilir. Sağ tıklayarak var olan satır silebilirsiniz **System.Activities.DurableInstancing.Instances** seçerek **Düzenle üst 200 satırı**, ENTER tuşuna basın **yürütme** düğmesi Sonuçlar bölmesinde tüm satırları ve seçerek **Sil**.  Veritabanında görüntülenen örnek doğrulamak için örneği oluşturulmuş uygulamanızı, örnekler görünümü istemci çalıştırılmadan önce boş olduğundan emin olun. İstemci (ilk 1000 satırı Seç) sorgu olan çalışan yeniden çalıştırın ve doğrulayın, sonra yeni bir örneği eklendi.

7. İş akışı hizmeti için add öğesi ileti göndermek için enter tuşuna basın. İstemci, aşağıdaki metni görüntülenir:

    ```Output
    Sending add item messageService returned: Item added to orderPress any key to continue . . .
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)
