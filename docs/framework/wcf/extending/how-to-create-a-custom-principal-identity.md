---
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
ms.openlocfilehash: 05a90c4020f225414b21e82684e46b3c2abda010
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797076"
---
# <a name="how-to-create-a-custom-principal-identity"></a>Nasıl yapılır: Özel Sorumlu Kimliği Oluşturma
, <xref:System.Security.Permissions.PrincipalPermissionAttribute> Hizmet yöntemlerine erişimi denetlemenin bildirime dayalı bir yöntemidir. Bu öznitelik <xref:System.ServiceModel.Description.PrincipalPermissionMode> kullanılırken listeleme, yetkilendirme denetimleri gerçekleştirme modunu belirtir. Bu mod olarak <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom>ayarlandığında, kullanıcının <xref:System.Threading.Thread.CurrentPrincipal%2A> özelliği tarafından döndürülen özel <xref:System.Security.Principal.IPrincipal> bir sınıf belirtmesini sağlar. Bu konu başlığı altında, özel <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom> bir yetkilendirme ilkesiyle birlikte kullanılan ve özel bir sorumlu olan senaryo gösterilmektedir.  
  
 Kullanma <xref:System.Security.Permissions.PrincipalPermissionAttribute>hakkında daha fazla bilgi için bkz [. nasıl yapılır: PrincipalPermissionAttribute sınıfıyla](../how-to-restrict-access-with-the-principalpermissionattribute-class.md)erişimi kısıtlayın.  
  
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
- [Nasıl yapılır: ASP.NET rol sağlayıcısını bir hizmetle kullanma](../feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [Nasıl yapılır: PrincipalPermissionAttribute sınıfı ile erişimi kısıtlama](../how-to-restrict-access-with-the-principalpermissionattribute-class.md)
