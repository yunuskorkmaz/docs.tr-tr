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
ms.openlocfilehash: 4f494919d11e0f979cf1964c08106fbb9b9ed20b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503399"
---
# <a name="icorprofilercallbackmoduleattachedtoassembly-method"></a><span data-ttu-id="eb2f0-102">ICorProfilerCallback::ModuleAttachedToAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eb2f0-102">ICorProfilerCallback::ModuleAttachedToAssembly Method</span></span>
<span data-ttu-id="eb2f0-103">Profil oluşturucuyu bir modülün üst derlemesine iliştirilmekte olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="eb2f0-103">Notifies the profiler that a module is being attached to its parent assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb2f0-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="eb2f0-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleAttachedToAssembly(  
    [in] ModuleID   moduleId,  
    [in] AssemblyID AssemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb2f0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="eb2f0-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="eb2f0-106">'ndaki İliştirilmekte olan modülün KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="eb2f0-106">[in] The ID of the module that is being attached.</span></span>  
  
 `AssemblyId`  
 <span data-ttu-id="eb2f0-107">'ndaki Modülün eklendiği üst derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="eb2f0-107">[in] The ID of the parent assembly to which the module is attached.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb2f0-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eb2f0-108">Remarks</span></span>  
 <span data-ttu-id="eb2f0-109">Bir modül bir içeri aktarma adres tablosu (ıAT) aracılığıyla, öğesine yapılan çağrısıyla `LoadLibrary` veya meta veri başvurusu aracılığıyla yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="eb2f0-109">A module can be loaded through an import address table (IAT), through a call to `LoadLibrary`, or through a metadata reference.</span></span> <span data-ttu-id="eb2f0-110">Sonuç olarak, ortak dil çalışma zamanı (CLR) yükleyicisinin, bir modülün yaşadığı derlemeyi belirlemek için birden çok kod yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="eb2f0-110">As a result, the common language runtime (CLR) loader has multiple code paths for determining the assembly in which a module lives.</span></span> <span data-ttu-id="eb2f0-111">Bu nedenle, [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) çağrıldıktan sonra, modül içinde bulunduğu derlemeyi bilmez ve üst derleme kimliğini elde etmek mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="eb2f0-111">Therefore, it is possible that after [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) is called, the module does not know what assembly it is in and getting the parent assembly ID is not possible.</span></span> <span data-ttu-id="eb2f0-112">`ModuleAttachedToAssembly`Yöntemi, modül üst derlemesine iliştirildiği zaman çağrılır ve üst derleme kimliği elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="eb2f0-112">The `ModuleAttachedToAssembly` method is called when the module is attached to its parent assembly and its parent assembly ID can be obtained.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb2f0-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eb2f0-113">Requirements</span></span>  
 <span data-ttu-id="eb2f0-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb2f0-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb2f0-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="eb2f0-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eb2f0-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="eb2f0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb2f0-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb2f0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb2f0-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb2f0-118">See also</span></span>

- [<span data-ttu-id="eb2f0-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eb2f0-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
