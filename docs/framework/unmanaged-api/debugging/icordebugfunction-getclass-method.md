---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea71e984be42e3b1a7b4b9fa6df878aca911c412
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501194"
---
# <a name="icordebugfunctiongetclass-method"></a><span data-ttu-id="7e802-102">ICorDebugFunction::GetClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7e802-102">ICorDebugFunction::GetClass Method</span></span>
<span data-ttu-id="7e802-103">Bu işlev bir üyesi, sınıfın temsil ettiği bir Icordebugclass nesnesini alır.</span><span class="sxs-lookup"><span data-stu-id="7e802-103">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e802-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7e802-104">Syntax</span></span>  
  
```  
HRESULT GetClass (  
    [out] ICorDebugClass **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e802-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7e802-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="7e802-106">[out] Adresini bir işaretçiye `ICorDebugClass` bu işlev bir sınıfın üyesi değilse, sınıf veya null temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="7e802-106">[out] A pointer to the address of the `ICorDebugClass` object that represents the class, or null, if this function is not a member of a class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e802-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7e802-107">Requirements</span></span>  
 <span data-ttu-id="7e802-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e802-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e802-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7e802-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7e802-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e802-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e802-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e802-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
