---
title: ICorProfilerThreadEnum::GetCount Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerThreadEnum.GetCount
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerThreadEnum::GetCount
helpviewer_keywords:
- ICorProfilerThreadEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: d6dbdc4a-6115-455d-a3f3-704a81d3646b
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ae6e5324328eef8d86e0202e30012ffaba45beab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerthreadenumgetcount-method"></a><span data-ttu-id="07474-102">ICorProfilerThreadEnum::GetCount Metodu</span><span class="sxs-lookup"><span data-stu-id="07474-102">ICorProfilerThreadEnum::GetCount Method</span></span>
<span data-ttu-id="07474-103">Uygulama tarafından kullanılan iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="07474-103">Gets the number of threads that are used by the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07474-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="07474-104">Syntax</span></span>  
  
```  
HRESULT GetCount (    [out] ULONG * pcelt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="07474-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="07474-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="07474-106">[out] Uygulama tarafından kullanılan iş parçacıklarının sayısı.</span><span class="sxs-lookup"><span data-stu-id="07474-106">[out] The number of threads used by the application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07474-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="07474-107">Requirements</span></span>  
 <span data-ttu-id="07474-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07474-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07474-109">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="07474-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="07474-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="07474-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07474-111">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07474-111">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07474-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="07474-112">See Also</span></span>  
 [<span data-ttu-id="07474-113">Icorprofilerthreadenum arabirimi</span><span class="sxs-lookup"><span data-stu-id="07474-113">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 [<span data-ttu-id="07474-114">Profil oluşturma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="07474-114">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
