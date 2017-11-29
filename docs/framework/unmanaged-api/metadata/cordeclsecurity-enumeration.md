---
title: "CorDeclSecurity Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDeclSecurity
api_location: mscoree.dll
api_type: COM
f1_keywords: CorDeclSecurity
helpviewer_keywords: CorDeclSecurity enumeration [.NET Framework metadata]
ms.assetid: 864f1267-d267-4696-8df7-1f83f8444d6f
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e5ba8de0a8db315e5c06586ad2248cfea241653b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="cordeclsecurity-enumeration"></a><span data-ttu-id="855d7-102">CorDeclSecurity Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="855d7-102">CorDeclSecurity Enumeration</span></span>
<span data-ttu-id="855d7-103">Bildirim temelli güvenlik kullanılarak gerçekleştirilebilir güvenlik eylemleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="855d7-103">Specifies the security actions that can be performed using declarative security.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="855d7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="855d7-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="855d7-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="855d7-105">Members</span></span>  
  
|<span data-ttu-id="855d7-106">Üye</span><span class="sxs-lookup"><span data-stu-id="855d7-106">Member</span></span>|<span data-ttu-id="855d7-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="855d7-107">Description</span></span>|  
|------------|-----------------|  
|`dclActionMask`|<span data-ttu-id="855d7-108">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="855d7-108">Reserved.</span></span>|  
|`dclActionNil`|<span data-ttu-id="855d7-109">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="855d7-109">Reserved.</span></span>|  
|`dclRequest`|<span data-ttu-id="855d7-110">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="855d7-110">Reserved.</span></span>|  
|`dclDemand`|<span data-ttu-id="855d7-111">Geçerli izin nesnesi tarafından belirtilen izni verilmiş tüm arayanlar çağrı yığınında yüksek gereklidir.</span><span class="sxs-lookup"><span data-stu-id="855d7-111">All callers higher in the call stack are required to have been granted the permission specified by the current permission object.</span></span>|  
|`dclAssert`|<span data-ttu-id="855d7-112">Arayanlar yığında yüksek kaynağa erişim izni verilmemiş bile çağıran kodu geçerli izin nesnesi tarafından tanımlanan kaynağa erişebilir</span><span class="sxs-lookup"><span data-stu-id="855d7-112">The calling code can access the resource identified by the current permission object, even if callers higher in the stack have not been granted permission to access the resource</span></span>|  
|`dclDeny`|<span data-ttu-id="855d7-113">Erişim izni verilmiş olsa bile geçerli izni nesnesi tarafından belirlenen kaynak erişim olanağı çağıranlar için reddedildi.</span><span class="sxs-lookup"><span data-stu-id="855d7-113">The ability to access the resource specified by the current permission object is denied to callers, even if they have been granted permission to access it.</span></span>|  
|`dclPermitOnly`|<span data-ttu-id="855d7-114">Kod diğer kaynaklara erişim izni verilmiş olsa bile, yalnızca bu izni nesnesi tarafından belirlenen kaynakları erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="855d7-114">Only the resources specified by this permission object can be accessed, even if the code has been granted permission to access other resources.</span></span>|  
|`dclLinktimeCheck`|<span data-ttu-id="855d7-115">Anında arayanlar belirli bir süre için belirtilmiş izni verilmiş olması gereklidir.</span><span class="sxs-lookup"><span data-stu-id="855d7-115">The immediate caller is required to have been granted the specified permission for a given period of time.</span></span>|  
|`dclInheritanceCheck`|<span data-ttu-id="855d7-116">Başka bir sınıf ya da bir yöntemini geçersiz kılma türetilmiş sınıf belirtilen izin verilmiş olması gereklidir.</span><span class="sxs-lookup"><span data-stu-id="855d7-116">The derived class inheriting another class or overriding a method is required to have been granted the specified permission.</span></span>|  
|`dclRequestMinimum`|<span data-ttu-id="855d7-117">Çağıran, kodun çalışması için gerekli minimum izinleri isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="855d7-117">The caller can request for the minimum permissions required for code to run.</span></span> <span data-ttu-id="855d7-118">Bu eylem yalnızca derleme kapsamında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="855d7-118">This action can only be used within the scope of the assembly.</span></span>|  
|`dclRequestOptional`|<span data-ttu-id="855d7-119">Çağıran, isteğe bağlı (çalıştırmak için gerekli değildir) için ek izinler isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="855d7-119">The caller can request for additional permissions that are optional (not required to run).</span></span> <span data-ttu-id="855d7-120">Bu istek, özellikle istenen tüm izinleri örtük olarak reddediyor.</span><span class="sxs-lookup"><span data-stu-id="855d7-120">This request implicitly refuses all other permissions not specifically requested.</span></span> <span data-ttu-id="855d7-121">Bu eylem yalnızca derleme kapsamında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="855d7-121">This action can only be used within the scope of the assembly.</span></span>|  
|`dclRequestRefuse`|<span data-ttu-id="855d7-122">Arayanın istek kötüye kullanımını izinler için izni yok.</span><span class="sxs-lookup"><span data-stu-id="855d7-122">The caller's request for permissions that might be misused will not be granted.</span></span> <span data-ttu-id="855d7-123">Bu eylem yalnızca derleme kapsamında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="855d7-123">This action can only be used within the scope of the assembly.</span></span>|  
|`dclPrejitGrant`|<span data-ttu-id="855d7-124">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="855d7-124">Reserved.</span></span>|  
|`dclPrejitDenied`|<span data-ttu-id="855d7-125">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="855d7-125">Reserved.</span></span>|  
|`dclNonCasDemand`|<span data-ttu-id="855d7-126">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="855d7-126">Reserved.</span></span>|  
|`dclNonCasLinkDemand`|<span data-ttu-id="855d7-127">Anında arayanlar belirtilmiş izni verilmiş olması gereklidir.</span><span class="sxs-lookup"><span data-stu-id="855d7-127">The immediate caller is required to have been granted the specified permission.</span></span>|  
|`dclNonCasInheritance`|<span data-ttu-id="855d7-128">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="855d7-128">Reserved.</span></span>|  
|`dclLinkDemandChoice`|<span data-ttu-id="855d7-129">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="855d7-129">Reserved.</span></span>|  
|`dclInheritanceDemandChoice`|<span data-ttu-id="855d7-130">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="855d7-130">Reserved.</span></span>|  
|`dclDemandChoice`|<span data-ttu-id="855d7-131">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="855d7-131">Reserved.</span></span>|  
|`dclMaximumValue`|<span data-ttu-id="855d7-132">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="855d7-132">Reserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="855d7-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="855d7-133">Requirements</span></span>  
 <span data-ttu-id="855d7-134">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="855d7-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="855d7-135">**Başlık:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="855d7-135">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="855d7-136">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="855d7-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="855d7-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="855d7-137">See Also</span></span>  
 [<span data-ttu-id="855d7-138">Meta veri numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="855d7-138">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
