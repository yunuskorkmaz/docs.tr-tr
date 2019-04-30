---
title: 'Nasıl yapılır: Bir İş Akışı Uygulamasından Bir Hizmete Erişme'
ms.date: 03/30/2017
ms.assetid: 925ef8ea-5550-4c9d-bb7b-209e20c280ad
ms.openlocfilehash: 178fb04244cb3e5075722877fdd3e2b5a92b8502
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61779669"
---
# <a name="how-to-access-a-service-from-a-workflow-application"></a>Nasıl yapılır: Bir İş Akışı Uygulamasından Bir Hizmete Erişme
Bu konu, bir iş akışı hizmeti, bir iş akışı konsol uygulamasından çağırmak açıklar. Tamamlanmasına bağlıdır [nasıl yapılır: Mesajlaşma etkinlikleriyle iş akışı hizmeti oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md) konu. Bu konu, bir iş akışı uygulamasından bir iş akışı hizmeti çağırmak amacıyla açıklar ancak aynı yöntemleri herhangi bir Windows Communication Foundation (WCF) hizmeti bir iş akışı uygulamasından çağırmak için kullanılabilir.

### <a name="create-a-workflow-console-application-project"></a>Bir iş akışı konsol uygulaması projesi oluşturma

1. Visual Studio 2012 başlatın.

2. Oluşturduğunuz MyWFService proje yüklenecek [nasıl yapılır: Mesajlaşma etkinlikleriyle iş akışı hizmeti oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md) konu.

3. Sağ tıklayın **MyWFService** çözümde **Çözüm Gezgini** seçip **Ekle**, **yeni proje**. Seçin **iş akışı** içinde **yüklü şablonlar** ve **iş akışı konsol uygulaması** proje türleri listesinden. MyWFClient Projeyi adlandırın ve aşağıdaki çizimde gösterildiği gibi varsayılan konumu kullanın.

     ![Yeni Proje iletişim kutusu Ekle](./media/how-to-access-a-service-from-a-workflow-application/add-new-project-dialog.jpg)

     Tıklayın **Tamam** kapatmak için düğme **yeni proje iletişim kutusu Ekle**.

4. Proje oluşturulduktan sonra Workflow1.xaml dosyası tasarımcıda açılır. Tıklayın **araç kutusu** zaten açın ve araç kutusu penceresini açık tutun raptiyeyi değil ise, araç kutusunu açmak için sekmesinde.

5. Tuşuna **Ctrl**+**F5** oluştur ve hizmeti başlatın. Önceki örneklerde olduğu gibi ASP.NET Geliştirme Sunucusu başlatılır ve Internet Explorer'ı WCF Yardım sayfasını görüntüler. Sonraki adımda kullanmanız gerekeceğinden bu sayfasının URI'sini inceleyin.

     ![IE WCF Yardım sayfası ve URI görüntüleme](./media/how-to-access-a-service-from-a-workflow-application/ie-wcf-help-page-uri.jpg)

6. Sağ tıklayın **MyWFClient** projesi **Çözüm Gezgini** seçip **Ekle** > **hizmet başvurusu**. Tıklayın **bulma** diğer hizmetler için geçerli çözüm aramak için. Hizmetler listesinde Service1.xamlx yanındaki üçgene tıklayın. Service1 hizmeti tarafından uygulanan sözleşmelerin listelemek için Service1 yanındaki üçgene tıklayın. Genişletin **Service1** düğümünde **Hizmetleri** listesi. Yankı işlemi görüntülenen **işlemleri** listesinde aşağıdaki çizimde gösterildiği gibi.

     ![Hizmet Başvurusu Ekle iletişim kutusu](./media/how-to-access-a-service-from-a-workflow-application/add-service-reference.jpg)

     Varsayılan ad alanı tutun ve tıklayın **Tamam** kapatmak için **hizmet Başvurusu Ekle** iletişim. Aşağıdaki iletişim kutusu görüntülenir.

     ![Hizmet başvurusu bildirim iletişim kutusu Ekle](./media/how-to-access-a-service-from-a-workflow-application/add-service-reference-dialog.jpg)

     Tıklayın **Tamam** iletişim kutusunu kapatmak için. Ardından, çözümü derlemek için CTRL + SHIFT + B tuşlarına basın. Araç kutusunda yeni bir bölüm eklenmiştir bildirimi adlı **MyWFClient.ServiceReference1.Activities**. Bu bölümü genişletin ve aşağıdaki çizimde gösterildiği gibi eklenmiş olan Echo etkinlik dikkat edin.

     ![Araç kutusunda echo etkinliği](./media/how-to-access-a-service-from-a-workflow-application/echo-activity-toolbox.jpg)

7. Sürükle ve bırak bir <xref:System.Activities.Statements.Sequence> Tasarımcı yüzeyine etkinlik. Bunun altında olduğunu **akış denetimi** araç bölümü.

8. İle <xref:System.Activities.Statements.Sequence> odağı etkinliği tıklatın **değişkenleri** adlı bir dize değişkeni ekleyin ve bağlayın `inString`. Değişkeni varsayılan değerini verin `"Hello, world"` adlı bir dize değişkeni yanı sıra `outString` Aşağıdaki diyagramda gösterildiği gibi.

     ![İnString değişkeni ekleme](./media/how-to-access-a-service-from-a-workflow-application/add-instring-variable.jpg)

9. Sürükle ve bırak bir **Yankı** etkinliğini <xref:System.Activities.Statements.Sequence>. Özellikler penceresinde bağlama `inMsg` bağımsız değişkeni `inString` değişkeni ve `outMsg` bağımsız değişkeni `outString` aşağıdaki çizimde gösterildiği gibi bir değişken. Bu değeri geçirir `inString` değişken işleme ve dönüş değeri alır ve yerleştirir `outString` değişkeni.

     ![Bağımsız değişkenlerine bağlama](./media/how-to-access-a-service-from-a-workflow-application/bind-arguments-variables.jpg)

10. Sürükle ve bırak bir **WriteLine** etkinlik aşağıdaki **Yankı** hizmet çağrısı tarafından döndürülen dize görüntülemek için etkinliği. **WriteLine** etkinlik bulunan **Temelleri** araç kutusunda düğümü. Bağlama **metin** bağımsız değişkeni **WriteLine** etkinliğini `outString` değişken yazarak `outString` üzerindeki metin kutusunun içine **WriteLine** etkinlik. İş akışı aşağıdaki gibi görünmelidir.

     ![Tüm istemci iş akışı](./media/how-to-access-a-service-from-a-workflow-application/complete-client-workflow.jpg)

11. MyWFService çözüme sağ tıklayıp **başlangıç projelerini Ayarla...** . Seçin **birden fazla başlangıç projesi** radyo düğmesini seçip alt **Başlat** her proje için **eylem** aşağıdaki çizimde gösterildiği gibi sütun.

     ![Başlangıç projeleri seçenekleri](./media/how-to-access-a-service-from-a-workflow-application/startup-project-options.jpg)

12. Hem hizmet hem de istemci başlatmak için Ctrl + F5 tuşlarına basın. ASP.NET Geliştirme Sunucusu hizmeti barındıran, Internet Explorer'ı WCF Yardım sayfasını görüntüler ve istemci iş akışı uygulama konsol penceresinde başlatılır ve ("Hello, world") hizmetten döndürülen dizeyi gösterir.

## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Nasıl yapılır: Mesajlaşma etkinlikleriyle iş akışı hizmeti oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)
- [Web projesinde bir iş akışından bir WCF hizmetini kullanma](https://go.microsoft.com/fwlink/?LinkId=207725)
