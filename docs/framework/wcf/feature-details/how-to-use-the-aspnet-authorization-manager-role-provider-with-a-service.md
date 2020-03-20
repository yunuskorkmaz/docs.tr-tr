---
title: 'Nasıl yapılır: ASP.NET Yetkilendirme Yöneticisi Rol Sağlayıcısını Bir Hizmetle Kullanma'
ms.date: 03/30/2017
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
ms.openlocfilehash: 009b96defdf27591ddb98afaa684745b5fcbe0d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184806"
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a><span data-ttu-id="64a1b-102">Nasıl yapılır: ASP.NET Yetkilendirme Yöneticisi Rol Sağlayıcısını Bir Hizmetle Kullanma</span><span class="sxs-lookup"><span data-stu-id="64a1b-102">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>
<span data-ttu-id="64a1b-103">ASP.NET bir Web hizmeti barındırdığında, hizmete yetki sağlamak için Yetkilendirme Yöneticisi'ni uygulamaya entegre edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="64a1b-103">When ASP.NET hosts a Web service, you can integrate Authorization Manager into the application to provide authorization to the service.</span></span> <span data-ttu-id="64a1b-104">Yetkilendirme Yöneticisi, bir uygulama geliştiricisinin görevleri oluşturmak için birlikte gruplandırılabilen tek tek işlemleri tanımlamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="64a1b-104">Authorization Manager enables an application developer to define individual operations, which can be grouped together to form tasks.</span></span> <span data-ttu-id="64a1b-105">Yönetici daha sonra rolleri belirli görevleri veya tek tek işlemleri gerçekleştirmek için yetkilendirebilir.</span><span class="sxs-lookup"><span data-stu-id="64a1b-105">An administrator can then authorize roles to perform specific tasks or individual operations.</span></span> <span data-ttu-id="64a1b-106">Yetkilendirme Yöneticisi rolleri, görevleri, işlemleri ve kullanıcıları yönetmek için Microsoft Yönetim Konsolu (MMC) snap-in olarak bir yönetim aracı sağlar.</span><span class="sxs-lookup"><span data-stu-id="64a1b-106">Authorization Manager provides an administration tool as a Microsoft Management Console (MMC) snap-in to manage roles, tasks, operations, and users.</span></span> <span data-ttu-id="64a1b-107">Yöneticiler, Bir XML dosyasında, Etkin Dizin'de veya Etkin Dizin Uygulama Modu (ADAM) deposunda bir Yetkilendirme Yöneticisi ilkesi deposunu yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="64a1b-107">Administrators configure an Authorization Manager policy store in an XML file, Active Directory, or in an Active Directory Application Mode (ADAM) store.</span></span>  
  
 <span data-ttu-id="64a1b-108">Yetkilendirme Yöneticisi, Web hizmetini barındıran ASP.NET uygulama için Yetkilendirme Yöneticisi ASP.NET rol sağlayıcısını yapılandırarak uygulamaya entegre edilir.</span><span class="sxs-lookup"><span data-stu-id="64a1b-108">Authorization Manager is Integrated into the application by configuring the Authorization Manager ASP.NET role provider for the ASP.NET application that is hosting the Web service.</span></span> <span data-ttu-id="64a1b-109">Diğer ASP.NET rol sağlayıcıları gibi, Yetkilendirme Yöneticisi ASP.NET rol `providers` sağlayıcısı da <> öğesi kullanılarak yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="64a1b-109">Like other ASP.NET role providers, the Authorization Manager ASP.NET role provider is configured using the <`providers`> element.</span></span>  
  
 <span data-ttu-id="64a1b-110">Aşağıdaki kod örneği, Yetkilendirme Yöneticisi'ni uygulamaya entegre eden bir Web hizmeti için yapılandırma dosyasının bir bölümüdür.</span><span class="sxs-lookup"><span data-stu-id="64a1b-110">The following code example is a portion of a configuration file for a Web service that is integrating Authorization Manager into the application.</span></span>  
  
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
  
 <span data-ttu-id="64a1b-111">Bir ASP.NET rol sağlayıcısını WCF uygulamasıyla tümleştirme hakkında daha fazla bilgi için bkz [ASP.NET.](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)</span><span class="sxs-lookup"><span data-stu-id="64a1b-111">For more information about integrating an ASP.NET role provider with a WCF application, see [How to: Use the ASP.NET Role Provider with a Service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span> <span data-ttu-id="64a1b-112">Yetkilendirme Yöneticisi'ni ASP.NET kullanma hakkında daha fazla bilgi için bkz [ASP.NET.](https://docs.microsoft.com/previous-versions/msp-n-p/ff649313(v=pandp.10))</span><span class="sxs-lookup"><span data-stu-id="64a1b-112">For more information about using Authorization Manager with ASP.NET, see [How to: Use Authorization Manager (AzMan) with ASP.NET 2.0](https://docs.microsoft.com/previous-versions/msp-n-p/ff649313(v=pandp.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64a1b-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64a1b-113">See also</span></span>

- [<span data-ttu-id="64a1b-114">Nasıl yapılır: ASP.NET Rol Sağlayıcısını Bir Hizmetle Kullanma</span><span class="sxs-lookup"><span data-stu-id="64a1b-114">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
