---
title: ICorProfilerInfo2::EnumModuleFrozenObjects Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.EnumModuleFrozenObjects
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::EnumModuleFrozenObjects
helpviewer_keywords:
- EnumModuleFrozenObjects method [.NET Framework profiling]
- ICorProfilerInfo2::EnumModuleFrozenObjects method [.NET Framework profiling]
ms.assetid: 920b6483-7064-4d64-8613-fcc38ccf9b1e
topic_type:
- apiref
ms.openlocfilehash: 27b3037459ac4f995e37515f6e96c28449c80a4f
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862951"
---
# <a name="icorprofilerinfo2enummodulefrozenobjects-method"></a><span data-ttu-id="1f668-102">ICorProfilerInfo2::EnumModuleFrozenObjects Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1f668-102">ICorProfilerInfo2::EnumModuleFrozenObjects Method</span></span>
<span data-ttu-id="1f668-103">Belirtilen modüldeki dondurulmuş nesneler üzerinde yinelemeye izin veren bir Numaralandırıcı alır. Bu yöntem artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="1f668-103">Gets an enumerator that allows iteration over the frozen objects in the specified module.This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f668-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1f668-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumModuleFrozenObjects(  
    [in] ModuleID moduleID,  
    [out] ICorProfilerObjectEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f668-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1f668-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="1f668-106">'ndaki Numaralandırılacak dondurulmuş nesneleri içeren modülün KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="1f668-106">[in] The ID of the module that contains the frozen objects to be enumerated.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="1f668-107">dışı Dondurulmuş nesneleri numaralandırır [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) arabiriminin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1f668-107">[out] A pointer to the address of an [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) interface, which enumerates the frozen objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f668-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1f668-108">Requirements</span></span>  
 <span data-ttu-id="1f668-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f668-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f668-110">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1f668-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1f668-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1f668-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f668-112">**.NET Framework sürümleri:** 3,5, 3,0 sp1, 3,0, 2,0 SP1, 2,0</span><span class="sxs-lookup"><span data-stu-id="1f668-112">**.NET Framework Versions:** 3.5, 3.0 SP1, 3.0, 2.0 SP1, 2.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f668-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f668-113">See also</span></span>

- [<span data-ttu-id="1f668-114">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1f668-114">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="1f668-115">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1f668-115">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
