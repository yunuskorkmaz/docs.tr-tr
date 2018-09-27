---
title: System.Web.Routing Integration
ms.date: 03/30/2017
ms.assetid: 31fe2a4f-5c47-4e5d-8ee1-84c524609d41
ms.openlocfilehash: 2df1ff8230cd79f61fdee971d783544054bd8196
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47232352"
---
# <a name="systemwebrouting-integration"></a><span data-ttu-id="1bf78-102">System.Web.Routing Integration</span><span class="sxs-lookup"><span data-stu-id="1bf78-102">System.Web.Routing Integration</span></span>
<span data-ttu-id="1bf78-103">Bir Windows Communication Foundation (WCF) hizmeti Internet Information Service (IIS) yeniden barındırdığında sanal dizinde .svc dosya yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="1bf78-103">When hosting a Windows Communication Foundation (WCF) service in Internet Information Service (IIS) you place a .svc file in the virtual directory.</span></span> <span data-ttu-id="1bf78-104">Bu .svc dosya yanı sıra hizmeti uygulayan sınıf kullanmak için hizmet ana bilgisayar üreteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="1bf78-104">This .svc file specifies the service host factory to use as well as the class that implements the service.</span></span> <span data-ttu-id="1bf78-105">Hizmetine istek yaparken .svc dosya URI'de, örneğin belirttiğiniz: http://contoso.com/EmployeeServce.svc.</span><span class="sxs-lookup"><span data-stu-id="1bf78-105">When making requests to the service you specify the .svc file in the URI, for example: http://contoso.com/EmployeeServce.svc.</span></span> <span data-ttu-id="1bf78-106">Bu tür bir URI REST Hizmetleri yazma programcıları için en uygun değil.</span><span class="sxs-lookup"><span data-stu-id="1bf78-106">For programmers writing REST services this type of URI is not optimal.</span></span> <span data-ttu-id="1bf78-107">REST Hizmetleri için bir URI'leri, belirli bir kaynak belirtin ve normalde herhangi bir uzantısı yok.</span><span class="sxs-lookup"><span data-stu-id="1bf78-107">URIs for REST services specify a specific resource and normally do not have any extensions.</span></span> <span data-ttu-id="1bf78-108"><xref:System.Web.Routing> Tümleştirme özelliği için bir URI'leri uzantısız yanıt veren bir WCF REST hizmeti barındırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="1bf78-108">The <xref:System.Web.Routing> integration feature allows you to host a WCF REST service that responds to URIs without an extension.</span></span> <span data-ttu-id="1bf78-109">Yönlendirme bakın hakkında daha fazla bilgi için [ASP.NET yönlendirme](https://go.microsoft.com/fwlink/?LinkId=184660).</span><span class="sxs-lookup"><span data-stu-id="1bf78-109">For more information about routing see [ASP.NET Routing](https://go.microsoft.com/fwlink/?LinkId=184660).</span></span>  
  
## <a name="using-systemwebrouting-integration"></a><span data-ttu-id="1bf78-110">System.Web.Routing tümleştirmesi</span><span class="sxs-lookup"><span data-stu-id="1bf78-110">Using System.Web.Routing Integration</span></span>  
 <span data-ttu-id="1bf78-111">Kullanılacak <xref:System.Web.Routing> tümleştirme özelliği, kullandığınız <xref:System.ServiceModel.Activation.ServiceRoute> sınıfı bir veya daha fazla rotalar oluşturun ve bunları Ekle <xref:System.Web.Routing.RouteTable> Global.asax dosyasındaki.</span><span class="sxs-lookup"><span data-stu-id="1bf78-111">To use the <xref:System.Web.Routing> integration feature, you use the <xref:System.ServiceModel.Activation.ServiceRoute> class to create one or more routes and add them to the <xref:System.Web.Routing.RouteTable> in a Global.asax file.</span></span> <span data-ttu-id="1bf78-112">Bu yolları göreli hizmet yanıt veren bir URI'leri belirtin.</span><span class="sxs-lookup"><span data-stu-id="1bf78-112">These routes specify the relative URIs that the service responds to.</span></span> <span data-ttu-id="1bf78-113">Aşağıdaki örnek bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1bf78-113">The following example shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="1bf78-114">Bu, tüm istekleri ile başlayan göreli bir URI ile müşterilere yönlendirir `Service` hizmeti.</span><span class="sxs-lookup"><span data-stu-id="1bf78-114">This routes all requests with a relative URI that begins with Customers to the `Service` service.</span></span>  
  
 <span data-ttu-id="1bf78-115">Web.config dosyanızda eklemelisiniz `System.Web.Routing.UrlRoutingModule` modülünün, `runAllManagedModulesForAllRequests` özniteliğini `true`ve ekleme `UrlRoutingHandler` işleyicisine `<system.webServer>` aşağıdaki örnekte gösterildiği gibi bir öğe.</span><span class="sxs-lookup"><span data-stu-id="1bf78-115">In your Web.config file you must add the `System.Web.Routing.UrlRoutingModule` module, set the `runAllManagedModulesForAllRequests` attribute to `true`, and add the `UrlRoutingHandler` handler to the `<system.webServer>` element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="1bf78-116">Bu, modülü ve yönlendirme için gerekli işleyici yükler.</span><span class="sxs-lookup"><span data-stu-id="1bf78-116">This loads a module and handler required for routing.</span></span> <span data-ttu-id="1bf78-117">Daha fazla bilgi için [yönlendirme](../../../../docs/framework/wcf/feature-details/routing.md).</span><span class="sxs-lookup"><span data-stu-id="1bf78-117">For more information, see [Routing](../../../../docs/framework/wcf/feature-details/routing.md).</span></span> <span data-ttu-id="1bf78-118">Ayrıca ayarlamanız gerekir `aspNetCompatibilityEnabled` özniteliğini `true` içinde `<serviceHostingEnvironment>` aşağıdaki örnekte gösterildiği gibi bir öğe.</span><span class="sxs-lookup"><span data-stu-id="1bf78-118">You must also set the `aspNetCompatibilityEnabled` attribute to `true` in the `<serviceHostingEnvironment>` element as shown in the following example.</span></span>  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 <span data-ttu-id="1bf78-119">Aşağıdaki örnekte gösterildiği gibi hizmeti uygulayan sınıf ASP.NET uyumluluk gereksinimlerini etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1bf78-119">The class that implements the service must enable ASP.NET compatibility requirements as shown in the following example.</span></span>  
  
```  
[ServiceContract]  
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]  
    public class Service  
    {  
        // ...  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="1bf78-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1bf78-120">See Also</span></span>  
 [<span data-ttu-id="1bf78-121">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="1bf78-121">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [<span data-ttu-id="1bf78-122">ASP.NET yönlendirme</span><span class="sxs-lookup"><span data-stu-id="1bf78-122">ASP.NET Routing</span></span>](https://go.microsoft.com/fwlink/?LinkId=184660)
