---
title: WCF'de Yetkilendirme
ms.date: 03/30/2017
helpviewer_keywords:
- authorization [WCF]
- security [WCF], authorization
ms.assetid: 8ea0b552-af65-45b0-a157-c6c111b8ce5e
ms.openlocfilehash: c6bf779c7baeea1f9a253ad0bde966cea67b57aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488578"
---
# <a name="authorization-in-wcf"></a>WCF'de Yetkilendirme
Yetkilendirme access ve Hizmetleri ya da dosyalar gibi kaynaklara hakları denetleme işlemidir. Bu bölümdeki konular, çeşitli şekillerde Windows Communication Foundation (WCF) içinde bu temel görevi gerçekleştirmek nasıl gösterir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Erişim Denetimi Mekanizmaları](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md)  
 WCF ve önerilen kullandığı yetkilendirme mekanizmaları kısa bir özetini sağlar.  
  
 [Nasıl yapılır: PrincipalPermissionAttribute Sınıfı ile Erişimi Kısıtlama](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 Bir hizmetle erişimi kısıtlama sürecini gösterir <xref:System.Security.Permissions.PrincipalPermissionAttribute>.  
  
 [Nasıl yapılır: ASP.NET Rol Sağlayıcısını Bir Hizmetle Kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 Rol Sağlayıcısı'nın özelliğini kullanmasını sağlamak için bir hizmet yapılandırması anlatılmaktadır [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].  
  
 [Nasıl yapılır: ASP.NET Yetkilendirme Yöneticisi Rol Sağlayıcısını Bir Hizmetle Kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Yetkilendirme Yöneticisi'ni bir Web sitesi için yetkilendirme yönetmek için kullanabilirsiniz. WCF benzer şekilde yararlanabilir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]istemcilerin yetkilendirme için /Authorization Yöneticisi birleşimi.  
  
 [Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 Talep tabanlı yetkilendirme kimlik modeli altyapısını kullanarak temellerini açıklar.  
  
 [Temsilcilik ve Kimliğe Bürünme](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)  
 Temsilcilik ve kimliğe bürünme arasındaki farkı açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Kimlik Doğrulaması](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenliğe Genel Bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Windows Server App Fabric için güvenlik modeli](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
