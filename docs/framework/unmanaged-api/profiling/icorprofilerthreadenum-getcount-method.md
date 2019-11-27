---
title: ICorProfilerThreadEnum::GetCount Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.GetCount
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::GetCount
helpviewer_keywords:
- ICorProfilerThreadEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: d6dbdc4a-6115-455d-a3f3-704a81d3646b
topic_type:
- apiref
ms.openlocfilehash: 695b720119854de4645b2f14dd55811f2465504a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447646"
---
# <a name="icorprofilerthreadenumgetcount-method"></a><span data-ttu-id="76065-102">ICorProfilerThreadEnum::GetCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="76065-102">ICorProfilerThreadEnum::GetCount Method</span></span>
<span data-ttu-id="76065-103">Uygulama tarafından kullanılan iş parçacıklarının sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="76065-103">Gets the number of threads that are used by the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76065-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="76065-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (    [out] ULONG * pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="76065-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="76065-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="76065-106">dışı Uygulama tarafından kullanılan iş parçacıklarının sayısı.</span><span class="sxs-lookup"><span data-stu-id="76065-106">[out] The number of threads used by the application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76065-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="76065-107">Requirements</span></span>  
 <span data-ttu-id="76065-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76065-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76065-109">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="76065-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="76065-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="76065-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76065-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76065-111">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76065-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="76065-112">See also</span></span>

- [<span data-ttu-id="76065-113">ICorProfilerThreadEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="76065-113">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="76065-114">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="76065-114">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
