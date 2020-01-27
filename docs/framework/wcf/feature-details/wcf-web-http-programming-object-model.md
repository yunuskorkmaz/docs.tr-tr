---
title: WCF Web HTTP Programlama Nesnesi Modeli
ms.date: 03/30/2017
ms.assetid: ed96b5fc-ca2c-4b0d-bdba-d06b77c3cb2a
ms.openlocfilehash: 39c7ec31827d1cde5d95516cc3867f9d6bf9817f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739869"
---
# <a name="wcf-web-http-programming-object-model"></a>WCF Web HTTP Programlama Nesnesi Modeli
WCF WEB HTTP programlama modeli, geliştiricilerin SOAP gerektirmeden temel HTTP istekleri aracılığıyla Windows Communication Foundation (WCF) Web hizmetlerini kullanıma almasına olanak tanır. WCF WEB HTTP programlama modeli, mevcut WCF genişletilebilirlik modelinin üzerine kurulmuştur. Aşağıdaki sınıfları tanımlar:  
  
 **Programlama modeli:**  
  
- <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>  
  
- <xref:System.ServiceModel.Web.WebGetAttribute>  
  
- <xref:System.ServiceModel.Web.WebInvokeAttribute>  
  
- <xref:System.ServiceModel.Web.WebServiceHost>  
  
 **Kanallar ve dağıtıcı altyapısı:**  
  
- <xref:System.ServiceModel.WebHttpBinding>  
  
- <xref:System.ServiceModel.Description.WebHttpBehavior>  
  
 **Yardımcı program sınıfları ve genişletilebilirlik noktaları:**  
  
- <xref:System.UriTemplate>  
  
- <xref:System.UriTemplateTable>  
  
- <xref:System.ServiceModel.Dispatcher.QueryStringConverter>  
  
- <xref:System.ServiceModel.Dispatcher.WebHttpDispatchOperationSelector>  
  
## <a name="aspnetcacheprofileattribute"></a>AspNetCacheProfileAttribute  
 <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, bir hizmet işlemine uygulandığında, ASP .NET Çıkış önbelleğindeki işlemden yanıtları önbelleğe almak için kullanılması gereken yapılandırma dosyasında ASP.NET çıktı önbelleği profilini gösterir. Bu özellik, yapılandırma dosyasında önbellek ayarlarını belirten önbellek profili adı yalnızca bir parametre alır.  
  
## <a name="webgetattribute"></a>'A  
 <xref:System.ServiceModel.Web.WebGetAttribute> özniteliği, HTTP GET isteklerine yanıt veren bir hizmet işlemini işaretlemek için kullanılır. İşlem açıklamasına meta veri ekleyen pasif bir işlem davranışıdır (<xref:System.ServiceModel.Description.IOperationBehavior> Yöntemler hiçbir şey yapmaz). İşlem açıklamasında bu meta verileri (özellikle <xref:System.ServiceModel.Description.WebHttpBehavior>) sunan bir davranış, hizmetin davranış koleksiyonuna eklendiği için <xref:System.ServiceModel.Web.WebGetAttribute> uygulanması etkisizdir. <xref:System.ServiceModel.Web.WebGetAttribute> özniteliği aşağıdaki tabloda gösterilen isteğe bağlı parametreleri alır.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`BodyStyle`|Hizmet işleminden gönderilen ve alınan isteklerin ve yanıtların bir şekilde sarılıp döndürülmeyeceğini denetler ve özniteliği öğesine uygulanır.|  
|`RequestFormat`|İstek iletilerinin nasıl biçimlendirildiğini denetler.|  
|`ResponseFormat`|Yanıt iletilerinin nasıl biçimlendirildiğini denetler.|  
|`UriTemplate`|Öznitelik uygulandığı HTTP isteklerinin hangi HTTP isteklerinin hizmet işlemine eşlendiğini denetleyen URI şablonunu belirtir.|  
  
## <a name="webhttpbinding"></a>WebHttpBinding  
 <xref:System.ServiceModel.WebHttpBinding> sınıfı, <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>kullanarak XML, JSON ve ham ikili veriler için destek içerir. <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpTransportBindingElement> ve <xref:System.ServiceModel.WebHttpSecurity> nesnesinden oluşur. <xref:System.ServiceModel.WebHttpBinding>, <xref:System.ServiceModel.Description.WebHttpBehavior>birlikte kullanılmak üzere tasarlanmıştır.  
  
## <a name="webinvokeattribute"></a>Webvokeattribute  
 <xref:System.ServiceModel.Web.WebInvokeAttribute> özniteliği <xref:System.ServiceModel.Web.WebGetAttribute>benzerdir, ancak bir hizmet işlemini GET dışındaki HTTP isteklerine yanıt veren bir hizmet işlemi olarak işaretlemek için kullanılır. İşlem açıklamasına meta veri ekleyen pasif bir işlem davranışıdır (<xref:System.ServiceModel.Description.IOperationBehavior> Yöntemler hiçbir şey yapmaz). İşlem açıklamasında bu meta verileri (özellikle <xref:System.ServiceModel.Description.WebHttpBehavior>) sunan bir davranış, hizmetin davranış koleksiyonuna eklendiği için <xref:System.ServiceModel.Web.WebInvokeAttribute> uygulanması etkisizdir.  
  
 <xref:System.ServiceModel.Web.WebInvokeAttribute> özniteliği aşağıdaki tabloda gösterilen isteğe bağlı parametreleri alır.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`BodyStyle`|Hizmet işleminden gönderilen ve alınan isteklerin ve yanıtların bir şekilde sarılıp döndürülmeyeceğini denetler ve özniteliği öğesine uygulanır.|  
|`Method`|Hizmet işleminin eşlendiği HTTP yöntemini belirtir.|  
|`RequestFormat`|İstek iletilerinin nasıl biçimlendirildiğini denetler.|  
|`ResponseFormat`|Yanıt iletilerinin nasıl biçimlendirildiğini denetler.|  
|`UriTemplate`|Hangi GET isteklerinin hangi GET isteklerini eşleştirdiğini denetleyen URI şablonunu belirtir özniteliği öğesine uygulanır.|  
  
## <a name="uritemplate"></a>UriTemplate  
 <xref:System.UriTemplate> sınıfı, yapısal olarak benzer bir URI kümesi tanımlamanızı sağlar. Şablonlar, bir yol ve bir sorgu olmak üzere iki bölümden oluşur. Bir yol, eğik çizgiyle (/) ayrılmış bir dizi kesimden oluşur. Her segmentde bir sabit değer, bir değişken değeri (küme ayraçları [{}] içinde yazılmış, tam olarak bir segmentin içeriğiyle sınırlı) veya bir joker karakter\*("yolun geri kalanı") ile eşleşen bir joker karakter olabilir. Sorgu ifadesi tamamen atlanabilir. Varsa, sıralanmamış bir ad/değer çiftleri serisi belirtir. Sorgu ifadesinin öğeleri, sabit değer çiftleri (? x = 2) veya değişken çiftleri (? x = {*Value*}) olabilir. Eşlenmemiş değerlere izin verilmez. <xref:System.UriTemplate>, belirli URI 'leri veya URI gruplarını hizmet işlemlerine eşlemek için WCF WEB HTTP programlama modeli tarafından dahili olarak kullanılır.  
  
## <a name="uritemplatetable"></a>UriTemplateTable  
 <xref:System.UriTemplateTable> sınıfı, geliştiricinin seçme nesnesine göre bağlantılı <xref:System.UriTemplate> nesnelerinin ilişkilendirilebilir bir kümesini temsil eder. Bu, aday Tekdüzen Kaynak tanımlayıcılarını (URI 'Ler) küme içindeki şablonlara karşı eşleştirmenizi ve eşleşen şablonlarla ilişkili verileri almanızı sağlar. <xref:System.UriTemplateTable>, belirli URI 'leri veya URI gruplarını hizmet işlemlerine eşlemek için WCF WEB HTTP programlama modeli tarafından dahili olarak kullanılır.  
  
## <a name="webservicehost"></a>Web ServiceHost  
 <xref:System.ServiceModel.Web.WebServiceHost>, SOAP olmayan bir Web stili hizmetin barındırlanmasını kolaylaştırmak için <xref:System.ServiceModel.ServiceHost> genişletir. Hizmet açıklamasında hiçbir uç nokta bul<xref:System.ServiceModel.Web.WebServiceHost>, otomatik olarak hizmetin temel adresinde bir varsayılan uç nokta oluşturur. Varsayılan HTTP uç noktası oluşturulurken <xref:System.ServiceModel.Web.WebServiceHost>, HTTP Yardım sayfasını ve Web Hizmetleri Açıklama Dili (WSDL) Al işlevini de devre dışı bırakarak meta veri uç noktasının varsayılan HTTP uç noktasına müdahale etmez. <xref:System.ServiceModel.Web.WebServiceHost> Ayrıca, <xref:System.ServiceModel.WebHttpBinding> kullanan tüm uç noktaların gerekli <xref:System.ServiceModel.Description.WebHttpBehavior> eklenmiş olmasını da sağlar. Son olarak, <xref:System.ServiceModel.Web.WebServiceHost>, güvenli bir sanal dizinde kullanıldığında bitiş noktasının bağlamasını ilişkili Internet Information Services (IIS) güvenlik ayarlarıyla çalışacak şekilde otomatik olarak yapılandırır.  
  
## <a name="webservicehostfactory"></a>WebServiceHostFactory  
 <xref:System.ServiceModel.Activation.WebServiceHostFactory> sınıfı, bir hizmet Internet Information Services (IIS) veya Windows Işlem etkinleştirme hizmeti (WAS) altında barındırıldığı zaman dinamik olarak bir <xref:System.ServiceModel.Web.WebServiceHost> oluşturmak için kullanılır. Barındırma uygulamasının <xref:System.ServiceModel.Web.WebServiceHost>örnekladığı şirket içinde barındırılan bir hizmetten farklı olarak, IIS altında barındırılan hizmetler veya hizmet için <xref:System.ServiceModel.Web.WebServiceHost> oluşturmak üzere bu sınıfı kullanmıştı. <xref:System.ServiceModel.Activation.WebServiceHostFactory.CreateServiceHost%28System.Type%2CSystem.Uri%5B%5D%29> yöntemi, hizmet için gelen istek alındığında çağrılır.  
  
## <a name="webhttpbehavior"></a>WebHttpBehavior  
 <xref:System.ServiceModel.Description.WebHttpBehavior> sınıfı, hizmet modeli katmanında Web stil hizmeti desteği için gerekli olan biçimlendirme, işlem seçicileri ve benzeri işlemleri sağlar. Bu, bir uç nokta davranışı olarak uygulanır (<xref:System.ServiceModel.WebHttpBinding>ile birlikte kullanılır) ve aynı hizmet uygulamasının hem SOAP hem de POX uç noktalarını kullanıma sunmasına olanak tanıyan her bir uç nokta için biçimlendirme ve işlem seçicilerin belirtilmesini sağlar.  
  
### <a name="extending-webhttpbehavior"></a>WebHttpBehavior 'ı genişletme  
 <xref:System.ServiceModel.Description.WebHttpBehavior>, bir dizi sanal yöntem kullanılarak Genişletilebilir: <xref:System.ServiceModel.Description.WebHttpBehavior.GetOperationSelector%28System.ServiceModel.Description.ServiceEndpoint%29>, <xref:System.ServiceModel.Description.WebHttpBehavior.GetReplyClientFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>, <xref:System.ServiceModel.Description.WebHttpBehavior.GetRequestClientFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>, <xref:System.ServiceModel.Description.WebHttpBehavior.GetReplyDispatchFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>ve <xref:System.ServiceModel.Description.WebHttpBehavior.GetRequestDispatchFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>. Geliştiriciler <xref:System.ServiceModel.Description.WebHttpBehavior> bir sınıf türetebilir ve varsayılan davranışı özelleştirmek için bu yöntemleri geçersiz kılabilir.  
  
 <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>, <xref:System.ServiceModel.Description.WebHttpBehavior>genişletme örneğidir. <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>, Windows Communication Foundation (WCF) uç noktalarının tarayıcı tabanlı bir ASP.NET AJAX istemcisinden HTTP istekleri almasına olanak sağlar. [Http post kullanan AJAX Hizmeti](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) , bu genişletilebilirlik noktasını kullanmanın bir örneğidir.  
  
> [!WARNING]
> <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>kullanılırken, <xref:System.ServiceModel.Web.WebGetAttribute> veya <xref:System.ServiceModel.Web.WebInvokeAttribute> öznitelikleri içinde <xref:System.UriTemplate> desteklenmez.  
  
## <a name="webhttpdispatchoperationselector"></a>WebHttpDispatchOperationSelector  
 <xref:System.ServiceModel.Dispatcher.WebHttpDispatchOperationSelector> sınıfı, hizmet işlemlerine çağrı göndermek için <xref:System.UriTemplate> ve <xref:System.UriTemplateTable> sınıfları kullanır.  
  
## <a name="compatibility"></a>Uyumluluk  
 WCF WEB HTTP programlama modeli SOAP tabanlı iletiler kullanmaz ve bu nedenle WS-* protokollerini desteklemez. Ancak, aynı sözleşmeyi iki farklı uç noktayla kullanıma sunabilirsiniz: biri SOAP ve diğer SOAP kullanmayan diğeri. Bir örnek için bkz. [nasıl yapılır: bir SÖZLEŞMEYI SOAP ve Web istemcilerine](../../../../docs/framework/wcf/feature-details/how-to-expose-a-contract-to-soap-and-web-clients.md) sunma.  
  
## <a name="security"></a>Güvenlik  

WCF WEB HTTP programlama modeli WS-* protokollerini desteklemediğinden, WCF WEB HTTP programlama modeli üzerinde oluşturulmuş bir Web hizmetini güvenli hale getirmenin tek yolu, hizmetinizi SSL kullanarak kullanıma sunmasıdır. IIS 7,0 ile SSL ayarlama hakkında daha fazla bilgi için bkz. [IIS 'de SSL uygulama](https://support.microsoft.com/help/299875/how-to-implement-ssl-in-iis).
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
- <xref:System.ServiceModel.Web.WebInvokeAttribute>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- <xref:System.ServiceModel.Dispatcher.WebHttpDispatchOperationSelector>
- [WCF Web HTTP Programlama Modeli Genel Bakış](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
