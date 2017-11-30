---
title: "Nasıl yapılır: Özel Esas Kimlik Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- IPrincipal
- IAuthorizationPolicy
- PrincipalPermissionMode
- PrincipalPermissionAttribute
ms.assetid: c4845fca-0ed9-4adf-bbdc-10812be69b61
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 973b3ebbedf80a7c33047f74306232805989646c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Nasıl yapılır: ASP.NET rol sağlayıcısını bir hizmetle kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 [Nasıl yapılır: PrincipalPermissionAttribute sınıfı ile erişimi kısıtlama](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
