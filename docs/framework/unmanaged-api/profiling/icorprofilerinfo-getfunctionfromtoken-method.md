---
title: ICorProfilerInfo::GetFunctionFromToken Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetFunctionFromToken
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetFunctionFromToken
helpviewer_keywords:
- ICorProfilerInfo::GetFunctionFromToken method [.NET Framework profiling]
- GetFunctionFromToken method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 0eed759f-cce8-405d-88dc-9ee293a38928
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c7366df7d2213740f640590364b1cb4d28876115
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfogetfunctionfromtoken-method"></a><span data-ttu-id="938cc-102">ICorProfilerInfo::GetFunctionFromToken Metodu</span><span class="sxs-lookup"><span data-stu-id="938cc-102">ICorProfilerInfo::GetFunctionFromToken Method</span></span>
<span data-ttu-id="938cc-103">Bir işlev Kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="938cc-103">Gets the ID of a function.</span></span> <span data-ttu-id="938cc-104">Bu yöntem .NET Framework 2.0 sürümünde kullanımdan kalkmıştır.</span><span class="sxs-lookup"><span data-stu-id="938cc-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="938cc-105">Kullanım [Icorprofilerınfo2::getfunctionfromtokenandtypeargs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="938cc-105">Use the [ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="938cc-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="938cc-106">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromToken(  
    [in]  ModuleID   moduleId,  
    [in]  mdToken    token,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="remarks"></a><span data-ttu-id="938cc-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="938cc-107">Remarks</span></span>  
 <span data-ttu-id="938cc-108">`GetFunctionFromToken` Yöntemi, genel işlevler veya genel türlerde işlevleri çalışmaz; artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="938cc-108">The `GetFunctionFromToken` method will not work for generic functions or functions in generic types; it is now obsolete.</span></span> <span data-ttu-id="938cc-109">Kullanım `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` tüm işlevler için.</span><span class="sxs-lookup"><span data-stu-id="938cc-109">Use `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` for all functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="938cc-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="938cc-110">Requirements</span></span>  
 <span data-ttu-id="938cc-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="938cc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="938cc-112">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="938cc-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="938cc-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="938cc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="938cc-114">**.NET framework sürümleri:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="938cc-114">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="938cc-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="938cc-115">See Also</span></span>  
 [<span data-ttu-id="938cc-116">Icorprofilerınfo arabirimi</span><span class="sxs-lookup"><span data-stu-id="938cc-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
