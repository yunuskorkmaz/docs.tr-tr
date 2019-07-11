---
title: ICorDebugType::GetRank Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetRank
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetRank
helpviewer_keywords:
- GetRank method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::GetRank method [.NET Framework debugging]
ms.assetid: 72d3d927-f590-4f2d-8f60-448f3dfb96af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e42db5d7ebc9ec9983fe9e56477808415b26968b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751576"
---
# <a name="icordebugtypegetrank-method"></a><span data-ttu-id="27dae-102">ICorDebugType::GetRank Metodu</span><span class="sxs-lookup"><span data-stu-id="27dae-102">ICorDebugType::GetRank Method</span></span>
<span data-ttu-id="27dae-103">Bir dizi türü boyut sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="27dae-103">Gets the number of dimensions in an array type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27dae-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="27dae-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRank (  
    [out] ULONG32   *pnRank  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27dae-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="27dae-105">Parameters</span></span>  
 `pnRank`  
 <span data-ttu-id="27dae-106">[out] Boyutların sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="27dae-106">[out] A pointer to the number of dimensions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27dae-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="27dae-107">Requirements</span></span>  
 <span data-ttu-id="27dae-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27dae-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27dae-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="27dae-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="27dae-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="27dae-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27dae-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27dae-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
