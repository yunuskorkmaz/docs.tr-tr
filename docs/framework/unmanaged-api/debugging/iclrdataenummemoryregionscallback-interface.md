---
title: ICLRDataEnumMemoryRegionsCallback Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 091f5345461ebe5054e769ae9d051ef2e0737ffb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdataenummemoryregionscallback-interface"></a><span data-ttu-id="bd637-102">ICLRDataEnumMemoryRegionsCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bd637-102">ICLRDataEnumMemoryRegionsCallback Interface</span></span>
<span data-ttu-id="bd637-103">Bir geri arama yöntemi sağlar [Iclrdataenummemoryregions::enummemoryregions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) hata ayıklayıcısı için belirtilen bir bölge bellek numaralandırılamıyor girişiminde sonucunu bildirmek için.</span><span class="sxs-lookup"><span data-stu-id="bd637-103">Provides a callback method for [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bd637-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="bd637-104">Methods</span></span>  
  
|<span data-ttu-id="bd637-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="bd637-105">Method</span></span>|<span data-ttu-id="bd637-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bd637-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bd637-107">EnumMemoryRegion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bd637-107">EnumMemoryRegion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-enummemoryregion-method.md)|<span data-ttu-id="bd637-108">Tarafından çağrılır `ICLRDataEnumMemoryRegions::EnumMemoryRegions` hata ayıklayıcısı için belirtilen bir bölge bellek numaralandırılamıyor girişiminde sonucunu bildirmek için.</span><span class="sxs-lookup"><span data-stu-id="bd637-108">Called by `ICLRDataEnumMemoryRegions::EnumMemoryRegions` to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bd637-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bd637-109">Requirements</span></span>  
 <span data-ttu-id="bd637-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd637-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd637-111">**Başlık:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="bd637-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="bd637-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bd637-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd637-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd637-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd637-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bd637-114">See Also</span></span>  
 [<span data-ttu-id="bd637-115">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="bd637-115">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
