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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9206fbde13f457d4b2e2941ee744d645c6df9774
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781992"
---
# <a name="corunmanagedcallingconvention-enumeration"></a><span data-ttu-id="fb27b-102">CorUnmanagedCallingConvention Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="fb27b-102">CorUnmanagedCallingConvention Enumeration</span></span>
<span data-ttu-id="fb27b-103">Yönetilmeyen kod için çağırma kuralları belirtir.</span><span class="sxs-lookup"><span data-stu-id="fb27b-103">Specifies the calling conventions for unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb27b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fb27b-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="fb27b-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="fb27b-105">Members</span></span>  
  
|<span data-ttu-id="fb27b-106">Üye</span><span class="sxs-lookup"><span data-stu-id="fb27b-106">Member</span></span>|<span data-ttu-id="fb27b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fb27b-107">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_C`|<span data-ttu-id="fb27b-108">C dili çağırma kuralı.</span><span class="sxs-lookup"><span data-stu-id="fb27b-108">The C language calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL`|<span data-ttu-id="fb27b-109">Standart çağırma kuralı.</span><span class="sxs-lookup"><span data-stu-id="fb27b-109">The standard calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL`|<span data-ttu-id="fb27b-110">"Bu" çağırma kuralı.</span><span class="sxs-lookup"><span data-stu-id="fb27b-110">The "this" calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL`|<span data-ttu-id="fb27b-111">"Hızlı" çağırma kuralı.</span><span class="sxs-lookup"><span data-stu-id="fb27b-111">The "fast" calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_C`|<span data-ttu-id="fb27b-112">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="fb27b-112">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_STDCALL`|<span data-ttu-id="fb27b-113">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="fb27b-113">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_THISCALL`|<span data-ttu-id="fb27b-114">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="fb27b-114">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FASTCALL`|<span data-ttu-id="fb27b-115">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="fb27b-115">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb27b-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fb27b-116">Remarks</span></span>  
 <span data-ttu-id="fb27b-117">CLR, .NET Framework sürüm 1.0 "Hızlı" çağırma kuralı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="fb27b-117">The CLR does not support the "fast" calling convention in the .NET Framework version 1.0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb27b-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fb27b-118">Requirements</span></span>  
 <span data-ttu-id="fb27b-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb27b-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb27b-120">**Üst bilgi:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="fb27b-120">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="fb27b-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb27b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb27b-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fb27b-122">See also</span></span>

- [<span data-ttu-id="fb27b-123">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="fb27b-123">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
