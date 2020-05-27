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
ms.openlocfilehash: b4c521489f38360d45c2cf8ff3780e057299f0b4
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008956"
---
# <a name="corunmanagedcallingconvention-enumeration"></a><span data-ttu-id="1c55c-102">CorUnmanagedCallingConvention Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="1c55c-102">CorUnmanagedCallingConvention Enumeration</span></span>
<span data-ttu-id="1c55c-103">Yönetilmeyen kod için çağrı kurallarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1c55c-103">Specifies the calling conventions for unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c55c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1c55c-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="1c55c-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="1c55c-105">Members</span></span>  
  
|<span data-ttu-id="1c55c-106">Üye</span><span class="sxs-lookup"><span data-stu-id="1c55c-106">Member</span></span>|<span data-ttu-id="1c55c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1c55c-107">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_C`|<span data-ttu-id="1c55c-108">C dili çağırma kuralı.</span><span class="sxs-lookup"><span data-stu-id="1c55c-108">The C language calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL`|<span data-ttu-id="1c55c-109">Standart çağırma kuralı.</span><span class="sxs-lookup"><span data-stu-id="1c55c-109">The standard calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL`|<span data-ttu-id="1c55c-110">"This" çağırma kuralı.</span><span class="sxs-lookup"><span data-stu-id="1c55c-110">The "this" calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL`|<span data-ttu-id="1c55c-111">"Hızlı" çağırma kuralı.</span><span class="sxs-lookup"><span data-stu-id="1c55c-111">The "fast" calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_C`|<span data-ttu-id="1c55c-112">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="1c55c-112">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_STDCALL`|<span data-ttu-id="1c55c-113">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="1c55c-113">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_THISCALL`|<span data-ttu-id="1c55c-114">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="1c55c-114">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FASTCALL`|<span data-ttu-id="1c55c-115">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="1c55c-115">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c55c-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1c55c-116">Remarks</span></span>  
 <span data-ttu-id="1c55c-117">CLR, .NET Framework sürüm 1,0 ' de "hızlı" çağırma kuralını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="1c55c-117">The CLR does not support the "fast" calling convention in the .NET Framework version 1.0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c55c-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1c55c-118">Requirements</span></span>  
 <span data-ttu-id="1c55c-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c55c-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c55c-120">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="1c55c-120">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="1c55c-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c55c-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c55c-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c55c-122">See also</span></span>

- [<span data-ttu-id="1c55c-123">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="1c55c-123">Metadata Enumerations</span></span>](metadata-enumerations.md)
