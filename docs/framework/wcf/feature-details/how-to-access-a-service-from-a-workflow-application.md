---
title: 'Nasıl yapılır: Bir İş Akışı Uygulamasından Bir Hizmete Erişme'
ms.date: 03/30/2017
ms.assetid: 925ef8ea-5550-4c9d-bb7b-209e20c280ad
ms.openlocfilehash: c524dc07106f039d9dc6c17ee6fb966321b6da24
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964524"
---
# <a name="how-to-access-a-service-from-a-workflow-application"></a>Nasıl yapılır: Bir İş Akışı Uygulamasından Bir Hizmete Erişme
Bu konu, bir iş akışı konsol uygulamasından bir iş akışı hizmetinin nasıl çağrılacağını açıklar. Bu, [nasıl yapılır: mesajlaşma etkinlikleriyle Iş akışı hizmeti oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md) konusunun tamamlanmasına bağlıdır. Bu konu, bir iş akışı hizmetinin iş akışı uygulamasından nasıl çağrılacağını açıklar, ancak aynı yöntemler bir iş akışı uygulamasından herhangi bir Windows Communication Foundation (WCF) hizmetini çağırmak için de kullanılabilir.

### <a name="create-a-workflow-console-application-project"></a>Iş akışı konsol uygulaması projesi oluşturma

1. Visual Studio 2012 ' i başlatın.

2. Oluşturduğunuz MyWFService projesini, [nasıl yapılır: mesajlaşma etkinlikleriyle Iş akışı hizmeti oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md) konusunda yükleyin.

3. **Çözüm Gezgini** **MyWFService** çözümüne sağ tıklayın ve **Ekle**, **Yeni proje**' yi seçin. Proje türleri listesinden **yüklü şablonlar** ve **Iş akışı konsol uygulamasında** **iş akışı** ' nı seçin. Projeyi MyWFClient olarak adlandırın ve aşağıdaki çizimde gösterildiği gibi varsayılan konumu kullanın.

     ![Yeni Proje Ekle Iletişim kutusu](./media/how-to-access-a-service-from-a-workflow-application/add-new-project-dialog.jpg)

     **Yeni Proje Ekle Iletişim kutusunu**kapatmak için **Tamam** düğmesine tıklayın.

4. Proje oluşturulduktan sonra, Workflow1. xaml dosyası tasarımcıda açılır. **Araç kutusu sekmesine tıklayarak** araç kutusunu açın ve araç kutusu penceresini açık tutmak için raptiye ' ye tıklayın.

5. Hizmeti derlemek ve başlatmak için **Ctrl**+**F5** tuşlarına basın. Daha önce olduğu gibi, ASP.NET Development Server başlatılır ve Internet Explorer, WCF Yardım sayfasını görüntüler. Sonraki adımda kullanmanız gereken bu sayfanın URI 'sine dikkat edin.

     ![WCF Yardım sayfasını ve URI 'yi görüntüleyen IE](./media/how-to-access-a-service-from-a-workflow-application/ie-wcf-help-page-uri.jpg)

6. **Çözüm Gezgini** **MyWFClient** projesine sağ tıklayın ve > **hizmet başvurusu** **Ekle** ' yi seçin. Tüm hizmetlerde geçerli çözümü aramak için **bul** düğmesine tıklayın. Hizmetler listesinde Service1. xamlx yanındaki üçgeni tıklatın. Service1 hizmeti tarafından uygulanan sözleşmeleri listelemek için Service1 ' ın yanındaki üçgeni tıklatın. **Hizmetler** listesinde **Service1** düğümünü genişletin. Yankı işlemi, aşağıdaki çizimde gösterildiği gibi **işlemler** listesinde görüntülenir.

     ![Hizmet Başvurusu Ekle Iletişim kutusu](./media/how-to-access-a-service-from-a-workflow-application/add-service-reference.jpg)

     Varsayılan ad alanını koruyun ve **hizmet başvurusu Ekle** iletişim kutusunu kapatmak için **Tamam** ' a tıklayın. Aşağıdaki iletişim kutusu görüntülenir.

     ![Hizmet Başvurusu Ekle bildirimi iletişim kutusu](./media/how-to-access-a-service-from-a-workflow-application/add-service-reference-dialog.jpg)

     İletişim kutusunu kapatmak için **Tamam** ' ı tıklatın. Ardından, çözümü derlemek için CTRL + SHIFT + B tuşlarına basın. Araç kutusunda, **MyWFClient. ServiceReference1. Activities**adlı yeni bir bölüm eklendiğini unutmayın. Bu bölümü genişletin ve aşağıdaki çizimde gösterildiği gibi eklenen yankı etkinliğine dikkat edin.

     ![Araç kutusundaki yankı etkinliği](./media/how-to-access-a-service-from-a-workflow-application/echo-activity-toolbox.jpg)

7. <xref:System.Activities.Statements.Sequence> etkinliğini tasarımcı yüzeyine sürükleyip bırakın. Araç kutusunun **Denetim akışı** bölümünün altındadır.

8. Odak <xref:System.Activities.Statements.Sequence> etkinlik ile, **değişkenler** bağlantısına tıklayın ve `inString`adlı bir dize değişkeni ekleyin. Aşağıdaki diyagramda gösterildiği gibi, değişkenine `"Hello, world"` varsayılan değerini ve `outString` adlı bir dize değişkenini verin.

     ![InString değişkeni ekleme](./media/how-to-access-a-service-from-a-workflow-application/add-instring-variable.jpg)

9. **Yankı** etkinliğini <xref:System.Activities.Statements.Sequence>sürükleyin ve bırakın. Özellikler penceresinde, `inMsg` bağımsız değişkenini aşağıdaki çizimde gösterildiği gibi, `outString` değişkenine `inString` değişkenine ve `outMsg` bağımsız değişkenine bağlayın. Bu, `inString` değişkeninin değerini işleme geçirir ve sonra döndürülen değeri alır ve `outString` değişkenine koyar.

     ![Bağımsız değişkenleri değişkenlere bağlama](./media/how-to-access-a-service-from-a-workflow-application/bind-arguments-variables.jpg)

10. Hizmet çağrısının döndürdüğü dizeyi göstermek için **echo** etkinliğinin altına bir **WriteLine** etkinliği sürükleyip bırakın. **WriteLine** etkinliği araç kutusundaki **temel öğeler** düğümünde bulunur. WriteLine etkinliğinin **metin** bağımsız değişkenini **WriteLine** etkinliğinin metin kutusuna `outString` yazarak `outString` değişkenine bağlayın. İş akışı şimdi aşağıdaki çizimde gösterildiği gibi görünmelidir.

     ![Tüm istemci iş akışı](./media/how-to-access-a-service-from-a-workflow-application/complete-client-workflow.jpg)

11. MyWFService çözümüne sağ tıklayın ve **Başlangıç projelerini ayarla...** seçeneğini belirleyin. **Birden çok başlangıç projesi** radyo düğmesini seçin ve aşağıdaki çizimde gösterildiği gibi **eylem** sütunundaki her bir proje için **Başlat** ' ı seçin.

     ![Başlangıç projeleri seçenekleri](./media/how-to-access-a-service-from-a-workflow-application/startup-project-options.jpg)

12. Hem hizmeti hem de istemcisini başlatmak için CTRL + F5 tuşlarına basın. ASP.NET Development Server hizmeti barındırır, Internet Explorer WCF Yardım sayfasını görüntüler ve istemci iş akışı uygulaması bir konsol penceresinde başlatılır ve hizmetten döndürülen dizeyi ("Hello, World") görüntüler.

## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Nasıl yapılır: Mesajlaşma Etkinlikleriyle İş Akışı Hizmeti Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)
- [Bir Web projesindeki Iş akışından bir WCF hizmetini kullanma](https://docs.microsoft.com/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow)
