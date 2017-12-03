---
title: "Nasıl yapılır: ASP.NET Yetkilendirme Yöneticisi Rol Sağlayıcısını Bir Hizmetle Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b0440a377e7fda1647041df0692a56da950a166b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
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
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Tümleştirme bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] rol sağlayıcısı ile bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulama, bkz: [nasıl yapılır: ASP.NET rol sağlayıcısını bir hizmetle kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Yetkilendirme Yöneticisi'nde kullanarak [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], bkz: [nasıl yapılır: ASP.NET 2.0 ile kullanım Yetkilendirme Yöneticisi (AzMan)](http://go.microsoft.com/fwlink/?LinkId=71303).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: ASP.NET rol sağlayıcısını bir hizmetle kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
