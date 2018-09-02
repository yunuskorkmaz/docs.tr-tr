---
title: 'Nasıl yapılır: ASP.NET Yetkilendirme Yöneticisi Rol Sağlayıcısını Bir Hizmetle Kullanma'
ms.date: 03/30/2017
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
ms.openlocfilehash: c21c1a80468bd81f2df69009afd2be86ee714250
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43386712"
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a><span data-ttu-id="63464-102">Nasıl yapılır: ASP.NET Yetkilendirme Yöneticisi Rol Sağlayıcısını Bir Hizmetle Kullanma</span><span class="sxs-lookup"><span data-stu-id="63464-102">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>
<span data-ttu-id="63464-103">Zaman [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] bir Web hizmetini barındıran hizmete yetkilendirme sağlamak için uygulamaya Yetkilendirme Yöneticisi tümleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="63464-103">When [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] hosts a Web service, you can integrate Authorization Manager into the application to provide authorization to the service.</span></span> <span data-ttu-id="63464-104">Yetkilendirme Yöneticisi form görevleri gruplandırılmış tek işlemler tanımlamak bir uygulama geliştiricisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="63464-104">Authorization Manager enables an application developer to define individual operations, which can be grouped together to form tasks.</span></span> <span data-ttu-id="63464-105">Yönetici, ardından rolleri belirli görevleri veya tek işlemler gerçekleştirmek için yetki verebilir.</span><span class="sxs-lookup"><span data-stu-id="63464-105">An administrator can then authorize roles to perform specific tasks or individual operations.</span></span> <span data-ttu-id="63464-106">Yetkilendirme Yöneticisi bir Microsoft Yönetim Konsolu (MMC) ek rol, görevleri, operations ve kullanıcıları yönetmek için bileşeni bir yönetim aracı sağlar.</span><span class="sxs-lookup"><span data-stu-id="63464-106">Authorization Manager provides an administration tool as a Microsoft Management Console (MMC) snap-in to manage roles, tasks, operations, and users.</span></span> <span data-ttu-id="63464-107">Yöneticiler, bir XML dosyasında, Active Directory veya bir Active Directory uygulama modu (ADAM) deposunda bir Yetkilendirme Yöneticisi'ni ilke deposu yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="63464-107">Administrators configure an Authorization Manager policy store in an XML file, Active Directory, or in an Active Directory Application Mode (ADAM) store.</span></span>  
  
 <span data-ttu-id="63464-108">Yetkilendirme Yöneticisi, uygulamaya Yetkilendirme Yöneticisi'ni yapılandırarak tümleşiktir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] rol sağlayıcısı için [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web hizmetini barındıran uygulama.</span><span class="sxs-lookup"><span data-stu-id="63464-108">Authorization Manager is Integrated into the application by configuring the Authorization Manager [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider for the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application that is hosting the Web service.</span></span> <span data-ttu-id="63464-109">Gibi diğer [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Yetkilendirme Yöneticisi rol sağlayıcılarının [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] rol sağlayıcısını kullanarak yapılandırılmış <`providers`> öğesi.</span><span class="sxs-lookup"><span data-stu-id="63464-109">Like other [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role providers, the Authorization Manager [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider is configured using the <`providers`> element.</span></span>  
  
 <span data-ttu-id="63464-110">Aşağıdaki kod örneği, bir Web hizmeti Yetkilendirme Yöneticisi, uygulamayla tümleştirmek için bir yapılandırma dosyası bir kısmıdır.</span><span class="sxs-lookup"><span data-stu-id="63464-110">The following code example is a portion of a configuration file for a Web service that is integrating Authorization Manager into the application.</span></span>  
  
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
  
 <span data-ttu-id="63464-111">Tümleştirme hakkında daha fazla bilgi için bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] rol sağlayıcısı ile WCF uygulaması, bakın [nasıl yapılır: ASP.NET rol sağlayıcısını bir hizmetle kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="63464-111">For more information about integrating an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider with a WCF application, see [How to: Use the ASP.NET Role Provider with a Service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span> <span data-ttu-id="63464-112">Authorization Manager ile kullanma hakkında daha fazla bilgi için [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], bkz: [nasıl yapılır: ASP.NET 2.0 ile kullanım Yetkilendirme Yöneticisi (AzMan)](https://go.microsoft.com/fwlink/?LinkId=71303).</span><span class="sxs-lookup"><span data-stu-id="63464-112">For more information about using Authorization Manager with [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], see [How to: Use Authorization Manager (AzMan) with ASP.NET 2.0](https://go.microsoft.com/fwlink/?LinkId=71303).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63464-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="63464-113">See Also</span></span>  
 [<span data-ttu-id="63464-114">Nasıl yapılır: ASP.NET Rol Sağlayıcısını Bir Hizmetle Kullanma</span><span class="sxs-lookup"><span data-stu-id="63464-114">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
