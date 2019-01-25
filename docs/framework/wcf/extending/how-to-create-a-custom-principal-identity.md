---
title: 'Nasıl yapılır: Özel asıl kimlik oluşturma'
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
ms.openlocfilehash: 8f957419bcb12b0dbe735240df3cd38fa7d16e76
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54739686"
---
# <a name="how-to-create-a-custom-principal-identity"></a><span data-ttu-id="af89a-102">Nasıl yapılır: Özel asıl kimlik oluşturma</span><span class="sxs-lookup"><span data-stu-id="af89a-102">How to: Create a Custom Principal Identity</span></span>
<span data-ttu-id="af89a-103"><xref:System.Security.Permissions.PrincipalPermissionAttribute> Hizmet yöntemleri erişimi denetleme, bildirim temelli bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="af89a-103">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is a declarative means of controlling access to service methods.</span></span> <span data-ttu-id="af89a-104">Bu öznitelik kullanırken <xref:System.ServiceModel.Description.PrincipalPermissionMode> numaralandırma yetkilendirme denetimleri gerçekleştirmek için modu belirtir.</span><span class="sxs-lookup"><span data-stu-id="af89a-104">When using this attribute, the <xref:System.ServiceModel.Description.PrincipalPermissionMode> enumeration specifies the mode for performing authorization checks.</span></span> <span data-ttu-id="af89a-105">Bu modu ayarlandığında <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom>, özel bir belirtmesini sağlayan <xref:System.Security.Principal.IPrincipal> sınıfı tarafından döndürülen <xref:System.Threading.Thread.CurrentPrincipal%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="af89a-105">When this mode is set to <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom>, it enables the user to specify a custom <xref:System.Security.Principal.IPrincipal> class returned by the <xref:System.Threading.Thread.CurrentPrincipal%2A> property.</span></span> <span data-ttu-id="af89a-106">Bu konuda senaryoyu gösteren zaman <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom> özel yetkilendirme ilkesi ve özel bir kural ile birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="af89a-106">This topic illustrates the scenario when <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom> is used in combination with a custom authorization policy and a custom principal.</span></span>  
  
 <span data-ttu-id="af89a-107">Kullanma hakkında daha fazla bilgi için <xref:System.Security.Permissions.PrincipalPermissionAttribute>, bkz: [nasıl yapılır: PrincipalPermissionAttribute sınıfı ile erişimi kısıtlama](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span><span class="sxs-lookup"><span data-stu-id="af89a-107">For more information about using the <xref:System.Security.Permissions.PrincipalPermissionAttribute>, see [How to: Restrict Access with the PrincipalPermissionAttribute Class](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="af89a-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="af89a-108">Example</span></span>  
 [!code-csharp[PrincipalPermissionMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/principalpermissionmode/cs/source.cs#8)]
 [!code-vb[PrincipalPermissionMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/principalpermissionmode/vb/source.vb#8)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="af89a-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="af89a-109">Compiling the Code</span></span>  
 <span data-ttu-id="af89a-110">Aşağıdaki ad alanlarına başvurular, kodu derlemek için gereklidir:</span><span class="sxs-lookup"><span data-stu-id="af89a-110">References to the following namespaces are needed to compile the code:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="af89a-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af89a-111">See also</span></span>
- <xref:System.ServiceModel.Description.PrincipalPermissionMode>
- <xref:System.ServiceModel.Description.PrincipalPermissionMode>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- [<span data-ttu-id="af89a-112">Nasıl yapılır: ASP.NET rol sağlayıcısını bir hizmetle kullanma</span><span class="sxs-lookup"><span data-stu-id="af89a-112">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [<span data-ttu-id="af89a-113">Nasıl yapılır: PrincipalPermissionAttribute sınıfı ile erişimi kısıtlama</span><span class="sxs-lookup"><span data-stu-id="af89a-113">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
