---
title: ICLRDataEnumMemoryRegionsCallback Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataEnumMemoryRegionsCallback
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataEnumMemoryRegionsCallback
helpviewer_keywords: ICLRDataEnumMemoryRegionsCallback interface [.NET Framework debugging]
ms.assetid: 3f1af8b0-8478-48e0-a7ec-3e90e0b97649
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 40e51bfc176d8be6b008bc4274c0933253d7be3a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdataenummemoryregionscallback-interface"></a><span data-ttu-id="f41f8-102">ICLRDataEnumMemoryRegionsCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f41f8-102">ICLRDataEnumMemoryRegionsCallback Interface</span></span>
<span data-ttu-id="f41f8-103">Bir geri arama yöntemi sağlar [Iclrdataenummemoryregions::enummemoryregions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) hata ayıklayıcısı için belirtilen bir bölge bellek numaralandırılamıyor girişiminde sonucunu bildirmek için.</span><span class="sxs-lookup"><span data-stu-id="f41f8-103">Provides a callback method for [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f41f8-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f41f8-104">Methods</span></span>  
  
|<span data-ttu-id="f41f8-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f41f8-105">Method</span></span>|<span data-ttu-id="f41f8-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f41f8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f41f8-107">EnumMemoryRegion yöntemi</span><span class="sxs-lookup"><span data-stu-id="f41f8-107">EnumMemoryRegion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-enummemoryregion-method.md)|<span data-ttu-id="f41f8-108">Tarafından çağrılır `ICLRDataEnumMemoryRegions::EnumMemoryRegions` hata ayıklayıcısı için belirtilen bir bölge bellek numaralandırılamıyor girişiminde sonucunu bildirmek için.</span><span class="sxs-lookup"><span data-stu-id="f41f8-108">Called by `ICLRDataEnumMemoryRegions::EnumMemoryRegions` to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f41f8-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f41f8-109">Requirements</span></span>  
 <span data-ttu-id="f41f8-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f41f8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f41f8-111">**Başlık:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="f41f8-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="f41f8-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f41f8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f41f8-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f41f8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f41f8-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f41f8-114">See Also</span></span>  
 [<span data-ttu-id="f41f8-115">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f41f8-115">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
