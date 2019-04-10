---
title: SOAP ve HTTP Uç Noktaları
ms.date: 03/30/2017
ms.assetid: e3c8be75-9dda-4afa-89b6-a82cb3b73cf8
ms.openlocfilehash: 07f0c5a5a66683cf636595824b2ccaeaf1ab6a63
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59307450"
---
# <a name="soap-and-http-endpoints"></a>SOAP ve HTTP Uç Noktaları
Bu örnek nasıl rcp tabanlı bir hizmet ekleme ve SOAP hem Web WCF programlama modeli kullanarak "Düz eski XML" (POX) biçiminde kullanıma gösterir. Bkz: [temel HTTP hizmeti](../../../../docs/framework/wcf/samples/basic-http-service.md) hizmeti için HTTP bağlama hakkında daha fazla ayrıntı için örnek. Bu örnek aynı hizmeti SOAP ve farklı bağlamaları kullanarak HTTP üzerinden açığa çıkarmak için ilgili ayrıntıları ele alınmaktadır.  
  
## <a name="demonstrates"></a>Gösteriler  
 SOAP ve WCF kullanarak HTTP üzerinden RPC hizmeti gösterme.  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek iki bileşenden oluşur: bir WCF hizmeti ve SOAP ve HTTP bağlamalar kullanılarak hizmet işlemlerini çağıran bir konsol uygulaması (istemci) içeren bir Web uygulaması projesi (hizmet).  
  
 2 işlemleri – WCF hizmeti sunan`GetData` ve `PutData` – giriş olarak geçirilen dize echo. Hizmet işlemleri ile açıklamalı olan <xref:System.ServiceModel.Web.WebGetAttribute> ve <xref:System.ServiceModel.Web.WebInvokeAttribute>. Bu öznitelikler, bu işlemlerin HTTP projeksiyon denetler. İle buna açıklama <xref:System.ServiceModel.OperationContractAttribute>, bunları SOAP bağlamaları ortaya çıkmasını sağlar. Hizmetin `PutData` yöntem bir <xref:System.ServiceModel.Web.WebFaultException>, geri HTTP durum kodunu kullanarak HTTP üzerinden gönderilen ve bir SOAP hatası olarak SOAP üzerinden geri gönderilir.  
  
 Web.config dosyası WCF Hizmeti 3 uç noktaları ile yapılandırır:  
  
-   SOAP tabanlı istemciler tarafından erişim için hizmet meta verileri kullanıma sunan ~/service.svc/mex uç noktası.  
  
-   HTTP bağlaması kullanarak hizmete erişmek istemcileri etkinleştirir ~/service.svc/http uç noktası.  
  
-   HTTP bağlaması üzerinden SOAP'ı kullanarak hizmeti erişmesine olanak tanıyan ~/service.svc/soap uç noktası.  
  
 HTTP uç noktası ile yapılandırılmış bir <`webHttp`> olan standart uç nokta `helpEnabled` kümesine `true`. Sonuç olarak, hizmet, bir HTTP tabanlı istemciler hizmete erişmek için kullanabileceğiniz ~/service.svc/http/help tabanlı XHTML yardım sayfasına kullanıma sunar.  
  
 İstemci projesi bir SOAP proxy kullanarak hizmete erişim gösterir (aracılığıyla oluşturulan **hizmet Başvurusu Ekle**) hizmetini kullanarak erişmek ve <xref:System.Net.WebClient>.  
  
 Örnek Web barındırılan hizmet ve bir konsol uygulaması oluşur. Konsol uygulamasının çalışır gibi istemci hizmete isteği yapan ve konsol penceresine yanıtlardan bilgileri yazar.  
  
#### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1. SOAP ve HTTP uç noktaları örneği için çözümü açın.  
  
2. Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
3. CTRL + W, S, açmak için zaten açık değilse, basın **Çözüm Gezgini** penceresi.  
  
4. Gelen **Çözüm Gezgini** penceresinde sağ **hizmet** üzerine imleci getirin ve proje **hata ayıklama** bağlam menüsü seçeneği böylece **yeni başlangıç Örnek** bağlam menüsü görüntülenir. Tıklayın **yeni örnek Başlat**. Bu, hizmeti barındıran ASP.NET geliştirme sunucusu başlatır.  
  
5. Çözüm Gezgini Windows istemci projeye sağ tıklayın ve üzerine imleci getirin **hata ayıklama** bağlam menüsü seçeneği böylece **yeni örnek Başlat** bağlam menüsü görüntülenir. Tıklayın **yeni örnek Başlat**.  
  
6. İstemci konsol penceresi görünür ve çalışan hizmetin URI sağlar ve URI HTML Yardım sayfası çalışan hizmeti. Herhangi bir noktada HTML Yardım sayfası URI Yardım sayfasının bir tarayıcıda yazarak görüntüleyebilirsiniz.  
  
7. Örnek çalışırken, istemcinin geçerli etkinlik durumunu yazar.  
  
8. İstemci Konsolu uygulamayı sonlandırmak için herhangi bir tuşa basın.  
  
9. Hizmet hata ayıklamayı durdurmak için SHIFT + F5 tuşlarına basın.  
  
10. Windows bildirim alanındaki ASP.NET Geliştirme Sunucusu simgesine sağ tıklayıp **Durdur** bağlam menüsünden.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\SoapAndHttpEndpoints`
