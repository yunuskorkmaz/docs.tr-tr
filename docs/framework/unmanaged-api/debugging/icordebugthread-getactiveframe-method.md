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
ms.openlocfilehash: d623893bd77e46832b0bd823ed60c23e4eee29ba
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133535"
---
# <a name="icordebugthreadgetactiveframe-method"></a><span data-ttu-id="d5e3b-102">ICorDebugThread::GetActiveFrame Metodu</span><span class="sxs-lookup"><span data-stu-id="d5e3b-102">ICorDebugThread::GetActiveFrame Method</span></span>
<span data-ttu-id="d5e3b-103">Bu ICorDebugThread nesnesindeki etkin (en son) çerçeveye yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="d5e3b-103">Gets an interface pointer to the active (most recent) frame on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5e3b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d5e3b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5e3b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d5e3b-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="d5e3b-106">dışı Bir çerçeveyi temsil eden ICorDebugFrame Interface nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d5e3b-106">[out] A pointer to the address of an ICorDebugFrame interface object that represents a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5e3b-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d5e3b-107">Remarks</span></span>  
 <span data-ttu-id="d5e3b-108">Şu anda etkin bir çerçeve yoksa `ppFrame` parametresi null.</span><span class="sxs-lookup"><span data-stu-id="d5e3b-108">The `ppFrame` parameter is null if no frame is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5e3b-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d5e3b-109">Requirements</span></span>  
 <span data-ttu-id="d5e3b-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5e3b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5e3b-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d5e3b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d5e3b-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d5e3b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5e3b-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5e3b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
