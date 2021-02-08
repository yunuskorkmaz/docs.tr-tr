---
description: ': ICLRDataEnumMemoryRegionsCallback arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 863192844c4d4d8a35d1e73d38adea3a513bc944
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801377"
---
# <a name="iclrdataenummemoryregionscallback-interface"></a><span data-ttu-id="d97da-103">ICLRDataEnumMemoryRegionsCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d97da-103">ICLRDataEnumMemoryRegionsCallback Interface</span></span>

<span data-ttu-id="d97da-104">Hata ayıklayıcıya raporlamak için [ıclrdataenummemoryregion:: EnumMemoryRegion](iclrdataenummemoryregions-enummemoryregions-method.md) için bir geri çağırma yöntemi sağlar, belirtilen bellek bölgesini numaralandırma girişiminin sonucu.</span><span class="sxs-lookup"><span data-stu-id="d97da-104">Provides a callback method for [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d97da-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d97da-105">Methods</span></span>  
  
|<span data-ttu-id="d97da-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d97da-106">Method</span></span>|<span data-ttu-id="d97da-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d97da-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d97da-108">EnumMemoryRegion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d97da-108">EnumMemoryRegion Method</span></span>](iclrdataenummemoryregionscallback-enummemoryregion-method.md)|<span data-ttu-id="d97da-109">`ICLRDataEnumMemoryRegions::EnumMemoryRegions`Hata ayıklayıcıya, belirtilen bellek bölgesini numaralandırma girişiminin sonucunu bildirmek için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="d97da-109">Called by `ICLRDataEnumMemoryRegions::EnumMemoryRegions` to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d97da-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d97da-110">Requirements</span></span>  

 <span data-ttu-id="d97da-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d97da-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d97da-112">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="d97da-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="d97da-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d97da-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d97da-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d97da-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d97da-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d97da-115">See also</span></span>

- [<span data-ttu-id="d97da-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d97da-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
