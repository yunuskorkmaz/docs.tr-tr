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
ms.openlocfilehash: 841953625235406f013e9f140ad91c7b65680e47
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863959"
---
# <a name="icorprofilerinfogetclassfromtoken-method"></a><span data-ttu-id="16884-102">ICorProfilerInfo::GetClassFromToken Metodu</span><span class="sxs-lookup"><span data-stu-id="16884-102">ICorProfilerInfo::GetClassFromToken Method</span></span>
<span data-ttu-id="16884-103">Meta veri belirteci verilen sınıfın KIMLIĞINI alır.</span><span class="sxs-lookup"><span data-stu-id="16884-103">Gets the ID of the class, given the metadata token.</span></span> <span data-ttu-id="16884-104">Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="16884-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="16884-105">Bunun yerine [ICorProfilerInfo2:: GetClassFromTokenAndTypeArgs](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="16884-105">Use [ICorProfilerInfo2::GetClassFromTokenAndTypeArgs](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16884-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="16884-106">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromToken(  
    [in]  ModuleID  moduleId,  
    [in]  mdTypeDef typeDef,  
    [out] ClassID   *pClassId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16884-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="16884-107">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="16884-108">'ndaki Sınıfını içeren modülün KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="16884-108">[in] The ID of the module that contains the class.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="16884-109">'ndaki Sınıfa başvuran bir `mdTypeDef` meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="16884-109">[in] An `mdTypeDef` metadata token that references the class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="16884-110">dışı Sınıf KIMLIĞINE yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="16884-110">[out] A pointer to the class ID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16884-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="16884-111">Remarks</span></span>  
 <span data-ttu-id="16884-112">Bu yöntem artık kullanılmıyor; Bunun yerine, tüm türler için `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` kullanın.</span><span class="sxs-lookup"><span data-stu-id="16884-112">This method is obsolete; instead, use `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` for all types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16884-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="16884-113">Requirements</span></span>  
 <span data-ttu-id="16884-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16884-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16884-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="16884-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="16884-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="16884-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16884-117">**.NET Framework sürümleri:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="16884-117">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16884-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16884-118">See also</span></span>

- [<span data-ttu-id="16884-119">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="16884-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
