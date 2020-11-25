---
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
ms.openlocfilehash: 9d35f6b1928d714216b669704ec28e53895f6549
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699072"
---
# <a name="corunmanagedcallingconvention-enumeration"></a><span data-ttu-id="85c6e-102">CorUnmanagedCallingConvention Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="85c6e-102">CorUnmanagedCallingConvention Enumeration</span></span>

<span data-ttu-id="85c6e-103">Yönetilmeyen kod için çağrı kurallarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="85c6e-103">Specifies the calling conventions for unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85c6e-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="85c6e-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="85c6e-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="85c6e-105">Members</span></span>  
  
|<span data-ttu-id="85c6e-106">Üye</span><span class="sxs-lookup"><span data-stu-id="85c6e-106">Member</span></span>|<span data-ttu-id="85c6e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="85c6e-107">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_C`|<span data-ttu-id="85c6e-108">C dili çağırma kuralı.</span><span class="sxs-lookup"><span data-stu-id="85c6e-108">The C language calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL`|<span data-ttu-id="85c6e-109">Standart çağırma kuralı.</span><span class="sxs-lookup"><span data-stu-id="85c6e-109">The standard calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL`|<span data-ttu-id="85c6e-110">"This" çağırma kuralı.</span><span class="sxs-lookup"><span data-stu-id="85c6e-110">The "this" calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL`|<span data-ttu-id="85c6e-111">"Hızlı" çağırma kuralı.</span><span class="sxs-lookup"><span data-stu-id="85c6e-111">The "fast" calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_C`|<span data-ttu-id="85c6e-112">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="85c6e-112">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_STDCALL`|<span data-ttu-id="85c6e-113">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="85c6e-113">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_THISCALL`|<span data-ttu-id="85c6e-114">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="85c6e-114">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FASTCALL`|<span data-ttu-id="85c6e-115">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="85c6e-115">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85c6e-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="85c6e-116">Remarks</span></span>  

 <span data-ttu-id="85c6e-117">CLR, .NET Framework sürüm 1,0 ' de "hızlı" çağırma kuralını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="85c6e-117">The CLR does not support the "fast" calling convention in the .NET Framework version 1.0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85c6e-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="85c6e-118">Requirements</span></span>  

 <span data-ttu-id="85c6e-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85c6e-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85c6e-120">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="85c6e-120">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="85c6e-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85c6e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85c6e-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85c6e-122">See also</span></span>

- [<span data-ttu-id="85c6e-123">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="85c6e-123">Metadata Enumerations</span></span>](metadata-enumerations.md)
