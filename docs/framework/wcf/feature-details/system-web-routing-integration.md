---
title: System.Web.Routing Tümleştirmesi
ms.date: 03/30/2017
ms.assetid: 31fe2a4f-5c47-4e5d-8ee1-84c524609d41
ms.openlocfilehash: 059f14c94bb7502a2e4f4616ca2c5e6ac5273afa
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600743"
---
# <a name="systemwebrouting-integration"></a><span data-ttu-id="3ba0b-102">System.Web.Routing Tümleştirmesi</span><span class="sxs-lookup"><span data-stu-id="3ba0b-102">System.Web.Routing Integration</span></span>
<span data-ttu-id="3ba0b-103">Internet Information Service (IIS) içinde bir Windows Communication Foundation (WCF) hizmeti barındırırken, sanal dizinde bir. svc dosyası yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3ba0b-103">When hosting a Windows Communication Foundation (WCF) service in Internet Information Service (IIS) you place a .svc file in the virtual directory.</span></span> <span data-ttu-id="3ba0b-104">Bu. svc dosyası, kullanılacak hizmet ana bilgisayar fabrikasını ve hizmeti uygulayan sınıfını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3ba0b-104">This .svc file specifies the service host factory to use as well as the class that implements the service.</span></span> <span data-ttu-id="3ba0b-105">Hizmete istek yaparken, URI 'de. svc dosyasını belirtirsiniz, örneğin: `http://contoso.com/EmployeeServce.svc` .</span><span class="sxs-lookup"><span data-stu-id="3ba0b-105">When making requests to the service you specify the .svc file in the URI, for example: `http://contoso.com/EmployeeServce.svc`.</span></span> <span data-ttu-id="3ba0b-106">REST Hizmetleri yazan programcılar için, bu tür bir URI en uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="3ba0b-106">For programmers writing REST services, this type of URI is not optimal.</span></span> <span data-ttu-id="3ba0b-107">REST Hizmetleri için URI 'Ler belirli bir kaynağı belirtir ve normalde hiçbir uzantıya sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="3ba0b-107">URIs for REST services specify a specific resource and normally do not have any extensions.</span></span> <span data-ttu-id="3ba0b-108"><xref:System.Web.Routing>Tümleştirme özelliği, uzantısı olmayan URI 'lere yanıt veren bır WCF REST hizmetini barındırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3ba0b-108">The <xref:System.Web.Routing> integration feature allows you to host a WCF REST service that responds to URIs without an extension.</span></span> <span data-ttu-id="3ba0b-109">Yönlendirme hakkında daha fazla bilgi için bkz. [ASP.net Routing](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="3ba0b-109">For more information about routing see [ASP.NET Routing](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100)).</span></span>  
  
## <a name="using-systemwebrouting-integration"></a><span data-ttu-id="3ba0b-110">System. Web. Routing tümleştirmesini kullanma</span><span class="sxs-lookup"><span data-stu-id="3ba0b-110">Using System.Web.Routing Integration</span></span>  
 <span data-ttu-id="3ba0b-111"><xref:System.Web.Routing>Tümleştirme özelliğini kullanmak için <xref:System.ServiceModel.Activation.ServiceRoute> sınıfını kullanarak bir veya daha fazla yol oluşturun ve bunları <xref:System.Web.Routing.RouteTable> Global. asax dosyasına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3ba0b-111">To use the <xref:System.Web.Routing> integration feature, you use the <xref:System.ServiceModel.Activation.ServiceRoute> class to create one or more routes and add them to the <xref:System.Web.Routing.RouteTable> in a Global.asax file.</span></span> <span data-ttu-id="3ba0b-112">Bu rotalar hizmetin yanıt verdiği göreli URI 'Leri belirtir.</span><span class="sxs-lookup"><span data-stu-id="3ba0b-112">These routes specify the relative URIs that the service responds to.</span></span> <span data-ttu-id="3ba0b-113">Aşağıdaki örnek bunun nasıl yapılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="3ba0b-113">The following example shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="3ba0b-114">Bu, tüm istekleri müşterilerle çalışmaya başlayan göreli bir URI ile yönlendirir `Service` .</span><span class="sxs-lookup"><span data-stu-id="3ba0b-114">This routes all requests with a relative URI that begins with Customers to the `Service` service.</span></span>  
  
 <span data-ttu-id="3ba0b-115">Web. config dosyanızda `System.Web.Routing.UrlRoutingModule` modülünü eklemeniz, `runAllManagedModulesForAllRequests` özniteliğini olarak ayarlamanız `true` ve `UrlRoutingHandler` `<system.webServer>` Aşağıdaki örnekte gösterildiği gibi işleyiciyi öğesine eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3ba0b-115">In your Web.config file you must add the `System.Web.Routing.UrlRoutingModule` module, set the `runAllManagedModulesForAllRequests` attribute to `true`, and add the `UrlRoutingHandler` handler to the `<system.webServer>` element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="3ba0b-116">Bu, yönlendirme için gerekli bir modülü ve işleyiciyi yükler.</span><span class="sxs-lookup"><span data-stu-id="3ba0b-116">This loads a module and handler required for routing.</span></span> <span data-ttu-id="3ba0b-117">Daha fazla bilgi için bkz. [yönlendirme](routing.md).</span><span class="sxs-lookup"><span data-stu-id="3ba0b-117">For more information, see [Routing](routing.md).</span></span> <span data-ttu-id="3ba0b-118">Ayrıca, `aspNetCompatibilityEnabled` `true` `<serviceHostingEnvironment>` Aşağıdaki örnekte gösterildiği gibi öğesini öğesi içinde olarak ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3ba0b-118">You must also set the `aspNetCompatibilityEnabled` attribute to `true` in the `<serviceHostingEnvironment>` element as shown in the following example.</span></span>  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 <span data-ttu-id="3ba0b-119">Hizmeti uygulayan sınıfın aşağıdaki örnekte gösterildiği gibi ASP.NET uyumluluk gereksinimlerini etkinleştirmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="3ba0b-119">The class that implements the service must enable ASP.NET compatibility requirements as shown in the following example.</span></span>  
  
```csharp
[ServiceContract]  
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]  
    public class Service  
    {  
        // ...  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="3ba0b-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3ba0b-120">See also</span></span>

- [<span data-ttu-id="3ba0b-121">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="3ba0b-121">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
- <span data-ttu-id="3ba0b-122">[ASP.NET yönlendirme](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3ba0b-122">[ASP.NET Routing](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100))</span></span>
