---
title: WCF Web HTTP Programlama Nesnesi Modeli
ms.date: 03/30/2017
ms.assetid: ed96b5fc-ca2c-4b0d-bdba-d06b77c3cb2a
ms.openlocfilehash: 43ec16927c703ca373eaa4299093503b2fab2266
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988569"
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
 <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, Bir hizmet işlemine uygulandığında, ASP .NET Çıkış önbelleğindeki işlemden yanıtları önbelleğe almak için kullanılması gereken yapılandırma dosyasında ASP.net çıktı önbelleği profilini gösterir. Bu özellik, yapılandırma dosyasında önbellek ayarlarını belirten önbellek profili adı yalnızca bir parametre alır.  
  
## <a name="webgetattribute"></a>'A  
 Özniteliği <xref:System.ServiceModel.Web.WebGetAttribute> , http get isteklerine yanıt veren bir hizmet işlemini işaretlemek için kullanılır. İşlem açıklamasına meta veri ekleyen pasif bir işlem <xref:System.ServiceModel.Description.IOperationBehavior> davranışıdır (hiçbir şey yoktur). Öğesinin uygulanması <xref:System.ServiceModel.Web.WebGetAttribute> , işlem açıklamasında bu meta verileri (özellikle <xref:System.ServiceModel.Description.WebHttpBehavior>,) hizmetin davranış koleksiyonuna eklendiği takdirde hiçbir etkiye sahip değildir. <xref:System.ServiceModel.Web.WebGetAttribute> Öznitelik, aşağıdaki tabloda gösterilen isteğe bağlı parametreleri alır.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`BodyStyle`|Hizmet işleminden gönderilen ve alınan isteklerin ve yanıtların bir şekilde sarılıp döndürülmeyeceğini denetler ve özniteliği öğesine uygulanır.|  
|`RequestFormat`|İstek iletilerinin nasıl biçimlendirildiğini denetler.|  
|`ResponseFormat`|Yanıt iletilerinin nasıl biçimlendirildiğini denetler.|  
|`UriTemplate`|Öznitelik uygulandığı HTTP isteklerinin hangi HTTP isteklerinin hizmet işlemine eşlendiğini denetleyen URI şablonunu belirtir.|  
  
## <a name="webhttpbinding"></a>WebHttpBinding  
 <xref:System.ServiceModel.WebHttpBinding> Sınıfı ,<xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>kullanarak XML, JSON ve ham ikili veriler için destek içerir. <xref:System.ServiceModel.Channels.HttpsTransportBindingElement> ,<xref:System.ServiceModel.Channels.HttpTransportBindingElement> Ve bir<xref:System.ServiceModel.WebHttpSecurity> nesnesinden oluşur. , İle birlikte kullanılmak üzere tasarlanmıştır. <xref:System.ServiceModel.Description.WebHttpBehavior> <xref:System.ServiceModel.WebHttpBinding>  
  
## <a name="webinvokeattribute"></a>Webvokeattribute  
 <xref:System.ServiceModel.Web.WebInvokeAttribute> Özniteliği ilebenzerdir,ancakbirhizmetişleminiGetdışındakihttpisteklerineyanıtverenbirhizmetişlemi<xref:System.ServiceModel.Web.WebGetAttribute>olarak işaretlemek için kullanılır. İşlem açıklamasına meta veri ekleyen pasif bir işlem <xref:System.ServiceModel.Description.IOperationBehavior> davranışıdır (hiçbir şey yoktur). Öğesinin uygulanması <xref:System.ServiceModel.Web.WebInvokeAttribute> , işlem açıklamasında bu meta verileri (özellikle <xref:System.ServiceModel.Description.WebHttpBehavior>,) hizmetin davranış koleksiyonuna eklendiği takdirde hiçbir etkiye sahip değildir.  
  
 <xref:System.ServiceModel.Web.WebInvokeAttribute> Öznitelik, aşağıdaki tabloda gösterilen isteğe bağlı parametreleri alır.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`BodyStyle`|Hizmet işleminden gönderilen ve alınan isteklerin ve yanıtların bir şekilde sarılıp döndürülmeyeceğini denetler ve özniteliği öğesine uygulanır.|  
|`Method`|Hizmet işleminin eşlendiği HTTP yöntemini belirtir.|  
|`RequestFormat`|İstek iletilerinin nasıl biçimlendirildiğini denetler.|  
|`ResponseFormat`|Yanıt iletilerinin nasıl biçimlendirildiğini denetler.|  
|`UriTemplate`|Hangi GET isteklerinin hangi GET isteklerini eşleştirdiğini denetleyen URI şablonunu belirtir özniteliği öğesine uygulanır.|  
  
## <a name="uritemplate"></a>UriTemplate  
 Sınıfı <xref:System.UriTemplate> , yapısal olarak benzer bir URI kümesi tanımlamanızı sağlar. Şablonlar, bir yol ve bir sorgu olmak üzere iki bölümden oluşur. Bir yol, eğik çizgiyle (/) ayrılmış bir dizi kesimden oluşur. Her segment bir sabit değere sahip olabilir, bir değişken değeri (küme ayraçları [{}] içinde yazılmış, tam olarak bir segmentin içeriğiyle sınırlı) veya bir joker karakter ("yolun geri kalanı" ile eşleşen yıldız\*[] olarak yazılmış), şurada görünmelidir: Yolun sonu. Sorgu ifadesi tamamen atlanabilir. Varsa, sıralanmamış bir ad/değer çiftleri serisi belirtir. Sorgu ifadesinin öğeleri, sabit değer çiftleri (? x = 2) veya değişken çiftleri (? x = {*Value*}) olabilir. Eşlenmemiş değerlere izin verilmez. <xref:System.UriTemplate>, belirli URI 'leri veya URI gruplarını hizmet işlemlerine eşlemek için WCF WEB HTTP programlama modeli tarafından dahili olarak kullanılır.  
  
## <a name="uritemplatetable"></a>UriTemplateTable  
 Sınıfı, geliştiricinin seçme nesnesine göre ilişkili <xref:System.UriTemplate> bir nesne kümesini temsil eder. <xref:System.UriTemplateTable> Bu, aday Tekdüzen Kaynak tanımlayıcılarını (URI 'Ler) küme içindeki şablonlara karşı eşleştirmenizi ve eşleşen şablonlarla ilişkili verileri almanızı sağlar. <xref:System.UriTemplateTable>, belirli URI 'leri veya URI gruplarını hizmet işlemlerine eşlemek için WCF WEB HTTP programlama modeli tarafından dahili olarak kullanılır.  
  
## <a name="webservicehost"></a>Web ServiceHost  
 <xref:System.ServiceModel.Web.WebServiceHost>SOAP olmayan Web stili bir hizmetin barındırlanmasını kolaylaştırmak içinöğesinigenişletir.<xref:System.ServiceModel.ServiceHost> Hizmet açıklamasında hiçbir uç nokta bulduğunda,otomatikolarakhizmetintemeladresindebirvarsayılanuçnoktaoluşturur.<xref:System.ServiceModel.Web.WebServiceHost> Varsayılan HTTP uç noktası oluşturulurken Ayrıca, http <xref:System.ServiceModel.Web.WebServiceHost> yardım sayfasını ve Web Hizmetleri Açıklama Dili (wsdl) Al işlevini devre dışı bırakır. böylece, meta veri uç noktasının varsayılan HTTP uç noktasına müdahale etmez. <xref:System.ServiceModel.Web.WebServiceHost>Ayrıca, kullanan <xref:System.ServiceModel.WebHttpBinding> tüm uç noktaların gerekli <xref:System.ServiceModel.Description.WebHttpBehavior> eklenmiş olmasını sağlar. Son olarak <xref:System.ServiceModel.Web.WebServiceHost> , güvenli bir sanal dizinde kullanıldığında bitiş noktasının bağlamasını ilişkili Internet Information Services (IIS) güvenlik ayarlarıyla çalışacak şekilde otomatik olarak yapılandırır.  
  
## <a name="webservicehostfactory"></a>WebServiceHostFactory  
 Sınıfı, bir hizmet Internet Information Services (IIS) <xref:System.ServiceModel.Web.WebServiceHost> veya Windows işlem etkinleştirme hizmeti (was) altında barındırıldığı zaman dinamik olarak oluşturmak için kullanılır. <xref:System.ServiceModel.Activation.WebServiceHostFactory> Barındırma uygulamasının <xref:System.ServiceModel.Web.WebServiceHost>tarafından oluşturulduğu şirket içinde barındırılan bir hizmetin aksine, IIS altında barındırılan hizmetler veya hizmeti <xref:System.ServiceModel.Web.WebServiceHost> oluşturmak için bu sınıfı kullanın. <xref:System.ServiceModel.Activation.WebServiceHostFactory.CreateServiceHost%28System.Type%2CSystem.Uri%5B%5D%29> Yöntemi, hizmet için gelen istek alındığında çağrılır.  
  
## <a name="webhttpbehavior"></a>WebHttpBehavior  
 <xref:System.ServiceModel.Description.WebHttpBehavior> Sınıfı, hizmet modeli katmanında Web stili hizmet desteği için gereken, gerekli biçimleri, işlem seçicileri ve benzerlerini sağlar. Bu bir uç nokta davranışı olarak uygulanır (ile <xref:System.ServiceModel.WebHttpBinding>birlikte kullanılır) ve aynı hizmet uygulamasının hem SOAP hem de POX uç noktalarını kullanıma sunmasına olanak tanıyan her bir uç nokta için biçimlendirme ve işlem seçicilerin belirtilmesini sağlar.  
  
### <a name="extending-webhttpbehavior"></a>WebHttpBehavior 'ı genişletme  
 <xref:System.ServiceModel.Description.WebHttpBehavior>, bir dizi sanal yöntem kullanılarak Genişletilebilir: <xref:System.ServiceModel.Description.WebHttpBehavior.GetOperationSelector%28System.ServiceModel.Description.ServiceEndpoint%29>, <xref:System.ServiceModel.Description.WebHttpBehavior.GetReplyClientFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>, <xref:System.ServiceModel.Description.WebHttpBehavior.GetRequestClientFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29> <xref:System.ServiceModel.Description.WebHttpBehavior.GetReplyDispatchFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>, ve <xref:System.ServiceModel.Description.WebHttpBehavior.GetRequestDispatchFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>. Geliştiriciler, ' dan <xref:System.ServiceModel.Description.WebHttpBehavior> bir sınıf türetebilir ve varsayılan davranışı özelleştirmek için bu yöntemleri geçersiz kılabilir.  
  
 , <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> Genişletme<xref:System.ServiceModel.Description.WebHttpBehavior>örneğidir. <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>Windows Communication Foundation (WCF) uç noktalarının tarayıcı tabanlı bir ASP.NET AJAX istemcisinden HTTP istekleri almasını sağlar. [Http post kullanan AJAX Hizmeti](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) , bu genişletilebilirlik noktasını kullanmanın bir örneğidir.  
  
> [!WARNING]
> Kullanırken <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>, <xref:System.UriTemplate> <xref:System.ServiceModel.Web.WebGetAttribute> veya öznitelikleriiçindedesteklenmez<xref:System.ServiceModel.Web.WebInvokeAttribute> .  
  
## <a name="webhttpdispatchoperationselector"></a>WebHttpDispatchOperationSelector  
 Sınıfı <xref:System.ServiceModel.Dispatcher.WebHttpDispatchOperationSelector> , hizmet <xref:System.UriTemplate> işlemlerine <xref:System.UriTemplateTable> çağrı göndermek için ve sınıflarını kullanır.  
  
## <a name="compatibility"></a>Uyumluluk  
 WCF WEB HTTP programlama modeli SOAP tabanlı iletiler kullanmaz ve bu nedenle WS-* protokollerini desteklemez. Ancak, aynı sözleşmeyi iki farklı uç noktayla kullanıma sunabilirsiniz: biri SOAP ve diğer SOAP kullanmayan diğeri. Bkz [. nasıl yapılır: Bir örnek için bir sözleşmeyi SOAP ve Web](../../../../docs/framework/wcf/feature-details/how-to-expose-a-contract-to-soap-and-web-clients.md) istemcilerine sunun.  
  
## <a name="security"></a>Güvenlik  
 WCF WEB HTTP programlama modeli WS-* protokollerini desteklemediğinden, WCF WEB HTTP programlama modeli üzerinde oluşturulmuş bir Web hizmetini güvenli hale getirmenin tek yolu, hizmetinizi SSL kullanarak kullanıma sunmasıdır. IIS 7,0 ile SSL ayarlama hakkında daha fazla bilgi için bkz. [IIS 'de SSL uygulama](https://go.microsoft.com/fwlink/?LinkId=131613)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
- <xref:System.ServiceModel.Web.WebInvokeAttribute>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- <xref:System.ServiceModel.Dispatcher.WebHttpDispatchOperationSelector>
- [WCF Web HTTP Programlama Modeli Genel Bakış](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
