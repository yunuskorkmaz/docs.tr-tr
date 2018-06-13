---
title: System.Web.Routing Integration
ms.date: 03/30/2017
ms.assetid: 31fe2a4f-5c47-4e5d-8ee1-84c524609d41
ms.openlocfilehash: 5bd405d66dcad597bbe6f452703d25372fdb7682
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498029"
---
# <a name="systemwebrouting-integration"></a><span data-ttu-id="fdaab-102">System.Web.Routing Integration</span><span class="sxs-lookup"><span data-stu-id="fdaab-102">System.Web.Routing Integration</span></span>
<span data-ttu-id="fdaab-103">Windows Communication Foundation (WCF) hizmetini Internet Information Service (IIS) barındırdığında sanal dizinde .svc dosyasını yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="fdaab-103">When hosting a Windows Communication Foundation (WCF) service in Internet Information Service (IIS) you place a .svc file in the virtual directory.</span></span> <span data-ttu-id="fdaab-104">Bu .svc dosya hizmeti uygulayan sınıfa yanı sıra kullanmak için hizmet ana bilgisayar üreteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="fdaab-104">This .svc file specifies the service host factory to use as well as the class that implements the service.</span></span> <span data-ttu-id="fdaab-105">İstekleri hizmete yaparken .svc dosyasındaki URI, örneğin belirttiğiniz: http://contoso.com/EmployeeServce.svc.</span><span class="sxs-lookup"><span data-stu-id="fdaab-105">When making requests to the service you specify the .svc file in the URI, for example: http://contoso.com/EmployeeServce.svc.</span></span> <span data-ttu-id="fdaab-106">Bu tür bir URI REST Hizmetleri yazma programcıları için en uygun değil.</span><span class="sxs-lookup"><span data-stu-id="fdaab-106">For programmers writing REST services this type of URI is not optimal.</span></span> <span data-ttu-id="fdaab-107">URI'ler REST Hizmetleri için belirli bir kaynak belirtin ve tüm uzantılar normalde sahip değil.</span><span class="sxs-lookup"><span data-stu-id="fdaab-107">URIs for REST services specify a specific resource and normally do not have any extensions.</span></span> <span data-ttu-id="fdaab-108"><xref:System.Web.Routing> Tümleştirme özelliği için URI uzantısız yanıt bir WCF REST hizmeti barındırma olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="fdaab-108">The <xref:System.Web.Routing> integration feature allows you to host a WCF REST service that responds to URIs without an extension.</span></span> <span data-ttu-id="fdaab-109">Yönlendirme bakın hakkında daha fazla bilgi için [ASP.NET yönlendirme](http://go.microsoft.com/fwlink/?LinkId=184660) ve [AspNetRouteIntegration](../../../../docs/framework/wcf/samples/aspnetrouteintegration.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="fdaab-109">For more information about routing see [ASP.NET Routing](http://go.microsoft.com/fwlink/?LinkId=184660) and the [AspNetRouteIntegration](../../../../docs/framework/wcf/samples/aspnetrouteintegration.md) sample.</span></span>  
  
## <a name="using-systemwebrouting-integration"></a><span data-ttu-id="fdaab-110">System.Web.Routing tümleştirmesini kullanma</span><span class="sxs-lookup"><span data-stu-id="fdaab-110">Using System.Web.Routing Integration</span></span>  
 <span data-ttu-id="fdaab-111">Kullanılacak <xref:System.Web.Routing> tümleştirme özelliği, kullandığınız <xref:System.ServiceModel.Activation.ServiceRoute> bir veya daha fazla yol oluşturmak ve bunlara eklemek için sınıfı <xref:System.Web.Routing.RouteTable> Global.asax dosyasındaki.</span><span class="sxs-lookup"><span data-stu-id="fdaab-111">To use the <xref:System.Web.Routing> integration feature, you use the <xref:System.ServiceModel.Activation.ServiceRoute> class to create one or more routes and add them to the <xref:System.Web.Routing.RouteTable> in a Global.asax file.</span></span> <span data-ttu-id="fdaab-112">Bu yollar hizmet yanıtlaması URI'ler göreli belirtin.</span><span class="sxs-lookup"><span data-stu-id="fdaab-112">These routes specify the relative URIs that the service responds to.</span></span> <span data-ttu-id="fdaab-113">Aşağıdaki örnek bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fdaab-113">The following example shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="fdaab-114">Bu ile başlayan göreli bir URI ile müşteriler için tüm istekleri yönlendirir `Service` hizmet.</span><span class="sxs-lookup"><span data-stu-id="fdaab-114">This routes all requests with a relative URI that begins with Customers to the `Service` service.</span></span>  
  
 <span data-ttu-id="fdaab-115">Web.config dosyanızda eklemelisiniz `System.Web.Routing.UrlRoutingModule` modülünün, `runAllManagedModulesForAllRequests` özniteliğini `true`, ekleyin `UrlRoutingHandler` işleyicisine `<system.webServer>` aşağıdaki örnekte gösterildiği gibi öğesi.</span><span class="sxs-lookup"><span data-stu-id="fdaab-115">In your Web.config file you must add the `System.Web.Routing.UrlRoutingModule` module, set the `runAllManagedModulesForAllRequests` attribute to `true`, and add the `UrlRoutingHandler` handler to the `<system.webServer>` element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="fdaab-116">Bu modül ve yönlendirme için gerekli işleyici yükler.</span><span class="sxs-lookup"><span data-stu-id="fdaab-116">This loads a module and handler required for routing.</span></span> <span data-ttu-id="fdaab-117">Daha fazla bilgi için bkz: [yönlendirme](../../../../docs/framework/wcf/feature-details/routing.md).</span><span class="sxs-lookup"><span data-stu-id="fdaab-117">For more information, see [Routing](../../../../docs/framework/wcf/feature-details/routing.md).</span></span> <span data-ttu-id="fdaab-118">De ayarlamalısınız `aspNetCompatibilityEnabled` özniteliğini `true` içinde `<serviceHostingEnvironment>` aşağıdaki örnekte gösterildiği gibi öğesi.</span><span class="sxs-lookup"><span data-stu-id="fdaab-118">You must also set the `aspNetCompatibilityEnabled` attribute to `true` in the `<serviceHostingEnvironment>` element as shown in the following example.</span></span>  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 <span data-ttu-id="fdaab-119">Aşağıdaki örnekte gösterildiği gibi hizmeti uygulayan sınıf ASP.NET uyumluluk gereksinimlerini etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fdaab-119">The class that implements the service must enable ASP.NET compatibility requirements as shown in the following example.</span></span>  
  
```  
[ServiceContract]  
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]  
    public class Service  
    {  
        // ...  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="fdaab-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fdaab-120">See Also</span></span>  
 [<span data-ttu-id="fdaab-121">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="fdaab-121">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [<span data-ttu-id="fdaab-122">ASP.NET yönlendirme</span><span class="sxs-lookup"><span data-stu-id="fdaab-122">ASP.NET Routing</span></span>](http://go.microsoft.com/fwlink/?LinkId=184660)
