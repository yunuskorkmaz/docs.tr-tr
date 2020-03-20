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
# <a name="systemwebrouting-integration"></a><span data-ttu-id="7a6b7-102">System.Web.Routing Tümleştirmesi</span><span class="sxs-lookup"><span data-stu-id="7a6b7-102">System.Web.Routing Integration</span></span>
<span data-ttu-id="7a6b7-103">Internet Information Service 'te (IIS) bir Windows Communication Foundation (WCF) hizmeti barındırırken sanal dizine bir .svc dosyası yersiniz.</span><span class="sxs-lookup"><span data-stu-id="7a6b7-103">When hosting a Windows Communication Foundation (WCF) service in Internet Information Service (IIS) you place a .svc file in the virtual directory.</span></span> <span data-ttu-id="7a6b7-104">Bu .svc dosyası, hizmeti uygulayan sınıfın yanı sıra kullanılacak servis ana bilgisayar fabrikasını da belirtir.</span><span class="sxs-lookup"><span data-stu-id="7a6b7-104">This .svc file specifies the service host factory to use as well as the class that implements the service.</span></span> <span data-ttu-id="7a6b7-105">Hizmete istekte bulunduktan sonra URI'deki .svc dosyasını belirtin, örneğin: `http://contoso.com/EmployeeServce.svc`.</span><span class="sxs-lookup"><span data-stu-id="7a6b7-105">When making requests to the service you specify the .svc file in the URI, for example: `http://contoso.com/EmployeeServce.svc`.</span></span> <span data-ttu-id="7a6b7-106">REST hizmetleri yazan programcılar için, bu tür URI en uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="7a6b7-106">For programmers writing REST services, this type of URI is not optimal.</span></span> <span data-ttu-id="7a6b7-107">REST hizmetleri için URI'ler belirli bir kaynak belirtir ve normalde herhangi bir uzantısı yoktur.</span><span class="sxs-lookup"><span data-stu-id="7a6b7-107">URIs for REST services specify a specific resource and normally do not have any extensions.</span></span> <span data-ttu-id="7a6b7-108">Tümleştirme özelliği, <xref:System.Web.Routing> uri'lere uzantısı zolmadan yanıt veren bir WCF REST hizmeti barındırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="7a6b7-108">The <xref:System.Web.Routing> integration feature allows you to host a WCF REST service that responds to URIs without an extension.</span></span> <span data-ttu-id="7a6b7-109">Yönlendirme hakkında daha fazla bilgi için ASP.NET [Yönlendirme'ye](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100))bakın.</span><span class="sxs-lookup"><span data-stu-id="7a6b7-109">For more information about routing see [ASP.NET Routing](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100)).</span></span>  
  
## <a name="using-systemwebrouting-integration"></a><span data-ttu-id="7a6b7-110">System.Web.Routing Entegrasyonunu Kullanma</span><span class="sxs-lookup"><span data-stu-id="7a6b7-110">Using System.Web.Routing Integration</span></span>  
 <span data-ttu-id="7a6b7-111">Tümleştirme <xref:System.Web.Routing> özelliğini kullanmak için <xref:System.ServiceModel.Activation.ServiceRoute> sınıfı bir veya daha fazla yol <xref:System.Web.Routing.RouteTable> oluşturmak ve bunları global.asax dosyasına eklemek için kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="7a6b7-111">To use the <xref:System.Web.Routing> integration feature, you use the <xref:System.ServiceModel.Activation.ServiceRoute> class to create one or more routes and add them to the <xref:System.Web.Routing.RouteTable> in a Global.asax file.</span></span> <span data-ttu-id="7a6b7-112">Bu rotalar, hizmetin yanıt verdiği göreli ÜR'leri belirtir.</span><span class="sxs-lookup"><span data-stu-id="7a6b7-112">These routes specify the relative URIs that the service responds to.</span></span> <span data-ttu-id="7a6b7-113">Aşağıdaki örnekte, bunun nasıl yapılacağını gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7a6b7-113">The following example shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="7a6b7-114">Bu, müşterilerle başlayan göreceli bir URI `Service` ile tüm istekleri hizmete yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="7a6b7-114">This routes all requests with a relative URI that begins with Customers to the `Service` service.</span></span>  
  
 <span data-ttu-id="7a6b7-115">`System.Web.Routing.UrlRoutingModule` Web.config dosyanızda modülü eklemeniz, özniteliği `runAllManagedModulesForAllRequests` `true`ayarlamanız ve `UrlRoutingHandler` işleyiciyi `<system.webServer>` aşağıdaki örnekte gösterildiği gibi öğeye eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7a6b7-115">In your Web.config file you must add the `System.Web.Routing.UrlRoutingModule` module, set the `runAllManagedModulesForAllRequests` attribute to `true`, and add the `UrlRoutingHandler` handler to the `<system.webServer>` element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="7a6b7-116">Bu, yönlendirme için gerekli bir modül ve işleyici yükler.</span><span class="sxs-lookup"><span data-stu-id="7a6b7-116">This loads a module and handler required for routing.</span></span> <span data-ttu-id="7a6b7-117">Daha fazla bilgi için [Yönlendirme'ye](../../../../docs/framework/wcf/feature-details/routing.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="7a6b7-117">For more information, see [Routing](../../../../docs/framework/wcf/feature-details/routing.md).</span></span> <span data-ttu-id="7a6b7-118">Ayrıca, aşağıdaki `aspNetCompatibilityEnabled` `true` örnekte gösterildiği `<serviceHostingEnvironment>` gibi öğedeki özniteliği de ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7a6b7-118">You must also set the `aspNetCompatibilityEnabled` attribute to `true` in the `<serviceHostingEnvironment>` element as shown in the following example.</span></span>  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 <span data-ttu-id="7a6b7-119">Hizmeti uygulayan sınıf, aşağıdaki örnekte gösterildiği gibi ASP.NET uyumluluk gereksinimlerini etkinleştirmelidir.</span><span class="sxs-lookup"><span data-stu-id="7a6b7-119">The class that implements the service must enable ASP.NET compatibility requirements as shown in the following example.</span></span>  
  
```csharp
[ServiceContract]  
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]  
    public class Service  
    {  
        // ...  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="7a6b7-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a6b7-120">See also</span></span>

- [<span data-ttu-id="7a6b7-121">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="7a6b7-121">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- <span data-ttu-id="7a6b7-122">[ASP.NET Yönlendirme](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7a6b7-122">[ASP.NET Routing](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100))</span></span>
