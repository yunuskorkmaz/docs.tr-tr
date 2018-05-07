---
title: ASP.NET AJAX için WCF Hizmetleri Oluşturma
ms.date: 03/30/2017
ms.assetid: 04c0402c-e617-4ba5-aedf-d17692234776
ms.openlocfilehash: c2d56380b626cd0eafc178b4db3584883b00a6bf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="creating-wcf-services-for-aspnet-ajax"></a>ASP.NET AJAX için WCF Hizmetleri Oluşturma
Microsoft ASP.NET AJAX, esnek ve tanıdık kullanıcı arabirimi öğeleri ile zengin kullanıcı deneyimi içeren Web sayfaları hızlı bir şekilde oluşturmanızı sağlar. ASP.NET AJAX tarayıcılar arası ECMAScript (JavaScript) ve dinamik HTML (DHTML) teknolojilerini istemci-komut dosyası kitaplıkları sağlar ve onu ASP.NET 2.0 sunucu tabanlı geliştirme platformu ile tümleştirir. ASP.NET AJAX'ı kullanarak, kullanıcı deneyimi ve Web uygulamalarınızın verimliliğini artırabilir.  
  
 ASP.NET AJAX istemci betik kitaplıkları ve sağlam geliştirme çerçeve sağlamak üzere tümleşik sunucu bileşenlerinin oluşur. Bir ASP.NET sayfasından bir hizmete erişmek için: hizmet URL'si sayfasındaki ASP.NET betik Yöneticisi denetime eklendikten sonra hizmet işlemleri kullanarak tam olarak normal JavaScript işlevi çağrısı gibi görünüyor JavaScript kodu çağrılabilir. Bkz: [ASP.NET AJAX'ı öğrenin](http://go.microsoft.com/fwlink/?LinkId=186475) Web Hizmetleri içinde AJAX framework kullanımıyla ilgili.  
  
 Çoğu Windows Communication Foundation (WCF) hizmetlerini ASP.NET AJAX ile uyumlu bir hizmet olarak uygun bir ASP.NET AJAX uç noktası ekleyerek açık olabilir.  
  
 Visual Studio kullanıyorsanız, AJAX etkinleştirilmiş WCF hizmetleri, kullanılabilir için önceden oluşturulmuş bir şablonu kullanabilir **Yeni Öğe Ekle** ASP.NET Web siteleri veya Web uygulamaları ile çalışırken iletişim.  
  
 Visual Studio şablonları kullanmıyorsanız, ASP.NET AJAX uç noktası oluşturmanın iki yolu vardır:  
  
-   Herhangi bir yapılandırma kullanmadan dinamik ana bilgisayar etkinleştirmesi uç noktası oluşturun. WCF yapılandırma sistemiyle tanımıyorsanız bu en temel bir yaklaşımdır. Daha fazla bilgi için bkz: [nasıl yapılır: ASP.NET AJAX uç nokta olmadan kullanarak Yapılandırması Ekle](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
-   Bir AJAX etkinleştirilmiş uç nokta Yapılandırması'nı kullanarak bir WCF hizmetine ekleyin. Daha fazla bilgi için bkz: [nasıl yapılır: ASP.NET AJAX uç noktası eklemek için yapılandırma kullan](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).  
  
 Açıklanan Web programlama modeli [WCF Web HTTP programlama modeline genel bakış](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md) ASP.NET AJAX Hizmetleri ile kullanılabilir. Özellikle:  
  
-   Kullanabileceğiniz <xref:System.ServiceModel.Web.WebGetAttribute> ve <xref:System.ServiceModel.Web.WebInvokeAttribute> arasında HTTP GET ve POST HTTP fiilleri seçmek için öznitelikler. Doğru kullandıysanız, bu, uygulamanızın performansını önemli ölçüde artırabilir. Daha fazla bilgi için bkz: [nasıl yapılır: istekleri ASP.NET AJAX uç noktaları için HTTP POST ve HTTP GET arasında seçim yapma](../../../../docs/framework/wcf/feature-details/http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md).  
  
-   Kullanabileceğiniz <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> ve <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> hizmetinizin varsayılan JavaScript nesne gösterimi (JSON) yerine XML verileri döndürmek için neden özellikleri. Bunu yapmak ASP.NET AJAX framework ile bir XML DOM nesnesi almak JavaScript istemci neden olur.  
  
    > [!WARNING]
    >  İşleminizi içerik türünü text/XML Bunun çalışması ayarlamanız gerekir. Aksi takdirde, JavaScript istemci bir XML DOM nesne yerine XML içeren bir dize alır.  
  
     XML verileri içerik türü uygun şekilde ayarlanan döndüren bir işlemin bir örnek verilmiştir:  
  
    ```  
    [OperationContract, WebGet(ResponseFormat=WebMessageFormat.Xml)]  
    public XElement GetData()  
    {  
    XElement x;  
    //Get some data here...  
  
    WebOperationContext.Current.OutgoingResponse.ContentType = "text/xml";      
    return x;  
    }  
    ```  
  
-   Bulunan diğer özelliklerden <xref:System.ServiceModel.Web.WebGetAttribute> ve <xref:System.ServiceModel.Web.WebInvokeAttribute> öznitelikleri, ASP.NET AJAX ile uyumluluk gerekirse değiştirilebilir. ASP.NET AJAX çağırma kurallarını ihlal etti değil sürece Web programlama modeli diğer yönlerini kullanılabilir.  
  
 Daha Gelişmiş senaryolar bazı ek ayrıntıları WCF AJAX desteğinin anlaşılmasını gerektirir:  
  
-   Nasıl veriler arasında bir AJAX sayfa istemcisi ve JavaScript kullanarak bir WCF hizmeti ve Ayrıntılar için .NET Framework türleri JavaScript türlerine nasıl eşlenir aktarılır anlamak için bkz: [JSON ve diğer veri aktarma biçimleri için destek](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md).  
  
-   ASP.NET özelliklerden yararlanmak için örneğin, URL tabanlı kimlik doğrulaması ve ASP.NET oturum bilgilerine erişme, ASP.NET uyumluluk modu yapılandırma yoluyla etkinleştirmek isteyebilirsiniz.  
  
 WCF'de AJAX uç noktaları bile kullanmadan ASP.NET AJAX framework tüketilebilir. Bunun yapılması, WCF AJAX desteği destek mimarisini bilinmesini gerektirir. Bu mimarinin bir tartışma için bkz: [WCF Web HTTP programlama nesnesi modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md). Bu yaklaşım gösteren bir kod örneği için bkz: [JSON ve XML ile AJAX hizmeti](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Web HTTP Programlama Modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [Nasıl yapılır: Yapılandırma Kullanmadan ASP.NET AJAX Uç Noktası Ekleme](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)  
 [Nasıl yapılır: ASP.NET AJAX Uç Noktası Eklemek için Yapılandırma Kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)  
 [Nasıl yapılır: ASP.NET AJAX Uç Noktaları için HTTP POST ve HTTP GET İstekleri Arasında Seçim Yapma](../../../../docs/framework/wcf/feature-details/http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md)
