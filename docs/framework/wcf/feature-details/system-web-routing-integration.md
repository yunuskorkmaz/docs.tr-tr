---
title: System.Web.Routing Integration
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31fe2a4f-5c47-4e5d-8ee1-84c524609d41
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8f74a0f9d7a39d7d5ccb97d7f4ef022b32bbf4fc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="systemwebrouting-integration"></a>System.Web.Routing Integration
Barındırdığında bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmeti Internet Information Service (IIS) sanal dizinde .svc dosya yerleştirin. Bu .svc dosya hizmeti uygulayan sınıfa yanı sıra kullanmak için hizmet ana bilgisayar üreteci belirtir. İstekleri hizmete yaparken .svc dosyasındaki URI, örneğin belirttiğiniz: http://contoso.com/EmployeeServce.svc. Bu tür bir URI REST Hizmetleri yazma programcıları için en uygun değil. URI'ler REST Hizmetleri için belirli bir kaynak belirtin ve tüm uzantılar normalde sahip değil. <xref:System.Web.Routing> Tümleştirme özelliği barındırmanıza olanak sağlayan bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uzantısız URI'ler için yanıt REST hizmeti. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]yönlendirme Bkz: [ASP.NET yönlendirme](http://go.microsoft.com/fwlink/?LinkId=184660) ve [AspNetRouteIntegration](../../../../docs/framework/wcf/samples/aspnetrouteintegration.md) örnek.  
  
## <a name="using-systemwebrouting-integration"></a>System.Web.Routing tümleştirmesini kullanma  
 Kullanılacak <xref:System.Web.Routing> tümleştirme özelliği, kullandığınız <xref:System.ServiceModel.Activation.ServiceRoute> bir veya daha fazla yol oluşturmak ve bunlara eklemek için sınıfı <xref:System.Web.Routing.RouteTable> Global.asax dosyasındaki. Bu yollar hizmet yanıtlaması URI'ler göreli belirtin. Aşağıdaki örnek bunun nasıl yapılacağı gösterilmektedir.  
  
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
  
 Bu ile başlayan göreli bir URI ile müşteriler için tüm istekleri yönlendirir `Service` hizmet.  
  
 Web.config dosyanızda eklemelisiniz `System.Web.Routing.UrlRoutingModule` modülünün, `runAllManagedModulesForAllRequests` özniteliğini `true`, ekleyin `UrlRoutingHandler` işleyicisine `<system.webServer>` aşağıdaki örnekte gösterildiği gibi öğesi.  
  
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
  
 Bu modül ve yönlendirme için gerekli işleyici yükler. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Yönlendirme](../../../../docs/framework/wcf/feature-details/routing.md). De ayarlamalısınız `aspNetCompatibilityEnabled` özniteliğini `true` içinde `<serviceHostingEnvironment>` aşağıdaki örnekte gösterildiği gibi öğesi.  
  
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
 [ASP.NET yönlendirme](http://go.microsoft.com/fwlink/?LinkId=184660)
