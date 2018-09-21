---
title: 'Nasıl yapılır: Bir İş Akışı Uygulamasından Bir Hizmete Erişme'
ms.date: 03/30/2017
ms.assetid: 925ef8ea-5550-4c9d-bb7b-209e20c280ad
ms.openlocfilehash: 460e5d0f1bbfdebf885176ed9fcc336b76731edd
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46493321"
---
# <a name="how-to-access-a-service-from-a-workflow-application"></a>Nasıl yapılır: Bir İş Akışı Uygulamasından Bir Hizmete Erişme
Bu konu, bir iş akışı hizmeti, bir iş akışı konsol uygulamasından çağırmak açıklar. Tamamlanmasına bağlıdır [nasıl yapılır: Mesajlaşma etkinlikleriyle iş akışı hizmeti oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md) konu. Bu konu, bir iş akışı uygulamasından bir iş akışı hizmeti çağırmak amacıyla açıklar ancak aynı yöntemleri herhangi bir Windows Communication Foundation (WCF) hizmeti bir iş akışı uygulamasından çağırmak için kullanılabilir.

### <a name="create-a-workflow-console-application-project"></a>Bir iş akışı konsol uygulaması projesi oluşturma

1.  Başlangıç [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].

2.  Oluşturduğunuz MyWFService proje yüklenecek [nasıl yapılır: Mesajlaşma etkinlikleriyle iş akışı hizmeti oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md) konu.

3.  Sağ tıklayın **MyWFService** çözümde **Çözüm Gezgini** seçip **Ekle**, **yeni proje**. Seçin **iş akışı** içinde **yüklü şablonlar** ve **iş akışı konsol uygulaması** proje türleri listesinden. MyWFClient Projeyi adlandırın ve aşağıdaki çizimde gösterildiği gibi varsayılan konumu kullanın.

     ![Yeni Proje iletişim kutusu Ekle](../../../../docs/framework/wcf/feature-details/media/addnewprojectdlg.JPG "AddNewProjectDlg")

     Tıklayın **Tamam** kapatmak için düğme **yeni proje iletişim kutusu Ekle**.

4.  Proje oluşturulduktan sonra Workflow1.xaml dosyası tasarımcıda açılır. Tıklayın **araç kutusu** zaten açın ve araç kutusu penceresini açık tutun raptiyeyi değil ise, araç kutusunu açmak için sekmesinde.

5.  Tuşuna **Ctrl**+**F5** oluştur ve hizmeti başlatın. Önceki örneklerde olduğu gibi ASP.NET Geliştirme Sunucusu başlatılır ve Internet Explorer'ı WCF Yardım sayfasını görüntüler. Sonraki adımda kullanmanız gerekeceğinden bu sayfasının URI'sini inceleyin.

     ![IE WCF Yardım sayfası ve URI görüntüleme](../../../../docs/framework/wcf/feature-details/media/iewcfhelppagewuri.JPG "IEWCFHelpPageWURI")

6.  Sağ tıklayın **MyWFClient** projesi **Çözüm Gezgini** seçip **Ekle** > **hizmet başvurusu**. Tıklayın **bulma** diğer hizmetler için geçerli çözüm aramak için. Hizmetler listesinde Service1.xamlx yanındaki üçgene tıklayın. Service1 hizmeti tarafından uygulanan sözleşmelerin listelemek için Service1 yanındaki üçgene tıklayın. Genişletin **Service1** düğümünde **Hizmetleri** listesi. Yankı işlemi görüntülenen **işlemleri** listesinde aşağıdaki çizimde gösterildiği gibi.

     ![Hizmet Başvurusu Ekle iletişim kutusu](../../../../docs/framework/wcf/feature-details/media/addservicereference.JPG "Addservıcereference")

     Varsayılan ad alanı tutun ve tıklayın **Tamam** kapatmak için **hizmet Başvurusu Ekle** iletişim. Aşağıdaki iletişim kutusu görüntülenir.

     ![Hizmet Başvurusu Ekle bildirim iletişim](../../../../docs/framework/wcf/feature-details/media/asrdlg.JPG "ASRDlg")

     Tıklayın **Tamam** iletişim kutusunu kapatmak için. Ardından, çözümü derlemek için CTRL + SHIFT + B tuşlarına basın. Araç kutusunda yeni bir bölüm eklenmiştir bildirimi adlı **MyWFClient.ServiceReference1.Activities**. Bu bölümü genişletin ve aşağıdaki çizimde gösterildiği gibi eklenmiş olan Echo etkinlik dikkat edin.

     ![Etkinlik araç kutusu echo](../../../../docs/framework/wcf/feature-details/media/echoactivity.JPG "EchoActivity")

7.  Sürükle ve bırak bir <xref:System.Activities.Statements.Sequence> Tasarımcı yüzeyine etkinlik. Bunun altında olduğunu **akış denetimi** araç bölümü.

8.  İle <xref:System.Activities.Statements.Sequence> odağı etkinliği tıklatın **değişkenleri** adlı bir dize değişkeni ekleyin ve bağlayın `inString`. Değişkeni varsayılan değerini verin `"Hello, world"` adlı bir dize değişkeni yanı sıra `outString` Aşağıdaki diyagramda gösterildiği gibi.

     ![Bir değişkeni ekleme](../../../../docs/framework/wcf/feature-details/media/instringvar.JPG "inStringVar")

9. Sürükle ve bırak bir **Yankı** etkinliğini <xref:System.Activities.Statements.Sequence>. Özellikler penceresinde bağlama `inMsg` bağımsız değişkeni `inString` değişkeni ve `outMsg` bağımsız değişkeni `outString` aşağıdaki çizimde gösterildiği gibi bir değişken. Bu değeri geçirir `inString` değişken işleme ve dönüş değeri alır ve yerleştirir `outString` değişkeni.

     ![Bağımsız değişkenleri için bağlama](../../../../docs/framework/wcf/feature-details/media/argumentbind.JPG "ArgumentBind")

10. Sürükle ve bırak bir **WriteLine** etkinlik aşağıdaki **Yankı** hizmet çağrısı tarafından döndürülen dize görüntülemek için etkinliği. **WriteLine** etkinlik bulunan **Temelleri** araç kutusunda düğümü. Bağlama **metin** bağımsız değişkeni **WriteLine** etkinliğini `outString` değişken yazarak `outString` üzerindeki metin kutusunun içine **WriteLine** etkinlik. İş akışı aşağıdaki gibi görünmelidir.

     ![Tüm istemci iş akışı](../../../../docs/framework/wcf/feature-details/media/completeclientwf.JPG "CompleteClientWF")

11. MyWFService çözüme sağ tıklayıp **başlangıç projelerini Ayarla...** . Seçin **birden fazla başlangıç projesi** radyo düğmesini seçip alt **Başlat** her proje için **eylem** aşağıdaki çizimde gösterildiği gibi sütun.

     ![Başlangıç projeleri seçenekleri](../../../../docs/framework/wcf/feature-details/media/startupprojects.JPG "StartupProjects")

12. Hem hizmet hem de istemci başlatmak için Ctrl + F5 tuşlarına basın. ASP.NET Geliştirme Sunucusu hizmeti barındıran, Internet Explorer'ı WCF Yardım sayfasını görüntüler ve istemci iş akışı uygulama konsol penceresinde başlatılır ve ("Hello, world") hizmetten döndürülen dizeyi gösterir.

## <a name="see-also"></a>Ayrıca Bkz.

- [İş Akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Nasıl yapılır: Mesajlaşma Etkinlikleriyle İş Akışı Hizmeti Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)
- [Web projesinde bir iş akışından bir WCF hizmetini kullanma](https://go.microsoft.com/fwlink/?LinkId=207725)