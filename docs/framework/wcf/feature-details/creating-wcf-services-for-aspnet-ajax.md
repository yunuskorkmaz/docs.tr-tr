---
title: ASP.NET AJAX için WCF Hizmetleri Oluşturma
ms.date: 03/30/2017
ms.assetid: 04c0402c-e617-4ba5-aedf-d17692234776
ms.openlocfilehash: 4d3953046a796686a465cd8096b8f2ba930aa9fd
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43463266"
---
# <a name="creating-wcf-services-for-aspnet-ajax"></a>ASP.NET AJAX için WCF Hizmetleri Oluşturma
Microsoft ASP.NET AJAX zengin bir kullanıcı deneyimi ile esnek ve tanıdık bir kullanıcı arabirimi öğeleri içeren Web sayfaları hızlıca oluşturmanıza olanak sağlar. ASP.NET AJAX tarayıcılar arası ECMAScript (JavaScript) ve dinamik HTML (DHTML) teknolojiler bir araya getiren betiği istemci kitaplıkları sağlar ve bunları ASP.NET 2.0 sunucu tabanlı geliştirme platformu ile tümleştirilir. ASP.NET AJAX'ı kullanarak, kullanıcı deneyimini ve Web uygulamalarınızı verimliliğini artırabilir.  
  
 ASP.NET AJAX istemci betik kitaplıkları ve güçlü geliştirme framework sağlamak için tümleşik sunucu bileşenlerinin oluşur. Bir ASP.NET sayfasından bir hizmete erişmek için: hizmet URL'si ASP.NET komut Yöneticisi denetimi sayfasına eklendikten sonra hizmet işlemleri tam olarak normal işlev gibi JavaScript çağrısı görünen JavaScript kodu kullanarak çağrılabilir. Bkz: [öğrenin ASP.NET AJAX](https://go.microsoft.com/fwlink/?LinkId=186475) Web Hizmetleri AJAX çerçevesine kullanımıyla ilgili.  
  
 Çoğu Windows Communication Foundation (WCF) Hizmetleri ASP.NET AJAX ile uyumlu bir hizmet olarak uygun bir ASP.NET AJAX uç noktası ekleyerek açık olabilir.  
  
 Visual Studio kullanıyorsanız, kullanılabilen AJAX etkin WCF hizmetleri için önceden oluşturulmuş bir şablon kullanabilir **Yeni Öğe Ekle** ASP.NET Web siteleri ve Web uygulamaları ile çalışırken iletişim.  
  
 Visual Studio şablonları kullanmıyorsanız, bir ASP.NET AJAX uç noktası oluşturmanın iki yolu vardır:  
  
-   Herhangi bir yapılandırma olmadan dinamik ana bilgisayar etkinleştirme kullanarak uç noktası oluşturun. WCF yapılandırma sistemi ile alışkın değilseniz en basit yaklaşımdır. Daha fazla bilgi için [nasıl yapılır: bir ASP.NET AJAX uç noktası olmadan kullanarak Yapılandırması Ekle](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
-   AJAX etkinleştirilmiş bir uç nokta Yapılandırması'nı kullanarak bir WCF Hizmeti ekleyin. Daha fazla bilgi için [nasıl yapılır: ASP.NET AJAX uç noktası eklemek için yapılandırma kullan](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).  
  
 Açıklanan Web programlama modeli [WCF Web HTTP programlama modeli genel bakış](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md) ASP.NET AJAX Hizmetleri ile kullanılabilir. Özellikle:  
  
-   Kullanabileceğiniz <xref:System.ServiceModel.Web.WebGetAttribute> ve <xref:System.ServiceModel.Web.WebInvokeAttribute> arasında HTTP GET ve POST HTTP fiilleri seçmek için öznitelikler. Doğru kullandıysanız, bu, uygulamanızın performansını önemli ölçüde artırabilir. Daha fazla bilgi için [nasıl yapılır: istekleri ASP.NET AJAX uç noktaları için HTTP POST ve HTTP GET arasında seçim yapma](../../../../docs/framework/wcf/feature-details/http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md).  
  
-   Kullanabileceğiniz <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> ve <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> varsayılan JavaScript nesne gösterimi (JSON) yerine XML verileri döndürmek için hizmetinize neden özellikleri. ASP.NET AJAX framework ile bunu bir XML DOM nesnesi almak JavaScript istemci neden olur.  
  
    > [!WARNING]
    >  İşleminizi içerik türü metin/xml Bunun çalışması ayarlamanız gerekir. Aksi takdirde, JavaScript istemci XML yerine bir XML DOM nesnesi içeren bir dize alır.  
  
     XML verileri ile uygun şekilde ayarlanmış içerik türünü döndüren bir işlem örneği verilmiştir:  
  
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
  
-   Üzerinde başka hiçbir özellik <xref:System.ServiceModel.Web.WebGetAttribute> ve <xref:System.ServiceModel.Web.WebInvokeAttribute> ASP.NET AJAX ile uyumluluk gerekliyse, öznitelikler değiştirilebilir. ASP.NET AJAX çağırma kurallarını ihlal değil sürece Web programlama modelinin diğer yönleri kullanılabilir.  
  
 Daha gelişmiş senaryoları WCF AJAX desteğinin bazı ek ayrıntıları anlaşılmasını gerektirir:  
  
-   Nasıl veri ayrıntıları yanı sıra, JavaScript kullanarak bir WCF Hizmeti ile bir AJAX sayfasına istemci arasında .NET Framework türleri JavaScript türleriyle nasıl eşleştiği aktarılır anlamak için bkz [JSON ve diğer veri aktarma biçimleri için destek](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md).  
  
-   ASP.NET özelliklerinden yararlanmak için örneğin, URL tabanlı kimlik doğrulaması ve ASP.NET oturum bilgilerine erişmek, ASP.NET uyumlu mod yapılandırma yoluyla sağlamak isteyebilirsiniz.  
  
 WCF AJAX uç noktaları kullanmadan ASP.NET AJAX framework bile tarafından kullanılabilir. Bunun yapılması, WCF AJAX desteği destek mimarisi bilinmesini gerektirir. Bu mimarinin bir tartışma için bkz [WCF Web HTTP programlama nesnesi modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md). Bu yaklaşım gösteren bir kod örneği için bkz. [JSON ve XML ile AJAX hizmeti](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Web HTTP Programlama Modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [Nasıl yapılır: Yapılandırma Kullanmadan ASP.NET AJAX Uç Noktası Ekleme](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)  
 [Nasıl yapılır: ASP.NET AJAX Uç Noktası Eklemek için Yapılandırma Kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)  
 [Nasıl yapılır: ASP.NET AJAX Uç Noktaları için HTTP POST ve HTTP GET İstekleri Arasında Seçim Yapma](../../../../docs/framework/wcf/feature-details/http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md)
