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
ms.openlocfilehash: 2ebe7ef37fb072e3688cc4dcfa5ed89832e886e9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122943"
---
# <a name="iclrdataenummemoryregionscallbackenummemoryregion-method"></a><span data-ttu-id="bcdee-102">ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bcdee-102">ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion Method</span></span>
<span data-ttu-id="bcdee-103">Hata ayıklayıcıya raporlamak için [ıclrdataenummemoryregion:: EnumMemoryRegion](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) tarafından çağırılır, belirtilen bellek bölgesini numaralandırma girişimi sonucu.</span><span class="sxs-lookup"><span data-stu-id="bcdee-103">Called by [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcdee-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bcdee-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemoryRegion (  
    [in] CLRDATA_ADDRESS  address,  
    [in] ULONG32          size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bcdee-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bcdee-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="bcdee-106">'ndaki Numaralandırılacak bellek bölgesinin başlangıç adresi.</span><span class="sxs-lookup"><span data-stu-id="bcdee-106">[in] The starting address of the memory region that was to be enumerated.</span></span>  
  
 `size`  
 <span data-ttu-id="bcdee-107">'ndaki Bellek bölgesinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="bcdee-107">[in] The size, in bytes, of the memory region.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bcdee-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bcdee-108">Remarks</span></span>  
 <span data-ttu-id="bcdee-109">`ICLRDataEnumMemoryRegions::EnumMemoryRegions` yöntemi, her bir bellek bölgesini numaralandırma denemesinden sonra bu geri arama yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="bcdee-109">The `ICLRDataEnumMemoryRegions::EnumMemoryRegions` method will call this callback method after each attempt to enumerate a memory region.</span></span> <span data-ttu-id="bcdee-110">Bu yöntem hata belirten bir HRESULT döndürürse bile sabit listesi devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="bcdee-110">The enumeration will continue even if this method returns an HRESULT indicating failure.</span></span>  
  
 <span data-ttu-id="bcdee-111">Bu geri çağırma tarafından bildirilen bölgeler, yinelemeler veya çakışan bölgeler olabilir.</span><span class="sxs-lookup"><span data-stu-id="bcdee-111">Regions reported by this callback may be duplicates or overlapping regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bcdee-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bcdee-112">Requirements</span></span>  
 <span data-ttu-id="bcdee-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bcdee-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bcdee-114">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="bcdee-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="bcdee-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="bcdee-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bcdee-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bcdee-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcdee-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bcdee-117">See also</span></span>

- [<span data-ttu-id="bcdee-118">ICLRDataEnumMemoryRegionsCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bcdee-118">ICLRDataEnumMemoryRegionsCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md)
