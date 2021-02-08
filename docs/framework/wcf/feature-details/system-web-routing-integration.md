---
description: ': System. Web. Routing Integration hakkında daha fazla bilgi edinin'
title: System.Web.Routing Tümleştirmesi
ms.date: 03/30/2017
ms.assetid: 31fe2a4f-5c47-4e5d-8ee1-84c524609d41
ms.openlocfilehash: 8f396d5a3cad30f5cc67cb0cf44fad76a0bb54c9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793343"
---
# <a name="systemwebrouting-integration"></a><span data-ttu-id="263a5-103">System.Web.Routing Tümleştirmesi</span><span class="sxs-lookup"><span data-stu-id="263a5-103">System.Web.Routing Integration</span></span>

<span data-ttu-id="263a5-104">Internet Information Service (IIS) içinde bir Windows Communication Foundation (WCF) hizmeti barındırırken, sanal dizinde bir. svc dosyası yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="263a5-104">When hosting a Windows Communication Foundation (WCF) service in Internet Information Service (IIS) you place a .svc file in the virtual directory.</span></span> <span data-ttu-id="263a5-105">Bu. svc dosyası, kullanılacak hizmet ana bilgisayar fabrikasını ve hizmeti uygulayan sınıfını belirtir.</span><span class="sxs-lookup"><span data-stu-id="263a5-105">This .svc file specifies the service host factory to use as well as the class that implements the service.</span></span> <span data-ttu-id="263a5-106">Hizmete istek yaparken, URI 'de. svc dosyasını belirtirsiniz, örneğin: `http://contoso.com/EmployeeServce.svc` .</span><span class="sxs-lookup"><span data-stu-id="263a5-106">When making requests to the service you specify the .svc file in the URI, for example: `http://contoso.com/EmployeeServce.svc`.</span></span> <span data-ttu-id="263a5-107">REST Hizmetleri yazan programcılar için, bu tür bir URI en uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="263a5-107">For programmers writing REST services, this type of URI is not optimal.</span></span> <span data-ttu-id="263a5-108">REST Hizmetleri için URI 'Ler belirli bir kaynağı belirtir ve normalde hiçbir uzantıya sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="263a5-108">URIs for REST services specify a specific resource and normally do not have any extensions.</span></span> <span data-ttu-id="263a5-109"><xref:System.Web.Routing>Tümleştirme özelliği, uzantısı olmayan URI 'lere yanıt veren bır WCF REST hizmetini barındırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="263a5-109">The <xref:System.Web.Routing> integration feature allows you to host a WCF REST service that responds to URIs without an extension.</span></span> <span data-ttu-id="263a5-110">Yönlendirme hakkında daha fazla bilgi için bkz. [ASP.net Routing](/previous-versions/aspnet/cc668201(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="263a5-110">For more information about routing see [ASP.NET Routing](/previous-versions/aspnet/cc668201(v=vs.100)).</span></span>  
  
## <a name="using-systemwebrouting-integration"></a><span data-ttu-id="263a5-111">System. Web. Routing tümleştirmesini kullanma</span><span class="sxs-lookup"><span data-stu-id="263a5-111">Using System.Web.Routing Integration</span></span>  

 <span data-ttu-id="263a5-112"><xref:System.Web.Routing>Tümleştirme özelliğini kullanmak için <xref:System.ServiceModel.Activation.ServiceRoute> sınıfını kullanarak bir veya daha fazla yol oluşturun ve bunları <xref:System.Web.Routing.RouteTable> Global. asax dosyasına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="263a5-112">To use the <xref:System.Web.Routing> integration feature, you use the <xref:System.ServiceModel.Activation.ServiceRoute> class to create one or more routes and add them to the <xref:System.Web.Routing.RouteTable> in a Global.asax file.</span></span> <span data-ttu-id="263a5-113">Bu rotalar hizmetin yanıt verdiği göreli URI 'Leri belirtir.</span><span class="sxs-lookup"><span data-stu-id="263a5-113">These routes specify the relative URIs that the service responds to.</span></span> <span data-ttu-id="263a5-114">Aşağıdaki örnek bunun nasıl yapılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="263a5-114">The following example shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="263a5-115">Bu, tüm istekleri müşterilerle çalışmaya başlayan göreli bir URI ile yönlendirir `Service` .</span><span class="sxs-lookup"><span data-stu-id="263a5-115">This routes all requests with a relative URI that begins with Customers to the `Service` service.</span></span>  
  
 <span data-ttu-id="263a5-116">Web.config dosyanızda `System.Web.Routing.UrlRoutingModule` modülünü eklemeniz, `runAllManagedModulesForAllRequests` özniteliğini olarak ayarlamanız `true` ve `UrlRoutingHandler` `<system.webServer>` Aşağıdaki örnekte gösterildiği gibi işleyiciyi öğesine eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="263a5-116">In your Web.config file you must add the `System.Web.Routing.UrlRoutingModule` module, set the `runAllManagedModulesForAllRequests` attribute to `true`, and add the `UrlRoutingHandler` handler to the `<system.webServer>` element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="263a5-117">Bu, yönlendirme için gerekli bir modülü ve işleyiciyi yükler.</span><span class="sxs-lookup"><span data-stu-id="263a5-117">This loads a module and handler required for routing.</span></span> <span data-ttu-id="263a5-118">Daha fazla bilgi için bkz. [yönlendirme](routing.md).</span><span class="sxs-lookup"><span data-stu-id="263a5-118">For more information, see [Routing](routing.md).</span></span> <span data-ttu-id="263a5-119">Ayrıca, `aspNetCompatibilityEnabled` `true` `<serviceHostingEnvironment>` Aşağıdaki örnekte gösterildiği gibi öğesini öğesi içinde olarak ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="263a5-119">You must also set the `aspNetCompatibilityEnabled` attribute to `true` in the `<serviceHostingEnvironment>` element as shown in the following example.</span></span>  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 <span data-ttu-id="263a5-120">Hizmeti uygulayan sınıfın aşağıdaki örnekte gösterildiği gibi ASP.NET uyumluluk gereksinimlerini etkinleştirmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="263a5-120">The class that implements the service must enable ASP.NET compatibility requirements as shown in the following example.</span></span>  
  
```csharp
[ServiceContract]  
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]  
    public class Service  
    {  
        // ...  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="263a5-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="263a5-121">See also</span></span>

- [<span data-ttu-id="263a5-122">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="263a5-122">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
- <span data-ttu-id="263a5-123">[ASP.NET yönlendirme](/previous-versions/aspnet/cc668201(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="263a5-123">[ASP.NET Routing](/previous-versions/aspnet/cc668201(v=vs.100))</span></span>
