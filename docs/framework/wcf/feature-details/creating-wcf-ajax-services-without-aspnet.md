---
title: ASP.NET Olmadan WCF AJAX Hizmetleri Oluşturma
ms.date: 03/30/2017
ms.assetid: ba4a7d1b-e277-4978-9f62-37684e6dc934
ms.openlocfilehash: f4d1d093132c501844aacbaa9cf28ecc3cede442
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185232"
---
# <a name="creating-wcf-ajax-services-without-aspnet"></a>ASP.NET Olmadan WCF AJAX Hizmetleri Oluşturma
Windows Communication Foundation (WCF) AJAX hizmetlerine, JAVAScript özellikli herhangi bir Web sayfasından, ASP.NET AJAX gerektirmeden erişilebilir. Bu konu, böyle bir WCF hizmetinin nasıl oluşturulacak olduğunu açıklar.  
  
 ASP.NET AJAX ile WCF kullanma ile ilgili talimatlar [için, ASP.NET AJAX için WCF Hizmetleri Oluşturma'ya](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)bakın.  
  
 WCF AJAX hizmeti oluşturmanın üç bölümü vardır:  
  
- Tarayıcıdan erişilebilen bir AJAX bitiş noktası oluşturma.  
  
- AJAX uyumlu bir hizmet sözleşmesi oluşturma.  
  
- WCF AJAX hizmetlerine erişim.  
  
## <a name="creating-an-ajax-endpoint"></a>AJAX Bitiş Noktası Oluşturma  
 Bir WCF hizmetinde AJAX desteğini etkinleştirmenin en <xref:System.ServiceModel.Activation.WebServiceHostFactory> temel yolu, aşağıdaki örnekte olduğu gibi hizmetle ilişkili .svc dosyasındakini kullanmaktır.  
  
```text
<%ServiceHost
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CityService"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory  
%>  
```  
  
 Alternatif olarak, bir AJAX bitiş noktası eklemek için yapılandırmayı da kullanabilirsiniz. <xref:System.ServiceModel.WebHttpBinding> Hizmet bitiş noktasını kullanın ve bu bitiş noktasını <xref:System.ServiceModel.Description.WebHttpBehavior> aşağıdaki kod parçacığında gösterildiği gibi yapılandırın.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="AjaxBehavior">  
          <webHttp/>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <services>  
      <service name="Microsoft.Ajax.Samples.CityService">  
        <endpoint
          address="ajaxEndpoint"  
          behaviorConfiguration="AjaxBehavior"  
          binding="webHttpBinding"  
          contract="Microsoft.Ajax.Samples.ICityService" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 Çalışma örneği [için, JSON ve XML ile AJAX Hizmeti'ne](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md)bakın.  
  
## <a name="creating-an-ajax-compatible-service-contract"></a>AJAX Uyumlu Hizmet Sözleşmesi Oluşturma  
 Varsayılan olarak, XML formatında bir AJAX uç nokta iade verileri üzerinde maruz kalan hizmet sözleşmeleri. Ayrıca, varsayılan olarak hizmet işlemlerine, aşağıdaki örnekte gösterildiği gibi, işlem adının ardından gelen bitiş noktası adresini içeren URL'lere HTTP POST istekleri aracılığıyla erişilebilir.  
  
```csharp
[OperationContract]  
string[] GetCities(string firstLetters);  
```  
  
 Bu işlem, bir XML `http://serviceaddress/endpointaddress/GetCities` iletisine http post kullanarak erişilebilir ve döndürülebiliyor.  
  
 Bu temel yönleri özelleştirmek için tam Web Programlama Modeli kullanabilirsiniz. Örneğin, işlemin yanıtlandığı <xref:System.ServiceModel.Web.WebGetAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> HTTP fiilini denetlemek veya özel IU'ları `UriTemplate` belirtmek için bu özniteliklerin özelliğini kullanmak için öznitelikleri kullanabilirsiniz. Daha fazla bilgi için [WCF Web HTTP Programlama Modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md) konusuna bakın.  
  
 JSON veri formatı genellikle AJAX hizmetlerinde kullanılır. XML yerine JSON döndüren bir işlem <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> oluşturmak <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>için, <xref:System.ServiceModel.Web.WebMessageFormat.Json>(veya) özelliğini . [Tek Başına JSON Serileştirme](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md) konusu, yerleşik .NET türlerinin ve veri sözleşmesi türlerinin JSON ile nasıl eşleşiş gösterdiğini gösterir.  
  
 Normalde, JSON istekleri ve yanıtları yalnızca bir öğeden oluşur. Önceki `GetCities` işlem için istek aşağıdaki ifadeye benzer.  
  
```json
"na"  
```  
  
 Bu isteğe yanıt aşağıdaki ifadeye benzer.  
  
```json
["Nairobi", "Naples", "Nashville"]  
```  
  
 İşlem fazladan bir parametre alıyorsa, istek stilinin her iki parametreyi de tek bir JSON nesnesine sarmak için sarılması gerekir. Bu stil JSON iletisinin bir örneği aşağıdaki örnektedir.  
  
```json  
{"firstLetters": "na", "maxNumber": 2}  
```  
  
 Aşağıdaki sözleşme bu iletiyi kabul eder.  
  
```csharp
[WebInvoke(BodyStyle=WebMessageBodyStyle.WrappedRequest, ResponseFormat=WebMessageFormat.Json)]  
[OperationContract]  
string[] GetCities(string firstLetters, int maxNumber);  
```  
  
## <a name="accessing-ajax-services"></a>AJAX Hizmetlerine Erişim  
 WCF AJAX uç noktaları her zaman hem JSON hem de XML isteklerini kabul eylemektedir.  
  
 "Uygulama/json" içerik türüne sahip HTTP POST istekleri JSON olarak kabul edilir ve XML 'yi (örneğin, "text/xml") gösteren içerik türüne sahip olanlar XML olarak kabul edilir.  
  
 HTTP GET istekleri, URL'deki tüm istek parametrelerini içerir.  
  
 BU HTTP isteğini bitiş noktasına nasıl oluşturacağına karar vermek kullanıcıya kaçıktır. Ayrıca, kullanıcı istek gövdesini oluşturan JSON oluşturma üzerinde tam kontrole sahiptir. JavaScript'ten istek oluşturma örneği için [JSON ve XML içeren AJAX Hizmeti'ne](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md)bakın.
