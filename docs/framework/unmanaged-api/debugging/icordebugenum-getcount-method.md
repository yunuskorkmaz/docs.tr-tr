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
ms.openlocfilehash: 5eddad89c60f25c957a06822d54cc73501b974ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415635"
---
# <a name="icordebugenumgetcount-method"></a><span data-ttu-id="4f295-102">ICorDebugEnum::GetCount Metodu</span><span class="sxs-lookup"><span data-stu-id="4f295-102">ICorDebugEnum::GetCount Method</span></span>
<span data-ttu-id="4f295-103">Sabit listede öğe sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="4f295-103">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f295-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4f295-104">Syntax</span></span>  
  
```  
HRESULT GetCount (  
    [out] ULONG *pcelt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4f295-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4f295-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="4f295-106">[out] Listedeki öğe sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4f295-106">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f295-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4f295-107">Requirements</span></span>  
 <span data-ttu-id="4f295-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f295-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f295-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4f295-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4f295-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4f295-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f295-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f295-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
