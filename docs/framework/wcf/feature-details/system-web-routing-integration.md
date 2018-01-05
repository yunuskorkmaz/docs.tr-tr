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
# <a name="systemwebrouting-integration"></a><span data-ttu-id="dd383-102">System.Web.Routing Integration</span><span class="sxs-lookup"><span data-stu-id="dd383-102">System.Web.Routing Integration</span></span>
<span data-ttu-id="dd383-103">Barındırdığında bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmeti Internet Information Service (IIS) sanal dizinde .svc dosya yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="dd383-103">When hosting a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service in Internet Information Service (IIS) you place a .svc file in the virtual directory.</span></span> <span data-ttu-id="dd383-104">Bu .svc dosya hizmeti uygulayan sınıfa yanı sıra kullanmak için hizmet ana bilgisayar üreteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="dd383-104">This .svc file specifies the service host factory to use as well as the class that implements the service.</span></span> <span data-ttu-id="dd383-105">İstekleri hizmete yaparken .svc dosyasındaki URI, örneğin belirttiğiniz: http://contoso.com/EmployeeServce.svc.</span><span class="sxs-lookup"><span data-stu-id="dd383-105">When making requests to the service you specify the .svc file in the URI, for example: http://contoso.com/EmployeeServce.svc.</span></span> <span data-ttu-id="dd383-106">Bu tür bir URI REST Hizmetleri yazma programcıları için en uygun değil.</span><span class="sxs-lookup"><span data-stu-id="dd383-106">For programmers writing REST services this type of URI is not optimal.</span></span> <span data-ttu-id="dd383-107">URI'ler REST Hizmetleri için belirli bir kaynak belirtin ve tüm uzantılar normalde sahip değil.</span><span class="sxs-lookup"><span data-stu-id="dd383-107">URIs for REST services specify a specific resource and normally do not have any extensions.</span></span> <span data-ttu-id="dd383-108"><xref:System.Web.Routing> Tümleştirme özelliği barındırmanıza olanak sağlayan bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uzantısız URI'ler için yanıt REST hizmeti.</span><span class="sxs-lookup"><span data-stu-id="dd383-108">The <xref:System.Web.Routing> integration feature allows you to host a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] REST service that responds to URIs without an extension.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="dd383-109">yönlendirme Bkz: [ASP.NET yönlendirme](http://go.microsoft.com/fwlink/?LinkId=184660) ve [AspNetRouteIntegration](../../../../docs/framework/wcf/samples/aspnetrouteintegration.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="dd383-109"> routing see [ASP.NET Routing](http://go.microsoft.com/fwlink/?LinkId=184660) and the [AspNetRouteIntegration](../../../../docs/framework/wcf/samples/aspnetrouteintegration.md) sample.</span></span>  
  
## <a name="using-systemwebrouting-integration"></a><span data-ttu-id="dd383-110">System.Web.Routing tümleştirmesini kullanma</span><span class="sxs-lookup"><span data-stu-id="dd383-110">Using System.Web.Routing Integration</span></span>  
 <span data-ttu-id="dd383-111">Kullanılacak <xref:System.Web.Routing> tümleştirme özelliği, kullandığınız <xref:System.ServiceModel.Activation.ServiceRoute> bir veya daha fazla yol oluşturmak ve bunlara eklemek için sınıfı <xref:System.Web.Routing.RouteTable> Global.asax dosyasındaki.</span><span class="sxs-lookup"><span data-stu-id="dd383-111">To use the <xref:System.Web.Routing> integration feature, you use the <xref:System.ServiceModel.Activation.ServiceRoute> class to create one or more routes and add them to the <xref:System.Web.Routing.RouteTable> in a Global.asax file.</span></span> <span data-ttu-id="dd383-112">Bu yollar hizmet yanıtlaması URI'ler göreli belirtin.</span><span class="sxs-lookup"><span data-stu-id="dd383-112">These routes specify the relative URIs that the service responds to.</span></span> <span data-ttu-id="dd383-113">Aşağıdaki örnek bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="dd383-113">The following example shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="dd383-114">Bu ile başlayan göreli bir URI ile müşteriler için tüm istekleri yönlendirir `Service` hizmet.</span><span class="sxs-lookup"><span data-stu-id="dd383-114">This routes all requests with a relative URI that begins with Customers to the `Service` service.</span></span>  
  
 <span data-ttu-id="dd383-115">Web.config dosyanızda eklemelisiniz `System.Web.Routing.UrlRoutingModule` modülünün, `runAllManagedModulesForAllRequests` özniteliğini `true`, ekleyin `UrlRoutingHandler` işleyicisine `<system.webServer>` aşağıdaki örnekte gösterildiği gibi öğesi.</span><span class="sxs-lookup"><span data-stu-id="dd383-115">In your Web.config file you must add the `System.Web.Routing.UrlRoutingModule` module, set the `runAllManagedModulesForAllRequests` attribute to `true`, and add the `UrlRoutingHandler` handler to the `<system.webServer>` element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="dd383-116">Bu modül ve yönlendirme için gerekli işleyici yükler.</span><span class="sxs-lookup"><span data-stu-id="dd383-116">This loads a module and handler required for routing.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="dd383-117">[Yönlendirme](../../../../docs/framework/wcf/feature-details/routing.md).</span><span class="sxs-lookup"><span data-stu-id="dd383-117"> [Routing](../../../../docs/framework/wcf/feature-details/routing.md).</span></span> <span data-ttu-id="dd383-118">De ayarlamalısınız `aspNetCompatibilityEnabled` özniteliğini `true` içinde `<serviceHostingEnvironment>` aşağıdaki örnekte gösterildiği gibi öğesi.</span><span class="sxs-lookup"><span data-stu-id="dd383-118">You must also set the `aspNetCompatibilityEnabled` attribute to `true` in the `<serviceHostingEnvironment>` element as shown in the following example.</span></span>  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 <span data-ttu-id="dd383-119">Aşağıdaki örnekte gösterildiği gibi hizmeti uygulayan sınıf ASP.NET uyumluluk gereksinimlerini etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="dd383-119">The class that implements the service must enable ASP.NET compatibility requirements as shown in the following example.</span></span>  
  
```  
[ServiceContract]  
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]  
    public class Service  
    {  
        // ...  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="dd383-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dd383-120">See Also</span></span>  
 [<span data-ttu-id="dd383-121">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="dd383-121">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [<span data-ttu-id="dd383-122">ASP.NET yönlendirme</span><span class="sxs-lookup"><span data-stu-id="dd383-122">ASP.NET Routing</span></span>](http://go.microsoft.com/fwlink/?LinkId=184660)
