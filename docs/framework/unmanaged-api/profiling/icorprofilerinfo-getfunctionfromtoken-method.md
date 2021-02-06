---
description: ': ICorProfilerInfo:: GetFunctionFromToken yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 58dea413539d6e3a625f515aa7e8d5123152c90a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647459"
---
# <a name="icorprofilerinfogetfunctionfromtoken-method"></a><span data-ttu-id="92562-103">ICorProfilerInfo::GetFunctionFromToken Metodu</span><span class="sxs-lookup"><span data-stu-id="92562-103">ICorProfilerInfo::GetFunctionFromToken Method</span></span>

<span data-ttu-id="92562-104">Bir işlevin KIMLIĞINI alır.</span><span class="sxs-lookup"><span data-stu-id="92562-104">Gets the ID of a function.</span></span> <span data-ttu-id="92562-105">Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="92562-105">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="92562-106">Bunun yerine [ICorProfilerInfo2:: GetFunctionFromTokenAndTypeArgs](icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="92562-106">Use the [ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs](icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92562-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="92562-107">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromToken(  
    [in]  ModuleID   moduleId,  
    [in]  mdToken    token,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="remarks"></a><span data-ttu-id="92562-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="92562-108">Remarks</span></span>  

 <span data-ttu-id="92562-109">`GetFunctionFromToken`Yöntemi genel türlerde genel işlevler veya işlevler için çalışmaz; artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="92562-109">The `GetFunctionFromToken` method will not work for generic functions or functions in generic types; it is now obsolete.</span></span> <span data-ttu-id="92562-110">`ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs`Tüm işlevler için kullanın.</span><span class="sxs-lookup"><span data-stu-id="92562-110">Use `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` for all functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92562-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="92562-111">Requirements</span></span>  

 <span data-ttu-id="92562-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92562-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92562-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="92562-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="92562-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="92562-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92562-115">**.NET Framework sürümleri:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="92562-115">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92562-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92562-116">See also</span></span>

- [<span data-ttu-id="92562-117">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="92562-117">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
