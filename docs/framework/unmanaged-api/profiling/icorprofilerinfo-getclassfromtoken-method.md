---
description: ': ICorProfilerInfo:: GetClassFromToken Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 0460a9b767f29f108a2b290b848f4cc6b6394ecb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647758"
---
# <a name="icorprofilerinfogetclassfromtoken-method"></a><span data-ttu-id="820f6-103">ICorProfilerInfo::GetClassFromToken Metodu</span><span class="sxs-lookup"><span data-stu-id="820f6-103">ICorProfilerInfo::GetClassFromToken Method</span></span>

<span data-ttu-id="820f6-104">Meta veri belirteci verilen sınıfın KIMLIĞINI alır.</span><span class="sxs-lookup"><span data-stu-id="820f6-104">Gets the ID of the class, given the metadata token.</span></span> <span data-ttu-id="820f6-105">Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="820f6-105">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="820f6-106">Bunun yerine [ICorProfilerInfo2:: GetClassFromTokenAndTypeArgs](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="820f6-106">Use [ICorProfilerInfo2::GetClassFromTokenAndTypeArgs](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="820f6-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="820f6-107">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromToken(  
    [in]  ModuleID  moduleId,  
    [in]  mdTypeDef typeDef,  
    [out] ClassID   *pClassId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="820f6-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="820f6-108">Parameters</span></span>  

 `moduleID`  
 <span data-ttu-id="820f6-109">'ndaki Sınıfını içeren modülün KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="820f6-109">[in] The ID of the module that contains the class.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="820f6-110">'ndaki `mdTypeDef` Sınıfa başvuran bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="820f6-110">[in] An `mdTypeDef` metadata token that references the class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="820f6-111">dışı Sınıf KIMLIĞINE yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="820f6-111">[out] A pointer to the class ID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="820f6-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="820f6-112">Remarks</span></span>  

 <span data-ttu-id="820f6-113">Bu yöntem artık kullanılmıyor; Bunun yerine, `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` tüm türler için kullanın.</span><span class="sxs-lookup"><span data-stu-id="820f6-113">This method is obsolete; instead, use `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` for all types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="820f6-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="820f6-114">Requirements</span></span>  

 <span data-ttu-id="820f6-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="820f6-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="820f6-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="820f6-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="820f6-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="820f6-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="820f6-118">**.NET Framework sürümleri:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="820f6-118">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="820f6-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="820f6-119">See also</span></span>

- [<span data-ttu-id="820f6-120">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="820f6-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
