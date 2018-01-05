---
title: ICorProfilerInfo::GetClassFromToken Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetClassFromToken
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetClassFromToken
helpviewer_keywords:
- ICorProfilerInfo::GetClassFromToken method [.NET Framework profiling]
- GetClassFromToken method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 0afc1197-2a5b-424f-8b82-9cb59a7e00db
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9972a9d97f94a6286adc0906416349f92e6bf7ec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetclassfromtoken-method"></a><span data-ttu-id="21fc4-102">ICorProfilerInfo::GetClassFromToken Metodu</span><span class="sxs-lookup"><span data-stu-id="21fc4-102">ICorProfilerInfo::GetClassFromToken Method</span></span>
<span data-ttu-id="21fc4-103">Meta veri simgesi verilen sınıf Kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="21fc4-103">Gets the ID of the class, given the metadata token.</span></span> <span data-ttu-id="21fc4-104">Bu yöntem .NET Framework 2.0 sürümünde kullanımdan kalkmıştır.</span><span class="sxs-lookup"><span data-stu-id="21fc4-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="21fc4-105">Kullanım [Icorprofilerınfo2::getclassfromtokenandtypeargs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) yerine.</span><span class="sxs-lookup"><span data-stu-id="21fc4-105">Use [ICorProfilerInfo2::GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21fc4-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21fc4-106">Syntax</span></span>  
  
```  
HRESULT GetClassFromToken(  
    [in]  ModuleID  moduleId,  
    [in]  mdTypeDef typeDef,  
    [out] ClassID   *pClassId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="21fc4-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="21fc4-107">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="21fc4-108">[in] Sınıf içeren modülü kimliği.</span><span class="sxs-lookup"><span data-stu-id="21fc4-108">[in] The ID of the module that contains the class.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="21fc4-109">[in] Bir `mdTypeDef` sınıfı başvuran meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="21fc4-109">[in] An `mdTypeDef` metadata token that references the class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="21fc4-110">[out] Sınıf kimliği için bir işaretçi</span><span class="sxs-lookup"><span data-stu-id="21fc4-110">[out] A pointer to the class ID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21fc4-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="21fc4-111">Remarks</span></span>  
 <span data-ttu-id="21fc4-112">Bu yöntem artık kullanılmıyor; Bunun yerine, kullanın `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` tüm türleri.</span><span class="sxs-lookup"><span data-stu-id="21fc4-112">This method is obsolete; instead, use `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` for all types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21fc4-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="21fc4-113">Requirements</span></span>  
 <span data-ttu-id="21fc4-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21fc4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21fc4-115">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="21fc4-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="21fc4-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21fc4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21fc4-117">**.NET framework sürümleri:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="21fc4-117">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21fc4-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="21fc4-118">See Also</span></span>  
 [<span data-ttu-id="21fc4-119">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="21fc4-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
