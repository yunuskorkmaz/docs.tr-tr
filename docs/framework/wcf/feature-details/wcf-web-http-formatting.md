---
title: WCF Web HTTP biçimlendirmesi
ms.date: 03/30/2017
ms.assetid: e2414896-5463-41cd-b0a6-026a713eac2c
ms.openlocfilehash: 011ff4f2e667268fac1aa2d82c0a2c4ffefc8dde
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585564"
---
# <a name="wcf-web-http-formatting"></a>WCF Web HTTP biçimlendirmesi
WCF Web HTTP programlama modeli, bir hizmet işleminin yanıtını döndürmek için en iyi biçimi dinamik olarak belirlemenizi sağlar. Uygun biçimi belirlemek için iki yöntem desteklenir: otomatik ve açık.  
  
## <a name="automatic-formatting"></a>Otomatik biçimlendirme  
 Etkinleştirildiğinde otomatik biçimlendirme, yanıtın döndürüleceği en iyi biçimi seçer. Aşağıdaki sırayla aşağıdakileri denetleyerek en iyi biçimi belirler:  
  
1. İstek iletisinin Accept üstbilgisindeki medya türleri.  
  
2. İstek iletisinin içerik türü.  
  
3. İşlemdeki varsayılan biçim ayarı.  
  
4. WebHttpBehavior 'daki varsayılan biçim ayarı.  
  
 İstek iletisi bir Accept üst bilgisi içeriyorsa, Windows Communication Foundation (WCF) altyapısı desteklediği bir türü arar. `Accept`Üst bilgi, medya türleri için öncelikler belirtiyorsa, bunlar kabul edilir. Üstbilgide uygun biçim bulunamazsa `Accept` , istek iletisinin içerik türü kullanılır. Uygun bir içerik türü belirtilmemişse, işlem için varsayılan biçim ayarı kullanılır. Varsayılan biçim `ResponseFormat` , <xref:System.ServiceModel.Web.WebGetAttribute> ve özniteliklerinin parametresiyle ayarlanır <xref:System.ServiceModel.Web.WebInvokeAttribute> . İşlem üzerinde hiçbir varsayılan biçim belirtilmemişse, <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> özelliğin değeri kullanılır. Otomatik biçimlendirme <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> özelliği kullanır. Bu özellik olarak ayarlandığında `true` , WCF altyapısı kullanılacak en iyi biçimi belirler. Otomatik Biçim seçimi, geriye doğru uyumluluk için varsayılan olarak devre dışıdır. Otomatik Biçim Seçimi programlı bir şekilde veya yapılandırma aracılığıyla etkinleştirilebilir. Aşağıdaki örnekte, kodda otomatik biçim seçiminin nasıl etkinleştirileceği gösterilmektedir.  
  
```csharp
// This code assumes the service name is MyService and the service contract is IMyContract
Uri baseAddress = new Uri("http://localhost:8000");  
  
WebServiceHost host = new WebServiceHost(typeof(MyService), baseAddress)  
try  
{  
   ServiceEndpoint sep = host.AddServiceEndpoint(typeof(IMyContract), new WebHttpBinding(), "");  
   // Check it see if the WebHttpBehavior already exists  
   WebHttpBehavior whb = sep.Behaviors.Find<WebHttpBehavior>();  
  
   if (whb != null)  
   {  
      whb.AutomaticFormatSelectionEnabled = true;  
   }  
   else  
   {  
      WebHttpBehavior webBehavior = new WebHttpBehavior();  
      webBehavior.AutomaticFormatSelectionEnabled = true;  
      sep.Behaviors.Add(webBehavior);  
   }  
         // Open host to start listening for messages  
   host.Open();
  
  // ...  
}  
  catch(CommunicationException ex)  
  {  
     Console.WriteLine("An exception occurred: " + ex.Message());  
  }  
```  
  
 Otomatik biçimlendirme, yapılandırma aracılığıyla da etkinleştirilebilir. <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>Özelliğini kullanarak doğrudan veya üzerinde özelliği ayarlayabilirsiniz <xref:System.ServiceModel.Description.WebHttpBehavior> <xref:System.ServiceModel.Description.WebHttpEndpoint> . Aşağıdaki örnek, üzerinde otomatik biçim seçiminin nasıl etkinleştirileceğini gösterir <xref:System.ServiceModel.Description.WebHttpBehavior> .  
  
```xml  
<system.serviceModel>  
  <behaviors>  
    <endpointBehaviors>  
      <behavior>  
        <webHttp automaticFormatSelectionEnabled="true" />  
      </behavior>  
    </endpointBehaviors>  
  </behaviors>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <!-- the "" standard endpoint is used by WebServiceHost for auto creating a web endpoint. -->  
      <standardEndpoint name="" helpEnabled="true" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 Aşağıdaki örnek kullanılarak otomatik biçim seçiminin nasıl etkinleştirileceğini gösterir <xref:System.ServiceModel.Description.WebHttpEndpoint> .  
  
```xml  
<system.serviceModel>  
    <standardEndpoints>  
      <webHttpEndpoint>  
        <!-- the "" standard endpoint is used by WebServiceHost for auto creating a web endpoint. -->  
        <standardEndpoint name="" helpEnabled="true" automaticFormatSelectionEnabled="true"  />  
      </webHttpEndpoint>  
    </standardEndpoints>  
  </system.serviceModel>  
```  
  
## <a name="explicit-formatting"></a>Açık biçimlendirme  
 Adından da anlaşılacağı gibi, geliştirici, işlem kodu içinde kullanmak için en iyi biçimi belirler. En iyi biçim XML veya JSON ise, geliştirici ya <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> da olarak ayarlanır <xref:System.ServiceModel.Web.WebMessageFormat.Xml> <xref:System.ServiceModel.Web.WebMessageFormat.Json> . <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A>Özelliği açıkça ayarlanmamışsa, işlemin varsayılan biçimi kullanılır.  
  
 Aşağıdaki örnek, biçim sorgu dizesi parametresini kullanılacak bir biçim için denetler. Belirtilmişse, kullanarak işlemin biçimini ayarlar <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> .  
  
```csharp
public class Service : IService  
{  
    [WebGet]  
     public string EchoWithGet(string s)  
    {  
        // if a format query string parameter has been specified, set the response format to that. If no such
        // query string parameter exists the Accept header will be used
        string formatQueryStringValue = WebOperationContext.Current.IncomingRequest.UriTemplateMatch.QueryParameters["format"];  
        if (!string.IsNullOrEmpty(formatQueryStringValue))  
        {  
            if (formatQueryStringValue.Equals("xml", System.StringComparison.OrdinalIgnoreCase))  
            {
                WebOperationContext.Current.OutgoingResponse.Format = WebMessageFormat.Xml;
            }
            else if (formatQueryStringValue.Equals("json", System.StringComparison.OrdinalIgnoreCase))  
            {  
                WebOperationContext.Current.OutgoingResponse.Format = WebMessageFormat.Json;  
            }  
            else  
            {  
                throw new WebFaultException<string>($"Unsupported format '{formatQueryStringValue}'",   HttpStatusCode.BadRequest);
            }  
        }  
        return "You said " + s;  
    }  
```  
  
 XML veya JSON dışındaki biçimleri desteklemeniz gerekiyorsa, işleminizi bir dönüş türüne sahip olacak şekilde tanımlayın <xref:System.ServiceModel.Channels.Message> . İşlem kodu içinde, kullanılacak uygun biçimi belirleyip <xref:System.ServiceModel.Channels.Message> aşağıdaki yöntemlerden birini kullanarak bir nesne oluşturun:  
  
- `WebOperationContext.CreateAtom10Response`  
  
- `WebOperationContext.CreateJsonResponse`  
  
- `WebOperationContext.CreateStreamResponse`  
  
- `WebOperationContext.CreateTextResponse`  
  
- `WebOperationContext.CreateXmlResponse`  
  
 Bu yöntemlerin her biri içerik alır ve uygun biçimde bir ileti oluşturur. `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements`Yöntemi, istemci tarafından azalan tercih sırasına göre tercih edilen biçimlerin bir listesini almak için kullanılabilir. Aşağıdaki örnek, kullanılacak biçimi belirlemede kullanılacak şekilde nasıl kullanılacağını gösterir `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` ve ardından yanıt iletisini oluşturmak için uygun oluşturma yanıtı yöntemini kullanır.  
  
```csharp
public class Service : IService  
{  
    public Message EchoListWithGet(string list)  
    {  
        List<string> returnList = new List<string>(list.Split(new char[] { ',' }, StringSplitOptions.RemoveEmptyEntries));  
        IList<ContentType> acceptHeaderElements = WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements();  
        for (int x = 0; x < acceptHeaderElements.Count; x++)  
        {  
            string normalizedMediaType = acceptHeaderElements[x].MediaType.ToLowerInvariant();  
            switch (normalizedMediaType)  
            {  
                case "image/jpeg": return CreateJpegResponse(returnList);  
                case "application/xhtml+xml": return CreateXhtmlResponse(returnList);  
                case "application/atom+xml": return CreateAtom10Response(returnList);  
                case "application/xml": return CreateXmlResponse(returnList);  
                case "application/json": return CreateJsonResponse(returnList);  
          }  
    }  
  
    // Default response format is XML  
    return CreateXmlResponse(returnList);  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.UriTemplate>
- <xref:System.UriTemplateMatch>
- [WCF Web HTTP Programlama Modeli](wcf-web-http-programming-model.md)
- [UriTemplate ve UriTemplateTable](uritemplate-and-uritemplatetable.md)
- [WCF Web HTTP Programlama Modeli Genel Bakış](wcf-web-http-programming-model-overview.md)
- [WCF Web HTTP Programlama Nesnesi Modeli](wcf-web-http-programming-object-model.md)
