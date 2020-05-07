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
ms.openlocfilehash: ddcb8064dfb9be30c66404a8762a9ca73cd6afe4
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860654"
---
# <a name="iclrdataenummemoryregionscallback-interface"></a><span data-ttu-id="f9651-102">ICLRDataEnumMemoryRegionsCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f9651-102">ICLRDataEnumMemoryRegionsCallback Interface</span></span>
<span data-ttu-id="f9651-103">Hata ayıklayıcıya raporlamak için [ıclrdataenummemoryregion:: EnumMemoryRegion](iclrdataenummemoryregions-enummemoryregions-method.md) için bir geri çağırma yöntemi sağlar, belirtilen bellek bölgesini numaralandırma girişiminin sonucu.</span><span class="sxs-lookup"><span data-stu-id="f9651-103">Provides a callback method for [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f9651-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f9651-104">Methods</span></span>  
  
|<span data-ttu-id="f9651-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f9651-105">Method</span></span>|<span data-ttu-id="f9651-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9651-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f9651-107">EnumMemoryRegion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f9651-107">EnumMemoryRegion Method</span></span>](iclrdataenummemoryregionscallback-enummemoryregion-method.md)|<span data-ttu-id="f9651-108">Hata ayıklayıcıya, belirtilen bellek bölgesini numaralandırma girişiminin sonucunu bildirmek `ICLRDataEnumMemoryRegions::EnumMemoryRegions` için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="f9651-108">Called by `ICLRDataEnumMemoryRegions::EnumMemoryRegions` to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f9651-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f9651-109">Requirements</span></span>  
 <span data-ttu-id="f9651-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9651-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9651-111">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="f9651-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="f9651-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f9651-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9651-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9651-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9651-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9651-114">See also</span></span>

- [<span data-ttu-id="f9651-115">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f9651-115">Debugging Interfaces</span></span>](debugging-interfaces.md)
