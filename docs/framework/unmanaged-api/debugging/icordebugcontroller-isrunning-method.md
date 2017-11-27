---
title: "ICorDebugController::IsRunning Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController.IsRunning
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController::IsRunning
helpviewer_keywords:
- IsRunning method [.NET Framework debugging]
- ICorDebugController::IsRunning method [.NET Framework debugging]
ms.assetid: b33ff059-40c4-4dfe-9cb2-21bfed2de0b0
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0cfb2c0fe3c2ebf9473afc4f1a93f50e8fe437f1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcontrollerisrunning-method"></a><span data-ttu-id="b0a8a-102">ICorDebugController::IsRunning Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b0a8a-102">ICorDebugController::IsRunning Method</span></span>
<span data-ttu-id="b0a8a-103">İşlemdeki iş parçacıklarının ücretsiz olarak çalışmakta olan olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="b0a8a-103">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0a8a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b0a8a-104">Syntax</span></span>  
  
```  
HRESULT IsRunning (  
    [out] BOOL *pbRunning  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b0a8a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b0a8a-105">Parameters</span></span>  
 `pbRunning`  
 <span data-ttu-id="b0a8a-106">[out] Bir değer için bir işaretçi `true` serbestçe; Aksi halde, işlemdeki iş parçacıklarının çalıştırıyorsanız, `false`.</span><span class="sxs-lookup"><span data-stu-id="b0a8a-106">[out] A pointer to a value that is `true` if the threads in the process are running freely; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0a8a-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b0a8a-107">Requirements</span></span>  
 <span data-ttu-id="b0a8a-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0a8a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0a8a-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b0a8a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b0a8a-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0a8a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0a8a-111">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0a8a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0a8a-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b0a8a-112">See Also</span></span>  
 
