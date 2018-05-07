---
title: WCF Web HTTP Programlama Nesnesi Modeli
ms.date: 03/30/2017
ms.assetid: ed96b5fc-ca2c-4b0d-bdba-d06b77c3cb2a
ms.openlocfilehash: 412f3cb8aa0fcbb491bb9aeee907f848d272b847
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="wcf-web-http-programming-object-model"></a>WCF Web HTTP Programlama Nesnesi Modeli
WCF WEB HTTP programlama modeli, geliştiricilerin SOAP gerek kalmadan Windows Communication Foundation (WCF) Web hizmetlerini temel HTTP istekleri aracılığıyla kullanıma olanak tanır. WCF WEB HTTP programlama modeli, var olan WCF genişletilebilirlik modeli üzerinde oluşturulmuştur. Aşağıdaki sınıflar tanımlar:  
  
 **Programlama modeli:**  
  
-   <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>  
  
-   <xref:System.ServiceModel.Web.WebGetAttribute>  
  
-   <xref:System.ServiceModel.Web.WebInvokeAttribute>  
  
-   <xref:System.ServiceModel.Web.WebServiceHost>  
  
 **Kanallar ve dağıtıcı altyapı:**  
  
-   <xref:System.ServiceModel.WebHttpBinding>  
  
-   <xref:System.ServiceModel.Description.WebHttpBehavior>  
  
 **Yardımcı program sınıfları ve genişletilebilirlik noktaları:**  
  
-   <xref:System.UriTemplate>  
  
-   <xref:System.UriTemplateTable>  
  
-   <xref:System.ServiceModel.Dispatcher.QueryStringConverter>  
  
-   <xref:System.ServiceModel.Dispatcher.WebHttpDispatchOperationSelector>  
  
## <a name="aspnetcacheprofileattribute"></a>AspNetCacheProfileAttribute  
 <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, Bir hizmet işlemi için ASP.NET gösterir uygulandığında çıktı önbellek profili yapılandırma dosyasında tarafından önbellek yanıtlarını ASP .NET çıktı önbelleğindeki işleminden kullanılmalıdır. Bu özellik yalnızca bir parametre, yapılandırma dosyasında önbellek ayarlarını belirtir önbellek profili adı alır.  
  
## <a name="webgetattribute"></a>WebGetAttribute  
 <xref:System.ServiceModel.Web.WebGetAttribute> Özniteliği, bir hizmet işlemi bir HTTP GET isteklerine yanıt olarak işaretlemek için kullanılır. Pasif işlemi davranıştır ( <xref:System.ServiceModel.Description.IOperationBehavior> yöntemleri hiçbir şey yapmak), meta veri işlemi açıklama ekler. Uygulama <xref:System.ServiceModel.Web.WebGetAttribute> bir davranış, bu meta veri işlemi açıklamasında arar sürece herhangi bir etkisi olmaz (özellikle, <xref:System.ServiceModel.Description.WebHttpBehavior>) hizmetin davranışı koleksiyonuna eklenir. <xref:System.ServiceModel.Web.WebGetAttribute> Özniteliği aşağıdaki tabloda gösterilen isteğe bağlı parametreleri alır.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`BodyStyle`|İsteklerin ve yanıtların gönderilen ve öznitelik uygulandığı hizmet işlemi alınan sarmalamak denetler.|  
|`RequestFormat`|İstek iletilerinin nasıl biçimlendirileceğini denetler.|  
|`ResponseFormat`|Yanıt iletilerini nasıl biçimlendirileceğini denetler.|  
|`UriTemplate`|Hangi HTTP isteklerinin öznitelik uygulandığı hizmet işlemi eşlenmiş denetimleri URI şablonunu belirtir.|  
  
## <a name="webhttpbinding"></a>WebHttpBinding  
 <xref:System.ServiceModel.WebHttpBinding> Sınıfı içerir XML, JSON ve ham ikili veriler kullanılarak desteği <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>. Oluşur bir <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpTransportBindingElement> ve <xref:System.ServiceModel.WebHttpSecurity> nesne. <xref:System.ServiceModel.WebHttpBinding> İle birlikte kullanılmak üzere tasarlanmış <xref:System.ServiceModel.Description.WebHttpBehavior>.  
  
## <a name="webinvokeattribute"></a>WebInvokeAttribute  
 <xref:System.ServiceModel.Web.WebInvokeAttribute> Özniteliği benzer <xref:System.ServiceModel.Web.WebGetAttribute>, ancak bir hizmet işlemi için HTTP yanıt veren bir GET dışında istekleri olarak işaretlemek için kullanılır. Pasif işlemi davranıştır ( <xref:System.ServiceModel.Description.IOperationBehavior> yöntemleri hiçbir şey yapmak), meta veri işlemi açıklama ekler. Uygulama <xref:System.ServiceModel.Web.WebInvokeAttribute> bir davranış, bu meta veri işlemi açıklamasında arar sürece herhangi bir etkisi olmaz (özellikle, <xref:System.ServiceModel.Description.WebHttpBehavior>) hizmetin davranışı koleksiyonuna eklenir.  
  
 <xref:System.ServiceModel.Web.WebInvokeAttribute> Özniteliği aşağıdaki tabloda gösterilen isteğe bağlı parametreleri alır.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`BodyStyle`|İsteklerin ve yanıtların gönderilen ve öznitelik uygulandığı hizmet işlemi alınan sarmalamak denetler.|  
|`Method`|Hizmet işlemini eşlenmiş HTTP yöntemini belirtir.|  
|`RequestFormat`|İstek iletilerinin nasıl biçimlendirileceğini denetler.|  
|`ResponseFormat`|Yanıt iletilerini nasıl biçimlendirileceğini denetler.|  
|`UriTemplate`|Hangi GET istekleri öznitelik uygulandığı hizmet işlemi eşlenmiş denetimleri URI şablonunu belirtir.|  
  
## <a name="uritemplate"></a>UriTemplate  
 <xref:System.UriTemplate> Sınıfı, yapısal olarak benzer URI'ler kümesini tanımlamanızı sağlar. Şablonları bir yol ve sorgu olmak üzere iki bölümden oluşur. Bir yol kesimleri eğik çizgi (/) ayrılmış bir dizi oluşur. Her segment değişmez değer, bir değişken değeri (yazılmış süslü ayraçlar [{}] içinde kısıtlı tam olarak bir segment içeriğini eşleştirmek için) veya joker karakter bulunabilir (bir yıldız işareti olarak yazılmış [\*], "yolu rest" ile eşleşen), konumunda görünür olmalıdır Yolun sonu. Sorgu ifadesi tamamen atlanabilir. Varsa, ad/değer çiftleri sırasız bir dizi belirtir. Sorgu ifadesi öğeleri ya da değişmez değer çiftleri olabilir (? x = 2) veya değişken çiftleri (? = x {*değeri*}). Eşlenmemiş değerlere izin verilmez. <xref:System.UriTemplate> WCF WEB HTTP programlama modeli tarafından belirli URI'ler ya da kullanıcı grupları URI'ler hizmet işlemleri için eşlemek için dahili olarak kullanılır.  
  
## <a name="uritemplatetable"></a>UriTemplateTable  
 <xref:System.UriTemplateTable> Sınıfı temsil eder ilişkilendirilebilir bir dizi <xref:System.UriTemplate> bağlı nesneleri nesneyi geliştiricinin seçme. Eşleşen şablonları ile ilişkili verileri almanıza ve şablonları kümesindeki karşı adayı Tekdüzen Kaynak Tanımlayıcıları (URI'ler) eşleşmesi olanak tanır. <xref:System.UriTemplateTable> WCF WEB HTTP programlama modeli tarafından belirli URI'ler ya da kullanıcı grupları URI'ler hizmet işlemleri için eşlemek için dahili olarak kullanılır.  
  
## <a name="webservicehost"></a>WebServiceHost  
 <xref:System.ServiceModel.Web.WebServiceHost> genişletir <xref:System.ServiceModel.ServiceHost> SOAP olmayan stili Web hizmetini barındırmak daha kolay. Varsa <xref:System.ServiceModel.Web.WebServiceHost> uç nokta yok bulur hizmet açıklamasında otomatik olarak varsayılan uç noktası hizmetin taban adresi oluşturur. Varsayılan bir HTTP uç oluştururken <xref:System.ServiceModel.Web.WebServiceHost> meta veri uç noktasının varsayılan HTTP uç noktası ile etkilemediğinden için de HTTP yardım sayfasına ve Web Hizmetleri Açıklama Dili (WSDL) alma işlevini devre dışı bırakır. <xref:System.ServiceModel.Web.WebServiceHost> Ayrıca, tüm uç noktaları kullanan sağlar <xref:System.ServiceModel.WebHttpBinding> gerekli olan <xref:System.ServiceModel.Description.WebHttpBehavior> bağlı. Son olarak, <xref:System.ServiceModel.Web.WebServiceHost> güvenli sanal bir dizinde kullanıldığında ilişkili Internet Information Services (IIS) güvenlik ayarları ile çalışmak için uç noktanın bağlama otomatik olarak yapılandırır.  
  
## <a name="webservicehostfactory"></a>WebServiceHostFactory  
 <xref:System.ServiceModel.Activation.WebServiceHostFactory> Sınıfı dinamik olarak oluşturmak için kullanılan bir <xref:System.ServiceModel.Web.WebServiceHost> ne zaman bir hizmet barındırılan Internet Information Services (IIS) veya Windows İşlem Etkinleştirme Hizmeti (WAS) altında. Burada barındırma uygulamasının örneğini oluşturan kendini barındıran hizmet aksine <xref:System.ServiceModel.Web.WebServiceHost>, hizmetleri altında barındırılan bir IIS veya olan bu sınıf oluşturmak için kullanın <xref:System.ServiceModel.Web.WebServiceHost> hizmeti. <xref:System.ServiceModel.Activation.WebServiceHostFactory.CreateServiceHost%28System.Type%2CSystem.Uri%5B%5D%29> Yöntemi hizmeti için gelen bir istek alındığında çağrılır.  
  
## <a name="webhttpbehavior"></a>WebHttpBehavior  
 <xref:System.ServiceModel.Description.WebHttpBehavior> Sınıfı işlemi seçiciler, gerekli biçimlendiricileri sağlayan ve benzeri hizmet modeli katmanında stili Web hizmeti desteği için gereklidir. Bu uç noktası davranışı gerçekleştirilir (ile birlikte kullanılan <xref:System.ServiceModel.WebHttpBinding>) ve biçimlendiricileri ve işlem Seçici SOAP ve POX uç noktalarını kullanıma sunmak aynı hizmet uygulaması sağlayan her bitiş belirtilmesine izin verir.  
  
### <a name="extending-webhttpbehavior"></a>WebHttpBehavior genişletme  
 <xref:System.ServiceModel.Description.WebHttpBehavior> çeşitli sanal yöntemler kullanarak genişletilebilirdir: <xref:System.ServiceModel.Description.WebHttpBehavior.GetOperationSelector%28System.ServiceModel.Description.ServiceEndpoint%29>, <xref:System.ServiceModel.Description.WebHttpBehavior.GetReplyClientFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>, <xref:System.ServiceModel.Description.WebHttpBehavior.GetRequestClientFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>, <xref:System.ServiceModel.Description.WebHttpBehavior.GetReplyDispatchFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>, ve <xref:System.ServiceModel.Description.WebHttpBehavior.GetRequestDispatchFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>. Geliştiriciler bir sınıftan türetilen <xref:System.ServiceModel.Description.WebHttpBehavior> ve varsayılan davranışını özelleştirmek için bu yöntemleri geçersiz kılın.  
  
 <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> Genişletme örneğidir <xref:System.ServiceModel.Description.WebHttpBehavior>. <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> Tarayıcı tabanlı ASP.NET AJAX istemciden gelen HTTP isteklerini almak Windows Communication Foundation (WCF) uç noktaları sağlar. [AJAX hizmeti kullanarak HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) bu genişletilebilirlik noktasını kullanarak bir örnektir.  
  
> [!WARNING]
>  Kullanırken <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>, <xref:System.UriTemplate> içinde desteklenmeyen <xref:System.ServiceModel.Web.WebGetAttribute> veya <xref:System.ServiceModel.Web.WebInvokeAttribute> öznitelikleri.  
  
## <a name="webhttpdispatchoperationselector"></a>WebHttpDispatchOperationSelector  
 <xref:System.ServiceModel.Dispatcher.WebHttpDispatchOperationSelector> Sınıfını kullanan <xref:System.UriTemplate> ve <xref:System.UriTemplateTable> hizmet işlemlerine çağrıları gönderilmesi için sınıflar.  
  
## <a name="compatibility"></a>Uyumluluk  
 WCF WEB HTTP programlama modeli SOAP tabanlı iletileri kullanmaz ve bu nedenle WS - desteklemez * protokoller. Ancak, aynı sözleşme iki farklı bitiş noktası tarafından kullanıma: SOAP ve diğer olmayan bir kullanarak SOAP kullanarak. Bkz: [nasıl yapılır: bir sözleşmeyi SOAP ve Web istemcileri kullanıma](../../../../docs/framework/wcf/feature-details/how-to-expose-a-contract-to-soap-and-web-clients.md) bir örnek.  
  
## <a name="security"></a>Güvenlik  
 WCF WEB HTTP programlama modeli WS - desteklemediğinden * WCF WEB HTTP programlama modeli üzerinde oluşturulmuş bir Web hizmeti güvenli hale getirmek için tek yoludur SSL kullanarak hizmetinizi kullanıma sunmak için protokoller. SSL ile ayarlama hakkında daha fazla bilgi için [!INCLUDE[iisver](../../../../includes/iisver-md.md)] görmek [IIS'te SSL uygulama](http://go.microsoft.com/fwlink/?LinkId=131613)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>  
 <xref:System.ServiceModel.Web.WebInvokeAttribute>  
 <xref:System.ServiceModel.Description.WebHttpBehavior>  
 <xref:System.ServiceModel.Dispatcher.WebHttpDispatchOperationSelector>  
 [WCF Web HTTP Programlama Modeli Genel Bakış](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
