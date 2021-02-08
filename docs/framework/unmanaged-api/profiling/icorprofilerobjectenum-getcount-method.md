---
description: ': ICorProfilerObjectEnum:: GetCount yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: b1bedfca913a099f88780807021497d15f75fcd8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798946"
---
# <a name="icorprofilerobjectenumgetcount-method"></a><span data-ttu-id="01587-103">ICorProfilerObjectEnum::GetCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="01587-103">ICorProfilerObjectEnum::GetCount Method</span></span>

<span data-ttu-id="01587-104">Koleksiyondaki dondurulmuş nesnelerin toplam sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="01587-104">Gets the total number of frozen objects in the collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01587-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="01587-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01587-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="01587-106">Parameters</span></span>  

 `pcelt`  
 <span data-ttu-id="01587-107">dışı Koleksiyondaki dondurulmuş nesne sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="01587-107">[out] A pointer to the number of frozen objects in the collection.</span></span>  
  
 <span data-ttu-id="01587-108">Bu yöntem, .NET Framework sürüm 3,5 hizmet paketi 1 (SP1) ve sonraki sürümlerde her zaman sıfır döndürür.</span><span class="sxs-lookup"><span data-stu-id="01587-108">This method will always return zero in the .NET Framework version 3.5 Service Pack 1 (SP1) and later versions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01587-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="01587-109">Requirements</span></span>  

 <span data-ttu-id="01587-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01587-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01587-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="01587-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="01587-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="01587-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01587-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01587-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01587-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01587-114">See also</span></span>

- [<span data-ttu-id="01587-115">ICorProfilerObjectEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="01587-115">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
