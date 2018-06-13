---
title: ICorDebugArrayValue::GetCount Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetCount
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetCount
helpviewer_keywords:
- ICorDebugArrayValue::GetCount method [.NET Framework debugging]
- GetCount method, ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: 44cd98cf-2127-4d46-8c6a-da4e857bb6b0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aa72f82d2fc78110fc2bee8edd265916996aa884
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403152"
---
# <a name="icordebugarrayvaluegetcount-method"></a><span data-ttu-id="8f0f9-102">ICorDebugArrayValue::GetCount Metodu</span><span class="sxs-lookup"><span data-stu-id="8f0f9-102">ICorDebugArrayValue::GetCount Method</span></span>
<span data-ttu-id="8f0f9-103">Dizideki öğeler toplam sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="8f0f9-103">Gets the total number of elements in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f0f9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8f0f9-104">Syntax</span></span>  
  
```  
HRESULT GetCount (  
    [out] ULONG32 *pnCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8f0f9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8f0f9-105">Parameters</span></span>  
 `pnCount`  
 <span data-ttu-id="8f0f9-106">[out] Dizideki öğeler toplam sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8f0f9-106">[out] A pointer to the total number of elements in the array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f0f9-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8f0f9-107">Requirements</span></span>  
 <span data-ttu-id="8f0f9-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f0f9-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f0f9-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8f0f9-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8f0f9-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8f0f9-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f0f9-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f0f9-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
