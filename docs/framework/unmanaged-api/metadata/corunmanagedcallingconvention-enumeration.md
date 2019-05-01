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
ms.openlocfilehash: ff308a81282a1cc14c35583daf9cbb057149e556
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61905443"
---
# <a name="corunmanagedcallingconvention-enumeration"></a><span data-ttu-id="fa742-102">CorUnmanagedCallingConvention Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="fa742-102">CorUnmanagedCallingConvention Enumeration</span></span>
<span data-ttu-id="fa742-103">Yönetilmeyen kod için çağırma kuralları belirtir.</span><span class="sxs-lookup"><span data-stu-id="fa742-103">Specifies the calling conventions for unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa742-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fa742-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="fa742-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="fa742-105">Members</span></span>  
  
|<span data-ttu-id="fa742-106">Üye</span><span class="sxs-lookup"><span data-stu-id="fa742-106">Member</span></span>|<span data-ttu-id="fa742-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa742-107">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_C`|<span data-ttu-id="fa742-108">C dili çağırma kuralı.</span><span class="sxs-lookup"><span data-stu-id="fa742-108">The C language calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL`|<span data-ttu-id="fa742-109">Standart çağırma kuralı.</span><span class="sxs-lookup"><span data-stu-id="fa742-109">The standard calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL`|<span data-ttu-id="fa742-110">"Bu" çağırma kuralı.</span><span class="sxs-lookup"><span data-stu-id="fa742-110">The "this" calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL`|<span data-ttu-id="fa742-111">"Hızlı" çağırma kuralı.</span><span class="sxs-lookup"><span data-stu-id="fa742-111">The "fast" calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_C`|<span data-ttu-id="fa742-112">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="fa742-112">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_STDCALL`|<span data-ttu-id="fa742-113">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="fa742-113">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_THISCALL`|<span data-ttu-id="fa742-114">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="fa742-114">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FASTCALL`|<span data-ttu-id="fa742-115">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="fa742-115">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa742-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fa742-116">Remarks</span></span>  
 <span data-ttu-id="fa742-117">CLR, .NET Framework sürüm 1.0 "Hızlı" çağırma kuralı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="fa742-117">The CLR does not support the "fast" calling convention in the .NET Framework version 1.0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa742-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fa742-118">Requirements</span></span>  
 <span data-ttu-id="fa742-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa742-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa742-120">**Üst bilgi:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="fa742-120">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="fa742-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa742-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa742-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa742-122">See also</span></span>

- [<span data-ttu-id="fa742-123">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="fa742-123">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
