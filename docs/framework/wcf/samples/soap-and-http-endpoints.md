---
title: SOAP ve HTTP Uç Noktaları
ms.date: 03/30/2017
ms.assetid: e3c8be75-9dda-4afa-89b6-a82cb3b73cf8
ms.openlocfilehash: f10b1aa4514aee50c0c0d17cabdb9516a3ca7584
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144025"
---
# <a name="soap-and-http-endpoints"></a>SOAP ve HTTP Uç Noktaları
Bu örnek, WCF Web Programlama modelini kullanarak RPC tabanlı bir hizmetin nasıl uygulanacağını ve SOAP biçiminde ve "Düz Eski XML" (POX) biçiminde nasıl ortaya çıkarılabildiğini göstermektedir. Hizmet için HTTP bağlama hakkında daha fazla bilgi için [Temel HTTP Hizmeti](../../../../docs/framework/wcf/samples/basic-http-service.md) örneğine bakın. Bu örnek, farklı ciltler kullanarak SOAP ve HTTP üzerinden aynı hizmeti açığa çıkarmak la ilgili ayrıntılara odaklanır.  
  
## <a name="demonstrates"></a>Gösteriler  
 WCF kullanarak SOAP ve HTTP üzerinden bir RPC hizmeti açığa.  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek iki bileşenden oluşur: Bir WCF hizmeti içeren bir Web Application projesi (Hizmet) ve SOAP ve HTTP bağlamaları kullanarak servis işlemlerini çağıran bir konsol uygulaması (İstemci).  
  
 WCF hizmeti 2 işlemi`GetData` ortaya `PutData` çıkarır - ve – bu giriş olarak geçirilen dize yankı. Hizmet işlemleri ile açıklamalı <xref:System.ServiceModel.Web.WebGetAttribute> ve <xref:System.ServiceModel.Web.WebInvokeAttribute>. Bu öznitelikler, bu işlemlerin HTTP projeksiyonuna denetler. Buna ek olarak, soap ciltler üzerinde maruz kalmalarını sağlayan , ile <xref:System.ServiceModel.OperationContractAttribute>açıklamalı. Hizmetin `PutData` <xref:System.ServiceModel.Web.WebFaultException>yöntemi, HTTP durum kodunu kullanarak HTTP üzerinden geri gönderilen alır ve soap hatası olarak SOAP üzerinden geri gönderilir bir atar.  
  
 Web.config dosyası WCF hizmetini 3 uç noktayla yapılandırır:  
  
- SOAP tabanlı istemciler tarafından erişim için hizmet meta verilerini ortaya çıkaran ~/service.svc/mex bitiş noktası.  
  
- Müşterilerin HTTP bağlamasını kullanarak hizmete erişmesini sağlayan ~/service.svc/http bitiş noktası.  
  
- Müşterilerin HTTP bağlama üzerinden SOAP kullanarak hizmete erişmelerini sağlayan ~/service.svc/soap endpoint.  
  
 HTTP bitiş noktası, <`webHttp`> standart bitiş noktası `helpEnabled` olarak `true`ayarlanmış olarak yapılandırılır. Sonuç olarak, hizmet, HTTP tabanlı istemcilerin hizmete erişmek için kullanabileceği ~/service.svc/http/help adresindeki XHTML tabanlı bir yardım sayfasını ortaya çıkarır.  
  
 İstemci projesi, bir SOAP proxy kullanarak hizmete erişimi **(Hizmet**Başvurusu <xref:System.Net.WebClient>Ekle yoluyla oluşturulan) ve hizmete erişimin .  
  
 Örnek, Web tarafından barındırılan bir hizmet ve konsol uygulamasından oluşur. Konsol uygulaması çalışırken, istemci hizmete istekte bulundu ve konsol penceresine verilen yanıtlardan ilgili bilgileri yazar.  
  
#### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1. SOAP ve HTTP Uç Noktaları Örneği için çözümü açın.  
  
2. Çözümü derlemek için CTRL+SHIFT+B'ye basın.  
  
3. Zaten açık değilse, **Çözüm Gezgini** penceresini açmak için CTRL+W, S tuşlarına basın.  
  
4. Çözüm **Gezgini** **penceresinden, Hizmet** projesine sağ tıklayın ve imleci **Hata Ayıklama** bağlamı menüsü seçeneğinin üzerine yerleştirin, böylece **Yeni Örnek Başlat** bağlam menüsü görünür. **Yeni Örneği Başlat'ı**tıklatın. Bu, hizmeti barındıran ASP.NET geliştirme sunucusunu başlatıyor.  
  
5. Çözüm Gezgini pencerelerinden, İstemci projesini sağ tıklatın ve imleci **Hata Ayıklama** bağlamı menüsü seçeneğinin üzerine yerleştirin, böylece **Yeni Örnek Başlat** bağlam menüsü görünür. **Yeni Örneği Başlat'ı**tıklatın.  
  
6. İstemci konsol penceresi görüntülenir ve çalışan hizmetin URI'sini ve çalışan hizmet için HTML yardım sayfasının URI'sini sağlar. Herhangi bir zamanda, bir tarayıcıdaki yardım sayfasının URI'sini yazarak HTML yardım sayfasını görüntüleyebilirsiniz.  
  
7. Örnek çalışırken, istemci geçerli etkinliğin durumunu yazar.  
  
8. İstemci konsolu uygulamasını sonlandırmak için herhangi bir tuşa basın.  
  
9. Hizmetin hata ayıklamasını durdurmak için SHIFT+F5 tuşuna basın.  
  
10. Windows Bildirim Alanı'nda, ASP.NET geliştirme sunucusu simgesine sağ tıklayın ve bağlam menüsünden **Durdur'u** seçin.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\SoapAndHttpEndpoints`
