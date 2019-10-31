---
title: ICLRDataEnumMemoryRegionsCallback Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegionsCallback
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegionsCallback
helpviewer_keywords:
- ICLRDataEnumMemoryRegionsCallback interface [.NET Framework debugging]
ms.assetid: 3f1af8b0-8478-48e0-a7ec-3e90e0b97649
topic_type:
- apiref
ms.openlocfilehash: cf46133095d1345ffbe0356d3ab486c11ae6dbd6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122906"
---
# <a name="iclrdataenummemoryregionscallback-interface"></a><span data-ttu-id="8c199-102">ICLRDataEnumMemoryRegionsCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c199-102">ICLRDataEnumMemoryRegionsCallback Interface</span></span>
<span data-ttu-id="8c199-103">Hata ayıklayıcıya raporlamak için [ıclrdataenummemoryregion:: EnumMemoryRegion](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) için bir geri çağırma yöntemi sağlar, belirtilen bellek bölgesini numaralandırma girişiminin sonucu.</span><span class="sxs-lookup"><span data-stu-id="8c199-103">Provides a callback method for [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8c199-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8c199-104">Methods</span></span>  
  
|<span data-ttu-id="8c199-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8c199-105">Method</span></span>|<span data-ttu-id="8c199-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8c199-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8c199-107">EnumMemoryRegion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8c199-107">EnumMemoryRegion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-enummemoryregion-method.md)|<span data-ttu-id="8c199-108">Hata ayıklayıcıya, belirtilen bellek bölgesini numaralandırma girişiminin sonucunu raporlamak için `ICLRDataEnumMemoryRegions::EnumMemoryRegions` tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="8c199-108">Called by `ICLRDataEnumMemoryRegions::EnumMemoryRegions` to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8c199-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8c199-109">Requirements</span></span>  
 <span data-ttu-id="8c199-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c199-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c199-111">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="8c199-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="8c199-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8c199-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c199-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c199-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c199-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8c199-114">See also</span></span>

- [<span data-ttu-id="8c199-115">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8c199-115">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
