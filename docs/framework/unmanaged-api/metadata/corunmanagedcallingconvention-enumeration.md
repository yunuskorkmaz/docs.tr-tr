---
title: "CorUnmanagedCallingConvention Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorUnmanagedCallingConvention
api_location: mscoree.dll
api_type: COM
f1_keywords: CorUnmanagedCallingConvention
helpviewer_keywords: CorUnmanagedCallingConvention enumeration [.NET Framework metadata]
ms.assetid: 83058790-160b-4703-a5eb-74b66acbdfa9
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f66cb036de8450d4c1b3431b92487260956d47f0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="corunmanagedcallingconvention-enumeration"></a><span data-ttu-id="233e2-102">CorUnmanagedCallingConvention Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="233e2-102">CorUnmanagedCallingConvention Enumeration</span></span>
<span data-ttu-id="233e2-103">Yönetilmeyen kodu çağırma kurallarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="233e2-103">Specifies the calling conventions for unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="233e2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="233e2-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="233e2-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="233e2-105">Members</span></span>  
  
|<span data-ttu-id="233e2-106">Üye</span><span class="sxs-lookup"><span data-stu-id="233e2-106">Member</span></span>|<span data-ttu-id="233e2-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="233e2-107">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_C`|<span data-ttu-id="233e2-108">C dili çağırma kuralı.</span><span class="sxs-lookup"><span data-stu-id="233e2-108">The C language calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL`|<span data-ttu-id="233e2-109">Standart arama kuralı.</span><span class="sxs-lookup"><span data-stu-id="233e2-109">The standard calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL`|<span data-ttu-id="233e2-110">"Bu" çağırma.</span><span class="sxs-lookup"><span data-stu-id="233e2-110">The "this" calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL`|<span data-ttu-id="233e2-111">"Hızlı" çağırma kuralı.</span><span class="sxs-lookup"><span data-stu-id="233e2-111">The "fast" calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_C`|<span data-ttu-id="233e2-112">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="233e2-112">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_STDCALL`|<span data-ttu-id="233e2-113">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="233e2-113">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_THISCALL`|<span data-ttu-id="233e2-114">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="233e2-114">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FASTCALL`|<span data-ttu-id="233e2-115">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="233e2-115">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="233e2-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="233e2-116">Remarks</span></span>  
 <span data-ttu-id="233e2-117">CLR, .NET Framework sürüm 1.0 "Hızlı" çağırma desteklemez.</span><span class="sxs-lookup"><span data-stu-id="233e2-117">The CLR does not support the "fast" calling convention in the .NET Framework version 1.0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="233e2-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="233e2-118">Requirements</span></span>  
 <span data-ttu-id="233e2-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="233e2-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="233e2-120">**Başlık:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="233e2-120">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="233e2-121">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="233e2-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="233e2-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="233e2-122">See Also</span></span>  
 [<span data-ttu-id="233e2-123">Meta veri numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="233e2-123">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
