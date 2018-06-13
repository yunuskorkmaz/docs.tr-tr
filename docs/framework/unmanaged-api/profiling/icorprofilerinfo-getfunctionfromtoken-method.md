---
title: ICorProfilerInfo::GetFunctionFromToken Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetFunctionFromToken
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetFunctionFromToken
helpviewer_keywords:
- ICorProfilerInfo::GetFunctionFromToken method [.NET Framework profiling]
- GetFunctionFromToken method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 0eed759f-cce8-405d-88dc-9ee293a38928
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eb894e3f52d28ce419ddda90f9fc0ac0e8dce022
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461948"
---
# <a name="icorprofilerinfogetfunctionfromtoken-method"></a><span data-ttu-id="f9236-102">ICorProfilerInfo::GetFunctionFromToken Metodu</span><span class="sxs-lookup"><span data-stu-id="f9236-102">ICorProfilerInfo::GetFunctionFromToken Method</span></span>
<span data-ttu-id="f9236-103">Bir işlev Kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="f9236-103">Gets the ID of a function.</span></span> <span data-ttu-id="f9236-104">Bu yöntem .NET Framework 2.0 sürümünde kullanımdan kalkmıştır.</span><span class="sxs-lookup"><span data-stu-id="f9236-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="f9236-105">Kullanım [Icorprofilerınfo2::getfunctionfromtokenandtypeargs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="f9236-105">Use the [ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9236-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f9236-106">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromToken(  
    [in]  ModuleID   moduleId,  
    [in]  mdToken    token,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="remarks"></a><span data-ttu-id="f9236-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f9236-107">Remarks</span></span>  
 <span data-ttu-id="f9236-108">`GetFunctionFromToken` Yöntemi, genel işlevler veya genel türlerde işlevleri çalışmaz; artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="f9236-108">The `GetFunctionFromToken` method will not work for generic functions or functions in generic types; it is now obsolete.</span></span> <span data-ttu-id="f9236-109">Kullanım `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` tüm işlevler için.</span><span class="sxs-lookup"><span data-stu-id="f9236-109">Use `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` for all functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9236-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f9236-110">Requirements</span></span>  
 <span data-ttu-id="f9236-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9236-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9236-112">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f9236-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f9236-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f9236-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9236-114">**.NET framework sürümleri:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="f9236-114">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9236-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f9236-115">See Also</span></span>  
 [<span data-ttu-id="f9236-116">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f9236-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
