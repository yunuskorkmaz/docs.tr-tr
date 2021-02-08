---
description: ': Iclrdataenummemoryregion:: EnumMemoryRegion yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 48887defab38d6ac99c718e14646d39166927438
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785737"
---
# <a name="iclrdataenummemoryregionsenummemoryregions-method"></a><span data-ttu-id="d0cce-103">ICLRDataEnumMemoryRegions::EnumMemoryRegions Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d0cce-103">ICLRDataEnumMemoryRegions::EnumMemoryRegions Method</span></span>

<span data-ttu-id="d0cce-104">Belirtilen bellek alanını numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="d0cce-104">Enumerates specified areas of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0cce-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0cce-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemoryRegions (  
    [in] ICLRDataEnumMemoryRegionsCallback  *callback,  
    [in] ULONG32                            miniDumpFlags,  
    [in] CLRDataEnumMemoryFlags             clrFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0cce-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d0cce-106">Parameters</span></span>  

 `callback`  
 <span data-ttu-id="d0cce-107">'ndaki Bir [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) örneğine, sonucun hata ayıklayıcısını bildirmek üzere numaralandırılmakta olan her bellek bölgesi için bu yöntem tarafından çağrılan bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d0cce-107">[in] A pointer to an [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) instance that is called by this method for each memory region being enumerated to notify the debugger of the result.</span></span>  
  
 <span data-ttu-id="d0cce-108">Geri arama bir hata gösteriyorsa bile, bellek bölümlerinin numaralandırılması devam eder.</span><span class="sxs-lookup"><span data-stu-id="d0cce-108">The enumeration of memory regions continues even if the callback indicates a failure.</span></span>  
  
 `miniDumpFlags`  
 <span data-ttu-id="d0cce-109">'ndaki Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="d0cce-109">[in] Not used.</span></span>  
  
 `clrFlags`  
 <span data-ttu-id="d0cce-110">'ndaki Numaralandırılacak bellek bölgelerini belirten [CLRDataEnumMemoryFlags](clrdataenummemoryflags-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="d0cce-110">[in] A value of the [CLRDataEnumMemoryFlags](clrdataenummemoryflags-enumeration.md) enumeration that specifies the regions of memory to be enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0cce-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d0cce-111">Remarks</span></span>  

 <span data-ttu-id="d0cce-112">Bu yöntem, sonuçları çağırana bildirmek için belirtilen [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) örneğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d0cce-112">This method uses the specified [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) instance to notify the caller of results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0cce-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d0cce-113">Requirements</span></span>  

 <span data-ttu-id="d0cce-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0cce-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0cce-115">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="d0cce-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="d0cce-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d0cce-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0cce-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0cce-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0cce-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0cce-118">See also</span></span>

- [<span data-ttu-id="d0cce-119">ICLRDataEnumMemoryRegions Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d0cce-119">ICLRDataEnumMemoryRegions Interface</span></span>](iclrdataenummemoryregions-interface.md)
