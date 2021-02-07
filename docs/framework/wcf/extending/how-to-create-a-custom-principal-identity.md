---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: özel bir asıl kimlik oluşturma'
title: 'Nasıl yapılır: Özel Sorumlu Kimliği Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- IPrincipal
- IAuthorizationPolicy
- PrincipalPermissionMode
- PrincipalPermissionAttribute
ms.assetid: c4845fca-0ed9-4adf-bbdc-10812be69b61
ms.openlocfilehash: 0967257021ba6cdb68426dfa48f9078afe1256fd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743687"
---
# <a name="how-to-create-a-custom-principal-identity"></a>Nasıl yapılır: Özel Sorumlu Kimliği Oluşturma

, <xref:System.Security.Permissions.PrincipalPermissionAttribute> Hizmet yöntemlerine erişimi denetlemenin bildirime dayalı bir yöntemidir. Bu öznitelik kullanılırken <xref:System.ServiceModel.Description.PrincipalPermissionMode> Listeleme, yetkilendirme denetimleri gerçekleştirme modunu belirtir. Bu mod olarak ayarlandığında <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom> , kullanıcının <xref:System.Security.Principal.IPrincipal> özelliği tarafından döndürülen özel bir sınıf belirtmesini sağlar <xref:System.Threading.Thread.CurrentPrincipal%2A> . Bu konu başlığı altında, <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom> özel bir yetkilendirme ilkesiyle birlikte kullanılan ve özel bir sorumlu olan senaryo gösterilmektedir.  
  
 Kullanma hakkında daha fazla bilgi için <xref:System.Security.Permissions.PrincipalPermissionAttribute> bkz. [nasıl yapılır: erişimi, PrincipalPermissionAttribute sınıfı ile kısıtlama](../how-to-restrict-access-with-the-principalpermissionattribute-class.md).  
  
## <a name="example"></a>Örnek  

 [!code-csharp[PrincipalPermissionMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/principalpermissionmode/cs/source.cs#8)]
 [!code-vb[PrincipalPermissionMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/principalpermissionmode/vb/source.vb#8)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  

 Kodu derlemek için aşağıdaki ad alanlarına başvurular gereklidir:  
  
- <xref:System>  
  
- <xref:System.Collections.Generic>  
  
- <xref:System.Security.Permissions>  
  
- <xref:System.Security.Principal>  
  
- <xref:System.Threading>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
- <xref:System.ServiceModel.Description>  
  
- <xref:System.IdentityModel.Claims>  
  
- <xref:System.IdentityModel.Policy>  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.PrincipalPermissionMode>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- [Nasıl yapılır: ASP.NET Rol Sağlayıcısını Bir Hizmetle Kullanma](../feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [Nasıl yapılır: PrincipalPermissionAttribute Sınıfı ile Erişimi Kısıtlama](../how-to-restrict-access-with-the-principalpermissionattribute-class.md)
