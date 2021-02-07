---
description: 'Şu konuda daha fazla bilgi edinin: ıcorıscript Genum:: GetCount Yöntemi'
title: ICorDebugEnum::GetCount Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugEnum.GetCount
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum::GetCount
helpviewer_keywords:
- ICorDebugEnum::GetCount method [.NET Framework debugging]
- GetCount method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: d8a74304-1cb2-4977-a21d-e1af48c563ff
topic_type:
- apiref
ms.openlocfilehash: 38fa85958ea0c6945a5575d12700701ed355891d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694570"
---
# <a name="icordebugenumgetcount-method"></a><span data-ttu-id="e9866-103">ICorDebugEnum::GetCount Metodu</span><span class="sxs-lookup"><span data-stu-id="e9866-103">ICorDebugEnum::GetCount Method</span></span>

<span data-ttu-id="e9866-104">Numaralandırmadaki öğelerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="e9866-104">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9866-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e9866-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9866-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e9866-106">Parameters</span></span>  

 `pcelt`  
 <span data-ttu-id="e9866-107">dışı Numaralandırmadaki öğelerin sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e9866-107">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9866-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e9866-108">Requirements</span></span>  

 <span data-ttu-id="e9866-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9866-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9866-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e9866-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9866-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e9866-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9866-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9866-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
