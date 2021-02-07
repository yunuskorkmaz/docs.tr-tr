---
description: 'Şu konuda daha fazla bilgi edinin: ıcorı, Garrayvalue:: GetCount Yöntemi'
title: ICorDebugArrayValue::GetCount Yöntemi
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
ms.openlocfilehash: 7b1422714ed9c6f89c65c310165b8cdaa6566360
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723158"
---
# <a name="icordebugarrayvaluegetcount-method"></a><span data-ttu-id="49f9b-103">ICorDebugArrayValue::GetCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="49f9b-103">ICorDebugArrayValue::GetCount Method</span></span>

<span data-ttu-id="49f9b-104">Dizideki toplam öğe sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="49f9b-104">Gets the total number of elements in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49f9b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="49f9b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG32 *pnCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49f9b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="49f9b-106">Parameters</span></span>  

 `pnCount`  
 <span data-ttu-id="49f9b-107">dışı Dizideki toplam öğe sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="49f9b-107">[out] A pointer to the total number of elements in the array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49f9b-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="49f9b-108">Requirements</span></span>  

 <span data-ttu-id="49f9b-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49f9b-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49f9b-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="49f9b-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="49f9b-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="49f9b-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49f9b-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49f9b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
