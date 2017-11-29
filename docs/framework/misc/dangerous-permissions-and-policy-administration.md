---
title: "Tehlikeli İzinler ve İlke Yönetimi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- permissions [.NET Framework], policy administration
- security [.NET Framework], dangerous permissions
- code security, dangerous permissions
- secure coding, dangerous permissions
- permissions [.NET Framework], dangerous
ms.assetid: 1929e854-23a0-4bb1-94be-e8aa3b609e32
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0c8a01cbae2077838a8eef3f2f673e7d9d646717
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="dangerous-permissions-and-policy-administration"></a><span data-ttu-id="26f42-102">Tehlikeli İzinler ve İlke Yönetimi</span><span class="sxs-lookup"><span data-stu-id="26f42-102">Dangerous Permissions and Policy Administration</span></span>
<span data-ttu-id="26f42-103">.NET Framework izinleri sağlayan korumalı işlemlerinin birkaç olası circumvented bir güvenlik sistemi izin verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="26f42-103">Several of the protected operations for which the .NET Framework provides permissions can potentially allow the security system to be circumvented.</span></span> <span data-ttu-id="26f42-104">Yalnızca güvenilir kod ve ardından yalnızca gerektiğinde bu tehlikeli izinleri verilmelidir.</span><span class="sxs-lookup"><span data-stu-id="26f42-104">These dangerous permissions should be given only to trustworthy code, and then only as necessary.</span></span> <span data-ttu-id="26f42-105">Aynı zamanda bu izinleri verildiğinde genellikle kötü amaçlı kod karşı savunma yoktur yoktur.</span><span class="sxs-lookup"><span data-stu-id="26f42-105">There is usually no defense against malicious code if it is granted these permissions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="26f42-106">İçinde [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], terminolojisi ve .NET Framework güvenlik modelinin önemli değişiklikler olmuştur.</span><span class="sxs-lookup"><span data-stu-id="26f42-106">In the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], there have been important changes to the .NET Framework security model and terminology.</span></span> <span data-ttu-id="26f42-107">Bu değişiklikler hakkında daha fazla bilgi için bkz: [güvenlik değişiklikleri](../../../docs/framework/security/security-changes.md).</span><span class="sxs-lookup"><span data-stu-id="26f42-107">For more information about these changes, see [Security Changes](../../../docs/framework/security/security-changes.md).</span></span>  
  
 <span data-ttu-id="26f42-108">Tehlikeli izinler aşağıdaki tabloda açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="26f42-108">The dangerous permissions are explained in the following table.</span></span>  
  
|<span data-ttu-id="26f42-109">İzin</span><span class="sxs-lookup"><span data-stu-id="26f42-109">Permission</span></span>|<span data-ttu-id="26f42-110">Riski</span><span class="sxs-lookup"><span data-stu-id="26f42-110">Potential risk</span></span>|  
|----------------|--------------------|  
|<xref:System.Security.Permissions.SecurityPermission>||  
|<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>|<span data-ttu-id="26f42-111">Tehlikeli görülür, yönetilmeyen koda çağırmak yönetilen kod sağlar.</span><span class="sxs-lookup"><span data-stu-id="26f42-111">Allows managed code to call into unmanaged code, which is often dangerous.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SkipVerification>|<span data-ttu-id="26f42-112">Doğrulama kod herhangi bir şey yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="26f42-112">Without verification, the code can do anything.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence>|<span data-ttu-id="26f42-113">Geçersiz kılınan kanıt güvenlik ilkesi kandırmaya.</span><span class="sxs-lookup"><span data-stu-id="26f42-113">Invalidated evidence can fool security policy.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPolicy>|<span data-ttu-id="26f42-114">Güvenlik ilkesini değiştirme olanağı güvenlik devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="26f42-114">The ability to modify security policy can disable security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter>|<span data-ttu-id="26f42-115">Seri hale getirme kullanımını erişilebilirlik mekanizmaları atlayabilir.</span><span class="sxs-lookup"><span data-stu-id="26f42-115">The use of serialization can circumvent accessibility mechanisms.</span></span> <span data-ttu-id="26f42-116">Ayrıntılar için bkz [güvenlik ve Serileştirme](../../../docs/framework/misc/security-and-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="26f42-116">For details, see [Security and Serialization](../../../docs/framework/misc/security-and-serialization.md).</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPrincipal>|<span data-ttu-id="26f42-117">Geçerli sorumlu ayarlamanıza olanak rol tabanlı güvenlik neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="26f42-117">The ability to set the current principal can trick role-based security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlThread>|<span data-ttu-id="26f42-118">İş parçacığı işleme iş parçacıkları ile ilişkili güvenlik durumu nedeniyle tehlikeli.</span><span class="sxs-lookup"><span data-stu-id="26f42-118">Manipulation of threads is dangerous because of the security state associated with threads.</span></span>|  
|<xref:System.Security.Permissions.ReflectionPermission>||  
|<xref:System.MemberAccessException>|<span data-ttu-id="26f42-119">Özel üyelerin erişilebilirlik mekanizmaları üstesinden gelmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="26f42-119">Can use private members to defeat accessibility mechanisms.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="26f42-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="26f42-120">See Also</span></span>  
 [<span data-ttu-id="26f42-121">Güvenli kodlama yönergeleri</span><span class="sxs-lookup"><span data-stu-id="26f42-121">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
