---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo4:: EnumThreads yöntemi'
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
ms.openlocfilehash: d597e68b8765e135d5bdb403dbdb161b7acbaa9b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99686940"
---
# <a name="icorprofilerinfo4enumthreads-method"></a><span data-ttu-id="05f96-103">ICorProfilerInfo4::EnumThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="05f96-103">ICorProfilerInfo4::EnumThreads Method</span></span>

<span data-ttu-id="05f96-104">Profili oluşturulan işlemdeki tüm yönetilen iş parçacıklarının koleksiyonunu sırayla yinelemek için yöntemler sağlayan bir Numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="05f96-104">Returns an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05f96-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="05f96-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumThreads([out]  
            ICorProfilerThreadEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05f96-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="05f96-106">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="05f96-107">dışı [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) arabirimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="05f96-107">[out] A pointer to an [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05f96-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="05f96-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05f96-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="05f96-109">Requirements</span></span>  

 <span data-ttu-id="05f96-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05f96-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05f96-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="05f96-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="05f96-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="05f96-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05f96-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05f96-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05f96-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05f96-114">See also</span></span>

- [<span data-ttu-id="05f96-115">ICorProfilerThreadEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="05f96-115">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="05f96-116">ICorProfilerInfo4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="05f96-116">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="05f96-117">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="05f96-117">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="05f96-118">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="05f96-118">Profiling</span></span>](index.md)
