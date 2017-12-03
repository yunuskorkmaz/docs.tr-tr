---
title: WCF'de Yetkilendirme
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- authorization [WCF]
- security [WCF], authorization
ms.assetid: 8ea0b552-af65-45b0-a157-c6c111b8ce5e
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 09bbbaad055447103a1153f1888dcae4a511cbeb
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="authorization-in-wcf"></a>WCF'de Yetkilendirme
Yetkilendirme access ve Hizmetleri ya da dosyalar gibi kaynaklara hakları denetleme işlemidir. Bu bölümdeki konular, bu temel görevi gerçekleştirmek nasıl Göster [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] çeşitli şekillerde.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Erişim denetimi mekanizmaları](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md)  
 İçinde yetkilendirme mekanizmaları kısa bir özeti sağlar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]ve önerilen kullanır.  
  
 [Nasıl yapılır: PrincipalPermissionAttribute sınıfı ile erişimi kısıtlama](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 Bir hizmetle erişimi kısıtlama sürecini gösterir <xref:System.Security.Permissions.PrincipalPermissionAttribute>.  
  
 [Nasıl yapılır: ASP.NET rol sağlayıcısını bir hizmetle kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 Rol Sağlayıcısı'nın özelliğini kullanmasını sağlamak için bir hizmet yapılandırması anlatılmaktadır [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].  
  
 [Nasıl yapılır: ASP.NET Yetkilendirme Yöneticisi Rol sağlayıcısını bir hizmetle kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Yetkilendirme Yöneticisi'ni bir Web sitesi için yetkilendirme yönetmek için kullanabilirsiniz. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]benzer şekilde Dengeleme yapabilirsiniz [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]istemcilerin yetkilendirme için /Authorization Yöneticisi birleşimi.  
  
 [Beyanlar ve yetkilendirmeyi kimlik modeliyle yönetme](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 Talep tabanlı yetkilendirme kimlik modeli altyapısını kullanarak temellerini açıklar.  
  
 [Temsilcilik ve kimliğe bürünme](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)  
 Temsilcilik ve kimliğe bürünme arasındaki farkı açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Kimlik doğrulaması](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenlik genel bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Windows Server App Fabric için güvenlik modeli](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
