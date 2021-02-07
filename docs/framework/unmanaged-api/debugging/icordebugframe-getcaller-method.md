---
description: ': ICorDebugFrame:: GetCaller Yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugFrame::GetCaller Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCaller
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCaller
helpviewer_keywords:
- GetCaller method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetCaller method [.NET Framework debugging]
ms.assetid: bfdc946b-8238-4eb9-8a85-884049fb0fd4
topic_type:
- apiref
ms.openlocfilehash: a042341f6edfa0e8f6ca00f758107852f9e381cb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693050"
---
# <a name="icordebugframegetcaller-method"></a><span data-ttu-id="d8452-103">ICorDebugFrame::GetCaller Metodu</span><span class="sxs-lookup"><span data-stu-id="d8452-103">ICorDebugFrame::GetCaller Method</span></span>

<span data-ttu-id="d8452-104">Bu çerçeveyi çağıran geçerli zincirde ICorDebugFrame nesnesine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="d8452-104">Gets a pointer to the ICorDebugFrame object in the current chain that called this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8452-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8452-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCaller (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8452-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d8452-106">Parameters</span></span>  

 `ppFrame`  
 <span data-ttu-id="d8452-107">dışı `ICorDebugFrame` Çağırma çerçevesini temsil eden nesnenin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d8452-107">[out] A pointer to the address of an `ICorDebugFrame` object that represents the calling frame.</span></span> <span data-ttu-id="d8452-108">Çağrılan çerçeve geçerli zincirde en dıştaki çerçevedir ise bu değer null olur.</span><span class="sxs-lookup"><span data-stu-id="d8452-108">This value is null if the called frame is the outermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8452-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d8452-109">Requirements</span></span>  

 <span data-ttu-id="d8452-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8452-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8452-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d8452-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8452-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d8452-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8452-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8452-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
