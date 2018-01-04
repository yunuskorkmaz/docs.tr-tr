---
title: "Nasıl yapılır: Bir İş Akışı Uygulamasından Bir Hizmete Erişme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 925ef8ea-5550-4c9d-bb7b-209e20c280ad
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0ffac399e3f7cb3f860128b072251131ac356a2a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-access-a-service-from-a-workflow-application"></a>Nasıl yapılır: Bir İş Akışı Uygulamasından Bir Hizmete Erişme
Bu konuda, bir iş akışı konsol uygulamasından bir iş akışı hizmeti çağırma açıklar. Tamamlanma bağlı olduğu [nasıl yapılır: Mesajlaşma etkinlikleriyle iş akışı hizmeti oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md) konu. Herhangi bir çağrıda için bu konu bir iş akışı uygulamasından bir iş akışı hizmeti nasıl açıklansa da, aynı yöntemleri kullanılabilir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] bir iş akışı uygulamasından service.  
  
### <a name="create-a-workflow-console-application-project"></a>Bir iş akışı konsol uygulama projesi oluşturma  
  
1.  Başlat [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Oluşturduğunuz MyWFService proje yük [nasıl yapılır: Mesajlaşma etkinlikleriyle iş akışı hizmeti oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md) konu.  
  
3.  Sağ tıklayın **MyWFService** çözümde **Çözüm Gezgini** seçip **Ekle**, **yeni proje**. Seçin **iş akışı** içinde **yüklü şablonlar** ve **iş akışı konsol uygulaması** proje türleri listesinden. Projeyi MyWFClient adlandırın ve varsayılan konumu aşağıdaki çizimde gösterildiği gibi kullanın.  
  
     ![Yeni Proje iletişim kutusu ekleme](../../../../docs/framework/wcf/feature-details/media/addnewprojectdlg.JPG "AddNewProjectDlg")  
  
     Tıklatın **Tamam** kapatmak için düğmesini **yeni proje iletişim kutusu Ekle**.  
  
4.  Proje oluşturulduktan sonra Workflow1.xaml dosyası tasarımcıda açılır. Tıklatın **araç** sekmesini zaten açın ve araç penceresi açık tutmak için Raptiye tıklatın değilse araç kutusunu açın.  
  
5.  Derleme ve hizmeti başlatmak için Ctrl + F5 tuşuna basın. Önceki gibi ASP.NET Geliştirme Sunucusu başlatılır ve Internet Explorer WCF Yardım sayfasını görüntüler. Sonraki adımda kullanmanız gerektiği gibi bu sayfa için URI dikkat edin.  
  
     ![WCF Yardım sayfası ve URI IE görüntüleme](../../../../docs/framework/wcf/feature-details/media/iewcfhelppagewuri.JPG "IEWCFHelpPageWURI")  
  
6.  Sağ tıklayın **MyWFClient** proje **Çözüm Gezgini** seçip **hizmet Başvurusu Ekle**. Tıklatın **bulma** diğer hizmetler için geçerli çözümü aramak için düğmesini. Hizmetler listesinde Service1.xamlx yanındaki üçgen'ı tıklatın. Service1 hizmeti tarafından uygulanan sözleşmeleri listelemek için Service1 yanındaki üçgen'ı tıklatın. Genişletme **Service1** düğümünde **Hizmetleri** listesi. Echo işlemi görüntülenen **Operations** listesinde aşağıdaki çizimde gösterildiği gibi.  
  
     ![Hizmet Başvurusu Ekle iletişim kutusu](../../../../docs/framework/wcf/feature-details/media/addservicereference.JPG "Addservıcereference")  
  
     Varsayılan ad alanını tutun ve tıklatın **Tamam** kapatmak için **hizmet Başvurusu Ekle** iletişim. Aşağıdaki iletişim kutusu görüntülenir.  
  
     ![Ekle hizmet başvurusu bildirim iletişim kutusu](../../../../docs/framework/wcf/feature-details/media/asrdlg.JPG "ASRDlg")  
  
     Tıklatın **Tamam** iletişim kutusunu kapatmak üzere. Ardından, çözümü derlemek için CTRL + SHIFT + B tuşuna basın. Araç kutusu yeni bir bölüm eklenmiştir bildiriminde adlı **MyWFClient.ServiceReference1.Activities**. Bu bölümü genişletin ve aşağıdaki çizimde gösterildiği gibi eklenen Yankı etkinlik dikkat edin.  
  
     ![Araç kutusu etkinliğinde echo](../../../../docs/framework/wcf/feature-details/media/echoactivity.JPG "EchoActivity")  
  
7.  Sürükleme ve bırakma bir <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence` Tasarımcı yüzeyine etkinlik. Altında olan **akış denetimi** araç bölümü.  
  
8.  İle <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence` , odakta etkinliği tıklatın **değişkenleri** adlı bir dize değişkeni ekleyin ve bağlama `inString`. Varsayılan değer olan değişkeni verin `"Hello, world"` adlı bir dize değişkeni yanı sıra `outString` aşağıdaki çizimde gösterildiği gibi.  
  
     ![Bir değişken ekleme](../../../../docs/framework/wcf/feature-details/media/instringvar.JPG "inStringVar")  
  
9. Sürükleme ve bırakma bir **Echo** etkinliğini <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence`. Özellikler penceresinde bağlamak `inMsg` bağımsız değişkeni `inString` değişken ve `outMsg` bağımsız değişkeni `outString` aşağıdaki çizimde gösterildiği gibi değişkeni. Bu değeri geçirir `inString` değişken işlemi için dönüş değerini alır ve yerleştirir `outString` değişkeni.  
  
     ![Bağımsız değişkenler bağlama](../../../../docs/framework/wcf/feature-details/media/argumentbind.JPG "ArgumentBind")  
  
10. Sürükleme ve bırakma bir **WriteLine** etkinlik aşağıdaki **Echo** hizmet çağrı tarafından döndürülen dize görüntülemek için etkinliği. **WriteLine** etkinlik bulunduğu **Temelleri** araç düğümünde. Bağlama **metin** bağımsız değişkeni **WriteLine** etkinliğe `outString` yazarak değişken `outString` üzerinde metin kutusuna **WriteLine** etkinlik. İş akışı şimdi aşağıdaki gibi görünmelidir.  
  
     ![Tam istemci iş akışı](../../../../docs/framework/wcf/feature-details/media/completeclientwf.JPG "CompleteClientWF")  
  
11. MyWFService çözüme sağ tıklayın ve seçin **başlangıç projelerini Ayarla...** . Seçin **birden fazla başlangıç projesi** radyo düğmesini seçin ve Seç **Başlat** her proje için **eylem** aşağıdaki çizimde gösterildiği gibi sütun.  
  
     ![Başlangıç projeleri seçenekleri](../../../../docs/framework/wcf/feature-details/media/startupprojects.JPG "StartupProjects")  
  
12. Hem hizmet hem de istemci başlatmak için Ctrl + F5 tuşuna basın. ASP.NET Geliştirme Sunucusu hizmeti barındıran, Internet Explorer WCF Yardım sayfasını görüntüler ve istemci iş akışı uygulama konsol penceresinde başlatılır ve ("Hello, world") hizmetinden döndürülen dize görüntüler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş Akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Nasıl yapılır: Mesajlaşma Etkinlikleriyle İş Akışı Hizmeti Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)  
 [Bir Web projesi bir iş akışında bir WCF hizmetinden kullanma](http://go.microsoft.com/fwlink/?LinkId=207725)
