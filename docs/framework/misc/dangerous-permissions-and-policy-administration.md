---
title: Tehlikeli İzinler ve İlke Yönetimi
description: Bkz. .NET 'teki çeşitli tehlikeli izinlerin bağlantıları. Bu izinler yalnızca güvenilir koda ve yalnızca gerekli olduğunda verilmelidir.
ms.date: 03/30/2017
helpviewer_keywords:
- permissions [.NET Framework], policy administration
- security [.NET Framework], dangerous permissions
- code security, dangerous permissions
- secure coding, dangerous permissions
- permissions [.NET Framework], dangerous
ms.assetid: 1929e854-23a0-4bb1-94be-e8aa3b609e32
ms.openlocfilehash: ba3d47dc445e4b368f57d59d735fc331f5d6de81
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281621"
---
# <a name="dangerous-permissions-and-policy-administration"></a><span data-ttu-id="ec64e-104">Tehlikeli İzinler ve İlke Yönetimi</span><span class="sxs-lookup"><span data-stu-id="ec64e-104">Dangerous Permissions and Policy Administration</span></span>
<span data-ttu-id="ec64e-105">.NET Framework izin sağladığı korumalı işlemlerden bazıları güvenlik sisteminin atlalanmasına izin verebilir.</span><span class="sxs-lookup"><span data-stu-id="ec64e-105">Several of the protected operations for which the .NET Framework provides permissions can potentially allow the security system to be circumvented.</span></span> <span data-ttu-id="ec64e-106">Bu tehlikeli izinler yalnızca güvenilir koda ve yalnızca gerekli şekilde verilmelidir.</span><span class="sxs-lookup"><span data-stu-id="ec64e-106">These dangerous permissions should be given only to trustworthy code, and then only as necessary.</span></span> <span data-ttu-id="ec64e-107">Bu izinler verildiğinde, genellikle kötü amaçlı koda karşı savunma yoktur.</span><span class="sxs-lookup"><span data-stu-id="ec64e-107">There is usually no defense against malicious code if it is granted these permissions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ec64e-108">.NET Framework 4 ' te, .NET Framework güvenlik modelinde ve terminolojisinde önemli değişiklikler yapıldı.</span><span class="sxs-lookup"><span data-stu-id="ec64e-108">In the .NET Framework 4, there have been important changes to the .NET Framework security model and terminology.</span></span> <span data-ttu-id="ec64e-109">Bu değişiklikler hakkında daha fazla bilgi için bkz. [güvenlik değişiklikleri](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).</span><span class="sxs-lookup"><span data-stu-id="ec64e-109">For more information about these changes, see [Security Changes](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).</span></span>  
  
 <span data-ttu-id="ec64e-110">Tehlikeli izinler aşağıdaki tabloda açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="ec64e-110">The dangerous permissions are explained in the following table.</span></span>  
  
|<span data-ttu-id="ec64e-111">İzin</span><span class="sxs-lookup"><span data-stu-id="ec64e-111">Permission</span></span>|<span data-ttu-id="ec64e-112">Olası risk</span><span class="sxs-lookup"><span data-stu-id="ec64e-112">Potential risk</span></span>|  
|----------------|--------------------|  
|<xref:System.Security.Permissions.SecurityPermission>||  
|<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>|<span data-ttu-id="ec64e-113">Yönetilen kodun, genellikle tehlikeli olan yönetilmeyen koda çağrı yapmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="ec64e-113">Allows managed code to call into unmanaged code, which is often dangerous.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SkipVerification>|<span data-ttu-id="ec64e-114">Doğrulama olmadan kod herhangi bir işlem yapabilir.</span><span class="sxs-lookup"><span data-stu-id="ec64e-114">Without verification, the code can do anything.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence>|<span data-ttu-id="ec64e-115">Geçersiz kılınan bulgu, güvenlik ilkesini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="ec64e-115">Invalidated evidence can fool security policy.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPolicy>|<span data-ttu-id="ec64e-116">Güvenlik ilkesini değiştirme özelliği güvenliği devre dışı bırakabilir.</span><span class="sxs-lookup"><span data-stu-id="ec64e-116">The ability to modify security policy can disable security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter>|<span data-ttu-id="ec64e-117">Serileştirme kullanımı erişilebilirlik mekanizmalarını değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="ec64e-117">The use of serialization can circumvent accessibility mechanisms.</span></span> <span data-ttu-id="ec64e-118">Ayrıntılar için bkz. [güvenlik ve serileştirme](security-and-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="ec64e-118">For details, see [Security and Serialization](security-and-serialization.md).</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPrincipal>|<span data-ttu-id="ec64e-119">Geçerli sorumluyu ayarlama özelliği rol tabanlı güvenliği kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="ec64e-119">The ability to set the current principal can trick role-based security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlThread>|<span data-ttu-id="ec64e-120">İş parçacıkları ile ilişkili güvenlik durumu nedeniyle iş parçacıklarının işlenmesi tehlikelidir.</span><span class="sxs-lookup"><span data-stu-id="ec64e-120">Manipulation of threads is dangerous because of the security state associated with threads.</span></span>|  
|<xref:System.Security.Permissions.ReflectionPermission>||  
|<xref:System.MemberAccessException>|<span data-ttu-id="ec64e-121">, Erişilebilirlik mekanizmalarını erteetmek için özel üyeleri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="ec64e-121">Can use private members to defeat accessibility mechanisms.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ec64e-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec64e-122">See also</span></span>

- [<span data-ttu-id="ec64e-123">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="ec64e-123">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
