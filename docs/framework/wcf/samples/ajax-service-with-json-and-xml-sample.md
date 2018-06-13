---
title: JSON ve XML ile AJAX Hizmeti Örneği
ms.date: 03/30/2017
ms.assetid: 8ea5860d-0c42-4ae9-941a-e07efdd8e29c
ms.openlocfilehash: 32964c287b0064daf529aa4c1e28f0927d29a6d5
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33807351"
---
# <a name="ajax-service-with-json-and-xml-sample"></a>JSON ve XML ile AJAX Hizmeti Örneği
Bu örnek, JavaScript nesne gösterimi (JSON) veya XML veri döndüren bir zaman uyumsuz JavaScript ve XML (AJAX) bir hizmet oluşturmak için Windows Communication Foundation (WCF) kullanımı gösterilmiştir. Bir AJAX hizmeti bir Web tarayıcısı istemciden JavaScript kodu kullanarak erişebilirsiniz. Bu örnek derlemeler [temel AJAX hizmeti](../../../../docs/framework/wcf/samples/basic-ajax-service.md) örnek.  
  
 Diğer AJAX örnekleri farklı olarak, bu örnek, ASP.NET AJAX kullanmaz ve <xref:System.Web.UI.ScriptManager> denetim. Bazı ek yapılandırma WCF AJAX Hizmetleri herhangi bir HTML sayfasında JavaScript aracılığıyla erişilebilen ve bu senaryo burada gösterilir. WCF ile ASP.NET AJAX kullanılarak bir örnek için bkz: [AJAX örnekleri](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).  
  
 Bu örnek, JSON ve XML arasında bir işlem yanıt türünü geçiş gösterilmektedir. Bu işlevsellik, olup hizmet ASP.NET AJAX veya bir HTML/JavaScript istemci sayfası tarafından erişilebilmesi için yapılandırılan bağımsız olarak kullanılabilir.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 ASP.NET AJAX istemcileri kullanımını etkinleştirmek için kullanın <xref:System.ServiceModel.Activation.WebServiceHostFactory> (değil <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>) .svc dosyasındaki. <xref:System.ServiceModel.Activation.WebServiceHostFactory> ekler bir <xref:System.ServiceModel.Description.WebHttpEndpoint> hizmetine standart uç noktası. Uç nokta .svc dosyasıyla ilişkili boş bir adresindeki yapılandırılmıştır; Bu hizmet adresini anlamına gelir http://localhost/ServiceModelSamples/service.svc, işlem adı dışında hiçbir ek sonek ile.  
  
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
  
 Varsayılan verilerin biçimlendirilmesi için <xref:System.ServiceModel.Description.WebHttpEndpoint> , varsayılan veri biçimi sırasında XML'dir <xref:System.ServiceModel.Description.WebScriptEndpoint> JSON. Daha fazla bilgi için bkz: [ASP.NET olmadan WCF AJAX hizmetleri oluşturma](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md).  
  
 Aşağıdaki örnekte iki işlem ile standart bir WCF Hizmeti hizmetidir. İki işlem gerektiren <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> Gövde stili <xref:System.ServiceModel.Web.WebGetAttribute> veya <xref:System.ServiceModel.Web.WebInvokeAttribute> özel öznitelikleri `webHttp` davranışı ve şifrelemeyle JSON/XML veri biçimi anahtarı vardır.  

```csharp
[OperationContract]  
[WebInvoke(ResponseFormat = WebMessageFormat.Xml, BodyStyle = WebMessageBodyStyle.Wrapped)]  
MathResult DoMathXml(double n1, double n2);  
```

 İşlem yanıt biçimi varsayılan değer XML olarak belirtilen ayarını [ \<webHttp >](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) davranışı. Ancak, iyi açıkça bir yöntemdir yanıt biçimi belirtin.  
  
 Başka bir işlem kullanır `WebInvokeAttribute` özniteliği ve XML yerine JSON yanıt için açıkça belirtir.  

```csharp
[OperationContract]  
[WebInvoke(ResponseFormat = WebMessageFormat.Json, BodyStyle = WebMessageBodyStyle.Wrapped)]  
MathResult DoMathJson(double n1, double n2);  
```

 Her iki durumda da, karmaşık bir tür işlemler geri bildirdiğine dikkat edin `MathResult`, standart bir WCF veri sözleşmesi türü değil.  
  
 İstemci Web sayfası XmlAjaxClientPage.htm kullanıcı tıkladığında, önceki iki işlemlerden birini çağırır JavaScript kodu içeren **(dönüş JSON) hesaplamayı** veya **hesaplamayı (dönüş XML)**  sayfasında düğmeler. Hizmetini çağırmak için kodu JSON gövdesi oluşturur ve HTTP POST kullanarak gönderir. İstek el ile aksine, JavaScript'te oluşturulduğunda [temel AJAX hizmeti](../../../../docs/framework/wcf/samples/basic-ajax-service.md) örnek ve ASP.NET AJAX kullanılarak diğer örnekleri.  

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

 Hizmet yanıtladığında yanıt herhangi bir metin kutusuna sayfasında işlenmesi olmadan görüntülenir. Bu tanıtım amacıyla kullanılan XML ve JSON veri biçimleri doğrudan gözlemlemek olanak tanımak uygulanır.  

```javascript
// Create result handler   
xmlHttp.onreadystatechange=function(){  
     if(xmlHttp.readyState == 4){  
          document.getElementById("result").value = xmlHttp.responseText;  
     }  
}  
```

> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\XmlAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm XmlAjaxService.sln açıklandığı gibi yapı [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Gidin http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm (XmlAjaxClientPage.htm proje dizininden tarayıcıda aç değil).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [HTTP POST Kullanan AJAX Hizmeti](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)
