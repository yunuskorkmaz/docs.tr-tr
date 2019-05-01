---
title: ASP.NET Olmadan WCF AJAX Hizmetleri Oluşturma
ms.date: 03/30/2017
ms.assetid: ba4a7d1b-e277-4978-9f62-37684e6dc934
ms.openlocfilehash: 77a850408c3d952dbd4f682ea704d3248ae17c3e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857213"
---
# <a name="creating-wcf-ajax-services-without-aspnet"></a>ASP.NET Olmadan WCF AJAX Hizmetleri Oluşturma
Windows Communication Foundation (WCF) AJAX Hizmetleri, ASP.NET AJAX gerek kalmadan, tüm JavaScript etkin Web sayfasından erişilebilir. Bu konuda bu tür bir WCF hizmeti oluşturma işlemini açıklar.  
  
 ASP.NET AJAX ile WCF kullanma ile ilgili yönergeler için bkz: [ASP.NET AJAX için WCF hizmetleri oluşturma](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md).  
  
 Bir WCF AJAX hizmeti oluşturmanın üç bölümü vardır:  
  
- Bir AJAX uç noktası oluşturma bir tarayıcıdan erişilebilir.  
  
- Bir AJAX uyumlu hizmet anlaşması oluşturuluyor.  
  
- AJAX WCF hizmetlerine erişme.  
  
## <a name="creating-an-ajax-endpoint"></a>Bir AJAX uç noktası oluşturuluyor  
 Bir WCF hizmetinde AJAX desteğini etkinleştirmek için en temel yolu <xref:System.ServiceModel.Activation.WebServiceHostFactory> .svc dosyasında aşağıdaki örnekteki gibi bir hizmet ile ilişkilendirilmiş.  
  
```  
<%ServiceHost   
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CityService"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory  
%>  
```  
  
 Alternatif olarak, bir AJAX uç noktası eklemek için yapılandırmayı kullanabilirsiniz. Kullanım <xref:System.ServiceModel.WebHttpBinding> hizmet uç noktasında ve uç noktasına yapılandırma <xref:System.ServiceModel.Description.WebHttpBehavior> aşağıdaki kod parçacığında gösterildiği gibi.  
  
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
  
 Çalışan bir örnek için bkz. [JSON ve XML ile AJAX hizmeti](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).  
  
## <a name="creating-an-ajax-compatible-service-contract"></a>Bir AJAX uyumlu hizmet sözleşmesi oluşturma  
 Varsayılan olarak, hizmet sözleşmelerini AJAX bir uç nokta dönüş verileri XML biçiminde üzerinden kullanıma. Ayrıca, hizmet işlemleri varsayılan olarak aşağıdaki örnekte gösterildiği gibi işlem adından önce gelen uç nokta adresini içeren URL'leri için HTTP POST istekleri aracılığıyla erişilebilir.  
  
```  
[OperationContract]  
string[] GetCities(string firstLetters);  
```  
  
 Bu işlem, bir HTTP POST kullanılarak erişilebilir `http://serviceaddress/endpointaddress/GetCities` ve bir XML iletisi döndürür.  
  
 Tam Web programlama modeli temel özellikleri özelleştirmek için kullanabilirsiniz. Örneğin, kullanabilirsiniz <xref:System.ServiceModel.Web.WebGetAttribute> veya <xref:System.ServiceModel.Web.WebInvokeAttribute> işlemi yanıt vereceği HTTP fiili denetlemek veya öznitelikleri `UriTemplate` özelliği özel bir URI'leri belirtmek için bu ilgili özniteliklerin. Daha fazla bilgi için [WCF Web HTTP programlama modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md) konu.  
  
 JSON veri biçimi genellikle AJAX hizmetlerinde kullanılır. XML yerine JSON döndüren bir işlem oluşturmak için <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> (veya <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>) özelliğini <xref:System.ServiceModel.Web.WebMessageFormat.Json>. [Tek başına JSON serileştirme](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md) konu, JSON için nasıl yerleşik .NET türleri ve veri anlaşması türleri Haritası gösterir.  
  
 Normalde, yalnızca bir öğesi olan JSON isteklerini ve yanıtlarını oluşur. Önceki `GetCities` işlemi, istek aşağıdaki deyimi benzer.  
  
```  
"na"  
```  
  
 Bu isteğin yanıtını aşağıdaki deyimi benzer.  
  
```  
["Nairobi", "Naples", "Nashville"]  
```  
  
 İşlem ek bir parametre alırsa, tek bir JSON nesnesinde hem parametreler sarmalamak için istek stili alınmalıdır. Aşağıdaki örnekte bu stil JSON iletisi örneğidir.  
  
```json  
{"firstLetters": "na", "maxNumber": 2}  
```  
  
 Şu sözleşme bu iletiyi kabul eder.  
  
```  
[WebInvoke(BodyStyle=WebMessageBodyStyle.WrappedRequest, ResponseFormat=WebMessageFormat.Json)]  
[OperationContract]  
string[] GetCities(string firstLetters, int maxNumber);  
```  
  
## <a name="accessing-ajax-services"></a>AJAX hizmetlerine erişme  
 WCF AJAX uç noktaları her zaman hem JSON hem de XML isteklerini kabul etmek.  
  
 HTTP POST istekleri bir content-type "application/json" JSON olarak kabul edilir ve bu XML (örneğin, "metin/xml") gösteren içerik türü ile XML olarak kabul edilir.  
  
 HTTP GET istekleri URL içinde tüm istek parametrelerini içerir.  
  
 Bu uç nokta için HTTP isteği oluşturmak nasıl karar vermek için kullanıcı en fazla olur. Ayrıca, kullanıcının istek gövdesini form JSON oluşturmak üzerinde tam denetime sahiptir. JavaScript'ten bir isteği oluşturma örneği için bkz: [JSON ve XML ile AJAX hizmeti](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).
