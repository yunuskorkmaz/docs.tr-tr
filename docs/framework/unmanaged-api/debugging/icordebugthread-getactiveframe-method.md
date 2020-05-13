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
ms.openlocfilehash: 843c6df1ef41fdd3227b92275182432ad4cc43b1
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379722"
---
# <a name="icordebugthreadgetactiveframe-method"></a><span data-ttu-id="32985-102">ICorDebugThread::GetActiveFrame Metodu</span><span class="sxs-lookup"><span data-stu-id="32985-102">ICorDebugThread::GetActiveFrame Method</span></span>
<span data-ttu-id="32985-103">Bu ICorDebugThread nesnesindeki etkin (en son) çerçeveye yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="32985-103">Gets an interface pointer to the active (most recent) frame on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32985-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="32985-104">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32985-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="32985-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="32985-106">dışı Bir çerçeveyi temsil eden ICorDebugFrame Interface nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="32985-106">[out] A pointer to the address of an ICorDebugFrame interface object that represents a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32985-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="32985-107">Remarks</span></span>  
 <span data-ttu-id="32985-108">`ppFrame`Şu anda hiçbir çerçeve etkin değilse parametre null olur.</span><span class="sxs-lookup"><span data-stu-id="32985-108">The `ppFrame` parameter is null if no frame is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32985-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="32985-109">Requirements</span></span>  
 <span data-ttu-id="32985-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32985-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32985-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="32985-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="32985-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="32985-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32985-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32985-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
