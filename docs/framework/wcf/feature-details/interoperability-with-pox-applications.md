---
title: POX Uygulamaları ile Birlikte Çalışabilirlik
ms.date: 03/30/2017
ms.assetid: 449276b8-4633-46f0-85c9-81f01d127636
ms.openlocfilehash: 7522233723b6b91d5a7b27d3f82ca328e29ce3f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33494206"
---
# <a name="interoperability-with-pox-applications"></a>POX Uygulamaları ile Birlikte Çalışabilirlik
"Düz eski XML" (POX) uygulamalar, yalnızca bir SOAP Zarfı içinde içine alınmamış XML uygulama verileri içeren ham HTTP ileti değiş tokuşu ile iletişim. Windows Communication Foundation (WCF) hizmetlerini ve POX iletileri kullanan istemciler sağlayabilir. Hizmeti, WCF Hizmetleri Web tarayıcıları gibi istemcilere uç noktalarını kullanıma sunar ve POX ileti gönderme ve alma komut dosyası dillerini uygulamak için kullanılabilir. İstemcide, WCF programlama modeli POX tabanlı Hizmetleri ile iletişim kuran istemciler uygulamak için kullanılabilir.  
  
> [!NOTE]
>  Bu belge için ilk olarak yazılmıştır [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0.  [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.5 POX uygulamaları ile çalışmak için yerleşik desteğe sahiptir. Bkz: hakkında daha fazla bilgi için [WCF Web HTTP programlama modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
  
## <a name="pox-programming-with-wcf"></a>WCF ile POX programlama  
 POX iletileri kullanarak HTTP üzerinden iletişim kuracak WCF hizmetleri bir [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
```xml  
<customBinding>  
   <binding name="poxServerBinding">  
       <textMessageEncoding messageVersion="None" />  
       <httpTransport />  
   </binding>  
</customBinding>  
```  
  
 Bu özel bağlama iki öğeleri içerir:  
  
-   [ \<HttpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) ve  
  
-   [ \<TextMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).  
  
 WCF metin ileti Kodlayıcı kullanacak şekilde yapılandırılmış özel standart <xref:System.ServiceModel.Channels.MessageVersion.None%2A> SAOP zarfına Sarmalanan değil gelen XML ileti yükü işlemek imkan tanıyan değeri.  
  
 POX iletileri kullanarak HTTP üzerinden iletişim kuracak WCF istemcileri (aşağıdaki kesinlik temelli kodda gösterildiği) benzer bir bağlama kullanın.  
  
```  
private static Binding CreatePoxBinding()  
{  
    TextMessageEncodingBindingElement encoder =   
    new TextMessageEncodingBindingElement( MessageVersion.None, Encoding.UTF8 );  
    HttpTransportBindingElement transport = new HttpTransportBindingElement();  
    transport.ManualAddressing = true;  
    return new CustomBinding( new BindingElement[] { encoder, transport } );  
}   
```  
  
 POX istemcileri iletileri için gönderdikleri URI'ler açıkça belirtmeniz gerekir çünkü bunlar genellikle yapılandırmalısınız <xref:System.ServiceModel.Channels.HttpTransportBindingElement> ayarlayarak el ile adresleme modu için <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A> özelliğine `true` öğesindeki. Bu uygulama kodu tarafından açıkça ele alınması gereken iletileri sağlar ve yeni bir oluşturmak için gerekli değil <xref:System.ServiceModel.ChannelFactory> her zaman bir uygulama için farklı bir HTTP URI ileti gönderir.  
  
 POX iletileri önemli protokol bilgileri iletmek için SOAP üstbilgileri kullanmadığından, POX istemcileri ve Hizmetleri genellikle göndermek veya bir ileti almak için kullanılan temel alınan HTTP isteği parçalarını yönetme gerekir. HTTP üstbilgilerine ve durum kodları gibi HTTP özgü protokol bilgileri ortaya iki sınıflarıyla WCF programlama modeli:  
  
-   <xref:System.ServiceModel.Channels.HttpRequestMessageProperty>, HTTP yöntemi ve istek üstbilgileri gibi bir HTTP isteğiyle ilgili bilgileri içerir.  
  
-   <xref:System.ServiceModel.Channels.HttpResponseMessageProperty>, HTTP yanıtının HTTP durum kodu ve durum açıklaması gibi tüm HTTP yanıt üstbilgilerini gibi hakkında bilgiler içerir.  
  
 Aşağıdaki kod örneği için ele bir HTTP GET isteği iletisi oluşturulacağını gösterir http://localhost:8100/customers.  
  
```  
Message request = Message.CreateMessage( MessageVersion.None, String.Empty );  
request.Headers.To = "http://localhost:8100/customers";  
  
HttpRequestMessageProperty property = new HttpRequestMessageProperty();  
property.Method = "GET";  
property.SuppressEntityBody = true;  
request.Properties.Add( HttpRequestMessageProperty.Name, property );  
```  
  
 İlk olarak, boş bir istek <xref:System.ServiceModel.Channels.Message> çağrılarak oluşturulan <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29>. <xref:System.ServiceModel.Channels.MessageVersion.None%2A> Parametresi SOAP Zarfı gerekli olmadığını göstermek için kullanılır ve <xref:System.String.Empty> parametresi eylem olarak geçirilir. İstek iletisi ayarlayarak ardından ele <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> üstbilgi İstenen URI. Daha sonra bir <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> oluşturulur ve <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> HTTP fiili GET yöntemi ayarlanır ve <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> ayarlanır `true` hiçbir veri giden HTTP istek iletisinin gövdesinde gönderilmesi gerektiğini belirtmek için. Son olarak, istek özelliği eklenen <xref:System.ServiceModel.Channels.Message.Properties%2A> nasıl HTTP taşıma isteği gönderir etkileyebilir şekilde istek iletisi koleksiyonu. İletiyi daha sonra uygun örneği gönderilmek üzere hazır <xref:System.ServiceModel.Channels.IRequestChannel>.  
  
 Benzer teknikleri ayıklamak için hizmette kullanılabilir <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> gelen ileti ve yapı yanıt.
