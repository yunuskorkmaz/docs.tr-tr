---
title: 'Nasıl yapılır: ASP.NET Yetkilendirme Yöneticisi Rol Sağlayıcısını Bir Hizmetle Kullanma'
ms.date: 03/30/2017
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
ms.openlocfilehash: bbdafdd96a32b41d7c6892944ed872e3f8702f0e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280604"
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a><span data-ttu-id="9830d-102">Nasıl yapılır: ASP.NET Yetkilendirme Yöneticisi Rol Sağlayıcısını Bir Hizmetle Kullanma</span><span class="sxs-lookup"><span data-stu-id="9830d-102">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>

<span data-ttu-id="9830d-103">ASP.NET bir Web hizmeti barındırdığınızda, hizmete yetkilendirme sağlamak için Yetkilendirme Yöneticisini uygulamayla tümleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9830d-103">When ASP.NET hosts a Web service, you can integrate Authorization Manager into the application to provide authorization to the service.</span></span> <span data-ttu-id="9830d-104">Yetkilendirme Yöneticisi, bir uygulama geliştiricisinin, görevleri biçimlendirmek için birlikte gruplandırılabilen bireysel işlemleri tanımlamasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="9830d-104">Authorization Manager enables an application developer to define individual operations, which can be grouped together to form tasks.</span></span> <span data-ttu-id="9830d-105">Yönetici daha sonra belirli görevleri veya bağımsız işlemleri gerçekleştirmek için rolleri yetkilendirebilirler.</span><span class="sxs-lookup"><span data-stu-id="9830d-105">An administrator can then authorize roles to perform specific tasks or individual operations.</span></span> <span data-ttu-id="9830d-106">Yetkilendirme Yöneticisi, rolleri, görevleri, işlemleri ve kullanıcıları yönetmek için bir Microsoft Yönetim Konsolu (MMC) ek bileşeni olarak bir yönetim aracı sağlar.</span><span class="sxs-lookup"><span data-stu-id="9830d-106">Authorization Manager provides an administration tool as a Microsoft Management Console (MMC) snap-in to manage roles, tasks, operations, and users.</span></span> <span data-ttu-id="9830d-107">Yöneticiler bir XML dosyasında, Active Directory veya Active Directory uygulama modu (ADAM) deposunda bir Yetkilendirme Yöneticisi ilke deposu yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="9830d-107">Administrators configure an Authorization Manager policy store in an XML file, Active Directory, or in an Active Directory Application Mode (ADAM) store.</span></span>  
  
 <span data-ttu-id="9830d-108">Yetkilendirme Yöneticisi, Web hizmetini barındıran ASP.NET uygulaması için Authorization Manager ASP.NET rol sağlayıcısı yapılandırılarak uygulamayla tümleştirilir.</span><span class="sxs-lookup"><span data-stu-id="9830d-108">Authorization Manager is Integrated into the application by configuring the Authorization Manager ASP.NET role provider for the ASP.NET application that is hosting the Web service.</span></span> <span data-ttu-id="9830d-109">Diğer ASP.NET rol sağlayıcıları gibi, Yetkilendirme Yöneticisi ASP.NET rol sağlayıcısı da <> öğesi kullanılarak yapılandırılır `providers` .</span><span class="sxs-lookup"><span data-stu-id="9830d-109">Like other ASP.NET role providers, the Authorization Manager ASP.NET role provider is configured using the <`providers`> element.</span></span>  
  
 <span data-ttu-id="9830d-110">Aşağıdaki kod örneği, Yetkilendirme Yöneticisi 'Ni uygulamayla tümleştiren bir Web hizmeti yapılandırma dosyasının bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="9830d-110">The following code example is a portion of a configuration file for a Web service that is integrating Authorization Manager into the application.</span></span>  
  
```xml  
<system.web>  
    <roleManager enabled="true" defaultProvider="AzManRoleProvider">  
      <providers>  
        <add name="AzManRoleProvider"  
             type="System.Web.Security.AuthorizationStoreRoleProvider, System.Web, Version=2.0.0.0, Culture=neutral, publicKeyToken=b03f5f7f11d50a3a"  
             connectionStringName="AzManPolicyStoreConnectionString"
             applicationName="SecureService"/>  
      </providers>  
    </roleManager>  
</system.web>  
```  
  
 <span data-ttu-id="9830d-111">Bir ASP.NET rol sağlayıcısını bir WCF uygulamasıyla tümleştirme hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir hizmetle ASP.NET rol sağlayıcısını kullanma](how-to-use-the-aspnet-role-provider-with-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="9830d-111">For more information about integrating an ASP.NET role provider with a WCF application, see [How to: Use the ASP.NET Role Provider with a Service](how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span> <span data-ttu-id="9830d-112">ASP.NET ile Yetkilendirme Yöneticisi 'ni kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Yetkilendirme Yöneticisi 'ni (AzMan) ASP.NET 2,0 ile](/previous-versions/msp-n-p/ff649313(v=pandp.10))kullanma.</span><span class="sxs-lookup"><span data-stu-id="9830d-112">For more information about using Authorization Manager with ASP.NET, see [How to: Use Authorization Manager (AzMan) with ASP.NET 2.0](/previous-versions/msp-n-p/ff649313(v=pandp.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9830d-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9830d-113">See also</span></span>

- [<span data-ttu-id="9830d-114">Nasıl yapılır: ASP.NET Rol Sağlayıcısını Bir Hizmetle Kullanma</span><span class="sxs-lookup"><span data-stu-id="9830d-114">How to: Use the ASP.NET Role Provider with a Service</span></span>](how-to-use-the-aspnet-role-provider-with-a-service.md)
