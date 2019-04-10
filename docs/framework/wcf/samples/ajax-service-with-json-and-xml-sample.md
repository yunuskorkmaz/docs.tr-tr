---
title: JSON ve XML ile AJAX Hizmeti Örneği
ms.date: 03/30/2017
ms.assetid: 8ea5860d-0c42-4ae9-941a-e07efdd8e29c
ms.openlocfilehash: e5f2838575b212f6b95fd01b469d771017ef534c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207493"
---
# <a name="ajax-service-with-json-and-xml-sample"></a>JSON ve XML ile AJAX Hizmeti Örneği
Bu örnek, Windows Communication Foundation (WCF) JavaScript nesne gösterimi (JSON) veya XML veri döndüren bir zaman uyumsuz JavaScript ve XML (AJAX) hizmet oluşturma için nasıl kullanılacağını gösterir. JavaScript kodu bir Web tarayıcısı istemcisini kullanarak bir AJAX hizmete erişebilir. Bu örnek yapılar [temel AJAX hizmeti](../../../../docs/framework/wcf/samples/basic-ajax-service.md) örnek.  
  
 Diğer AJAX örnekleri farklı olarak, bu örnek, ASP.NET AJAX kullanmaz ve <xref:System.Web.UI.ScriptManager> denetimi. Bazı ek yapılandırma ile WCF AJAX Hizmetleri herhangi bir HTML sayfasında JavaScript üzerinden erişilebilir ve bu senaryo burada gösterilir. ASP.NET AJAX ile WCF kullanan bir örnek için bkz: [AJAX örnekleri](ajax.md).
  
 Bu örnekte yanıt türü bir işlemin JSON ve XML arasında geçiş yapma gösterilmektedir. Bu işlev, mi hizmeti ASP.NET AJAX veya bir HTML/JavaScript istemci sayfası tarafından erişilecek yapılandırılmış bağımsız olarak kullanılabilir.  
  
> [!NOTE]
> Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.
  
ASP.NET AJAX istemci kullanımını etkinleştirmek için <xref:System.ServiceModel.Activation.WebServiceHostFactory> (değil <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>) .svc dosyasında. <xref:System.ServiceModel.Activation.WebServiceHostFactory> ekler bir <xref:System.ServiceModel.Description.WebHttpEndpoint> hizmetine standart uç noktası. Uç nokta, boş bir adresten .svc dosyanın göreli yapılandırılır; Bu hizmet adresini olduğu anlamına gelir `http://localhost/ServiceModelSamples/service.svc`, işlem adı dışında hiçbir ek sonekleri ile.  
  
```svc
<%@ServiceHost language="c#" Debug="true" Service="Microsoft.Samples.XmlAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebServiceHostFactory" %>  
```  
  
 Web.config dosyasında aşağıdaki bölümde, uç nokta için ek yapılandırma değişiklikleri yapmak için kullanılabilir. Hiçbir ek değişikliklerin gerekli olup olmadığını kaldırılabilir.  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <!-- Use this element to configure the endpoint -->  
      <standardEndpoint name="" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 Varsayılan verilerin biçimlendirilmesi için <xref:System.ServiceModel.Description.WebHttpEndpoint> XML için varsayılan veri biçimi çalışırken olduğu <xref:System.ServiceModel.Description.WebScriptEndpoint> JSON. Daha fazla bilgi için [ASP.NET olmadan WCF AJAX hizmetleri oluşturma](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md).  
  
 Aşağıdaki örnekte iki işlem ile standart bir WCF Hizmeti hizmetidir. Her iki işlem gerektiren <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> gövde stilini <xref:System.ServiceModel.Web.WebGetAttribute> veya <xref:System.ServiceModel.Web.WebInvokeAttribute> özel öznitelikler `webHttp` davranışı ve JSON/XML veri biçimi anahtarda ilgisi yoktur.  

```csharp
[OperationContract]  
[WebInvoke(ResponseFormat = WebMessageFormat.Xml, BodyStyle = WebMessageBodyStyle.Wrapped)]  
MathResult DoMathXml(double n1, double n2);  
```

 Varsayılan olan XML olarak yanıt biçimi işlemi için belirtilen ayarlama [ \<webHttp >](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) davranışı. Ancak, bunu açıkça alışkanlıktır yanıt biçimi belirtin.  
  
 Başka bir işlem kullandığı `WebInvokeAttribute` özniteliği ve XML yerine JSON yanıtı açıkça belirtir.  

```csharp
[OperationContract]  
[WebInvoke(ResponseFormat = WebMessageFormat.Json, BodyStyle = WebMessageBodyStyle.Wrapped)]  
MathResult DoMathJson(double n1, double n2);  
```

 Her iki durumda da karmaşık bir tür işlemleri iade Not `MathResult`, standart bir WCF veri anlaşması türü.  
  
 İstemci Web sayfası XmlAjaxClientPage.htm kullanıcı tıkladığında, önceki iki işlemlerden birini çağırır JavaScript kodu içeren **(dönüş JSON'u) hesaplamayı** veya **hesaplamayı (dönüş XML)**  sayfasında düğme. Hizmeti çağırmak için kodu, bir JSON gövdesi oluşturur ve HTTP POST kullanarak gönderir. İstek, aksine JavaScript'te el ile oluşturulduğunda [temel AJAX hizmeti](../../../../docs/framework/wcf/samples/basic-ajax-service.md) örnek ve ASP.NET AJAX kullanılarak diğer örnekleri.  

```csharp
// Create HTTP request  
var xmlHttp;  
// Request instantiation code omitted…  
// Result handler code omitted…  
  
// Build the operation URL  
var url = "service.svc/ajaxEndpoint/";  
url = url + operation;  
  
// Build the body of the JSON message  
var body = '{"n1":';  
body = body + document.getElementById("num1").value + ',"n2":';  
body = body + document.getElementById("num2").value + '}';  
  
// Send the HTTP request  
xmlHttp.open("POST", url, true);  
xmlHttp.setRequestHeader("Content-type", "application/json");  
xmlHttp.send(body);  
```

 Hizmet yanıt verdiğinde yanıt herhangi başka bir metin kutusuna sayfasında işlem olmadan görüntülenir. Bu, doğrudan kullanılan XML ve JSON veri biçimlerini gözlemleyin olanak sağlamak tanıtım amacıyla uygulanır.  

```javascript
// Create result handler   
xmlHttp.onreadystatechange=function(){  
     if(xmlHttp.readyState == 4){  
          document.getElementById("result").value = xmlHttp.responseText;  
     }  
}  
```

> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\XmlAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  ' % S'çözüm XmlAjaxService.sln açıklandığı gibi oluşturmak [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Gidin `http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm` (XmlAjaxClientPage.htm proje dizininden tarayıcıda aç değil).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [HTTP POST Kullanan AJAX Hizmeti](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)
