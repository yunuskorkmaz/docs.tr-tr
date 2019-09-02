---
title: Tehlikeli İzinler ve İlke Yönetimi
ms.date: 03/30/2017
helpviewer_keywords:
- permissions [.NET Framework], policy administration
- security [.NET Framework], dangerous permissions
- code security, dangerous permissions
- secure coding, dangerous permissions
- permissions [.NET Framework], dangerous
ms.assetid: 1929e854-23a0-4bb1-94be-e8aa3b609e32
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ffe4f3e000c80610d5a105dddef90f9cfd51f0dc
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205591"
---
# <a name="dangerous-permissions-and-policy-administration"></a><span data-ttu-id="2a5db-102">Tehlikeli İzinler ve İlke Yönetimi</span><span class="sxs-lookup"><span data-stu-id="2a5db-102">Dangerous Permissions and Policy Administration</span></span>
<span data-ttu-id="2a5db-103">.NET Framework izin sağladığı korumalı işlemlerden bazıları güvenlik sisteminin atlalanmasına izin verebilir.</span><span class="sxs-lookup"><span data-stu-id="2a5db-103">Several of the protected operations for which the .NET Framework provides permissions can potentially allow the security system to be circumvented.</span></span> <span data-ttu-id="2a5db-104">Bu tehlikeli izinler yalnızca güvenilir koda ve yalnızca gerekli şekilde verilmelidir.</span><span class="sxs-lookup"><span data-stu-id="2a5db-104">These dangerous permissions should be given only to trustworthy code, and then only as necessary.</span></span> <span data-ttu-id="2a5db-105">Bu izinler verildiğinde, genellikle kötü amaçlı koda karşı savunma yoktur.</span><span class="sxs-lookup"><span data-stu-id="2a5db-105">There is usually no defense against malicious code if it is granted these permissions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2a5db-106">.NET Framework 4 ' te, .NET Framework güvenlik modelinde ve terminolojisinde önemli değişiklikler yapıldı.</span><span class="sxs-lookup"><span data-stu-id="2a5db-106">In the .NET Framework 4, there have been important changes to the .NET Framework security model and terminology.</span></span> <span data-ttu-id="2a5db-107">Bu değişiklikler hakkında daha fazla bilgi için bkz. [güvenlik değişiklikleri](../security/security-changes.md).</span><span class="sxs-lookup"><span data-stu-id="2a5db-107">For more information about these changes, see [Security Changes](../security/security-changes.md).</span></span>  
  
 <span data-ttu-id="2a5db-108">Tehlikeli izinler aşağıdaki tabloda açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="2a5db-108">The dangerous permissions are explained in the following table.</span></span>  
  
|<span data-ttu-id="2a5db-109">İzin</span><span class="sxs-lookup"><span data-stu-id="2a5db-109">Permission</span></span>|<span data-ttu-id="2a5db-110">Olası risk</span><span class="sxs-lookup"><span data-stu-id="2a5db-110">Potential risk</span></span>|  
|----------------|--------------------|  
|<xref:System.Security.Permissions.SecurityPermission>||  
|<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>|<span data-ttu-id="2a5db-111">Yönetilen kodun, genellikle tehlikeli olan yönetilmeyen koda çağrı yapmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="2a5db-111">Allows managed code to call into unmanaged code, which is often dangerous.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SkipVerification>|<span data-ttu-id="2a5db-112">Doğrulama olmadan kod herhangi bir işlem yapabilir.</span><span class="sxs-lookup"><span data-stu-id="2a5db-112">Without verification, the code can do anything.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence>|<span data-ttu-id="2a5db-113">Geçersiz kılınan bulgu, güvenlik ilkesini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="2a5db-113">Invalidated evidence can fool security policy.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPolicy>|<span data-ttu-id="2a5db-114">Güvenlik ilkesini değiştirme özelliği güvenliği devre dışı bırakabilir.</span><span class="sxs-lookup"><span data-stu-id="2a5db-114">The ability to modify security policy can disable security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter>|<span data-ttu-id="2a5db-115">Serileştirme kullanımı erişilebilirlik mekanizmalarını değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="2a5db-115">The use of serialization can circumvent accessibility mechanisms.</span></span> <span data-ttu-id="2a5db-116">Ayrıntılar için bkz. [güvenlik ve serileştirme](security-and-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="2a5db-116">For details, see [Security and Serialization](security-and-serialization.md).</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPrincipal>|<span data-ttu-id="2a5db-117">Geçerli sorumluyu ayarlama özelliği rol tabanlı güvenliği kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="2a5db-117">The ability to set the current principal can trick role-based security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlThread>|<span data-ttu-id="2a5db-118">İş parçacıkları ile ilişkili güvenlik durumu nedeniyle iş parçacıklarının işlenmesi tehlikelidir.</span><span class="sxs-lookup"><span data-stu-id="2a5db-118">Manipulation of threads is dangerous because of the security state associated with threads.</span></span>|  
|<xref:System.Security.Permissions.ReflectionPermission>||  
|<xref:System.MemberAccessException>|<span data-ttu-id="2a5db-119">, Erişilebilirlik mekanizmalarını erteetmek için özel üyeleri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="2a5db-119">Can use private members to defeat accessibility mechanisms.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2a5db-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a5db-120">See also</span></span>

- [<span data-ttu-id="2a5db-121">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="2a5db-121">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
