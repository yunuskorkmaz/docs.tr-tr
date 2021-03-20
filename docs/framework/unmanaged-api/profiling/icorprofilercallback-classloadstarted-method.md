---
description: ': ICorProfilerCallback:: ClassLoadStarted yöntemi hakkında daha fazla bilgi edinin'
title: ICorProfilerCallback::ClassLoadStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassLoadStarted
helpviewer_keywords:
- ICorProfilerCallback::ClassLoadStarted method [.NET Framework profiling]
- ClassLoadStarted method [.NET Framework profiling]
ms.assetid: 9f728de8-45c2-45a5-ac4a-45660bd36ecf
topic_type:
- apiref
ms.openlocfilehash: 4950f1d806efb304a860fa6fce18f8655bdc0976
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759264"
---
# <a name="icorprofilercallbackclassloadstarted-method"></a><span data-ttu-id="2e0f5-103">ICorProfilerCallback::ClassLoadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2e0f5-103">ICorProfilerCallback::ClassLoadStarted Method</span></span>

<span data-ttu-id="2e0f5-104">Profil oluşturucuyu bir sınıfın yüklenmekte olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="2e0f5-104">Notifies the profiler that a class is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e0f5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2e0f5-105">Syntax</span></span>  
  
```cpp  
HRESULT ClassLoadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e0f5-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2e0f5-106">Parameters</span></span>

<span data-ttu-id="2e0f5-107">`classId` 'ndaki Yüklenmekte olan sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2e0f5-107">`classId` [in] Identifies the class that is being loaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="2e0f5-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2e0f5-108">Remarks</span></span>  

 <span data-ttu-id="2e0f5-109">Değeri, `classId` [ICorProfilerCallback:: ClassLoadFinished](icorprofilercallback-classloadfinished-method.md) yöntemi çağrılana kadar bir bilgi isteği için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="2e0f5-109">The value of `classId` is not valid for an information request until the [ICorProfilerCallback::ClassLoadFinished](icorprofilercallback-classloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e0f5-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2e0f5-110">Requirements</span></span>  

 <span data-ttu-id="2e0f5-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e0f5-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e0f5-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2e0f5-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2e0f5-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2e0f5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e0f5-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e0f5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e0f5-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e0f5-115">See also</span></span>

- [<span data-ttu-id="2e0f5-116">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2e0f5-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
