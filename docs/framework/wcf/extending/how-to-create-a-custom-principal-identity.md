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
# <a name="how-to-create-a-custom-principal-identity"></a><span data-ttu-id="2de96-102">Nasıl yapılır: Özel Sorumlu Kimliği Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2de96-102">How to: Create a Custom Principal Identity</span></span>
<span data-ttu-id="2de96-103">, <xref:System.Security.Permissions.PrincipalPermissionAttribute> Hizmet yöntemlerine erişimi denetlemenin bildirime dayalı bir yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="2de96-103">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is a declarative means of controlling access to service methods.</span></span> <span data-ttu-id="2de96-104">Bu öznitelik <xref:System.ServiceModel.Description.PrincipalPermissionMode> kullanılırken listeleme, yetkilendirme denetimleri gerçekleştirme modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="2de96-104">When using this attribute, the <xref:System.ServiceModel.Description.PrincipalPermissionMode> enumeration specifies the mode for performing authorization checks.</span></span> <span data-ttu-id="2de96-105">Bu mod olarak <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom>ayarlandığında, kullanıcının <xref:System.Threading.Thread.CurrentPrincipal%2A> özelliği tarafından döndürülen özel <xref:System.Security.Principal.IPrincipal> bir sınıf belirtmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="2de96-105">When this mode is set to <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom>, it enables the user to specify a custom <xref:System.Security.Principal.IPrincipal> class returned by the <xref:System.Threading.Thread.CurrentPrincipal%2A> property.</span></span> <span data-ttu-id="2de96-106">Bu konu başlığı altında, özel <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom> bir yetkilendirme ilkesiyle birlikte kullanılan ve özel bir sorumlu olan senaryo gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2de96-106">This topic illustrates the scenario when <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom> is used in combination with a custom authorization policy and a custom principal.</span></span>  
  
 <span data-ttu-id="2de96-107">Kullanma <xref:System.Security.Permissions.PrincipalPermissionAttribute>hakkında daha fazla bilgi için bkz [. nasıl yapılır: PrincipalPermissionAttribute sınıfıyla](../how-to-restrict-access-with-the-principalpermissionattribute-class.md)erişimi kısıtlayın.</span><span class="sxs-lookup"><span data-stu-id="2de96-107">For more information about using the <xref:System.Security.Permissions.PrincipalPermissionAttribute>, see [How to: Restrict Access with the PrincipalPermissionAttribute Class](../how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2de96-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="2de96-108">Example</span></span>  
 [!code-csharp[PrincipalPermissionMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/principalpermissionmode/cs/source.cs#8)]
 [!code-vb[PrincipalPermissionMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/principalpermissionmode/vb/source.vb#8)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2de96-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="2de96-109">Compiling the Code</span></span>  
 <span data-ttu-id="2de96-110">Kodu derlemek için aşağıdaki ad alanlarına başvurular gereklidir:</span><span class="sxs-lookup"><span data-stu-id="2de96-110">References to the following namespaces are needed to compile the code:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2de96-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2de96-111">See also</span></span>

- <xref:System.ServiceModel.Description.PrincipalPermissionMode>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- [<span data-ttu-id="2de96-112">Nasıl yapılır: ASP.NET rol sağlayıcısını bir hizmetle kullanma</span><span class="sxs-lookup"><span data-stu-id="2de96-112">How to: Use the ASP.NET Role Provider with a Service</span></span>](../feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [<span data-ttu-id="2de96-113">Nasıl yapılır: PrincipalPermissionAttribute sınıfı ile erişimi kısıtlama</span><span class="sxs-lookup"><span data-stu-id="2de96-113">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../how-to-restrict-access-with-the-principalpermissionattribute-class.md)
