---
title: 'Nasıl yapılır: ASP.NET Yetkilendirme Yöneticisi Rol Sağlayıcısını Bir Hizmetle Kullanma'
ms.date: 03/30/2017
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
ms.openlocfilehash: 20955578ce4d344c2057036c0944557edf737389
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76212231"
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a>Nasıl yapılır: ASP.NET Yetkilendirme Yöneticisi Rol Sağlayıcısını Bir Hizmetle Kullanma
ASP.NET bir Web hizmeti barındırdığınızda, hizmete yetkilendirme sağlamak için Yetkilendirme Yöneticisini uygulamayla tümleştirebilirsiniz. Yetkilendirme Yöneticisi, bir uygulama geliştiricisinin, görevleri biçimlendirmek için birlikte gruplandırılabilen bireysel işlemleri tanımlamasına olanak sağlar. Yönetici daha sonra belirli görevleri veya bağımsız işlemleri gerçekleştirmek için rolleri yetkilendirebilirler. Yetkilendirme Yöneticisi, rolleri, görevleri, işlemleri ve kullanıcıları yönetmek için bir Microsoft Yönetim Konsolu (MMC) ek bileşeni olarak bir yönetim aracı sağlar. Yöneticiler bir XML dosyasında, Active Directory veya Active Directory uygulama modu (ADAM) deposunda bir Yetkilendirme Yöneticisi ilke deposu yapılandırır.  
  
 Yetkilendirme Yöneticisi, Web hizmetini barındıran ASP.NET uygulaması için Authorization Manager ASP.NET rol sağlayıcısı yapılandırılarak uygulamayla tümleştirilir. Diğer ASP.NET rol sağlayıcıları gibi, Yetkilendirme Yöneticisi ASP.NET rol sağlayıcısı da <`providers`> öğesi kullanılarak yapılandırılır.  
  
 Aşağıdaki kod örneği, Yetkilendirme Yöneticisi 'Ni uygulamayla tümleştiren bir Web hizmeti yapılandırma dosyasının bir parçasıdır.  
  
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
  
 Bir ASP.NET rol sağlayıcısını bir WCF uygulamasıyla tümleştirme hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir hizmetle ASP.NET rol sağlayıcısını kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md). ASP.NET ile Yetkilendirme Yöneticisi 'ni kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Yetkilendirme Yöneticisi 'ni (AzMan) ASP.NET 2,0 ile](https://docs.microsoft.com/previous-versions/msp-n-p/ff649313(v=pandp.10))kullanma.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: ASP.NET Rol Sağlayıcısını Bir Hizmetle Kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
