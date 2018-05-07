---
title: 'Nasıl yapılır: Özel Esas Kimlik Oluşturma'
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
ms.openlocfilehash: e3ecee7be32cef7fc5371e56cfc32e2d0ef7ae6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-custom-principal-identity"></a>Nasıl yapılır: Özel Esas Kimlik Oluşturma
<xref:System.Security.Permissions.PrincipalPermissionAttribute> Hizmet yöntemleri erişimi denetleme, bildirim temelli bir yoludur. Bu öznitelik kullanırken <xref:System.ServiceModel.Description.PrincipalPermissionMode> numaralandırma yetkilendirme denetimleri gerçekleştirmek için modu belirtir. Bu modu ayarlandığında <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom>, özel bir belirtmesini sağlayan <xref:System.Security.Principal.IPrincipal> sınıfı tarafından döndürülen <xref:System.Threading.Thread.CurrentPrincipal%2A> özelliği. Bu konuda senaryosu gösterilmektedir, <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom> özel yetkilendirme ilkesi ve özel bir kural ile birlikte kullanılır.  
  
 Kullanma hakkında daha fazla bilgi için <xref:System.Security.Permissions.PrincipalPermissionAttribute>, bkz: [nasıl yapılır: PrincipalPermissionAttribute sınıfı ile erişimi kısıtla](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[PrincipalPermissionMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/principalpermissionmode/cs/source.cs#8)]
 [!code-vb[PrincipalPermissionMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/principalpermissionmode/vb/source.vb#8)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Kodu derlemek için aşağıdaki ad alanlarına başvurular gerekir:  
  
-   <xref:System>  
  
-   <xref:System.Collections.Generic>  
  
-   <xref:System.Security.Permissions>  
  
-   <xref:System.Security.Principal>  
  
-   <xref:System.Threading>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
-   <xref:System.ServiceModel.Description>  
  
-   <xref:System.IdentityModel.Claims>  
  
-   <xref:System.IdentityModel.Policy>  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
 [Nasıl yapılır: ASP.NET Rol Sağlayıcısını Bir Hizmetle Kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 [Nasıl yapılır: PrincipalPermissionAttribute Sınıfı ile Erişimi Kısıtlama](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
