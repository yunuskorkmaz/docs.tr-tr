---
title: ICLRDataEnumMemoryRegions::EnumMemoryRegions Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegions.EnumMemoryRegions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions
helpviewer_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions method [.NET Framework debugging]
- EnumMemoryRegions method [.NET Framework debugging]
ms.assetid: 22d2e339-f174-40b5-a478-0b744501566f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c9e3aa909c4eb674b166bfd14feb59e35df4cfd
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57488532"
---
# <a name="iclrdataenummemoryregionsenummemoryregions-method"></a><span data-ttu-id="60543-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions Yöntemi</span><span class="sxs-lookup"><span data-stu-id="60543-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions Method</span></span>
<span data-ttu-id="60543-103">Belirtilen bellek alanları numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="60543-103">Enumerates specified areas of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60543-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="60543-104">Syntax</span></span>  
  
```  
HRESULT EnumMemoryRegions (  
    [in] ICLRDataEnumMemoryRegionsCallback  *callback,  
    [in] ULONG32                            miniDumpFlags,  
    [in] CLRDataEnumMemoryFlags             clrFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60543-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="60543-105">Parameters</span></span>  
 `callback`  
 <span data-ttu-id="60543-106">[in] Bir işaretçi bir [Iclrdataenummemoryregionscallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) sonucun hata ayıklayıcı bildirmek için numaralandırılan her bellek bölge için bu yöntem tarafından çağrılan örnek.</span><span class="sxs-lookup"><span data-stu-id="60543-106">[in] A pointer to an [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instance that is called by this method for each memory region being enumerated to notify the debugger of the result.</span></span>  
  
 <span data-ttu-id="60543-107">Bile hata geri çağırma gösterir bellek bölümlerinin listelenmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="60543-107">The enumeration of memory regions continues even if the callback indicates a failure.</span></span>  
  
 `miniDumpFlags`  
 <span data-ttu-id="60543-108">[in] Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="60543-108">[in] Not used.</span></span>  
  
 `clrFlags`  
 <span data-ttu-id="60543-109">[in] Değerini [CLRDataEnumMemoryFlags](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md) sıralanması bellek bölümlerinin belirten sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="60543-109">[in] A value of the [CLRDataEnumMemoryFlags](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md) enumeration that specifies the regions of memory to be enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60543-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="60543-110">Remarks</span></span>  
 <span data-ttu-id="60543-111">Bu yöntemde belirtilen [Iclrdataenummemoryregionscallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) sonuçlarının çağrıyı yapana bunu bildirmesi örneği.</span><span class="sxs-lookup"><span data-stu-id="60543-111">This method uses the specified [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instance to notify the caller of results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60543-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="60543-112">Requirements</span></span>  
 <span data-ttu-id="60543-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60543-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60543-114">**Üst bilgi:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="60543-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="60543-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="60543-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60543-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60543-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60543-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="60543-117">See also</span></span>
- [<span data-ttu-id="60543-118">ICLRDataEnumMemoryRegions Arabirimi</span><span class="sxs-lookup"><span data-stu-id="60543-118">ICLRDataEnumMemoryRegions Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-interface.md)
