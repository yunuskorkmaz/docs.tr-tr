---
description: ': ICorDebugFrame:: Getzincirine metodu hakkında daha fazla bilgi edinin'
title: ICorDebugFrame::GetChain Yöntemi
ms.date: 03/30/2017
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
ms.openlocfilehash: d162d484a54f107fb5937e57f60e2b82cad90ca1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693063"
---
# <a name="icordebugframegetchain-method"></a><span data-ttu-id="4e687-103">ICorDebugFrame::GetChain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4e687-103">ICorDebugFrame::GetChain Method</span></span>

<span data-ttu-id="4e687-104">Bu çerçevenin parçası olduğu zincire yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="4e687-104">Gets a pointer to the chain this frame is a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e687-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4e687-105">Syntax</span></span>  
  
```cpp  
HRESULT GetChain (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e687-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4e687-106">Parameters</span></span>  

 `ppChain`  
 <span data-ttu-id="4e687-107">dışı Bu çerçeveyi içeren zinciri temsil eden bir ıcordebugzincirleri nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4e687-107">[out] A pointer to the address of an ICorDebugChain object that represents the chain containing this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e687-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4e687-108">Requirements</span></span>  

 <span data-ttu-id="4e687-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e687-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e687-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4e687-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4e687-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4e687-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e687-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e687-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
