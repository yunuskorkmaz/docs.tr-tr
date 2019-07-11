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
ms.openlocfilehash: 3345e2e87ba41f750031deed2d15e13dbe4f06c8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769298"
---
# <a name="icorprofilercallbackmoduleattachedtoassembly-method"></a><span data-ttu-id="0c0b4-102">ICorProfilerCallback::ModuleAttachedToAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0c0b4-102">ICorProfilerCallback::ModuleAttachedToAssembly Method</span></span>
<span data-ttu-id="0c0b4-103">Profil Oluşturucu, bir modül, ana derlemeye bağlı olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="0c0b4-103">Notifies the profiler that a module is being attached to its parent assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c0b4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0c0b4-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleAttachedToAssembly(  
    [in] ModuleID   moduleId,  
    [in] AssemblyID AssemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c0b4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0c0b4-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="0c0b4-106">[in] İliştirilmekte olan modül kimliği.</span><span class="sxs-lookup"><span data-stu-id="0c0b4-106">[in] The ID of the module that is being attached.</span></span>  
  
 `AssemblyId`  
 <span data-ttu-id="0c0b4-107">[in] Modül eklendiği ana derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="0c0b4-107">[in] The ID of the parent assembly to which the module is attached.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c0b4-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0c0b4-108">Remarks</span></span>  
 <span data-ttu-id="0c0b4-109">Bir modül, bir içeri aktarma adres tablosunda (IAT) yapılan bir çağrıyla yüklenebilir `LoadLibrary`, isterse bir meta veri başvurusu.</span><span class="sxs-lookup"><span data-stu-id="0c0b4-109">A module can be loaded through an import address table (IAT), through a call to `LoadLibrary`, or through a metadata reference.</span></span> <span data-ttu-id="0c0b4-110">Sonuç olarak, ortak dil çalışma zamanı (CLR) yükleyicisi bir modül içinde bulunduğu derlemenin belirlemek için birden çok kod yolları vardır.</span><span class="sxs-lookup"><span data-stu-id="0c0b4-110">As a result, the common language runtime (CLR) loader has multiple code paths for determining the assembly in which a module lives.</span></span> <span data-ttu-id="0c0b4-111">Bu nedenle, olası bundan sonra [Icorprofilercallback::moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) çağrılır, hangi derleme modülü bilmez olarak ve üst derleme Kimliğini alma mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="0c0b4-111">Therefore, it is possible that after [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) is called, the module does not know what assembly it is in and getting the parent assembly ID is not possible.</span></span> <span data-ttu-id="0c0b4-112">`ModuleAttachedToAssembly` Modülü kendi üst derlemesi ve kendi üst derlemesi kimliği elde edilebilir eklendiğinde yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="0c0b4-112">The `ModuleAttachedToAssembly` method is called when the module is attached to its parent assembly and its parent assembly ID can be obtained.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c0b4-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0c0b4-113">Requirements</span></span>  
 <span data-ttu-id="0c0b4-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c0b4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c0b4-115">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0c0b4-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0c0b4-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0c0b4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c0b4-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c0b4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c0b4-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c0b4-118">See also</span></span>

- [<span data-ttu-id="0c0b4-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0c0b4-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
