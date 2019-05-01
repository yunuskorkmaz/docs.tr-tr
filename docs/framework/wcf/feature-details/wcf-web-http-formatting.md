---
title: WCF Web HTTP biçimlendirme
ms.date: 03/30/2017
ms.assetid: e2414896-5463-41cd-b0a6-026a713eac2c
ms.openlocfilehash: f3d3a2d992f234c690f3fb87514b700a6596a5fe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61935479"
---
# <a name="wcf-web-http-formatting"></a>WCF Web HTTP biçimlendirme
WCF Web HTTP programlama modeli yanıtına döndürmek bir hizmet işlemi için en iyi biçimi dinamik olarak belirlemenize olanak tanır. Uygun bir biçim belirlemek için iki yöntem desteklenir: otomatik ve açık.  
  
## <a name="automatic-formatting"></a>Otomatik biçimlendirme  
 Etkin olduğunda, otomatik biçimlendirme yanıtta döndürülecek en iyi biçimde seçer. Aşağıdaki sırayla denetleyerek, en iyi biçimi belirler:  
  
1. Medya türleri istek iletisinin Accept üst bilgisi.  
  
2. İstek iletisi content-type.  
  
3. Varsayılan biçimi ayarlama işlemi.  
  
4. İçinde WebHttpBehavior ayarı varsayılan biçimi.  
  
 İsteğine bir Accept üst bilgisi içeriyorsa, Windows Communication Foundation (WCF) altyapısı onu destekleyen bir türü arar. Varsa `Accept` medya türlerinden öncelikleri üstbilgisini belirtir, bunların tümü kabul edilir. Hiçbir uygun biçimde bulunursa `Accept` üst bilgi, istek iletisinin içerik türü kullanılır. Uygun içerik türü belirtilirse, ayarlama işlemi için varsayılan biçimi kullanılır. Varsayılan biçimi ile ayarlanır `ResponseFormat` parametresinin <xref:System.ServiceModel.Web.WebGetAttribute> ve <xref:System.ServiceModel.Web.WebInvokeAttribute> öznitelikleri. Hiçbir varsayılan biçimi işlemi, değerini belirttiyseniz, <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> özelliği kullanılır. Otomatik biçimlendirme dayanır <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> özelliği. Bu özelliği ayarlandığında `true`, WCF altyapısı kullanılacak en iyi biçimi belirler. Otomatik Biçim Seçimi varsayılan olarak devre dışıdır için geriye dönük uyumluluk. Otomatik Biçim Seçimi program aracılığıyla veya yapılandırma yoluyla etkinleştirilebilir. Aşağıdaki örnek kodda Otomatik Biçim Seçimi etkinleştirme gösterir.  
  
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
  
 Otomatik biçimlendirme yapılandırma aracılığıyla etkinleştirilebilir. Ayarlayabileceğiniz <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> özelliği doğrudan üzerinde <xref:System.ServiceModel.Description.WebHttpBehavior> veya bu adı kullanıyor <xref:System.ServiceModel.Description.WebHttpEndpoint>. Aşağıdaki örnek otomatik biçim seçimi üzerinde nasıl etkinleştirileceğini gösterir <xref:System.ServiceModel.Description.WebHttpBehavior>.  
  
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
  
 Aşağıdaki örnek, Otomatik Biçim Seçimi kullanarak etkinleştirmek gösterilmektedir <xref:System.ServiceModel.Description.WebHttpEndpoint>.  
  
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
  
## <a name="explicit-formatting"></a>Explicit biçimlendirme  
 Adından da anlaşılacağı gibi açık biçimlendirmede Geliştirici işlem kodu içinde kullanmak için en iyi biçimi belirler. En iyi biçimi XML veya JSON ise Geliştirici ayarlar <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> ya da <xref:System.ServiceModel.Web.WebMessageFormat.Xml> veya <xref:System.ServiceModel.Web.WebMessageFormat.Json>. Varsa <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> özelliği açıkça ayarlanmamışsa, ardından işlem varsayılan biçimi kullanılır.  
  
 Aşağıdaki örnek, biçim sorgu dizesi parametresi için kullanılacak biçimi denetler. Belirtilen değilse, işlemin ayarlar kullanılarak Biçimlendirilecek <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A>.  
  
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
  
 XML veya JSON dışında biçimleri için destek gerekiyorsa, dönüş türüne sahip olmasını işleminizi tanımlama <xref:System.ServiceModel.Channels.Message>. İşlem kod içinde kullanmak ve oluşturmak için uygun biçimde belirlemek bir <xref:System.ServiceModel.Channels.Message> aşağıdaki yöntemlerden birini kullanarak nesne:  
  
- `WebOperationContext.CreateAtom10Response`  
  
- `WebOperationContext.CreateJsonResponse`  
  
- `WebOperationContext.CreateStreamResponse`  
  
- `WebOperationContext.CreateTextResponse`  
  
- `WebOperationContext.CreateXmlResponse`  
  
 Bu yöntemlerin her biri, içerik alır ve bir ileti ile uygun biçimde oluşturur. `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` Yöntemi tercih azalan dosyasındaki istemci tarafından tercih edilen biçimler listesini almak için kullanılabilir. Aşağıdaki örnek nasıl kullanılacağını gösterir `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` biçimini kullanın ve ardından kullanan belirlemek için uygun bir yanıt iletisi oluşturmak için yanıt yöntemi oluşturun.  
  
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
