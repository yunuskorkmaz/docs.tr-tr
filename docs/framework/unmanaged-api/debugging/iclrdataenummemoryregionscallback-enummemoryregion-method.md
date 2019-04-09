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
ms.openlocfilehash: 85b1c5455cb2008a352461d6b506e43fcef48d17
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130929"
---
# <a name="iclrdataenummemoryregionscallbackenummemoryregion-method"></a><span data-ttu-id="f942f-102">ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f942f-102">ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion Method</span></span>
<span data-ttu-id="f942f-103">Çağıran [Iclrdataenummemoryregions::enummemoryregions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) hata ayıklayıcıya, belirtilen bellek bölgesini numaralandırma girişiminin sonucunu raporlamak için.</span><span class="sxs-lookup"><span data-stu-id="f942f-103">Called by [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f942f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f942f-104">Syntax</span></span>  
  
```  
HRESULT EnumMemoryRegion (  
    [in] CLRDATA_ADDRESS  address,  
    [in] ULONG32          size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f942f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f942f-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="f942f-106">[in] Numaralandırılacak olan bellek bölgesini başlangıç adresi.</span><span class="sxs-lookup"><span data-stu-id="f942f-106">[in] The starting address of the memory region that was to be enumerated.</span></span>  
  
 `size`  
 <span data-ttu-id="f942f-107">[in] Bellek bölümünün bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="f942f-107">[in] The size, in bytes, of the memory region.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f942f-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f942f-108">Remarks</span></span>  
 <span data-ttu-id="f942f-109">`ICLRDataEnumMemoryRegions::EnumMemoryRegions` Yöntemi bir bellek bölgesini numaralandırma her girişimden sonra bu geri çağırma yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="f942f-109">The `ICLRDataEnumMemoryRegions::EnumMemoryRegions` method will call this callback method after each attempt to enumerate a memory region.</span></span> <span data-ttu-id="f942f-110">Bu yöntem, hata olduğunu gösteren bir HRESULT döndürür bile numaralandırması devam eder.</span><span class="sxs-lookup"><span data-stu-id="f942f-110">The enumeration will continue even if this method returns an HRESULT indicating failure.</span></span>  
  
 <span data-ttu-id="f942f-111">Bu geri çağırma tarafından bildirilen bölgeler, yinelenen veya örtüşen bölgelerde olabilir.</span><span class="sxs-lookup"><span data-stu-id="f942f-111">Regions reported by this callback may be duplicates or overlapping regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f942f-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f942f-112">Requirements</span></span>  
 <span data-ttu-id="f942f-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f942f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f942f-114">**Üst bilgi:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="f942f-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="f942f-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f942f-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="f942f-116">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="f942f-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f942f-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f942f-117">See also</span></span>

- [<span data-ttu-id="f942f-118">ICLRDataEnumMemoryRegionsCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f942f-118">ICLRDataEnumMemoryRegionsCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md)
