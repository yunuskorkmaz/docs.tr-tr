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
ms.openlocfilehash: dad66c8a55982762ede754a4b3cd747b7a91b87d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59225436"
---
# <a name="iclrdataenummemoryregionscallback-interface"></a><span data-ttu-id="017ce-102">ICLRDataEnumMemoryRegionsCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="017ce-102">ICLRDataEnumMemoryRegionsCallback Interface</span></span>
<span data-ttu-id="017ce-103">İçin bir geri arama yöntemi sağlar [Iclrdataenummemoryregions::enummemoryregions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) hata ayıklayıcıya, belirtilen bellek bölgesini numaralandırma girişiminin sonucunu raporlamak için.</span><span class="sxs-lookup"><span data-stu-id="017ce-103">Provides a callback method for [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="017ce-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="017ce-104">Methods</span></span>  
  
|<span data-ttu-id="017ce-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="017ce-105">Method</span></span>|<span data-ttu-id="017ce-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="017ce-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="017ce-107">EnumMemoryRegion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="017ce-107">EnumMemoryRegion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-enummemoryregion-method.md)|<span data-ttu-id="017ce-108">Çağıran `ICLRDataEnumMemoryRegions::EnumMemoryRegions` hata ayıklayıcıya, belirtilen bellek bölgesini numaralandırma girişiminin sonucunu raporlamak için.</span><span class="sxs-lookup"><span data-stu-id="017ce-108">Called by `ICLRDataEnumMemoryRegions::EnumMemoryRegions` to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="017ce-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="017ce-109">Requirements</span></span>  
 <span data-ttu-id="017ce-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="017ce-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="017ce-111">**Üst bilgi:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="017ce-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="017ce-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="017ce-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="017ce-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="017ce-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="017ce-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="017ce-114">See also</span></span>

- [<span data-ttu-id="017ce-115">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="017ce-115">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
