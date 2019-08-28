---
title: JSON ve XML ile AJAX Hizmeti Örneği
ms.date: 03/30/2017
ms.assetid: 8ea5860d-0c42-4ae9-941a-e07efdd8e29c
ms.openlocfilehash: 62c573a844ce5382308814342330f778fa041a69
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045202"
---
# <a name="ajax-service-with-json-and-xml-sample"></a>JSON ve XML ile AJAX Hizmeti Örneği

Bu örnek, JavaScript Nesne Gösterimi (JSON) veya XML verileri döndüren zaman uyumsuz bir JavaScript ve XML (AJAX) hizmeti oluşturmak için Windows Communication Foundation (WCF) kullanımını gösterir. Bir Web tarayıcısı istemcisinden JavaScript kodu kullanarak bir AJAX hizmetine erişebilirsiniz. Bu örnek, [temel Ajax hizmet](../../../../docs/framework/wcf/samples/basic-ajax-service.md) örneğinde oluşturulur.

Diğer Ajax örneklerinin aksine, bu örnek ASP.NET AJAX ve <xref:System.Web.UI.ScriptManager> denetimini kullanmaz. Bazı ek yapılandırmalar ile, WCF AJAX hizmetlerine JavaScript aracılığıyla herhangi bir HTML sayfasından erişilebilir ve bu senaryo burada gösterilmiştir. WCF 'yi ASP.NET AJAX ile kullanmayla ilgili bir örnek için bkz. [Ajax örnekleri](ajax.md).

Bu örnek, bir işlemin yanıt türünün JSON ve XML arasında nasıl değiştirileceğini gösterir. Bu işlevsellik, hizmetin ASP.NET AJAX tarafından veya bir HTML/JavaScript istemci sayfası tarafından erişilecek şekilde yapılandırılıp yapılandırılmadığına bakılmaksızın kullanılabilir.

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.

Non-ASP.NET AJAX istemcilerinin kullanımını etkinleştirmek için. svc dosyasında ( <xref:System.ServiceModel.Activation.WebServiceHostFactory> Not <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>) kullanın. <xref:System.ServiceModel.Activation.WebServiceHostFactory>hizmete standart <xref:System.ServiceModel.Description.WebHttpEndpoint> bir uç nokta ekler. Uç nokta,. svc dosyasına göre boş bir adreste yapılandırılır; Bu, hizmetin adresinin, işlem adından farklı ek `http://localhost/ServiceModelSamples/service.svc`sonekler olmadan olduğu anlamına gelir.

```svc
<%@ServiceHost language="c#" Debug="true" Service="Microsoft.Samples.XmlAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebServiceHostFactory" %>
```

Web. config dosyasındaki aşağıdaki bölüm, uç noktada ek yapılandırma değişiklikleri yapmak için kullanılabilir. Ek değişiklik gerekmiyorsa bu, kaldırılabilir.

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

İçin varsayılan veri biçimi <xref:System.ServiceModel.Description.WebScriptEndpoint> XML 'dir,ancakiçinvarsayılanveribiçimiJSONolur.<xref:System.ServiceModel.Description.WebHttpEndpoint> Daha fazla bilgi için bkz. [ASP.net olmadan WCF AJAX hizmetleri oluşturma](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md).

Aşağıdaki örnekteki hizmet, iki işlem içeren standart bir WCF hizmetidir. Her iki işlem de <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> , `webHttp` davranışa özgü olan <xref:System.ServiceModel.Web.WebGetAttribute> ve <xref:System.ServiceModel.Web.WebInvokeAttribute> JSON/XML veri biçimi anahtarına hiçbir pul bulunmayan ve özniteliklerde gövde stilini gerektirir.

```csharp
[OperationContract]
[WebInvoke(ResponseFormat = WebMessageFormat.Xml, BodyStyle = WebMessageBodyStyle.Wrapped)]
MathResult DoMathXml(double n1, double n2);
```

İşlemin yanıt biçimi, [ \<Web http >](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) davranışı için varsayılan ayar olan XML olarak belirtilir. Ancak, yanıt biçimini açıkça belirtmek iyi bir uygulamadır.

Diğer işlem `WebInvokeAttribute` özniteliğini kullanır ve yanıt için XML yerine açıkça JSON belirler.

```csharp
[OperationContract]
[WebInvoke(ResponseFormat = WebMessageFormat.Json, BodyStyle = WebMessageBodyStyle.Wrapped)]
MathResult DoMathJson(double n1, double n2);
```

Her iki durumda da işlemler standart bir WCF veri anlaşması türü olan `MathResult`karmaşık bir tür döndürdüğüne de göz önünde.

XmlAjaxClientPage. htm istemci Web sayfası, Kullanıcı **Hesaplama gerçekleştirme (JSON döndürme)** veya sayfadaki **Hesaplama (dönüş XML)** düğmelerini tıklattığında önceki Iki işlemden birini çağıran JavaScript kodunu içerir. Hizmeti çağırmak için kod bir JSON gövdesi oluşturur ve HTTP POST kullanarak gönderir. İstek, [temel Ajax hizmet](../../../../docs/framework/wcf/samples/basic-ajax-service.md) örneği ve ASP.NET Ajax kullanan diğer örneklerin aksine, JavaScript 'te el ile oluşturulur.

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

Hizmet yanıt verdiğinde, yanıt sayfadaki bir metin kutusunda başka işlem yapılmadan görüntülenir. Bu, kullanılan XML ve JSON veri biçimlerini doğrudan gözlemlemeye olanak tanımak için tanıtım amaçlı olarak uygulanır.

```javascript
// Create result handler
xmlHttp.onreadystatechange=function(){
     if(xmlHttp.readyState == 4){
          document.getElementById("result").value = xmlHttp.responseText;
     }
}
```

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\XmlAjaxService`

#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

2. [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümünde açıklandığı gibi XmlAjaxService. sln çözümünü oluşturun.

3. Öğesine `http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm` gidin (proje dizininden tarayıcıda XmlAjaxClientPage. htm dosyasını açmayın).

## <a name="see-also"></a>Ayrıca bkz.

- [HTTP POST Kullanan AJAX Hizmeti](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)
