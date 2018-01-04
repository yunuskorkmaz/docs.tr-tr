---
title: "ICLRDataEnumMemoryRegions::EnumMemoryRegions Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataEnumMemoryRegions.EnumMemoryRegions
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataEnumMemoryRegions::EnumMemoryRegions
helpviewer_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions method [.NET Framework debugging]
- EnumMemoryRegions method [.NET Framework debugging]
ms.assetid: 22d2e339-f174-40b5-a478-0b744501566f
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1685b1f739519485e5e68928b29a874587e6f9c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdataenummemoryregionsenummemoryregions-method"></a><span data-ttu-id="24bd3-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions Yöntemi</span><span class="sxs-lookup"><span data-stu-id="24bd3-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions Method</span></span>
<span data-ttu-id="24bd3-103">Belirtilen alanları bellek numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="24bd3-103">Enumerates specified areas of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24bd3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="24bd3-104">Syntax</span></span>  
  
```  
HRESULT EnumMemoryRegions (  
    [in] ICLRDataEnumMemoryRegionsCallback  *callback,  
    [in] ULONG32                            miniDumpFlags,  
    [in] CLRDataEnumMemoryFlags             clrFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="24bd3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="24bd3-105">Parameters</span></span>  
 `callback`  
 <span data-ttu-id="24bd3-106">[in] Bir işaretçi bir [Iclrdataenummemoryregionscallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) sonucun hata ayıklayıcı bildirmek için numaralandırılan her bellek bölge için bu yöntem tarafından çağrılan örnek.</span><span class="sxs-lookup"><span data-stu-id="24bd3-106">[in] A pointer to an [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instance that is called by this method for each memory region being enumerated to notify the debugger of the result.</span></span>  
  
 <span data-ttu-id="24bd3-107">Bir hata geri çağırma gösteriyor olsa bile bellek bölümlerinin listesi devam eder.</span><span class="sxs-lookup"><span data-stu-id="24bd3-107">The enumeration of memory regions continues even if the callback indicates a failure.</span></span>  
  
 `miniDumpFlags`  
 <span data-ttu-id="24bd3-108">[in] Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="24bd3-108">[in] Not used.</span></span>  
  
 `clrFlags`  
 <span data-ttu-id="24bd3-109">[in] Değerini [CLRDataEnumMemoryFlags](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md) sıralanması bellek bölümlerinin belirtir numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="24bd3-109">[in] A value of the [CLRDataEnumMemoryFlags](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md) enumeration that specifies the regions of memory to be enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24bd3-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="24bd3-110">Remarks</span></span>  
 <span data-ttu-id="24bd3-111">Bu yöntem belirtilen kullanır [Iclrdataenummemoryregionscallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) sonuçları arayan bildirmek için örneği.</span><span class="sxs-lookup"><span data-stu-id="24bd3-111">This method uses the specified [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instance to notify the caller of results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24bd3-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="24bd3-112">Requirements</span></span>  
 <span data-ttu-id="24bd3-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24bd3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24bd3-114">**Başlık:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="24bd3-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="24bd3-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24bd3-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24bd3-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24bd3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24bd3-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="24bd3-117">See Also</span></span>  
 [<span data-ttu-id="24bd3-118">ICLRDataEnumMemoryRegions Arabirimi</span><span class="sxs-lookup"><span data-stu-id="24bd3-118">ICLRDataEnumMemoryRegions Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-interface.md)
