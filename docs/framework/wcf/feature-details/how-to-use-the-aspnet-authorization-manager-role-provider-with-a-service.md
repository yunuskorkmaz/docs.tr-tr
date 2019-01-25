---
title: 'Nasıl yapılır: ASP.NET Yetkilendirme Yöneticisi Rol sağlayıcısını bir hizmetle kullanma'
ms.date: 03/30/2017
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
ms.openlocfilehash: de6c96fd8d0ea17954463d554504cdb4180a5268
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54625568"
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a>Nasıl yapılır: ASP.NET Yetkilendirme Yöneticisi Rol sağlayıcısını bir hizmetle kullanma
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
  
 Tümleştirme hakkında daha fazla bilgi için bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] rol sağlayıcısı ile WCF uygulaması, bakın [nasıl yapılır: ASP.NET rol sağlayıcısını bir hizmetle kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md). Authorization Manager ile kullanma hakkında daha fazla bilgi için [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], bkz: [nasıl yapılır: Yetkilendirme Yöneticisi'ni (AzMan) ASP.NET 2.0 ile](https://go.microsoft.com/fwlink/?LinkId=71303).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: ASP.NET rol sağlayıcısını bir hizmetle kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
