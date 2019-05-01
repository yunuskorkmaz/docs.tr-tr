---
title: POX uygulamaları ile birlikte çalışabilirlik
ms.date: 03/30/2017
ms.assetid: 449276b8-4633-46f0-85c9-81f01d127636
ms.openlocfilehash: b7fdb4e16bce52025515ced065d0f48cffb7fa3f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62046898"
---
# <a name="interoperability-with-pox-applications"></a><span data-ttu-id="3a0ad-102">POX uygulamaları ile birlikte çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="3a0ad-102">Interoperability with POX applications</span></span>

<span data-ttu-id="3a0ad-103">"Düz eski XML" (POX) uygulamalar, yalnızca bir SOAP Zarfı içinde içine XML uygulama verileri içeren ham HTTP ileti değiş tokuşu ile iletişim.</span><span class="sxs-lookup"><span data-stu-id="3a0ad-103">"Plain Old XML" (POX) applications communicate by exchanging raw HTTP messages that contain only XML application data that is not enclosed within a SOAP envelope.</span></span> <span data-ttu-id="3a0ad-104">Windows Communication Foundation (WCF) hizmetleri hem de POX iletileri kullanan istemciler sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="3a0ad-104">Windows Communication Foundation (WCF) can provide both services and clients that use POX messages.</span></span> <span data-ttu-id="3a0ad-105">Hizmette, WCF Hizmetleri'nin istemcilere Web tarayıcıları gibi uç noktalarını kullanıma sunar ve POX iletileri gönderip komut dosyası dilleri uygulamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3a0ad-105">On the service, WCF can be used to implement services that expose endpoints to clients such as Web browsers and scripting languages that send and receive POX messages.</span></span> <span data-ttu-id="3a0ad-106">İstemcide, WCF programlama modeli POX tabanlı hizmetler ile iletişim kuran istemciler uygulamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3a0ad-106">On the client, the WCF programming model can be used to implement clients that communicate with POX-based services.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3a0ad-107">Bu belge için özgün olarak yazıldığı [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0.</span><span class="sxs-lookup"><span data-stu-id="3a0ad-107">This document was originally written for the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0.</span></span>  [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] <span data-ttu-id="3a0ad-108">3.5 POX uygulamaları ile çalışmak için yerleşik destek sunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3a0ad-108">3.5 has built-in support for working with POX applications.</span></span> <span data-ttu-id="3a0ad-109">Bkz: hakkında daha fazla bilgi için [WCF Web HTTP programlama modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md).</span><span class="sxs-lookup"><span data-stu-id="3a0ad-109">For more information about see [WCF Web HTTP Programming Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md).</span></span>
  
## <a name="pox-programming-with-wcf"></a><span data-ttu-id="3a0ad-110">WCF ile POX programlama</span><span class="sxs-lookup"><span data-stu-id="3a0ad-110">POX programming with WCF</span></span>

<span data-ttu-id="3a0ad-111">POX iletileri kullanarak HTTP üzerinden iletişim kuran bir WCF hizmetleri bir [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="3a0ad-111">WCF services that communicate over HTTP using POX messages use a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>

```xml
<customBinding>
   <binding name="poxServerBinding">
       <textMessageEncoding messageVersion="None" />
       <httpTransport />
   </binding>
</customBinding>
```

<span data-ttu-id="3a0ad-112">Bu özel bağlama iki öğeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="3a0ad-112">This custom binding contains two elements:</span></span>

- [<span data-ttu-id="3a0ad-113">\<httpTransport ></span><span class="sxs-lookup"><span data-stu-id="3a0ad-113">\<httpTransport></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md)

- [<span data-ttu-id="3a0ad-114">\<textMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="3a0ad-114">\<textMessageEncoding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md)

<span data-ttu-id="3a0ad-115">WCF metin ileti Kodlayıcı kullanacak şekilde yapılandırılmış özel standart <xref:System.ServiceModel.Channels.MessageVersion.None%2A> sağlayan bir SOAP Zarfı içinde sarmalanmış değil gelen XML ileti yüklerini işlemek için bir değer.</span><span class="sxs-lookup"><span data-stu-id="3a0ad-115">The standard WCF Text Message Encoder is specially configured to use the <xref:System.ServiceModel.Channels.MessageVersion.None%2A> value, which allows it to process XML message payloads that do not arrive wrapped in a SOAP envelope.</span></span>

<span data-ttu-id="3a0ad-116">POX iletileri kullanarak HTTP üzerinden iletişim kuran bir WCF istemcileri, (kesinlik temelli aşağıdaki kodda gösterilen) benzer bir bağlama kullanın.</span><span class="sxs-lookup"><span data-stu-id="3a0ad-116">WCF clients that communicate over HTTP using POX messages use a similar binding (shown in the following imperative code).</span></span>

```csharp
private static Binding CreatePoxBinding()
{
    TextMessageEncodingBindingElement encoder =
        new TextMessageEncodingBindingElement( MessageVersion.None, Encoding.UTF8 );
    HttpTransportBindingElement transport = new HttpTransportBindingElement();
    transport.ManualAddressing = true;
    return new CustomBinding( new BindingElement[] { encoder, transport } );
}
```

<span data-ttu-id="3a0ad-117">POX istemciler için iletileri gönderdikleri bir URI'leri açıkça belirtmeniz gerekir çünkü bunlar genellikle yapılandırmalısınız <xref:System.ServiceModel.Channels.HttpTransportBindingElement> ayarlayarak el ile adresleme modu için <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A> özelliğini `true` öğesindeki.</span><span class="sxs-lookup"><span data-stu-id="3a0ad-117">Because POX clients must explicitly specify the URIs to which they send messages, they usually must configure the <xref:System.ServiceModel.Channels.HttpTransportBindingElement> to a manual addressing mode by setting the <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A> property to `true` on the element.</span></span> <span data-ttu-id="3a0ad-118">Bu uygulama kodu tarafından açık olarak ele alınması iletileri sağlar ve yeni bir oluşturmak için gerekli değil <xref:System.ServiceModel.ChannelFactory> her zaman bir uygulama için farklı bir HTTP URI bir ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="3a0ad-118">This allows messages to be addressed explicitly by application code and it is not necessary to create a new <xref:System.ServiceModel.ChannelFactory> every time an application sends a message to a different HTTP URI.</span></span>

<span data-ttu-id="3a0ad-119">POX iletileri Protokolü önemli bilgileri iletmek için SOAP üstbilgileri kullanmadığından, POX istemciler ve Hizmetler genellikle bir ileti gönderip için kullanılan temel alınan HTTP isteği parçalarını işleme gerekir.</span><span class="sxs-lookup"><span data-stu-id="3a0ad-119">Because POX messages do not use SOAP headers to convey important protocol information, POX clients and services often must manipulate pieces of the underlying HTTP request used to send or receive a message.</span></span> <span data-ttu-id="3a0ad-120">HTTP üst bilgileri ve durum kodları gibi protokol HTTP'ye özel bilgileri ortaya iki sınıflarıyla WCF programlama modeli içinde:</span><span class="sxs-lookup"><span data-stu-id="3a0ad-120">HTTP-specific protocol information such as the HTTP headers and status codes are surfaced in the WCF programming model through two classes:</span></span>

- <span data-ttu-id="3a0ad-121"><xref:System.ServiceModel.Channels.HttpRequestMessageProperty>, HTTP yöntemi ve istek üst bilgileri gibi HTTP isteğiyle ilgili bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="3a0ad-121"><xref:System.ServiceModel.Channels.HttpRequestMessageProperty>, which contains information about the HTTP request, such as the HTTP method and request headers.</span></span>

- <span data-ttu-id="3a0ad-122"><xref:System.ServiceModel.Channels.HttpResponseMessageProperty>, HTTP yanıtının HTTP durum kodu ve durum açıklaması yanı sıra HTTP yanıt üst bilgileri gibi bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="3a0ad-122"><xref:System.ServiceModel.Channels.HttpResponseMessageProperty>, which contains information about the HTTP response, such as the HTTP status code and status description, as well as any HTTP response headers.</span></span>
  
<span data-ttu-id="3a0ad-123">Aşağıdaki kod örneği için gönderilen bir HTTP GET isteği iletisi oluşturma işlemi gösterilmektedir `http://localhost:8100/customers`.</span><span class="sxs-lookup"><span data-stu-id="3a0ad-123">The following code example shows how to create an HTTP GET request message that is addressed to `http://localhost:8100/customers`.</span></span>

```csharp
Message request = Message.CreateMessage( MessageVersion.None, String.Empty );
request.Headers.To = "http://localhost:8100/customers";

HttpRequestMessageProperty property = new HttpRequestMessageProperty();
property.Method = "GET";
property.SuppressEntityBody = true;
request.Properties.Add( HttpRequestMessageProperty.Name, property );
```

<span data-ttu-id="3a0ad-124">İlk olarak boş bir istek <xref:System.ServiceModel.Channels.Message> çağrılarak oluşturulan <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29>.</span><span class="sxs-lookup"><span data-stu-id="3a0ad-124">First, an empty request <xref:System.ServiceModel.Channels.Message> is created by calling <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29>.</span></span> <span data-ttu-id="3a0ad-125"><xref:System.ServiceModel.Channels.MessageVersion.None%2A> Parametresi SOAP Zarfı gerekli olduğunu belirtmek için kullanılır ve <xref:System.String.Empty> parametre olarak eylemin geçirilir.</span><span class="sxs-lookup"><span data-stu-id="3a0ad-125">The <xref:System.ServiceModel.Channels.MessageVersion.None%2A> parameter is used to indicate that a SOAP envelope is not required and <xref:System.String.Empty> parameter is passed as the Action.</span></span> <span data-ttu-id="3a0ad-126">İstek iletisi ayarlayarak ardından ele <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> istenilen URI'nin başlığı.</span><span class="sxs-lookup"><span data-stu-id="3a0ad-126">The request message is then addressed by setting <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> header to the desired URI.</span></span> <span data-ttu-id="3a0ad-127">Ardından, bir <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> oluşturulur ve <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> HTTP fiili GET yöntemi ayarlamak ve <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> ayarlanır `true` giden HTTP istek iletisi gövdesinde veri gönderileceğini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="3a0ad-127">Next, an <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> is created and the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> is set to the HTTP verb GET method and the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> is set to `true` to indicate that no data should be sent in the body of the outgoing HTTP request message.</span></span> <span data-ttu-id="3a0ad-128">Son olarak, istek özelliği eklenir <xref:System.ServiceModel.Channels.Message.Properties%2A> koleksiyonu istek iletisi için HTTP aktarım isteği nasıl göndereceğini etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="3a0ad-128">Finally, the request property is added to the <xref:System.ServiceModel.Channels.Message.Properties%2A> collection of the request message so it can influence how the HTTP Transport sends the request.</span></span> <span data-ttu-id="3a0ad-129">İleti üzerinde uygun bir örneğine gönderilmek için hazır ise <xref:System.ServiceModel.Channels.IRequestChannel>.</span><span class="sxs-lookup"><span data-stu-id="3a0ad-129">The message is then ready to be sent over an appropriate instance of the <xref:System.ServiceModel.Channels.IRequestChannel>.</span></span>

<span data-ttu-id="3a0ad-130">Benzer teknikler ayıklamak için hizmette kullanılabilir <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> bir gelen iletiyi ve yapı bir yanıt.</span><span class="sxs-lookup"><span data-stu-id="3a0ad-130">Similar techniques can be used on the service to extract the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> from an incoming message and construct a response.</span></span>
