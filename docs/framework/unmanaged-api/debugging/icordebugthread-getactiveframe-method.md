---
title: ICorDebugThread::GetActiveFrame Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.GetActiveFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::GetActiveFrame
helpviewer_keywords:
- ICorDebugThread::GetActiveFrame method [.NET Framework debugging]
- GetActiveFrame method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 8d6d3a1a-fef6-4f2f-a22c-3bdd30d70e07
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f8b5d9d42b7c3f7827ce938fdd3dffe57b00142c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthreadgetactiveframe-method"></a><span data-ttu-id="53407-102">ICorDebugThread::GetActiveFrame Metodu</span><span class="sxs-lookup"><span data-stu-id="53407-102">ICorDebugThread::GetActiveFrame Method</span></span>
<span data-ttu-id="53407-103">Arabirim işaretçisi etkin (en son) kareye bu Icordebugthread nesnede alır.</span><span class="sxs-lookup"><span data-stu-id="53407-103">Gets an interface pointer to the active (most recent) frame on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53407-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="53407-104">Syntax</span></span>  
  
```  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="53407-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="53407-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="53407-106">[out] Bir çerçeve temsil eden bir Icordebugframe arabirimi nesnesi adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="53407-106">[out] A pointer to the address of an ICorDebugFrame interface object that represents a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53407-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="53407-107">Remarks</span></span>  
 <span data-ttu-id="53407-108">`ppFrame` Parametredir hiçbir çerçevesi şu anda etkin değilse null.</span><span class="sxs-lookup"><span data-stu-id="53407-108">The `ppFrame` parameter is null if no frame is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53407-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="53407-109">Requirements</span></span>  
 <span data-ttu-id="53407-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53407-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53407-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="53407-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="53407-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53407-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53407-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53407-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
