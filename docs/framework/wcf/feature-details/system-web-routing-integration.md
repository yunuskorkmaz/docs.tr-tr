---
title: System.Web.Routing Tümleştirmesi
ms.date: 03/30/2017
ms.assetid: 31fe2a4f-5c47-4e5d-8ee1-84c524609d41
ms.openlocfilehash: a80b5c3b336b4fd18b347a25ceaf509baf6461b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184390"
---
# <a name="systemwebrouting-integration"></a>System.Web.Routing Tümleştirmesi
Internet Information Service 'te (IIS) bir Windows Communication Foundation (WCF) hizmeti barındırırken sanal dizine bir .svc dosyası yersiniz. Bu .svc dosyası, hizmeti uygulayan sınıfın yanı sıra kullanılacak servis ana bilgisayar fabrikasını da belirtir. Hizmete istekte bulunduktan sonra URI'deki .svc dosyasını belirtin, örneğin: `http://contoso.com/EmployeeServce.svc`. REST hizmetleri yazan programcılar için, bu tür URI en uygun değildir. REST hizmetleri için URI'ler belirli bir kaynak belirtir ve normalde herhangi bir uzantısı yoktur. Tümleştirme özelliği, <xref:System.Web.Routing> uri'lere uzantısı zolmadan yanıt veren bir WCF REST hizmeti barındırmanızı sağlar. Yönlendirme hakkında daha fazla bilgi için ASP.NET [Yönlendirme'ye](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100))bakın.  
  
## <a name="using-systemwebrouting-integration"></a>System.Web.Routing Entegrasyonunu Kullanma  
 Tümleştirme <xref:System.Web.Routing> özelliğini kullanmak için <xref:System.ServiceModel.Activation.ServiceRoute> sınıfı bir veya daha fazla yol <xref:System.Web.Routing.RouteTable> oluşturmak ve bunları global.asax dosyasına eklemek için kullanırsınız. Bu rotalar, hizmetin yanıt verdiği göreli ÜR'leri belirtir. Aşağıdaki örnekte, bunun nasıl yapılacağını gösterilmektedir.  
  
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
  
 Bu, müşterilerle başlayan göreceli bir URI `Service` ile tüm istekleri hizmete yönlendirir.  
  
 `System.Web.Routing.UrlRoutingModule` Web.config dosyanızda modülü eklemeniz, özniteliği `runAllManagedModulesForAllRequests` `true`ayarlamanız ve `UrlRoutingHandler` işleyiciyi `<system.webServer>` aşağıdaki örnekte gösterildiği gibi öğeye eklemeniz gerekir.  
  
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
  
 Bu, yönlendirme için gerekli bir modül ve işleyici yükler. Daha fazla bilgi için [Yönlendirme'ye](../../../../docs/framework/wcf/feature-details/routing.md)bakın. Ayrıca, aşağıdaki `aspNetCompatibilityEnabled` `true` örnekte gösterildiği `<serviceHostingEnvironment>` gibi öğedeki özniteliği de ayarlamanız gerekir.  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 Hizmeti uygulayan sınıf, aşağıdaki örnekte gösterildiği gibi ASP.NET uyumluluk gereksinimlerini etkinleştirmelidir.  
  
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
- [ASP.NET Yönlendirme](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100))
