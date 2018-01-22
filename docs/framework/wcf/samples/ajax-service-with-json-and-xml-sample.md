---
title: "JSON ve XML ile AJAX Hizmeti Örneği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ea5860d-0c42-4ae9-941a-e07efdd8e29c
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7d831d4663031419977b75c6cfe183ac4bd52a86
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="ajax-service-with-json-and-xml-sample"></a>JSON ve XML ile AJAX Hizmeti Örneği
Bu örnek nasıl kullanılacağı ortaya [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] JavaScript nesne gösterimi (JSON) veya XML veri döndüren bir zaman uyumsuz JavaScript ve XML (AJAX) bir hizmet oluşturmak için. Bir AJAX hizmeti bir Web tarayıcısı istemciden JavaScript kodu kullanarak erişebilirsiniz. Bu örnek derlemeler [temel AJAX hizmeti](../../../../docs/framework/wcf/samples/basic-ajax-service.md) örnek.  
  
 Diğer AJAX örnekleri farklı olarak, bu örnek, ASP.NET AJAX kullanmaz ve <xref:System.Web.UI.ScriptManager> denetim. Bazı ek yapılandırma [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] AJAX Hizmetleri, JavaScript aracılığıyla herhangi bir HTML sayfadan erişilebilir ve bu senaryo burada gösterilir. Kullanarak bir örnek için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET AJAX ile bkz [AJAX örnekleri](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).  
  
 Bu örnek, JSON ve XML arasında bir işlem yanıt türünü geçiş gösterilmektedir. Bu işlevsellik, olup hizmet ASP.NET AJAX veya bir HTML/JavaScript istemci sayfası tarafından erişilebilmesi için yapılandırılan bağımsız olarak kullanılabilir.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 ASP.NET AJAX istemcileri kullanımını etkinleştirmek için kullanın <xref:System.ServiceModel.Activation.WebServiceHostFactory> (değil <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>) .svc dosyasındaki. <xref:System.ServiceModel.Activation.WebServiceHostFactory>ekler bir <xref:System.ServiceModel.Description.WebHttpEndpoint> hizmetine standart uç noktası. Uç nokta .svc dosyasıyla ilişkili boş bir adresindeki yapılandırılmıştır; Bu hizmet adresini işlemi adı dışında hiçbir ek sonekleri http://localhost/ServiceModelSamples/service.svc anlamına gelir.  
  
```html  
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
  
 Aşağıdaki örnek hizmetinde bir standarttır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmeti iki işlem ile. İki işlem gerektiren <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> Gövde stili <xref:System.ServiceModel.Web.WebGetAttribute> veya <xref:System.ServiceModel.Web.WebInvokeAttribute> özel öznitelikleri `webHttp` davranışı ve şifrelemeyle JSON/XML veri biçimi anahtarı vardır.  
  
```  
[OperationContract]  
[WebInvoke(ResponseFormat = WebMessageFormat.Xml, BodyStyle = WebMessageBodyStyle.Wrapped)]  
MathResult DoMathXml(double n1, double n2);  
```  
  
 İşlem yanıt biçimi varsayılan değer XML olarak belirtilen ayarını [ \<webHttp >](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) davranışı. Ancak, iyi açıkça bir yöntemdir yanıt biçimi belirtin.  
  
 Başka bir işlem kullanır `WebInvokeAttribute` özniteliği ve XML yerine JSON yanıt için açıkça belirtir.  
  
```  
[OperationContract]  
[WebInvoke(ResponseFormat = WebMessageFormat.Json, BodyStyle = WebMessageBodyStyle.Wrapped)]  
MathResult DoMathJson(double n1, double n2);  
```  
  
 Her iki durumda da, karmaşık bir tür işlemler geri bildirdiğine dikkat edin `MathResult`, bir standart olduğu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] veri sözleşme türü.  
  
 İstemci Web sayfası XmlAjaxClientPage.htm kullanıcı tıkladığında, önceki iki işlemlerden birini çağırır JavaScript kodu içeren **(dönüş JSON) hesaplamayı** veya **hesaplamayı (dönüş XML)**  sayfasında düğmeler. Hizmetini çağırmak için kodu JSON gövdesi oluşturur ve HTTP POST kullanarak gönderir. İstek el ile aksine, JavaScript'te oluşturulduğunda [temel AJAX hizmeti](../../../../docs/framework/wcf/samples/basic-ajax-service.md) örnek ve ASP.NET AJAX kullanılarak diğer örnekleri.  
  
```  
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
  
```  
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
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\XmlAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm XmlAjaxService.sln açıklandığı gibi yapı [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  İçin http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm gidin (XmlAjaxClientPage.htm proje dizininden tarayıcıda aç değil).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [HTTP POST Kullanan AJAX Hizmeti](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)
