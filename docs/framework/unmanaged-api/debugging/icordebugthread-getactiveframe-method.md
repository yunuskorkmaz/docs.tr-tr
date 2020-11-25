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
ms.openlocfilehash: 6ca4c1ad5ef575db075a5066146bacb6d1e59ea2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728088"
---
# <a name="icordebugthreadgetactiveframe-method"></a><span data-ttu-id="533cd-102">ICorDebugThread::GetActiveFrame Metodu</span><span class="sxs-lookup"><span data-stu-id="533cd-102">ICorDebugThread::GetActiveFrame Method</span></span>

<span data-ttu-id="533cd-103">Bu ICorDebugThread nesnesindeki etkin (en son) çerçeveye yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="533cd-103">Gets an interface pointer to the active (most recent) frame on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="533cd-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="533cd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="533cd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="533cd-105">Parameters</span></span>  

 `ppFrame`  
 <span data-ttu-id="533cd-106">dışı Bir çerçeveyi temsil eden ICorDebugFrame Interface nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="533cd-106">[out] A pointer to the address of an ICorDebugFrame interface object that represents a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="533cd-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="533cd-107">Remarks</span></span>  

 <span data-ttu-id="533cd-108">`ppFrame`Şu anda hiçbir çerçeve etkin değilse parametre null olur.</span><span class="sxs-lookup"><span data-stu-id="533cd-108">The `ppFrame` parameter is null if no frame is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="533cd-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="533cd-109">Requirements</span></span>  

 <span data-ttu-id="533cd-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="533cd-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="533cd-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="533cd-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="533cd-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="533cd-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="533cd-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="533cd-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
