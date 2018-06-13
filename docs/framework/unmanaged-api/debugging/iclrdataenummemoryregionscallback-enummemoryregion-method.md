---
title: ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegionsCallback.EnumMemoryRegion
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion
helpviewer_keywords:
- EnumMemoryRegion method [.NET Framework debugging]
- ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion method [.NET Framework debugging]
ms.assetid: 9bb93fab-57e8-4f9a-9ef3-1794504fa896
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d0ed92cbf5a859b9d5b7b8eddefda3ad34a98f27
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404056"
---
# <a name="iclrdataenummemoryregionscallbackenummemoryregion-method"></a><span data-ttu-id="b47d4-102">ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b47d4-102">ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion Method</span></span>
<span data-ttu-id="b47d4-103">Tarafından çağrılır [Iclrdataenummemoryregions::enummemoryregions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) hata ayıklayıcısı için belirtilen bir bölge bellek numaralandırılamıyor girişiminde sonucunu bildirmek için.</span><span class="sxs-lookup"><span data-stu-id="b47d4-103">Called by [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b47d4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b47d4-104">Syntax</span></span>  
  
```  
HRESULT EnumMemoryRegion (  
    [in] CLRDATA_ADDRESS  address,  
    [in] ULONG32          size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b47d4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b47d4-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="b47d4-106">[in] Numaralandırılacak olan bellek bölge başlangıç adresi.</span><span class="sxs-lookup"><span data-stu-id="b47d4-106">[in] The starting address of the memory region that was to be enumerated.</span></span>  
  
 `size`  
 <span data-ttu-id="b47d4-107">[in] Bellek alanının bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="b47d4-107">[in] The size, in bytes, of the memory region.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b47d4-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b47d4-108">Remarks</span></span>  
 <span data-ttu-id="b47d4-109">`ICLRDataEnumMemoryRegions::EnumMemoryRegions` Yöntemi, bir bellek bölge Numaralandırılacak her girişiminden sonra bu geri çağırma yöntemi çağıracaktır.</span><span class="sxs-lookup"><span data-stu-id="b47d4-109">The `ICLRDataEnumMemoryRegions::EnumMemoryRegions` method will call this callback method after each attempt to enumerate a memory region.</span></span> <span data-ttu-id="b47d4-110">Bu yöntem HRESULT hata olduğunu gösteren döndürürse bile numaralandırma devam eder.</span><span class="sxs-lookup"><span data-stu-id="b47d4-110">The enumeration will continue even if this method returns an HRESULT indicating failure.</span></span>  
  
 <span data-ttu-id="b47d4-111">Bu geri çağırma tarafından bildirilen bölgeleri yinelenen veya örtüşen bölgeler olabilir.</span><span class="sxs-lookup"><span data-stu-id="b47d4-111">Regions reported by this callback may be duplicates or overlapping regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b47d4-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b47d4-112">Requirements</span></span>  
 <span data-ttu-id="b47d4-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b47d4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b47d4-114">**Başlık:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="b47d4-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="b47d4-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b47d4-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b47d4-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b47d4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b47d4-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b47d4-117">See Also</span></span>  
 [<span data-ttu-id="b47d4-118">ICLRDataEnumMemoryRegionsCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b47d4-118">ICLRDataEnumMemoryRegionsCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md)
