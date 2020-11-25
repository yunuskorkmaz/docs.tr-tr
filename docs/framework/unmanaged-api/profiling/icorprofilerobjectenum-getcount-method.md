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
ms.openlocfilehash: a0777797870a707c0d0f00bc0b4c986448118231
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702400"
---
# <a name="icorprofilerobjectenumgetcount-method"></a><span data-ttu-id="fe5f3-102">ICorProfilerObjectEnum::GetCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe5f3-102">ICorProfilerObjectEnum::GetCount Method</span></span>

<span data-ttu-id="fe5f3-103">Koleksiyondaki dondurulmuş nesnelerin toplam sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="fe5f3-103">Gets the total number of frozen objects in the collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe5f3-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="fe5f3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe5f3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fe5f3-105">Parameters</span></span>  

 `pcelt`  
 <span data-ttu-id="fe5f3-106">dışı Koleksiyondaki dondurulmuş nesne sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fe5f3-106">[out] A pointer to the number of frozen objects in the collection.</span></span>  
  
 <span data-ttu-id="fe5f3-107">Bu yöntem, .NET Framework sürüm 3,5 hizmet paketi 1 (SP1) ve sonraki sürümlerde her zaman sıfır döndürür.</span><span class="sxs-lookup"><span data-stu-id="fe5f3-107">This method will always return zero in the .NET Framework version 3.5 Service Pack 1 (SP1) and later versions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe5f3-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fe5f3-108">Requirements</span></span>  

 <span data-ttu-id="fe5f3-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe5f3-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe5f3-110">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="fe5f3-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fe5f3-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="fe5f3-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe5f3-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe5f3-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe5f3-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe5f3-113">See also</span></span>

- [<span data-ttu-id="fe5f3-114">ICorProfilerObjectEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fe5f3-114">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
