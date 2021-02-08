---
description: 'Hakkında daha fazla bilgi edinin: CorDeclSecurity numaralandırması'
title: CorDeclSecurity Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDeclSecurity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorDeclSecurity
helpviewer_keywords:
- CorDeclSecurity enumeration [.NET Framework metadata]
ms.assetid: 864f1267-d267-4696-8df7-1f83f8444d6f
topic_type:
- apiref
ms.openlocfilehash: 4c4b57c09ea8b3ec1b98ff120d72a5920dc5aa4a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784554"
---
# <a name="cordeclsecurity-enumeration"></a><span data-ttu-id="5fd21-103">CorDeclSecurity Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="5fd21-103">CorDeclSecurity Enumeration</span></span>

<span data-ttu-id="5fd21-104">Bildirime dayalı güvenlik kullanılarak gerçekleştirilebilecek güvenlik eylemlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5fd21-104">Specifies the security actions that can be performed using declarative security.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fd21-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="5fd21-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDeclSecurity {  
  
    dclActionMask               =   0x001f,  
    dclActionNil                =   0x0000,  
    dclRequest                  =   0x0001,  
    dclDemand                   =   0x0002,  
    dclAssert                   =   0x0003,  
    dclDeny                     =   0x0004,  
    dclPermitOnly               =   0x0005,  
    dclLinktimeCheck            =   0x0006,  
    dclInheritanceCheck         =   0x0007,  
    dclRequestMinimum           =   0x0008,  
    dclRequestOptional          =   0x0009,  
    dclRequestRefuse            =   0x000a,  
    dclPrejitGrant              =   0x000b,  
    dclPrejitDenied             =   0x000c,  
    dclNonCasDemand             =   0x000d,  
    dclNonCasLinkDemand         =   0x000e,  
    dclNonCasInheritance        =   0x000f,  
    dclLinkDemandChoice         =   0x0010,  
    dclInheritanceDemandChoice  =   0x0011,  
    dclDemandChoice             =   0x0012,  
    dclMaximumValue             =   0x0012  
  
} CorDeclSecurity;  
```  
  
## <a name="members"></a><span data-ttu-id="5fd21-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="5fd21-106">Members</span></span>  
  
|<span data-ttu-id="5fd21-107">Üye</span><span class="sxs-lookup"><span data-stu-id="5fd21-107">Member</span></span>|<span data-ttu-id="5fd21-108">Description</span><span class="sxs-lookup"><span data-stu-id="5fd21-108">Description</span></span>|  
|------------|-----------------|  
|`dclActionMask`|<span data-ttu-id="5fd21-109">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="5fd21-109">Reserved.</span></span>|  
|`dclActionNil`|<span data-ttu-id="5fd21-110">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="5fd21-110">Reserved.</span></span>|  
|`dclRequest`|<span data-ttu-id="5fd21-111">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="5fd21-111">Reserved.</span></span>|  
|`dclDemand`|<span data-ttu-id="5fd21-112">Çağrı yığınında daha yüksek olan tüm arayanlara geçerli izin nesnesi tarafından belirtilen izin verilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="5fd21-112">All callers higher in the call stack are required to have been granted the permission specified by the current permission object.</span></span>|  
|`dclAssert`|<span data-ttu-id="5fd21-113">Çağıran kod, yığında daha yüksek arayanlara kaynağa erişim izni verilmese bile, geçerli izin nesnesi tarafından tanımlanan kaynağa erişebilir</span><span class="sxs-lookup"><span data-stu-id="5fd21-113">The calling code can access the resource identified by the current permission object, even if callers higher in the stack have not been granted permission to access the resource</span></span>|  
|`dclDeny`|<span data-ttu-id="5fd21-114">Geçerli izin nesnesi tarafından belirtilen kaynağa erişme özelliği, bunlara erişim izni verilmiş olsa bile çağıranlara reddedilir.</span><span class="sxs-lookup"><span data-stu-id="5fd21-114">The ability to access the resource specified by the current permission object is denied to callers, even if they have been granted permission to access it.</span></span>|  
|`dclPermitOnly`|<span data-ttu-id="5fd21-115">Koda diğer kaynaklara erişim izni verilse bile, yalnızca bu izin nesnesi tarafından belirtilen kaynaklara erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="5fd21-115">Only the resources specified by this permission object can be accessed, even if the code has been granted permission to access other resources.</span></span>|  
|`dclLinktimeCheck`|<span data-ttu-id="5fd21-116">Hemen çağıranın belirli bir süre için belirtilen izin verilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="5fd21-116">The immediate caller is required to have been granted the specified permission for a given period of time.</span></span>|  
|`dclInheritanceCheck`|<span data-ttu-id="5fd21-117">Başka bir sınıfı devralan veya bir yöntemi geçersiz kılan türetilmiş sınıfın belirtilen izin verilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="5fd21-117">The derived class inheriting another class or overriding a method is required to have been granted the specified permission.</span></span>|  
|`dclRequestMinimum`|<span data-ttu-id="5fd21-118">Çağıran, kodun çalışması için gereken en düşük izinleri isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="5fd21-118">The caller can request for the minimum permissions required for code to run.</span></span> <span data-ttu-id="5fd21-119">Bu eylem yalnızca derlemenin kapsamı içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5fd21-119">This action can only be used within the scope of the assembly.</span></span>|  
|`dclRequestOptional`|<span data-ttu-id="5fd21-120">Çağıran, isteğe bağlı (çalışması için gerekli değildir) ek izinler talep edebilir.</span><span class="sxs-lookup"><span data-stu-id="5fd21-120">The caller can request for additional permissions that are optional (not required to run).</span></span> <span data-ttu-id="5fd21-121">Bu istek özellikle istenen tüm diğer izinleri örtülü olarak reddeder.</span><span class="sxs-lookup"><span data-stu-id="5fd21-121">This request implicitly refuses all other permissions not specifically requested.</span></span> <span data-ttu-id="5fd21-122">Bu eylem yalnızca derlemenin kapsamı içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5fd21-122">This action can only be used within the scope of the assembly.</span></span>|  
|`dclRequestRefuse`|<span data-ttu-id="5fd21-123">Çağıranın, yanlış bir şekilde kötüye olabilecek izin isteği verilmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="5fd21-123">The caller's request for permissions that might be misused will not be granted.</span></span> <span data-ttu-id="5fd21-124">Bu eylem yalnızca derlemenin kapsamı içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5fd21-124">This action can only be used within the scope of the assembly.</span></span>|  
|`dclPrejitGrant`|<span data-ttu-id="5fd21-125">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="5fd21-125">Reserved.</span></span>|  
|`dclPrejitDenied`|<span data-ttu-id="5fd21-126">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="5fd21-126">Reserved.</span></span>|  
|`dclNonCasDemand`|<span data-ttu-id="5fd21-127">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="5fd21-127">Reserved.</span></span>|  
|`dclNonCasLinkDemand`|<span data-ttu-id="5fd21-128">Hemen çağıranın belirtilen izin verilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="5fd21-128">The immediate caller is required to have been granted the specified permission.</span></span>|  
|`dclNonCasInheritance`|<span data-ttu-id="5fd21-129">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="5fd21-129">Reserved.</span></span>|  
|`dclLinkDemandChoice`|<span data-ttu-id="5fd21-130">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="5fd21-130">Reserved.</span></span>|  
|`dclInheritanceDemandChoice`|<span data-ttu-id="5fd21-131">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="5fd21-131">Reserved.</span></span>|  
|`dclDemandChoice`|<span data-ttu-id="5fd21-132">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="5fd21-132">Reserved.</span></span>|  
|`dclMaximumValue`|<span data-ttu-id="5fd21-133">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="5fd21-133">Reserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5fd21-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5fd21-134">Requirements</span></span>  

 <span data-ttu-id="5fd21-135">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5fd21-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fd21-136">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="5fd21-136">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="5fd21-137">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fd21-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fd21-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5fd21-138">See also</span></span>

- [<span data-ttu-id="5fd21-139">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="5fd21-139">Metadata Enumerations</span></span>](metadata-enumerations.md)
