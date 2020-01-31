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
ms.openlocfilehash: c8313b7c97eb5d94424259dc91459f62e13368fb
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785601"
---
# <a name="iclrdataenummemoryregionscallbackenummemoryregion-method"></a><span data-ttu-id="5c62a-102">ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c62a-102">ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion Method</span></span>
<span data-ttu-id="5c62a-103">Hata ayıklayıcıya raporlamak için [ıclrdataenummemoryregion:: EnumMemoryRegion](iclrdataenummemoryregions-enummemoryregions-method.md) tarafından çağırılır, belirtilen bellek bölgesini numaralandırma girişimi sonucu.</span><span class="sxs-lookup"><span data-stu-id="5c62a-103">Called by [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c62a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5c62a-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemoryRegion (  
    [in] CLRDATA_ADDRESS  address,  
    [in] ULONG32          size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c62a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5c62a-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="5c62a-106">'ndaki Numaralandırılacak bellek bölgesinin başlangıç adresi.</span><span class="sxs-lookup"><span data-stu-id="5c62a-106">[in] The starting address of the memory region that was to be enumerated.</span></span>  
  
 `size`  
 <span data-ttu-id="5c62a-107">'ndaki Bellek bölgesinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="5c62a-107">[in] The size, in bytes, of the memory region.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c62a-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5c62a-108">Remarks</span></span>  
 <span data-ttu-id="5c62a-109">`ICLRDataEnumMemoryRegions::EnumMemoryRegions` yöntemi, her bir bellek bölgesini numaralandırma denemesinden sonra bu geri arama yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="5c62a-109">The `ICLRDataEnumMemoryRegions::EnumMemoryRegions` method will call this callback method after each attempt to enumerate a memory region.</span></span> <span data-ttu-id="5c62a-110">Bu yöntem hata belirten bir HRESULT döndürürse bile sabit listesi devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="5c62a-110">The enumeration will continue even if this method returns an HRESULT indicating failure.</span></span>  
  
 <span data-ttu-id="5c62a-111">Bu geri çağırma tarafından bildirilen bölgeler, yinelemeler veya çakışan bölgeler olabilir.</span><span class="sxs-lookup"><span data-stu-id="5c62a-111">Regions reported by this callback may be duplicates or overlapping regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c62a-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5c62a-112">Requirements</span></span>  
 <span data-ttu-id="5c62a-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c62a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c62a-114">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="5c62a-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="5c62a-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5c62a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c62a-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c62a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c62a-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c62a-117">See also</span></span>

- [<span data-ttu-id="5c62a-118">ICLRDataEnumMemoryRegionsCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5c62a-118">ICLRDataEnumMemoryRegionsCallback Interface</span></span>](iclrdataenummemoryregionscallback-interface.md)
