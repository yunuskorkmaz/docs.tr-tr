---
title: System.Web.Routing Tümleştirmesi
ms.date: 03/30/2017
ms.assetid: 31fe2a4f-5c47-4e5d-8ee1-84c524609d41
ms.openlocfilehash: fdc355d4560294a16f3e9c488fdaf142d2982c0d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745332"
---
# <a name="systemwebrouting-integration"></a><span data-ttu-id="885fc-102">System.Web.Routing Tümleştirmesi</span><span class="sxs-lookup"><span data-stu-id="885fc-102">System.Web.Routing Integration</span></span>
<span data-ttu-id="885fc-103">Internet Information Service (IIS) içinde bir Windows Communication Foundation (WCF) hizmeti barındırırken, sanal dizinde bir. svc dosyası yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="885fc-103">When hosting a Windows Communication Foundation (WCF) service in Internet Information Service (IIS) you place a .svc file in the virtual directory.</span></span> <span data-ttu-id="885fc-104">Bu. svc dosyası, kullanılacak hizmet ana bilgisayar fabrikasını ve hizmeti uygulayan sınıfını belirtir.</span><span class="sxs-lookup"><span data-stu-id="885fc-104">This .svc file specifies the service host factory to use as well as the class that implements the service.</span></span> <span data-ttu-id="885fc-105">Hizmete istek yaparken, URI 'de. svc dosyasını belirtirsiniz, örneğin: `http://contoso.com/EmployeeServce.svc`.</span><span class="sxs-lookup"><span data-stu-id="885fc-105">When making requests to the service you specify the .svc file in the URI, for example: `http://contoso.com/EmployeeServce.svc`.</span></span> <span data-ttu-id="885fc-106">REST Hizmetleri yazan programcılar için, bu tür bir URI en uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="885fc-106">For programmers writing REST services, this type of URI is not optimal.</span></span> <span data-ttu-id="885fc-107">REST Hizmetleri için URI 'Ler belirli bir kaynağı belirtir ve normalde hiçbir uzantıya sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="885fc-107">URIs for REST services specify a specific resource and normally do not have any extensions.</span></span> <span data-ttu-id="885fc-108"><xref:System.Web.Routing> tümleştirme özelliği, uzantısı olmayan URI 'lere yanıt veren bir WCF REST hizmetini barındırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="885fc-108">The <xref:System.Web.Routing> integration feature allows you to host a WCF REST service that responds to URIs without an extension.</span></span> <span data-ttu-id="885fc-109">Yönlendirme hakkında daha fazla bilgi için bkz. [ASP.net Routing](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="885fc-109">For more information about routing see [ASP.NET Routing](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100)).</span></span>  
  
## <a name="using-systemwebrouting-integration"></a><span data-ttu-id="885fc-110">System. Web. Routing tümleştirmesini kullanma</span><span class="sxs-lookup"><span data-stu-id="885fc-110">Using System.Web.Routing Integration</span></span>  
 <span data-ttu-id="885fc-111"><xref:System.Web.Routing> tümleştirme özelliğini kullanmak için, bir veya daha fazla yol oluşturmak ve bunları bir Global. asax dosyasındaki <xref:System.Web.Routing.RouteTable> eklemek için <xref:System.ServiceModel.Activation.ServiceRoute> sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="885fc-111">To use the <xref:System.Web.Routing> integration feature, you use the <xref:System.ServiceModel.Activation.ServiceRoute> class to create one or more routes and add them to the <xref:System.Web.Routing.RouteTable> in a Global.asax file.</span></span> <span data-ttu-id="885fc-112">Bu rotalar hizmetin yanıt verdiği göreli URI 'Leri belirtir.</span><span class="sxs-lookup"><span data-stu-id="885fc-112">These routes specify the relative URIs that the service responds to.</span></span> <span data-ttu-id="885fc-113">Aşağıdaki örnek bunun nasıl yapılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="885fc-113">The following example shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="885fc-114">Bu, tüm istekleri müşteriler ile `Service` hizmetine başlayan göreli bir URI ile yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="885fc-114">This routes all requests with a relative URI that begins with Customers to the `Service` service.</span></span>  
  
 <span data-ttu-id="885fc-115">Web. config dosyanızda `System.Web.Routing.UrlRoutingModule` modülünü eklemeli, `runAllManagedModulesForAllRequests` özniteliğini `true`olarak ayarlamanız ve `UrlRoutingHandler` işleyicisini aşağıdaki örnekte gösterildiği gibi `<system.webServer>` öğesine eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="885fc-115">In your Web.config file you must add the `System.Web.Routing.UrlRoutingModule` module, set the `runAllManagedModulesForAllRequests` attribute to `true`, and add the `UrlRoutingHandler` handler to the `<system.webServer>` element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="885fc-116">Bu, yönlendirme için gerekli bir modülü ve işleyiciyi yükler.</span><span class="sxs-lookup"><span data-stu-id="885fc-116">This loads a module and handler required for routing.</span></span> <span data-ttu-id="885fc-117">Daha fazla bilgi için bkz. [yönlendirme](../../../../docs/framework/wcf/feature-details/routing.md).</span><span class="sxs-lookup"><span data-stu-id="885fc-117">For more information, see [Routing](../../../../docs/framework/wcf/feature-details/routing.md).</span></span> <span data-ttu-id="885fc-118">Ayrıca, aşağıdaki örnekte gösterildiği gibi, `aspNetCompatibilityEnabled` özniteliğini `<serviceHostingEnvironment>` öğesinde `true` olarak ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="885fc-118">You must also set the `aspNetCompatibilityEnabled` attribute to `true` in the `<serviceHostingEnvironment>` element as shown in the following example.</span></span>  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 <span data-ttu-id="885fc-119">Hizmeti uygulayan sınıfın aşağıdaki örnekte gösterildiği gibi ASP.NET uyumluluk gereksinimlerini etkinleştirmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="885fc-119">The class that implements the service must enable ASP.NET compatibility requirements as shown in the following example.</span></span>  
  
```csharp 
[ServiceContract]  
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]  
    public class Service  
    {  
        // ...  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="885fc-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="885fc-120">See also</span></span>

- [<span data-ttu-id="885fc-121">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="885fc-121">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- <span data-ttu-id="885fc-122">[ASP.NET yönlendirme](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="885fc-122">[ASP.NET Routing](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100))</span></span>
