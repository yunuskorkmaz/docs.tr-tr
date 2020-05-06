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
ms.openlocfilehash: e6cdc924df126e56d2e7c8c9cb8762ee88712fcc
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860693"
---
# <a name="iclrdataenummemoryregionsenummemoryregions-method"></a><span data-ttu-id="a8d48-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a8d48-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions Method</span></span>
<span data-ttu-id="a8d48-103">Belirtilen bellek alanını numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="a8d48-103">Enumerates specified areas of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8d48-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a8d48-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemoryRegions (  
    [in] ICLRDataEnumMemoryRegionsCallback  *callback,  
    [in] ULONG32                            miniDumpFlags,  
    [in] CLRDataEnumMemoryFlags             clrFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8d48-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a8d48-105">Parameters</span></span>  
 `callback`  
 <span data-ttu-id="a8d48-106">'ndaki Bir [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) örneğine, sonucun hata ayıklayıcısını bildirmek üzere numaralandırılmakta olan her bellek bölgesi için bu yöntem tarafından çağrılan bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a8d48-106">[in] A pointer to an [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) instance that is called by this method for each memory region being enumerated to notify the debugger of the result.</span></span>  
  
 <span data-ttu-id="a8d48-107">Geri arama bir hata gösteriyorsa bile, bellek bölümlerinin numaralandırılması devam eder.</span><span class="sxs-lookup"><span data-stu-id="a8d48-107">The enumeration of memory regions continues even if the callback indicates a failure.</span></span>  
  
 `miniDumpFlags`  
 <span data-ttu-id="a8d48-108">'ndaki Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="a8d48-108">[in] Not used.</span></span>  
  
 `clrFlags`  
 <span data-ttu-id="a8d48-109">'ndaki Numaralandırılacak bellek bölgelerini belirten [CLRDataEnumMemoryFlags](clrdataenummemoryflags-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="a8d48-109">[in] A value of the [CLRDataEnumMemoryFlags](clrdataenummemoryflags-enumeration.md) enumeration that specifies the regions of memory to be enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8d48-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a8d48-110">Remarks</span></span>  
 <span data-ttu-id="a8d48-111">Bu yöntem, sonuçları çağırana bildirmek için belirtilen [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) örneğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a8d48-111">This method uses the specified [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) instance to notify the caller of results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8d48-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a8d48-112">Requirements</span></span>  
 <span data-ttu-id="a8d48-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8d48-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8d48-114">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="a8d48-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="a8d48-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a8d48-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8d48-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8d48-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8d48-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a8d48-117">See also</span></span>

- [<span data-ttu-id="a8d48-118">ICLRDataEnumMemoryRegions Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a8d48-118">ICLRDataEnumMemoryRegions Interface</span></span>](iclrdataenummemoryregions-interface.md)
