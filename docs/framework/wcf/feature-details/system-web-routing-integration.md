---
title: System.Web.Routing Tümleştirmesi
ms.date: 03/30/2017
ms.assetid: 31fe2a4f-5c47-4e5d-8ee1-84c524609d41
ms.openlocfilehash: 059f14c94bb7502a2e4f4616ca2c5e6ac5273afa
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600743"
---
# <a name="systemwebrouting-integration"></a>System.Web.Routing Tümleştirmesi
Internet Information Service (IIS) içinde bir Windows Communication Foundation (WCF) hizmeti barındırırken, sanal dizinde bir. svc dosyası yerleştirebilirsiniz. Bu. svc dosyası, kullanılacak hizmet ana bilgisayar fabrikasını ve hizmeti uygulayan sınıfını belirtir. Hizmete istek yaparken, URI 'de. svc dosyasını belirtirsiniz, örneğin: `http://contoso.com/EmployeeServce.svc` . REST Hizmetleri yazan programcılar için, bu tür bir URI en uygun değildir. REST Hizmetleri için URI 'Ler belirli bir kaynağı belirtir ve normalde hiçbir uzantıya sahip değildir. <xref:System.Web.Routing>Tümleştirme özelliği, uzantısı olmayan URI 'lere yanıt veren bır WCF REST hizmetini barındırmanıza olanak tanır. Yönlendirme hakkında daha fazla bilgi için bkz. [ASP.net Routing](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100)).  
  
## <a name="using-systemwebrouting-integration"></a>System. Web. Routing tümleştirmesini kullanma  
 <xref:System.Web.Routing>Tümleştirme özelliğini kullanmak için <xref:System.ServiceModel.Activation.ServiceRoute> sınıfını kullanarak bir veya daha fazla yol oluşturun ve bunları <xref:System.Web.Routing.RouteTable> Global. asax dosyasına ekleyin. Bu rotalar hizmetin yanıt verdiği göreli URI 'Leri belirtir. Aşağıdaki örnek bunun nasıl yapılacağını göstermektedir.  
  
```aspx-csharp  
<%@ Application Language="C#" %>  
<%@ Import Namespace="System.Web.Routing" %>  
<%@ Import Namespace="System.ServiceModel.Activation" %>  
<%@ Import Namespace="System.ServiceModel.Web " %>  
  
<script RunAt="server">  
    void Application_Start(object sender, EventArgs e)  
    {  
        RegisterRoutes(RouteTable.Routes);  
    }  
  
    private void RegisterRoutes(RouteCollection routes)  
    {  
        routes.Add(new ServiceRoute("Customers", new WebServiceHostFactory(), typeof(Service)));
   }  
</script>  
```  
  
 Bu, tüm istekleri müşterilerle çalışmaya başlayan göreli bir URI ile yönlendirir `Service` .  
  
 Web. config dosyanızda `System.Web.Routing.UrlRoutingModule` modülünü eklemeniz, `runAllManagedModulesForAllRequests` özniteliğini olarak ayarlamanız `true` ve `UrlRoutingHandler` `<system.webServer>` Aşağıdaki örnekte gösterildiği gibi işleyiciyi öğesine eklemeniz gerekir.  
  
```xml  
<system.webServer>  
      <modules runAllManagedModulesForAllRequests="true">  
        <add name="UrlRoutingModule" type="System.Web.Routing.UrlRoutingModule, System.Web, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" />  
      </modules>  
      <handlers>  
        <add name="UrlRoutingHandler" preCondition="integratedMode" verb="*" path="UrlRouting.axd"/>  
      </handlers>  
    </system.webServer>  
```  
  
 Bu, yönlendirme için gerekli bir modülü ve işleyiciyi yükler. Daha fazla bilgi için bkz. [yönlendirme](routing.md). Ayrıca, `aspNetCompatibilityEnabled` `true` `<serviceHostingEnvironment>` Aşağıdaki örnekte gösterildiği gibi öğesini öğesi içinde olarak ayarlamanız gerekir.  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 Hizmeti uygulayan sınıfın aşağıdaki örnekte gösterildiği gibi ASP.NET uyumluluk gereksinimlerini etkinleştirmesi gerekir.  
  
```csharp
[ServiceContract]  
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]  
    public class Service  
    {  
        // ...  
    }  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Web HTTP Programlama Modeli](wcf-web-http-programming-model.md)
- [ASP.NET yönlendirme](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100))
