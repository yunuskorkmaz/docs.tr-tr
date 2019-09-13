---
title: ASP.NET Olmadan WCF AJAX Hizmetleri Oluşturma
ms.date: 03/30/2017
ms.assetid: ba4a7d1b-e277-4978-9f62-37684e6dc934
ms.openlocfilehash: 04d2831407f4aa32c72aabbbff0e6fdde769bd23
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895096"
---
# <a name="creating-wcf-ajax-services-without-aspnet"></a>ASP.NET Olmadan WCF AJAX Hizmetleri Oluşturma
Windows Communication Foundation (WCF) AJAX hizmetlerine, ASP.NET AJAX gerekmeden JavaScript etkin herhangi bir Web sayfasından erişilebilir. Bu konuda, böyle bir WCF hizmetinin nasıl oluşturulacağı açıklanmaktadır.  
  
 WCF 'yi ASP.NET AJAX ile kullanmayla ilgili yönergeler için bkz. [ASP.NET AJAX IçIN WCF Hizmetleri oluşturma](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md).  
  
 WCF AJAX Hizmeti oluşturmanın üç bölümü vardır:  
  
- Tarayıcıdan erişilebilen bir AJAX uç noktası oluşturma.  
  
- AJAX uyumlu hizmet sözleşmesi oluşturma.  
  
- WCF AJAX hizmetlerine erişme.  
  
## <a name="creating-an-ajax-endpoint"></a>AJAX uç noktası oluşturma  
 Bir WCF hizmetinde Ajax desteğini etkinleştirmenin en temel yolu, aşağıdaki örnekte olduğu gibi hizmeti ile <xref:System.ServiceModel.Activation.WebServiceHostFactory> ilişkili. svc dosyasında kullanmaktır.  
  
```text
<%ServiceHost   
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CityService"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory  
%>  
```  
  
 Alternatif olarak, bir AJAX uç noktası eklemek için yapılandırma da kullanabilirsiniz. Hizmet uç noktasında öğesini kullanın ve bu uç noktayı aşağıdaki kod parçacığında <xref:System.ServiceModel.Description.WebHttpBehavior> gösterildiği gibi ile yapılandırın. <xref:System.ServiceModel.WebHttpBinding>  
  
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
  
 Çalışan bir örnek için bkz. [JSON ve XML Ile AJAX Hizmeti](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).  
  
## <a name="creating-an-ajax-compatible-service-contract"></a>AJAX uyumlu hizmet sözleşmesi oluşturma  
 Varsayılan olarak, bir AJAX uç noktası üzerinden kullanıma sunulan hizmet sözleşmeleri XML biçimindeki verileri döndürür. Ayrıca, varsayılan olarak hizmet işlemlerine, aşağıdaki örnekte gösterildiği gibi, uç nokta adresini ve ardından işlem adını içeren URL 'lere HTTP POST istekleri aracılığıyla erişilebilir.  
  
```csharp
[OperationContract]  
string[] GetCities(string firstLetters);  
```  
  
 Bu işleme bir http post `http://serviceaddress/endpointaddress/GetCities` ile erişilebilir ve bir XML iletisi döndürülür.  
  
 Bu temel yönleri özelleştirmek için tam Web programlama modelini kullanabilirsiniz. Örneğin, <xref:System.ServiceModel.Web.WebGetAttribute> veya <xref:System.ServiceModel.Web.WebInvokeAttribute> özniteliklerini kullanarak `UriTemplate` işlemin yanıt verdiği http fiilini denetleyebilir veya özel URI 'leri belirtmek için bu ilgili özniteliklerin özelliğini kullanabilirsiniz. Daha fazla bilgi için bkz. [WCF Web http programlama modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md) konusu.  
  
 JSON veri biçimi genellikle AJAX hizmetlerinde kullanılır. XML yerine JSON döndüren bir işlem oluşturmak için <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> ( <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>veya) özelliğini olarak <xref:System.ServiceModel.Web.WebMessageFormat.Json>ayarlayın. [Tek BAŞıNA JSON serileştirme](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md) konusu, yerleşik .net türlerinin ve veri SÖZLEŞMESI türlerinin JSON ile nasıl eşlendiğini gösterir.  
  
 Normal olarak, JSON istekleri ve yanıtları yalnızca bir öğeden oluşur. Önceki `GetCities` işlem için, istek aşağıdaki ifadeye benzer.  
  
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
  
 Bu, uç noktaya HTTP isteğinin nasıl oluşturulacağını belirlemek için kullanıcıya kadar yapılır. Ayrıca, kullanıcının isteğin gövdesini oluşturan JSON 'u oluşturmak için tam denetimi vardır. JavaScript 'ten bir istek oluşturma örneği için bkz. [JSON ve XML Ile AJAX Hizmeti](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).
