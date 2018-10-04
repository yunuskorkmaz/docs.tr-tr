---
title: System.Web.Routing Integration
ms.date: 03/30/2017
ms.assetid: 31fe2a4f-5c47-4e5d-8ee1-84c524609d41
ms.openlocfilehash: 2df1ff8230cd79f61fdee971d783544054bd8196
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48782109"
---
# <a name="systemwebrouting-integration"></a>System.Web.Routing Integration
Bir Windows Communication Foundation (WCF) hizmeti Internet Information Service (IIS) yeniden barındırdığında sanal dizinde .svc dosya yerleştirin. Bu .svc dosya yanı sıra hizmeti uygulayan sınıf kullanmak için hizmet ana bilgisayar üreteci belirtir. Hizmetine istek yaparken .svc dosya URI'de, örneğin belirttiğiniz: http://contoso.com/EmployeeServce.svc. Bu tür bir URI REST Hizmetleri yazma programcıları için en uygun değil. REST Hizmetleri için bir URI'leri, belirli bir kaynak belirtin ve normalde herhangi bir uzantısı yok. <xref:System.Web.Routing> Tümleştirme özelliği için bir URI'leri uzantısız yanıt veren bir WCF REST hizmeti barındırmanıza olanak sağlar. Yönlendirme bakın hakkında daha fazla bilgi için [ASP.NET yönlendirme](https://go.microsoft.com/fwlink/?LinkId=184660).  
  
## <a name="using-systemwebrouting-integration"></a>System.Web.Routing tümleştirmesi  
 Kullanılacak <xref:System.Web.Routing> tümleştirme özelliği, kullandığınız <xref:System.ServiceModel.Activation.ServiceRoute> sınıfı bir veya daha fazla rotalar oluşturun ve bunları Ekle <xref:System.Web.Routing.RouteTable> Global.asax dosyasındaki. Bu yolları göreli hizmet yanıt veren bir URI'leri belirtin. Aşağıdaki örnek bunun nasıl yapılacağı gösterilmektedir.  
  
```  
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
  
 Bu, tüm istekleri ile başlayan göreli bir URI ile müşterilere yönlendirir `Service` hizmeti.  
  
 Web.config dosyanızda eklemelisiniz `System.Web.Routing.UrlRoutingModule` modülünün, `runAllManagedModulesForAllRequests` özniteliğini `true`ve ekleme `UrlRoutingHandler` işleyicisine `<system.webServer>` aşağıdaki örnekte gösterildiği gibi bir öğe.  
  
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
  
 Bu, modülü ve yönlendirme için gerekli işleyici yükler. Daha fazla bilgi için [yönlendirme](../../../../docs/framework/wcf/feature-details/routing.md). Ayrıca ayarlamanız gerekir `aspNetCompatibilityEnabled` özniteliğini `true` içinde `<serviceHostingEnvironment>` aşağıdaki örnekte gösterildiği gibi bir öğe.  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 Aşağıdaki örnekte gösterildiği gibi hizmeti uygulayan sınıf ASP.NET uyumluluk gereksinimlerini etkinleştirmeniz gerekir.  
  
```  
[ServiceContract]  
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]  
    public class Service  
    {  
        // ...  
    }  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Web HTTP Programlama Modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [ASP.NET yönlendirme](https://go.microsoft.com/fwlink/?LinkId=184660)
