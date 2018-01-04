---
title: "POX Uygulamaları ile Birlikte Çalışabilirlik"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 449276b8-4633-46f0-85c9-81f01d127636
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8cb7e209397e593ae1fd81c2bc2552e54a32adf0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="interoperability-with-pox-applications"></a>POX Uygulamaları ile Birlikte Çalışabilirlik
"Düz eski XML" (POX) uygulamalar, yalnızca bir SOAP Zarfı içinde içine alınmamış XML uygulama verileri içeren ham HTTP ileti değiş tokuşu ile iletişim. [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]Hizmetleri ve POX iletileri kullanan istemciler sağlayabilir. Hizmetinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web tarayıcıları ve POX ileti gönderme ve alma komut dosyası dilleri gibi istemcilere uç noktalarını kullanıma sunar Hizmetleri uygulamak için kullanılabilir. İstemci üzerindeki [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] programlama modeli, POX tabanlı Hizmetleri ile iletişim kuran istemciler uygulamak için kullanılabilir.  
  
> [!NOTE]
>  Bu belge için ilk olarak yazılmıştır [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0.  [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]3.5 POX uygulamaları ile çalışmak için yerleşik desteğe sahiptir. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]bkz: [WCF Web HTTP programlama modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
  
## <a name="pox-programming-with-wcf"></a>WCF ile POX programlama  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]POX iletileri kullanarak HTTP üzerinden iletişim kuracak Hizmetleri bir [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
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
  
 Standart [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] metin ileti Kodlayıcı kullanacak şekilde yapılandırılmış özel <xref:System.ServiceModel.Channels.MessageVersion.None%2A> SAOP zarfına Sarmalanan değil gelen XML ileti yükü işlemek imkan tanıyan değeri.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]POX iletileri kullanarak HTTP üzerinden iletişim kuran istemciler (aşağıdaki kesinlik temelli kodda gösterildiği) benzer bir bağlama kullanın.  
  
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
  
 POX iletileri önemli protokol bilgileri iletmek için SOAP üstbilgileri kullanmadığından, POX istemcileri ve Hizmetleri genellikle göndermek veya bir ileti almak için kullanılan temel alınan HTTP isteği parçalarını yönetme gerekir. HTTP üstbilgilerine ve durum kodları gibi HTTP özgü protokol bilgileri ortaya içinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iki sınıflarıyla programlama modeli:  
  
-   <xref:System.ServiceModel.Channels.HttpRequestMessageProperty>, HTTP yöntemi ve istek üstbilgileri gibi bir HTTP isteğiyle ilgili bilgileri içerir.  
  
-   <xref:System.ServiceModel.Channels.HttpResponseMessageProperty>, HTTP yanıtının HTTP durum kodu ve durum açıklaması gibi tüm HTTP yanıt üstbilgilerini gibi hakkında bilgiler içerir.  
  
 Aşağıdaki kod örneğinde yönelik bir HTTP GET isteği iletisi http://localhost:8100/müşterilere oluşturulacağını gösterir.  
  
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
