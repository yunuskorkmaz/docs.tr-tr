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
ms.openlocfilehash: e4fa0a3745200d39a468292e9520b1aeb0e9f1b2
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860674"
---
# <a name="iclrdataenummemoryregionscallbackenummemoryregion-method"></a><span data-ttu-id="acd9e-102">ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="acd9e-102">ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion Method</span></span>
<span data-ttu-id="acd9e-103">Hata ayıklayıcıya raporlamak için [ıclrdataenummemoryregion:: EnumMemoryRegion](iclrdataenummemoryregions-enummemoryregions-method.md) tarafından çağırılır, belirtilen bellek bölgesini numaralandırma girişimi sonucu.</span><span class="sxs-lookup"><span data-stu-id="acd9e-103">Called by [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acd9e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="acd9e-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemoryRegion (  
    [in] CLRDATA_ADDRESS  address,  
    [in] ULONG32          size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="acd9e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="acd9e-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="acd9e-106">'ndaki Numaralandırılacak bellek bölgesinin başlangıç adresi.</span><span class="sxs-lookup"><span data-stu-id="acd9e-106">[in] The starting address of the memory region that was to be enumerated.</span></span>  
  
 `size`  
 <span data-ttu-id="acd9e-107">'ndaki Bellek bölgesinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="acd9e-107">[in] The size, in bytes, of the memory region.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="acd9e-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="acd9e-108">Remarks</span></span>  
 <span data-ttu-id="acd9e-109">Yöntemi `ICLRDataEnumMemoryRegions::EnumMemoryRegions` , her bir bellek bölgesini numaralandırma denemesinden sonra bu geri çağırma yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="acd9e-109">The `ICLRDataEnumMemoryRegions::EnumMemoryRegions` method will call this callback method after each attempt to enumerate a memory region.</span></span> <span data-ttu-id="acd9e-110">Bu yöntem hata belirten bir HRESULT döndürürse bile sabit listesi devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="acd9e-110">The enumeration will continue even if this method returns an HRESULT indicating failure.</span></span>  
  
 <span data-ttu-id="acd9e-111">Bu geri çağırma tarafından bildirilen bölgeler, yinelemeler veya çakışan bölgeler olabilir.</span><span class="sxs-lookup"><span data-stu-id="acd9e-111">Regions reported by this callback may be duplicates or overlapping regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="acd9e-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="acd9e-112">Requirements</span></span>  
 <span data-ttu-id="acd9e-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="acd9e-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="acd9e-114">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="acd9e-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="acd9e-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="acd9e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="acd9e-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="acd9e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acd9e-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="acd9e-117">See also</span></span>

- [<span data-ttu-id="acd9e-118">ICLRDataEnumMemoryRegionsCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="acd9e-118">ICLRDataEnumMemoryRegionsCallback Interface</span></span>](iclrdataenummemoryregionscallback-interface.md)
