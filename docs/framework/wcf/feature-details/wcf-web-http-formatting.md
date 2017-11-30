---
title: "WCF Web HTTP biçimlendirme"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
ms.assetid: e2414896-5463-41cd-b0a6-026a713eac2c
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3a41c6c7304234535993d83329c4faa464218e3d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="wcf-web-http-formatting"></a>WCF Web HTTP biçimlendirme
WCF Web HTTP programlama modeli yanıt olarak döndürmek bir hizmet işlemi için en iyi biçimi dinamik olarak belirlemenize olanak tanır. Uygun bir biçim belirlemek için iki yöntem desteklenir: otomatik ve açık.  
  
## <a name="automatic-formatting"></a>Otomatik biçimlendirme  
 Etkinleştirildiğinde, otomatik biçimlendirme yanıt dönmek en iyi biçimde seçer. En iyi biçim sırayla aşağıdakileri kontrol ederek belirler:  
  
1.  İstek iletisinin Accept üstbilgisindeki medya türleri.  
  
2.  İstek iletisi content-type.  
  
3.  İşlemde ayarı varsayılan biçimi.  
  
4.  WebHttpBehavior ayarı varsayılan biçimi.  
  
 İstek iletisinde bir Accept üstbilgisi içeriyorsa [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] desteklediği bir tür altyapı arar. Varsa `Accept` ayardaki, üstbilgi medya türlerinden öncelikleri belirtir. Uygun bir biçim bulunursa `Accept` üstbilgisi, istek iletisi içerik türü kullanılır. Uygun içerik türü belirtilirse, varsayılan biçimi işlem için ayarını kullanılır. Varsayılan biçimi ile ayarlanır `ResponseFormat` parametresinin <xref:System.ServiceModel.Web.WebGetAttribute> ve <xref:System.ServiceModel.Web.WebInvokeAttribute> öznitelikleri. Varsayılan biçimi işlemi, değerini belirttiyseniz, <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> özelliği kullanılır. Otomatik biçimlendirme kullanır <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> özelliği. Bu özellik ayarlandığında `true`, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] altyapı kullanmak için en iyi biçim belirler. Otomatik Biçim Seçimi varsayılan olarak devre dışıdır için geriye dönük uyumluluk. Otomatik Biçim Seçimi program aracılığıyla veya yapılandırma yoluyla etkinleştirilebilir. Aşağıdaki örnek kodda Otomatik Biçim Seçimi etkinleştirme gösterir.  
  
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
  
 Otomatik biçimlendirme yapılandırma aracılığıyla etkinleştirilebilir. Ayarlayabileceğiniz <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> özelliği doğrudan üzerinde <xref:System.ServiceModel.Description.WebHttpBehavior> veya kullanarak <xref:System.ServiceModel.Description.WebHttpEndpoint>. Aşağıdaki örnek, Otomatik Biçim Seçimi etkinleştirmek gösterilmiştir <xref:System.ServiceModel.Description.WebHttpBehavior>.  
  
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
  
 Aşağıdaki örnek, Otomatik Biçim Seçimi kullanarak etkinleştirmek gösterilmiştir <xref:System.ServiceModel.Description.WebHttpEndpoint>.  
  
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
 Adından da anlaşılacağı gibi açık biçimlendirmede Geliştirici işlem kodu içinde kullanmak için en iyi biçimini belirler. En iyi biçimde XML veya JSON ise Geliştirici ayarlar <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> ya da <xref:System.ServiceModel.Web.WebMessageFormat.Xml> veya <xref:System.ServiceModel.Web.WebMessageFormat.Json>. Varsa <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> özelliği açıkça ayarlanmamışsa, sonra işlemin varsayılan biçimi kullanılır.  
  
 Aşağıdaki örnek biçim sorgu dizesi parametresi için kullanılacak biçimi denetler. Belirtilen sahip değilse, işlem ayarlar biçimi kullanılarak <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A>.  
  
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
                 throw new WebFaultException<string>(string.Format("Unsupported format '{0}'", formatQueryStringValue), HttpStatusCode.BadRequest);  
            }  
        }  
        return "You said " + s;  
    }  
```  
  
 XML veya JSON dışında biçimleri desteklemeniz gerekiyorsa, bir dönüş türüne sahip işleminizi tanımlamak <xref:System.ServiceModel.Channels.Message>. İşlem kodu içinde kullanın ve sonra oluşturmak için uygun biçimde belirlemek bir <xref:System.ServiceModel.Channels.Message> aşağıdaki yöntemlerden birini kullanarak nesnesi:  
  
-   `WebOperationContext.CreateAtom10Response`  
  
-   `WebOperationContext.CreateJsonResponse`  
  
-   `WebOperationContext.CreateStreamResponse`  
  
-   `WebOperationContext.CreateTextResponse`  
  
-   `WebOperationContext.CreateXmlResponse`  
  
 Bu yöntemlerin her biri içerik alır ve uygun biçimiyle bir ileti oluşturur. `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` Yöntemi, azalan tercihlere dosyasındaki istemci tarafından tercih edilen biçimler listesini almak için kullanılabilir. Aşağıdaki örnekte nasıl kullanılacağını gösterir `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` kullanın ve ardından kullanır biçimine belirlemek için uygun yanıt iletisi oluşturmak için yanıt yöntemi oluşturun.  
  
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
 <xref:System.UriTemplate>  
 <xref:System.UriTemplateMatch>  
 [WCF Web HTTP programlama modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [UriTemplate ve UriTemplateTable](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)  
 [WCF Web HTTP programlama modeli genel bakış](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)  
 [WCF Web HTTP programlama nesnesi modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
