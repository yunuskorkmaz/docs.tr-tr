---
title: System.Web.Routing Tümleştirmesi
ms.date: 03/30/2017
ms.assetid: 31fe2a4f-5c47-4e5d-8ee1-84c524609d41
ms.openlocfilehash: 85137689a31573dc10e8f7384007830ab40d31df
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976032"
---
# <a name="systemwebrouting-integration"></a>System.Web.Routing Tümleştirmesi
Internet Information Service (IIS) içinde bir Windows Communication Foundation (WCF) hizmeti barındırırken, sanal dizinde bir. svc dosyası yerleştirebilirsiniz. Bu. svc dosyası, kullanılacak hizmet ana bilgisayar fabrikasını ve hizmeti uygulayan sınıfını belirtir. Hizmete istek yaparken, URI 'de. svc dosyasını belirtirsiniz, örneğin: `http://contoso.com/EmployeeServce.svc`. REST hizmetlerini yazan programcılar için bu tür bir URI en uygun değildir. REST Hizmetleri için URI 'Ler belirli bir kaynağı belirtir ve normalde hiçbir uzantıya sahip değildir. <xref:System.Web.Routing> tümleştirme özelliği, uzantısı olmayan URI 'lere yanıt veren bir WCF REST hizmetini barındırmanıza olanak tanır. Yönlendirme hakkında daha fazla bilgi için bkz. [ASP.net Routing](https://go.microsoft.com/fwlink/?LinkId=184660).  
  
## <a name="using-systemwebrouting-integration"></a>System. Web. Routing tümleştirmesini kullanma  
 <xref:System.Web.Routing> tümleştirme özelliğini kullanmak için, bir veya daha fazla yol oluşturmak ve bunları bir Global. asax dosyasındaki <xref:System.Web.Routing.RouteTable> eklemek için <xref:System.ServiceModel.Activation.ServiceRoute> sınıfını kullanın. Bu rotalar hizmetin yanıt verdiği göreli URI 'Leri belirtir. Aşağıdaki örnek bunun nasıl yapılacağını göstermektedir.  
  
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
  
 Bu, tüm istekleri müşteriler ile `Service` hizmetine başlayan göreli bir URI ile yönlendirir.  
  
 Web. config dosyanızda `System.Web.Routing.UrlRoutingModule` modülünü eklemeli, `runAllManagedModulesForAllRequests` özniteliğini `true`olarak ayarlamanız ve `UrlRoutingHandler` işleyicisini aşağıdaki örnekte gösterildiği gibi `<system.webServer>` öğesine eklemeniz gerekir.  
  
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
  
 Bu, yönlendirme için gerekli bir modülü ve işleyiciyi yükler. Daha fazla bilgi için bkz. [yönlendirme](../../../../docs/framework/wcf/feature-details/routing.md). Ayrıca, aşağıdaki örnekte gösterildiği gibi, `aspNetCompatibilityEnabled` özniteliğini `<serviceHostingEnvironment>` öğesinde `true` olarak ayarlamanız gerekir.  
  
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

- [WCF Web HTTP Programlama Modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [ASP.NET yönlendirme](https://go.microsoft.com/fwlink/?LinkId=184660)
