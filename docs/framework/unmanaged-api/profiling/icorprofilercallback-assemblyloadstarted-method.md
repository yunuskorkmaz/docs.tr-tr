---
title: ICorProfilerCallback::AssemblyLoadStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyLoadStarted
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadStarted method [.NET Framework profiling]
- AssemblyLoadStarted method [.NET Framework profiling]
ms.assetid: 67e8209d-a0ca-4118-a6e6-c1ee0abc2221
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4ace66630176149a18a174fad24f782a289b0e9d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763007"
---
# <a name="icorprofilercallbackassemblyloadstarted-method"></a><span data-ttu-id="87e2c-102">ICorProfilerCallback::AssemblyLoadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="87e2c-102">ICorProfilerCallback::AssemblyLoadStarted Method</span></span>
<span data-ttu-id="87e2c-103">Profil Oluşturucu, bir derlemenin yüklendiği bildirir.</span><span class="sxs-lookup"><span data-stu-id="87e2c-103">Notifies the profiler that an assembly is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87e2c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="87e2c-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyLoadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87e2c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="87e2c-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="87e2c-106">[in] Yüklenmekte bütünleştirilmiş kodu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="87e2c-106">[in] Identifies the assembly that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87e2c-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="87e2c-107">Remarks</span></span>  
 <span data-ttu-id="87e2c-108">Değerini `assemblyId` kadar bir bilgi isteği için geçerli değil [Icorprofilercallback::assemblyloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md) yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="87e2c-108">The value of `assemblyId` is not valid for an information request until the [ICorProfilerCallback::AssemblyLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87e2c-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="87e2c-109">Requirements</span></span>  
 <span data-ttu-id="87e2c-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87e2c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87e2c-111">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="87e2c-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="87e2c-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="87e2c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87e2c-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87e2c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87e2c-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87e2c-114">See also</span></span>

- [<span data-ttu-id="87e2c-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="87e2c-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
