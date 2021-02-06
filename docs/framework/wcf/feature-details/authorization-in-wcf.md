---
description: Daha fazla bilgi için bkz. WCF 'de yetkilendirme
title: WCF'de Yetkilendirme
ms.date: 03/30/2017
helpviewer_keywords:
- authorization [WCF]
- security [WCF], authorization
ms.assetid: 8ea0b552-af65-45b0-a157-c6c111b8ce5e
ms.openlocfilehash: 3fda699a33d8b512d047232398e9cfac63661a85
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643715"
---
# <a name="authorization-in-wcf"></a>WCF'de Yetkilendirme

Yetkilendirme, hizmetler veya dosyalar gibi kaynaklara erişimi ve hakları denetleme işlemidir. Bu bölümdeki konularda, bu temel görevin çeşitli yollarla Windows Communication Foundation (WCF) üzerinde nasıl gerçekleştirileceği gösterilmektedir.  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [Erişim Denetimi Mekanizmaları](access-control-mechanisms.md)  
 WCF 'de yetkilendirme mekanizmalarının kısa bir özetini ve önerilen kullanımları sağlar.  
  
 [Nasıl yapılır: PrincipalPermissionAttribute Sınıfı ile Erişimi Kısıtlama](../how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 İle bir hizmete erişimi kısıtlama sürecini gösterir <xref:System.Security.Permissions.PrincipalPermissionAttribute> .  
  
 [Nasıl yapılır: ASP.NET Rol Sağlayıcısını Bir Hizmetle Kullanma](how-to-use-the-aspnet-role-provider-with-a-service.md)  
 ASP.NET 'in rol sağlayıcısı özelliğini kullanmasını sağlamak için bir hizmetin yapılandırılmasını adım adım açıklar.  
  
 [Nasıl yapılır: ASP.NET Yetkilendirme Yöneticisi Rol Sağlayıcısını Bir Hizmetle Kullanma](how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)  
 ASP.NET, bir Web sitesi için yetkilendirmeyi yönetmek üzere Yetkilendirme Yöneticisi 'ni kullanabilir. WCF, istemci yetkilendirmesi için ASP.NET/Authorization Manager bileşiminden benzer şekilde yararlanabilir.  
  
 [Kimlik Modeliyle Beyanlar ve Yetkilendirmeyi Yönetme](managing-claims-and-authorization-with-the-identity-model.md)  
 Talep tabanlı yetkilendirme için kimlik modeli altyapısını kullanmanın temellerini açıklar.  
  
 [Temsilcilik ve Kimliğe Bürünme](delegation-and-impersonation-with-wcf.md)  
 Temsil ve kimliğe bürünme arasındaki farkı açıklar.  
  
## <a name="reference"></a>Başvuru  

 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
## <a name="related-sections"></a>İlgili Bölümler  

 [Kimlik Doğrulaması](authentication-in-wcf.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenliğe genel bakış](security-overview.md)
- [Windows Server App Fabric için güvenlik modeli](/previous-versions/appfabric/ee677202(v=azure.10))
