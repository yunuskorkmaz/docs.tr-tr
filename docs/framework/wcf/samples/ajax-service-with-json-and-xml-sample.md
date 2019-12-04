---
title: JSON ve XML ile AJAX Hizmeti Örneği
ms.date: 03/30/2017
ms.assetid: 8ea5860d-0c42-4ae9-941a-e07efdd8e29c
ms.openlocfilehash: ca9bdbfa135ac7dc0b69589d4f8fce07bc4c4afe
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716211"
---
# <a name="ajax-service-with-json-and-xml-sample"></a>JSON ve XML ile AJAX Hizmeti Örneği

Bu örnek, JavaScript Nesne Gösterimi (JSON) veya XML verileri döndüren zaman uyumsuz bir JavaScript ve XML (AJAX) hizmeti oluşturmak için Windows Communication Foundation (WCF) kullanımını gösterir. Bir Web tarayıcısı istemcisinden JavaScript kodu kullanarak bir AJAX hizmetine erişebilirsiniz. Bu örnek, [temel Ajax hizmet](../../../../docs/framework/wcf/samples/basic-ajax-service.md) örneğinde oluşturulur.

Diğer AJAX örneklerinin aksine bu örnek, ASP.NET AJAX ve <xref:System.Web.UI.ScriptManager> denetimini kullanmaz. Bazı ek yapılandırmalar ile, WCF AJAX hizmetlerine JavaScript aracılığıyla herhangi bir HTML sayfasından erişilebilir ve bu senaryo burada gösterilmiştir. WCF 'yi ASP.NET AJAX ile kullanmayla ilgili bir örnek için bkz. [Ajax örnekleri](ajax.md).

Bu örnek, bir işlemin yanıt türünün JSON ve XML arasında nasıl değiştirileceğini gösterir. Bu işlevsellik, hizmetin ASP.NET AJAX tarafından veya bir HTML/JavaScript istemci sayfası tarafından erişilecek şekilde yapılandırılıp yapılandırılmadığına bakılmaksızın kullanılabilir.

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.

Non-ASP.NET AJAX istemcilerinin kullanımını etkinleştirmek için. svc dosyasında <xref:System.ServiceModel.Activation.WebServiceHostFactory> (<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>değil) kullanın. <xref:System.ServiceModel.Activation.WebServiceHostFactory> hizmete <xref:System.ServiceModel.Description.WebHttpEndpoint> bir standart uç nokta ekler. Uç nokta,. svc dosyasına göre boş bir adreste yapılandırılır; Bu, hizmet adresinin, işlem adından farklı ek sonekler olmadan `http://localhost/ServiceModelSamples/service.svc`olduğu anlamına gelir.

`<%@ServiceHost language="c#" Debug="true" Service="Microsoft.Samples.XmlAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebServiceHostFactory" %>`

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

<xref:System.ServiceModel.Description.WebHttpEndpoint> için varsayılan veri biçimi XML 'dir, ancak <xref:System.ServiceModel.Description.WebScriptEndpoint> için varsayılan veri biçimi JSON olur. Daha fazla bilgi için bkz. [ASP.net olmadan WCF AJAX hizmetleri oluşturma](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md).

Aşağıdaki örnekteki hizmet, iki işlem içeren standart bir WCF hizmetidir. Her iki işlem de, `webHttp` davranışına özgü olan ve JSON/XML veri biçimi anahtarında hiçbir pul bulunmayan <xref:System.ServiceModel.Web.WebGetAttribute> veya <xref:System.ServiceModel.Web.WebInvokeAttribute> özniteliklerde <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> gövde stilini gerektirir.

```csharp
[OperationContract]
[WebInvoke(ResponseFormat = WebMessageFormat.Xml, BodyStyle = WebMessageBodyStyle.Wrapped)]
MathResult DoMathXml(double n1, double n2);
```

İşlemin yanıt biçimi XML olarak belirtilir, bu, [\<webHttp >](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) davranışı için varsayılan ayardır. Ancak, yanıt biçimini açıkça belirtmek iyi bir uygulamadır.

Diğer işlem `WebInvokeAttribute` özniteliğini kullanır ve yanıt için XML yerine açıkça JSON belirler.

```csharp
[OperationContract]
[WebInvoke(ResponseFormat = WebMessageFormat.Json, BodyStyle = WebMessageBodyStyle.Wrapped)]
MathResult DoMathJson(double n1, double n2);
```

Her iki durumda da işlemler, standart bir WCF veri sözleşmesi türü olan `MathResult`karmaşık bir tür döndürdüğüne göz önünde bulunur.

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
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\XmlAjaxService`

#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

2. [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümünde açıklandığı gibi XmlAjaxService. sln çözümünü oluşturun.

3. `http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm` gidin (proje dizininden tarayıcıda XmlAjaxClientPage. htm dosyasını açmayın).

## <a name="see-also"></a>Ayrıca bkz.

- [HTTP POST Kullanan AJAX Hizmeti](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)
