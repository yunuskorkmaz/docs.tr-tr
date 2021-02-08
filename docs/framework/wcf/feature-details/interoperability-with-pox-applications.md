---
description: 'Daha fazla bilgi edinin: POX uygulamalarıyla birlikte çalışabilirlik'
title: POX Uygulamaları ile birlikte çalışabilirlik
ms.date: 03/30/2017
ms.assetid: 449276b8-4633-46f0-85c9-81f01d127636
ms.openlocfilehash: 832b9ae93f6046ca9995b57bdcbbfbfeb46d2a09
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802716"
---
# <a name="interoperability-with-pox-applications"></a><span data-ttu-id="a905a-103">POX Uygulamaları ile birlikte çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="a905a-103">Interoperability with POX applications</span></span>

<span data-ttu-id="a905a-104">"Düz eski XML" (POX) uygulamaları, yalnızca bir SOAP Zarfı içinde olmayan XML uygulama verileri içeren ham HTTP iletileri değiş tokuşu yaparak iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="a905a-104">"Plain Old XML" (POX) applications communicate by exchanging raw HTTP messages that contain only XML application data that is not enclosed within a SOAP envelope.</span></span> <span data-ttu-id="a905a-105">Windows Communication Foundation (WCF), POX iletileri kullanan Hizmetleri ve istemcileri sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="a905a-105">Windows Communication Foundation (WCF) can provide both services and clients that use POX messages.</span></span> <span data-ttu-id="a905a-106">Hizmette, Web tarayıcıları ve POX iletileri gönderen ve alan komut dosyası dilleri gibi istemcilere uç noktalar sunan Hizmetleri uygulamak için WCF kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a905a-106">On the service, WCF can be used to implement services that expose endpoints to clients such as Web browsers and scripting languages that send and receive POX messages.</span></span> <span data-ttu-id="a905a-107">İstemci üzerinde, WCF programlama modeli POX tabanlı hizmetlerle iletişim kuran istemcileri uygulamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a905a-107">On the client, the WCF programming model can be used to implement clients that communicate with POX-based services.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a905a-108">Bu belge ilk olarak .NET Framework 3,0 için yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="a905a-108">This document was originally written for the .NET Framework 3.0.</span></span>  <span data-ttu-id="a905a-109">.NET Framework 3,5, POX uygulamalarıyla çalışmak için yerleşik desteğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a905a-109">.NET Framework 3.5 has built-in support for working with POX applications.</span></span> <span data-ttu-id="a905a-110">Daha fazla bilgi için bkz. [WCF Web http programlama modeli](wcf-web-http-programming-model.md).</span><span class="sxs-lookup"><span data-stu-id="a905a-110">For more information about see [WCF Web HTTP Programming Model](wcf-web-http-programming-model.md).</span></span>
  
## <a name="pox-programming-with-wcf"></a><span data-ttu-id="a905a-111">WCF ile POX programlama</span><span class="sxs-lookup"><span data-stu-id="a905a-111">POX programming with WCF</span></span>

<span data-ttu-id="a905a-112">POX iletileri kullanarak HTTP üzerinden iletişim kuran WCF Hizmetleri bir kullanır [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="a905a-112">WCF services that communicate over HTTP using POX messages use a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md).</span></span>

```xml
<customBinding>
   <binding name="poxServerBinding">
       <textMessageEncoding messageVersion="None" />
       <httpTransport />
   </binding>
</customBinding>
```

<span data-ttu-id="a905a-113">Bu özel bağlama iki öğe içerir:</span><span class="sxs-lookup"><span data-stu-id="a905a-113">This custom binding contains two elements:</span></span>

- [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md)

- [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md)

<span data-ttu-id="a905a-114">Standart WCF metin Iletisi Kodlayıcısı, <xref:System.ServiceModel.Channels.MessageVersion.None%2A> BIR SOAP zarfına kaydırılmış olan XML ileti yüklerini işlemesini sağlayan değerini kullanmak için özel olarak yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="a905a-114">The standard WCF Text Message Encoder is specially configured to use the <xref:System.ServiceModel.Channels.MessageVersion.None%2A> value, which allows it to process XML message payloads that do not arrive wrapped in a SOAP envelope.</span></span>

<span data-ttu-id="a905a-115">POX iletileri kullanarak HTTP üzerinden iletişim kuran WCF istemcileri benzer bir bağlama kullanır (aşağıdaki kesinlik kodu içinde gösterilmiştir).</span><span class="sxs-lookup"><span data-stu-id="a905a-115">WCF clients that communicate over HTTP using POX messages use a similar binding (shown in the following imperative code).</span></span>

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

<span data-ttu-id="a905a-116">POX istemcilerinin, iletileri gönderdikleri URI 'Leri açıkça belirtmesi gerektiğinden, genellikle <xref:System.ServiceModel.Channels.HttpTransportBindingElement> <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A> özelliğini öğesi üzerinde olarak ayarlayarak bir el ile adresleme moduna almalıdır `true` .</span><span class="sxs-lookup"><span data-stu-id="a905a-116">Because POX clients must explicitly specify the URIs to which they send messages, they usually must configure the <xref:System.ServiceModel.Channels.HttpTransportBindingElement> to a manual addressing mode by setting the <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A> property to `true` on the element.</span></span> <span data-ttu-id="a905a-117">Bu, iletilerin açıkça uygulama kodu tarafından oluşturulmasına olanak sağlar ve <xref:System.ServiceModel.ChannelFactory> bir uygulamanın farklı bır http URI 'sine ileti göndermesi durumunda yeni bir oluşturma işlemi için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="a905a-117">This allows messages to be addressed explicitly by application code and it is not necessary to create a new <xref:System.ServiceModel.ChannelFactory> every time an application sends a message to a different HTTP URI.</span></span>

<span data-ttu-id="a905a-118">POX iletileri önemli protokol bilgilerini iletmek için SOAP üstbilgileri kullanmadığından, POX istemcileri ve Hizmetleri genellikle bir ileti göndermek veya almak için kullanılan temel HTTP isteğinin parçalarını işlemelidir.</span><span class="sxs-lookup"><span data-stu-id="a905a-118">Because POX messages do not use SOAP headers to convey important protocol information, POX clients and services often must manipulate pieces of the underlying HTTP request used to send or receive a message.</span></span> <span data-ttu-id="a905a-119">Http üstbilgileri ve durum kodları gibi HTTP özel protokol bilgileri, iki sınıf aracılığıyla WCF programlama modelinde ortaya çıkmış:</span><span class="sxs-lookup"><span data-stu-id="a905a-119">HTTP-specific protocol information such as the HTTP headers and status codes are surfaced in the WCF programming model through two classes:</span></span>

- <span data-ttu-id="a905a-120"><xref:System.ServiceModel.Channels.HttpRequestMessageProperty>http yöntemi ve istek üstbilgileri gibi HTTP isteğiyle ilgili bilgileri içeren.</span><span class="sxs-lookup"><span data-stu-id="a905a-120"><xref:System.ServiceModel.Channels.HttpRequestMessageProperty>, which contains information about the HTTP request, such as the HTTP method and request headers.</span></span>

- <span data-ttu-id="a905a-121"><xref:System.ServiceModel.Channels.HttpResponseMessageProperty>http durum kodu ve durum açıklaması gibi http yanıtı hakkındaki bilgileri ve tüm HTTP yanıt üstbilgilerini içeren.</span><span class="sxs-lookup"><span data-stu-id="a905a-121"><xref:System.ServiceModel.Channels.HttpResponseMessageProperty>, which contains information about the HTTP response, such as the HTTP status code and status description, as well as any HTTP response headers.</span></span>
  
<span data-ttu-id="a905a-122">Aşağıdaki kod örneği, tarafından belirtilen bir HTTP GET isteği iletisinin nasıl oluşturulacağını göstermektedir `http://localhost:8100/customers` .</span><span class="sxs-lookup"><span data-stu-id="a905a-122">The following code example shows how to create an HTTP GET request message that is addressed to `http://localhost:8100/customers`.</span></span>

```csharp
Message request = Message.CreateMessage( MessageVersion.None, String.Empty );
request.Headers.To = "http://localhost:8100/customers";

HttpRequestMessageProperty property = new HttpRequestMessageProperty();
property.Method = "GET";
property.SuppressEntityBody = true;
request.Properties.Add( HttpRequestMessageProperty.Name, property );
```

<span data-ttu-id="a905a-123">İlk olarak, çağırarak boş bir istek <xref:System.ServiceModel.Channels.Message> oluşturulur <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29> .</span><span class="sxs-lookup"><span data-stu-id="a905a-123">First, an empty request <xref:System.ServiceModel.Channels.Message> is created by calling <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29>.</span></span> <span data-ttu-id="a905a-124"><xref:System.ServiceModel.Channels.MessageVersion.None%2A>Parametresi, BIR SOAP zarfının gerekli olmadığını ve <xref:System.String.Empty> eylem olarak parametre geçtiğini belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a905a-124">The <xref:System.ServiceModel.Channels.MessageVersion.None%2A> parameter is used to indicate that a SOAP envelope is not required and <xref:System.String.Empty> parameter is passed as the Action.</span></span> <span data-ttu-id="a905a-125">İstek iletisi daha sonra <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> üst bilgi Istenen URI 'ye ayarlanarak karşılanır.</span><span class="sxs-lookup"><span data-stu-id="a905a-125">The request message is then addressed by setting <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> header to the desired URI.</span></span> <span data-ttu-id="a905a-126">Sonra, bir <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> oluşturulur ve <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> http fiili get yöntemi olarak ayarlanır ve <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> `true` giden http istek iletisinin gövdesinde hiçbir veri gönderilmeyeceğini belirtmek için olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="a905a-126">Next, an <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> is created and the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> is set to the HTTP verb GET method and the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> is set to `true` to indicate that no data should be sent in the body of the outgoing HTTP request message.</span></span> <span data-ttu-id="a905a-127">Son olarak, istek özelliği istek <xref:System.ServiceModel.Channels.Message.Properties%2A> iletisi koleksiyonuna eklenerek http aktarımının isteği nasıl göndereceğini etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="a905a-127">Finally, the request property is added to the <xref:System.ServiceModel.Channels.Message.Properties%2A> collection of the request message so it can influence how the HTTP Transport sends the request.</span></span> <span data-ttu-id="a905a-128">İleti daha sonra uygun bir örneği üzerinden gönderilmeye hazırlanmalıdır <xref:System.ServiceModel.Channels.IRequestChannel> .</span><span class="sxs-lookup"><span data-stu-id="a905a-128">The message is then ready to be sent over an appropriate instance of the <xref:System.ServiceModel.Channels.IRequestChannel>.</span></span>

<span data-ttu-id="a905a-129">Bir <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> gelen iletiden ayıklamak ve yanıt oluşturmak için hizmette benzer teknikler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a905a-129">Similar techniques can be used on the service to extract the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> from an incoming message and construct a response.</span></span>
