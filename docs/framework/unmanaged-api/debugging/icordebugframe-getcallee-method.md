---
description: ': ICorDebugFrame:: Getçağrılan yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugFrame::GetCallee Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCallee
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCallee
helpviewer_keywords:
- ICorDebugFrame::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 92d8136d-0436-4c7e-a6b2-80765f892a0d
topic_type:
- apiref
ms.openlocfilehash: 85b64933cb2f180445b88f7b19f8b78f1788252e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693076"
---
# <a name="icordebugframegetcallee-method"></a><span data-ttu-id="6ab65-103">ICorDebugFrame::GetCallee Metodu</span><span class="sxs-lookup"><span data-stu-id="6ab65-103">ICorDebugFrame::GetCallee Method</span></span>

<span data-ttu-id="6ab65-104">Geçerli zincirde bu karenin çağrıldığı ICorDebugFrame nesnesine bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="6ab65-104">Gets a pointer to the ICorDebugFrame object in the current chain that this frame called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ab65-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6ab65-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCallee (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ab65-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6ab65-106">Parameters</span></span>  

 `ppFrame`  
 <span data-ttu-id="6ab65-107">dışı `ICorDebugFrame` Çağrılan çerçeveyi temsil eden nesnenin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6ab65-107">[out] A pointer to the address of an `ICorDebugFrame` object that represents the called frame.</span></span> <span data-ttu-id="6ab65-108">Bu değer, çağıran çerçeve geçerli zincirde en içteki çerçevedir ise null olur.</span><span class="sxs-lookup"><span data-stu-id="6ab65-108">This value is null if the calling frame is the innermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ab65-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6ab65-109">Requirements</span></span>  

 <span data-ttu-id="6ab65-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ab65-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ab65-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6ab65-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6ab65-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6ab65-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6ab65-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ab65-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
