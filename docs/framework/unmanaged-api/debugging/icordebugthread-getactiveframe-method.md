---
description: ': ICorDebugThread:: GetActiveFrame Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 3b15aad39503dfec9ac8f98f839ee1a6b16b3f90
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659268"
---
# <a name="icordebugthreadgetactiveframe-method"></a><span data-ttu-id="b9a37-103">ICorDebugThread::GetActiveFrame Metodu</span><span class="sxs-lookup"><span data-stu-id="b9a37-103">ICorDebugThread::GetActiveFrame Method</span></span>

<span data-ttu-id="b9a37-104">Bu ICorDebugThread nesnesindeki etkin (en son) çerçeveye yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="b9a37-104">Gets an interface pointer to the active (most recent) frame on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9a37-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b9a37-105">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9a37-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b9a37-106">Parameters</span></span>  

 `ppFrame`  
 <span data-ttu-id="b9a37-107">dışı Bir çerçeveyi temsil eden ICorDebugFrame Interface nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b9a37-107">[out] A pointer to the address of an ICorDebugFrame interface object that represents a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9a37-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b9a37-108">Remarks</span></span>  

 <span data-ttu-id="b9a37-109">`ppFrame`Şu anda hiçbir çerçeve etkin değilse parametre null olur.</span><span class="sxs-lookup"><span data-stu-id="b9a37-109">The `ppFrame` parameter is null if no frame is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9a37-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b9a37-110">Requirements</span></span>  

 <span data-ttu-id="b9a37-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9a37-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9a37-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b9a37-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b9a37-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b9a37-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9a37-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9a37-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
