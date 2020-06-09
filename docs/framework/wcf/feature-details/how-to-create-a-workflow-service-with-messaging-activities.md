---
title: 'Nasıl yapılır: Mesajlaşma Etkinlikleriyle İş Akışı Hizmeti Oluşturma'
ms.date: 03/30/2017
ms.assetid: 53d094e2-6901-4aa1-88b8-024b27ccf78b
ms.openlocfilehash: b4991fc9f8a6c45cae3943f1506247c42ed2b30b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597130"
---
# <a name="how-to-create-a-workflow-service-with-messaging-activities"></a>Nasıl yapılır: Mesajlaşma Etkinlikleriyle İş Akışı Hizmeti Oluşturma
Bu konuda, mesajlaşma etkinlikleri kullanılarak basit bir iş akışı hizmetinin nasıl oluşturulacağı açıklanmaktadır. Bu konu, hizmetin yalnızca mesajlaşma etkinliklerinden oluşan bir iş akışı hizmeti oluşturma mekanizması üzerinde odaklanır. Gerçek dünyada bir hizmette, iş akışı birçok farklı etkinlik içerir. Hizmet, bir dizeyi alıp çağrıyı yapana döndüren Echo adlı bir işlem uygular. Bu konu, iki konu serisinin ilk ilkisidir. Sonraki konuda [nasıl yapılır: bir Iş akışı uygulamasından bir hizmete erişme](how-to-access-a-service-from-a-workflow-application.md) , bu konuda oluşturulan hizmeti çağırabileceği bir iş akışı uygulamasının nasıl oluşturulduğunu açıklar.  
  
### <a name="to-create-a-workflow-service-project"></a>Bir iş akışı hizmeti projesi oluşturmak için  
  
1. Visual Studio 2012 ' i başlatın.  
  
2. **Yeni proje Iletişim kutusunu**göstermek için **Dosya** menüsüne tıklayın, **Yeni**' yi ve ardından **Proje** ' yi seçin. Proje türleri listesinden yüklü şablonlar ve **WCF Iş akışı hizmeti uygulaması** listesinden **iş akışı** ' nı seçin. Projeyi adlandırın `MyWFService` ve aşağıdaki çizimde gösterildiği gibi varsayılan konumu kullanın.  
  
     **Yeni proje Iletişim kutusunu**kapatmak için **Tamam** düğmesine tıklayın.  
  
3. Proje oluşturulduğunda, Service1. xamlx dosyası, aşağıdaki çizimde gösterildiği gibi tasarımcıda açılır.  
  
     ![Ekran görüntüsü tasarımcıda Open Service1. xamlx dosyasını gösterir.](./media/how-to-create-a-workflow-service-with-messaging-activities/default-workflow-service.jpg)  
  
     **Sıralı hizmet** etiketli etkinliğe sağ tıklayın ve **Sil**' i seçin.  
  
### <a name="to-implement-the-workflow-service"></a>İş akışı hizmetini uygulamak için  
  
1. Araç kutusunu göstermek için ekranın sol tarafındaki **araç kutusu** sekmesini seçin ve pencereyi açık tutmak için raptiye ' ye tıklayın. Aşağıdaki çizimde gösterildiği gibi, ileti etkinliklerini ve mesajlaşma etkinliği şablonlarını göstermek için araç kutusu ' nın **mesajlaşma** bölümünü genişletin.  
  
     ![Iletişim kutusu ile genişletilmiş Iletişim kutusu bölümü gösteren ekran görüntüsü.](./media/how-to-create-a-workflow-service-with-messaging-activities/toolbox-messaging-section.jpg)  
  
2. Bir **ReceiveAndSendReply** şablonunu sürükleyip iş akışı tasarımcısına bırakın. Bu <xref:System.Activities.Statements.Sequence> **Receive** <xref:System.ServiceModel.Activities.SendReply> , aşağıdaki çizimde gösterildiği gibi, alma etkinliği ve sonrasında etkinlik gelen bir etkinlik oluşturur.  
  
     ![ReceiveAndSendReply şablonunu gösteren ekran görüntüsü.](./media/how-to-create-a-workflow-service-with-messaging-activities/receiveandsendreply-template.jpg)  
  
     <xref:System.ServiceModel.Activities.SendReply>Etkinliğin <xref:System.ServiceModel.Activities.SendReply.Request%2A> özelliğinin olarak ayarlanmış olduğuna `Receive` , etkinliğin <xref:System.ServiceModel.Activities.Receive> yanıtlanıyor olduğu etkinliğin adına <xref:System.ServiceModel.Activities.SendReply> dikkat edin.  
  
3. <xref:System.ServiceModel.Activities.Receive>Etkinlik türü ' nde `Echo` , **OperationName**etiketli metin kutusuna yazın. Bu, hizmetin uyguladığı işlemin adını tanımlar.  
  
     ![İşlem adının nerede belirtildiğinin gösterildiği ekran görüntüsü.](./media/how-to-create-a-workflow-service-with-messaging-activities/define-operation-name.jpg)  
  
4. <xref:System.ServiceModel.Activities.Receive>Etkinlik seçiliyken, zaten açık değilse **Görünüm** menüsüne tıklayıp **Özellikler penceresi**' ni seçerek Özellikler penceresini açın. **Özellikler penceresinde** , **CanCreateInstance** ' ı görene kadar aşağı kaydırın ve aşağıdaki çizimde gösterildiği gibi onay kutusuna tıklayın. Bu ayar, iş akışı hizmet ana bilgisayarının bir ileti alındığında hizmetin yeni bir örneğini (gerekirse) oluşturmasını sağlar.  
  
     ![CanCreateInstance özelliğini gösteren ekran görüntüsü.](./media/how-to-create-a-workflow-service-with-messaging-activities/cancreateinstance-property.jpg)  
  
5. Etkinliği seçin <xref:System.Activities.Statements.Sequence> ve tasarımcının sol alt köşesindeki **değişkenler** düğmesine tıklayın. Bu, değişkenler düzenleyicisini görüntüler. İşleme gönderilen dizeyi depolayacak bir değişken eklemek için **değişken Oluştur** bağlantısına tıklayın. Değişkenini adlandırın `msg` ve aşağıdaki çizimde gösterildiği gibi **değişken** türünü String olarak ayarlayın.  
  
     ![Nasıl değişken ekleneceğini gösteren ekran görüntüsü.](./media/how-to-create-a-workflow-service-with-messaging-activities/add-variable-msg-string.jpg)  
  
     Değişkenler düzenleyicisini kapatmak için **değişkenler** düğmesine tekrar tıklayın.  
  
6. **Tanımla** ' ya tıklayın. **Content** <xref:System.ServiceModel.Activities.Receive> **İçerik tanımı** Iletişim kutusunu göstermek için etkinliğin içerik metin kutusunda bağlantısını yapın. **Parametreler** radyo düğmesini seçin, **yeni parametre Ekle** bağlantısına tıklayın, `inMsg` **ad** metin kutusunu yazın, **tür** açılan liste kutusunda **dize** ' yi seçin ve `msg` Aşağıdaki çizimde gösterildiği gibi **ata** metin kutusuna yazın.  
  
     ![Parametre içeriği eklemeyi gösteren ekran görüntüsü.](./media/how-to-create-a-workflow-service-with-messaging-activities/adding-parameters-content.jpg)  
  
     Bu, alma etkinliğinin dize parametresini alacağını ve verilerin değişkene bağlandığını belirtir `msg` . **Içerik tanımı** iletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.  
  
7. Içerik tanımı iletişim kutusunu göstermek için etkinliğin **içerik** kutusunda **tanımla...** bağlantısına tıklayın <xref:System.ServiceModel.Activities.SendReply> . **Content Definition** **Parametreler** radyo düğmesini seçin, **yeni parametre Ekle** bağlantısına tıklayın, `outMsg` **ad** metin kutusunu yazın, **tür** açılan liste kutusunda **dize** ' yi seçin ve `msg` **değer** metin kutusunda aşağıdaki çizimde gösterildiği gibi yazın.  
  
     ![OutMsg parametresinin nasıl ekleneceğini gösteren ekran görüntüsü.](./media/how-to-create-a-workflow-service-with-messaging-activities/outmsg-parameters-content.jpg)  
  
     Bu, <xref:System.ServiceModel.Activities.SendReply> etkinliğin bir ileti veya ileti sözleşmesi türü göndereceğini ve verilerin değişkene bağlandığını belirtir `msg` . Bu bir etkinlik olduğu <xref:System.ServiceModel.Activities.SendReply> için bu, içindeki verilerin, `msg` etkinliğin istemciye geri gönderdiği iletiyi doldurmak için kullanıldığı anlamına gelir. **Içerik tanımı** iletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.  
  
8. **Build** menüsüne tıklayıp Build **Solution**' ı seçerek çözümü kaydedin ve oluşturun.  
  
## <a name="configure-the-workflow-service-project"></a>Iş akışı hizmeti projesini yapılandırma  
 İş akışı hizmeti tamamlanmıştır. Bu bölümde, barındırmak ve çalıştırmak kolay hale getirmek için iş akışı hizmeti çözümünün nasıl yapılandırılacağı açıklanmaktadır. Bu çözüm, hizmeti barındırmak için ASP.NET geliştirme sunucusunu kullanır.  
  
#### <a name="to-set-project-start-up-options"></a>Proje başlangıç seçeneklerini ayarlamak için  
  
1. **Çözüm Gezgini**, **MyWFService** ' e sağ tıklayın ve **Özellikler** ' i seçerek **Proje özellikleri** iletişim kutusunu görüntüleyin.  
  
2. **Web** sekmesini seçin ve **Başlangıç eylemi** altında **belirli sayfa** ' yı seçin ve `Service1.xamlx` Aşağıdaki çizimde gösterildiği gibi metin kutusuna yazın.  
  
     ![Proje Özellikleri iletişim kutusunu gösteren ekran görüntüsü.](./media/how-to-create-a-workflow-service-with-messaging-activities/project-properties-dialog.jpg)  
  
     Bu, ASP.NET geliştirme sunucusunda Service1. xamlx içinde tanımlanan hizmeti barındırır.  
  
3. Hizmeti başlatmak için CTRL + F5 tuşlarına basın. Aşağıdaki görüntüde gösterildiği gibi, ASP.NET geliştirme sunucusu simgesi masaüstünün sağ alt tarafında görüntülenir.  
  
     ![ASP.NET Developer Server simgesini gösteren ekran görüntüsü.](./media/how-to-create-a-workflow-service-with-messaging-activities/asp-net-dev-server-icon.jpg)  
  
     Ayrıca, Internet Explorer hizmet için WCF hizmeti yardım sayfasını görüntüler.  
  
     ![WCF hizmeti yardım sayfasını gösteren ekran görüntüsü.](./media/how-to-create-a-workflow-service-with-messaging-activities/wcf-service-help-page.jpg)  
  
4. Bu hizmeti çağıran bir iş akışı istemcisi oluşturmak için [nasıl yapılır: bir Iş akışı uygulamasından hizmete erişme](how-to-access-a-service-from-a-workflow-application.md) konusuna geçin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Hizmetleri](workflow-services.md)
- [İş Akışı Hizmetlerini Barındırmaya Genel Bakış](hosting-workflow-services-overview.md)
- [Mesajlaşma Etkinlikleri](messaging-activities.md)
