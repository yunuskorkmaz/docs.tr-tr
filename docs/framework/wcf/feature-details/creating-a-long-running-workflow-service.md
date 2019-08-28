---
title: Uzun Süre Çalışan Bir İş Akışı Hizmeti Oluşturma
ms.date: 03/30/2017
ms.assetid: 4c39bd04-5b8a-4562-a343-2c63c2821345
ms.openlocfilehash: e6206babdb728b6ce38c94441f775e1fdffe7d79
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040410"
---
# <a name="creating-a-long-running-workflow-service"></a>Uzun Süre Çalışan Bir İş Akışı Hizmeti Oluşturma

Bu konuda, uzun süre çalışan bir iş akışı hizmetinin nasıl oluşturulacağı açıklanmaktadır. Uzun süre çalışan iş akışı hizmetleri uzun süreler için çalıştırılabilir. Bazı bir noktada iş akışı, bazı ek bilgiler için bekleyen boşta kalabilir. Bu gerçekleştiğinde, iş akışı bir SQL veritabanında kalıcı hale getirilir ve bellekten kaldırılır. Ek bilgiler kullanılabilir hale geldiğinde, iş akışı örneği belleğe geri yüklenir ve yürütülmeye devam eder.  Bu senaryoda, çok basitleştirilmiş bir sıralama sistemi uygulıyız.  İstemci sıraya başlamak için iş akışı hizmetine bir başlangıç iletisi gönderir. İstemciye bir sıra KIMLIĞI döndürür. Bu noktada, iş akışı hizmeti istemciden başka bir ileti bekliyor ve boşta durumuna geçiyor ve bir SQL Server veritabanına kalıcı hale getirildi.  İstemci bir öğeyi sipariş etmek için bir sonraki iletiyi gönderdiğinde, iş akışı hizmeti belleğe geri yüklenir ve siparişi işlemeyi sonlandırır. Kod örneğinde, öğenin sıraya eklendiğini belirten bir dize döndürür. Kod örneği, teknolojinin gerçek bir dünya uygulaması değil, uzun süre çalışan iş akışı hizmetlerini gösteren basit bir örnektir. Bu konu başlığı altında, Visual Studio 2012 projeleri ve çözümleri oluşturmayı bildiğiniz varsayılmaktadır.

## <a name="prerequisites"></a>Önkoşullar

Bu yönergeyi kullanabilmeniz için aşağıdaki yazılımların yüklü olması gerekir:

1. Microsoft SQL Server 2008

2. Visual Studio 2012

3. MICROSOFT[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]

4. WCF ve Visual Studio 2012 hakkında bilgi sahibisiniz ve proje/çözüm oluşturma hakkında bilgi sahibi olabilirsiniz.

### <a name="to-setup-the-sql-database"></a>SQL veritabanını ayarlamak için

1. İş akışı hizmeti örneklerinin kalıcı olabilmesi için Microsoft SQL Server yüklü olmalıdır ve kalıcı iş akışı örneklerini depolamak için bir veritabanı yapılandırmanız gerekir. **Başlat** düğmesine tıklayarak, **tüm programlar**, **Microsoft SQL Server 2008**ve **MICROSOFT sql Management Studio**' nı seçerek Microsoft SQL Management Studio 'yi çalıştırın.

2. SQL Server örneğine oturum açmak için **Bağlan** düğmesine tıklayın

3. Ağaç görünümünde **veritabanları** ' na sağ tıklayın ve **Yeni veritabanı** ' nı seçin. adlı `SQLPersistenceStore`yeni bir veritabanı oluşturun.

4. Gerekli veritabanı şemalarını ayarlamak için Sqlpersistenınstancestore veritabanındaki C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en dizininde bulunan SqlWorkflowInstanceStoreSchema. SQL komut dosyasını çalıştırın.

5. Gerekli veritabanı mantığını ayarlamak için Sqlpersistenınstancestore veritabanındaki C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en dizininde bulunan Sqlworkflowcestorelogic. SQL komut dosyasını çalıştırın.

### <a name="to-create-the-web-hosted-workflow-service"></a>Web 'de barındırılan Iş akışı hizmeti oluşturmak için

1. Boş bir Visual Studio 2012 çözümü oluşturun, adlandırın `OrderProcessing`.

2. Çözüme adlı `OrderService` yeni bir WCF iş akışı hizmeti uygulama projesi ekleyin.

3. Proje Özellikleri iletişim kutusunda **Web** sekmesini seçin.

    1. **Başlatma eylemi** altında **belirli sayfa** ' yı seçin `Service1.xamlx`ve belirtin.

        ![Iş akışı hizmeti projesi Web özellikleri](./media/creating-a-long-running-workflow-service/start-action-specific-page-option.png "Web 'de barındırılan iş akışı hizmeti 'Ne özgü sayfa seçeneğini oluşturma")

    2. **Sunucular** altında **yerel IIS Web sunucusu kullan**' ı seçin.

        ![Yerel Web sunucusu ayarları](./media/creating-a-long-running-workflow-service/use-local-web-server.png "Web 'de barındırılan iş akışı hizmetini oluşturma-Yerel IIS Web sunucusu seçeneğini kullanın")

        > [!WARNING]
        > Bu ayarı yapmak için, Visual Studio 2012 ' i yönetici modunda çalıştırmalısınız.

        Bu iki adım, iş akışı hizmeti projesini IIS tarafından barındırılacak şekilde yapılandırır.

4. Henüz `Service1.xamlx` açık değilse açın ve var olan **ReceiveRequest** ve **SendResponse** etkinliklerini silin.

5. **Sıralı hizmet** etkinliğini seçin ve **değişkenler** bağlantısına tıklayın ve aşağıdaki çizimde gösterilen değişkenleri ekleyin. Bunu yapmak, daha sonra iş akışı hizmetinde kullanılacak bazı değişkenleri ekler.

    > [!NOTE]
    > CorrelationHandle, değişken türü açılan kutusunda değilse, açılan listeden **türler Için araştır** ' ı seçin. **Tür adı** kutusuna CorrelationHandle yazın, ListBox ' dan CorrelationHandle ' ı seçin ve **Tamam**' a tıklayın.

    ![Değişken Ekle](./media/creating-a-long-running-workflow-service/add-variables-sequential-service-activity.gif "Sıralı hizmet etkinliğine değişken ekleyin.")

6. Bir **ReceiveAndSendReply** etkinlik şablonunu sürükleyip **sıralı hizmet** etkinliğine bırakın. Bu etkinlik kümesi bir istemciden bir ileti alır ve tekrar yanıt gönderir.

    1. **Alma** etkinliğini seçin ve aşağıdaki çizimde vurgulanan özellikleri ayarlayın.

        ![Alma etkinliği özelliklerini ayarla](./media/creating-a-long-running-workflow-service/set-receive-activity-properties.png "Alma etkinliği özelliklerini ayarlayın.")

        DisplayName özelliği, tasarımcıda alma etkinliği için görünen adı ayarlar. ServiceContractName ve OperationName özellikleri, alma etkinliği tarafından uygulanan hizmet sözleşmesinin ve işlemin adını belirtir. Iş akışı hizmetlerinde sözleşmelerin nasıl kullanıldığı hakkında daha fazla bilgi için bkz. [Iş akışında sözleşmeleri kullanma](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).

    2. **ReceiveStartOrder** etkinliğinde **define...** bağlantısına tıklayın ve aşağıdaki çizimde gösterilen özellikleri ayarlayın.  **Parametreler** radyo düğmesinin seçili olduğuna, adlı `p_customerName` parametrenin `customerName` değişkenine bağlandığını unutmayın. Bu, **alma** etkinliğini bazı verileri alacak şekilde yapılandırır ve bu verileri yerel değişkenlere bağlar.

        ![Alma etkinliği tarafından alınan verileri ayarlama](./media/creating-a-long-running-workflow-service/set-properties-for-receive-content.png "Alma etkinliği tarafından alınan veriler için özellikleri ayarlayın.")

    3. **SendReplyToReceive** etkinliğini seçin ve aşağıdaki çizimde gösterilen vurgulanan özelliği ayarlayın.

        ![SendReply etkinliğinin özelliklerini ayarlama](./media/creating-a-long-running-workflow-service/set-properties-for-reply-activities.png "Setreplyproperties")

    4. **SendReplyToStartOrder** etkinliğinde **define...** bağlantısına tıklayın ve aşağıdaki çizimde gösterilen özellikleri ayarlayın. **Parametreler** radyo düğmesinin seçili olduğuna dikkat edin; adlı `p_orderId` bir parametre `orderId` değişkenine bağlanır. Bu ayar, SendReplyToStartOrder etkinliğinin çağırana String türünde bir değer döndürmesini belirtir.

        ![SendReply etkinlik içerik verilerini yapılandırma](./media/creating-a-long-running-workflow-service/setreplycontent-for-sendreplytostartorder-activity.png "SetReplyToStartOrder etkinliğinin ayarını yapılandırın.")

    5. **Receive** ve **SendReply** etkinlikleri arasında bir atama etkinliği sürükleyip bırakın ve aşağıdaki çizimde gösterildiği gibi özellikleri ayarlayın:

        ![Atama etkinliği ekleme](./media/creating-a-long-running-workflow-service/add-an-assign-activity.png "Atama etkinliği ekleyin.")

        Bu, yeni bir sipariş KIMLIĞI oluşturur ve değeri OrderID değişkenine koyar.

    6. **ReplyToStartOrder** etkinliğini seçin. Özellikler penceresinde, **Correlationbaşlatıcıları**için üç nokta düğmesine tıklayın. **Başlatıcı Ekle** bağlantısını seçin, başlatıcı metin `orderIdHandle` kutusunda girin, bağıntı türü için sorgu bağıntı Başlatıcısı ' nı seçin ve XPath sorguları açılan kutusu altında p_orderId ' yi seçin. Bu ayarlar aşağıdaki çizimde gösterilmiştir. **Tamam**'ı tıklatın.  Bu, istemci ile iş akışı hizmetinin bu örneği arasında bir bağıntı başlatır. Bu sipariş KIMLIĞINI içeren bir ileti alındığında, iş akışı hizmetinin bu örneğine yönlendirilir.

        ![Bağıntı başlatıcısı ekleme](./media/creating-a-long-running-workflow-service/add-correlationinitializers.png "Bağıntı başlatıcısı ekleyin.")

7. Başka bir **ReceiveAndSendReply** etkinliğini, iş akışının sonuna sürükleyin ve bırakın (ilk **Receive** ve **SendReply** etkinliklerini içeren **sıra** dışında). Bu, istemci tarafından gönderilen ikinci iletiyi alır ve buna yanıt verir.

    1. Yeni eklenen **Receive** ve **SendReply** etkinliklerini Içeren **diziyi** seçin ve **değişkenler** düğmesine tıklayın. Aşağıdaki çizimde vurgulanan değişkeni ekleyin:

        ![Yeni değişkenler ekleme](./media/creating-a-long-running-workflow-service/add-the-itemid-variable.png "ItemId değişkenini ekleyin.")

        Ayrıca, `orderResult` kapsama`Sequence` **dize** olarak ekleyin.

    2. **Alma** etkinliğini seçin ve aşağıdaki çizimde gösterilen özellikleri ayarlayın:

        ![Alma etkinliği özelliklerini ayarla](./media/creating-a-long-running-workflow-service/set-receive-activities-properties.png "Alma etkinlikleri özelliklerini ayarlayın.")

        > [!NOTE]
        > **ServiceContractName** alanını ile `../IAddItem`değiştirmeyi unutmayın.

    3. **ReceiveAddItem** etkinliğinde **define...** bağlantısına tıklayın ve aşağıdaki çizimde gösterilen parametreleri ekleyin: Bu, Receive etkinliğini iki parametreyi kabul edecek şekılde yapılandırır, sipariş KIMLIĞI ve sıralanan öğenin kimliği.

        ![İkinci alım için parametreleri belirtme](./media/creating-a-long-running-workflow-service/add-receive-two-parameters.png "Alma etkinliğini iki parametre alacak şekilde yapılandırın.")

    4. **CorrelateOn** üç nokta düğmesine tıklayın ve girin `orderIdHandle`. **XPath sorguları**altında aşağı açılan oka tıklayın ve öğesini seçin `p_orderId`. Bu, ikinci alma etkinliğinde bağıntıyı yapılandırır. Bağıntı hakkında daha fazla bilgi için bkz. [bağıntı](../../../../docs/framework/wcf/feature-details/correlation.md).

        ![CorrelatesOn özelliğini ayarlama](./media/creating-a-long-running-workflow-service/correlateson-setting.png "CorrelatesOn özelliğini ayarlayın.")

    5. Bir **IF** etkinliğini **receiveaddidıtem** etkinliğinden hemen sonra sürükleyin ve bırakın. Bu etkinlik tıpkı bir if bildirisi gibi davranır.

        1. **Koşul** özelliğini olarak ayarlayın`itemId=="Zune HD" (itemId="Zune HD" for Visual Basic)`

        2. ' A bir **atama** etkinliğini sürükleyip **daha sonra** , aşağıdaki çizimde gösterildiği gibi, başka bir şekilde **atama** etkinliklerinin özelliklerini ayarla bölümüne bırakın.

            ![Hizmet çağrısının sonucunu atama](./media/creating-a-long-running-workflow-service/assign-result-of-service-call.png "Hizmet çağrısının sonucunu atayın.")

            Koşul ise `true` , Bölüm yürütülür . Koşul `false` **Else** bölümü yürütülür.

        3. **SendReplyToReceive** etkinliğini seçin ve aşağıdaki çizimde gösterilen **DisplayName** özelliğini ayarlayın.

            ![SendReply etkinlik özelliklerini ayarlama](./media/creating-a-long-running-workflow-service/send-reply-activity-property.png "SendReply etkinlik özelliğini ayarlayın.")

        4. **Setreplytoaddidıtem** etkinliğinde **define...** bağlantısına tıklayın ve aşağıdaki çizimde gösterildiği gibi yapılandırın. Bu, `orderResult` değişkende değeri döndürecek **SendReplyToAddItem** etkinliğini yapılandırır.

            ![SendReply etkinliği için veri bağlamayı ayarlama](./media/creating-a-long-running-workflow-service/set-property-for-sendreplytoadditem.gif "Sendreplytoaddidıtem etkinliğinin özelliğini ayarlayın.")

8. Web. config dosyasını açın ve iş akışı kalıcılığını etkinleştirmek için \<davranış > bölümüne aşağıdaki öğeleri ekleyin.

    ```xml
    <sqlWorkflowInstanceStore connectionString="Data Source=your-machine\SQLExpress;Initial Catalog=SQLPersistenceStore;Integrated Security=True;Asynchronous Processing=True" instanceEncodingOption="None" instanceCompletionAction="DeleteAll" instanceLockedExceptionAction="BasicRetry" hostLockRenewalPeriod="00:00:30" runnableInstancesDetectionPeriod="00:00:02" />
              <workflowIdle timeToUnload="0"/>
    ```

    > [!WARNING]
    > Önceki kod parçacığında ana bilgisayarınızı ve SQL Server örnek adınızı değiştirdiğinizden emin olun.

9. Çözümü oluşturun.

### <a name="to-create-a-client-application-to-call-the-workflow-service"></a>Iş akışı hizmetini çağırmak üzere bir Istemci uygulaması oluşturmak için

1. Çözüme adlı `OrderClient` yeni bir konsol uygulaması projesi ekleyin.

2. `OrderClient` Projeye aşağıdaki derlemelere başvurular ekleyin

    1. System.ServiceModel.dll

    2. System. ServiceModel. Activities. dll

3. İş akışı hizmetine bir hizmet başvurusu ekleyin ve ad alanı `OrderService` olarak belirtin.

4. İstemci projesi `Main()` yönteminde aşağıdaki kodu ekleyin:

    ```csharp
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

5. Çözümü derleyin ve `OrderClient` uygulamayı çalıştırın. İstemci aşağıdaki metni görüntüler:

    ```Output
    Sending start messageWorkflow service is idle...Press [ENTER] to send an add item message to reactivate the workflow service...
    ```

6. İş akışı hizmetinin kalıcı olduğunu doğrulamak için, **Başlat** menüsüne gidip **tüm programlar**' a, **Microsoft SQL Server 2008** **SQL Server Management Studio**' i seçerek SQL Server Management Studio başlatın.

    1. Sol taraftaki bölmede, **veritabanları**, **sqlpersistenınstancestore**, **Görünümler** ' i genişletin ve **System. Activities. durableörnek oluşturma. örnekler** ' i seçin ve **en üstteki 1000 satırları Seç**' i seçin. **Sonuçlar** bölmesinde, listelenen en az bir örnek olduğunu doğrulayın. Çalıştırılırken bir özel durum oluşursa, önceki çalıştırmaların başka örnekleri olabilir. **System. Activities. Durableörnek oluşturma. Instances** ' a sağ tıklayıp, **en üstteki 200 satırları Düzenle**' yi seçerek **yürütme** düğmesine basarak, sonuçlar bölmesinde tüm satırları seçip **Sil**' i seçerek mevcut satırları silebilirsiniz.  Veritabanında görüntülenmekte olan örneği uygulamanızın oluşturduğu örnek olduğunu doğrulamak için, istemci çalıştırılmadan önce örnekler görünümünün boş olduğunu doğrulayın. İstemci çalışmaya başladıktan sonra sorguyu yeniden çalıştırın (en üstteki 1000 satırları seçin) ve yeni bir örnek eklendiğini doğrulayın.

7. Öğe Ekle iletisini iş akışı hizmetine göndermek için ENTER tuşuna basın. İstemci aşağıdaki metni görüntüler:

    ```Output
    Sending add item messageService returned: Item added to orderPress any key to continue . . .
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)
