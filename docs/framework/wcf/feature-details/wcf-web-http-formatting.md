---
title: WCF Web HTTP biçimlendirme
ms.date: 03/30/2017
ms.assetid: e2414896-5463-41cd-b0a6-026a713eac2c
ms.openlocfilehash: b6c9728fe40e26977366b73337e72b1514a12a19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184190"
---
# <a name="wcf-web-http-formatting"></a>WCF Web HTTP biçimlendirme
WCF Web HTTP programlama modeli, yanıtını geri döndürmek için bir hizmet işlemi için en iyi biçimi dinamik olarak belirlemenize olanak tanır. Uygun biçimi belirlemek için iki yöntem desteklenir: otomatik ve açık.  
  
## <a name="automatic-formatting"></a>Otomatik biçimlendirme  
 Etkinleştirildiğinde, otomatik biçimlendirme yanıtı döndürecek en iyi biçimi seçer. Sırayla aşağıdakileri işaretleyerek en iyi biçimi belirler:  
  
1. İstek iletisinin Kabul üstbilgisinde ortam türleri.  
  
2. İstek iletisinin içerik türü.  
  
3. İşlemdeki varsayılan biçim ayarı.  
  
4. Web'de varsayılan biçim ayarıHttpBehavior.  
  
 İstek iletisi bir Üstbilgi içeriyorsa, Windows Communication Foundation (WCF) altyapısı desteklediği bir türü arar. `Accept` Üstbilgi, ortam türleri için öncelikleri belirtirse, bunlar onurlanır. `Accept` Üstbilgide uygun biçim bulunmazsa, istek iletisinin içerik türü kullanılır. Uygun içerik türü belirtilmemişse, işlem için varsayılan biçim ayarı kullanılır. Varsayılan biçim `ResponseFormat` <xref:System.ServiceModel.Web.WebGetAttribute> ve <xref:System.ServiceModel.Web.WebInvokeAttribute> özniteliklerin parametresi ile ayarlanır. İşlemde varsayılan biçim belirtilmemişse, özelliğin <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> değeri kullanılır. Otomatik biçimlendirme <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> özelliğine dayanır. Bu özellik `true`ayarlandığında, WCF altyapısı kullanılacak en iyi biçimi belirler. Otomatik biçim seçimi geriye dönük uyumluluk için varsayılan olarak devre dışı bırakılır. Otomatik biçim seçimi programlı olarak veya yapılandırma yoluyla etkinleştirilebilir. Aşağıdaki örnekte, kodda otomatik biçim seçiminin nasıl etkinleştirilen gösterilmektedir.  
  
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
  
 Otomatik biçimlendirme yapılandırma yoluyla da etkinleştirilebilir. <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> Özelliği doğrudan üzerinde <xref:System.ServiceModel.Description.WebHttpBehavior> ayarlayabilirsiniz veya <xref:System.ServiceModel.Description.WebHttpEndpoint>. Aşağıdaki örnekte, <xref:System.ServiceModel.Description.WebHttpBehavior>''de otomatik biçim seçiminin nasıl etkinleştirilen  
  
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
  
 Aşağıdaki örnekte, otomatik biçim seçiminin nasıl etkinleştirilen bir şekilde gösterilmektedir. <xref:System.ServiceModel.Description.WebHttpEndpoint>  
  
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
 Adından da anlaşılacağı gibi, açık biçimlendirme geliştirici işlem kodu içinde kullanılacak en iyi biçimi belirler. En iyi biçim XML veya JSON <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> ise <xref:System.ServiceModel.Web.WebMessageFormat.Xml> <xref:System.ServiceModel.Web.WebMessageFormat.Json>geliştirici ya da ayarlar. <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> Özellik açıkça ayarlanmazsa, işlemin varsayılan biçimi kullanılır.  
  
 Aşağıdaki örnekte, kullanılacak bir biçim için biçim sorgusu dize parametresini denetler. Belirtilmişse, 'yi kullanarak <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A>işlemin biçimini ayarlar.  
  
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
  
 XML veya JSON dışındaki biçimleri desteklemeniz gerekiyorsa, işleminizi bir geri <xref:System.ServiceModel.Channels.Message>dönüş türüne sahip olmak için tanımlayın. İşlem kodu içinde, kullanılacak uygun biçimi belirleyin <xref:System.ServiceModel.Channels.Message> ve ardından aşağıdaki yöntemlerden birini kullanarak bir nesne oluşturun:  
  
- `WebOperationContext.CreateAtom10Response`  
  
- `WebOperationContext.CreateJsonResponse`  
  
- `WebOperationContext.CreateStreamResponse`  
  
- `WebOperationContext.CreateTextResponse`  
  
- `WebOperationContext.CreateXmlResponse`  
  
 Bu yöntemlerin her biri içerik alır ve uygun biçimde bir ileti oluşturur. Yöntem, `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` tercihi azaltmak amacıyla istemci tarafından tercih edilen biçimlerin listesini almak için kullanılabilir. Aşağıdaki örnek, kullanılacak `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` biçimi belirlemek için nasıl kullanılacağını gösterir ve yanıt iletisi oluşturmak için uygun yanıt oluşturma yöntemini kullanır.  
  
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
- [WCF Web HTTP Programlama Modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [UriTemplate ve UriTemplateTable](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)
- [WCF Web HTTP Programlama Modeli Genel Bakış](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
- [WCF Web HTTP Programlama Nesnesi Modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
