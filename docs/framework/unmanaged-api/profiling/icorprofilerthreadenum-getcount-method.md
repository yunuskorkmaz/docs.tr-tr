---
description: ': ICorProfilerThreadEnum:: GetCount metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 5219dfc71b79be82f769ac7c8230beaf62c6f33e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646432"
---
# <a name="icorprofilerthreadenumgetcount-method"></a><span data-ttu-id="d5ca6-103">ICorProfilerThreadEnum::GetCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d5ca6-103">ICorProfilerThreadEnum::GetCount Method</span></span>

<span data-ttu-id="d5ca6-104">Uygulama tarafından kullanılan iş parçacıklarının sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="d5ca6-104">Gets the number of threads that are used by the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5ca6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d5ca6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (    [out] ULONG * pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5ca6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d5ca6-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="d5ca6-107">dışı Uygulama tarafından kullanılan iş parçacıklarının sayısı.</span><span class="sxs-lookup"><span data-stu-id="d5ca6-107">[out] The number of threads used by the application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5ca6-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d5ca6-108">Requirements</span></span>  

 <span data-ttu-id="d5ca6-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5ca6-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5ca6-110">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d5ca6-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d5ca6-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d5ca6-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5ca6-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5ca6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5ca6-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5ca6-113">See also</span></span>

- [<span data-ttu-id="d5ca6-114">ICorProfilerThreadEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d5ca6-114">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="d5ca6-115">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d5ca6-115">Profiling Interfaces</span></span>](profiling-interfaces.md)
