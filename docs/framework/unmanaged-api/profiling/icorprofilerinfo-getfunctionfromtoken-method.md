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
ms.openlocfilehash: 18c3b6e840ec1f6cb1481c8d752e6399dcdae077
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498147"
---
# <a name="icorprofilerinfogetfunctionfromtoken-method"></a><span data-ttu-id="e8c82-102">ICorProfilerInfo::GetFunctionFromToken Metodu</span><span class="sxs-lookup"><span data-stu-id="e8c82-102">ICorProfilerInfo::GetFunctionFromToken Method</span></span>
<span data-ttu-id="e8c82-103">Bir işlevin KIMLIĞINI alır.</span><span class="sxs-lookup"><span data-stu-id="e8c82-103">Gets the ID of a function.</span></span> <span data-ttu-id="e8c82-104">Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="e8c82-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="e8c82-105">Bunun yerine [ICorProfilerInfo2:: GetFunctionFromTokenAndTypeArgs](icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="e8c82-105">Use the [ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs](icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8c82-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e8c82-106">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromToken(  
    [in]  ModuleID   moduleId,  
    [in]  mdToken    token,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="remarks"></a><span data-ttu-id="e8c82-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e8c82-107">Remarks</span></span>  
 <span data-ttu-id="e8c82-108">`GetFunctionFromToken`Yöntemi genel türlerde genel işlevler veya işlevler için çalışmaz; artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="e8c82-108">The `GetFunctionFromToken` method will not work for generic functions or functions in generic types; it is now obsolete.</span></span> <span data-ttu-id="e8c82-109">`ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs`Tüm işlevler için kullanın.</span><span class="sxs-lookup"><span data-stu-id="e8c82-109">Use `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` for all functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8c82-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e8c82-110">Requirements</span></span>  
 <span data-ttu-id="e8c82-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8c82-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8c82-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e8c82-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e8c82-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e8c82-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8c82-114">**.NET Framework sürümleri:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="e8c82-114">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8c82-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e8c82-115">See also</span></span>

- [<span data-ttu-id="e8c82-116">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e8c82-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
