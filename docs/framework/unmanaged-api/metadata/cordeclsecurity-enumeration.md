---
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5409d1b89ba3e50c4ae17ed5aa6bf063cf6c93cb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62046039"
---
# <a name="cordeclsecurity-enumeration"></a><span data-ttu-id="d36dd-102">CorDeclSecurity Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="d36dd-102">CorDeclSecurity Enumeration</span></span>
<span data-ttu-id="d36dd-103">Bildirime dayalı güvenlik kullanarak gerçekleştirilebilir güvenlik eylemleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="d36dd-103">Specifies the security actions that can be performed using declarative security.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d36dd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d36dd-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="d36dd-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="d36dd-105">Members</span></span>  
  
|<span data-ttu-id="d36dd-106">Üye</span><span class="sxs-lookup"><span data-stu-id="d36dd-106">Member</span></span>|<span data-ttu-id="d36dd-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d36dd-107">Description</span></span>|  
|------------|-----------------|  
|`dclActionMask`|<span data-ttu-id="d36dd-108">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="d36dd-108">Reserved.</span></span>|  
|`dclActionNil`|<span data-ttu-id="d36dd-109">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="d36dd-109">Reserved.</span></span>|  
|`dclRequest`|<span data-ttu-id="d36dd-110">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="d36dd-110">Reserved.</span></span>|  
|`dclDemand`|<span data-ttu-id="d36dd-111">Çağrı yığınında daha yüksek tüm çağıranlar geçerli bir izin nesnesi tarafından belirtilen izin verilen gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d36dd-111">All callers higher in the call stack are required to have been granted the permission specified by the current permission object.</span></span>|  
|`dclAssert`|<span data-ttu-id="d36dd-112">Çağıranlar yığınında daha yüksek bir kaynağa erişim izni verilmemiş bile, çağırma kodunun geçerli izin nesnesi tarafından tanımlanan kaynağa erişebilir</span><span class="sxs-lookup"><span data-stu-id="d36dd-112">The calling code can access the resource identified by the current permission object, even if callers higher in the stack have not been granted permission to access the resource</span></span>|  
|`dclDeny`|<span data-ttu-id="d36dd-113">Erişim izni verilmiş olsa bile geçerli bir izin nesnesi tarafından belirtilen kaynak erişim olanağı arayanlar için reddedildi.</span><span class="sxs-lookup"><span data-stu-id="d36dd-113">The ability to access the resource specified by the current permission object is denied to callers, even if they have been granted permission to access it.</span></span>|  
|`dclPermitOnly`|<span data-ttu-id="d36dd-114">Yalnızca bu izin nesnesi tarafından belirtilen kaynak kodu diğer kaynaklara erişim izni verilmiş olsa bile erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="d36dd-114">Only the resources specified by this permission object can be accessed, even if the code has been granted permission to access other resources.</span></span>|  
|`dclLinktimeCheck`|<span data-ttu-id="d36dd-115">Şu anki çağırıcı, belirli bir süre için belirtilen izin verilen gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d36dd-115">The immediate caller is required to have been granted the specified permission for a given period of time.</span></span>|  
|`dclInheritanceCheck`|<span data-ttu-id="d36dd-116">Başka bir sınıf ya da bir yöntemini geçersiz kılma türetilen sınıfın belirtilen izin verilen gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d36dd-116">The derived class inheriting another class or overriding a method is required to have been granted the specified permission.</span></span>|  
|`dclRequestMinimum`|<span data-ttu-id="d36dd-117">Çağıran kodun çalışması için gereken en düşük izinleri isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="d36dd-117">The caller can request for the minimum permissions required for code to run.</span></span> <span data-ttu-id="d36dd-118">Bu eylem, yalnızca derlemenin kapsamında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d36dd-118">This action can only be used within the scope of the assembly.</span></span>|  
|`dclRequestOptional`|<span data-ttu-id="d36dd-119">Çağıran, isteğe bağlı (çalıştırmak için gerekli değildir) için ek izinler isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="d36dd-119">The caller can request for additional permissions that are optional (not required to run).</span></span> <span data-ttu-id="d36dd-120">Bu istek özel olarak istenen tüm izinlerin dolaylı olarak reddeder.</span><span class="sxs-lookup"><span data-stu-id="d36dd-120">This request implicitly refuses all other permissions not specifically requested.</span></span> <span data-ttu-id="d36dd-121">Bu eylem, yalnızca derlemenin kapsamında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d36dd-121">This action can only be used within the scope of the assembly.</span></span>|  
|`dclRequestRefuse`|<span data-ttu-id="d36dd-122">Çağıranın isteği yanlış izinleri verilmez.</span><span class="sxs-lookup"><span data-stu-id="d36dd-122">The caller's request for permissions that might be misused will not be granted.</span></span> <span data-ttu-id="d36dd-123">Bu eylem, yalnızca derlemenin kapsamında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d36dd-123">This action can only be used within the scope of the assembly.</span></span>|  
|`dclPrejitGrant`|<span data-ttu-id="d36dd-124">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="d36dd-124">Reserved.</span></span>|  
|`dclPrejitDenied`|<span data-ttu-id="d36dd-125">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="d36dd-125">Reserved.</span></span>|  
|`dclNonCasDemand`|<span data-ttu-id="d36dd-126">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="d36dd-126">Reserved.</span></span>|  
|`dclNonCasLinkDemand`|<span data-ttu-id="d36dd-127">Şu anki çağırıcı belirtilen izin verilen gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d36dd-127">The immediate caller is required to have been granted the specified permission.</span></span>|  
|`dclNonCasInheritance`|<span data-ttu-id="d36dd-128">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="d36dd-128">Reserved.</span></span>|  
|`dclLinkDemandChoice`|<span data-ttu-id="d36dd-129">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="d36dd-129">Reserved.</span></span>|  
|`dclInheritanceDemandChoice`|<span data-ttu-id="d36dd-130">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="d36dd-130">Reserved.</span></span>|  
|`dclDemandChoice`|<span data-ttu-id="d36dd-131">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="d36dd-131">Reserved.</span></span>|  
|`dclMaximumValue`|<span data-ttu-id="d36dd-132">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="d36dd-132">Reserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d36dd-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d36dd-133">Requirements</span></span>  
 <span data-ttu-id="d36dd-134">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d36dd-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d36dd-135">**Üst bilgi:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="d36dd-135">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="d36dd-136">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d36dd-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d36dd-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d36dd-137">See also</span></span>

- [<span data-ttu-id="d36dd-138">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="d36dd-138">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
