---
description: ': ICLRDataEnumMemoryRegionsCallback:: EnumMemoryRegion yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 733911f71898ea7019a0b8d854fb1c1bf61a2474
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801403"
---
# <a name="iclrdataenummemoryregionscallbackenummemoryregion-method"></a><span data-ttu-id="68a53-103">ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="68a53-103">ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion Method</span></span>

<span data-ttu-id="68a53-104">Hata ayıklayıcıya raporlamak için [ıclrdataenummemoryregion:: EnumMemoryRegion](iclrdataenummemoryregions-enummemoryregions-method.md) tarafından çağırılır, belirtilen bellek bölgesini numaralandırma girişimi sonucu.</span><span class="sxs-lookup"><span data-stu-id="68a53-104">Called by [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68a53-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="68a53-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemoryRegion (  
    [in] CLRDATA_ADDRESS  address,  
    [in] ULONG32          size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68a53-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="68a53-106">Parameters</span></span>  

 `address`  
 <span data-ttu-id="68a53-107">'ndaki Numaralandırılacak bellek bölgesinin başlangıç adresi.</span><span class="sxs-lookup"><span data-stu-id="68a53-107">[in] The starting address of the memory region that was to be enumerated.</span></span>  
  
 `size`  
 <span data-ttu-id="68a53-108">'ndaki Bellek bölgesinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="68a53-108">[in] The size, in bytes, of the memory region.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68a53-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="68a53-109">Remarks</span></span>  

 <span data-ttu-id="68a53-110">`ICLRDataEnumMemoryRegions::EnumMemoryRegions`Yöntemi, her bir bellek bölgesini numaralandırma denemesinden sonra bu geri çağırma yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="68a53-110">The `ICLRDataEnumMemoryRegions::EnumMemoryRegions` method will call this callback method after each attempt to enumerate a memory region.</span></span> <span data-ttu-id="68a53-111">Bu yöntem hata belirten bir HRESULT döndürürse bile sabit listesi devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="68a53-111">The enumeration will continue even if this method returns an HRESULT indicating failure.</span></span>  
  
 <span data-ttu-id="68a53-112">Bu geri çağırma tarafından bildirilen bölgeler, yinelemeler veya çakışan bölgeler olabilir.</span><span class="sxs-lookup"><span data-stu-id="68a53-112">Regions reported by this callback may be duplicates or overlapping regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68a53-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="68a53-113">Requirements</span></span>  

 <span data-ttu-id="68a53-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68a53-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68a53-115">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="68a53-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="68a53-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="68a53-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68a53-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68a53-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68a53-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68a53-118">See also</span></span>

- [<span data-ttu-id="68a53-119">ICLRDataEnumMemoryRegionsCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="68a53-119">ICLRDataEnumMemoryRegionsCallback Interface</span></span>](iclrdataenummemoryregionscallback-interface.md)
