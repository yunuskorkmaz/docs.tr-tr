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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0e7ce243658a8c8a8404ff9079ed1395e56486f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604169"
---
# <a name="iclrdataenummemoryregionscallback-interface"></a><span data-ttu-id="9e607-102">ICLRDataEnumMemoryRegionsCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e607-102">ICLRDataEnumMemoryRegionsCallback Interface</span></span>
<span data-ttu-id="9e607-103">İçin bir geri arama yöntemi sağlar [Iclrdataenummemoryregions::enummemoryregions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) hata ayıklayıcıya, belirtilen bellek bölgesini numaralandırma girişiminin sonucunu raporlamak için.</span><span class="sxs-lookup"><span data-stu-id="9e607-103">Provides a callback method for [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9e607-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9e607-104">Methods</span></span>  
  
|<span data-ttu-id="9e607-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="9e607-105">Method</span></span>|<span data-ttu-id="9e607-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9e607-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9e607-107">EnumMemoryRegion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9e607-107">EnumMemoryRegion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-enummemoryregion-method.md)|<span data-ttu-id="9e607-108">Çağıran `ICLRDataEnumMemoryRegions::EnumMemoryRegions` hata ayıklayıcıya, belirtilen bellek bölgesini numaralandırma girişiminin sonucunu raporlamak için.</span><span class="sxs-lookup"><span data-stu-id="9e607-108">Called by `ICLRDataEnumMemoryRegions::EnumMemoryRegions` to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9e607-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9e607-109">Requirements</span></span>  
 <span data-ttu-id="9e607-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e607-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e607-111">**Üst bilgi:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="9e607-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="9e607-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e607-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e607-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e607-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e607-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e607-114">See also</span></span>
- [<span data-ttu-id="9e607-115">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9e607-115">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
