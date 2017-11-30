---
title: "ASP.NET Olmadan WCF AJAX Hizmetleri Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba4a7d1b-e277-4978-9f62-37684e6dc934
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 70926e1deb9b4911a7d89d49280b9a0e6068cc42
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="creating-wcf-ajax-services-without-aspnet"></a>ASP.NET Olmadan WCF AJAX Hizmetleri Oluşturma
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]AJAX Hizmetleri, ASP.NET AJAX gerek kalmadan tüm JavaScript etkin Web sayfasından erişilebilir. Bu konuda gibi oluşturmayı açıklar bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet.  
  
 Kullanma yönergeleri için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET AJAX ile bkz [ASP.NET AJAX için WCF hizmetleri oluşturma](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md).  
  
 Bir oluşturma üç bölümden oluşur bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] AJAX hizmeti:  
  
-   AJAX uç noktası oluşturma, tarayıcıdan erişilebilir.  
  
-   Bir AJAX uyumlu hizmet sözleşmesi oluşturma.  
  
-   WCF AJAX Hizmetleri erişme.  
  
## <a name="creating-an-ajax-endpoint"></a>AJAX uç noktası oluşturma  
 AJAX desteğini etkinleştirmek için en temel yolu bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmetidir kullanmak için <xref:System.ServiceModel.Activation.WebServiceHostFactory> aşağıdaki örnekteki gibi hizmeti ile ilişkilendirilen .svc dosyasındaki.  
  
```  
<%ServiceHost   
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CityService"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory  
%>  
```  
  
 Alternatif olarak, bir AJAX uç noktası eklemek için yapılandırma kullanabilirsiniz. Kullanım <xref:System.ServiceModel.WebHttpBinding> hizmet uç noktası üzerinde ve bu bitiş noktası ile yapılandırma <xref:System.ServiceModel.Description.WebHttpBehavior> aşağıdaki kod parçacığında gösterildiği gibi.  
  
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
  
 Çalışan bir örnek için bkz: [JSON ve XML ile AJAX hizmeti](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).  
  
## <a name="creating-an-ajax-compatible-service-contract"></a>Bir AJAX uyumlu hizmet sözleşmesi oluşturma  
 Varsayılan olarak, hizmet sözleşmelerini AJAX bir uç nokta dönüş verileri XML biçiminde üzerinden açık. Ayrıca, varsayılan olarak hizmet işlemleri aşağıdaki örnekte gösterildiği gibi işlem adından uç noktası adresi dahil URL'ler için HTTP POST istekleri üzerinden erişilebilir.  
  
```  
[OperationContract]  
string[] GetCities(string firstLetters);  
```  
  
 Bu işlem bir HTTP POST kullanılarak erişilebilir olduğundan `http://serviceaddress/endpointaddress/GetCities` ve bir XML iletisi döndürür.  
  
 Bu temel özelliklerini özelleştirmek için tam Web programlama modelini kullanabilirsiniz. Örneğin, kullanabileceğiniz <xref:System.ServiceModel.Web.WebGetAttribute> veya <xref:System.ServiceModel.Web.WebInvokeAttribute> işlemi yanıt vereceği HTTP fiili denetlemek veya kullanmak için öznitelikler `UriTemplate` özel URI'ler belirtmek için bu ilgili öznitelikler özelliği. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][WCF Web HTTP programlama modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md) konu.  
  
 JSON veri biçimi genellikle AJAX Hizmetleri kullanılır. XML yerine JSON döndüren bir işlemi oluşturmak için <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> (veya <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>) özelliğine <xref:System.ServiceModel.Web.WebMessageFormat.Json>. [Tek başına JSON serileştirmesi](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md) konu, JSON olarak nasıl yerleşik .NET türleri ve verileri sözleşme türleri Haritası gösterir.  
  
 Normalde, JSON isteklerinin ve yanıtlarının yalnızca bir öğe oluşur. Önceki `GetCities` işlemi, isteği şu deyimi benzer.  
  
```  
"na"  
```  
  
 Bu istek için yanıt aşağıdaki ifadeyi benzer.  
  
```  
["Nairobi", "Naples", "Nashville"]  
```  
  
 İşlemi fazladan bir parametre alırsa, isteği stili parametrelerinin her ikisini de tek bir JSON nesnesinde sarmalamak için alınmalıdır. Aşağıdaki örnekte bu stil JSON iletisi örneğidir.  
  
```json  
{"firstLetters": "na", "maxNumber": 2}  
```  
  
 Aşağıdaki sözleşme bu iletiyi kabul eder.  
  
```  
[WebInvoke(BodyStyle=WebMessageBodyStyle.WrappedRequest, ResponseFormat=WebMessageFormat.Json)]  
[OperationContract]  
string[] GetCities(string firstLetters, int maxNumber);  
```  
  
## <a name="accessing-ajax-services"></a>AJAX hizmetlere erişme  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]AJAX uç noktaları her zaman JSON ve XML isteklerini kabul edin.  
  
 HTTP POST istekleri bir içerik türü "application/json" JSON olarak kabul edilir ve XML (örneğin, "text/xml") gösteren içerik türü olan XML olarak kabul edilir.  
  
 HTTP GET istekleri URL'de bulunan tüm istek parametrelerini içerir.  
  
 Bu uç noktanın HTTP isteği oluşturmak nasıl karar vermek için kullanıcı kadar olur. Ayrıca, kullanıcının istek gövdesini form JSON oluşturma üzerinde tam denetime sahiptir. Bir istek JavaScript'ten oluşturma örneği için bkz: [JSON ve XML ile AJAX hizmeti](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).
