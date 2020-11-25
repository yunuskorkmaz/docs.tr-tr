---
title: ICorProfilerInfo4::EnumThreads Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.EnumThreads
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::EnumThreads
helpviewer_keywords:
- ICorProfilerInfo4::EnumThreads method [.NET Framework profiling]
- EnumThreads method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: bca7a5b4-c207-4894-918c-0733926296dd
topic_type:
- apiref
ms.openlocfilehash: df0e66c8563404d7de4f1e11f41483f2f61f519c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721562"
---
# <a name="icorprofilerinfo4enumthreads-method"></a><span data-ttu-id="ce866-102">ICorProfilerInfo4::EnumThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ce866-102">ICorProfilerInfo4::EnumThreads Method</span></span>

<span data-ttu-id="ce866-103">Profili oluşturulan işlemdeki tüm yönetilen iş parçacıklarının koleksiyonunu sırayla yinelemek için yöntemler sağlayan bir Numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="ce866-103">Returns an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce866-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ce866-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumThreads([out]  
            ICorProfilerThreadEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce866-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ce866-105">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="ce866-106">dışı [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) arabirimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ce866-106">[out] A pointer to an [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce866-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ce866-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce866-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ce866-108">Requirements</span></span>  

 <span data-ttu-id="ce866-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce866-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce866-110">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ce866-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ce866-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ce866-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce866-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce866-112">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce866-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce866-113">See also</span></span>

- [<span data-ttu-id="ce866-114">ICorProfilerThreadEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ce866-114">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="ce866-115">ICorProfilerInfo4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ce866-115">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="ce866-116">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ce866-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="ce866-117">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ce866-117">Profiling</span></span>](index.md)
