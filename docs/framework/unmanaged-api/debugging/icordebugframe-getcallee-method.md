---
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
ms.openlocfilehash: 6347e0109f256dc46eb0140ffd1f51977c205b51
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678811"
---
# <a name="icordebugframegetcallee-method"></a><span data-ttu-id="a8ea0-102">ICorDebugFrame::GetCallee Metodu</span><span class="sxs-lookup"><span data-stu-id="a8ea0-102">ICorDebugFrame::GetCallee Method</span></span>

<span data-ttu-id="a8ea0-103">Geçerli zincirde bu karenin çağrıldığı ICorDebugFrame nesnesine bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="a8ea0-103">Gets a pointer to the ICorDebugFrame object in the current chain that this frame called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8ea0-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a8ea0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCallee (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8ea0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a8ea0-105">Parameters</span></span>  

 `ppFrame`  
 <span data-ttu-id="a8ea0-106">dışı `ICorDebugFrame` Çağrılan çerçeveyi temsil eden nesnenin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a8ea0-106">[out] A pointer to the address of an `ICorDebugFrame` object that represents the called frame.</span></span> <span data-ttu-id="a8ea0-107">Bu değer, çağıran çerçeve geçerli zincirde en içteki çerçevedir ise null olur.</span><span class="sxs-lookup"><span data-stu-id="a8ea0-107">This value is null if the calling frame is the innermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8ea0-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a8ea0-108">Requirements</span></span>  

 <span data-ttu-id="a8ea0-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8ea0-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8ea0-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a8ea0-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a8ea0-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a8ea0-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8ea0-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8ea0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
