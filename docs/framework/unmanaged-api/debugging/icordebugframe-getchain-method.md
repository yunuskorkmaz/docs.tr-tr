---
title: ICorDebugFrame::GetChain Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugFrame.GetChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetChain
helpviewer_keywords:
- ICorDebugFrame::GetChain method [.NET Framework debugging]
- GetChain method [.NET Framework debugging]
ms.assetid: e28e51d3-8f73-494f-bcd4-48bac239fbe1
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 479ad2db4752f9e031783b430396286c6989b115
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugframegetchain-method"></a><span data-ttu-id="9bfb1-102">ICorDebugFrame::GetChain Metodu</span><span class="sxs-lookup"><span data-stu-id="9bfb1-102">ICorDebugFrame::GetChain Method</span></span>
<span data-ttu-id="9bfb1-103">Bu çerçeve bir parçası olan zinciri işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="9bfb1-103">Gets a pointer to the chain this frame is a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bfb1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9bfb1-104">Syntax</span></span>  
  
```  
HRESULT GetChain (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9bfb1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9bfb1-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="9bfb1-106">[out] Bu çerçeve içeren zinciri temsil eden Icordebugchain nesne adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9bfb1-106">[out] A pointer to the address of an ICorDebugChain object that represents the chain containing this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9bfb1-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9bfb1-107">Requirements</span></span>  
 <span data-ttu-id="9bfb1-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9bfb1-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bfb1-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9bfb1-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9bfb1-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9bfb1-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9bfb1-111">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bfb1-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
