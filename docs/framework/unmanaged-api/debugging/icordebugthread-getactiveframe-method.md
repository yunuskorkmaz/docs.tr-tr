---
title: ICorDebugThread::GetActiveFrame Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetActiveFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetActiveFrame
helpviewer_keywords:
- ICorDebugThread::GetActiveFrame method [.NET Framework debugging]
- GetActiveFrame method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 8d6d3a1a-fef6-4f2f-a22c-3bdd30d70e07
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a1bbe5674ba11b5ee6033c65f229d698eff15ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420647"
---
# <a name="icordebugthreadgetactiveframe-method"></a><span data-ttu-id="595e7-102">ICorDebugThread::GetActiveFrame Metodu</span><span class="sxs-lookup"><span data-stu-id="595e7-102">ICorDebugThread::GetActiveFrame Method</span></span>
<span data-ttu-id="595e7-103">Arabirim işaretçisi etkin (en son) kareye bu Icordebugthread nesnede alır.</span><span class="sxs-lookup"><span data-stu-id="595e7-103">Gets an interface pointer to the active (most recent) frame on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="595e7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="595e7-104">Syntax</span></span>  
  
```  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="595e7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="595e7-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="595e7-106">[out] Bir çerçeve temsil eden bir Icordebugframe arabirimi nesnesi adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="595e7-106">[out] A pointer to the address of an ICorDebugFrame interface object that represents a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="595e7-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="595e7-107">Remarks</span></span>  
 <span data-ttu-id="595e7-108">`ppFrame` Parametredir hiçbir çerçevesi şu anda etkin değilse null.</span><span class="sxs-lookup"><span data-stu-id="595e7-108">The `ppFrame` parameter is null if no frame is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="595e7-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="595e7-109">Requirements</span></span>  
 <span data-ttu-id="595e7-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="595e7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="595e7-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="595e7-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="595e7-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="595e7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="595e7-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="595e7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
