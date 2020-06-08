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
ms.openlocfilehash: 12b4b897f9dc51175037d39c0368b6ce59fefefb
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498485"
---
# <a name="icorprofilerinfogetclassfromtoken-method"></a><span data-ttu-id="f4537-102">ICorProfilerInfo::GetClassFromToken Metodu</span><span class="sxs-lookup"><span data-stu-id="f4537-102">ICorProfilerInfo::GetClassFromToken Method</span></span>
<span data-ttu-id="f4537-103">Meta veri belirteci verilen sınıfın KIMLIĞINI alır.</span><span class="sxs-lookup"><span data-stu-id="f4537-103">Gets the ID of the class, given the metadata token.</span></span> <span data-ttu-id="f4537-104">Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="f4537-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="f4537-105">Bunun yerine [ICorProfilerInfo2:: GetClassFromTokenAndTypeArgs](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="f4537-105">Use [ICorProfilerInfo2::GetClassFromTokenAndTypeArgs](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4537-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="f4537-106">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromToken(  
    [in]  ModuleID  moduleId,  
    [in]  mdTypeDef typeDef,  
    [out] ClassID   *pClassId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4537-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f4537-107">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="f4537-108">'ndaki Sınıfını içeren modülün KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="f4537-108">[in] The ID of the module that contains the class.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="f4537-109">'ndaki `mdTypeDef`Sınıfa başvuran bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="f4537-109">[in] An `mdTypeDef` metadata token that references the class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="f4537-110">dışı Sınıf KIMLIĞINE yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f4537-110">[out] A pointer to the class ID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f4537-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f4537-111">Remarks</span></span>  
 <span data-ttu-id="f4537-112">Bu yöntem artık kullanılmıyor; Bunun yerine, `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` tüm türler için kullanın.</span><span class="sxs-lookup"><span data-stu-id="f4537-112">This method is obsolete; instead, use `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` for all types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4537-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f4537-113">Requirements</span></span>  
 <span data-ttu-id="f4537-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4537-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4537-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f4537-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f4537-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f4537-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f4537-117">**.NET Framework sürümleri:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="f4537-117">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4537-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4537-118">See also</span></span>

- [<span data-ttu-id="f4537-119">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f4537-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
