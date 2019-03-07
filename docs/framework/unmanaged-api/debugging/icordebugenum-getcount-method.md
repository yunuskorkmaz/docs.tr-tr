---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b4af328c537fbc3b64eb1a2ac3df3a4e4224789e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466631"
---
# <a name="icordebugenumgetcount-method"></a><span data-ttu-id="466b6-102">ICorDebugEnum::GetCount Metodu</span><span class="sxs-lookup"><span data-stu-id="466b6-102">ICorDebugEnum::GetCount Method</span></span>
<span data-ttu-id="466b6-103">Sabit listede öğe sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="466b6-103">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="466b6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="466b6-104">Syntax</span></span>  
  
```  
HRESULT GetCount (  
    [out] ULONG *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="466b6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="466b6-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="466b6-106">[out] Listedeki öğe sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="466b6-106">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="466b6-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="466b6-107">Requirements</span></span>  
 <span data-ttu-id="466b6-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="466b6-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="466b6-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="466b6-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="466b6-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="466b6-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="466b6-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="466b6-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
