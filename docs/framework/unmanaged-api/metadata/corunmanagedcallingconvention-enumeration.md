---
description: 'Daha fazla bilgi edinin: CorUnmanagedCallingConvention numaralandırması'
title: CorUnmanagedCallingConvention Numaralandırması
ms.date: 03/30/2017
api_name:
- CorUnmanagedCallingConvention
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorUnmanagedCallingConvention
helpviewer_keywords:
- CorUnmanagedCallingConvention enumeration [.NET Framework metadata]
ms.assetid: 83058790-160b-4703-a5eb-74b66acbdfa9
topic_type:
- apiref
ms.openlocfilehash: a4b5c70b7dcb4750d641540662941ed3cc08c94b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707299"
---
# <a name="corunmanagedcallingconvention-enumeration"></a><span data-ttu-id="42297-103">CorUnmanagedCallingConvention Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="42297-103">CorUnmanagedCallingConvention Enumeration</span></span>

<span data-ttu-id="42297-104">Yönetilmeyen kod için çağrı kurallarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="42297-104">Specifies the calling conventions for unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42297-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="42297-105">Syntax</span></span>  
  
```cpp  
typedef enum CorUnmanagedCallingConvention {  
  
    IMAGE_CEE_UNMANAGED_CALLCONV_C         = 0x1,  
    IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL   = 0x2,  
    IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL  = 0x3,  
    IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL  = 0x4,  
  
    IMAGE_CEE_CS_CALLCONV_C                = 0x1,  
    IMAGE_CEE_CS_CALLCONV_STDCALL          = 0x2,  
    IMAGE_CEE_CS_CALLCONV_THISCALL         = 0x3,  
    IMAGE_CEE_CS_CALLCONV_FASTCALL         = 0x4  
  
} CorUnmanagedCallingConvention;  
```  
  
## <a name="members"></a><span data-ttu-id="42297-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="42297-106">Members</span></span>  
  
|<span data-ttu-id="42297-107">Üye</span><span class="sxs-lookup"><span data-stu-id="42297-107">Member</span></span>|<span data-ttu-id="42297-108">Description</span><span class="sxs-lookup"><span data-stu-id="42297-108">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_C`|<span data-ttu-id="42297-109">C dili çağırma kuralı.</span><span class="sxs-lookup"><span data-stu-id="42297-109">The C language calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL`|<span data-ttu-id="42297-110">Standart çağırma kuralı.</span><span class="sxs-lookup"><span data-stu-id="42297-110">The standard calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL`|<span data-ttu-id="42297-111">"This" çağırma kuralı.</span><span class="sxs-lookup"><span data-stu-id="42297-111">The "this" calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL`|<span data-ttu-id="42297-112">"Hızlı" çağırma kuralı.</span><span class="sxs-lookup"><span data-stu-id="42297-112">The "fast" calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_C`|<span data-ttu-id="42297-113">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="42297-113">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_STDCALL`|<span data-ttu-id="42297-114">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="42297-114">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_THISCALL`|<span data-ttu-id="42297-115">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="42297-115">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FASTCALL`|<span data-ttu-id="42297-116">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="42297-116">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42297-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="42297-117">Remarks</span></span>  

 <span data-ttu-id="42297-118">CLR, .NET Framework sürüm 1,0 ' de "hızlı" çağırma kuralını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="42297-118">The CLR does not support the "fast" calling convention in the .NET Framework version 1.0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42297-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="42297-119">Requirements</span></span>  

 <span data-ttu-id="42297-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42297-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42297-121">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="42297-121">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="42297-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42297-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42297-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="42297-123">See also</span></span>

- [<span data-ttu-id="42297-124">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="42297-124">Metadata Enumerations</span></span>](metadata-enumerations.md)
