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
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a>Nasıl yapılır: ASP.NET Yetkilendirme Yöneticisi Rol Sağlayıcısını Bir Hizmetle Kullanma
ASP.NET bir Web hizmeti barındırdığında, hizmete yetki sağlamak için Yetkilendirme Yöneticisi'ni uygulamaya entegre edebilirsiniz. Yetkilendirme Yöneticisi, bir uygulama geliştiricisinin görevleri oluşturmak için birlikte gruplandırılabilen tek tek işlemleri tanımlamasını sağlar. Yönetici daha sonra rolleri belirli görevleri veya tek tek işlemleri gerçekleştirmek için yetkilendirebilir. Yetkilendirme Yöneticisi rolleri, görevleri, işlemleri ve kullanıcıları yönetmek için Microsoft Yönetim Konsolu (MMC) snap-in olarak bir yönetim aracı sağlar. Yöneticiler, Bir XML dosyasında, Etkin Dizin'de veya Etkin Dizin Uygulama Modu (ADAM) deposunda bir Yetkilendirme Yöneticisi ilkesi deposunu yapılandırır.  
  
 Yetkilendirme Yöneticisi, Web hizmetini barındıran ASP.NET uygulama için Yetkilendirme Yöneticisi ASP.NET rol sağlayıcısını yapılandırarak uygulamaya entegre edilir. Diğer ASP.NET rol sağlayıcıları gibi, Yetkilendirme Yöneticisi ASP.NET rol `providers` sağlayıcısı da <> öğesi kullanılarak yapılandırılır.  
  
 Aşağıdaki kod örneği, Yetkilendirme Yöneticisi'ni uygulamaya entegre eden bir Web hizmeti için yapılandırma dosyasının bir bölümüdür.  
  
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
  
 Bir ASP.NET rol sağlayıcısını WCF uygulamasıyla tümleştirme hakkında daha fazla bilgi için bkz [ASP.NET.](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md) Yetkilendirme Yöneticisi'ni ASP.NET kullanma hakkında daha fazla bilgi için bkz [ASP.NET.](https://docs.microsoft.com/previous-versions/msp-n-p/ff649313(v=pandp.10))  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: ASP.NET Rol Sağlayıcısını Bir Hizmetle Kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
