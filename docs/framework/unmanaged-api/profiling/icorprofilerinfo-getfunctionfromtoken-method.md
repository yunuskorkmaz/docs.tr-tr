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
ms.openlocfilehash: 9c971df072cc7c6546e5c17278c78c7e9668ab63
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780628"
---
# <a name="icorprofilerinfogetfunctionfromtoken-method"></a><span data-ttu-id="85c35-102">ICorProfilerInfo::GetFunctionFromToken Metodu</span><span class="sxs-lookup"><span data-stu-id="85c35-102">ICorProfilerInfo::GetFunctionFromToken Method</span></span>
<span data-ttu-id="85c35-103">Bir işlev Kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="85c35-103">Gets the ID of a function.</span></span> <span data-ttu-id="85c35-104">Bu yöntem .NET Framework 2.0 sürümünde artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="85c35-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="85c35-105">Kullanım [Icorprofilerınfo2::getfunctionfromtokenandtypeargs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="85c35-105">Use the [ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85c35-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="85c35-106">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromToken(  
    [in]  ModuleID   moduleId,  
    [in]  mdToken    token,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="remarks"></a><span data-ttu-id="85c35-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="85c35-107">Remarks</span></span>  
 <span data-ttu-id="85c35-108">`GetFunctionFromToken` Yöntemi, genel işlevler veya genel türlerindeki işlevleri çalışmaz; artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="85c35-108">The `GetFunctionFromToken` method will not work for generic functions or functions in generic types; it is now obsolete.</span></span> <span data-ttu-id="85c35-109">Kullanım `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` tüm işlevler için.</span><span class="sxs-lookup"><span data-stu-id="85c35-109">Use `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` for all functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85c35-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="85c35-110">Requirements</span></span>  
 <span data-ttu-id="85c35-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85c35-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85c35-112">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="85c35-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="85c35-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="85c35-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85c35-114">**.NET framework sürümleri:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="85c35-114">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85c35-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85c35-115">See also</span></span>

- [<span data-ttu-id="85c35-116">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="85c35-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
