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
ms.openlocfilehash: 0a0af0c86bc44a4968119e1afd2a84e17e941601
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405505"
---
# <a name="iclrdataenummemoryregionscallback-interface"></a><span data-ttu-id="97ac1-102">ICLRDataEnumMemoryRegionsCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="97ac1-102">ICLRDataEnumMemoryRegionsCallback Interface</span></span>
<span data-ttu-id="97ac1-103">Bir geri arama yöntemi sağlar [Iclrdataenummemoryregions::enummemoryregions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) hata ayıklayıcısı için belirtilen bir bölge bellek numaralandırılamıyor girişiminde sonucunu bildirmek için.</span><span class="sxs-lookup"><span data-stu-id="97ac1-103">Provides a callback method for [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="97ac1-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="97ac1-104">Methods</span></span>  
  
|<span data-ttu-id="97ac1-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="97ac1-105">Method</span></span>|<span data-ttu-id="97ac1-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="97ac1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="97ac1-107">EnumMemoryRegion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="97ac1-107">EnumMemoryRegion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-enummemoryregion-method.md)|<span data-ttu-id="97ac1-108">Tarafından çağrılır `ICLRDataEnumMemoryRegions::EnumMemoryRegions` hata ayıklayıcısı için belirtilen bir bölge bellek numaralandırılamıyor girişiminde sonucunu bildirmek için.</span><span class="sxs-lookup"><span data-stu-id="97ac1-108">Called by `ICLRDataEnumMemoryRegions::EnumMemoryRegions` to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="97ac1-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="97ac1-109">Requirements</span></span>  
 <span data-ttu-id="97ac1-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97ac1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97ac1-111">**Başlık:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="97ac1-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="97ac1-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="97ac1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97ac1-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97ac1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97ac1-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="97ac1-114">See Also</span></span>  
 [<span data-ttu-id="97ac1-115">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="97ac1-115">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
