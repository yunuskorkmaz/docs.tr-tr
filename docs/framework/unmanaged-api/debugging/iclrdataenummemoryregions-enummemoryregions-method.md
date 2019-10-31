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
ms.openlocfilehash: 693ec07176f80711709cd9b85c6886bea8be74b2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122960"
---
# <a name="iclrdataenummemoryregionsenummemoryregions-method"></a><span data-ttu-id="71462-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions Yöntemi</span><span class="sxs-lookup"><span data-stu-id="71462-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions Method</span></span>
<span data-ttu-id="71462-103">Belirtilen bellek alanını numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="71462-103">Enumerates specified areas of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71462-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="71462-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemoryRegions (  
    [in] ICLRDataEnumMemoryRegionsCallback  *callback,  
    [in] ULONG32                            miniDumpFlags,  
    [in] CLRDataEnumMemoryFlags             clrFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71462-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="71462-105">Parameters</span></span>  
 `callback`  
 <span data-ttu-id="71462-106">'ndaki Bir [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) örneğine, sonucun hata ayıklayıcısını bildirmek üzere numaralandırılmakta olan her bellek bölgesi için bu yöntem tarafından çağrılan bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="71462-106">[in] A pointer to an [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instance that is called by this method for each memory region being enumerated to notify the debugger of the result.</span></span>  
  
 <span data-ttu-id="71462-107">Geri arama bir hata gösteriyorsa bile, bellek bölümlerinin numaralandırılması devam eder.</span><span class="sxs-lookup"><span data-stu-id="71462-107">The enumeration of memory regions continues even if the callback indicates a failure.</span></span>  
  
 `miniDumpFlags`  
 <span data-ttu-id="71462-108">'ndaki Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="71462-108">[in] Not used.</span></span>  
  
 `clrFlags`  
 <span data-ttu-id="71462-109">'ndaki Numaralandırılacak bellek bölgelerini belirten [CLRDataEnumMemoryFlags](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="71462-109">[in] A value of the [CLRDataEnumMemoryFlags](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md) enumeration that specifies the regions of memory to be enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71462-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="71462-110">Remarks</span></span>  
 <span data-ttu-id="71462-111">Bu yöntem, sonuçları çağırana bildirmek için belirtilen [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) örneğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="71462-111">This method uses the specified [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instance to notify the caller of results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71462-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="71462-112">Requirements</span></span>  
 <span data-ttu-id="71462-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71462-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71462-114">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="71462-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="71462-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="71462-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="71462-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71462-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71462-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71462-117">See also</span></span>

- [<span data-ttu-id="71462-118">ICLRDataEnumMemoryRegions Arabirimi</span><span class="sxs-lookup"><span data-stu-id="71462-118">ICLRDataEnumMemoryRegions Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-interface.md)
