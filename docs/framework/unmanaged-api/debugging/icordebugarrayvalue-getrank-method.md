---
title: ICorDebugArrayValue::GetRank Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugArrayValue.GetRank
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugArrayValue::GetRank
helpviewer_keywords:
- ICorDebugArrayValue::GetRank method [.NET Framework debugging]
- GetRank method, ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: 5e83c82c-593d-4691-90b0-383d218b415e
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a7e92a0edfe220bda820550cc385bf2eb3846b08
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugarrayvaluegetrank-method"></a><span data-ttu-id="df07c-102">ICorDebugArrayValue::GetRank Metodu</span><span class="sxs-lookup"><span data-stu-id="df07c-102">ICorDebugArrayValue::GetRank Method</span></span>
<span data-ttu-id="df07c-103">Dizideki boyut sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="df07c-103">Gets the number of dimensions in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df07c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="df07c-104">Syntax</span></span>  
  
```  
HRESULT GetRank (  
    [out] ULONG32   *pnRank  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="df07c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="df07c-105">Parameters</span></span>  
 `pnRank`  
 <span data-ttu-id="df07c-106">[out] Bu boyut sayısını gösteren bir işaretçi `ICorDebugArrayValue` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="df07c-106">[out] A pointer to the number of dimensions in this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df07c-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="df07c-107">Requirements</span></span>  
 <span data-ttu-id="df07c-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df07c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df07c-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="df07c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="df07c-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="df07c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df07c-111">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df07c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
