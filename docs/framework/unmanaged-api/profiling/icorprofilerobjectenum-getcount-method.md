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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8466de39f2f2769fec332290c187ecba396d7d56
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59080936"
---
# <a name="icorprofilerobjectenumgetcount-method"></a><span data-ttu-id="6b7b7-102">ICorProfilerObjectEnum::GetCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6b7b7-102">ICorProfilerObjectEnum::GetCount Method</span></span>
<span data-ttu-id="6b7b7-103">Koleksiyondaki donmuş nesneler toplam sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="6b7b7-103">Gets the total number of frozen objects in the collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b7b7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6b7b7-104">Syntax</span></span>  
  
```  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b7b7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6b7b7-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="6b7b7-106">[out] Donmuş nesneler koleksiyonunda sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6b7b7-106">[out] A pointer to the number of frozen objects in the collection.</span></span>  
  
 <span data-ttu-id="6b7b7-107">Bu yöntem her zaman sıfır .NET Framework sürüm 3.5 döndürür Service Pack 1 (SP1) ve sonraki sürümler.</span><span class="sxs-lookup"><span data-stu-id="6b7b7-107">This method will always return zero in the .NET Framework version 3.5 Service Pack 1 (SP1) and later versions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b7b7-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6b7b7-108">Requirements</span></span>  
 <span data-ttu-id="6b7b7-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b7b7-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b7b7-110">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6b7b7-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6b7b7-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b7b7-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b7b7-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b7b7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b7b7-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b7b7-113">See also</span></span>

- [<span data-ttu-id="6b7b7-114">ICorProfilerObjectEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6b7b7-114">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
