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
ms.openlocfilehash: 386f975ab0bbbe804fda2bd7567acf24f69e77fb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676081"
---
# <a name="iclrdataenummemoryregionsenummemoryregions-method"></a><span data-ttu-id="a509b-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a509b-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions Method</span></span>

<span data-ttu-id="a509b-103">Belirtilen bellek alanını numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="a509b-103">Enumerates specified areas of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a509b-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a509b-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemoryRegions (  
    [in] ICLRDataEnumMemoryRegionsCallback  *callback,  
    [in] ULONG32                            miniDumpFlags,  
    [in] CLRDataEnumMemoryFlags             clrFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a509b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a509b-105">Parameters</span></span>  

 `callback`  
 <span data-ttu-id="a509b-106">'ndaki Bir [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) örneğine, sonucun hata ayıklayıcısını bildirmek üzere numaralandırılmakta olan her bellek bölgesi için bu yöntem tarafından çağrılan bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a509b-106">[in] A pointer to an [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) instance that is called by this method for each memory region being enumerated to notify the debugger of the result.</span></span>  
  
 <span data-ttu-id="a509b-107">Geri arama bir hata gösteriyorsa bile, bellek bölümlerinin numaralandırılması devam eder.</span><span class="sxs-lookup"><span data-stu-id="a509b-107">The enumeration of memory regions continues even if the callback indicates a failure.</span></span>  
  
 `miniDumpFlags`  
 <span data-ttu-id="a509b-108">'ndaki Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="a509b-108">[in] Not used.</span></span>  
  
 `clrFlags`  
 <span data-ttu-id="a509b-109">'ndaki Numaralandırılacak bellek bölgelerini belirten [CLRDataEnumMemoryFlags](clrdataenummemoryflags-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="a509b-109">[in] A value of the [CLRDataEnumMemoryFlags](clrdataenummemoryflags-enumeration.md) enumeration that specifies the regions of memory to be enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a509b-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a509b-110">Remarks</span></span>  

 <span data-ttu-id="a509b-111">Bu yöntem, sonuçları çağırana bildirmek için belirtilen [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) örneğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a509b-111">This method uses the specified [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) instance to notify the caller of results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a509b-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a509b-112">Requirements</span></span>  

 <span data-ttu-id="a509b-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a509b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a509b-114">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="a509b-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="a509b-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a509b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a509b-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a509b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a509b-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a509b-117">See also</span></span>

- [<span data-ttu-id="a509b-118">ICLRDataEnumMemoryRegions Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a509b-118">ICLRDataEnumMemoryRegions Interface</span></span>](iclrdataenummemoryregions-interface.md)
