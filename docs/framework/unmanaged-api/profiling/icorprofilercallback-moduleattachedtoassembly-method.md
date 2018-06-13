---
title: ICorProfilerCallback::ModuleAttachedToAssembly Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleAttachedToAssembly
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleAttachedToAssembly
helpviewer_keywords:
- ICorProfilerCallback::ModuleAttachedToAssembly method [.NET Framework profiling]
- ModuleAttachedToAssembly method [.NET Framework profiling]
ms.assetid: b595798a-5d40-4cac-ab4f-911c61d2c5d2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e6b5281e30c48471131fa12e5106f7d0a6826e1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452565"
---
# <a name="icorprofilercallbackmoduleattachedtoassembly-method"></a><span data-ttu-id="69f71-102">ICorProfilerCallback::ModuleAttachedToAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="69f71-102">ICorProfilerCallback::ModuleAttachedToAssembly Method</span></span>
<span data-ttu-id="69f71-103">Profil Oluşturucu bir modül kendi üst derlemeye bağlı olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="69f71-103">Notifies the profiler that a module is being attached to its parent assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69f71-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="69f71-104">Syntax</span></span>  
  
```  
HRESULT ModuleAttachedToAssembly(  
    [in] ModuleID   moduleId,  
    [in] AssemblyID AssemblyId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="69f71-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="69f71-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="69f71-106">[in] İliştirilmekte olan modül kimliği.</span><span class="sxs-lookup"><span data-stu-id="69f71-106">[in] The ID of the module that is being attached.</span></span>  
  
 `AssemblyId`  
 <span data-ttu-id="69f71-107">[in] Modül bağlı olduğu üst derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="69f71-107">[in] The ID of the parent assembly to which the module is attached.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69f71-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="69f71-108">Remarks</span></span>  
 <span data-ttu-id="69f71-109">Bir modülü içeri aktarma adres tablosunu (IAT) bir çağrıyla yüklenebilir `LoadLibrary`, veya bir meta veri başvuru.</span><span class="sxs-lookup"><span data-stu-id="69f71-109">A module can be loaded through an import address table (IAT), through a call to `LoadLibrary`, or through a metadata reference.</span></span> <span data-ttu-id="69f71-110">Sonuç olarak, ortak dil çalışma zamanı (CLR) yükleyicisi, bir modül yaşadığı derleme belirlemek için birden çok kod yolları vardır.</span><span class="sxs-lookup"><span data-stu-id="69f71-110">As a result, the common language runtime (CLR) loader has multiple code paths for determining the assembly in which a module lives.</span></span> <span data-ttu-id="69f71-111">Bu nedenle, olası bundan sonra [Icorprofilercallback::moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) çağrılır modülü hangi derleme bilmez olarak ve üst derleme kimliği alma mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="69f71-111">Therefore, it is possible that after [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) is called, the module does not know what assembly it is in and getting the parent assembly ID is not possible.</span></span> <span data-ttu-id="69f71-112">`ModuleAttachedToAssembly` Modülü kendi üst derleme ve kimliği elde edilebilir kendi üst derleme iliştirildiğinde yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="69f71-112">The `ModuleAttachedToAssembly` method is called when the module is attached to its parent assembly and its parent assembly ID can be obtained.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69f71-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="69f71-113">Requirements</span></span>  
 <span data-ttu-id="69f71-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69f71-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69f71-115">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="69f71-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="69f71-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69f71-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69f71-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69f71-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69f71-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="69f71-118">See Also</span></span>  
 [<span data-ttu-id="69f71-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="69f71-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
