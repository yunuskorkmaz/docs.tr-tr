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
# <a name="how-to-create-a-custom-principal-identity"></a><span data-ttu-id="0e3a8-103">Nasıl yapılır: Özel Sorumlu Kimliği Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0e3a8-103">How to: Create a Custom Principal Identity</span></span>

<span data-ttu-id="0e3a8-104">, <xref:System.Security.Permissions.PrincipalPermissionAttribute> Hizmet yöntemlerine erişimi denetlemenin bildirime dayalı bir yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="0e3a8-104">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is a declarative means of controlling access to service methods.</span></span> <span data-ttu-id="0e3a8-105">Bu öznitelik kullanılırken <xref:System.ServiceModel.Description.PrincipalPermissionMode> Listeleme, yetkilendirme denetimleri gerçekleştirme modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="0e3a8-105">When using this attribute, the <xref:System.ServiceModel.Description.PrincipalPermissionMode> enumeration specifies the mode for performing authorization checks.</span></span> <span data-ttu-id="0e3a8-106">Bu mod olarak ayarlandığında <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom> , kullanıcının <xref:System.Security.Principal.IPrincipal> özelliği tarafından döndürülen özel bir sınıf belirtmesini sağlar <xref:System.Threading.Thread.CurrentPrincipal%2A> .</span><span class="sxs-lookup"><span data-stu-id="0e3a8-106">When this mode is set to <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom>, it enables the user to specify a custom <xref:System.Security.Principal.IPrincipal> class returned by the <xref:System.Threading.Thread.CurrentPrincipal%2A> property.</span></span> <span data-ttu-id="0e3a8-107">Bu konu başlığı altında, <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom> özel bir yetkilendirme ilkesiyle birlikte kullanılan ve özel bir sorumlu olan senaryo gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0e3a8-107">This topic illustrates the scenario when <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom> is used in combination with a custom authorization policy and a custom principal.</span></span>  
  
 <span data-ttu-id="0e3a8-108">Kullanma hakkında daha fazla bilgi için <xref:System.Security.Permissions.PrincipalPermissionAttribute> bkz. [nasıl yapılır: erişimi, PrincipalPermissionAttribute sınıfı ile kısıtlama](../how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span><span class="sxs-lookup"><span data-stu-id="0e3a8-108">For more information about using the <xref:System.Security.Permissions.PrincipalPermissionAttribute>, see [How to: Restrict Access with the PrincipalPermissionAttribute Class](../how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e3a8-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="0e3a8-109">Example</span></span>  

 [!code-csharp[PrincipalPermissionMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/principalpermissionmode/cs/source.cs#8)]
 [!code-vb[PrincipalPermissionMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/principalpermissionmode/vb/source.vb#8)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0e3a8-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="0e3a8-110">Compiling the Code</span></span>  

 <span data-ttu-id="0e3a8-111">Kodu derlemek için aşağıdaki ad alanlarına başvurular gereklidir:</span><span class="sxs-lookup"><span data-stu-id="0e3a8-111">References to the following namespaces are needed to compile the code:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0e3a8-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e3a8-112">See also</span></span>

- <xref:System.ServiceModel.Description.PrincipalPermissionMode>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- [<span data-ttu-id="0e3a8-113">Nasıl yapılır: ASP.NET Rol Sağlayıcısını Bir Hizmetle Kullanma</span><span class="sxs-lookup"><span data-stu-id="0e3a8-113">How to: Use the ASP.NET Role Provider with a Service</span></span>](../feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [<span data-ttu-id="0e3a8-114">Nasıl yapılır: PrincipalPermissionAttribute Sınıfı ile Erişimi Kısıtlama</span><span class="sxs-lookup"><span data-stu-id="0e3a8-114">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../how-to-restrict-access-with-the-principalpermissionattribute-class.md)
