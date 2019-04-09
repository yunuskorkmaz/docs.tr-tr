---
title: WCF Web HTTP Programlama Nesnesi Modeli
ms.date: 03/30/2017
ms.assetid: ed96b5fc-ca2c-4b0d-bdba-d06b77c3cb2a
ms.openlocfilehash: f1772220ed5f425ec603fd8927f4617446d106eb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59096016"
---
# <a name="wcf-web-http-programming-object-model"></a>WCF Web HTTP Programlama Nesnesi Modeli
WCF WEB HTTP programlama modeli, geliştiricilerin SOAP gerek kalmadan Windows Communication Foundation (WCF) Web Hizmetleri temel HTTP istekleri aracılığıyla kullanıma sunmak sağlar. WCF WEB HTTP programlama modeli, var olan WCF genişletilebilirlik model temelinde oluşturulmuştur. Aşağıdaki sınıfları tanımlar:  
  
 **Programlama modeli:**  
  
-   <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>  
  
-   <xref:System.ServiceModel.Web.WebGetAttribute>  
  
-   <xref:System.ServiceModel.Web.WebInvokeAttribute>  
  
-   <xref:System.ServiceModel.Web.WebServiceHost>  
  
 **Kanallar ve dağıtıcı altyapısı:**  
  
-   <xref:System.ServiceModel.WebHttpBinding>  
  
-   <xref:System.ServiceModel.Description.WebHttpBehavior>  
  
 **Yardımcı program sınıfları ve genişletilebilirlik noktaları:**  
  
-   <xref:System.UriTemplate>  
  
-   <xref:System.UriTemplateTable>  
  
-   <xref:System.ServiceModel.Dispatcher.QueryStringConverter>  
  
-   <xref:System.ServiceModel.Dispatcher.WebHttpDispatchOperationSelector>  
  
## <a name="aspnetcacheprofileattribute"></a>AspNetCacheProfileAttribute  
 <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, Bir hizmet işlemi için ASP.NET gösterir uygulandığında çıktı önbellek profili yapılandırma dosyasındaki tarafından önbellek yanıtları ASP .NET çıktı önbelleğinde işlemden kullanılmalıdır. Bu özellik yalnızca bir parametre, önbellek ayarlarını belirtir yapılandırma dosyasında önbellek profili adı alır.  
  
## <a name="webgetattribute"></a>WebGetAttribute  
 <xref:System.ServiceModel.Web.WebGetAttribute> Özniteliği, bir hizmet işlemi bir HTTP GET isteklerine yanıt olarak işaretlemek için kullanılır. Pasif işlemi davranıştır ( <xref:System.ServiceModel.Description.IOperationBehavior> yöntemleri bir şey yapmak), meta veri işlemi açıklamaya ekler. Uygulama <xref:System.ServiceModel.Web.WebGetAttribute> bir davranış, bu meta veri işlemi açıklamasında arar sürece hiçbir etkisi (özellikle <xref:System.ServiceModel.Description.WebHttpBehavior>) bu hizmetin davranışı koleksiyona eklenir. <xref:System.ServiceModel.Web.WebGetAttribute> Özniteliği isteğe bağlı parametreler aşağıdaki tabloda gösterilen alır.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`BodyStyle`|İsteklerin ve yanıtların gönderilen ve alınan öznitelik uygulandığı hizmet işlemi sarmalamak kontrol eder.|  
|`RequestFormat`|İstek iletilerinin nasıl biçimlendirileceğini denetler.|  
|`ResponseFormat`|Yanıt iletilerini nasıl biçimlendirileceğini denetler.|  
|`UriTemplate`|Öznitelik uygulandığı hizmet işlemi için hangi HTTP isteklerinin eşlenir denetimleri URI şablonunu belirtir.|  
  
## <a name="webhttpbinding"></a>webHttpBinding  
 <xref:System.ServiceModel.WebHttpBinding> Sınıfı, XML, JSON ve ham ikili verileri kullanma için destek içerir <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>. Oluşan bir <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpTransportBindingElement> ve <xref:System.ServiceModel.WebHttpSecurity> nesne. <xref:System.ServiceModel.WebHttpBinding> İle birlikte kullanılmak üzere tasarlanmış <xref:System.ServiceModel.Description.WebHttpBehavior>.  
  
## <a name="webinvokeattribute"></a>WebInvokeAttribute  
 <xref:System.ServiceModel.Web.WebInvokeAttribute> Özniteliği benzer <xref:System.ServiceModel.Web.WebGetAttribute>, ancak bir hizmet işlemi için HTTP yanıt veren bir GET dışındaki istekleri olarak işaretlemek için kullanılır. Pasif işlemi davranıştır ( <xref:System.ServiceModel.Description.IOperationBehavior> yöntemleri bir şey yapmak), meta veri işlemi açıklamaya ekler. Uygulama <xref:System.ServiceModel.Web.WebInvokeAttribute> bir davranış, bu meta veri işlemi açıklamasında arar sürece hiçbir etkisi (özellikle <xref:System.ServiceModel.Description.WebHttpBehavior>) bu hizmetin davranışı koleksiyona eklenir.  
  
 <xref:System.ServiceModel.Web.WebInvokeAttribute> Özniteliği isteğe bağlı parametreler aşağıdaki tabloda gösterilen alır.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`BodyStyle`|İsteklerin ve yanıtların gönderilen ve alınan öznitelik uygulandığı hizmet işlemi sarmalamak kontrol eder.|  
|`Method`|Hizmet işlemi eşlendiği HTTP yöntemi belirtir.|  
|`RequestFormat`|İstek iletilerinin nasıl biçimlendirileceğini denetler.|  
|`ResponseFormat`|Yanıt iletilerini nasıl biçimlendirileceğini denetler.|  
|`UriTemplate`|Öznitelik uygulandığı hizmet işlemi için hangi GET istekleri eşlenir denetimleri URI şablonunu belirtir.|  
  
## <a name="uritemplate"></a>UriTemplate  
 <xref:System.UriTemplate> Sınıfı bir dizi yapısal olarak benzer bir URI'leri tanımlamanıza izin verir. Şablonları bir yol ve sorgu olmak üzere iki bölümden oluşur. Bir yol kesimleri eğik çizgi (/) ayrılmış bir dizi oluşur. Her bir kesim değişmez değer, bir değişken değeri (yazılan kaşlı ayraçlar içinde [{}], kısıtlı içeriği tam olarak bir segmentin eşleşecek şekilde) veya bir joker karakter olabilir (yıldız işareti olarak yazılmış [\*], "yolun rest" ile eşleşir), en görünmesi gerekir Yolun sonuna. Sorgu ifadesi tamamen atlanabilir. Varsa, ad/değer çiftleri sırasız bir dizi belirtir. Sorgu ifadesinin öğeleri ya da değişmez değer çifti olabilir (? x = 2) veya değişken çiftleri (? = x {*değer*}). Eşlenmemiş değerlere izin verilmez. <xref:System.UriTemplate> WCF WEB HTTP programlama modeli tarafından belirli URI'ler ya da URI'ları grupları hizmet işlemleri eşleştirmek için dahili olarak kullanılır.  
  
## <a name="uritemplatetable"></a>UriTemplateTable  
 <xref:System.UriTemplateTable> Sınıfı temsil eder, ilişkili bir dizi <xref:System.UriTemplate> bağlı olan nesneleri geliştirici bir nesne seçme. Eşleşen şablonlarıyla ilişkili verileri almanıza ve şablonlar kümesi, karşı aday Tekdüzen Kaynak Tanımlayıcıları (URI'lar) eşleşen olanak tanır. <xref:System.UriTemplateTable> WCF WEB HTTP programlama modeli tarafından belirli URI'ler ya da URI'ları grupları hizmet işlemleri eşleştirmek için dahili olarak kullanılır.  
  
## <a name="webservicehost"></a>WebServiceHost  
 <xref:System.ServiceModel.Web.WebServiceHost> genişletir <xref:System.ServiceModel.ServiceHost> olmayan SOAP stili Web hizmeti barındırma daha kolay hale getirmek için. Varsa <xref:System.ServiceModel.Web.WebServiceHost> uç nokta bulur hizmet açıklamasında otomatik olarak bir varsayılan uç noktası hizmetin taban adresi oluşturur. Varsayılan bir HTTP uç oluştururken <xref:System.ServiceModel.Web.WebServiceHost> Ayrıca HTTP yardım sayfasına ve Web Hizmetleri Açıklama Dili (WSDL) alma işlevselliğini devre dışı bırakır meta veri uç noktasının varsayılan HTTP uç noktası ile aksatmaz şekilde. <xref:System.ServiceModel.Web.WebServiceHost> Ayrıca tüm uç noktalar, kullanmasını sağlar <xref:System.ServiceModel.WebHttpBinding> gerekli olan <xref:System.ServiceModel.Description.WebHttpBehavior> bağlı. Son olarak, <xref:System.ServiceModel.Web.WebServiceHost> güvenli sanal bir dizinde kullanıldığında ilişkili Internet Information Services (IIS) güvenlik ayarları ile çalışmak için uç noktanın bağlama otomatik olarak yapılandırır.  
  
## <a name="webservicehostfactory"></a>WebServiceHostFactory  
 <xref:System.ServiceModel.Activation.WebServiceHostFactory> Sınıfı dinamik olarak oluşturmak için kullanılan bir <xref:System.ServiceModel.Web.WebServiceHost> ne zaman bir hizmeti barındırılan Internet Information Services (IIS) veya Windows İşlem Etkinleştirme Hizmeti (WAS) altında. Burada barındırma uygulamasını başlatır şirket içinde barındırılan bir hizmet farklı <xref:System.ServiceModel.Web.WebServiceHost>, IIS altında barındırılan hizmetleri veya olan bu sınıf oluşturmak için kullanın <xref:System.ServiceModel.Web.WebServiceHost> hizmeti. <xref:System.ServiceModel.Activation.WebServiceHostFactory.CreateServiceHost%28System.Type%2CSystem.Uri%5B%5D%29> Yöntemi hizmeti için gelen bir istek alındığında çağrılır.  
  
## <a name="webhttpbehavior"></a>WebHttpBehavior  
 <xref:System.ServiceModel.Description.WebHttpBehavior> Sınıfı işlemi seçiciler, gerekli biçimlendiricileri sağlar ve hizmet modeli katmanında Web stili hizmet desteği vb. gerekir. Bu uç nokta davranışı uygulanır (ile birlikte kullanılan <xref:System.ServiceModel.WebHttpBinding>) ve biçimlendiricileri ve işlem Seçici SOAP hem POX uç noktalarını kullanıma sunmak aynı hizmet uygulaması sağlayan her uç noktası için belirtilmesine izin verir.  
  
### <a name="extending-webhttpbehavior"></a>WebHttpBehavior genişletme  
 <xref:System.ServiceModel.Description.WebHttpBehavior> bir dizi sanal yöntem kullanarak genişletilebilirdir: <xref:System.ServiceModel.Description.WebHttpBehavior.GetOperationSelector%28System.ServiceModel.Description.ServiceEndpoint%29>, <xref:System.ServiceModel.Description.WebHttpBehavior.GetReplyClientFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>, <xref:System.ServiceModel.Description.WebHttpBehavior.GetRequestClientFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>, <xref:System.ServiceModel.Description.WebHttpBehavior.GetReplyDispatchFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>, ve <xref:System.ServiceModel.Description.WebHttpBehavior.GetRequestDispatchFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>. Geliştiriciler bir sınıftan türetilebilir <xref:System.ServiceModel.Description.WebHttpBehavior> ve varsayılan davranışını özelleştirmek için bu yöntemi geçersiz kılın.  
  
 <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> Genişletme ilişkin bir örnektir <xref:System.ServiceModel.Description.WebHttpBehavior>. <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> Tarayıcı tabanlı ASP.NET AJAX istemciden gelen HTTP isteklerini almak Windows Communication Foundation (WCF) uç noktaları sağlar. [Hizmet HTTP POST kullanan AJAX](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) bu genişletilebilirlik noktası kullanarak, bir örnek verilmiştir.  
  
> [!WARNING]
>  Kullanırken <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>, <xref:System.UriTemplate> içinde desteklenmeyen <xref:System.ServiceModel.Web.WebGetAttribute> veya <xref:System.ServiceModel.Web.WebInvokeAttribute> öznitelikleri.  
  
## <a name="webhttpdispatchoperationselector"></a>WebHttpDispatchOperationSelector  
 <xref:System.ServiceModel.Dispatcher.WebHttpDispatchOperationSelector> Sınıfının kullandığı <xref:System.UriTemplate> ve <xref:System.UriTemplateTable> çağrıları hizmet işlemlerine gönderileceği sınıfları.  
  
## <a name="compatibility"></a>Uyumluluk  
 WCF WEB HTTP programlama modeli SOAP tabanlı iletileri kullanmaz ve bu nedenle WS - desteklemez * protokoller. Bununla birlikte, aynı sözleşme iki farklı uç noktası tarafından kullanıma sunma: SOAP ve diğer değil bir kullanarak SOAP kullanarak. Bkz: [nasıl yapılır: Bir sözleşmeyi SOAP ve Web istemcilerine sunma](../../../../docs/framework/wcf/feature-details/how-to-expose-a-contract-to-soap-and-web-clients.md) örneği.  
  
## <a name="security"></a>Güvenlik  
 WCF WEB HTTP programlama modeli WS - desteklemediği için * protokolleri WCF WEB HTTP programlama modeli üzerinde oluşturulmuş bir Web hizmeti güvenli hale getirmek için tek yolu olduğundan SSL kullanarak hizmetinize kullanıma sunmak için. SSL ile ayarlama hakkında daha fazla bilgi için [!INCLUDE[iisver](../../../../includes/iisver-md.md)] bkz [IIS'te SSL uygulama](https://go.microsoft.com/fwlink/?LinkId=131613)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
- <xref:System.ServiceModel.Web.WebInvokeAttribute>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- <xref:System.ServiceModel.Dispatcher.WebHttpDispatchOperationSelector>
- [WCF Web HTTP Programlama Modeli Genel Bakış](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
