---
title: "Nasıl yapılır: Mesajlaşma Etkinlikleriyle İş Akışı Hizmeti Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53d094e2-6901-4aa1-88b8-024b27ccf78b
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6b2f418298b5b937b5d4c7af2bd2def38c5827e9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-workflow-service-with-messaging-activities"></a>Nasıl yapılır: Mesajlaşma Etkinlikleriyle İş Akışı Hizmeti Oluşturma
Bu konu, Mesajlaşma etkinlikleri kullanarak basit bir iş akışı hizmeti oluşturmayı açıklar. Bu konu, burada yalnızca Mesajlaşma etkinlikleri servis oluşur bir iş akışı hizmeti oluşturma mekanizması odaklanır. Gerçek dünya hizmetinde, iş akışı diğer birçok etkinlik içerir. Hizmet bir dize alır ve çağırana dize verir Yankı adlı bir işlemi uygular. İlk iki Konular'a dizi konudur. Sonraki konuyu [nasıl yapılır: bir hizmet bir iş akışı uygulamanın erişim](../../../../docs/framework/wcf/feature-details/how-to-access-a-service-from-a-workflow-application.md) bu konuda oluşturulan hizmet çağırabilirsiniz bir iş akışı uygulamasının nasıl oluşturulacağını açıklar.  
  
### <a name="to-create-a-workflow-service-project"></a>Bir iş akışı hizmeti projesi oluşturmak için  
  
1.  Başlat [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Tıklatın **dosya** menüsünde, select **yeni**ve ardından **proje** görüntülemek için **yeni proje iletişim kutusu**. Seçin **iş akışı** yüklenmiş şablonlar listesinden ve **WCF iş akışı hizmeti uygulaması** proje türleri listesinden. Proje adı `MyWFService` ve varsayılan konumu aşağıdaki çizimde gösterildiği gibi kullanın.  
  
     Tıklatın **Tamam** kapatmak için düğmesini **yeni proje iletişim kutusu**.  
  
3.  Proje oluşturduğunuzda, Service1.xamlx dosya Tasarımcısı'nda aşağıdaki çizimde gösterildiği gibi açılır.  
  
     ![Varsayılan iş akışı Tasarımcısı'nda görüntülenen](../../../../docs/framework/wcf/feature-details/media/defaultworkflowservice.JPG "DefaultWorkflowService")  
  
     Etiketli etkinliği sağ **sıralı hizmet** seçip **silmek**.  
  
### <a name="to-implement-the-workflow-service"></a>İş akışı hizmeti uygulamak için  
  
1.  Seçin **araç** penceresi açık tutmak için Raptiye araç kutusunu görüntülemek ve ekranın sol tarafındaki sekmesinde. Genişletme **ileti** aşağıdaki çizimde gösterildiği gibi Mesajlaşma etkinlikleri ve mesajlaşma etkinlik şablonları görüntülemek için araç kutusu bölümü.  
  
     ![Araç kutusu İleti sekmesi ile Genişletilmiş](../../../../docs/framework/wcf/feature-details/media/wfdesignertoolbox.JPG "WFDesignerToolbox")  
  
2.  Sürükleme ve bırakma bir **ReceiveAndSendReply** iş akışı Tasarımcısı için şablon. Bu oluşturur bir <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence` etkinliği ile bir **alma** etkinlik arkasından bir <xref:System.ServiceModel.Activities.SendReply> aşağıdaki çizimde gösterildiği gibi etkinlik.  
  
     ![ReceiveAndSendReply şablonu Tasarımcısı'nda](../../../../docs/framework/wcf/feature-details/media/receiveandsendreply.JPG "ReceiveAndSendReply")  
  
     Dikkat <xref:System.ServiceModel.Activities.SendReply> etkinliğin <xref:System.ServiceModel.Activities.SendReply.Request%2A> özelliği ayarlanmış `Receive`, adını <xref:System.ServiceModel.Activities.Receive> hangi etkinlik <xref:System.ServiceModel.Activities.SendReply> etkinlik yanıtlama.  
  
3.  İçinde <xref:System.ServiceModel.Activities.Receive> etkinlik türü `Echo` etiketli metin kutusu içine **OperationName**. Bu işlemin hizmeti adının tanımlar uygular.  
  
     ![İşlem adı belirtmeniz](../../../../docs/framework/wcf/feature-details/media/defineoperation.JPG "DefineOperation")  
  
4.  İle <xref:System.ServiceModel.Activities.Receive> seçili etkinlik Özellikler penceresini açmak tıklayarak açık değilse **Görünüm** menü ve seçerek **Özellikler penceresini**. İçinde **Özellikler penceresini** görene kadar aşağı kaydırın **CanCreateInstance** ve aşağıdaki çizimde gösterildiği gibi onay kutusuna tıklayın. Bu ayar, bir ileti alındığında (gerekirse) hizmetinin yeni bir örneğini oluşturmak iş akışı hizmeti ana bilgisayarı sağlar.  
  
     ![CanCreateInstance özelliği](../../../../docs/framework/wcf/feature-details/media/cancreateinstance.JPG "CanCreateInstance")  
  
5.  Seçin <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence` etkinliği ve tıklatın **değişkenleri** tasarımcısının sol alt köşesinde düğmesini. Bu değişkenleri Düzenleyicisi görüntüler. Tıklatın **oluşturma değişkeni** işleme gönderilen dize depolamak için bir değişken eklemek için bağlantı. Değişken adı `msg` ve kendi **değişkeni** aşağıdaki çizimde gösterildiği gibi dize olarak yazın.  
  
     ![Değişken Ekle](../../../../docs/framework/wcf/feature-details/media/addvariable.JPG "AddVariable")  
  
     Tıklatın **değişkenleri** değişkenleri Düzenleyicisi'ni kapatmak için tekrar düğmesi.  
  
6.  Tıklatın **tanımlayın...** bağlamak **içerik** metin kutusu <xref:System.ServiceModel.Activities.Receive> görüntülemek için etkinliği **içerik tanımı** iletişim. Seçin **parametreleri** radyo düğmesi, tıklatın **yeni parametresini ekleyin** bağlantı, yazın `inMsg` içinde **adı** metin kutusunda **dize**içinde **türü** liste kutusu ve türü aşağı bırakma `msg` içinde **atamak için** aşağıdaki çizimde gösterildiği gibi metin kutusu.  
  
     ![Parametreleri içerik ekleme](../../../../docs/framework/wcf/feature-details/media/parameterscontent.jpg "ParametersContent")  
  
     Bu alma etkinliğini dize parametresi alan ve veri bağlı olduğu belirtir `msg` değişkeni. Tıklatın **Tamam** kapatmak için **içerik tanımı** iletişim.  
  
7.  Tıklatın **tanımlayın...**  bağlamak **içerik** kutusunda <xref:System.ServiceModel.Activities.SendReply> görüntülemek için etkinliği **içerik tanımı** iletişim. Seçin **parametreleri** radyo düğmesi, tıklatın **yeni bir parametre eklemek** bağlantı, yazın `outMsg` içinde **adı** metin kutusuna, select **dize**içinde **türü** açılır liste kutusunu ve `msg` içinde **değeri** aşağıdaki çizimde gösterildiği gibi metin kutusu.  
  
     ![Parametreleri içerik ekleme](../../../../docs/framework/wcf/feature-details/media/parameterscontent2.jpg "ParametersContent2")  
  
     Bu belirleyen <xref:System.ServiceModel.Activities.SendReply> etkinliği bir ileti veya ileti sözleşme türü gönderir ve bu verileri bağlı `msg` değişkeni. Bu olduğundan bir <xref:System.ServiceModel.Activities.SendReply> etkinlik, yani verileri `msg` etkinlik istemciye geri gönderir ileti doldurmak için kullanılır. Tıklatın **Tamam** kapatmak için **içerik tanımı** iletişim.  
  
8.  Kaydet ve tıklayarak çözümü derlemek **yapı** menü ve seçme **yapı çözümü**.  
  
## <a name="configure-the-workflow-service-project"></a>İş akışı hizmeti projesi yapılandırın  
 İş akışı hizmeti tamamlanır. Bu bölümde, barındırma ve çalıştırma kolaylaştırmak için iş akışı hizmeti çözümü yapılandırmak açıklanmaktadır. Bu çözüm ASP.NET Geliştirme Sunucusu hizmetini barındırmak için kullanır.  
  
#### <a name="to-set-project-start-up-options"></a>Proje başlatma seçenekleri ayarlamak için  
  
1.  İçinde **Çözüm Gezgini**, sağ **MyWFService** seçip **özellikleri** görüntülemek için **proje özelliklerini** iletişim.  
  
2.  Seçin **Web** sekmesinde ve seçin **belirli sayfa** altında **eylemi Başlat** ve türü `Service1.xamlx` aşağıdaki çizimde gösterildiği gibi metin kutusundaki.  
  
     ![Proje Özellikleri iletişim kutusu](../../../../docs/framework/wcf/feature-details/media/projectpropertiesdlg.JPG "ProjectPropertiesDlg")  
  
     ASP.NET Geliştirme Sunucusu Service1.xamlx tanımlanan hizmetini barındırır.  
  
3.  Hizmeti başlatmak için Ctrl + F5 tuşuna basın. ASP.NET Geliştirme Sunucusu simgesi alt sağ tarafında bulunan masaüstü aşağıdaki görüntüde gösterildiği gibi görüntülenir.  
  
     ![ASP.NET Geliştirme Sunucusu simgesi](../../../../docs/framework/wcf/feature-details/media/aspnetdevservericon.JPG "ASPNETDEVServerIcon")  
  
     Ayrıca, WCF hizmeti Yardım Sayfası'hizmeti için Internet Explorer görüntüler.  
  
     ![WCF Yardım sayfası](../../../../docs/framework/wcf/feature-details/media/wcfhelppate.JPG "WCFHelpPate")  
  
4.  Oturum devam [nasıl yapılır: bir hizmet bir iş akışı uygulamanın erişim](../../../../docs/framework/wcf/feature-details/how-to-access-a-service-from-a-workflow-application.md) bu hizmeti çağıran bir iş akışı istemcisi oluşturmak için konu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [İş akışı hizmetlerini barındırma genel bakış](../../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md)  
 [Mesajlaşma etkinlikleri](../../../../docs/framework/wcf/feature-details/messaging-activities.md)
