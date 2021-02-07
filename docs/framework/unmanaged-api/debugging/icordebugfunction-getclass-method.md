---
description: ': ICorDebugFunction:: GetClass yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugFunction::GetClass Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetClass
helpviewer_keywords:
- GetClass method, ICorDebugFunction interface [.NET Framework debugging]
- ICorDebugFunction::GetClass method [.NET Framework debugging]
ms.assetid: 27967230-144f-40d3-9e23-961d0241abd9
topic_type:
- apiref
ms.openlocfilehash: 09049962082bc51cc47a56b0de591a26c2ef93fc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692595"
---
# <a name="icordebugfunctiongetclass-method"></a><span data-ttu-id="eb52f-103">ICorDebugFunction::GetClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eb52f-103">ICorDebugFunction::GetClass Method</span></span>

<span data-ttu-id="eb52f-104">Bu işlevin üyesi olduğu sınıfı temsil eden bir ICorDebugClass nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="eb52f-104">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb52f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eb52f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb52f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="eb52f-106">Parameters</span></span>  

 `ppClass`  
 <span data-ttu-id="eb52f-107">dışı `ICorDebugClass` Sınıfı temsil eden nesnenin adresine yönelik bir işaretçi veya bu işlev bir sınıfın üyesi değilse null.</span><span class="sxs-lookup"><span data-stu-id="eb52f-107">[out] A pointer to the address of the `ICorDebugClass` object that represents the class, or null, if this function is not a member of a class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb52f-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eb52f-108">Requirements</span></span>  

 <span data-ttu-id="eb52f-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb52f-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb52f-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="eb52f-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eb52f-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="eb52f-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb52f-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb52f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
