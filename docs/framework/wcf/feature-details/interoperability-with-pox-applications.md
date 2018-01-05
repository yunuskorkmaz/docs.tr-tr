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
# <a name="interoperability-with-pox-applications"></a><span data-ttu-id="71beb-102">POX Uygulamaları ile Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="71beb-102">Interoperability with POX Applications</span></span>
<span data-ttu-id="71beb-103">"Düz eski XML" (POX) uygulamalar, yalnızca bir SOAP Zarfı içinde içine alınmamış XML uygulama verileri içeren ham HTTP ileti değiş tokuşu ile iletişim.</span><span class="sxs-lookup"><span data-stu-id="71beb-103">"Plain Old XML" (POX) applications communicate by exchanging raw HTTP messages that contain only XML application data that is not enclosed within a SOAP envelope.</span></span> [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="71beb-104">Hizmetleri ve POX iletileri kullanan istemciler sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="71beb-104"> can provide both services and clients that use POX messages.</span></span> <span data-ttu-id="71beb-105">Hizmetinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web tarayıcıları ve POX ileti gönderme ve alma komut dosyası dilleri gibi istemcilere uç noktalarını kullanıma sunar Hizmetleri uygulamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="71beb-105">On the service, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] can be used to implement services that expose endpoints to clients such as Web browsers and scripting languages that send and receive POX messages.</span></span> <span data-ttu-id="71beb-106">İstemci üzerindeki [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] programlama modeli, POX tabanlı Hizmetleri ile iletişim kuran istemciler uygulamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="71beb-106">On the client, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] programming model can be used to implement clients that communicate with POX-based services.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="71beb-107">Bu belge için ilk olarak yazılmıştır [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0.</span><span class="sxs-lookup"><span data-stu-id="71beb-107">This document was originally written for the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0.</span></span>  [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]<span data-ttu-id="71beb-108">3.5 POX uygulamaları ile çalışmak için yerleşik desteğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="71beb-108"> 3.5 has built-in support for working with POX applications.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="71beb-109">bkz: [WCF Web HTTP programlama modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)</span><span class="sxs-lookup"><span data-stu-id="71beb-109"> see [WCF Web HTTP Programming Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)</span></span>  
  
## <a name="pox-programming-with-wcf"></a><span data-ttu-id="71beb-110">WCF ile POX programlama</span><span class="sxs-lookup"><span data-stu-id="71beb-110">POX Programming with WCF</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="71beb-111">POX iletileri kullanarak HTTP üzerinden iletişim kuracak Hizmetleri bir [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="71beb-111"> services that communicate over HTTP using POX messages use a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
```xml  
<customBinding>  
   <binding name="poxServerBinding">  
       <textMessageEncoding messageVersion="None" />  
       <httpTransport />  
   </binding>  
</customBinding>  
```  
  
 <span data-ttu-id="71beb-112">Bu özel bağlama iki öğeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="71beb-112">This custom binding contains two elements:</span></span>  
  
-   <span data-ttu-id="71beb-113">[ \<HttpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) ve</span><span class="sxs-lookup"><span data-stu-id="71beb-113">The [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) and</span></span>  
  
-   <span data-ttu-id="71beb-114">[ \<TextMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span><span class="sxs-lookup"><span data-stu-id="71beb-114">The [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span></span>  
  
 <span data-ttu-id="71beb-115">Standart [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] metin ileti Kodlayıcı kullanacak şekilde yapılandırılmış özel <xref:System.ServiceModel.Channels.MessageVersion.None%2A> SAOP zarfına Sarmalanan değil gelen XML ileti yükü işlemek imkan tanıyan değeri.</span><span class="sxs-lookup"><span data-stu-id="71beb-115">The standard [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Text Message Encoder is specially configured to use the <xref:System.ServiceModel.Channels.MessageVersion.None%2A> value, which allows it to process XML message payloads that do not arrive wrapped in a SOAP envelope.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="71beb-116">POX iletileri kullanarak HTTP üzerinden iletişim kuran istemciler (aşağıdaki kesinlik temelli kodda gösterildiği) benzer bir bağlama kullanın.</span><span class="sxs-lookup"><span data-stu-id="71beb-116"> clients that communicate over HTTP using POX messages use a similar binding (shown in the following imperative code).</span></span>  
  
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
  
 <span data-ttu-id="71beb-117">POX istemcileri iletileri için gönderdikleri URI'ler açıkça belirtmeniz gerekir çünkü bunlar genellikle yapılandırmalısınız <xref:System.ServiceModel.Channels.HttpTransportBindingElement> ayarlayarak el ile adresleme modu için <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A> özelliğine `true` öğesindeki.</span><span class="sxs-lookup"><span data-stu-id="71beb-117">Because POX clients must explicitly specify the URIs to which they send messages, they usually must configure the <xref:System.ServiceModel.Channels.HttpTransportBindingElement> to a manual addressing mode by setting the <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A> property to `true` on the element.</span></span> <span data-ttu-id="71beb-118">Bu uygulama kodu tarafından açıkça ele alınması gereken iletileri sağlar ve yeni bir oluşturmak için gerekli değil <xref:System.ServiceModel.ChannelFactory> her zaman bir uygulama için farklı bir HTTP URI ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="71beb-118">This allows messages to be addressed explicitly by application code and it is not necessary to create a new <xref:System.ServiceModel.ChannelFactory> every time an application sends a message to a different HTTP URI.</span></span>  
  
 <span data-ttu-id="71beb-119">POX iletileri önemli protokol bilgileri iletmek için SOAP üstbilgileri kullanmadığından, POX istemcileri ve Hizmetleri genellikle göndermek veya bir ileti almak için kullanılan temel alınan HTTP isteği parçalarını yönetme gerekir.</span><span class="sxs-lookup"><span data-stu-id="71beb-119">Because POX messages do not use SOAP headers to convey important protocol information, POX clients and services often must manipulate pieces of the underlying HTTP request used to send or receive a message.</span></span> <span data-ttu-id="71beb-120">HTTP üstbilgilerine ve durum kodları gibi HTTP özgü protokol bilgileri ortaya içinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iki sınıflarıyla programlama modeli:</span><span class="sxs-lookup"><span data-stu-id="71beb-120">HTTP-specific protocol information such as the HTTP headers and status codes are surfaced in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] programming model through two classes:</span></span>  
  
-   <span data-ttu-id="71beb-121"><xref:System.ServiceModel.Channels.HttpRequestMessageProperty>, HTTP yöntemi ve istek üstbilgileri gibi bir HTTP isteğiyle ilgili bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="71beb-121"><xref:System.ServiceModel.Channels.HttpRequestMessageProperty>, which contains information about the HTTP request, such as the HTTP method and request headers.</span></span>  
  
-   <span data-ttu-id="71beb-122"><xref:System.ServiceModel.Channels.HttpResponseMessageProperty>, HTTP yanıtının HTTP durum kodu ve durum açıklaması gibi tüm HTTP yanıt üstbilgilerini gibi hakkında bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="71beb-122"><xref:System.ServiceModel.Channels.HttpResponseMessageProperty>, which contains information about the HTTP response, such as the HTTP status code and status description, as well as any HTTP response headers.</span></span>  
  
 <span data-ttu-id="71beb-123">Aşağıdaki kod örneğinde yönelik bir HTTP GET isteği iletisi http://localhost:8100/müşterilere oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="71beb-123">The following code example shows how to create an HTTP GET request message that is addressed to http://localhost:8100/customers.</span></span>  
  
```  
Message request = Message.CreateMessage( MessageVersion.None, String.Empty );  
request.Headers.To = "http://localhost:8100/customers";  
  
HttpRequestMessageProperty property = new HttpRequestMessageProperty();  
property.Method = "GET";  
property.SuppressEntityBody = true;  
request.Properties.Add( HttpRequestMessageProperty.Name, property );  
```  
  
 <span data-ttu-id="71beb-124">İlk olarak, boş bir istek <xref:System.ServiceModel.Channels.Message> çağrılarak oluşturulan <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29>.</span><span class="sxs-lookup"><span data-stu-id="71beb-124">First, an empty request <xref:System.ServiceModel.Channels.Message> is created by calling <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29>.</span></span> <span data-ttu-id="71beb-125"><xref:System.ServiceModel.Channels.MessageVersion.None%2A> Parametresi SOAP Zarfı gerekli olmadığını göstermek için kullanılır ve <xref:System.String.Empty> parametresi eylem olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="71beb-125">The <xref:System.ServiceModel.Channels.MessageVersion.None%2A> parameter is used to indicate that a SOAP envelope is not required and <xref:System.String.Empty> parameter is passed as the Action.</span></span> <span data-ttu-id="71beb-126">İstek iletisi ayarlayarak ardından ele <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> üstbilgi İstenen URI.</span><span class="sxs-lookup"><span data-stu-id="71beb-126">The request message is then addressed by setting <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> header to the desired URI.</span></span> <span data-ttu-id="71beb-127">Daha sonra bir <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> oluşturulur ve <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> HTTP fiili GET yöntemi ayarlanır ve <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> ayarlanır `true` hiçbir veri giden HTTP istek iletisinin gövdesinde gönderilmesi gerektiğini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="71beb-127">Next, an <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> is created and the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> is set to the HTTP verb GET method and the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> is set to `true` to indicate that no data should be sent in the body of the outgoing HTTP request message.</span></span> <span data-ttu-id="71beb-128">Son olarak, istek özelliği eklenen <xref:System.ServiceModel.Channels.Message.Properties%2A> nasıl HTTP taşıma isteği gönderir etkileyebilir şekilde istek iletisi koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="71beb-128">Finally, the request property is added to the <xref:System.ServiceModel.Channels.Message.Properties%2A> collection of the request message so it can influence how the HTTP Transport sends the request.</span></span> <span data-ttu-id="71beb-129">İletiyi daha sonra uygun örneği gönderilmek üzere hazır <xref:System.ServiceModel.Channels.IRequestChannel>.</span><span class="sxs-lookup"><span data-stu-id="71beb-129">The message is then ready to be sent over an appropriate instance of the <xref:System.ServiceModel.Channels.IRequestChannel>.</span></span>  
  
 <span data-ttu-id="71beb-130">Benzer teknikleri ayıklamak için hizmette kullanılabilir <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> gelen ileti ve yapı yanıt.</span><span class="sxs-lookup"><span data-stu-id="71beb-130">Similar techniques can be used on the service to extract the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> from an incoming message and construct a response.</span></span>
