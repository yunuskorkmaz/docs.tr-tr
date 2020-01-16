---
title: WCF'de Yetkilendirme
ms.date: 03/30/2017
helpviewer_keywords:
- authorization [WCF]
- security [WCF], authorization
ms.assetid: 8ea0b552-af65-45b0-a157-c6c111b8ce5e
ms.openlocfilehash: 0097adc3d9677d9ce5595a3ac632b51d94d53f6f
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964679"
---
# <a name="authorization-in-wcf"></a>WCF'de Yetkilendirme
Yetkilendirme, hizmetler veya dosyalar gibi kaynaklara erişimi ve hakları denetleme işlemidir. Bu bölümdeki konularda, bu temel görevin çeşitli yollarla Windows Communication Foundation (WCF) üzerinde nasıl gerçekleştirileceği gösterilmektedir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Erişim Denetimi Mekanizmaları](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md)  
 WCF 'de yetkilendirme mekanizmalarının kısa bir özetini ve önerilen kullanımları sağlar.  
  
 [Nasıl yapılır: PrincipalPermissionAttribute Sınıfı ile Erişimi Kısıtlama](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>bir hizmete erişimi kısıtlama sürecini gösterir.  
  
 [Nasıl yapılır: ASP.NET Rol Sağlayıcısını Bir Hizmetle Kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 ASP.NET 'in rol sağlayıcısı özelliğini kullanmasını sağlamak için bir hizmetin yapılandırılmasını adım adım açıklar.  
  
 [Nasıl yapılır: ASP.NET Yetkilendirme Yöneticisi Rol Sağlayıcısını Bir Hizmetle Kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)  
 ASP.NET, bir Web sitesi için yetkilendirmeyi yönetmek üzere Yetkilendirme Yöneticisi 'ni kullanabilir. WCF, istemci yetkilendirmesi için ASP.NET/Authorization Manager bileşiminden benzer şekilde yararlanabilir.  
  
 [Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 Talep tabanlı yetkilendirme için kimlik modeli altyapısını kullanmanın temellerini açıklar.  
  
 [Temsilcilik ve Kimliğe Bürünme](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)  
 Temsil ve kimliğe bürünme arasındaki farkı açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Kimlik Doğrulaması](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenliğe Genel Bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Windows Server App Fabric için güvenlik modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
