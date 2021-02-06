---
description: ': ICorProfilerInfo:: GetClassIDInfo yöntemi hakkında daha fazla bilgi edinin'
title: ICorProfilerInfo::GetClassIDInfo Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetClassIDInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetClassIDInfo
helpviewer_keywords:
- GetClassIDInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetClassIDInfo method [.NET Framework profiling]
ms.assetid: 9e93b99e-5aca-415c-8e37-7f33753b612d
topic_type:
- apiref
ms.openlocfilehash: 05937580bd8bd672da16875964548829d071f4bf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647719"
---
# <a name="icorprofilerinfogetclassidinfo-method"></a><span data-ttu-id="92b02-103">ICorProfilerInfo::GetClassIDInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="92b02-103">ICorProfilerInfo::GetClassIDInfo Method</span></span>

<span data-ttu-id="92b02-104">Belirtilen sınıf için üst modülü ve meta veri belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="92b02-104">Gets the parent module and the metadata token for the specified class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92b02-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="92b02-105">Syntax</span></span>  
  
```cpp  
HRESULT GetClassIDInfo(  
    [in]  ClassID   classId,  
    [out] ModuleID  *pModuleId,  
    [out] mdTypeDef *pTypeDefToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92b02-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="92b02-106">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="92b02-107">'ndaki Bilgilerin alınacağı sınıfın KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="92b02-107">[in] The ID of the class for which to get the information.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="92b02-108">dışı Sınıfın üst modülünün KIMLIĞINE yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="92b02-108">[out] A pointer to the ID of the parent module of the class.</span></span>  
  
 `pTypeDefToken`  
 <span data-ttu-id="92b02-109">dışı Sınıf için meta veri belirtecine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="92b02-109">[out] A pointer to the metadata token for the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92b02-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="92b02-110">Remarks</span></span>  

 <span data-ttu-id="92b02-111">Profil Oluşturucu kodu, belirli bir modül için meta veri arabirimi elde etmek üzere [ICorProfilerInfo:: GetModuleMetaData öğesini](icorprofilerinfo-getmodulemetadata-method.md) çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="92b02-111">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) to obtain a metadata interface for a given module.</span></span> <span data-ttu-id="92b02-112">Tarafından başvurulan konuma döndürülen meta veri belirteci, `pTypeDefToken` daha sonra sınıfının meta verilerine erişmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="92b02-112">The metadata token that is returned to the location referenced by `pTypeDefToken` can then be used to access the metadata for the class.</span></span>  
  
 <span data-ttu-id="92b02-113">Genel türler hakkında daha fazla bilgi edinmek için [ICorProfilerInfo2:: GetClassIDInfo2](icorprofilerinfo2-getclassidinfo2-method.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="92b02-113">To get more information for generic types, use [ICorProfilerInfo2::GetClassIDInfo2](icorprofilerinfo2-getclassidinfo2-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92b02-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="92b02-114">Requirements</span></span>  

 <span data-ttu-id="92b02-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92b02-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92b02-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="92b02-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="92b02-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="92b02-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92b02-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92b02-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92b02-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92b02-119">See also</span></span>

- [<span data-ttu-id="92b02-120">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="92b02-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
