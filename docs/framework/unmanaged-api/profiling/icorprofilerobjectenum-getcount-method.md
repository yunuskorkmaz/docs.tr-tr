---
title: ICorProfilerObjectEnum::GetCount Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerObjectEnum.GetCount
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerObjectEnum::GetCount
helpviewer_keywords:
- ICorProfilerObjectEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: 166b0761-ed80-4ccd-9973-dc20e61bf8fa
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0680921a64d8f8bf9cdc5b4137c56dd8dfb7878e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerobjectenumgetcount-method"></a><span data-ttu-id="2121d-102">ICorProfilerObjectEnum::GetCount Metodu</span><span class="sxs-lookup"><span data-stu-id="2121d-102">ICorProfilerObjectEnum::GetCount Method</span></span>
<span data-ttu-id="2121d-103">Koleksiyonda dondurulmuş nesne toplam sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="2121d-103">Gets the total number of frozen objects in the collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2121d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2121d-104">Syntax</span></span>  
  
```  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2121d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2121d-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="2121d-106">[out] Koleksiyondaki dondurulmuş nesne sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2121d-106">[out] A pointer to the number of frozen objects in the collection.</span></span>  
  
 <span data-ttu-id="2121d-107">Bu yöntem her zaman sıfır .NET Framework sürüm 3.5 döndürülecek Service Pack 1 (SP1) ve sonraki sürümler.</span><span class="sxs-lookup"><span data-stu-id="2121d-107">This method will always return zero in the .NET Framework version 3.5 Service Pack 1 (SP1) and later versions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2121d-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2121d-108">Requirements</span></span>  
 <span data-ttu-id="2121d-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2121d-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2121d-110">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2121d-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2121d-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2121d-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2121d-112">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2121d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2121d-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2121d-113">See Also</span></span>  
 [<span data-ttu-id="2121d-114">Icorprofilerobjectenum arabirimi</span><span class="sxs-lookup"><span data-stu-id="2121d-114">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
