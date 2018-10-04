---
title: 'Nasıl yapılır: Mesajlaşma Etkinlikleriyle İş Akışı Hizmeti Oluşturma'
ms.date: 03/30/2017
ms.assetid: 53d094e2-6901-4aa1-88b8-024b27ccf78b
ms.openlocfilehash: 12fc8706eb81df281571bb6ab54f7c2a2805f351
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48580504"
---
# <a name="how-to-create-a-workflow-service-with-messaging-activities"></a>Nasıl yapılır: Mesajlaşma Etkinlikleriyle İş Akışı Hizmeti Oluşturma
Bu konuda, Mesajlaşma etkinlikleri kullanarak basit bir iş akışı hizmeti oluşturma işlemini açıklamaktadır. Bu konu, burada yalnızca Mesajlaşma etkinlikleri hizmet oluşan bir iş akışı hizmeti oluşturma mekanizması üzerinde odaklanır. Gerçek hizmetinde, diğer birçok etkinlik iş akışı içerir. Hizmet, bir dize alır ve dize çağırana döner, Echo adlı bir işlem uygular. Bu konu, ilk iki konuda serisinin yöneliktir. Bir sonraki konu [nasıl yapılır: bir hizmeti bir iş akışı uygulamanın erişim](../../../../docs/framework/wcf/feature-details/how-to-access-a-service-from-a-workflow-application.md) Bu konu başlığında oluşturduğunuz hizmeti çağıran bir iş akışı uygulamasının nasıl oluşturulacağını açıklar.  
  
### <a name="to-create-a-workflow-service-project"></a>Bir iş akışı hizmeti projesi oluşturmak için  
  
1.  Visual Studio 2012 başlatın.  
  
2.  Tıklayın **dosya** menüsünde **yeni**, ardından **proje** görüntülenecek **yeni proje iletişim kutusu**. Seçin **iş akışı** yüklü şablonlar listesinden ve **WCF iş akışı hizmeti uygulaması** proje türleri listesinden. Projeyi adlandırın `MyWFService` ve aşağıdaki çizimde gösterildiği gibi varsayılan konumu kullanın.  
  
     Tıklayın **Tamam** kapatmak için düğme **yeni proje iletişim kutusu**.  
  
3.  Proje oluşturulduğunda Service1.xamlx dosya Tasarımcısı'nda aşağıdaki çizimde gösterildiği gibi açılır.  
  
     ![Varsayılan iş akışı Tasarımcısı'nda görüntülenen](../../../../docs/framework/wcf/feature-details/media/defaultworkflowservice.JPG "DefaultWorkflowService")  
  
     Etiketli etkinliğe sağ tıklayın **sıralı hizmeti** seçip **Sil**.  
  
### <a name="to-implement-the-workflow-service"></a>İş akışı hizmeti uygulamak için  
  
1.  Seçin **araç kutusu** raptiyeyi pencereyi açık tutun ve araç kutusunu görüntülemek için ekranın sol tarafındaki sekmesi. Genişletin **Mesajlaşma** bölümü aşağıdaki çizimde gösterildiği gibi Mesajlaşma etkinlikleri ve mesajlaşma etkinlik şablonları görüntülemek için araç kutusu.  
  
     ![Araç kutusu sekmesi Mesajlaşma Genişletilmiş](../../../../docs/framework/wcf/feature-details/media/wfdesignertoolbox.JPG "WFDesignerToolbox")  
  
2.  Sürükle ve bırak bir **ReceiveAndSendReply** iş akışı Tasarımcısı şablonu. Bu oluşturur bir <xref:System.Activities.Statements.Sequence> etkinliği ile bir **alma** etkinliği tarafından izlenen bir <xref:System.ServiceModel.Activities.SendReply> aşağıdaki çizimde gösterildiği gibi etkinlik.  
  
     ![ReceiveAndSendReply şablon Tasarımcısı'nda](../../../../docs/framework/wcf/feature-details/media/receiveandsendreply.JPG "ReceiveAndSendReply")  
  
     Dikkat <xref:System.ServiceModel.Activities.SendReply> etkinliğin <xref:System.ServiceModel.Activities.SendReply.Request%2A> özelliği `Receive`, adını <xref:System.ServiceModel.Activities.Receive> hangi etkinlik <xref:System.ServiceModel.Activities.SendReply> etkinlik yanıtlama.  
  
3.  İçinde <xref:System.ServiceModel.Activities.Receive> etkinlik türü `Echo` etiketli metin kutusu içine **OperationName**. Bu hizmetin işlem adını tanımlar uygular.  
  
     ![İşlem adı belirtin](../../../../docs/framework/wcf/feature-details/media/defineoperation.JPG "DefineOperation")  
  
4.  İle <xref:System.ServiceModel.Activities.Receive> seçili etkinlik Özellikler penceresini açmak tıklayarak açık değilse **görünümü** menü ve seçerek **Özellikler penceresi**. İçinde **Özellikler penceresi** görene kadar aşağı kaydırın **CanCreateInstance** ve aşağıdaki çizimde gösterildiği gibi onay kutusuna tıklayın. Bu ayar, bir ileti alındığında (gerekirse) hizmetinin yeni bir örneğini oluşturmak iş akışı hizmeti konağı sağlar.  
  
     ![CanCreateInstance özelliği](../../../../docs/framework/wcf/feature-details/media/cancreateinstance.JPG "CanCreateInstance")  
  
5.  Seçin <xref:System.Activities.Statements.Sequence> etkinliği ve tıklatın **değişkenleri** tasarımcının sol alt köşedeki düğmesi. Bu değişkenler Düzenleyicisi'ni görüntüler. Tıklayın **değişkeni oluşturma** işleme gönderilen dize depolamak için bir değişken eklemek için bağlantı. Değişken adı `msg` ve kendi **değişkeni** aşağıdaki çizimde gösterildiği gibi dize olarak yazın.  
  
     ![Değişken Ekle](../../../../docs/framework/wcf/feature-details/media/addvariable.JPG "AddVariable")  
  
     Tıklayın **değişkenleri** yeniden değişkenleri Düzenleyicisi'ni kapatmak için düğme.  
  
6.  Tıklayın **tanımlayın...** bağlantısını **içerik** metin kutusu <xref:System.ServiceModel.Activities.Receive> görüntülemek için etkinliği **içerik tanımı** iletişim. Seçin **parametreleri** radyo düğmesini'a tıklayın **yeni parametre Ekle** yazın, bağlantı `inMsg` içinde **adı** metin kutusunda **dize**içinde **türü** liste kutusu ve tür açılan `msg` içinde **atamak** aşağıdaki çizimde gösterildiği gibi metin kutusu.  
  
     ![Parametreleri içerik ekleme](../../../../docs/framework/wcf/feature-details/media/parameterscontent.jpg "ParametersContent")  
  
     Bu alma etkinliğini dize parametresi alan ve verilerin bağlandığı belirtir `msg` değişkeni. Tıklayın **Tamam** kapatmak için **içerik tanımı** iletişim.  
  
7.  Tıklayın **tanımlayın...**  bağlantısını **içerik** kutusunda <xref:System.ServiceModel.Activities.SendReply> görüntülemek için etkinliği **içerik tanımı** iletişim. Seçin **parametreleri** ye radyo düğmesini **yeni parametre Ekle** bağlantı, yazın `outMsg` içinde **adı** metin seçin **dize**içinde **türü** açılan liste kutusunda ve `msg` içinde **değer** aşağıdaki çizimde gösterildiği gibi metin kutusu.  
  
     ![Parametreleri içerik ekleme](../../../../docs/framework/wcf/feature-details/media/parameterscontent2.jpg "ParametersContent2")  
  
     Bu belirten <xref:System.ServiceModel.Activities.SendReply> etkinlik, bir ileti ya da ileti anlaşması türü gönderir ve bu verilere bağlı `msg` değişkeni. Bu olduğundan bir <xref:System.ServiceModel.Activities.SendReply> etkinlik, başka bir deyişle verilerde `msg` etkinlik istemciye geri gönderir ileti doldurmak için kullanılır. Tıklayın **Tamam** kapatmak için **içerik tanımı** iletişim.  
  
8.  Kaydet ve tıklayarak çözüm oluşturun **derleme** menü ve seçerek **Çözümü Derle**.  
  
## <a name="configure-the-workflow-service-project"></a>İş akışı hizmeti projesi yapılandırma  
 Tam iş akışı hizmetidir. Bu bölümde, barındırma ve çalıştırma kolaylaştırmak için iş akışı hizmeti çözümün nasıl yapılandırılacağını açıklar. Bu çözüm, ASP.NET Geliştirme Sunucusu hizmeti barındırmak için kullanır.  
  
#### <a name="to-set-project-start-up-options"></a>Proje başlangıç seçeneklerini ayarlamak için  
  
1.  İçinde **Çözüm Gezgini**, sağ **MyWFService** seçip **özellikleri** görüntülenecek **proje özellikleri** iletişim.  
  
2.  Seçin **Web** sekmenize **belirli sayfa** altında **başlatma eylemi** ve türü `Service1.xamlx` metin kutusunda aşağıdaki çizimde gösterildiği gibi.  
  
     ![Proje Özellikleri iletişim kutusu](../../../../docs/framework/wcf/feature-details/media/projectpropertiesdlg.JPG "ProjectPropertiesDlg")  
  
     Bu, Service1.xamlx ASP.NET geliştirme sunucusu içinde tanımlanan hizmet barındırır.  
  
3.  Hizmeti başlatmak için Ctrl + F5 tuşlarına basın. ASP.NET Geliştirme Sunucusu simge, aşağıdaki görüntüde gösterildiği gibi daha düşük sağ tarafında bulunan masaüstü görüntülenir.  
  
     ![ASP.NET Geliştirici sunucu simgesi](../../../../docs/framework/wcf/feature-details/media/aspnetdevservericon.JPG "ASPNETDEVServerIcon")  
  
     Ayrıca, WCF hizmeti Yardım Sayfası'hizmeti için Internet Explorer görüntüler.  
  
     ![WCF Yardım sayfası](../../../../docs/framework/wcf/feature-details/media/wcfhelppate.JPG "WCFHelpPate")  
  
4.  Geçin [nasıl yapılır: bir hizmeti bir iş akışı uygulamanın erişim](../../../../docs/framework/wcf/feature-details/how-to-access-a-service-from-a-workflow-application.md) bu hizmetine çağrı yapan bir iş akışı istemcisi oluşturmak için konu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş Akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [İş Akışı Hizmetlerini Barındırmaya Genel Bakış](../../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md)  
 [Mesajlaşma Etkinlikleri](../../../../docs/framework/wcf/feature-details/messaging-activities.md)
