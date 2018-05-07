---
title: 'Nasıl yapılır: ASP.NET Yetkilendirme Yöneticisi Rol Sağlayıcısını Bir Hizmetle Kullanma'
ms.date: 03/30/2017
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
ms.openlocfilehash: 39103e86090ed57354efaf9c410a2733a58f06bc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a>Nasıl yapılır: ASP.NET Yetkilendirme Yöneticisi Rol Sağlayıcısını Bir Hizmetle Kullanma
Zaman [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] bir Web hizmetini barındıran hizmete yetkilendirme sağlamak için uygulamaya Yetkilendirme Yöneticisi tümleştirebilirsiniz. Yetkilendirme Yöneticisi form görevleri gruplanan tek tek işlemleri tanımlamak bir uygulama geliştiricisi sağlar. Bir yönetici, ardından rolleri belirli görevleri veya tek tek işlemleri gerçekleştirmek için yetki verebilir. Yetkilendirme Yöneticisi bir yönetim aracı bir Microsoft Yönetim Konsolu (MMC) ek bileşeni rolleri, görevleri, operations ve kullanıcıları yönetmek için sağlar. Yöneticiler, bir XML dosyasında, Active Directory veya bir Active Directory uygulama modu (ADAM) deposunda bir Yetkilendirme Yöneticisi ilke deposu yapılandırın.  
  
 Yetkilendirme Yöneticisi'ni tümleşik uygulamasına Yetkilendirme Yöneticisi'ni yapılandırarak [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] rol sağlayıcısı için [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web hizmetini barındıran uygulama. Gibi diğer [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] rol sağlayıcıları, Yetkilendirme Yöneticisi'ni [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] rol sağlayıcısı kullanılarak yapılandırılmış <`providers`> öğesi.  
  
 Aşağıdaki kod örneğinde, Yetkilendirme Yöneticisi'ni bir uygulamayla tümleştirmek bir Web hizmeti için bir yapılandırma dosyası bölümüdür.  
  
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
  
 Tümleştirme hakkında daha fazla bilgi için bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] rol sağlayıcısı WCF uygulamayla bkz [nasıl yapılır: ASP.NET rol sağlayıcısını bir hizmetle kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md). Yetkilendirme Yöneticisi ile kullanma hakkında daha fazla bilgi için [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], bkz: [nasıl yapılır: ASP.NET 2.0 ile kullanım Yetkilendirme Yöneticisi (AzMan)](http://go.microsoft.com/fwlink/?LinkId=71303).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: ASP.NET Rol Sağlayıcısını Bir Hizmetle Kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
