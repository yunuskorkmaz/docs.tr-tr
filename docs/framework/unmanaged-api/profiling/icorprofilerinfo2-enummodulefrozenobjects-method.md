---
description: 'Şu konuda daha fazla bilgi edinin: ICorProfilerInfo2:: EnumModuleFrozenObjects yöntemi'
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
ms.openlocfilehash: b68571544c00c8c234a73404a95433e91f0cfdcf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753217"
---
# <a name="icorprofilerinfo2enummodulefrozenobjects-method"></a><span data-ttu-id="ef646-103">ICorProfilerInfo2::EnumModuleFrozenObjects Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ef646-103">ICorProfilerInfo2::EnumModuleFrozenObjects Method</span></span>

<span data-ttu-id="ef646-104">Belirtilen modüldeki dondurulmuş nesneler üzerinde yinelemeye izin veren bir Numaralandırıcı alır. Bu yöntem artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="ef646-104">Gets an enumerator that allows iteration over the frozen objects in the specified module.This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef646-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ef646-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumModuleFrozenObjects(  
    [in] ModuleID moduleID,  
    [out] ICorProfilerObjectEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef646-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ef646-106">Parameters</span></span>  

 `moduleID`  
 <span data-ttu-id="ef646-107">'ndaki Numaralandırılacak dondurulmuş nesneleri içeren modülün KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="ef646-107">[in] The ID of the module that contains the frozen objects to be enumerated.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="ef646-108">dışı Dondurulmuş nesneleri numaralandırır [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) arabiriminin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ef646-108">[out] A pointer to the address of an [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) interface, which enumerates the frozen objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef646-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ef646-109">Requirements</span></span>  

 <span data-ttu-id="ef646-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef646-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef646-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ef646-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ef646-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ef646-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef646-113">**.NET Framework sürümleri:** 3,5, 3,0 sp1, 3,0, 2,0 SP1, 2,0</span><span class="sxs-lookup"><span data-stu-id="ef646-113">**.NET Framework Versions:** 3.5, 3.0 SP1, 3.0, 2.0 SP1, 2.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef646-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef646-114">See also</span></span>

- [<span data-ttu-id="ef646-115">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ef646-115">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="ef646-116">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ef646-116">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
