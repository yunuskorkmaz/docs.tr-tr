---
title: 'Nasıl yapılır: ASP.NET Yetkilendirme Yöneticisi Rol Sağlayıcısını Bir Hizmetle Kullanma'
ms.date: 03/30/2017
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
ms.openlocfilehash: c21c1a80468bd81f2df69009afd2be86ee714250
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2018
ms.locfileid: "43331715"
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a>Nasıl yapılır: ASP.NET Yetkilendirme Yöneticisi Rol Sağlayıcısını Bir Hizmetle Kullanma
Zaman [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] bir Web hizmetini barındıran hizmete yetkilendirme sağlamak için uygulamaya Yetkilendirme Yöneticisi tümleştirebilirsiniz. Yetkilendirme Yöneticisi form görevleri gruplandırılmış tek işlemler tanımlamak bir uygulama geliştiricisi sağlar. Yönetici, ardından rolleri belirli görevleri veya tek işlemler gerçekleştirmek için yetki verebilir. Yetkilendirme Yöneticisi bir Microsoft Yönetim Konsolu (MMC) ek rol, görevleri, operations ve kullanıcıları yönetmek için bileşeni bir yönetim aracı sağlar. Yöneticiler, bir XML dosyasında, Active Directory veya bir Active Directory uygulama modu (ADAM) deposunda bir Yetkilendirme Yöneticisi'ni ilke deposu yapılandırın.  
  
 Yetkilendirme Yöneticisi, uygulamaya Yetkilendirme Yöneticisi'ni yapılandırarak tümleşiktir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] rol sağlayıcısı için [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web hizmetini barındıran uygulama. Gibi diğer [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Yetkilendirme Yöneticisi rol sağlayıcılarının [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] rol sağlayıcısını kullanarak yapılandırılmış <`providers`> öğesi.  
  
 Aşağıdaki kod örneği, bir Web hizmeti Yetkilendirme Yöneticisi, uygulamayla tümleştirmek için bir yapılandırma dosyası bir kısmıdır.  
  
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
  
 Tümleştirme hakkında daha fazla bilgi için bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] rol sağlayıcısı ile WCF uygulaması, bakın [nasıl yapılır: ASP.NET rol sağlayıcısını bir hizmetle kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md). Authorization Manager ile kullanma hakkında daha fazla bilgi için [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], bkz: [nasıl yapılır: ASP.NET 2.0 ile kullanım Yetkilendirme Yöneticisi (AzMan)](https://go.microsoft.com/fwlink/?LinkId=71303).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: ASP.NET Rol Sağlayıcısını Bir Hizmetle Kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
