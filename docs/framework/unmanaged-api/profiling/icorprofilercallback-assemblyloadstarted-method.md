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
ms.openlocfilehash: a96a2a0d6e4bc48a46850aeaadd17c2669419cef
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59219362"
---
# <a name="icorprofilercallbackassemblyloadstarted-method"></a><span data-ttu-id="0aafc-102">ICorProfilerCallback::AssemblyLoadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0aafc-102">ICorProfilerCallback::AssemblyLoadStarted Method</span></span>
<span data-ttu-id="0aafc-103">Profil Oluşturucu, bir derlemenin yüklendiği bildirir.</span><span class="sxs-lookup"><span data-stu-id="0aafc-103">Notifies the profiler that an assembly is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0aafc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0aafc-104">Syntax</span></span>  
  
```  
HRESULT AssemblyLoadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0aafc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0aafc-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="0aafc-106">[in] Yüklenmekte bütünleştirilmiş kodu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0aafc-106">[in] Identifies the assembly that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0aafc-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0aafc-107">Remarks</span></span>  
 <span data-ttu-id="0aafc-108">Değerini `assemblyId` kadar bir bilgi isteği için geçerli değil [Icorprofilercallback::assemblyloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md) yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="0aafc-108">The value of `assemblyId` is not valid for an information request until the [ICorProfilerCallback::AssemblyLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0aafc-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0aafc-109">Requirements</span></span>  
 <span data-ttu-id="0aafc-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0aafc-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0aafc-111">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0aafc-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0aafc-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0aafc-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="0aafc-113">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="0aafc-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0aafc-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0aafc-114">See also</span></span>

- [<span data-ttu-id="0aafc-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0aafc-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
