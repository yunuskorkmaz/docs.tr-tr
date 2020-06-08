---
title: ICorProfilerObjectEnum::GetCount Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.GetCount
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::GetCount
helpviewer_keywords:
- ICorProfilerObjectEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: 166b0761-ed80-4ccd-9973-dc20e61bf8fa
topic_type:
- apiref
ms.openlocfilehash: 4c867a9e263f022fc6f8d90a883562e2560ad1b2
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494663"
---
# <a name="icorprofilerobjectenumgetcount-method"></a><span data-ttu-id="21068-102">ICorProfilerObjectEnum::GetCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="21068-102">ICorProfilerObjectEnum::GetCount Method</span></span>
<span data-ttu-id="21068-103">Koleksiyondaki dondurulmuş nesnelerin toplam sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="21068-103">Gets the total number of frozen objects in the collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21068-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="21068-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21068-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="21068-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="21068-106">dışı Koleksiyondaki dondurulmuş nesne sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="21068-106">[out] A pointer to the number of frozen objects in the collection.</span></span>  
  
 <span data-ttu-id="21068-107">Bu yöntem, .NET Framework sürüm 3,5 hizmet paketi 1 (SP1) ve sonraki sürümlerde her zaman sıfır döndürür.</span><span class="sxs-lookup"><span data-stu-id="21068-107">This method will always return zero in the .NET Framework version 3.5 Service Pack 1 (SP1) and later versions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21068-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="21068-108">Requirements</span></span>  
 <span data-ttu-id="21068-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21068-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21068-110">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="21068-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="21068-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="21068-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21068-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21068-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21068-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21068-113">See also</span></span>

- [<span data-ttu-id="21068-114">ICorProfilerObjectEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="21068-114">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
