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
ms.openlocfilehash: b4b6b7b7b0dbb36724ff5eee2f3f78a3a7422cb7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453339"
---
# <a name="icorprofilerinfogetclassfromtoken-method"></a><span data-ttu-id="a5cb6-102">ICorProfilerInfo::GetClassFromToken Metodu</span><span class="sxs-lookup"><span data-stu-id="a5cb6-102">ICorProfilerInfo::GetClassFromToken Method</span></span>
<span data-ttu-id="a5cb6-103">Meta veri simgesi verilen sınıf Kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="a5cb6-103">Gets the ID of the class, given the metadata token.</span></span> <span data-ttu-id="a5cb6-104">Bu yöntem .NET Framework 2.0 sürümünde kullanımdan kalkmıştır.</span><span class="sxs-lookup"><span data-stu-id="a5cb6-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="a5cb6-105">Kullanım [Icorprofilerınfo2::getclassfromtokenandtypeargs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) yerine.</span><span class="sxs-lookup"><span data-stu-id="a5cb6-105">Use [ICorProfilerInfo2::GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5cb6-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a5cb6-106">Syntax</span></span>  
  
```  
HRESULT GetClassFromToken(  
    [in]  ModuleID  moduleId,  
    [in]  mdTypeDef typeDef,  
    [out] ClassID   *pClassId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a5cb6-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a5cb6-107">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="a5cb6-108">[in] Sınıf içeren modülü kimliği.</span><span class="sxs-lookup"><span data-stu-id="a5cb6-108">[in] The ID of the module that contains the class.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="a5cb6-109">[in] Bir `mdTypeDef` sınıfı başvuran meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="a5cb6-109">[in] An `mdTypeDef` metadata token that references the class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="a5cb6-110">[out] Sınıf kimliği için bir işaretçi</span><span class="sxs-lookup"><span data-stu-id="a5cb6-110">[out] A pointer to the class ID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5cb6-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a5cb6-111">Remarks</span></span>  
 <span data-ttu-id="a5cb6-112">Bu yöntem artık kullanılmıyor; Bunun yerine, kullanın `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` tüm türleri.</span><span class="sxs-lookup"><span data-stu-id="a5cb6-112">This method is obsolete; instead, use `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` for all types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5cb6-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a5cb6-113">Requirements</span></span>  
 <span data-ttu-id="a5cb6-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5cb6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5cb6-115">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a5cb6-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a5cb6-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5cb6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5cb6-117">**.NET framework sürümleri:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="a5cb6-117">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5cb6-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a5cb6-118">See Also</span></span>  
 [<span data-ttu-id="a5cb6-119">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a5cb6-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
