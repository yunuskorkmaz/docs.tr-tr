---
title: ASP.NET Olmadan WCF AJAX Hizmetleri Oluşturma
ms.date: 03/30/2017
ms.assetid: ba4a7d1b-e277-4978-9f62-37684e6dc934
ms.openlocfilehash: b5f0f730f90227dcccc7e5ebf533d80a28f6e6eb
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599301"
---
# <a name="creating-wcf-ajax-services-without-aspnet"></a>ASP.NET Olmadan WCF AJAX Hizmetleri Oluşturma
Windows Communication Foundation (WCF) AJAX hizmetlerine, ASP.NET AJAX gerekmeden JavaScript etkin herhangi bir Web sayfasından erişilebilir. Bu konuda, böyle bir WCF hizmetinin nasıl oluşturulacağı açıklanmaktadır.  
  
 WCF 'yi ASP.NET AJAX ile kullanmayla ilgili yönergeler için bkz. [ASP.NET AJAX IçIN WCF Hizmetleri oluşturma](creating-wcf-services-for-aspnet-ajax.md).  
  
 WCF AJAX Hizmeti oluşturmanın üç bölümü vardır:  
  
- Tarayıcıdan erişilebilen bir AJAX uç noktası oluşturma.  
  
- AJAX uyumlu hizmet sözleşmesi oluşturma.  
  
- WCF AJAX hizmetlerine erişme.  
  
## <a name="creating-an-ajax-endpoint"></a>AJAX uç noktası oluşturma  
 Bir WCF hizmetinde AJAX desteğini etkinleştirmenin en temel yolu, <xref:System.ServiceModel.Activation.WebServiceHostFactory> Aşağıdaki örnekte olduğu gibi hizmeti ile ilişkili. svc dosyasında kullanmaktır.  
  
```text
<%ServiceHost
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CityService"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory  
%>  
```  
  
 Alternatif olarak, bir AJAX uç noktası eklemek için yapılandırma da kullanabilirsiniz. Hizmet uç noktasında öğesini kullanın <xref:System.ServiceModel.WebHttpBinding> ve bu uç noktayı <xref:System.ServiceModel.Description.WebHttpBehavior> Aşağıdaki kod parçacığında gösterildiği gibi ile yapılandırın.  
  
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
  
 Çalışan bir örnek için bkz. [JSON ve XML Ile AJAX Hizmeti](../samples/ajax-service-with-json-and-xml-sample.md).  
  
## <a name="creating-an-ajax-compatible-service-contract"></a>AJAX uyumlu hizmet sözleşmesi oluşturma  
 Varsayılan olarak, bir AJAX uç noktası üzerinden kullanıma sunulan hizmet sözleşmeleri XML biçimindeki verileri döndürür. Ayrıca, varsayılan olarak hizmet işlemlerine, aşağıdaki örnekte gösterildiği gibi, uç nokta adresini ve ardından işlem adını içeren URL 'lere HTTP POST istekleri aracılığıyla erişilebilir.  
  
```csharp
[OperationContract]  
string[] GetCities(string firstLetters);  
```  
  
 Bu işleme bir HTTP POST ile erişilebilir `http://serviceaddress/endpointaddress/GetCities` ve BIR XML iletisi döndürülür.  
  
 Bu temel yönleri özelleştirmek için tam Web programlama modelini kullanabilirsiniz. Örneğin, <xref:System.ServiceModel.Web.WebGetAttribute> veya <xref:System.ServiceModel.Web.WebInvokeAttribute> özniteliklerini kullanarak işlemin yanıt verdiği http fiilini denetleyebilir veya `UriTemplate` özel URI 'leri belirtmek için bu ilgili özniteliklerin özelliğini kullanabilirsiniz. Daha fazla bilgi için bkz. [WCF Web http programlama modeli](wcf-web-http-programming-model.md) konusu.  
  
 JSON veri biçimi genellikle AJAX hizmetlerinde kullanılır. XML yerine JSON döndüren bir işlem oluşturmak için <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> (veya <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> ) özelliğini olarak ayarlayın <xref:System.ServiceModel.Web.WebMessageFormat.Json> . [Tek BAŞıNA JSON serileştirme](stand-alone-json-serialization.md) konusu, yerleşik .net türlerinin ve veri SÖZLEŞMESI türlerinin JSON ile nasıl eşlendiğini gösterir.  
  
 Normal olarak, JSON istekleri ve yanıtları yalnızca bir öğeden oluşur. Önceki işlem için `GetCities` , istek aşağıdaki ifadeye benzer.  
  
```json
"na"  
```  
  
 Bu isteğin yanıtı aşağıdaki ifadeye benzer.  
  
```json
["Nairobi", "Naples", "Nashville"]  
```  
  
 İşlem ek bir parametre alırsa, her iki parametreyi de tek bir JSON nesnesinde sarmalamak için istek stili sarmalanmış olmalıdır. Bu stil JSON iletisine bir örnek aşağıdaki örnekte verilmiştir.  
  
```json  
{"firstLetters": "na", "maxNumber": 2}  
```  
  
 Aşağıdaki sözleşme bu iletiyi kabul eder.  
  
```csharp
[WebInvoke(BodyStyle=WebMessageBodyStyle.WrappedRequest, ResponseFormat=WebMessageFormat.Json)]  
[OperationContract]  
string[] GetCities(string firstLetters, int maxNumber);  
```  
  
## <a name="accessing-ajax-services"></a>AJAX hizmetlerine erişme  
 WCF AJAX uç noktaları her zaman hem JSON hem de XML isteklerini kabul eder.  
  
 İçerik türü "Application/JSON" olan HTTP POST istekleri JSON olarak değerlendirilir ve XML 'yi (örneğin, "text/xml") gösteren içerik türü olanlar XML olarak değerlendirilir.  
  
 HTTP GET istekleri, URL 'deki tüm istek parametrelerini içerir.  
  
 Bu, uç noktaya HTTP isteğinin nasıl oluşturulacağını belirlemek için kullanıcıya kadar yapılır. Ayrıca, kullanıcının isteğin gövdesini oluşturan JSON 'u oluşturmak için tam denetimi vardır. JavaScript 'ten bir istek oluşturma örneği için bkz. [JSON ve XML Ile AJAX Hizmeti](../samples/ajax-service-with-json-and-xml-sample.md).
