---
title: POX uygulamaları ile birlikte çalışabilirlik
ms.date: 03/30/2017
ms.assetid: 449276b8-4633-46f0-85c9-81f01d127636
ms.openlocfilehash: 17b85ab41589a130e950cd52c759305cc17e92b7
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591054"
---
# <a name="interoperability-with-pox-applications"></a>POX uygulamaları ile birlikte çalışabilirlik

"Düz eski XML" (POX) uygulamalar, yalnızca bir SOAP Zarfı içinde içine XML uygulama verileri içeren ham HTTP ileti değiş tokuşu ile iletişim. Windows Communication Foundation (WCF) hizmetleri hem de POX iletileri kullanan istemciler sağlayabilir. Hizmette, WCF Hizmetleri'nin istemcilere Web tarayıcıları gibi uç noktalarını kullanıma sunar ve POX iletileri gönderip komut dosyası dilleri uygulamak için kullanılabilir. İstemcide, WCF programlama modeli POX tabanlı hizmetler ile iletişim kuran istemciler uygulamak için kullanılabilir.  
  
> [!NOTE]
> Bu belgede, .NET Framework 3. 0'için başlangıçta yazılmıştır.  .NET framework 3.5 POX uygulamaları ile çalışmak için yerleşik destek sunmaktadır. Bkz: hakkında daha fazla bilgi için [WCF Web HTTP programlama modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md).
  
## <a name="pox-programming-with-wcf"></a>WCF ile POX programlama

POX iletileri kullanarak HTTP üzerinden iletişim kuran bir WCF hizmetleri bir [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).

```xml
<customBinding>
   <binding name="poxServerBinding">
       <textMessageEncoding messageVersion="None" />
       <httpTransport />
   </binding>
</customBinding>
```

Bu özel bağlama iki öğeleri içerir:

- [\<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md)

- [\<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md)

WCF metin ileti Kodlayıcı kullanacak şekilde yapılandırılmış özel standart <xref:System.ServiceModel.Channels.MessageVersion.None%2A> sağlayan bir SOAP Zarfı içinde sarmalanmış değil gelen XML ileti yüklerini işlemek için bir değer.

POX iletileri kullanarak HTTP üzerinden iletişim kuran bir WCF istemcileri, (kesinlik temelli aşağıdaki kodda gösterilen) benzer bir bağlama kullanın.

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

POX istemciler için iletileri gönderdikleri bir URI'leri açıkça belirtmeniz gerekir çünkü bunlar genellikle yapılandırmalısınız <xref:System.ServiceModel.Channels.HttpTransportBindingElement> ayarlayarak el ile adresleme modu için <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A> özelliğini `true` öğesindeki. Bu uygulama kodu tarafından açık olarak ele alınması iletileri sağlar ve yeni bir oluşturmak için gerekli değil <xref:System.ServiceModel.ChannelFactory> her zaman bir uygulama için farklı bir HTTP URI bir ileti gönderir.

POX iletileri Protokolü önemli bilgileri iletmek için SOAP üstbilgileri kullanmadığından, POX istemciler ve Hizmetler genellikle bir ileti gönderip için kullanılan temel alınan HTTP isteği parçalarını işleme gerekir. HTTP üst bilgileri ve durum kodları gibi protokol HTTP'ye özel bilgileri ortaya iki sınıflarıyla WCF programlama modeli içinde:

- <xref:System.ServiceModel.Channels.HttpRequestMessageProperty>, HTTP yöntemi ve istek üst bilgileri gibi HTTP isteğiyle ilgili bilgileri içerir.

- <xref:System.ServiceModel.Channels.HttpResponseMessageProperty>, HTTP yanıtının HTTP durum kodu ve durum açıklaması yanı sıra HTTP yanıt üst bilgileri gibi bilgileri içerir.
  
Aşağıdaki kod örneği için gönderilen bir HTTP GET isteği iletisi oluşturma işlemi gösterilmektedir `http://localhost:8100/customers`.

```csharp
Message request = Message.CreateMessage( MessageVersion.None, String.Empty );
request.Headers.To = "http://localhost:8100/customers";

HttpRequestMessageProperty property = new HttpRequestMessageProperty();
property.Method = "GET";
property.SuppressEntityBody = true;
request.Properties.Add( HttpRequestMessageProperty.Name, property );
```

İlk olarak boş bir istek <xref:System.ServiceModel.Channels.Message> çağrılarak oluşturulan <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29>. <xref:System.ServiceModel.Channels.MessageVersion.None%2A> Parametresi SOAP Zarfı gerekli olduğunu belirtmek için kullanılır ve <xref:System.String.Empty> parametre olarak eylemin geçirilir. İstek iletisi ayarlayarak ardından ele <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> istenilen URI'nin başlığı. Ardından, bir <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> oluşturulur ve <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> HTTP fiili GET yöntemi ayarlamak ve <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> ayarlanır `true` giden HTTP istek iletisi gövdesinde veri gönderileceğini belirtmek için. Son olarak, istek özelliği eklenir <xref:System.ServiceModel.Channels.Message.Properties%2A> koleksiyonu istek iletisi için HTTP aktarım isteği nasıl göndereceğini etkileyebilir. İleti üzerinde uygun bir örneğine gönderilmek için hazır ise <xref:System.ServiceModel.Channels.IRequestChannel>.

Benzer teknikler ayıklamak için hizmette kullanılabilir <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> bir gelen iletiyi ve yapı bir yanıt.
