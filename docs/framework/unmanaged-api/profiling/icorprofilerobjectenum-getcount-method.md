---
title: ICorProfilerObjectEnum::GetCount Metodu
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
ms.openlocfilehash: a363021700eacea1d4af80ca6371de5c587afda1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54622214"
---
# <a name="icorprofilerobjectenumgetcount-method"></a><span data-ttu-id="2e96c-102">ICorProfilerObjectEnum::GetCount Metodu</span><span class="sxs-lookup"><span data-stu-id="2e96c-102">ICorProfilerObjectEnum::GetCount Method</span></span>
<span data-ttu-id="2e96c-103">Koleksiyondaki donmuş nesneler toplam sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="2e96c-103">Gets the total number of frozen objects in the collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e96c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2e96c-104">Syntax</span></span>  
  
```  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2e96c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2e96c-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="2e96c-106">[out] Donmuş nesneler koleksiyonunda sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2e96c-106">[out] A pointer to the number of frozen objects in the collection.</span></span>  
  
 <span data-ttu-id="2e96c-107">Bu yöntem her zaman sıfır .NET Framework sürüm 3.5 döndürür Service Pack 1 (SP1) ve sonraki sürümler.</span><span class="sxs-lookup"><span data-stu-id="2e96c-107">This method will always return zero in the .NET Framework version 3.5 Service Pack 1 (SP1) and later versions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e96c-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2e96c-108">Requirements</span></span>  
 <span data-ttu-id="2e96c-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e96c-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e96c-110">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2e96c-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2e96c-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2e96c-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e96c-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e96c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e96c-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e96c-113">See also</span></span>
- [<span data-ttu-id="2e96c-114">ICorProfilerObjectEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2e96c-114">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
