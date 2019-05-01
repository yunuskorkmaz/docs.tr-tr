---
title: ICorProfilerInfo::GetClassFromToken Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetClassFromToken
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetClassFromToken
helpviewer_keywords:
- ICorProfilerInfo::GetClassFromToken method [.NET Framework profiling]
- GetClassFromToken method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 0afc1197-2a5b-424f-8b82-9cb59a7e00db
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 580c554c968819ba4ef2ba52edeb5e754d33ac1b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991906"
---
# <a name="icorprofilerinfogetclassfromtoken-method"></a><span data-ttu-id="beb2e-102">ICorProfilerInfo::GetClassFromToken Metodu</span><span class="sxs-lookup"><span data-stu-id="beb2e-102">ICorProfilerInfo::GetClassFromToken Method</span></span>
<span data-ttu-id="beb2e-103">Meta veri belirteci verilen sınıfı Kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="beb2e-103">Gets the ID of the class, given the metadata token.</span></span> <span data-ttu-id="beb2e-104">Bu yöntem .NET Framework 2.0 sürümünde artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="beb2e-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="beb2e-105">Kullanım [Icorprofilerınfo2::getclassfromtokenandtypeargs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) yerine.</span><span class="sxs-lookup"><span data-stu-id="beb2e-105">Use [ICorProfilerInfo2::GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="beb2e-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="beb2e-106">Syntax</span></span>  
  
```  
HRESULT GetClassFromToken(  
    [in]  ModuleID  moduleId,  
    [in]  mdTypeDef typeDef,  
    [out] ClassID   *pClassId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="beb2e-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="beb2e-107">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="beb2e-108">[in] Sınıfı içeren modül kimliği.</span><span class="sxs-lookup"><span data-stu-id="beb2e-108">[in] The ID of the module that contains the class.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="beb2e-109">[in] Bir `mdTypeDef` sınıfına başvuran meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="beb2e-109">[in] An `mdTypeDef` metadata token that references the class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="beb2e-110">[out] Sınıf kimliği için bir işaretçi</span><span class="sxs-lookup"><span data-stu-id="beb2e-110">[out] A pointer to the class ID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="beb2e-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="beb2e-111">Remarks</span></span>  
 <span data-ttu-id="beb2e-112">Bu yöntem artık kullanılmıyor; Bunun yerine, `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` tüm türleri.</span><span class="sxs-lookup"><span data-stu-id="beb2e-112">This method is obsolete; instead, use `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` for all types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="beb2e-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="beb2e-113">Requirements</span></span>  
 <span data-ttu-id="beb2e-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="beb2e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="beb2e-115">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="beb2e-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="beb2e-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="beb2e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="beb2e-117">**.NET framework sürümleri:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="beb2e-117">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="beb2e-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="beb2e-118">See also</span></span>

- [<span data-ttu-id="beb2e-119">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="beb2e-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
