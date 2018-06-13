---
title: SOAP ve HTTP Uç Noktaları
ms.date: 03/30/2017
ms.assetid: e3c8be75-9dda-4afa-89b6-a82cb3b73cf8
ms.openlocfilehash: 4c8a4695dbcaee2f0e7584418fbeac12815fa967
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809524"
---
# <a name="soap-and-http-endpoints"></a>SOAP ve HTTP Uç Noktaları
Bu örnek, RPC tabanlı bir hizmete uygulamak ve SOAP hem WCF Web programlama modeli kullanarak "Düz eski XML" (POX) biçiminde kullanıma gösterilmiştir. Bkz: [temel HTTP hizmeti](../../../../docs/framework/wcf/samples/basic-http-service.md) hizmeti için HTTP bağlama hakkında daha fazla ayrıntı için örnek. Bu örnek SOAP ve farklı bağlamalar kullanılarak HTTP üzerinden aynı hizmeti gösterme ilgilidir ayrıntıları odaklanır.  
  
## <a name="demonstrates"></a>Gösteriler  
 SOAP ve WCF kullanarak HTTP üzerinden RPC hizmeti gösterme.  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek iki bileşenden oluşur: bir WCF hizmeti ve SOAP ve HTTP bağlantılarını kullanarak hizmet işlemlerini çağıran bir konsol uygulaması (istemci) içeren bir Web uygulaması projesi (hizmeti).  
  
 2 operations – WCF hizmeti sunan`GetData` ve `PutData` – giriş olarak geçirilen dize echo. Hizmet işlemleri ile Açıklama <xref:System.ServiceModel.Web.WebGetAttribute> ve <xref:System.ServiceModel.Web.WebInvokeAttribute>. Bu öznitelikler, bu işlemlerin HTTP projeksiyon denetler. İle ek olarak, açıklama <xref:System.ServiceModel.OperationContractAttribute>, bunları SOAP bağlamaları açığa çıkarılması sağlar. Hizmetin `PutData` yöntemi atar bir <xref:System.ServiceModel.Web.WebFaultException>, geri HTTP durum kodu kullanarak HTTP üzerinden gönderilir ve bir SOAP hatası olarak SOAP üzerinden geri gönderilir.  
  
 Web.config dosyasını 3 uç ile WCF hizmeti yapılandırır:  
  
-   SOAP tabanlı istemcilerine erişmek için hizmet meta verilerini kullanıma sunan ~/service.svc/mex uç noktası.  
  
-   İstemcilerin HTTP bağlama kullanarak hizmet erişmesine olanak sağlayan ~/service.svc/http uç noktası.  
  
-   SOAP üzerinden HTTP bağlama kullanarak hizmete erişmek istemcilerin ~/service.svc/soap uç noktası.  
  
 HTTP uç noktası ile yapılandırılmış bir <`webHttp`> olan standart endpoint `helpEnabled` kümesine `true`. Sonuç olarak, hizmet istemcilerin HTTP tabanlı hizmete erişmek için kullanabileceği ~/service.svc/http/help bir temel XHTML yardım sayfasına kullanıma sunar.  
  
 Hizmeti bir SOAP proxy kullanarak erişen istemci projesi gösterir (aracılığıyla oluşturulan **hizmet Başvurusu Ekle**) ve hizmet kullanarak erişme <xref:System.Net.WebClient>.  
  
 Örnek bir Web barındırılan hizmeti ve bir konsol uygulaması oluşur. Konsol uygulaması çalışırken, istemci hizmete istek yaptığında ve konsol penceresine yanıtlardan bilgileri yazar.  
  
#### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1.  Çözüm SOAP ve HTTP uç noktaları örnek için açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
3.  Zaten açık değilse, CTRL + W, açmak için S tuşlarına basın **Çözüm Gezgini** penceresi.  
  
4.  Gelen **Çözüm Gezgini** penceresinde sağ **hizmet** proje ve imleci üzerine getirin **hata ayıklama** bağlam menüsü seçeneğini böylece **Başlat yeni Örnek** bağlam menüsü görüntülenir. Tıklatın **Başlat yeni örnek**. Bu hizmeti barındıran ASP.NET geliştirme sunucusu başlatır.  
  
5.  Çözüm Gezgini Windows istemci projesine sağ tıklayın ve imleci üzerine getirin **hata ayıklama** bağlam menüsü seçeneğini böylece **Başlat yeni örnek** bağlam menüsü görüntülenir. Tıklatın **Başlat yeni örnek**.  
  
6.  İstemci konsol penceresi görüntülenir ve çalışan hizmetin URI sağlar ve URI HTML sayfası çalışan hizmetin için yardımcı olur. Herhangi bir noktada, HTML Yardım sayfasına bir tarayıcıda yardım sayfasına URI'sini yazarak görüntüleyebilirsiniz.  
  
7.  Örnek çalışırken, istemcinin geçerli etkinlik durumunu yazar.  
  
8.  İstemci konsol uygulaması sonlandırmak için herhangi bir tuşa basın.  
  
9. Hata ayıklama hizmetini durdurmak için SHIFT + F5 tuşuna basın.  
  
10. Windows bildirim alanında ASP.NET Geliştirme Sunucusu simgesini sağ tıklatın ve seçin **durdurmak** ve bağlam menüsünden.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\SoapAndHttpEndpoints`
