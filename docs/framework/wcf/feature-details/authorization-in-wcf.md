---
title: WCF'de Yetkilendirme
ms.date: 03/30/2017
helpviewer_keywords:
- authorization [WCF]
- security [WCF], authorization
ms.assetid: 8ea0b552-af65-45b0-a157-c6c111b8ce5e
ms.openlocfilehash: 26aa445f3136fcb16e2eb9cdce6b245476297dfd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59161381"
---
# <a name="authorization-in-wcf"></a>WCF'de Yetkilendirme
Yetkilendirme, erişim ve kaynakları, hizmetleri ya da dosyalar gibi haklar denetleme işlemidir. Bu bölümdeki konular, çeşitli şekillerde Windows Communication Foundation (WCF) içinde temel bu görevi gerçekleştirmek nasıl gösterir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Erişim Denetimi Mekanizmaları](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md)  
 WCF ve önerilen kullandığı yetkilendirme mekanizmalarını kısa bir özetini sağlar.  
  
 [Nasıl yapılır: PrincipalPermissionAttribute sınıfı ile erişimi kısıtlama](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 İle ilgili bir hizmete erişimi kısıtlamak işlemini gösterir <xref:System.Security.Permissions.PrincipalPermissionAttribute>.  
  
 [Nasıl yapılır: ASP.NET rol sağlayıcısını bir hizmetle kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 Rol sağlayıcı özelliğini kullanmasını sağlamak için bir hizmet yapılandırmasını [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].  
  
 [Nasıl yapılır: ASP.NET Yetkilendirme Yöneticisi Rol sağlayıcısını bir hizmetle kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Yetkilendirme Yöneticisi, bir Web sitesi için yetkilendirmeyi yönetmek için kullanabilirsiniz. WCF benzer şekilde yararlanabilir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]istemcilerin yetkilendirme /Authorization Manager birleşimi.  
  
 [Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 Beyana dayalı yetkilendirme için kimlik modeli altyapısı kullanmanın temellerini açıklar.  
  
 [Temsilcilik ve Kimliğe Bürünme](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)  
 Temsilcilik ve kimliğe bürünme arasındaki farkı açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Kimlik Doğrulaması](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenliğe Genel Bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Windows Server AppFabric için güvenlik modeli](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
