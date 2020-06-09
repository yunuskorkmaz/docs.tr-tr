---
title: POX Uygulamaları ile birlikte çalışabilirlik
ms.date: 03/30/2017
ms.assetid: 449276b8-4633-46f0-85c9-81f01d127636
ms.openlocfilehash: 64a6d850a32b14bc60cd43466e04b53a7a39be81
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579273"
---
# <a name="interoperability-with-pox-applications"></a>POX Uygulamaları ile birlikte çalışabilirlik

"Düz eski XML" (POX) uygulamaları, yalnızca bir SOAP Zarfı içinde olmayan XML uygulama verileri içeren ham HTTP iletileri değiş tokuşu yaparak iletişim kurar. Windows Communication Foundation (WCF), POX iletileri kullanan Hizmetleri ve istemcileri sağlayabilir. Hizmette, Web tarayıcıları ve POX iletileri gönderen ve alan komut dosyası dilleri gibi istemcilere uç noktalar sunan Hizmetleri uygulamak için WCF kullanılabilir. İstemci üzerinde, WCF programlama modeli POX tabanlı hizmetlerle iletişim kuran istemcileri uygulamak için kullanılabilir.  
  
> [!NOTE]
> Bu belge ilk olarak .NET Framework 3,0 için yazılmıştır.  .NET Framework 3,5, POX uygulamalarıyla çalışmak için yerleşik desteğe sahiptir. Daha fazla bilgi için bkz. [WCF Web http programlama modeli](wcf-web-http-programming-model.md).
  
## <a name="pox-programming-with-wcf"></a>WCF ile POX programlama

POX iletileri kullanarak HTTP üzerinden iletişim kuran WCF Hizmetleri bir kullanır [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) .

```xml
<customBinding>
   <binding name="poxServerBinding">
       <textMessageEncoding messageVersion="None" />
       <httpTransport />
   </binding>
</customBinding>
```

Bu özel bağlama iki öğe içerir:

- [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md)

- [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md)

Standart WCF metin Iletisi Kodlayıcısı, <xref:System.ServiceModel.Channels.MessageVersion.None%2A> BIR SOAP zarfına kaydırılmış olan XML ileti yüklerini işlemesini sağlayan değerini kullanmak için özel olarak yapılandırılmıştır.

POX iletileri kullanarak HTTP üzerinden iletişim kuran WCF istemcileri benzer bir bağlama kullanır (aşağıdaki kesinlik kodu içinde gösterilmiştir).

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

POX istemcilerinin, iletileri gönderdikleri URI 'Leri açıkça belirtmesi gerektiğinden, genellikle <xref:System.ServiceModel.Channels.HttpTransportBindingElement> <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A> özelliğini öğesi üzerinde olarak ayarlayarak bir el ile adresleme moduna almalıdır `true` . Bu, iletilerin açıkça uygulama kodu tarafından oluşturulmasına olanak sağlar ve <xref:System.ServiceModel.ChannelFactory> bir uygulamanın farklı bır http URI 'sine ileti göndermesi durumunda yeni bir oluşturma işlemi için gerekli değildir.

POX iletileri önemli protokol bilgilerini iletmek için SOAP üstbilgileri kullanmadığından, POX istemcileri ve Hizmetleri genellikle bir ileti göndermek veya almak için kullanılan temel HTTP isteğinin parçalarını işlemelidir. Http üstbilgileri ve durum kodları gibi HTTP özel protokol bilgileri, iki sınıf aracılığıyla WCF programlama modelinde ortaya çıkmış:

- <xref:System.ServiceModel.Channels.HttpRequestMessageProperty>http yöntemi ve istek üstbilgileri gibi HTTP isteğiyle ilgili bilgileri içeren.

- <xref:System.ServiceModel.Channels.HttpResponseMessageProperty>http durum kodu ve durum açıklaması gibi http yanıtı hakkındaki bilgileri ve tüm HTTP yanıt üstbilgilerini içeren.
  
Aşağıdaki kod örneği, tarafından belirtilen bir HTTP GET isteği iletisinin nasıl oluşturulacağını göstermektedir `http://localhost:8100/customers` .

```csharp
Message request = Message.CreateMessage( MessageVersion.None, String.Empty );
request.Headers.To = "http://localhost:8100/customers";

HttpRequestMessageProperty property = new HttpRequestMessageProperty();
property.Method = "GET";
property.SuppressEntityBody = true;
request.Properties.Add( HttpRequestMessageProperty.Name, property );
```

İlk olarak, çağırarak boş bir istek <xref:System.ServiceModel.Channels.Message> oluşturulur <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29> . <xref:System.ServiceModel.Channels.MessageVersion.None%2A>Parametresi, BIR SOAP zarfının gerekli olmadığını ve <xref:System.String.Empty> eylem olarak parametre geçtiğini belirtmek için kullanılır. İstek iletisi daha sonra <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> üst bilgi Istenen URI 'ye ayarlanarak karşılanır. Sonra, bir <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> oluşturulur ve <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> http fiili get yöntemi olarak ayarlanır ve <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> `true` giden http istek iletisinin gövdesinde hiçbir veri gönderilmeyeceğini belirtmek için olarak ayarlanır. Son olarak, istek özelliği istek <xref:System.ServiceModel.Channels.Message.Properties%2A> iletisi koleksiyonuna eklenerek http aktarımının isteği nasıl göndereceğini etkileyebilir. İleti daha sonra uygun bir örneği üzerinden gönderilmeye hazırlanmalıdır <xref:System.ServiceModel.Channels.IRequestChannel> .

Bir <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> gelen iletiden ayıklamak ve yanıt oluşturmak için hizmette benzer teknikler kullanılabilir.
