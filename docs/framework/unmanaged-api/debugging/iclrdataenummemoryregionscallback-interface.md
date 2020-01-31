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
ms.openlocfilehash: 4e3891996af5945ed95c8c37dddfee5c446db248
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789116"
---
# <a name="iclrdataenummemoryregionscallback-interface"></a><span data-ttu-id="1003c-102">ICLRDataEnumMemoryRegionsCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1003c-102">ICLRDataEnumMemoryRegionsCallback Interface</span></span>
<span data-ttu-id="1003c-103">Hata ayıklayıcıya raporlamak için [ıclrdataenummemoryregion:: EnumMemoryRegion](iclrdataenummemoryregions-enummemoryregions-method.md) için bir geri çağırma yöntemi sağlar, belirtilen bellek bölgesini numaralandırma girişiminin sonucu.</span><span class="sxs-lookup"><span data-stu-id="1003c-103">Provides a callback method for [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1003c-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1003c-104">Methods</span></span>  
  
|<span data-ttu-id="1003c-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1003c-105">Method</span></span>|<span data-ttu-id="1003c-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1003c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1003c-107">EnumMemoryRegion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1003c-107">EnumMemoryRegion Method</span></span>](iclrdataenummemoryregionscallback-enummemoryregion-method.md)|<span data-ttu-id="1003c-108">Hata ayıklayıcıya, belirtilen bellek bölgesini numaralandırma girişiminin sonucunu raporlamak için `ICLRDataEnumMemoryRegions::EnumMemoryRegions` tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="1003c-108">Called by `ICLRDataEnumMemoryRegions::EnumMemoryRegions` to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1003c-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1003c-109">Requirements</span></span>  
 <span data-ttu-id="1003c-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1003c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1003c-111">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="1003c-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="1003c-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1003c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1003c-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1003c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1003c-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1003c-114">See also</span></span>

- [<span data-ttu-id="1003c-115">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1003c-115">Debugging Interfaces</span></span>](debugging-interfaces.md)
