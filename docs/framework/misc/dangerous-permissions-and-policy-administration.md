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
ms.openlocfilehash: 15d28ff7d11b5d15ce44d9ab1f56548256850ff8
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645754"
---
# <a name="dangerous-permissions-and-policy-administration"></a><span data-ttu-id="6900f-102">Tehlikeli İzinler ve İlke Yönetimi</span><span class="sxs-lookup"><span data-stu-id="6900f-102">Dangerous Permissions and Policy Administration</span></span>
<span data-ttu-id="6900f-103">.NET Framework'ün izin verdiği korumalı işlemlerden bazıları, güvenlik sisteminin atlatılmasına izin verebilir.</span><span class="sxs-lookup"><span data-stu-id="6900f-103">Several of the protected operations for which the .NET Framework provides permissions can potentially allow the security system to be circumvented.</span></span> <span data-ttu-id="6900f-104">Bu tehlikeli izinler yalnızca güvenilir koda ve daha sonra yalnızca gerektiği gibi verilmelidir.</span><span class="sxs-lookup"><span data-stu-id="6900f-104">These dangerous permissions should be given only to trustworthy code, and then only as necessary.</span></span> <span data-ttu-id="6900f-105">Bu izinler verilirse genellikle kötü amaçlı koda karşı savunma yoktur.</span><span class="sxs-lookup"><span data-stu-id="6900f-105">There is usually no defense against malicious code if it is granted these permissions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6900f-106">.NET Framework 4'te .NET Framework güvenlik modeli nde ve terminolojisinde önemli değişiklikler olmuştur.</span><span class="sxs-lookup"><span data-stu-id="6900f-106">In the .NET Framework 4, there have been important changes to the .NET Framework security model and terminology.</span></span> <span data-ttu-id="6900f-107">Bu değişiklikler hakkında daha fazla bilgi için [Güvenlik Değişiklikleri'ne](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes)bakın.</span><span class="sxs-lookup"><span data-stu-id="6900f-107">For more information about these changes, see [Security Changes](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).</span></span>  
  
 <span data-ttu-id="6900f-108">Tehlikeli izinler aşağıdaki tabloda açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="6900f-108">The dangerous permissions are explained in the following table.</span></span>  
  
|<span data-ttu-id="6900f-109">İzin</span><span class="sxs-lookup"><span data-stu-id="6900f-109">Permission</span></span>|<span data-ttu-id="6900f-110">Potansiyel risk</span><span class="sxs-lookup"><span data-stu-id="6900f-110">Potential risk</span></span>|  
|----------------|--------------------|  
|<xref:System.Security.Permissions.SecurityPermission>||  
|<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>|<span data-ttu-id="6900f-111">Yönetilen kodun genellikle tehlikeli olan yönetilmeyen koda çağrı lmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="6900f-111">Allows managed code to call into unmanaged code, which is often dangerous.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SkipVerification>|<span data-ttu-id="6900f-112">Doğrulama olmadan, kod her şeyi yapabilir.</span><span class="sxs-lookup"><span data-stu-id="6900f-112">Without verification, the code can do anything.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence>|<span data-ttu-id="6900f-113">Geçersiz kılınan kanıtlar güvenlik politikasını kandırabilir.</span><span class="sxs-lookup"><span data-stu-id="6900f-113">Invalidated evidence can fool security policy.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPolicy>|<span data-ttu-id="6900f-114">Güvenlik ilkesini değiştirme özelliği güvenliği devre dışı kılabilir.</span><span class="sxs-lookup"><span data-stu-id="6900f-114">The ability to modify security policy can disable security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter>|<span data-ttu-id="6900f-115">Serileştirme kullanımı erişilebilirlik mekanizmaları atlatmak olabilir.</span><span class="sxs-lookup"><span data-stu-id="6900f-115">The use of serialization can circumvent accessibility mechanisms.</span></span> <span data-ttu-id="6900f-116">Ayrıntılar için [Güvenlik ve Serileştirme'ye](security-and-serialization.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="6900f-116">For details, see [Security and Serialization](security-and-serialization.md).</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPrincipal>|<span data-ttu-id="6900f-117">Geçerli asıllığı ayarlama yeteneği rol tabanlı güvenliği kandırabilir.</span><span class="sxs-lookup"><span data-stu-id="6900f-117">The ability to set the current principal can trick role-based security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlThread>|<span data-ttu-id="6900f-118">İş parçacıklarının manipülasyonu, iş parçacıklarıyla ilişkili güvenlik durumu nedeniyle tehlikelidir.</span><span class="sxs-lookup"><span data-stu-id="6900f-118">Manipulation of threads is dangerous because of the security state associated with threads.</span></span>|  
|<xref:System.Security.Permissions.ReflectionPermission>||  
|<xref:System.MemberAccessException>|<span data-ttu-id="6900f-119">Erişilebilirlik mekanizmalarını yenmek için özel üyeler kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="6900f-119">Can use private members to defeat accessibility mechanisms.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6900f-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6900f-120">See also</span></span>

- [<span data-ttu-id="6900f-121">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="6900f-121">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
